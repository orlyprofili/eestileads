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

The following are temporary launch and scaling scenarios, not a recommendation to spend C$3,000 indefinitely.

| Operating mode | Monthly advertising budget | Expected all-in monthly cost |
|---|---:|---:|
| Small pilot | C$1,500 | C$1,515–1,610 |
| Recommended initial learning period | C$3,000 | C$3,015–3,110 |
| Scaling | C$5,000 | C$5,030–5,150 |

The recommended initial advertising budget is **C$3,000 per month**, ideally maintained for an approximately eight-week learning period. That means planning for roughly **C$6,000 in total advertising spend across the initial two-month test**, plus C$15–110 per month for software and communications. After the test, the monthly advertising budget should be reduced, maintained, or increased based on cost per qualified opportunity, quote, and signed job.

At C$1,500 per month, the campaign may not generate enough qualified monthly outcomes to support reliable optimization, particularly when Google's recommended optimization threshold is at least 15 monthly conversions at the selected funnel stage.

### Expected steady-state range

For a single small contractor, the expected cruising range after the initial experiment is approximately **C$600–2,200 per month in total**, consisting of C$15–110 of software and communications and roughly C$500–2,100 of advertising. This range is not guaranteed to produce a particular number of leads. It is an affordability range that must be constrained by contractor revenue, available capacity, and signed-job economics.

Paid advertising does not naturally disappear as the campaign learns. The budget can shrink or be paused only when organic search, Google Business Profile, reviews, referrals, or existing demand supply enough work. Paid lead volume will normally fall when paid spend falls.

### When marketing spend is affordable

Canadian government data for residential building SMEs reports average annual revenue of approximately C$533,000, with 76.3% of businesses profitable. The broader residential-building category—which includes remodelers as well as other residential contractors—reported an average net margin of 10.4% in 2024. Profitable firms averaged approximately C$532,000 of revenue and C$102,000 of net profit. Owner salary may already be included in expenses, so reported net profit is not necessarily the owner's entire compensation.

