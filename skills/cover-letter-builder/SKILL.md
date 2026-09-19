---
name: cover-letter-builder
description: Build a truthful, job-specific cover letter from an active job description and approved candidate evidence, then deliver plain text plus the requested DOCX, PDF, or Expressive Resume LaTeX output with validation and visual QA.
---

# Cover Letter Builder

Use this skill when the user asks to write, tailor, format, validate, or regenerate a cover letter, motivation letter, or application letter for a specific job. The result is an application-ready letter grounded in the active JD and the candidate's approved evidence.

## Operating boundary

This skill prepares drafts and files. It does not submit applications, send messages, change a tracker, edit the experience bank, or publish files unless the user separately asks for that action and approves the concrete change.

Before the first run in a job-application workspace, load `skills/job-application-onboarding/SKILL.md` and the local `.job-apply/workspace-profile.yaml` when present. Follow the configured source-of-truth, CV order, language, location, and output preferences. Do not assume that a profile, tracker, browser session, CV, or writing voice belongs to a particular person.

## Required inputs and readiness

A letter requires:

1. **An active job description for this application.** It may be pasted, attached, captured from the browser, or resolved from a tracker row. If it comes from Notion, show the row link and verify the source page is still available before drafting. Keep the captured JD text and a content hash with the output.
2. **Approved candidate evidence.** Prefer the experience bank as the evidence authority. If a CV is supplied, use it to identify the candidate and source documents and to resolve the selected CV profile. Never silently combine conflicting CVs.
3. **A target company and role.** Take these from the JD or the tracker. Do not infer an employer or title from a URL alone.
4. **A usable contact block.** Take the name and contact fields from the supplied CV or approved profile. Omit unknown fields rather than guessing.

If the JD is missing, stale, inaccessible, or ambiguous, stop and report the exact blocker. If evidence is missing, ask for a CV or an approved experience-bank source. Do not draft a generic letter to fill the gap. If a company-specific hook cannot be found after a reasonable source check, state that a cover letter may add little value and ask whether the user wants a short direct letter anyway.

## Conversation and intent gate

At the start, identify the requested operation:

- **Build:** create a new letter from the active JD and approved evidence.
- **Revise:** change an existing draft while preserving the user's stated wording and meaning.
- **Format:** convert approved text into DOCX, PDF, or Expressive Resume LaTeX.
- **Validate:** inspect an existing letter against the active JD and evidence.
- **Batch:** build multiple letters, keeping each company-specific and separately traceable.

When the user has not specified one of these, ask one short question and show the relevant JD/tracker link. Do not ask for information that is already available in the active profile or source files.

## Evidence and no-invention rules

- Treat the experience bank as the source of truth for what may be claimed. Every factual claim in the letter must link internally to an experience item and source document.
- Preserve original experience-bank wording, numbers, product names, dates, employers, and scope unless the user explicitly authorises an edit. A narrative sentence may change grammar or order, but it may not change the underlying fact.
- Never invent a responsibility, metric, client, tool, date, outcome, title, company fact, visa claim, or personal anecdote. Do not turn a skill keyword into evidence.
- If two sources conflict, show the conflict and ask which source to use. Do not merge them.
- Distinguish **supported**, **partially supported**, **unclear**, and **missing** requirements. A gap can be discussed as a gap; it cannot be written as experience.
- Do not paste a complete CV bullet verbatim into the letter unless the user requests exact wording. Recast supported evidence into natural prose without weakening specific facts.
- If the user supplies a draft or says “exact wording,” treat that text as authoritative. Make only the requested mechanical or structural changes and show any meaning-changing edit before applying it.

## JD and company analysis

Before writing, extract:

- role title, internship/seniority, location, language, work arrangement, and application route;
- the three to six most important requirements, separated into must-have, preferred, and nice-to-have;
- the business problem behind the requirements;
- the company's size/tone signal and likely reader;
- any explicit requirement for a cover letter, motivation letter, portfolio, work authorisation, or sponsorship.

