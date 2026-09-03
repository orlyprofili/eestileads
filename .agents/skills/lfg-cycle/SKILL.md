---
name: lfg-cycle
description: Use for portable issue-driven coding workflows invoked as issue create, issue check, issue fix, lfg, or rev. Drives an agent-ready issue through readiness audit, implementation, independent review, validation, fast-forward merge, preserved branch history, and issue closure.
---

# LFG Cycle

Run a scoped issue from durable specification to validated, reviewed, merged code. Read repository and user-level agent instructions first; project-specific build, test, flash, run, and monitoring details come from local skills, scripts, and docs.

## Commands

- `issue create`: create an agent-ready tracker issue from the current discussion.
- `issue check <id>`: audit and objectively repair an issue for cold-start readiness.
- `issue fix <id>`: implement, verify, and commit the issue on its topic branch; do not merge or close it.
- `lfg <id>`: run the full readiness-to-closure workflow.
- `rev [make|peer|resp]`: run the review protocol below. Bare `rev` runs `make` then a fresh `peer` review of the current scoped diff.

Accept equivalent command spellings with or without a leading slash.

## Rules

- Keep this workflow project-agnostic. Discover project commands from local instructions and skills.
- Use one durable tracker issue per scoped deliverable. Large trackers may have independently executable child issues.
- At the readiness gate, check whether the issue fits one LFG cycle. If not, stop and report that it must be split; do not implement it.
- Prefer no PR. Open one only when repository policy or the operator explicitly requires it.
- Preserve a linear graph: branch from the configured base, commit normally, and merge with `--ff-only`. Do not squash, rebase, create merge commits, or delete topic branches unless explicitly required.
- Preserve the topic branch locally and on the remote after merge so it decorates the completion commit.
- Require a fresh independent reviewer before merge. Self-review is not a substitute.
- Resolve every reviewer finding in scope. Fix agreed findings; dispute only with concrete evidence and obtain reviewer acceptance of the response.
- Split work only when a validated major finding would derail the scoped issue. Create an agent-ready issue for that derailment before proceeding.

## Issue Readiness

`issue create` produces the durable handoff artifact, not draft prose. Reconstruct the problem and solution from the discussion, inspect the repository enough to make references accurate, self-audit the draft as a cold agent, create the issue through the available tracker, and report its URL or ID plus `READY`, `NEEDS WORK`, or `BLOCKED`.

An agent-ready issue stands alone and includes:

1. Problem and scope: outcome, in scope, and out of scope.
2. Evidence and context: sourced facts, labeled hypotheses and unknowns, prior or conflicting work, and the relevant base branch or commit when available.
3. Code references: concrete paths, symbols, and useful line anchors.
4. Done criteria: observable pass/fail behavior.
5. Approach: ordered implementation plan.
6. Verification plan: exact checks and expected evidence.
7. Dependencies and prerequisites.
8. Regression surface: adjacent behavior, call sites, shared helpers, and prior fixes to re-check.

For `issue check <id>`, validate these sections and referenced code against the current repository. Patch only objectively inferable gaps; stop for operator judgment when the scope or acceptance criteria require a real product decision. Report `READY`, `NEEDS WORK`, or `BLOCKED` with remaining gaps.

## Operator Verification

The coding agent owns verification by default. Exhaust available tools, fixtures, emulators, logs, screenshots, test hardware, credentials, and reasonable-duration runs before involving the operator.

Use `Operator verification required: <reason>` only when the agent cannot perform the decisive check or when doing so is genuinely inefficient, for example:

- physical interaction or inaccessible hardware that requires a person;
- a long experiment, training job, soak test, or scheduled observation better run by the operator.

Run the strongest practical smoke, shortened, simulated, or partial check first. Record its result and give the operator the exact full command or action, expected evidence, and pass/fail condition. Pending operator verification blocks merge and issue closure.

## `issue fix` Workflow

