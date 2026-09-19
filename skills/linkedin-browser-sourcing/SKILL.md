---
name: linkedin-browser-sourcing
description: Source and verify internship and early-career jobs through LinkedIn in Chrome, then capture structured job data and official employer application links for the user's job tracker.
---

# LinkedIn Browser Sourcing

Use this skill when the user asks to find jobs on LinkedIn, inspect saved LinkedIn job links, verify whether listings are still active, or transfer job details into a tracker.

## Default Notion tracker

Use the user's active Job Tracking Pipeline view as the tracker for sourcing and reconciliation:

<https://app.notion.com/p/372d3b3acf8181498a26d68bd2b32a23?v=372d3b3acf81818f94b0000c84d46d87>

Load this view before searching, verifying, or proposing tracker updates. If it cannot be opened, report that exact failure and do not silently switch to another database.

## Run intent gate

- On every invocation, load the complete experience bank and discover the connected Notion job tracker before opening listings or writing data. Use the experience-bank preferences as the default sourcing brief.
- Always show the exact Notion tracker URL in the first response. If a specific row is identified, show its Notion page URL as well.
- If the user's request does not already name a clear operation, ask them to choose one action before proceeding:
  1. **Verify a job** — check one or more LinkedIn listings and report active/closed, Easy Apply, requirements, and portal.
  2. **Update a job** — verify a named listing, reconcile it with its Notion row, and fill missing properties.
  3. **Find more internships** — search LinkedIn using the experience-bank preferences and prepare new rows for review.
  4. **Bulk verify/reconcile** — process the selected tracker rows, preview the target set, then reconcile each row against LinkedIn.
  5. **Show the tracker** — return the tracker link and current accessible scope without changing anything.
- If the user already explicitly requests one of these operations, do not ask the same question again; state the detected action, scope, and whether the run is read-only or will update Notion.
- Do not silently choose “update” merely because a listing is open in Chrome. An open tab is evidence to inspect, not permission to write.
- If the tracker cannot be identified or the user has not selected an operation for an ambiguous request, stop and report the missing input instead of browsing or writing.
- Before any write, show the target row(s), the fields to change, and the source URLs/timestamps. Preserve user-entered values and use the safe-update rules below.
- End every run with the Notion tracker link, the selected operation, processed row count, and any rows left `Unknown` or requiring user review.

## Browser workflow

- Use the user's existing Chrome session and LinkedIn account. Do not ask for or store passwords, session tokens, or access keys.
- Search using the requested location, department, industry, seniority, internship status, and date range.
 - Load the complete experience bank first and use its user-preferences section as the sourcing input: target job families, industry priority, location, internship constraints, work authorization, and any stated exclusions.
 - Treat the experience-bank preferences as the default search brief until the user explicitly changes them. Record the brief used for each sourcing run.
- Open each listing and verify the title, company, location, posting date, employment type, application method, and current availability.
- Record the LinkedIn URL exactly as shown. Treat a listing as closed or uncertain when LinkedIn shows a closed, expired, removed, or unavailable state.
- Identify whether the listing supports Easy Apply. Record `Yes`, `No`, or `Unknown` based on the visible application control.
- Capture a verification timestamp and the exact page state used for each status decision.
- Treat login walls, rate limits, CAPTCHA, redirects, and missing controls as verification failures; record `Unknown` and continue with other listings.
- Use a stable duplicate key (LinkedIn job ID plus normalized company and title) before creating or updating a tracker row.
- For every tracker row in scope, run a deep-enrichment pass before marking it researched: capture the visible JD, active/closed state, Easy Apply state, official portal, requirements, application materials, salary, work authorization or visa language, and verification timestamp.
- Add company research to the single `Company Information` property when that property exists. Include employee size, review signals, revenue/funding/valuation or net-worth proxy, growth/headcount signals, visa or sponsorship language, source URLs, source dates, and an explicit confidence label. Never infer sponsorship from size, brand, funding, or reviews.
- Preserve the original LinkedIn URL and existing user-entered values. Fill missing fields with `Unknown` and a reason instead of inventing facts.
 - Treat login walls, rate limits, CAPTCHAs, redirects, and page-state ambiguity as hard verification failures. Never guess active status or Easy Apply.
 - Require a source URL and checked-at timestamp for every non-Unknown fact. Require two independent signals for “active” when the page exposes conflicting states.
 - Do not infer company value, growth, reviews, visa sponsorship, or work authorization from reputation, company size, funding, or job title.
 - Use an idempotent update keyed by LinkedIn job ID + normalized company/title. Preview the target row set and preserve user-entered fields before bulk writes.

## Official application portal

For every active listing, look for the employer's direct application route in the listing, company careers site, or the employer's applicant-tracking page. Prefer the specific job application URL; use the company's careers page only when no job-specific URL is available. Verify that the destination belongs to the employer or its named recruiting platform.

Capture an `Official Application Portal` URL separately from the LinkedIn `Link` URL. Never replace the LinkedIn link. If no official portal can be verified, record `Unknown` and explain why.

- Prefer a job-specific portal URL and verify that its title, company, and location match the LinkedIn listing.
- Do not treat a generic search result or unrelated company page as a verified portal.
 - If the portal title, employer, location, or role cannot be matched to the LinkedIn listing, record `Unknown` and keep the LinkedIn URL unchanged.
- Preserve canonical URLs without tracking parameters when possible, while retaining the original LinkedIn URL for traceability.

## Tracker fields

Capture, when available:

- Job title and company
- Department and industry
- Location and work arrangement
- Date posted and verification date
- Status: Active, Closed, or Unverified
- LinkedIn URL
- Official Application Portal URL
- Easy Apply: Yes, No, or Unknown
- CV, cover letter, or motivation-letter requirement
- Salary or stipend
- Company size and visa or work-authorization language
- Notes about deadlines, eligibility, language, and application steps

## Safe tracker updates

- Read the current row and property schema before writing. Map fields by property name, never by column position.
- Make updates idempotent: update a matching row instead of creating a duplicate.
- Do not overwrite user-entered values unless replacement is explicitly requested.
- Write only values supported by the listing or verified employer source; use `Unknown` for missing values.
- Re-read every changed row and confirm the LinkedIn URL, portal URL, status, and requirement fields.
 - After each batch, reconcile Notion against the source pages: the stored JD, title, company, location, and application state must match the latest visible listing. If they do not, mark the row `Unknown` and record the mismatch.

## Safety and accuracy

- Do not apply to jobs, send messages, or submit documents unless the user explicitly asks for that specific action.
- Do not infer visa sponsorship from company size or brand recognition. Record only explicit sponsorship or work-authorization language.
- Flag duplicate listings and stale links rather than creating duplicate tracker rows.
- Keep a clear distinction between facts visible in the listing and judgments or recommendations.
- Stop before destructive bulk edits when the database schema, target rows, or browser state cannot be identified reliably; report the exact missing evidence.
