---
name: kien-cover-letter
description: Activate whenever Kien provides a CV + job description together and asks for a cover letter, says "write a cover letter for X" / "cover letter for this role" / "pair this with a cover letter". Both the CV and the JD must come from Kien for that specific application — never assumed or reused from another skill's bank. Parses the JD, researches one concrete company hook, selects truthful stories from the supplied CV, and writes a concise, value-forward cover-letter draft. Hand the completed draft to humanizer for the separate final prose pass, then deliver plain text and a matching .docx.
---

# Kien's Cover Letter Skill — Story-First Draft

## On-demand references

- Read [Kien voice and evidence](references/kien-voice-and-evidence.md) before selecting stories or matching voice.
- Read [Kien draft framework](references/kien-draft-framework.md) before building the argument and running the self-audit.
- Read [Kien output profile](references/kien-output-profile.md) only when creating DOCX/PDF output.
- Read [cover-letter insight extraction](references/cover-letter-insight-extraction.md) after a large research review.
- Read [cover-letter scoring](references/cover-letter-scoring.md) before delivery.

## Mandatory loading order

For every cover-letter build or revision, load `kien-voice-and-evidence.md` and `kien-draft-framework.md` before selecting or rewriting stories. Load `cover-letter-insight-extraction.md` whenever research or public examples are part of the request, and load `cover-letter-scoring.md` before calling a draft ready. Load `kien-output-profile.md` only for DOCX/PDF/LaTeX output. The short skill file is a router; these references contain the detailed rules required for a pass.

## TRIGGER

Activate when the user:
- Provides a CV **and** a job description together and asks for a cover letter
- Says "write me a cover letter" / "cover letter for this" / "pair this with a cover letter" after already sharing both

**Hard rule: never proceed without both a CV and a JD for that specific application.** Do not fall back to any other skill's experience bank, and do not reuse a CV or JD from an earlier turn unless the user confirms it's the same application. If either is missing, ask for it before drafting anything.

## RESPONSIBILITY BOUNDARY

This skill owns the argument and the evidence:

- confirm the active JD and the employer's real problem;
- research one concrete, current company hook;
- select two truthful stories from the CV and any anecdotes Kien confirms for this application;
- map each story from situation or stakes → decision → action or method → result/output → day-one contribution;
- choose the narrative shape, order, and level of detail;
- preserve Kien's wording when he supplies exact language;
- run the JD, evidence, date, metric, and recipient checks.

`humanizer` owns the final sentence-level cleanup: it diagnoses AI tells, removes generic or helpful-assistant phrasing, adjusts rhythm and punctuation to Kien's writing profile, and performs one no-invention rewrite. Do not duplicate its detector rules here or ask it to invent a stronger hook. Do not humanize before the story draft and factual checks are complete.

---

## THE FOUR REQUIRED INPUTS

Personalize against all four, every time. If one is thin, ask — never pad with filler.

### INPUT 1 — Job description
Always required, provided fresh for this application. Parse per JD PARSING below.

### INPUT 2 — CV
Always required, provided fresh for this application — pasted or attached by the user, never assumed. Pull the header/contact block and every proof point only from what this CV actually contains. Never invent a metric, client, or outcome the CV doesn't back up, and never blend in content from a different CV or from memory of a past session.

### INPUT 3 — Business context (the hook)
The single biggest differentiator between a generic AI letter and a real one. Per HBR's research-first rule: know the company's actual work and the specific challenge this hire is meant to solve, not just its industry. This must be one specific, current, verifiable fact: a recent product launch, funding round, expansion, a stated mission line, a named pain point in the JD's "about us" section, a specific market they're entering, a personal connection to the org.

