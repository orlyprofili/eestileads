# Eestileads Project Assessment

**Assessment date:** September 3, 2026  
**Market:** Home and general renovation contracting in the Greater Toronto Area (GTA)  
**Cost scope:** Live operating expenses only. Codex and development costs are excluded.

## Executive summary

This is a viable project. The software can be built and operated with very little ongoing intervention, and its non-advertising operating costs should be low. The central risk is not engineering: it is acquiring high-intent GTA traffic, establishing contractor credibility, responding quickly, and collecting enough real sales outcomes to optimize advertising effectively.

The current planning confidence levels are:

- **90–95%** confidence that a reliable, highly automated acquisition and lead-management system can be built.
- **80–90%** confidence that it can provide better ownership, visibility, response speed, and measurement than a typical third-party lead supplier.
- **35–45%** confidence that it can immediately beat **C$100 per genuinely exclusive, reachable, properly qualified lead** using paid acquisition.
- **65–75%** confidence that it can beat the incumbent on cost per signed job within 6–12 months, provided the contractor has credible work, responds promptly, records sales outcomes, and funds a sufficient advertising test.

The recommended strategy is to build an owned acquisition system while continuing to purchase incumbent leads temporarily. Both sources should be measured through the same funnel for approximately eight weeks before deciding whether to replace, supplement, or retain the current supplier.

## Current repository state

At the time of assessment, the repository contains only a minimal `README.md` and agent workflow skills. It has no product implementation.

Missing elements include:

- A product specification and explicit definition of a qualified lead.
- Contractor services, territory, minimum project values, capacity, and business rules.
- Application code, database schema, or administrative interface.
- Deployment configuration, automated tests, and continuous integration.
- Advertising, analytics, CRM, email, SMS, or telephony integrations.
- Privacy, consent, retention, and security policies.
- Monitoring, alerting, and operational documentation.

The repository is therefore approximately **0/10 implemented and 2/10 specified**. This is not a technical disadvantage: there is no legacy architecture to unwind, and the product can be designed around the actual acquisition experiment.

## Recommended product

The acquisition and feedback loop should be:

```text
Google Ads / Google Business Profile / SEO
                    ↓
        Service-specific landing page
                    ↓
        Consented estimate form or call
                    ↓
      Validation, deduplication, scoring
                    ↓
       Immediate SMS/email follow-up
                    ↓
             Contractor CRM
                    ↓
  Qualified → appointment → quote → won/lost
                    ↓
       Offline outcomes returned to Google
```

### Public website and landing pages

Build separate, focused landing experiences for services such as:

- Kitchen renovations.
- Bathroom renovations.
- Basement renovations.
- Additions.
- Full-home renovations.

Each page should contain real project photography, reviews, relevant licensing and insurance information, a clear service area, and a specific call to action.

The estimate form should collect only information needed to serve and qualify the homeowner:

- Postal code and municipality.
- Project type.
- Homeowner status.
- Approximate budget.
- Desired timing.
- Project description and optional photographs.
- Name, phone number, and email address.
- Explicit contact and privacy consent.

### Qualification

Qualification should use deterministic business rules for geography, project category, budget, timing, duplication, and obvious spam. AI can extract structured information, summarize the request, identify ambiguity, and draft follow-up questions, but it should not silently override the agreed qualification rules.

A possible initial definition is:

```text
Qualified lead = homeowner
              AND within approved service area
              AND supported renovation type
              AND budget at or above the contractor's minimum
              AND desired start date within the accepted window
              AND valid, non-duplicate contact information
```

The exact definition must match the definition used to evaluate the incumbent's C$100 leads.

### Follow-up and CRM

The system should:

- Send an immediate confirmation by SMS and email.
- Notify the contractor instantly with a concise project summary.
- Offer a calendar link or trigger a callback workflow.
- Track reachable, qualified, appointment, quoted, won, lost, value, and loss reason.
- Prompt the contractor with one-tap status updates when an outcome is missing.
- Record source and campaign attribution for every lead.
- Identify duplicates and invalid contacts.

An AI voice agent should not be part of the initial release. Home-renovation sales depend heavily on trust, and automated calling introduces additional consent, disclosure, and customer-experience risk. It can be evaluated later using real missed-call and qualification data.

### Advertising feedback

The system should send qualified and closed outcomes back to Google Ads using enhanced conversions for leads. Google recommends using qualified or converted lead goals for offline lead measurement and selecting an optimization stage that produces at least 15 monthly conversions. It also recommends frequent uploads of conversion outcomes.

This is the main performance advantage over optimizing for unqualified form submissions. Advertising should learn which searches produce credible, valuable projects rather than simply which visitors complete the easiest form.

Sources:

- [Google Ads conversion-value best practices](https://support.google.com/google-ads/answer/14791574?hl=en)
- [Google Ads enhanced conversions for leads](https://support.google.com/google-ads/answer/9888656?hl=en)
- [Google Ads offline conversion import guidance](https://support.google.com/google-ads/answer/10029210?hl=en)

## Automation model

The system can be highly automated without giving an agent unconstrained authority over advertising spend.

### Automatically performed

- Code validation, tests, deployment, and health checks.
- Form validation, spam filtering, deduplication, and lead scoring.
- Lead summaries and follow-up message drafting.
- SMS and email acknowledgements.
- Contractor notifications and missing-outcome reminders.
- Attribution capture and offline conversion uploads.
- Daily budget pacing and hard-limit enforcement.
- Performance summaries and anomaly detection.
- Safe search-term and negative-keyword recommendations.
- Pausing campaigns under explicit, pre-approved failure conditions.
- Dependency and application monitoring.

Google Ads supports automated rules for bids, budgets, campaign status, and alerts, and recommends maximum-budget safeguards when rules can increase spending.

Sources:

- [Google Ads automated rules](https://support.google.com/google-ads/answer/2497710?hl=en)
- [Google Ads scripts](https://support.google.com/google-ads/answer/188712?hl=en)

### Human-owned decisions and actions

The operator or contractor must still:

- Supply accurate business facts, project criteria, service areas, and capacity.
- Supply licensed project photography, reviews, credentials, and proof of insurance.
- Own and verify external accounts.
- Add a payment method and approve an advertising ceiling.
- Answer homeowners, attend appointments, and quote work.
- Record whether opportunities were quoted, won, or lost and their approximate value.
- Approve material changes to positioning, budget, or geographic scope.

The administrative burden can be reduced to exception handling and one-tap sales-status updates. It cannot be eliminated completely because the system cannot reliably infer what happened during offline homeowner conversations.

### External setup likely required

The contractor or operator will likely need accounts for:

- A `.ca` domain registrar.
- Cloudflare.
- Google Ads and a Google Ads manager account where needed.
- Google Business Profile.
- Twilio or an equivalent Canadian telephony provider.
- Resend or another transactional email provider.
- OpenAI API.

Google requires a developer token for direct Google Ads API access. Applying for one requires a manager account, an API access form, and acceptance of Google's terms. Initial automation can use native Google Ads rules and scripts while API access is prepared.

Source: [Google Ads API developer tokens](https://developers.google.com/google-ads/api/docs/api-policy/developer-token)

## Monthly operating-cost estimate

All estimates are in Canadian dollars, before HST. They exclude Codex and all development labour.

### Software and communications

| Expense | Expected monthly cost |
|---|---:|
| `.ca` domain, amortized | C$1–2 |
| Application, database, file storage, and scheduled jobs | C$7–40 |
| Transactional email | C$0 initially |
| Phone number, SMS, and basic call tracking | C$5–30 |
| Production OpenAI API usage | C$2–25 |
| Monitoring and miscellaneous usage | C$0–15 |
| **Software subtotal** | **C$15–110** |

A lean deployment can use Cloudflare Workers and associated storage services. Cloudflare's paid Workers plan begins at US$5 per month. Supabase Pro, currently starting at US$25 per month, is an optional managed-database alternative rather than a requirement. Resend's free tier includes 3,000 transactional emails per month. A normal `.ca` domain typically costs C$10–20 per year.

Sources:

- [Cloudflare Workers pricing](https://developers.cloudflare.com/workers/platform/pricing/)
- [Supabase pricing](https://supabase.com/pricing)
- [Resend pricing](https://resend.com/docs/knowledge-base/what-is-resend-pricing)
- [CIRA domain-cost guidance](https://www.cira.ca/en/resources/news/domains/how-much-does-a-ca-domain-cost/)

### Production AI usage

GPT-5.6 Sol currently costs US$4 per million input tokens, US$0.40 per million cached input tokens, and US$20 per million output tokens. Routine lead extraction and classification can use the much less expensive GPT-5.6 Luna, reserving Sol for difficult analysis and periodic campaign review.

At the expected initial lead volume, production AI should cost only a few to a few dozen Canadian dollars per month. Advertising, not model usage, will dominate operating costs.

Source: [Official OpenAI GPT-5.6 Sol documentation](https://developers.openai.com/api/docs/models/gpt-5.6-sol)

### Advertising and total budget

| Operating mode | Monthly advertising budget | Expected all-in monthly cost |
|---|---:|---:|
| Small pilot | C$1,500 | C$1,515–1,610 |
| Recommended initial learning period | C$3,000 | C$3,015–3,110 |
| Scaling | C$5,000 | C$5,030–5,150 |

The recommended initial advertising budget is **C$3,000 per month**, ideally maintained for an approximately eight-week learning period. That means planning for roughly **C$6,000 in total advertising spend across the initial two-month test**, plus C$30–110 per month for software and communications. After the test, the monthly advertising budget should be reduced, maintained, or increased based on cost per qualified opportunity, quote, and signed job.

At C$1,500 per month, the campaign may not generate enough qualified monthly outcomes to support reliable optimization, particularly when Google's recommended optimization threshold is at least 15 monthly conversions at the selected funnel stage.

## Acquisition economics

Available benchmarks should be treated as directional because campaign definitions and lead quality differ.

- One GTA renovation marketing provider estimates C$100–200 for a qualified Google estimate request.
- One documented GTA bathroom-renovation Meta campaign reported C$90.64 per lead.
- A broader 2025 home-services search benchmark reported US$165.67 per lead for general construction and contractors.

Sources:

- [GTA renovation marketing estimate](https://novaclickia.com/home-renovation-marketing)
- [GTA bathroom-renovation Meta case study](https://www.ayramarketing.ca/portfolio/bathroom-renovation-meta-ads-case-study)
- [2025 home-services search benchmark](https://localiq.com/blog/home-services-search-advertising-benchmarks/)

At C$3,000 of monthly advertising spend:

- C$100 per inquiry produces 30 inquiries.
- C$200 per inquiry produces 15 inquiries.
- If 60% qualify, the result is approximately 9–18 qualified leads.
- The incumbent nominally supplies 30 qualified leads for C$3,000.

Therefore, replacing the incumbent based only on advertised cost per lead would be premature. C$100 is attractive if each lead is exclusive, reachable, phone-qualified, in the service area, appropriate in budget and timing, and refundable when invalid.

The incumbent is much easier to beat if leads are shared, weakly screened, unresponsive, outside the target territory, non-refundable, or counted differently from the owned system's leads.

## Required experiment

The owned system and incumbent should operate concurrently for approximately eight weeks. Every opportunity should be measured through the same stages:

```text
Cost
  → inquiry
  → reachable homeowner
  → qualified project
  → appointment or site visit
  → quote
  → signed contract
  → expected gross profit
```

The primary business metric should be **cost per signed gross-profit dollar**, with cost per signed job as the simpler headline metric. Cost per form submission should be diagnostic only.

Before the comparison begins, the incumbent must answer:

1. Is each lead exclusive?
2. What exact criteria make a lead billable?
3. Is the homeowner phone-qualified or merely a form submission?
4. Are fake, duplicate, unreachable, and out-of-area leads refunded?
5. Where are the leads sourced?
6. What proportion historically become appointments, quotes, and signed jobs?

## Why the owned system can win

The main advantages are not merely lower hosting or AI costs:

- The contractor owns the advertising account, website, data, and conversion history.
- Leads are exclusive and received directly.
- Response can be immediate.
- Qualification can match the contractor's actual economics.
- Advertising can optimize using quoted and won outcomes.
- Service, location, keyword, and project-value performance becomes visible.
- Organic pages, reviews, referrals, and remarketing can lower blended acquisition cost over time.
- There is no permanent agency-management or lead-reseller margin.

GPT-5.6 Sol materially reduces the cost of building, analyzing, testing, and maintaining the system. It does not eliminate auction prices, low data volume, weak customer proof, or poor sales follow-up. A rudimentary incumbent can still have a meaningful advantage through accumulated conversion data, established pages, historical negative keywords, or access to shared leads.

## Compliance and launch gates

### Contractor licensing

The City of Toronto states that a Building Renovator licence is required for businesses providing or advertising renovation services in Toronto. As of the assessment date, the application and licence fees total C$495.12, and the trade examination fee is C$79.65. These are launch or annual business costs, not monthly software costs.

Source: [City of Toronto Building Renovators](https://www.toronto.ca/services-payments/permits-licences-bylaws/building-renovators/)

The contractor's status must be verified before advertising Toronto renovation services. Requirements in other GTA municipalities should also be checked for the selected service territory.

### Privacy and communications consent

PIPEDA requires meaningful consent for collecting, using, and disclosing personal information. The form must prominently explain why information is collected, who receives it, and how it will be used.

CASL places the burden of demonstrating electronic-message consent on the sender. Although a genuine service inquiry can create a period of implied consent, explicit recorded consent is the safer product design.

An inquiry within the preceding six months can also qualify as an existing business relationship for National Do Not Call List purposes, but general telemarketing and automated-dialing rules still apply. This project should focus on homeowner-initiated inbound contact rather than cold outreach.

Sources:

- [Office of the Privacy Commissioner: consent](https://www.priv.gc.ca/en/privacy-topics/business-privacy/collecting-personal-information/consent/)
- [CRTC CASL frequently asked questions](https://crtc.gc.ca/eng/com500/faq500.htm/)
- [National Do Not Call List exemptions](https://www.lnnte-dncl.gc.ca/en/Organization/Exemptions)

## Recommendation

Proceed with the project as an **owned acquisition and measurement experiment**, not on the assumption that it will immediately produce leads below C$100.

The first implementation milestone should include:

1. A precise qualified-lead specification.
2. Service-specific landing pages and a consented estimate form.
3. Validation, deduplication, qualification, and instant routing.
4. A minimal contractor CRM with outcome tracking.
5. Source attribution and enhanced conversion support.
6. Hard advertising-budget controls and operational alerts.
7. Identical tracking for incumbent leads.
8. Automated tests, deployment, monitoring, backup, and recovery documentation.

Once the parallel test has enough outcomes, the decision should be based on cost per qualified opportunity, quote, signed job, and gross profit—not on raw lead volume.
