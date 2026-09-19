# Job-application pipeline stage contracts

These contracts keep specialist skills composable. They are internal handoffs, not prose for the applicant.

## Contract fields

Every stage returns:

```yaml
stage: name
status: PASS | REVISE | HOLD
input_refs: []
output_refs: []
evidence_refs: []
checks:
  - name: check-name
    status: pass | fail | warning
    evidence: source-id-or-path
issues: []
revision_target: stage-or-null
next_stage: stage-or-stop
```

A warning does not advance a stage when it violates a hard gate. Record warnings that the user should review even when the stage passes.

## Stage-specific quality checks

### Intake

- Exact role, company, location, and operation are known.
- The user’s requested side effects are separated from read-only research.
- A run ID and manifest exist.

### Job and company source

- JD text was captured from LinkedIn, the official portal, or the tracker row.
- Active status, access date, source URL, and content hash are recorded.
- Official employer application route is captured when available.
- Company size, business, recent event, and other tracker fields have source links and dates.
- LinkedIn and official-portal facts are not silently merged when they conflict.

### Evidence

- Every selected item has a source document and stable evidence ID.
- Original wording, employer, dates, metrics, tools, and scope are locked.
- Conflicts are exposed, not merged.
- Unresolved outcomes remain unresolved.

### CV personalization

- JD requirements are mapped to evidence IDs.
- Only supported keywords are used.
- Timeline and requested CV order match the approved profile.
- No Bloomberg or other excluded experience appears when the manifest excludes it.

### CV validation and build

- Critical JD gaps are separated from nice-to-have gaps.
- Dates, employers, titles, and metrics match the evidence bank.
- Approved text and rendered file have an exact content diff.
- PDF/DOCX has no overflow, clipping, broken links, missing glyphs, or accidental page break.

### Cover-letter draft

- The JD and CV are fresh for this application.
- The company hook is concrete and traceable.
- One primary story contains event, reaction, tension, choice, action, and consequence or honest uncertainty.
- The body interprets the CV rather than repeating it.
- The close names a concrete contribution and ask.

### Humanization

- The meaning lock protects every fact, number, date, link, tool, uncertainty, and exact phrase.
- The pass changes prose only; it does not add personal events, employer facts, results, or keywords.
- Kien’s approved samples control voice.
- Read-aloud, portability, banned-pattern, and factual-diff checks are recorded.
- If source material is thin, return `NEEDS STORY INPUT`.

### Cover-letter scoring and build

- Critical barriers pass: active JD, evidence traceability, story integrity, employer reason, role bridge, voice, and format.
- Persuasion score is reported separately from ATS and detector feedback.
- Minimum floors are enforced: story ≥4/5, evidence ≥4/5, role relevance ≥4/5, hook ≥3/5, voice ≥3/5.
- Rendered output matches the approved plain text exactly.

### Final cross-artifact check

- JD hash, company, role, location, and date agree across all artifacts.
- Every CV and letter claim maps to the same evidence bank IDs.
- Excluded employers or facts are absent.
- Links point to the intended job and official application portal.
- Any unresolved or user-review item is visible in the final report.
