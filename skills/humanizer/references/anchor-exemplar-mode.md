# Anchor-exemplar mode

Use this mode when the user wants one coherent, reproducible writing model rather than a blend of public examples.

## Core rule

Choose **one anchor exemplar** that matches the document's role, register, and length. Extract its functional blueprint and preferred plain wording. Use other examples only as corroboration and failure checks. Do not average several voices.

The anchor controls:

- paragraph count and approximate paragraph jobs;
- opening movement and first-person distance;
- sentence-length variation and clause density;
- connective style and how often a full stop replaces a transition;
- preferred verbs for action, judgement, and consequence;
- level of formality, contractions, and punctuation;
- how the letter moves from evidence to contribution;
- closing shape and degree of confidence.

The candidate's approved voice samples and factual source still control personal facts, identity, technical claims, and any distinctive wording that belongs to the candidate. A public exemplar cannot override them.

## How to select the anchor

Score candidate examples from 0–3 on each dimension:

```text
same document type:
same role/industry:
same seniority:
same register:
similar length:
clear concrete story:
clear employer-specific reason:
plain, reproducible wording:
```

Select the highest total. If no example is close enough, use Kien's approved writing as the anchor and label public examples as pattern references only.

## Extract a blueprint, not a transcript

Record these fields:

```text
Anchor URL and source type:
Paragraph count:
Paragraph 1 job and sentence shapes:
Paragraph 2 story shape:
Supporting proof-point shape:
Transition relationships used:
Opening verbs and nouns:
Action verbs:
How evidence is quantified:
How uncertainty is stated:
Close shape:
Words/structures explicitly avoided:
```

Use the anchor's **functional wording choices** when they are generic and necessary, such as “I noticed,” “I checked,” “because,” “before,” “that meant,” or “I would like to discuss.” Do not reproduce distinctive metaphors, unusual phrases, anecdotes, or sentences. Keep only the candidate's own approved phrases verbatim.

## Wording ledger: no invented synonyms

Build a small ledger from the anchor before drafting:

```text
Opening verbs:
Reaction verbs:
Decision verbs:
Evidence verbs:
Consequence verbs:
Connectors:
Uncertainty markers:
Role-bridge verbs:
Closing verbs:
Words the anchor avoids:
```

For each sentence, prefer a word already present in the candidate's samples or the anchor's functional ledger when it expresses the same supported meaning. Do not replace a plain anchor verb with a more impressive synonym. If neither source supplies a word, choose the shortest ordinary word that accurately names the action and mark it as a new editorial choice internally.

Exact wording rules:

- Preserve the candidate's approved phrases exactly when selected for the draft.
- Short generic functional phrases from the anchor may be reused when they are necessary to express the same relationship, such as a time, cause, or ask.
- Do not copy a distinctive sentence, metaphor, anecdote, unusual turn of phrase, or a sequence of more than a short excerpt from a public example.
- Do not claim that a public example used a word unless it appears in the source ledger.
- If the requested anchor wording would introduce a fact, tone, or promise that belongs to the example's writer, reject it and return to the candidate's evidence.

The goal is faithful vocabulary selection, not synonym invention and not a disguised copy of another applicant's letter.

## Reproducible drafting recipe

1. Write the candidate's facts into the anchor's paragraph jobs.
2. Follow the anchor's movement: where it starts, when it gives evidence, how it changes paragraph, and how it closes.
3. Use the anchor's connective preference and wording ledger. If it uses direct sentence breaks, do not insert formal transitions.
4. Match the anchor's level of specificity and restraint. Do not make a candidate story more dramatic than the evidence supports.
5. Run the source-of-truth diff. Any sentence that adds a fact is rejected even if it matches the anchor beautifully.
6. Run the guardrail and quality-control modules. The result must still pass the employer-specific hook, story, evidence, relevance, and voice gates.

## Multi-example validation without voice blending

After drafting from the anchor, consult two to five additional examples only to ask:

- Does the opening meet the company-specificity test?
- Does the body show a decision rather than list duties?
- Is the evidence density appropriate for the role?
- Is the close specific and restrained?
- Did the anchor create a known AI-slop pattern?

If another example suggests a stronger pattern, change the rule only when it improves the draft and remains compatible with the anchor. Never import that example's vocabulary, personality, or sentence sequence wholesale.

## Output audit

Return internally:

```text
Anchor selected:
Why it matches:
Blueprint followed:
Wording ledger used:
Functional wording patterns adopted:
Invented synonyms: 0 required
Distinctive public wording copied: 0 required
Other examples used for validation:
Candidate facts preserved:
Final decision: PASS | REVISE | NEEDS STORY INPUT | HOLD
```

This mode gives one consistent target while keeping the letter truthful and original.