**Strongest version of this input (Kien's preferred form, see CALIBRATION EXAMPLE): a specific case study of the company's own past project, named concretely, with the real underlying challenge stated in plain language — not just a fact, but a diagnosis.** If a real project/deployment/initiative of the target company is researchable (a launch, a rollout, a program the JD references), prefer building the opener around it over a generic fact.

**Company-context rule:** a short, verified employer descriptor may establish the scale or field of Kien's prior work, but it must explain the evidence that follows. Use one plain descriptor at most. Prefer “a leading real-estate brand in Vietnam” or “Vietnam's largest commercial bank by total assets” over a stack of prestige labels. Never call a company a conglomerate, leader, or largest institution without a source and a date.

**Rule:** if the user hasn't given a real business-context fact and none is extractable from what they pasted, ask for one line before writing the opener. Never fabricate a company detail, and never fall back to generic praise ("your innovative culture") — that is the exact AI-slop failure mode this skill exists to avoid.

**Event-research gate:** before drafting, search the target employer's official newsroom, annual report, product or research site, and the job posting for a named initiative, launch, partnership, published report, or documented business problem. Record its title, date, what happened, and why it connects to the role. If a relevant event exists, use it in the opener instead of paraphrasing the JD. If the event is adjacent rather than directly part of the target team, label the connection carefully; never imply it was the same team or product. A posting contact is not automatically the addressee.

**Corollary from the recruiter source (Medium, "1,000 cover letters"): if there is genuinely nothing specific to say about this company or this fit, say so and suggest skipping the cover letter rather than manufacturing one.** A cover letter with no real signal hurts more than no cover letter.

### INPUT 4 — One real anecdote (the method proof)
Without this, every letter reads as a stacked list of achievements instead of a person. Per the FPRS authentic-cover-letter framework: a resume proves *what* happened, a cover letter has to prove *how* the person works and *why* — that means at least one small, specific, real moment, not a fourth metric. It doesn't need to be dramatic. A decision made under a deadline, a moment something almost didn't work, the actual reason a project got started, a piece of feedback that stuck.

**Rule:** if Kien hasn't given a real anecdote and none is extractable from what he's already shared this session, ask for one before drafting the body — same treatment as INPUT 3. One anecdote can be reused and reweighted across multiple letters in a batch; it does not need to be reinvented per company. Never invent a struggle, a feeling, or a "moment that broke my brain open" that Kien didn't actually describe — a fabricated origin story is a more damaging failure than a flat one, because it's a lie with his name on it, not just a boring paragraph.

---

## REVIEW FEEDBACK CALIBRATION

When a writing reviewer returns feedback, convert it into an explicit revision gate before handing the draft to humanizer:

- Break a compressed middle into paragraphs that each advance one qualification or example, with a clear topic sentence.
- Tighten awkward or crowded sentences at the smallest factual unit. Preserve Kien's numbers, technical terms, and uncertainty.
- Balance examples around the JD's priorities. After each selected story, state the supported role task it transfers to; do not add an unverified outcome, sales metric, or client conversation.
- Keep the opening sequence verified company event -> Kien's reaction or question -> role and value proposition -> primary story; do not let a score trigger reordering.
- Remove repeated morals and skill summaries when the evidence already demonstrates them.
- Make the close complete by naming one contribution to the employer's team and making a low-pressure ask.

Log the feedback, the edit, and the evidence preserved. If the reviewer requests a detail that is absent from the supplied CV or confirmed anecdotes, return NEEDS STORY INPUT instead of filling it with a plausible sentence.

## HANDOFF TO HUMANIZER

Do this only after the story draft, JD mapping, and factual audit are complete:

1. Pass the exact draft and Kien's supplied writing sample(s) to `humanizer` with a context packet: mode `application-letter`, audience, purpose, tone, length, protected facts/terms/citations/links, prohibited additions, and the required output mode. Prefer two or three approved samples from the experience bank; if fewer exist, label voice confidence rather than inventing quirks.
2. Tell `humanizer` to protect every company name, role, date, metric, tool, output, uncertainty, keyword, citation, link, and phrase Kien marked exact.
3. Allow changes to sentence rhythm, connectors, punctuation, and paragraph shape only when they preserve the same facts, story order, and meaning. It may remove generic or AI-sounding language, but it may not add a hook, thesis, result, keyword, or employer fact. Require the draft, AI-tell audit, change summary, verification checklist, literal count gate, and one Signal I audit loop before it returns the text.
4. Run that prose pass once. Return to this skill only for the final JD, evidence, date, metric, recipient, and length checks. If the prose is still empty or too short to carry a real story, select better evidence or ask Kien for detail instead of asking for another synonym pass.
5. Build the DOCX from the final approved text verbatim and run the content diff described below.

The goal is a letter with a concrete moment, a decision Kien actually made, and a clear reason the story matters to this employer. If the draft is thin after sentence-level cleanup, return to story selection or ask Kien for evidence; do not pad it.

## Final handoff

After the humanizer pass, load the output profile for formatting and the draft framework for the final self-audit.

## Pipeline stage protocol

Run this skill as a gated argument stage:

1. **Intake:** bind the letter to a fresh CV, active JD, employer, role, contact block, and operation.
2. **Research:** identify one verified employer problem or event and record its source, date, and confidence.
3. **Evidence:** load Kien's voice/evidence references, rank decision stakes, and select one primary story plus one supporting proof point.
4. **Draft:** write the employer hook, reaction, tension, choice, action, consequence or honest uncertainty, and day-one contribution in the approved order.
5. **Audit:** run the insight and barrier checks; surface missing personal detail instead of inventing it.
6. **Handoff:** send the locked draft and context packet to `humanizer`, then return to JD/evidence checks before building.

**Stage QC:** `PASS` requires active JD, traceable facts, a concrete hook, story integrity, role bridge, and no unresolved source conflict. `REVISE` returns to research or story selection. `HOLD` blocks humanization when the CV, JD, hook, or anecdote is missing.
