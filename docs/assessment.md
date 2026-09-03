# Eestileads Project Assessment

**Assessment date:** September 3, 2026

**Market:** Home and general renovation contracting in the Greater Toronto Area

**Cost scope:** Live operating expenses only; development labour and Codex costs are excluded

**Decision being assessed:** Whether to build an owned lead-generation system for one contractor, given credible done-for-you alternatives

## Bottom line

The project is technically straightforward, but a full replacement for ContractorLaunch is not yet the rational first move.

ContractorLaunch publicly offers exclusive, qualified homeowner leads for $99 each and says its team handles advertising, CRM setup, automated follow-up, and booking. Whether media spend is included in that price still needs written confirmation. RenoLeadz publicly offers a similar Canadian service for C$125–150 per exclusive, verified lead with advertising explicitly included. Those prices are competitive with, and may be below, the raw paid-media cost of generating a comparable renovation lead independently.

That changes the original thesis:

- There is no strong evidence that a custom paid-acquisition system will immediately produce qualified leads for less.
- GPT-5.6 Sol can make the software inexpensive to build and maintain, but it cannot remove Google and Meta auction costs, create contractor credibility, or make homeowners answer the phone.
- The immediate opportunity is to measure the incumbent accurately, preserve business data, improve follow-up, and build contractor-owned assets.
- Independent paid advertising should be a gated experiment only if incumbent results are weak, contract terms are unattractive, capacity requires another source, or ownership has strategic value.
- For one contractor, a lean measurement and owned-asset system can be rational. A large standalone lead platform is unlikely to be justified unless it later serves several contractors.

The recommended course is therefore **measure, own, and selectively test**—not “replace the $100 lead supplier.”

## Current repository state

The repository currently contains a minimal README and this assessment; there is no application implementation. It is approximately **0/10 implemented**. The revised business requirements are now materially clearer, but the contractor-specific inputs and evidence listed in Phase 0 are still missing.

That is a useful stopping point. Building the earlier full acquisition design before inspecting ContractorLaunch data would risk automating an unproven answer to the wrong problem.

## Revised confidence assessment

These ranges are judgmental decision priors, not statistically derived forecasts. The largest unknown is the contractor’s actual funnel: delivered leads, reachable homeowners, quotes, signed work, contract value, and gross profit.

| Outcome | Current confidence | Interpretation |
|---|---:|---|
| Build a reliable, highly automated lead intake and measurement system | **90–95%** | Normal product engineering with manageable integrations |
| Improve attribution, response speed, record keeping, and data ownership | **85–95%** | High confidence if the contractor consistently records outcomes |
| Create useful contractor-owned web, review, referral, and organic assets | **75–90%** | Useful even if ContractorLaunch remains the primary paid source |
| Improve total sales performance without replacing ContractorLaunch | **60–75%** | Better routing and follow-up can help, but execution by the contractor remains decisive |
| Independently generate paid qualified leads at C$150 or less within six months | **35–55%** | Plausible, but GTA competition and low data volume are meaningful constraints |
| Match or beat ContractorLaunch’s advertised $99 qualified-lead price using paid media alone | **15–30%** | Low until currency, inclusions, qualification, and actual lead quality are known |
| Beat ContractorLaunch on cost per signed gross-profit dollar within 6–12 months | **30–50%** | Possible through better targeting and ownership, but the prior 65–75% estimate was too optimistic |
| Economically justify fully replacing a well-performing ContractorLaunch account within 12 months | **25–40%** | Replacement is not valuable merely because custom software can be built |

These probabilities should move materially after the first data audit:

- If ContractorLaunch is C$99 all-in, the leads are exclusive, at least 70% are reachable, at least 30% become real quote opportunities, and at least 10% sign, retaining it is probably the better paid channel.
- If the price is US$99, media is additional, leads fail the agreed criteria, exclusivity is weak, or fewer than roughly 5–8% sign despite sound sales follow-up, an owned paid test becomes substantially more attractive.
- If there is no reliable outcome data, there is no defensible basis for declaring either system cheaper.

## What the competitive landscape changes

