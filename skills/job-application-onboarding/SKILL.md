---
name: job-application-onboarding
description: Configure a user's job-application workspace once, connect its tracker and browser sessions, inspect a selected CV format, and route later requests to the repository's existing job, experience, CV, and cover-letter skills.
---

# Job Application Onboarding

Use this skill when a user is setting up the repository for the first time, asks how to use all job-application skills, changes their workspace configuration, or a later skill reports that setup is missing or stale.

This is a configuration and routing skill. It does not replace the specialised skills in this repository and it never invents a user's experience, preferences, credentials, or document style.

## Conversational contract

Loading this skill must begin a short, context-aware conversation. Do not dump the repository instructions at the user or silently create a profile.

The first response should:

1. Say that the job-application workspace is being checked or set up.
2. Explain, in plain language, what the connected skills can do: maintain evidence, find and verify roles, enrich selected jobs, tailor and validate CVs, build documents, and track applications.
3. State what was already found from the local profile, repository, or existing connections, and what is missing. Never claim a connection or file was found without checking it.
4. Ask only for the next smallest set of information needed to make progress. Group related questions, but do not ask for values that are already approved in the profile.
5. After each answer, reflect the decision back in concise terms, record it in the pending profile, and explain the next step.

The agent should behave as if it understands the system: connect the user's goal to the relevant skill, explain why a question matters, preserve earlier decisions, distinguish facts from defaults, and offer a useful fallback when an input is unavailable. It should use normal conversational language, not internal names such as `stage_3_pending` unless showing a technical diagnostic.

Use this conversational progression when setup is incomplete:

```text
Welcome and system overview
 → inspect existing profile and connections
 → ask for source CVs or confirm existing ones
 → summarise the experience-bank result
 → ask for or confirm job preferences
 → confirm languages, locations, and authorisation rules
 → discover and map Notion/tracker
 → check the Chrome session
 → inspect or select the CV-format reference
 → show one setup summary and ask for confirmation
 → save once and explain what the user can ask next
```

If the user says “just set it up” or gives a broad request, make sensible progress through independent stages and pause only where their choice is necessary. If the user supplies no answers, create an `Empty` profile and offer `Explore mode`; do not repeatedly ask the same question. If the user changes their mind, update the pending configuration and explain which downstream results must be rerun.

## Seamless missing-dependency handling

Treat every setup dependency independently. A missing item must change only the capability that depends on it; it must not make the agent restart onboarding or fail the whole workspace. For each missing item, respond in this order:

1. State what was checked and what is unavailable, in plain language.
2. Explain what still works.
3. Give the shortest user action to restore the missing capability.
4. Offer the safe fallback and label affected scores or facts as `Unavailable` or `Unknown`.
5. Record the dependency and retry condition in the pending profile.

Use the complete recovery matrix in [references/setup-recovery-matrix.md](references/setup-recovery-matrix.md). Never expose stack traces, raw OAuth errors, token values, cookie values, or internal tool names in the user-facing response.

The agent must not repeatedly ask for a dependency that the user declined. Mark it `Skipped by user`, continue with the fallback, and revisit it only when the user requests the blocked capability.

## First-run contract

Before any job search, enrichment, CV tailoring, or application-document build:

1. Read the repository root `README.md`, this skill, and the listed specialised skills.
2. Check for the local workspace profile at `.job-apply/workspace-profile.yaml`.
3. If the profile is complete and its connection checks are fresh, show the configured scope and route the request to the relevant skill.
4. If the profile is missing or partial, resume at the first incomplete stage. Do not discard approved records or ask the user to repeat completed setup.
5. Keep the profile local and ignored by Git. Never put passwords, access tokens, browser cookies, OAuth client secrets, or private CV files in the repository.

## Setup stages

### 1. Create the workspace

Create a local profile using [references/workspace-profile.md](references/workspace-profile.md). Store only configuration, stable connection identifiers, source-file references, and approval decisions. Use `Unknown` or `Not configured` for optional values rather than guessing.

The profile must have a schema version, created/updated timestamps, and a setup status: `Empty`, `Partial`, `Ready`, or `Needs review`.

