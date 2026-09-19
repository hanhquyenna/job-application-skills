---
name: job-application-pipeline
description: Orchestrate a complete job-application run through job sourcing, company research, experience-bank selection, CV personalization, validation, cover-letter drafting, humanization, document building, and final quality control.
---

# Job-application pipeline

Use this as the single entry skill when the user asks to find, verify, tailor, validate, build, or apply for a job and wants the specialist job-application skills run together. It coordinates the existing skills; it does not replace their detailed rules.

## Default job tracker

Unless the user names another tracker, use the active Job Tracking Pipeline view:

<https://app.notion.com/p/372d3b3acf8181498a26d68bd2b32a23?v=372d3b3acf81818f94b0000c84d46d87>

Pass this exact tracker URL into the intake manifest and show it at the start of sourcing or reconciliation. Do not replace it with an archived or similarly named database without reporting the mismatch.

## Operating principle

One pipeline run owns one job and one source-of-truth manifest. Each specialist receives the previous stage's approved artifact, performs its own work, returns a quality decision, and records evidence for that decision. The pipeline advances only on `PASS`. `REVISE` returns to the named stage. `HOLD` stops the run with the exact blocker.

The pipeline never hides a failed specialist behind an overall average score. A valid CV can still fail a JD gate; a polished letter can still fail a story or provenance gate.

## Intent gate

At the start, classify the requested operation:

- **Source:** find or verify jobs, research companies, and capture tracker fields.
- **Evidence:** create or maintain the experience bank.
- **CV:** tailor, validate, and render a CV for one active JD.
- **Cover letter:** draft, humanize, score, and format a letter for one active JD.
- **Full application:** run Source → Evidence → CV → Cover letter → Final check.

If the operation is ambiguous, ask one short question and show the relevant job or tracker link. Do not run external mutations merely because the user asked to “look into” a job.

## Required run manifest

Create or update an internal manifest before the first stage:

```yaml
run_id: unique-id
operation: source | evidence | cv | cover-letter | full
job:
  tracker_id: verified-or-null
  title: exact-title
  company: exact-company
  location: exact-location
  jd_url: source-url
  jd_hash: content-hash
  jd_status: active | stale | inaccessible | unknown
source_versions: {}
stages: {}
artifacts: {}
open_issues: []
side_effects: none | user-authorized-only
```

The manifest is the continuity layer between skills. Record source links, JD hash, evidence IDs, CV version, scores, output paths, and approval state. Never infer a job identity from a company name or URL alone.

## Stage sequence and gates

Read [the stage contracts and quality checks](references/qc-contracts.md) before running a full pipeline.

| Stage | Specialist skill(s) | Required output | Advance only when |
|---:|---|---|---|
| 0. Intake | This skill | Intent, job identity, requested side effects, manifest | Operation and job are unambiguous |
| 1. Job and company source | `linkedin-browser-sourcing`, `notion-linkedin-job-tracker` | Active JD capture, LinkedIn URL, official application URL, company research fields | JD is active or explicitly approved as a historical source; required links and source dates recorded |
| 2. Evidence | `experience-bank` | Selected evidence IDs, locked wording, provenance, unresolved facts | Every selected claim is traceable and conflicts are resolved |
| 3a. Personalize | `cv-personalizer` | Tailored CV text, JD match map, score, gaps | Active-JD gate passes and all claims are supported |
| 3b. Validate | `cv-validator` | Requirement matrix, severity gaps, factual/timeline checks | No critical factual or JD blocker; revision loop completed if needed |
| 3c. Build | `cv-builder` | Approved DOCX/PDF, content diff, render QA | Text diff matches approved CV and every page passes visual QA |
| 4a. Draft | `kien-cover-letter` | Company hook, story map, plain-text letter | CV and JD are supplied for this application; story and evidence gates pass |
| 4b. Humanize | `humanizer` | Single prose pass, audit, fact diff, voice check | No changed facts and no `NEEDS STORY INPUT` blocker |
| 4c. Score and build | `cover-letter-builder` plus cover-letter scoring reference | Barrier status, persuasion score, DOCX/PDF, render QA | All critical barriers pass and output matches approved text |
| 5. Final check | This skill | Cross-artifact report and next action | JD hash, company, role, dates, timeline, evidence IDs, scores, links, and files agree |

A user may start at any stage when its prerequisites are already present. The manifest must still record skipped stages and their evidence or reason.

## Quality-control loop

After every stage, write a compact gate record:

```text
Stage: <name>
Status: PASS | REVISE | HOLD
Artifact: <path or inline identifier>
Evidence checked: <IDs, URLs, hashes, counts>
Checks: <passed checks>
Issues: <specific failures or uncertainty>
Next stage: <name or stop>
```

- `PASS` advances to the next stage.
- `REVISE` names one prior stage and one concrete change. Re-run that stage's checks and downstream checks; do not restart unrelated work.
- `HOLD` names the blocker and the smallest input or authorization needed. Do not draft around it.

Use at most three revision cycles for one artifact. If the score stops improving, request the missing evidence or return the artifact for human review. A synonym-only loop is not a revision cycle that can make a failed story pass.

## Side effects and approvals

Reading public pages and local files is allowed within the user's request. Editing Notion, changing tracker fields, submitting applications, sending messages, uploading files, or publishing artifacts requires explicit user authorization for that concrete action. Keep side effects listed in the manifest and report them at the end.

## Final report

Return one concise report with:

- operation and job identity;
- stage statuses and revision count;
- active JD link and hash;
- selected evidence IDs and unresolved facts;
- CV and cover-letter scores with barrier failures, if any;
- output file paths and render results;
- external changes made, if authorized;
- the next action.

A full pipeline is complete only when the final check passes or the run is explicitly held with a concrete blocker.