The market is crowded, but it is not necessarily “involution.” Competition has compressed basic lead-generation work into standardized offers: ads, landing pages, CRM, text follow-up, and scheduling. Vendors can spread creative development, campaign knowledge, software, and operational staff across many contractors. A custom system for one contractor does not receive that scale advantage.

The remaining opportunities are harder and more contractor-specific:

- Better project and territory selection.
- Stronger portfolio evidence, reviews, and local reputation.
- Faster human response and better estimating.
- Accurate source-to-sale attribution.
- Optimization for signed gross profit instead of cheap forms.
- Contractor ownership of the domain, advertising accounts, audiences, and customer data.
- Organic search, Google Business Profile, referrals, and repeat work that lower blended acquisition cost over time.

Software can support all of these, but it is not itself the scarce advantage. The contractor’s proof, sales process, capacity, and job economics are.

## Competitive analysis

Public vendor claims are not audited results. The signed agreement, invoices, account permissions, raw lead exports, and actual outcomes should control the decision.

### Comparison

| Service | Public commercial model | Lead competition | What appears included | Ownership and principal risk |
|---|---|---|---|---|
| **ContractorLaunch** | $99 per qualified homeowner; no published setup fee, retainer, or long contract | Claims exclusive | Advertising, creative testing, CRM, AI follow-up, nurturing, and booking | Most attractive direct benchmark; currency, media inclusion, credit rules, and exit ownership must be verified |
| **RenoLeadz** | C$450/3, C$650/5, C$1,250/10; C$125–150 per lead plus tax | Claims exclusive | Advertising, phone verification, screening, tracking, and follow-up | Clearer Canadian all-in pricing; vendor controls the lead engine and portability is unclear |
| **HomeStars** | Contractor pays when shortlisted and receives homeowner contact information; public price is not standardized | Up to three professionals | Marketplace matching and professional profile | Shared opportunity; professional agreement does not guarantee quality, accuracy, volume, or work |
| **Bark** | Variable credits disclosed before the contractor contacts a lead | Up to five professionals | Marketplace matching and contact details | Shared, variably priced demand; remedies focus on invalid details rather than low intent |
| **CoreLaunch** | C$99/month plus 12.5% of ad spend; contractor funds media directly | Contractor-specific campaigns | Website, campaigns, tracking, CRM delivery, SMS, and optimization | Clear ownership model, but contractor bears all media-performance risk |
| **RenovationFind** | Price not publicly disclosed | Not established publicly | Manually pre-qualified projects and contractor portal | Cannot compare economically without a quote and written terms |
| **RenoAssistance** | Success fee only when a contractor wins; up to three contractors bid | Shared | Qualification and project matching | Public service areas currently do not list Toronto, so it is not a direct GTA option |

### ContractorLaunch: the benchmark

ContractorLaunch says it:

- Charges $99 for a qualified homeowner meeting client-defined criteria.
- Generates the lead under the contractor’s brand and does not share it.
- Sets up advertising, automations, and a CRM.
- Tests creative and uses AI to text, nurture, schedule, and remind leads.
- Has no setup fee, monthly retainer, or lock-in contract.

