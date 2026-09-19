# Prompt and AI-slop playbook

This reference is for requests about prompting Claude, building a humanizer skill, or auditing a draft for AI slop. It is an editing playbook, not a detector-evasion recipe. A natural result comes from specific source material, a real author profile, and structural revision. A blacklist by itself produces shorter generic prose.

## What the new research adds

The strongest recurring finding across public Reddit discussions and open-source skills is that “humanize this” is too underspecified. It gives the model no target voice, no protected facts, no audience, no reason for the text, and no test for success. The useful workflows make those variables explicit, then review the result against the source.

Three independent implementation patterns recur:

1. **Voice profile plus examples.** Extract sentence-length range, paragraph rhythm, punctuation, contractions, preferred openings, closings, hedge rate, domain vocabulary, and phrases to avoid. Public skill authors report better results after roughly 20 before/after pairs than from a generic humanizer prompt. Treat this as a calibration observation, not a universal threshold.
2. **Structure before vocabulary.** The sentence arrangement, paragraph symmetry, generic bridges, and perfectly resolved conclusions often carry more AI signal than one word such as “leverage.” Rebuild the logic while freezing the claim set; do not perform synonym substitution only.
3. **A gated loop.** Draft or edit, run a pattern audit, read aloud, compare against the author profile, perform a claim-by-claim diff, and stop when the remaining issue is missing evidence rather than wording. Public tools that publish benchmarks also separate a tell count or blind preference from detector scores.

Reddit is useful for practitioner observations but is anecdotal. The most consistent comments are: surface edits can leave the same AI skeleton; a detector score is not the same as human judgment; read-aloud rhythm matters; and an “unslop” pass can become a second kind of slop if it adds poetic mic-drop lines or random awkwardness. GitHub skills make the same distinction in code: voice profiles, before/after examples, structural scans, severity levels, and factual-diff checks are more useful than a giant banned-word list.

## Prompt architecture

Use these layers in this order. Put the supplied draft and source material in tagged blocks so the model can distinguish facts from instructions.

```text
<role>
You are an exacting editor. Improve the prose while preserving the author's claims and voice.
</role>

<purpose>
Audience: [who will read it]
Job: [cover letter / email / essay]
Point the reader should remember: [one sentence]
Length and format: [hard limits]
</purpose>

<protected_facts>
Names, dates, numbers, tools, URLs, outcomes, uncertainty, order, and exact phrases that must survive unchanged.
</protected_facts>

<author_samples>
2–5 samples written by the author. Use these to infer cadence and preferences; do not copy private facts or phrases that do not belong to the draft.
</author_samples>

<draft>...</draft>

<process>
1. Build a claim ledger and mark any unsupported statement.
2. Identify the three highest-impact structural or wording problems.
3. Rebuild the affected sentences or paragraph from the same claim set.
4. Check the result against the voice profile and read it aloud.
5. Run a factual diff and return only the requested output plus the audit fields.
</process>

<quality_bar>
Every paragraph must earn its place with a concrete event, decision, constraint, consequence, or company-specific reason. A sentence that could be moved to another employer without changing meaning is a warning. If the source lacks a real detail, return NEEDS STORY INPUT instead of inventing one.
</quality_bar>

<output>
Return: revised text; changed spans and reasons; protected-fact checklist; unresolved evidence; score. Do not report a detector score as proof of authorship.
</output>
```

For Claude, XML tags, explicit role, sequential instructions, relevant few-shot examples, and a stated reason for the constraints are supported prompt techniques. Keep the long source material near the top and the query near the end when context is large. Tell Claude what the prose should do, not only what it must not do. A long deny-list is weaker than a positive replacement rule plus an example.

## Voice profile fields

Capture these from Kien's approved writing and update them only from real samples:

- **Cadence:** short decisive sentences mixed with longer explanatory ones; avoid identical sentence lengths across a paragraph.
- **Openings:** begin with a real observation or event (“I read…”, “I once saw…”, “I stopped at the number.”), not a claim about enthusiasm.
- **Agency:** name the person who noticed, checked, ran, raised, wrote, or decided. Avoid inanimate subjects doing human work.
- **Vocabulary:** plain finance and operating terms; keep load-bearing technical terms such as IRR, debt-equity sensitivity, floating rate, Excel, and Power BI.
- **Stance:** preserve uncertainty when it is true (“I could not explain the gap”); do not replace it with “demonstrated rigour.”
- **Transitions:** use the few transitions Kien actually uses. Do not start every paragraph with “At,” “Additionally,” or “Furthermore.”
- **Punctuation:** no automatic em-dash or semicolon pass. Preserve a punctuation habit found in the samples.
- **Closings:** end on the role-specific contribution, not a second summary of the letter.

## Keyword and phrase inventory

Use this as a scan list and a prompt vocabulary aid. A hit is a warning, not an automatic deletion. Keep a word when it is technically precise, part of the author's normal voice, or required by the JD.

### Structural tells (highest priority)

- “It is not X, but Y” / “not only X, but also Y” when the contrast adds no information.
- “The real story is…”, “The key is…”, “What matters is…”, “At the end of the day…”.
- A noun, colon, and dramatic reveal: “The best part: it learns.”
- Every paragraph opening with “At [company]…”, “Additionally…”, or “Furthermore…”.
- Three balanced items used as a default rhythm rather than because three items matter.
- One-line moral or mic-drop close: “This taught me that…” / “And that is the point.”
- Generic fit bridge that survives a company-name swap.
- “From X to Y” range claims, “in today’s world,” and “in an ever-changing landscape.”
- Abstract inanimate agency: “the data revealed,” “the decision emerged,” “the process empowered.”
- Every story ending with a tidy lesson and no remaining uncertainty.

### Vague verbs and inflated modifiers

`leverage`, `utilize`, `harness`, `unlock`, `elevate`, `drive`, `foster`, `cultivate`, `empower`, `enable`, `facilitate`, `deliver`, `support`, `contribute`, `spearhead`, `orchestrate`, `showcase`, `underscore`, `bolster`, `garner`, `navigate`, `streamline`, `optimize`, `transform`, `enhance`, `align`, `integrate`, `operationalize`, `champion`, `passionate`, `robust`, `seamless`, `cutting-edge`, `innovative`, `pivotal`, `crucial`, `impactful`, `comprehensive`, `dynamic`, `strategic`, `valuable`, `meaningful`, `significant`.

Replace only when the object can be named: “ran the debt-equity sensitivity,” “checked the calculation with colleagues,” “wrote ten market insight reports,” or “set the maximum amount we could borrow.” If no object can be named, the problem is evidence, not vocabulary.

### Application boilerplate

`I am excited to apply`, `I am writing to express my interest`, `I am drawn to`, `perfect fit`, `proven track record`, `results-driven`, `team player`, `fast-paced environment`, `make a meaningful impact`, `aligns perfectly`, `valuable opportunity`, `I would welcome the opportunity`, `I look forward to the opportunity`, and `thank you for your time and consideration` when they merely fill space.

### Filler and hedging stacks

`it is important to note`, `it is worth noting`, `in addition`, `additionally`, `moreover`, `furthermore`, `ultimately`, `indeed`, `actually`, `really`, `very`, `quite`, `somewhat`, `in many ways`, `in this context`, `in the realm of`, `in the world of`, `as we move forward`, `going forward`, `the fact that`, `due to the fact that`, `in order to`, and stacked “I believe / I feel / I think” before a supported fact.

### Closers and false depth

`turn data into impact`, `turn complexity into clarity`, `make a difference`, `create value`, `help drive success`, `the future looks bright`, `this experience taught me the importance of`, `this reinforced my belief that`, `where X meets Y`, and `the possibilities are endless`. End with the concrete work the candidate wants to do.

## Cover-letter-specific rewrite algorithm