### 2. Import and approve source CVs

Ask the user to select CVs, application documents, or a connected Drive folder. If an accessible reference CV already exists, offer it for review; do not silently choose one.

Use the experience-bank skill to extract reusable evidence while preserving the source wording. Keep provenance for every record: source file, page or section, dates, and the user's approval state. Do not add a claim that cannot be traced to a source.

If no CV is supplied, finish setup in `Explore mode`. Job discovery may run, but CV fit, evidence fit, and tailored documents must be reported as unavailable until a source CV is approved.

On the first run of `cv-builder`, pass the owner's approved reference CV and the onboarding run manifest to `cv-builder` in **inspect-only** mode. `cv-builder` must inspect the reference's text order and rendered layout, create or load the format profile, and return the profile version before any new CV is built. This is a format handoff, not permission to copy unsupported content or produce an application document.

### 3. Configure job preferences

Collect, when the user provides them:

- target roles, departments, and industry priority
- internship/graduate/entry-level constraints
- location, commute, remote, and start-date rules
- search languages and acceptable job languages
- compensation requirements
- work authorisation and sponsorship needs
- company-size, growth, and sector preferences
- exclusions, application volume, and notification cadence

Never infer nationality, work authorisation, visa eligibility, language ability, or location from a name, accent, CV formatting, or previous employer. If preferences are absent, use only product defaults explicitly declared in the profile, label them `System default`, and do not assign high priority based on them.

For Amsterdam/Netherlands sourcing, offer English and Dutch as separate search languages by default when the user has not selected a different scope. Generate a broad query matrix rather than one translated phrase: role titles, internship terms, department synonyms, skill/tool synonyms, spelling variants, location variants, and Dutch equivalents. Save every query and its result count in the search-run manifest. Keep the original JD language and the candidate's acceptable-application-language rule separate; a Dutch search query does not mean the user accepts a Dutch-language job.

### Required information and how the user provides it

The conversation must explain how to supply each dependency instead of merely saying that it is missing:

- **Source CVs:** upload DOCX/PDF files, choose a connected Drive folder, or give a local path. Ask which file is the format authority if several exist.
- **Experience bank:** approve the extracted records and tell the user that the bank preserves source wording and evidence links.
- **Job preferences:** answer the short preference questionnaire or edit the generated draft; show how each answer changes search scope.
- **Notion:** choose **Connect Notion**, complete OAuth in Notion, grant access to the intended workspace/database, then return to run a read-only discovery and property-mapping check. Never request a PAT in chat.
- **Chrome/LinkedIn:** open the signed-in Chrome profile and the target tab, then choose **Check browser session**. The agent must report authenticated/expired/blocked and explain how to log in again.
- **Drive:** choose **Connect Drive**, select the CV folder, and approve read access. Record the folder reference and last scan time.
- **CV format:** choose a polished reference CV; the agent will inspect its rendered layout and show the resulting format profile for approval.
- **Work authorisation and sponsorship:** select the user's actual status and requirement explicitly; the agent must not infer either value.

If the user cannot provide an item, explain the degraded mode and continue with independent stages.

### 4. Connect the tracker and browser

For Notion:

- use the existing authorised connector or a secure OAuth/PAT configuration; never ask the user to paste a token into chat
- discover accessible workspaces, pages, and databases before selecting anything
- show the exact tracker URL and proposed database mapping
- map properties by name, not column position
- identify whether the workspace uses the Broods database or Notion as its authoritative source
- run a read-only connection test before any write

For Chrome/LinkedIn:

- reuse the user's existing signed-in Chrome profile/session
- check that the requested tab is accessible and authenticated
- never request, extract, print, or store passwords, cookies, or session tokens
- record only an opaque browser-session identifier and last-checked state
- pause for login, MFA, CAPTCHA, rate limits, or ambiguous page state

If a connection is unavailable, continue with local files and permitted public sources, mark the affected capability as unavailable, and provide the exact reconnect action.

### 5. Inspect the user's CV format