Sources: [ContractorLaunch homepage and pricing](https://contractorlaunch.io/), [services](https://contractorlaunch.io/services), and [terms](https://contractorlaunch.io/tandc).

If that is C$99 including media, and billing occurs only for an exclusive homeowner who actually meets meaningful budget, territory, project, and timing criteria, it is a strong offer. A custom system should not assume it can undercut it.

The public materials nevertheless contain issues requiring written clarification:

1. **Currency:** The site displays “$99” but does not clearly label CAD or USD.
2. **Media:** The simple price presentation implies a bundled service, but the public page does not explicitly say whether the contractor ever pays platform ad spend separately.
3. **Billable lead:** Client criteria define qualification, but the terms say that qualification does not guarantee availability, an appointment, financing, or a sale.
4. **Remedy:** The homepage says non-matching leads are not charged; the general terms say payments are non-refundable unless agreed otherwise and quality concerns are handled through credits in the Client Agreement.
5. **Ownership:** The homepage says the system is built in the contractor’s name and owned for life; section 8 of the terms says ContractorLaunch retains its ads, templates, automations, software configurations, funnels, copy, graphics, and internal processes and grants a limited licence during the active relationship.
6. **Exit:** Public material does not establish what happens to the CRM instance, workflows, phone numbers, domains, pixels, audiences, campaign history, creative, or data after cancellation.

None of those points proves the service is poor. They mean the buddy’s executed Service Agreement is essential evidence.

### RenoLeadz: the clearest pay-per-lead alternative

RenoLeadz publishes Canadian prices of:

- C$450 plus tax for 3 exclusive leads: C$150 each.
- C$650 plus tax for 5 exclusive leads: C$130 each.
- C$1,250 plus tax for 10 exclusive leads: C$125 each.

It says media, campaign management, phone verification, screening, tracking, and follow-up are included, and invalid leads are replaced. This establishes that C$125–150 is a plausible retail market price for small bundles of vendor-generated exclusive leads—not merely an arbitrary quote from ContractorLaunch.

Source: [RenoLeadz pricing and FAQ](https://renoleadz.com/).

### HomeStars and Bark: different products

HomeStars does use a pay-for-connection model, but it is not directly equivalent to ContractorLaunch. A homeowner can shortlist up to three professionals. HomeStars’ professional agreement disclaims guarantees concerning lead volume, quality, customer intent, information accuracy, and resulting work.

Sources: [HomeStars professional registration](https://www.homestars.com/pro/register), [professional agreement](https://www.homestars.com/assets/en_CA/HomeStars-Professional-User-Agreement-January-2025.pdf), and [homeowner matching process](https://www.homestars.com/blog/hiring-pros-on-homestars).

Bark charges a variable number of credits to contact a matched homeowner, and up to five professionals can respond. Its credit-return policy mainly addresses invalid or duplicate contact data, tests, and minors; a legitimate but unresponsive homeowner is a different problem.

Sources: [Bark Canada pricing](https://www.bark.com/en/ca/sellers/pricing/), [lead pricing](https://help.bark.com/hc/en-ca/articles/18043745477788-Understanding-lead-pricing), [response limits](https://help.bark.com/hc/en-ie/articles/28463866842652-How-many-responses-can-a-customer-receive), and [credit returns](https://help.bark.com/hc/en-ca/articles/27458342155932-Refunds-vs-Credit-Returns).

These marketplaces can supplement demand or reputation, but their shared connections should not be compared with an exclusive qualified lead at the same nominal price.

### CoreLaunch: the buy-versus-build comparison

CoreLaunch advertises C$99 per month plus 12.5% of ad spend, with media charged directly to the contractor. It says the contractor keeps the domain, website, advertising accounts, reports, and leads.

At C$1,000 of media, the public formula totals C$1,224 before usage charges. At C$2,000 it totals C$2,349. The custom system could avoid part of that platform fee, but not the C$1,000 or C$2,000 media cost.

Source: [CoreLaunch pricing and ownership model](https://corelaunch.ca/).

### Competitive conclusion

The order of preference is now conditional:

1. **Keep ContractorLaunch** if its true all-in signed-job economics are good.
2. **Add independent measurement and owned assets** regardless of which paid source wins.
3. **Use RenoLeadz as a price and quality challenger** if ContractorLaunch terms or results are weak.
4. **Use HomeStars or Bark only as separately measured supplemental sources.**
5. **Test owned paid acquisition only after a specific failure or strategic need is identified.**
6. **Build a multi-contractor product only if the intent changes from helping a buddy to operating a lead-generation business.**

## Economics that matter

### Do not optimize for cost per form

The comparable funnel is:

    spend
      → delivered lead
      → reachable homeowner
      → qualified project
      → appointment or site visit
      → quote
      → signed contract
      → expected gross profit

The primary metric should be **acquisition cost divided by attributable expected gross profit**. Cost per signed job is the simpler secondary metric. Raw cost per lead is useful only when every source uses the same definition.

If the ContractorLaunch price is C$99 per billable lead, customer-acquisition cost changes sharply with close rate:

| Lead-to-signed-job rate | Leads per signed job | Acquisition cost |
|---:|---:|---:|
| 5% | 20 | $1,980 |
| 8% | 12.5 | $1,238 |
| 10% | 10 | $990 |
| 15% | 6.7 | $660 |
| 20% | 5 | $495 |

If a typical signed project contributes C$8,000 after direct labour, materials, and subcontractors, C$990 consumes about 12% of gross profit and is attractive. C$1,980 consumes about 25% and is borderline. This is why lead quality and the contractor’s sales process matter more than whether the sticker price is $99 or $125.

Practical channel guardrails:

- **Green:** Acquisition consumes at most 10–15% of attributable gross profit.
- **Yellow:** 15–25%; continue only if results are measured and capacity supports growth.
- **Red:** More than 25%, or no reliable gross-profit attribution; diagnose or pause.

### What the $3,000 figure actually means

C$3,000 is not a required software bill or a permanent minimum. It was previously proposed as a monthly Google Ads learning budget. That recommendation is withdrawn as the default.

At ContractorLaunch’s displayed price, $3,000 is approximately the purchase cost of 30 billable leads. It may be a reasonable monthly acquisition budget for a contractor that can absorb and close that volume, but it is not a prerequisite for this project.

The revised spending stages are:

| Stage | Incremental monthly cost | Purpose |
|---|---:|---|
| Audit current source | C$0 beyond existing invoices | Determine whether there is a problem worth solving |
| Measurement and owned assets | C$15–100 | Track outcomes; operate site, forms, messaging, and reporting |
| Small owned paid pilot | C$750–1,500 media plus C$15–100 | Directional test only, triggered by a clear hypothesis |
| Proven scaling | C$1,500–3,000+ media plus C$15–150 | Only after signed-job economics satisfy the guardrails |

An owned paid test should run for 8–12 weeks or until it has at least 20 genuinely qualified leads. That is enough for a directional decision, not high statistical confidence. With low contractor volume, accumulating a robust comparison may take longer.

There is no guaranteed “cruising altitude.” C$600–2,200 per month remains a plausible affordability range for a single established contractor, but the rational level could be:

- Near zero paid spend when referrals, reviews, and organic traffic fill capacity.
- Roughly C$500–1,500 when only a few additional projects are needed.
- C$1,500–3,000 or more when close rates, gross profit, and crew capacity support deliberate growth.

Paid spend does not disappear through optimization. It only shrinks when the contractor needs less volume or unpaid channels replace it.

### Contractor size and affordability

Canadian government data for residential building SMEs reports average annual revenue around C$533,000. In 2024, 76.3% were profitable; the overall category’s average net margin was 10.4%, while profitable firms averaged about C$102,000 in net profit. The category includes remodelers and other residential builders, so it is a planning reference rather than a profile of this buddy’s business. Owner wages may already appear in expenses, meaning accounting profit is not identical to operator take-home.

Source: [Canadian Industry Statistics: residential building construction](https://www.ised-isde.canada.ca/app/ixb/cis/performance/23611?lang=eng).

| Annual revenue | C$600/month | C$1,200/month | C$2,200/month | Assessment |
|---:|---:|---:|---|
| C$150,000 | 4.8% of revenue | 9.6% | 17.6% | Even the low end is material |
| C$250,000 | 2.9% | 5.8% | 10.6% | Stay low unless signed-job return is proven |
| C$400,000 | 1.8% | 3.6% | 6.6% | Low to middle range can be defensible |
| C$500,000 | 1.4% | 2.9% | 5.3% | C$600–1,200 is reasonable with attribution |
| C$750,000 | 1.0% | 1.9% | 3.5% | Most of the range is affordable if capacity exists |
| C$1,000,000 | 0.7% | 1.4% | 2.6% | Upper range is modest relative to revenue |

These percentages are downside context, not ROI calculations. Profitable acquisition creates revenue and gross profit, and spending that replaces current lead purchases is not fully incremental.

## Is this rational for one contractor?

Yes, if “this” means a lean contractor-owned measurement, intake, follow-up, website, and data layer. That system has value even when a vendor supplies the leads.

Probably not yet, if “this” means recreating an agency, ad engine, CRM, AI appointment setter, SEO program, and operational support solely to save a few dollars against a credible $99–150 exclusive lead.

For a single contractor:

- Software savings are small.
- Campaign volume is low, so learning is slow.
- One contractor’s seasonality and capacity can interrupt experiments.
- The builder becomes the unpaid marketing operator unless monitoring and escalation are designed carefully.
- A vendor can amortize people, creative, tooling, and campaign failures across many customers.

Serving several contractors improves the platform economics and data volume, but creates a different business with sales, onboarding, support, territory conflicts, privacy obligations, billing disputes, and potential competition between clients. Multi-contractor expansion should not be assumed merely to justify the code.

The rational single-contractor product is therefore deliberately narrow. Expand only after the buddy’s measured results reveal a repeated problem.

## Revised product scope

### Phase 0: evidence before code

Obtain the ContractorLaunch agreement, recent invoices, and at least 60–90 days of raw lead and sales data. Record:

1. Currency, tax, media charges, minimum purchase, caps, and cancellation.
2. Exact billable-lead criteria and the remedy window.
3. Exclusivity and source.
4. Delivered, credited, invalid, duplicate, and unreachable counts.
5. Appointments, quotes, wins, losses, contract value, and expected gross profit.
6. Response time and number of follow-up attempts.
7. Account, domain, phone-number, pixel, creative, workflow, and data ownership.

If historical records are poor, start prospective tracking before changing suppliers.

### Phase 1: minimum vendor-independent measurement layer

Build:

- A canonical lead ledger importing or receiving every source.
- Standard funnel statuses and loss reasons.
- Source, campaign, cost, and consent records.
- One-tap contractor updates for reached, appointment, quoted, won, and lost.
- Contract value and expected gross-profit fields.
- Duplicate detection and basic validation.
- Immediate alerts and missed-outcome reminders.
- Weekly source scorecards.
- Export, backups, access controls, and audit history.

Start with the smallest implementation that produces trustworthy data. If ContractorLaunch already supports usable exports, a scheduled import and a compact outcome interface may be enough; do not recreate its entire CRM. This is the highest-confidence investment because it answers the business question without first taking media risk.

### Phase 2: contractor-owned demand assets

Build or improve:

- The contractor’s domain and website.
- Service-specific pages for kitchens, bathrooms, basements, additions, and full-home renovations.
- Real project photographs, proof, reviews, credentials, and service-area detail.
- Google Business Profile, review collection, referral capture, and call/form attribution.
- A short, consented estimate form collecting postal code, project, budget, timing, ownership, and contact details.

These assets can coexist with ContractorLaunch. Confirm the agreement before reusing vendor-created copy, creative, workflows, or configurations.

### Phase 3: optional paid experiment

Run an owned campaign only if Phase 0 identifies a reason:

- Incumbent signed-job acquisition cost is outside the guardrail.
- Lead criteria or remedies are unacceptable.
- Capacity requires incremental volume.
- The contractor needs account and data independence.
- A specific service or municipality appears underserved.

Use one narrow service and territory, a C$750–1,500 monthly cap, deterministic qualification, fast human follow-up, and the same scorecard as the incumbent. Do not launch five services across the entire GTA at once.

### Phase 4: scale or stop

Scale only when the owned source:

- Produces reachable, properly qualified homeowners.
- Generates quote opportunities, not merely forms.
- Meets the gross-profit acquisition guardrail.
- Does not overwhelm estimating or production capacity.
- Continues to perform after invalid leads and operator time are counted.

Otherwise retain the better vendor, improve organic assets, or pause paid acquisition.

## Automation model

The system can automate:

- Intake validation, deduplication, attribution, and routing.
- Immediate SMS and email acknowledgements.
- Contractor alerts and follow-up reminders.
- Lead summaries and deterministic qualification support.
- Cost ingestion and funnel reporting.
- Missing-outcome prompts.
- Offline qualified and won-conversion uploads.
- Budget pacing, hard caps, anomaly alerts, deployment, tests, backups, and monitoring.

The contractor still must:

- Provide accurate services, territory, capacity, budgets, project proof, and credentials.
- Own and verify external accounts and approve spending limits.
- Respond to homeowners, attend visits, estimate, sell, and deliver work.
- Record outcomes and approximate job economics.
- Approve material changes to offer, budget, or service area.

An AI voice agent is not recommended initially. Renovation sales are trust-sensitive, and automated calling introduces consent, disclosure, and customer-experience risk. AI is useful for extraction, summaries, follow-up drafting, anomaly review, and periodic analysis. Qualification and spend controls should remain explicit and auditable.

Google supports enhanced conversions for leads and recommends optimizing to a downstream stage with sufficient volume; its guidance uses at least 15 monthly conversions as a practical threshold. Low-volume contractors may therefore need to optimize to a qualified or appointment stage rather than signed jobs.

Sources: [Google Ads enhanced conversions for leads](https://support.google.com/google-ads/answer/9888656?hl=en), [offline conversion guidance](https://support.google.com/google-ads/answer/10029210?hl=en), and [conversion-value best practices](https://support.google.com/google-ads/answer/14791574?hl=en).

## Operating costs

All figures are Canadian dollars before HST unless a vendor displays an unspecified dollar amount.

### Owned software

| Expense | Expected monthly cost |
|---|---:|
| Domain, amortized | C$1–2 |
| Application, database, storage, and jobs | C$7–40 |
| Transactional email | C$0 initially |
| Phone number, SMS, and call tracking | C$5–30 |
| Production AI | C$1–15 initially |
| Monitoring and miscellaneous usage | C$0–15 |
| **Software subtotal** | **C$15–100** |

The exact infrastructure choice may move this modestly, but it will not change the business case. Cloudflare Workers begins at US$5 per month, Supabase Pro is an optional US$25 managed tier, and Resend offers a small free email tier.

Sources: [Cloudflare Workers pricing](https://developers.cloudflare.com/workers/platform/pricing/), [Supabase pricing](https://supabase.com/pricing), [Resend pricing](https://resend.com/docs/knowledge-base/what-is-resend-pricing), and [CIRA domain-cost guidance](https://www.cira.ca/en/resources/news/domains/how-much-does-a-ca-domain-cost/).

GPT-5.6 Sol is currently US$4 per million input tokens, US$0.40 per million cached input tokens, and US$20 per million output tokens. Routine classification can use GPT-5.6 Luna at much lower rates, with Sol reserved for difficult reviews. At single-contractor volume, AI should remain a minor line item.

Source: [official OpenAI GPT-5.6 Sol documentation](https://developers.openai.com/api/docs/models/gpt-5.6-sol).

### Total acquisition spend

Total monthly cost is:

    owned software
      + vendor lead invoices
      + any direct advertising
      + optional call or messaging usage

Do not silently add a C$3,000 media budget to a $99 pay-per-lead program. Verify whether the vendor price already includes media. In a hybrid test, explicitly reduce or cap one source so the contractor does not buy more opportunities than can be answered, quoted, and delivered.

## Compliance and launch gates

The City of Toronto states that businesses providing or advertising building-renovation services require a Building Renovator licence. The contractor’s status should be verified before advertising, along with requirements in every municipality served.

Source: [City of Toronto Building Renovators](https://www.toronto.ca/services-payments/permits-licences-bylaws/building-renovators/).

The estimate form must use meaningful privacy and contact consent. PIPEDA requires clarity about collection, use, and disclosure of personal information. CASL places the burden of proving electronic-message consent on the sender. Inbound homeowner inquiries are safer than cold outreach, but consent and suppression records are still required.

Sources: [Office of the Privacy Commissioner on consent](https://www.priv.gc.ca/en/privacy-topics/business-privacy/collecting-personal-information/consent/), [CRTC CASL FAQ](https://crtc.gc.ca/eng/com500/faq500.htm), and [National Do Not Call List exemptions](https://www.lnnte-dncl.gc.ca/en/Organization/Exemptions).

## Decision rule

Proceed now with the data audit. Then implement only the measurement gaps and contractor-owned assets that the audit shows are missing.

Do **not** commit to a default C$3,000 monthly owned-ad program or assume ContractorLaunch should be replaced. After enough reliable outcomes exist, choose the source with the best cost per signed gross-profit dollar, subject to acceptable ownership, contract, consent, and lead-quality terms.

The project succeeds if it gives the contractor a provably better and more durable acquisition position. It does not need to displace a good vendor to be worthwhile.
