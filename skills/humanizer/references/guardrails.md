# Humanizer guardrails

These rules are applied in priority order. A lower-level word edit cannot repair a higher-level story or flow failure.

## Priority order

### P0 — truth and source integrity

Stop the run if any of these occurs:

- a new claim, metric, outcome, employer fact, recipient name, anecdote, or personal reaction appears;
- a number, date, URL, tool, title, chronology, or qualifier changes;
- “noticed,” “could,” “may,” or “checked” is strengthened into “proved,” “did,” or “led”;
- a public example contributes facts or wording to the candidate's letter;
- a missing consequence is filled with a plausible result.

Decision: `HOLD` and restore the source wording or request evidence.

### P1 — story and flow

For application prose, enforce this shape unless the user explicitly chooses another format:

`employer-specific trigger → candidate reaction → concrete event → decision or trade-off → action/method → consequence or honest unresolved point → working rule → day-one contribution`

Guardrails:

- The opening must contain a detail that fails the employer-name swap test.
- The primary story must contain a visible signal and a choice. A task list is not a story.
- Use one primary story and at most one supporting proof point in a short letter.
- Do not open every body paragraph with `At [Company]`.
- Do not repeat the same lesson after each example.
- Do not force a thesis sentence. End on the working rule or contribution when that is cleaner.
- Every paragraph must change the reader's understanding: employer problem, candidate judgement, evidence, or contribution.
- The close must name a concrete contribution and a modest ask; it must not restate the introduction.

Decision: `REVISE` if any guardrail fails; `NEEDS STORY INPUT` if the missing element is not in the source.

### P2 — wording and style

Prefer:

- concrete nouns over abstract nouns;
- an active subject who noticed, checked, ran, wrote, raised, or decided;
- a plain verb with an object;
- one precise detail over three adjectives;
- a supported first-person reaction over an abstract lesson;
- varied sentence lengths that follow the thought, not a target distribution;
- transitions based on time, cause, or contrast only when the relationship is real.

Avoid:

- balanced “not X but Y” constructions used for emphasis alone;
- staged reveals (“the key is,” “what matters is,” “the real story is”);
- vague inanimate agency (“the data revealed,” “the decision emerged”);
- stacked qualifiers and hedge words before a fact;
- polished cause-effect bridges that the evidence does not support;
- sentence openings repeated three times in a row;
- a paragraph made entirely of tool names and metrics;
- decorative metaphors, poetic morals, and mic-drop endings;
- automatic em dashes, semicolons, colons, bold labels, or title case.

Style decision: keep an unusual construction when it is present in the author's samples and carries meaning. Remove it only when it is repeated mechanically or obscures the claim.

### P2b — connective tissue, openings, and closings

Connective words must describe a real relationship between two ideas. First identify the relationship, then choose the smallest natural connector. If the relationship is obvious, use no connector.

| Relationship | Preferred shapes | Use only when true |
|---|---|---|
| Time or sequence | `Later,`, `On another project,`, `Before the documents went to the bank,` | The events have an actual order. |
| Cause | `Because`, `That meant`, `So` | The first fact caused the next action. |
| Contrast | `But`, `Yet`, `On the other hand,` | The second fact changes or limits the first. |
| Continuation | `The same instinct showed up at…`, `That work also…` | The new example reinforces the same working rule. |
| Example | `For example,`, or simply start with the event | The sentence is genuinely an example. |
| Consequence | `As a result,`, `That left us…` | The consequence is supported, not assumed. |
| Return to role | `That is the work I would bring to…`, `I would use that habit when…` | The sentence names a concrete day-one contribution. |

Opening guardrails:

- Start with a real employer detail, event, decision, or observation.
- Do not start with `I am writing to express my interest`, `I am excited to apply`, `I am passionate about`, `I believe`, or a company compliment that could fit another employer.
- The first three lines should establish who the employer is, what caught the writer's attention, and what question or tension the writer brings.
- Do not force a hook if the source contains no verified company detail; return `NEEDS COMPANY INPUT`.
- Do not use a quotation, dramatic fragment, or rhetorical question unless it is genuinely present in the writer's voice and relevant to the role.

Body-transition guardrails:

- Do not begin every paragraph with a transition word.
- Do not use `Additionally`, `Furthermore`, `Moreover`, `Ultimately`, or `In conclusion` as automatic glue.
- Do not use `This experience taught me…` after every story. Prefer the next supported action or let the working rule remain implicit.
- Vary the connective shape: a time phrase, a cause clause, a sentence break, or a direct new event.
- If deleting the connector leaves the relationship clear, delete it.

Closing guardrails:

- End with the specific work the candidate could help the target team do and one modest invitation to discuss it.
- Prefer `I would like to discuss how I could help [team] [verb + object].` or a similarly plain sentence grounded in the letter.
- Do not close with a universal moral, `I look forward to hearing from you`, `thank you for your time and consideration` as the entire ending, or a second summary of the CV.
- Do not add “why this company” in the close if the opening already established it; use the close for contribution and ask.
- A two-sentence close is allowed only when the value sentence and the ask cannot be expressed clearly together.

Connector audit:

```text
Opening contains verified employer detail: yes / no
Opening contains candidate reaction or question: yes / no
Repeated paragraph starters:
Formal transition count:
Connectors with a supported relationship:
Connectors cut because the relationship was obvious:
Generic closing phrases removed:
Close names verb + object contribution: yes / no
```

### P3 — watched vocabulary

Scan these terms and ask whether the sentence can name the object or action. Do not blindly delete a technically load-bearing use.

**Vague verbs:** `leverage`, `utilize`, `harness`, `unlock`, `elevate`, `drive`, `foster`, `cultivate`, `empower`, `enable`, `facilitate`, `deliver`, `support`, `contribute`, `spearhead`, `orchestrate`, `showcase`, `underscore`, `bolster`, `garner`, `navigate`, `streamline`, `optimize`, `transform`, `enhance`, `align`, `integrate`, `operationalize`, `champion`.

**Inflated modifiers:** `robust`, `seamless`, `cutting-edge`, `innovative`, `pivotal`, `crucial`, `impactful`, `comprehensive`, `dynamic`, `strategic`, `valuable`, `meaningful`, `significant`, `exciting`, `passionate`, `proven`.

**Application boilerplate:** `I am excited to apply`, `I am writing to express my interest`, `I am drawn to`, `perfect fit`, `proven track record`, `results-driven`, `team player`, `fast-paced environment`, `make a meaningful impact`, `aligns perfectly`, `I would welcome the opportunity`, `I look forward to the opportunity`, `thank you for your time and consideration` when used as padding.

**Filler transitions:** `moreover`, `furthermore`, `additionally`, `ultimately`, `indeed`, `in this context`, `in today's world`, `in the world of`, `as we move forward`, `going forward`, `in order to`, `due to the fact that`.

**False-depth phrases:** `turn data into impact`, `turn complexity into clarity`, `create value`, `drive success`, `make a difference`, `the future looks bright`, `this experience taught me the importance of`, `this reinforced my belief that`, `where X meets Y`, `the possibilities are endless`.

For each hit, choose one action: `KEEP (technical)`, `REPLACE (concrete object)`, `CUT (filler)`, or `ASK (evidence missing)`. A clean scan with a broken story is still a failure.

## Quantitative style checks

These are warning thresholds, not rigid laws:

- no more than one generic opener or generic close;
- no more than one “This taught me…” construction, and only when it is the writer's own working rule;
- no more than one em dash per 400 words unless the voice profile supports more;
- no more than two formal transition adverbs in a 300-word letter;
- at least two concrete anchors in the body, such as a number, named output, named tool, audience, or decision;
- at least one first-person choice in the primary story;
- zero unsupported claims and zero unresolved outcomes presented as resolved.

## Final guardrail report

Return internally:

```text
P0 truth: PASS | HOLD
P1 story/flow: PASS | REVISE | NEEDS STORY INPUT
P2 wording/style: PASS | REVISE
P3 watched vocabulary: KEEP / REPLACE / CUT / ASK counts
Concrete anchors:
Author-voice confidence:
Facts changed: 0 required
Detector score: diagnostic only
Final decision: PASS | REVISE | NEEDS STORY INPUT | HOLD
```

The guardrails improve human readability and trust. They do not promise that any third-party detector will classify the text as human.