For the company hook, use one concrete, traceable fact tied to the role: a named product, market move, programme, customer problem, or initiative. Prefer official employer pages, the official careers portal, filings, and the JD itself. Record source URL, access date, and confidence. Do not use generic praise or convert an international footprint into a promise of visa sponsorship. If a recruiter or hiring manager is explicitly identified, use the name; otherwise use a register-appropriate generic greeting.

When introducing a previous employer, add one verified descriptor only when it clarifies the scale or setting of the evidence that follows. A personal sentence such as “I was fortunate to work there” is useful only when the candidate supplied it and it leads directly into what they did. Do not stack prestige labels or use “leading,” “largest,” or “conglomerate” without a dated source.

## Draft structure

Default to a one-page narrative letter:

1. **Greeting and opening (2–4 sentences):** name the role naturally, lead with the company-specific hook or a direct role-to-evidence connection, and make the fit concrete.
2. **Proof body (one or two paragraphs):** use two strong evidence items mapped to the highest JD priorities. Tell each as situation → action → impact. At least one should state the problem or stakes before the action.
3. **Gap or transition sentence (optional):** if the JD contains a real gap or the candidate is changing field, explain the supported overlap plainly. Never disguise a gap as a strength.
4. **Close (one or two sentences):** state what the candidate could contribute and make a specific, low-pressure ask. Keep the close substantive; do not end with a generic thanks-only line.

Target 250–320 words; 400 words is the hard ceiling unless the user asks for another length. Use block paragraphs, no body tables, no text boxes, and no decorative claims. Match the company's register without copying its jargon.

## Voice and authenticity pass

Load the user's stored writing-style profile when available. A user-provided draft outranks a generic style guide. Otherwise:

- use plain, specific verbs and varied sentence length;
- remove generic application openers, self-praise, empty enthusiasm, and corporate filler;
- keep at least one concrete moment or decision when the source evidence supports it;
- run a swap test: a company-specific sentence should not survive unchanged if the company name changes;
- run a read-aloud pass and remove sentences that sound templated;
- check repeated sentence openers, passive claims, vague ranges, and unsupported emotional language;
- do not add typos or artificial awkwardness to appear human.

If `humanizer` is used, pass a context packet with mode, audience, purpose, tone, length, protected facts/terms/citations/links, prohibited additions, and output mode. Prefer two or three approved writing samples; if fewer are available, label voice confidence and do not invent quirks. Require its change summary, verification checklist, and optional quality score before formatting.

## Expert-feedback calibration

Translate review feedback into a gated revision before formatting:

- If the middle is compressed, give each paragraph one purpose and separate stakes, action, and consequence.
- If examples feel list-like, order them from the primary decision story to supporting evidence and add a short, factual role bridge after each example.
- If wording is awkward or wordy, shorten the smallest supported span and remove repetition before changing vocabulary.
- If the opening is vague, lead with the verified company event, then name the role and the candidate's one-line value proposition.
- If the closing is weak, state one specific contribution to the named team and make a modest ask; do not repeat the CV or the opening.
- If feedback requests outcomes or role-specific metrics absent from the approved evidence, mark the gap instead of inventing one.

Record the feedback finding, change, and preserved evidence in the humanizer rule ledger. A review score can guide revision but cannot override the active-JD, source-of-truth, or no-invention barriers.

## Story and persuasion gate

Before formatting a Kien letter, read `../kien-cover-letter/references/kien-output-profile.md` and `../kien-cover-letter/references/cover-letter-scoring.md`. Formatting is downstream of the full story, evidence, and persuasion review; a short main skill file does not replace those references.

Before formatting, check the argument in this order: `employer-specific trigger → candidate reaction → tension or uncertainty → choice → action/method → consequence or honest unresolved result → working rule → day-one contribution`.

