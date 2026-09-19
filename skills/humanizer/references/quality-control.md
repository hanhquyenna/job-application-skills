# Humanizer quality-control module

Run the checks in order. A later pass must not hide a failure from an earlier pass.

## Gate 1: source and purpose

- Exact draft, audience, role, JD, company research, length, and output format are present.
- Claim ledger is complete.
- Voice profile is supplied or confidence is labelled low.
- If a cover letter lacks a real story, company reason, decision, or consequence, return `NEEDS STORY INPUT`.

## Gate 2: structural audit

Mark each occurrence of:

- generic opener or company-name swap sentence;
- repeated `At Company...` paragraph shape;
- CV chronology disguised as prose;
- staged contrast, false depth, or one-line moral;
- repeated transitions, triads, or identical sentence lengths;
- abstract bridge that says “fit” without naming work;
- generic close that could serve any employer.

Fix the three highest-impact problems first. Do not begin with synonym substitutions.

## Gate 3: evidence and story

For each proof point, answer:

```text
What happened?
What did the writer notice?
What choice did the writer make?
What action or method followed?
Who used the output?
What result, decision, or honest unresolved point is supported?
Why does this matter to this reader?
```

If an answer is missing, shorten the claim or request evidence. Do not fill the gap with a lesson sentence.

## Gate 4: voice and rhythm

- Read aloud once.
- Mark any sentence the writer would not say.
- Compare openings, sentence lengths, contractions, punctuation, and transitions with the profile.
- Remove smooth symmetry only where it is not a stable author habit.
- Do not add typos, slang, fragments, or odd punctuation as camouflage.

## Gate 5: final diff and decision

Return these fields internally:

```text
Structural tells before / after:
Protected facts preserved:
New claims: 0 required
Unresolved claims preserved:
Voice confidence:
Portability failures:
Hook / story / evidence / relevance / voice scores:
Decision: PASS | REVISE | NEEDS STORY INPUT | HOLD
```

`PASS` requires zero new claims, no critical story gap, a company-specific reason, and a readable result in the author's voice. Detector scores may be recorded as diagnostics, never as the acceptance criterion.