1. **Start with the event.** Choose a real company detail and a candidate reaction or question. The first sentence should fail the employer-name swap test.
2. **Choose one main decision story.** Record signal → reaction → choice → action → consequence or honest unresolved result. For Kien, a 64% IRR against 18–25% comparables and the decision to stop and check is stronger than “strong analytical skills.”
3. **Add one supporting proof point.** Use the board report, floating-rate sensitivity, or BIDV market reports only when it advances the same hiring reason.
4. **Connect to day-one work.** Name the client conversation, analysis, or decision the candidate could help with. Do not state “I am a great fit” as a substitute.
5. **Humanizer pass.** Remove duplicated lessons, generic bridges, false symmetry, and decorative words. Preserve unusual details, first-person choices, and honest limits.
6. **Audit.** Run portability, read-aloud, protected-fact diff, evidence provenance, and the cover-letter scoring rubric. Stop at PASS or return NEEDS STORY INPUT.

## What not to optimize

Do not add typos, fake slang, random fragments, invented vulnerability, or unusual punctuation to fool GPTZero. Do not paraphrase every sentence until the facts drift. Detector results are noisy, and public research shows false positives and large performance differences across writers and detectors. The quality target is a reader who can see what happened, what the candidate decided, and why the detail matters to this employer.

## Source notes

High-confidence prompt guidance: [Anthropic prompting best practices](https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/prompt-templates-and-variables). Practitioner and implementation references: [milock/humanizer](https://github.com/milock/humanizer), [Aboudjem/humanizer-skill](https://github.com/Aboudjem/humanizer-skill), [TaewoooPark/personal-humanizer-maker](https://github.com/TaewoooPark/personal-humanizer-maker), [SkillProof text-humanizer](https://github.com/Skillproofdev/text-humanizer), [Aparnabuilds/humanizer](https://github.com/Aparnabuilds/humanizer), [spuvr/humanizer](https://github.com/spuvr/humanizer), [aaron-he-zhu/humanizer-slop](https://github.com/aaron-he-zhu/aaron-marketing-skills/blob/main/references/humanizer-slop.md), and [autonovel anti-slop rules](https://github.com/NousResearch/autonovel/blob/master/ANTI-SLOP.md).

Public practitioner discussions: [voice matching and detector loop](https://www.reddit.com/r/ClaudeAI/comments/1tju3ck/claude_is_the_best_ai_humanizer_when_you_give_it/), [unslop-text and read-aloud rhythm](https://www.reddit.com/r/ClaudeAI/comments/1udl9hg/unsloptext_a_claude_skill_that_flags_and_removes/), [before/after calibration](https://www.reddit.com/r/claudeskills/comments/1v8wa5r/whats_the_best_humanizer_skill_out_there/), [humanizer skill review](https://www.reddit.com/r/ClaudeAI/comments/1s3i8cch/the_humanizer_a_claude_skill_that_catches_ai_patterns_in_your_writing/), and [workflow/stop-slop discussion](https://www.reddit.com/r/ClaudeWorkflows/comments/1u87n7c/workflow_eliminate_ai_tells_from_claudes_writing_with_the_stop_slop_claude_skill/).

Additional pattern references: [EnhancePost AI-slop list](https://enhancepost.com/blog/ai-slop-words-phrases-list/), [SwissGlobal AI-writing patterns](https://swissglobal.ch/wp-content/uploads/2026/04/AI-Writing-Patterns-SwissGlobal-Guide-1.pdf), [AI engineering anti-slop guide](https://github.com/louisfb01/ai-engineering-cheatsheets/blob/main/Anti_Slop_AI_Writing_Guide.md), [God of Prompt blocklist](https://godofprompt.ai/prompt-library/slop-word-blocklist-for-ai-writing), [AI slop measurement](https://arxiv.org/abs/2509.19163), and [Antislop research](https://arxiv.org/abs/2510.15061).

The full 227-source review, validation counts, and larger source index remain in [cover-letter-humanization-200.md](../../../../job-apply/research/cover-letter-humanization-200.md). Social sources are labelled anecdotal; blocked or login-only pages are not treated as fully verified.