Source: [Canadian Industry Statistics: residential building construction](https://www.ised-isde.canada.ca/app/ixb/cis/performance/23611?lang=eng)

The table below compares the proposed steady-state marketing range with a business at different revenue levels. "Benchmark profit" applies the reported 10.4% industry-wide net margin only as a planning reference. The marketing share shows how large the annual marketing commitment is relative to that profit pool if the spend produces no incremental profit and does not replace existing lead purchases.

| Annual contractor revenue | Benchmark profit at 10.4% | C$600/month marketing | C$1,200/month marketing | C$2,200/month marketing | Practical interpretation |
|---:|---:|---:|---:|---:|---|
| C$150,000 | C$15,600 | 46% of benchmark profit | 92% | 169% | C$600 is already material; higher spend is dangerous without immediate, measured wins. |
| C$250,000 | C$26,000 | 28% | 55% | 102% | Stay near the low end; C$2,200 can consume an entire typical profit year. |
| C$400,000 | C$41,600 | 17% | 35% | 63% | C$600–1,200 is defensible; C$2,200 should require proven signed-job returns. |
| C$500,000 | C$52,000 | 14% | 28% | 51% | C$600–1,200 is a reasonable base; C$2,200 remains an aggressive growth budget. |
| C$750,000 | C$78,000 | 9% | 18% | 34% | Most of the cruising range is affordable if capacity and attribution are sound. |
| C$1,000,000 | C$104,000 | 7% | 14% | 25% | C$2,200 is comparatively modest, subject to campaign profitability. |

These percentages do **not** mean that marketing literally reduces existing profit by the full amount. A successful campaign creates revenue and gross profit, while advertising that replaces C$100 incumbent leads is not entirely incremental spending. The table is a downside guardrail showing how damaging the commitment becomes when it fails to generate work.

For this project, the operating zones should be:

- **Green:** Marketing is no more than roughly 3% of annual revenue, acquisition cost is no more than 15% of attributable gross profit, and the contractor has capacity for the resulting work.
- **Yellow:** Marketing is 3–6% of annual revenue or consumes 15–30% of attributable gross profit. Continue only with reliable quote and signed-job tracking.
- **Red:** Marketing exceeds 6% of annual revenue, consumes more than 30% of attributable gross profit, or is being funded without enough cash runway to complete the test. Reduce or pause unless this is an explicitly time-limited launch investment.

Examples:

- A C$250,000 contractor spending C$2,200 per month allocates 10.6% of revenue to this channel before software, which is too aggressive for steady-state operation.
- A C$500,000 contractor spending C$1,200 per month allocates 2.9% of revenue, which is reasonable if it produces attributable contracts.
- A C$750,000 contractor spending C$2,200 per month allocates 3.5% of revenue, which can be rational but still needs measurable acquisition returns.

The final control is job-level economics. If a signed job contributes C$8,000 of gross profit after direct labour, materials, and subcontractors, a customer-acquisition cost around C$800–1,200 is healthy for this project. C$2,400 or more would consume at least 30% of that gross profit and should normally trigger a campaign or sales-process review.

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

## Competitive analysis

**Research date:** September 3, 2026

The contractor's current supplier is ContractorLaunch. This is an important clarification because ContractorLaunch is not merely a marketplace like HomeStars or Bark. It publicly describes a done-for-you, performance-priced acquisition system that creates exclusive leads under the contractor's brand, supplies a CRM, uses AI for follow-up and booking, and charges $99 per qualified homeowner.

All prices, features, lead-quality claims, and outcome claims below come from public vendor materials unless stated otherwise. They should not be treated as audited performance. The signed client agreement, invoices, account permissions, and actual lead outcomes are more authoritative than marketing pages.

### Market categories

The competitors fall into three different categories:

1. **Shared marketplaces:** HomeStars and Bark attract homeowners to a marketplace and charge contractors to access or connect with them. Several contractors may compete for the same project.
2. **Performance lead vendors:** ContractorLaunch and RenoLeadz advertise and qualify leads, charge for delivered leads, and publicly promise exclusivity.
3. **Owned-account marketing platforms:** CoreLaunch charges software and management fees while the contractor pays advertising platforms directly and retains its accounts and data.

Comparing cost per lead across these categories without considering exclusivity, qualification, media spend, ownership, and refund rules is misleading.

### Summary matrix

| Service | Model and public pricing | Exclusive? | Qualification and remedy | Contractor ownership | Main concern |
|---|---|---|---|---|---|
| **ContractorLaunch** | $99 per qualified homeowner; public site says no setup fee, monthly retainer, or long contract | Publicly claims yes | Criteria are set with the client; homepage says non-matching leads are not charged, while public terms say credits are governed by the client agreement | Homepage says ads, automations, and CRM are built under the contractor's name and owned for life | Public ownership and refund claims conflict with general terms; currency and whether ad spend is included should be confirmed in writing |
| **RenoLeadz** | C$450 for 3 leads, C$650 for 5, or C$1,250 for 10; effective C$125–150 per lead; advertising included | Publicly claims yes | OTP phone verification and quality screening; invalid leads are replaced rather than refunded | Vendor runs the lead engine, landing pages, CRM, and follow-up; portability is not established on the public page | More expensive than ContractorLaunch if lead quality is equivalent; claims are self-published and require a controlled test |
| **HomeStars** | No general public price list; contractor pays a fee when shortlisted and receives homeowner contact details | No; homeowner can connect with up to three pros | Matching is based on project and profile; professional agreement expressly disclaims guarantees of lead quality, intent, accuracy, volume, or a resulting job | Profile and reputation live on HomeStars; the contractor does not own the marketplace demand source | Contractor may pay while still competing against other shortlisted pros |
| **Bark** | Free account; variable credit charge disclosed before contacting each lead | No; as many as five professionals can respond | Customer answers matching questions; credit returns within 14 days are limited mainly to invalid contact information, duplicates/tests, or minors | Contractor receives contact details but does not own the marketplace or acquisition channel | Shared competition, variable pricing, credit expiry, and limited remedies for merely unresponsive or low-intent prospects |
| **CoreLaunch** | C$99/month plus 12.5% of ad spend; contractor pays Google and Meta directly | Yes, because campaigns run for the contractor | Automated site, campaigns, lead response, tracking, and optimization; no promised fixed lead price | Publicly says contractor keeps the domain, site, ad accounts, reports, and leads | Contractor bears media-performance risk; total cost depends on ad spend and actual conversion rate |

### ContractorLaunch

ContractorLaunch is the most relevant competitor and the benchmark this project must beat. Its public offer includes:

- $99 per qualified homeowner.
- Exclusive leads generated under the contractor's brand.
- No setup fee, monthly retainer, or long-term contract.
- Meta advertising, creative testing, CRM implementation, AI texting, nurturing, reminders, and calendar booking.
- Qualification based on project type, budget, service area, and other client criteria.

Sources:

- [ContractorLaunch homepage and pricing](https://contractorlaunch.io/)
- [ContractorLaunch services](https://contractorlaunch.io/services)
- [ContractorLaunch terms and conditions](https://contractorlaunch.io/tandc)

If the $99 is Canadian dollars, includes all media spend, applies only to genuinely qualified exclusive homeowners, and has no minimum monthly purchase, this is a very strong offer. The custom system should not be expected to beat it immediately on cost per qualified lead: published GTA paid-acquisition estimates alone are commonly around C$100–200 per estimate request before custom software overhead.

The public materials leave several material questions unresolved or inconsistent:

- **Currency:** The public page displays `$99` without clearly identifying CAD or USD.
- **Advertising cost:** The page presents $99 as the simple price and says there are no retainers or setup fees, but it does not explicitly state whether media spend is included or separately charged.
- **Qualification:** The public terms say criteria are established by the client but that qualification does not guarantee an appointment, sale, approval, financing, or customer availability. Lead-credit rules exist only in the client agreement.
- **Bad leads:** The homepage says a lead that does not match the criteria is not charged. The public terms say payments are generally non-refundable and quality concerns, where applicable, are resolved through credits under the client agreement.
- **Ownership:** The homepage and services page say the contractor owns the system and CRM for life. Section 8 of the public terms says ContractorLaunch retains ownership of its ads, templates, automations, software configurations, funnels, copy, graphics, and internal processes and provides only a limited licence during an active relationship.
- **Exit portability:** Public material does not establish exactly what remains usable after cancellation, including CRM workflows, phone numbers, domains, pixels, audiences, campaign history, creative files, and homeowner data exports.

These are not proof of wrongdoing; the public terms explicitly say the signed Service Agreement governs the specific service. They are reasons to inspect that agreement before funding a replacement system.

The buddy should supply a redacted copy of the ContractorLaunch agreement and two or three months of invoices and CRM exports. The following terms should be recorded exactly:

1. Currency, taxes, and whether media spend is included.
2. Minimum lead purchase, monthly cap, and cancellation terms.
3. The complete billable-lead definition.
4. Evidence required to dispute a lead and the dispute window.
5. Credit, replacement, and refund rules.
6. Whether an appointment must be booked for a lead to be billable.
7. Whether the lead is ever sold or routed to another contractor.
8. Administrative ownership of Meta, domains, CRM, pixels, phone numbers, and data.
9. Export and continued-use rights after cancellation.
10. Historical counts for delivered, reachable, qualified, booked, quoted, won, and lost leads.

### RenoLeadz

RenoLeadz publicly offers GTA coverage and bundles that include advertising:

- C$450 plus tax for 3 exclusive leads: C$150 per lead.
- C$650 plus tax for 5 exclusive leads: C$130 per lead.
- C$1,250 plus tax for 10 exclusive leads: C$125 per lead.
- No separate advertising spend or setup fee.
- Phone verification, screening, automated follow-up, and replacement of invalid leads.

Source: [RenoLeadz pricing and FAQ](https://renoleadz.com/)

On published pricing, ContractorLaunch is cheaper if the two vendors use comparable qualification standards. RenoLeadz is still useful as an external price check because its lead bundles and included advertising costs are stated more explicitly. Its public testimonials and revenue claims are vendor-controlled and should not substitute for a small trial with source-level outcome tracking.

### HomeStars

HomeStars is a marketplace and reputation platform rather than an exclusive contractor-branded acquisition system. Homeowners post a project, professionals express interest, and the homeowner chooses which professionals to shortlist. The contractor is charged when shortlisted and receives the homeowner's contact details. HomeStars says a homeowner can connect with up to three professionals.

Its professional agreement explicitly says that lead frequency, volume, quality, customer interest, customer data accuracy, creditworthiness, and job outcomes are not guaranteed. This makes a HomeStars connection fundamentally different from a contractually defined exclusive qualified lead.

Sources:

- [HomeStars professional registration and lead process](https://www.homestars.com/pro/register)
- [HomeStars professional user agreement](https://www.homestars.com/assets/en_CA/HomeStars-Professional-User-Agreement-January-2025.pdf)
- [HomeStars homeowner matching process](https://www.homestars.com/blog/hiring-pros-on-homestars)

HomeStars can be useful as a supplemental source and review asset, especially when the contractor has a strong profile. It is not the cleanest substitute for ContractorLaunch because the lead may be shared and the platform provides much weaker public quality guarantees.

### Bark

Bark is a broad service marketplace. Contractors can browse matched requests and spend credits only when they choose to contact a customer. Pricing varies with service, project size, location, demand, and intent. Up to five professionals can respond to the same customer.

Credit returns must generally be requested within 14 days and cover invalid contact details, duplicates or tests, and submissions by minors. Monetary refunds are limited and discretionary. A legitimate but unresponsive or price-shopping homeowner is therefore materially different from a refundable invalid lead.

Sources:

- [Bark Canada pricing model](https://www.bark.com/en/ca/sellers/pricing/)
- [Bark lead pricing factors](https://help.bark.com/hc/en-ca/articles/18043745477788-Understanding-lead-pricing)
- [Bark response limits](https://help.bark.com/hc/en-ie/articles/28463866842652-How-many-responses-can-a-customer-receive)
- [Bark credit-return rules](https://help.bark.com/hc/en-ca/articles/27458342155932-Refunds-vs-Credit-Returns)

Bark offers flexible, low-commitment access to demand but appears poorly aligned with a high-ticket contractor seeking exclusive opportunities and predictable qualification.

### CoreLaunch

CoreLaunch is the closest public comparison to building and owning this project's proposed stack. It advertises:

- C$99 per month plus 12.5% of actual ad spend.
- Google and Meta advertising paid from the contractor's accounts.
- A contractor-owned website, domain, ad accounts, reports, and leads.
- Automated creative, SEO content, tracking, CRM delivery, SMS response, and campaign optimization.
- No contract and cancellation at any time.

Source: [CoreLaunch pricing and ownership model](https://corelaunch.ca/)

At C$1,000 of monthly advertising, its public fee structure implies approximately C$1,224 total before usage costs: C$1,000 media, C$125 management, and C$99 platform access. At C$2,000 of media, the comparable total is C$2,349. The resulting cost per qualified lead depends entirely on campaign performance.

This model provides clearer financial and asset ownership than a pay-per-lead supplier, but the contractor assumes the risk of unsuccessful advertising. A custom implementation mainly competes with CoreLaunch on flexibility, verifiability, and avoiding the recurring platform and management fee—not on eliminating media cost.

### Other services considered

RenovationFind publicly describes manually pre-qualified homeowner projects, matching based on trade, location, and capacity, and a contractor portal where leads can be accepted. Its public page does not disclose contractor pricing or establish exclusivity, making a financial comparison impossible without a sales quote.

Source: [RenovationFind lead generation](https://www.renovationfind.com/products/lead-generation)

RenoAssistance uses a success-fee model: there are no membership or annual fees, up to three verified contractors can bid, and a fee is charged only when a contractor wins. Its current homeowner service-area page lists Greater Montréal, Greater Québec, Greater Ottawa, Estrie, Laurentians, Mauricie, and Outaouais—not Toronto—so it is not presently a direct GTA option based on the public coverage information.

Sources:

- [RenoAssistance contractor FAQ](https://www.renoassistance.ca/en/contractor/faq)
- [RenoAssistance service areas](https://www.renoassistance.ca/en/residential/faq)

### Competitive conclusion

The market is crowded, but the offerings are not interchangeable. For this contractor:

1. **ContractorLaunch is the incumbent to benchmark and potentially retain.** If its actual agreement matches the public $99 exclusive-qualified-lead promise and historical signed-job economics are good, replacing it solely to save money is not currently justified.
2. **RenoLeadz is the clearest performance-priced alternative.** Its published C$125–150 per lead is more expensive but explicitly includes advertising and replacements.
3. **HomeStars and Bark are supplemental marketplaces.** They expose the contractor to direct competition and should be evaluated separately from exclusive leads.
4. **CoreLaunch is a buy-versus-build benchmark.** It offers an owned-account model at a transparent recurring fee but leaves the contractor responsible for media efficiency.
5. **The custom project's strongest initial role may be measurement and owned organic acquisition rather than replacing ContractorLaunch.** A lightweight CRM and attribution layer can determine ContractorLaunch's true cost per reachable lead, quote, signed job, and gross-profit dollar while contractor-owned web, review, referral, and organic assets are developed.

The decision should be deferred until ContractorLaunch's actual contract and at least two months of source-level sales outcomes are available. Based only on its public offer, C$99 for an exclusive, properly qualified homeowner with advertising and nurturing included is more attractive than the original assessment assumed.

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
