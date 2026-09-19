# Cover-letter insight extraction at multiple levels

Use this reference after source collection and before drafting. The point is to convert a large source inventory into decisions that can be checked in a real letter. Do not treat source frequency as proof by itself; note whether a finding is supported by research, institutional guidance, or anecdotal practice.

## Level 0: evidence and confidence

First separate what a source can establish:

- **High confidence:** empirical studies, field experiments, official notices, and university guidance that directly states a writing criterion.
- **Medium confidence:** reputable journalism, original open-source tools, and employer-facing guides that provide techniques or observed failure modes.
- **Anecdotal:** Reddit, LinkedIn, and personal success stories. Use these to generate hypotheses about reader reactions, never to claim that a format caused an interview.

For every extracted insight record `finding → source IDs → confidence → limitation → operational rule`.

## Level 1: argument and reader movement

The reader should move through one argument:

`employer trigger → candidate reaction → tension or stake → choice → action → consequence or honest unresolved result → working rule → day-one contribution`

The key insight is that the letter's job is interpretation. The CV supplies what happened; the letter shows what Kien noticed, what he decided, and why that decision is relevant to this team. A letter that contains only employer praise and qualifications can be factually correct while failing to persuade.

**Test:** write the one sentence the reader should remember. If it is a list of tools, employers, or adjectives, select a stronger story. If it is a supported judgement such as “he stops when the number does not make sense and makes the risk visible before a decision,” the argument has a human centre.

## Level 2: paragraph function and flow

Each paragraph should have a different job:

1. **Opening:** one employer-specific detail and Kien's reaction. Apply the swap test: changing the company name should break at least one sentence.
2. **Primary story:** one concrete signal, a decision, the method, and a consequence or honest unresolved result. Put the stake before the technique when possible.
3. **Supporting proof:** one shorter example that reinforces the same reason to hire; do not repeat the primary paragraph's shape.
4. **Close:** name the contribution in the employer's context. Remove a generic summary if the final evidence already makes the point.

**Test:** label each paragraph's function in three words. If two paragraphs have the same label, combine or reselect evidence. If a paragraph survives a company-name swap, make it more specific or cut it.

## Level 3: sentence roles and rhythm

Classify each sentence as `scene/detail`, `reaction`, `decision`, `action`, `consequence`, `interpretation`, or `transition`. A strong story has at least one sentence in the first five categories. Too many interpretation and transition sentences produce polished but empty prose.

Prefer concrete first-person verbs where they are true: `stopped`, `noticed`, `checked`, `ran`, `raised`, `decided`, `compared`, `explained`. Put the decision near the event: “The model returned 64%. I stopped at the number.”

Vary sentence length because AI drafts often make every sentence similarly complete and similarly formal. Do not force fragments or fake mistakes. Read the letter aloud and mark any sentence you would not say to a colleague.

## Level 4: words and phrase frames

Flag, then replace only when the meaning allows it:

- **Abstract nouns:** `impact`, `opportunity`, `expertise`, `exposure`, `value`, `capabilities`, `solutions`, `stakeholders`, `landscape`, `growth`.
- **Generic verbs:** `leveraged`, `supported`, `contributed`, `delivered`, `produced`, `drove`, `enabled`, `aligned`.
- **Application frames:** `I am excited to apply`, `I am drawn to`, `perfect fit`, `proven track record`, `make a meaningful impact`, `I would welcome the opportunity`, `I look forward to discussing`.
- **AI-shaped bridges:** `This experience taught me`, `That is why`, `This aligns with`, `Overall`, `In today's fast-paced landscape`.

Do not ban a word mechanically. Give it a concrete object or retain it when Kien actually uses it. Preserve Kien's approved anchors: `I stopped at the number`, `I could not explain the gap`, `before letting it travel further`, `one-page reports`, `maximum bid price`, `maximum amount we could borrow`, `the risks we were willing to take`, and `which movement deserved attention`.

## Level 5: evidence, stakes, and provenance

For each factual sentence, record:

`source item → exact fact → scope → number/date/tool → decision or stake → outcome status`

Raw metrics are weaker than metrics attached to a decision. For finance roles, rank `board decision`, `maximum bid price`, `borrowing limit`, `rate exposure`, and `risk boundary` above a model name or software list. If an outcome is unknown, say so internally and do not manufacture a result in the letter.

## Level 6: reader and authenticity tests

- **First-pass test:** within 20–30 seconds, can a reader find the role, company-specific reason, strongest evidence, and reason to continue?
- **Swap test:** does the opening still work if the employer changes?
- **CV-repeat test:** does any paragraph merely translate a bullet into sentences?
- **Voice test:** does the sentence match Kien's approved samples in cadence and directness?
- **Speakability test:** would Kien say the sentence aloud without editing it mid-sentence?
- **Traceability test:** can every number, employer fact, tool, and outcome be linked to approved evidence?
- **Fairness test:** did the edit preserve Kien's non-native English voice instead of flattening it toward a detector's preferred style?

## Applying the layers to the ING letter

The opening's report reference passes the employer-specific test, but the sentence should show Kien's reaction rather than summarise ING's publication. The FLC story is the strongest primary story because the 64% IRR created a decision to stop and check. The one-page board reports add the missing stakes: maximum bid price, maximum borrowing, and risks to take before bank discussions. The floating-rate sensitivity is a supporting action because it shows the same judgement under a different assumption. BIDV works as a shorter proof point because the reports and client comparisons show repeated practice explaining which movement deserved attention.

The letter should therefore keep this sequence:

`ING report → Kien asks what the client does with the forecast → 64% IRR looks wrong → Kien checks it → board report sets decision limits → rate sensitivity raises risk before bank discussion → BIDV reports show repeated market interpretation → eFX Sales contribution`

Do not add a fabricated ING conversation, a corrected IRR, a confirmed bank decision, or an unverified audience for the BIDV reports. Ask for those details when they would materially raise the score.

## Extraction output

When a user asks for deep source analysis, return:

1. A source-quality count and limitations.
2. A finding ledger with source IDs, confidence, and operational rule.
3. Layered findings from argument to words.
4. A before/after diagnosis of the target letter.
5. A revised draft and its barrier score.
6. The smallest missing fact that would improve the score.