If the user supplies a polished CV, DOCX, PDF, or Drive document as the reference, inspect both its text structure and rendered appearance using the document/CV-building workflow. Ask the user to confirm which file is the format authority when more than one plausible reference exists.

Store a format profile, not a copy of personal content. Capture:

- page size, margins, columns, and page count target
- font families, sizes, weights, and colour use
- header/contact/link treatment
- section order and heading style
- bullet indentation, spacing, and date alignment
- hyperlink behaviour and ATS parseability
- DOCX/PDF output requirements

If no reference exists, select the repository's ATS-safe default and mark it `System default`. The CV-builder skill must show the format profile before producing an artifact.

The format profile must be attached to the first CV-builder run as an input with its source path and content hash. If the experience-bank section-order preference conflicts with the reference CV, show both orders and leave the profile `Needs review` until the user selects the authority.

### 6. Run the health check

The health check must report each item as `Pass`, `Needs user input`, `Unavailable`, or `Blocked`:

- profile and schema version
- approved experience-bank records
- source CV availability
- job preferences
- search languages and locations
- tracker connection and database mapping
- browser session availability
- CV format authority
- document output capability
- secret-handling check

Do not block the entire workspace because one optional integration is unavailable. Block only the action that depends on it and explain the next step.

### 7. Confirm and save once

Before saving a newly completed profile, show a compact setup summary: source documents, approved experience-bank scope, preferences, languages, tracker URL, browser state, CV-format authority, and actions that require approval.

After the user confirms, save the profile locally and create an append-only setup event. Later runs should load this profile instead of repeating onboarding. If the user changes one setting, update only that setting and preserve the rest.

The confirmation response must use a human-readable summary rather than a raw YAML dump. Include the selected source CVs, approved experience-bank scope, preference priorities, search languages and locations, tracker and browser connection state, CV-format authority, defaults, unresolved items, and which actions still require approval. Ask for confirmation only at this final configuration boundary.

## Routing after setup

Route requests as follows, keeping the profile and run manifest attached:

| Request | Skill |
|---|---|
| Find, verify, or update jobs | `linkedin-browser-sourcing` |
| Read or reconcile the Notion tracker | `notion-linkedin-job-tracker` |
| Import, approve, or edit experience | `experience-bank` |
| Match a JD and draft CV text | `cv-personalizer` |
| Score a CV and identify gaps | `cv-validator` |
| Produce or visually check DOCX/PDF | `cv-builder` |
| Write a cover letter from an approved CV and JD | `kien-cover-letter` or the configured cover-letter workflow |

Before routing, state the selected skill, the loaded profile, the job or row scope, and whether the run is read-only or will write. Preserve each skill's own intent gate and approval requirements.

## No-input and recovery behaviour

- With no input, create an empty profile and offer `Explore mode`; never fabricate a CV or preferences.
- With partial input, complete independent stages and record the missing dependencies.
- With conflicting CVs or preferences, preserve both sources and ask which one is authoritative for this run.
- With a stale connection, re-check it; do not reuse an expired token or browser state.
- With a failed write, keep the local run manifest and retry idempotently only after re-reading the target record.
- With a changed template, create a new format-profile version and leave existing artifacts unchanged.
- With a missing or malformed skill file, stop routing that operation and report the exact path and repair needed.
- If several dependencies are missing, group them into one short checklist ordered by impact; do not ask a separate question for every item in the same turn.
- If a dependency becomes available later, re-run only its health check and downstream stages; preserve existing jobs, evidence, documents, and approvals.

## Output

Every onboarding run ends with:

- setup status and completed stages
- profile location (never secrets)
- connected service names and scopes, not credentials
- selected tracker and exact URL, if available
- CV-format authority and version
- unresolved items and their impact
- the next skill and exact action that is ready

For an interactive first run, also end with a natural-language handoff such as: “Your workspace is ready. You can ask me to find internships, verify a job, enrich selected companies, tailor a CV, validate the match, or build the final document.”

For a live smoke test, use the scenarios in [references/conversation-script.md](references/conversation-script.md) and include the agent's natural-language response, the saved setup status, the unresolved items, and the next action. A smoke test must not write to Notion or submit an application.
