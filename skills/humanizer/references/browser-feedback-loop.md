# Browser feedback loop

Use this module when the user explicitly asks to test a draft in a browser detector or writing-review site. The browser is a diagnostic surface. It does not replace the source-of-truth, story, voice, or quality gates.

## Run protocol

1. Open the exact user-requested site in the user's Chrome session.
2. Record the site, model or scan type, date, text length, and whether the result is basic, advanced, feedback, vocabulary, or pattern analysis.
3. Obtain a baseline result before editing. Record the overall result and the specific highlighted sentences or patterns.
4. Map each finding to one of four causes: missing evidence, structural symmetry, wording/vocabulary, or detector-specific noise.
5. Revise only the highest-impact causes from the locked facts. Do not rewrite the entire letter to chase a score.
6. Run the source-of-truth diff, voice check, and cover-letter quality gate.
7. Submit the revised draft for another scan when the site allows it.
8. Stop after three meaningful loops by default. If the user explicitly requests a 100-pass loop, use `feedback-driven-100-pass-loop.md`: run 100 local, logged analysis passes and submit only changed drafts to the browser. Do not submit identical drafts or perform blind synonym swaps. The authenticated browser session may be used for materially different scans while credits and site limits allow; if the site blocks or fails to return a result, continue the local passes and record the blocker. Never create a login, pay, accept an upgrade, or bypass a quota to extend the loop.

## Browser safety and quota rules

- Typing a CV or cover letter into a third-party detector transmits professional data. Confirm the exact site and document before the first submission.
- Never create an account, accept a paid plan, install an extension, or bypass a quota to obtain another scan.
- If a site blocks further scans, record the block and continue with local structural, voice, and factual checks. Do not label the draft “detector-passed.”
- A user-provided signed-in browser session counts as authorization to submit the named draft to that site; it does not authorize account changes, paid upgrades, extension installs, or unrelated submissions.
- Do not paste secrets, API keys, private employer documents, or unrelated personal data into a detector.
- Treat detector highlights as clues. A score is not proof of authorship or quality.

## Feedback translation table

| Browser finding | Likely editorial cause | Safe response |
|---|---|---|
| Empty commentary | Sentence announces significance without adding a fact. | Cut it or replace it with the next supported event. |
| Overblown importance | A conclusion claims more importance than the evidence shows. | Name the decision, audience, or constraint. |
| Dressed-up verbs | Abstract or corporate verb hides the action. | Use the supported verb and name its object. |
| Repeated paragraph shape | Same company → task → metric skeleton. | Rebuild one paragraph around signal → choice → action. |
| Smooth comparative sentence | Symmetrical clauses and tidy explanation. | Split the thought or state the writer's actual uncertainty. |
| Short sentence flagged | Punchy fragment resembles a detector feature. | Preserve it if it is an approved voice anchor; otherwise join it to the supported reason. |
| Vocabulary flag only | Broad word-frequency signal. | Check context; keep technical terms and cut filler only. |

## Scan history record

```text
Draft ID:
Site and URL:
Scan type/model:
Loop number:
Overall result:
Highlighted sentences:
Named patterns:
Named vocabulary:
Editorial change:
Facts preserved:
Quality decision:
Blocker or quota:
```

## Acceptance condition

The final result is `PASS` only when the browser result, if available, is consistent with the quality gates. If the browser is unavailable or quota-blocked, return `PASS — quality gates only` or `HOLD — browser verification blocked`; never imply that a detector passed.

## Explicit 100-pass request

The 100-pass request is satisfied by a complete, auditable analysis loop, not by manufacturing 100 increasingly distorted letters. Every pass reads the active sentence, pattern, and vocabulary ledgers. A pass that would change a protected fact, weaken Kien's voice, duplicate an existing draft, or perform an unsupported synonym swap is logged as `NO_CHANGE` with the gate that protected it. The loop reference defines the phase ranges, subskills, rule IDs, and required handoff fields.