- Lead with one primary story that demonstrates judgement. Use one shorter supporting proof point only when it reinforces the same reason to hire the candidate.
- Do not let the body become `Company A → task → tool → metric; Company B → task → tool → metric`. That is a second CV even when every fact is correct.
- Judge persuasion separately from factual and ATS checks. Record hook specificity, story progression, evidence credibility, role relevance, and natural voice; a letter can be factually valid and still fail because the reader cannot see why the story matters.
- Apply [references/cover-letter-scoring.md](../kien-cover-letter/references/cover-letter-scoring.md) before formatting. Treat active-JD status, factual traceability, story integrity, and a supported employer hook as barriers. Return `HOLD` for any critical barrier failure even when the numeric score is high; do not let ATS keyword coverage compensate for a weak or generic story.
- Treat a personal reaction or choice as evidence only when the candidate supplied it. Never add sentiment, struggle, a corrected result, or a company event to create a stronger arc.
- Keep the evidence map and T-chart internal. The final letter should read as prose, not as a qualifications table, unless the application explicitly asks for a professional brief.
- Treat anonymous Reddit success claims as pattern observations, not outcome evidence. Prefer the recurring lessons: specific work over prestige, motivation over CV repetition, and concrete finance mechanics over “passion” language.

Reject common filler such as “I am writing to express my interest,” “I am excited to apply,” “perfect fit,” “passionate,” “results-driven,” “team player,” “innovative culture,” “proven track record,” “in today’s landscape,” and similar generic claims. Avoid AI-fingerprint words such as “delve,” “leverage,” “robust,” “seamless,” “unlock,” “foster,” and “cutting-edge” unless they appear in a user-supplied quotation that must be preserved.

## Output formats

Always provide the final letter as plain text in chat. Then create the requested file format:

- **DOCX:** use the documents workflow. Keep text extractable, use normal paragraphs, preserve the selected format profile, and render the DOCX before delivery. Inspect every rendered page for clipping, overflow, broken links, missing glyphs, and unwanted page breaks.
- **PDF:** create from the approved text or from the LaTeX source, then render and inspect every page.
- **Expressive Resume LaTeX:** when the user selects the referenced template, read [references/expressive-resume.md](references/expressive-resume.md). Generate a minimal `.tex` file using `ExpressiveCoverLetter`, the template's `coverletterheader` and contact helpers, and ordinary paragraphs. Compile with an available LaTeX toolchain or the repository's documented devcontainer, then visually inspect the PDF. Do not invent contact fields or add template components the user did not request.
- **No format specified:** use the user's approved document-format profile. If none exists, offer DOCX and plain text; do not silently impose LaTeX.

Name files with the candidate name, company, role, and `CoverLetter`, sanitised for filesystem use. Keep source JD hash, evidence IDs, output version, and approval state in the application record or a sidecar manifest when the user requests tracking.

## Final validation report

Before delivery, report:

- JD status and source link;
- word count and output format;
- requirements covered, with evidence references;
- requirements partially covered or missing;
- company-hook source and confidence;
- whether the user must review a factual, eligibility, or wording issue.

A “ready” letter has no unsupported claims, no unresolved source conflicts, no stale JD, no invented company facts, and passes document rendering QA. If the letter is not ready, return the draft only with the blocker clearly marked.

## Pipeline stage protocol

Run this skill as a gated letter-production stage:

1. **Readiness:** verify active JD, approved humanized text, scoring barriers, evidence map, recipient, format, and output profile.
2. **Build:** create DOCX/PDF/LaTeX from the approved text verbatim using the requested format.
3. **Diff:** extract the output and compare it with the approved plain text; no silent polishing or substitutions.
4. **Render:** inspect every page for clipping, overflow, links, missing glyphs, font substitution, blank pages, and unwanted breaks.
5. **Release:** write the output manifest with JD hash, evidence IDs, score, text hash, output hash, and render result.

**Stage QC:** `PASS` requires all critical persuasion barriers, exact text agreement, and clean rendering. `REVISE` names a formatting defect. `HOLD` returns to `kien-cover-letter` or `humanizer` when the content itself is not ready.