1. Read the issue and pass the readiness gate.
2. Create or switch to `<issue-id>-<short-kebab-scope>` from the configured base branch.
3. Implement only the scoped change. The root agent owns integration; delegate only disjoint work with explicit ownership.
4. Use project-specific skills and instructions for cheap iterative checks and focused pre-commit verification. Autofix is expected when the project workflow enables it; inspect and include its intended edits.
5. Run any additional issue-specific verification that is practical at this stage.
6. Commit in repository style and leave a clean tree containing only intended changes.
7. Report the branch, commits, verification, and any unresolved blocker. Do not merge or close the issue.

## Review Protocol

`rev make` creates a compact review packet without opening a PR: issue or scoped prompt, base and current branches, implementation summary, scoped diff, verification commands and results, known unrun checks, and any operator-only validation.

`rev peer` gives the initial packet to a fresh read-only reviewer. The reviewer validates scope, done criteria, changed-function call sites, adjacent behavior, regression surface, and verification sufficiency; reports major, minor, and nit findings with concrete evidence; and ends with `REVIEW STATUS: PASS` or `REVIEW STATUS: CHANGES REQUESTED`.

`rev resp` makes the author validate every finding:

- `fixed`: agree, fix, verify, and commit;
- `disputed`: cite concrete file/line or command evidence;
- `derailment`: validate that it cannot be fixed correctly in scope, create an agent-ready issue, and stop expansion of the current issue.

Send every response and updated review packet back to the same reviewer. An author dispute is never self-resolving. The reviewer checks the response evidence, fixes, and changed delta, then returns `PASS` or requests further changes for the current behavior. Do not reopen unchanged areas without concrete evidence newly exposed by the response or delta.

Repeat `resp → reviewer follow-up` until that reviewer returns `PASS`. After three response rounds without `PASS`, stop and report a review impasse for operator resolution; do not rotate reviewers merely to obtain a pass. Start over with a fresh reviewer only when the original reviewer is unavailable or the implementation has materially replaced the reviewed approach.

Reviewer prompt:

```text
Review this scoped diff as a blocking quality gate. Do not edit files.

Inputs: issue or scoped prompt, base branch, current branch, implementation summary, diff, verification summary, known unrun checks, and operator-only validation.
Validate the implementation against scope and done criteria. Check changed functions' call sites, adjacent behavior, regression risk, and whether verification matches the blast radius.
Report major, minor, and nit findings with concrete file/line or command evidence. Avoid generic praise and speculative follow-ups.
For a follow-up review, evaluate the author's responses and changed delta first. Reopen unchanged areas only when the response, delta, or concrete new evidence makes that necessary.
End with REVIEW STATUS: PASS or REVIEW STATUS: CHANGES REQUESTED.
```

## LFG Workflow

1. Run the readiness gate, then execute the `issue fix` workflow.
2. Run `rev make`, then `rev peer` with a fresh reviewer.
3. If changes are requested, run `rev resp`, commit fixes, and return the response and updated packet to the same reviewer for a delta-focused follow-up. Repeat within the review-round limit until that reviewer returns `PASS` for the current behavior.
4. Run the project-defined merge-boundary validation on the final tree, plus stronger issue-specific checks. Prefer one full gate after review; use cheaper checks while iterating.
5. Inspect autofix output. Commit intended mechanical changes; if validation exposes a behavioral fix, return it to the same reviewer for a delta-focused follow-up, then repeat final validation.
6. Stop before merge unless the tree is clean and scoped, validation passed, the reviewer returned `PASS`, no operator verification is pending, and the topic branch can fast-forward into the configured base.
7. Merge and preserve both refs:

```bash
git fetch origin
git switch <base>
git merge --ff-only origin/<base>
git merge --ff-only <branch>
git push origin <base> <branch>
```

8. Comment on the issue with the shipped summary, verification evidence, reviewer outcome, and merge SHA, then close it as completed. Close only the final deliverable of a multi-phase tracker.

If merge, push, or tracker access is unavailable, leave the topic branch committed, keep the issue open, and report the exact remaining commands. Also keep the issue open when work, review, validation, or operator verification remains incomplete; comment with the precise reason.

## Stop Conditions

Stop instead of guessing when the issue contradicts itself, acceptance requires an undocumented product decision, unrelated changes would be overwritten, independent review is unavailable, the review reaches its response-round limit without `PASS`, operator verification is pending, fast-forward merge is impossible, or a finding exposes a derailment outside the scoped deliverable.
