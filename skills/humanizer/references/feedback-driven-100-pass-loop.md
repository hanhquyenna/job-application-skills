# Feedback-driven 100-pass cover-letter loop

Use this reference when Kien asks for repeated detector feedback, asks to scroll through the complete report, or wants the one large humanizer skill to learn from each revision. It is an editorial convergence loop, not a promise to evade a detector.

## Subskill map

The humanizer remains one skill. Treat these as ordered subskills with separate inputs, outputs, and quality gates:

1. **feedback-surface-reader** — read the overall result, AI Sentences, AI Patterns, and AI Vocab. Scroll or expand the complete result before making a change. Record the scan model, date, exact highlighted sentences, named patterns, and named vocabulary. “No vocabulary found” is a finding and must be recorded.
2. **sentence-feedback-analyser** — map each highlighted sentence to evidence gap, repeated/CV-like shape, predictable wording, or detector noise. Analyse why the sentence was highlighted before changing it. Preserve a sentence marked human-like when it is factual, in Kien's voice, and fits the agreed order.
3. **pattern-restricter** — maintain a live pattern ledger. Track forced threes, repeated openings, staged run-ups, fake contrasts, one-line morals, symmetrical clauses, generic closers, and dash or hyphen habits. Restrict a pattern only when it is not required by the fact or the user's voice.
4. **vocabulary-restricter** — maintain a live vocabulary ledger. Record every flagged AI vocabulary item and its context. Replace vague or inflated verbs with a supported action and object, cut filler, and keep technical terms. An empty vocabulary finding must not trigger random synonym changes.
5. **example-led-paraphraser** — use public examples for movement and density only: trigger → reaction or question → event → choice → action → audience/consequence → modest ask. Use Kien's exact evidence and voice. Do not copy public phrases or invent a “human” quirk.
6. **order-keeper** — preserve the agreed order: verified company event first, direct connection to the primary personal story second, supporting evidence after that, and a short close. A detector finding never authorises reordering.
7. **meaning-and-voice-gate** — run a factual diff, protected-phrase check, read-aloud check, company-swap test, second-CV test, and interview-continuation test after each accepted edit.
8. **selection-and-ledger** — compare drafts by evidence, flow, voice, and reader usefulness. Keep the strongest legitimate draft, not automatically the one with the lowest detector score. Log rejected variants and the reason.
9. **predictability-auditor** — treat a high AI score as a clue that common next-word sequences, balanced syntax, or predictable paragraph movement may be present. GPTZero does not expose token probabilities, so infer only from its sentence highlights and the text itself. Vary information order and sentence length where Kien's voice permits; never add mistakes, slang, or unsupported detail to lower a score.

### Expert-feedback translation subskill

Use this after each writing-review scan and before sentence-level cleanup:

1. **Opening barrier:** if the reviewer says the opening is vague, keep the verified company event first, then add the role and one concrete value proposition. Do not replace a researched event with generic enthusiasm.
2. **Middle-density barrier:** if the middle is compressed, give each paragraph one job and one topic sentence. Separate stakes, choice, action, and consequence; keep the user's approved order.
3. **Example-balance barrier:** if examples feel list-like, rank them by the JD's priorities, give the primary decision story the most space, and add a short role bridge after each supporting story.
4. **Directness barrier:** if sentences are wordy or awkward, shorten the smallest supported span, remove repetition, and prefer a concrete subject, verb, and object. Do not do a synonym-only pass.
5. **Transfer barrier:** if the reviewer wants clearer fit, name the supported task, audience, or decision the evidence transfers to. Do not invent outcomes, sales metrics, client conversations, or responsibilities absent from the evidence ledger.
6. **Closing barrier:** end with one specific contribution to the named team and a modest ask. Remove a repeated skill summary or one-line moral when the evidence already demonstrates it.
7. **Shorthand barrier:** spell out or contextualise technical shorthand once for a general reader, while protecting exact numbers, tools, and finance terms.

Each finding becomes a rule-ledger entry with source, risk, permitted edit, forbidden edit, and evidence preserved. A score may guide the next edit; it never overrides truth, voice, order, or active-JD barriers.

## Rule ledger

Append new rules instead of replacing earlier rules. Each rule has an ID and a provenance field:

```text
R-ID:
Source: GPTZero sentence | GPTZero pattern | GPTZero vocabulary | Kien instruction | public example pattern | local audit
Finding:
Risk:
Permitted edit:
Forbidden edit:
Status: active | superseded | rejected
Evidence preserved:
```

Never turn one detector highlight into a universal blacklist. A rule is active only when it is supported by the current feedback and does not conflict with a protected fact, technical term, or Kien's approved voice.

## One hundred controlled passes

Set `pass_budget=100` when the user explicitly requests one hundred rewrites. A pass means one complete analysis cycle, not a forced synonym swap. The loop must keep a hash and a change log. It may record `NO_CHANGE: quality gate protected the current wording` when the best edit would lower truth, voice, or clarity. Never submit identical text to the browser.

| Passes | Subskill and work | Required gate |
|---:|---|---|
| 1–5 | Read and expand every browser feedback surface; create the claim, protected-term, sentence, pattern, and vocabulary ledgers. | Complete feedback record exists. |
| 6–15 | Extract recurring mechanics from approved public examples and Kien samples. Mark trigger, reaction, choice, action, audience, and consequence. | No source wording or unsupported fact enters the draft. |
| 16–25 | Repair the opening while preserving company event first and the direct bridge to the primary story. | Company-swap test and order check pass. |
| 26–40 | Edit one sentence at a time using the highest-impact AI-sentence findings. Prefer concrete subject + verb + object; keep real uncertainty and technical detail. | Sentence meaning and factual diff pass. |
| 41–55 | Repair paragraph movement and repeated CV chronology. Vary rhythm only where it sounds like Kien; do not add fragments, typos, slang, or fake emotion. | Read-aloud and interview-continuation checks pass. |
| 56–65 | Apply active pattern restrictions: remove forced threes only when one item can be omitted without losing a required employer detail; cut staged announcements, fake contrasts, duplicate morals, and generic closers. | Pattern ledger shows each removal and its reason. |
| 66–75 | Apply vocabulary restrictions. Replace a flagged vague verb with the supported action and object; cut filler; keep load-bearing finance, software, and company terms. | Every replacement has a source claim. |
| 76–85 | Use green or human-like sentences as candidates, never as automatic truth. Test them against voice, order, portability, and evidence. | Only supported green wording survives. |
| 86–92 | Compare the best variants. Prefer the version with the clearest decision, strongest company reason, and least generic commentary. | No new claims; no protected term changed. |
| 93–97 | Run final structural, voice, vocabulary, and truth audits. If a detector score is unchanged, diagnose rather than randomly paraphrase. | All quality gates reported. |
| 98–100 | Final read aloud, factual diff, browser feedback record, and handoff. | `PASS`, `PASS — quality gates only`, `NEEDS STORY INPUT`, or `HOLD`; never “detector passed” without visible evidence. |

## Browser feedback policy for the loop

For every **changed** draft, submit the exact text to the authenticated browser only when the user authorised that site and credits remain. Read all four surfaces after each submitted scan. Do not submit a scan for a `NO_CHANGE` pass. The browser is diagnostic and finite; if the site limits scans, continue the remaining passes locally and record `HOLD — browser verification blocked`. Never create an account, pay, install an extension, or paste secrets.

The browser findings are translated as follows:

- **AI sentence:** inspect its evidence, syntax, rhythm, and genericness; change the smallest supported unit.
- **AI pattern:** identify the exact construction, such as a three-item list; remove or reshape it only if the employer detail remains intact.
- **AI vocabulary:** inspect the word in context; replace only when a concrete supported verb or noun is available.
- **Human-like/green sentence:** retain only after the source-of-truth and order gates pass. A greeting or sign-off is not a voice model.
- **No vocabulary found:** record `VOCAB_RULE: none`; do not perform a synonym pass.
- **Persistent AI 100% with no pattern/vocabulary findings:** record `PROBABILITY_RULE: diagnostic only`; test one concrete syntax or information-order change, then preserve the strongest truthful draft if the score does not move. Do not treat the detector as a literal word-probability API.

## Required loop log

```text
Draft ID:
Pass number:
Feedback surface read:
Active rule IDs:
Finding analysed:
Edit or NO_CHANGE:
Browser submission: yes | no (reason)
Overall result and model:
Sentence/pattern/vocab findings after scan:
Facts preserved:
Order preserved:
Quality decision:
```

The final report should include the feedback ledger, the ten phase results, the number of changed and no-change passes, the final factual diff, and the honest browser status. The purpose is to improve a truthful letter that sounds like its writer, not to add artificial noise or game a classifier.

## GPTZero rationale dictionary

When GPTZero exposes `Why is it AI?`, record the exact labels before editing. Use these translations:

| GPTZero label | Interpretation | Safe response |
|---|---|---|
| Monotonous Syntax / Predictable Syntax | The sentence has a standard declarative or subject–verb–object shape. | Split or join it with a supported adjacent fact, or move a time/audience phrase. Do not force unusual grammar. |
| Task-Oriented / Functional Word Choice | The sentence states a precise action with ordinary nouns. | Keep the action. Add the supported decision, audience, or constraint if available. |
| Mechanical Writing / Lacks Creativity / Lacks Complexity | The detector expects imagery or layered prose. | Do not add metaphor to a finance or technical fact. Use a concrete comparison, uncertainty, or consequence already in the source ledger. |
| Detached Warmth / Overly Formal / Robotic Formality | A company hook, greeting, or polished phrase sounds distant. | Use a verified company detail and Kien's real reaction or question. Keep conventional salutations when the application requires them. |
| Mechanical Precision | A technical term or number is unusually exact. | Protect the number and technical term; specificity is a virtue in an application. |
| Persistent 100% after pattern and vocabulary panels are clean | The detector's document-level classifier is not giving an actionable word-level signal. | Log the result, test one legitimate syntax change, and retain the strongest truthful draft if the score does not move. |

## Expert-advice review subskill

When the browser offers an expert or rubric review, treat it as a separate quality surface from AI detection:

1. Record the overall score, what is working, every top-feedback item, each rubric dimension, and the exact reviewer explanation.
2. Open each available expert profile or review mode, then compare whether the advice is stable. A repeated suggestion is a stronger editorial rule; a one-off suggestion remains a candidate.
3. Translate advice into a bounded edit. “Tighten” means remove repetition or shorten a sentence. “Strengthen transitions” means name the relationship between two supported examples. “Add a concrete result” means request or use an existing result; never invent a client outcome.
4. Rescan a changed draft only after the edit and preserve the score history. If the score is unchanged, keep the clearest truthful version and log the plateau.

For Kien's ING letter, the expert panel scored **20/25** and consistently praised role fit, client-focused framing, specific examples, and metrics. It repeatedly requested a more specific ING/eFX opening and close, tighter phrasing, clearer bridges between examples, and one concrete eFX client-impact result. The existing evidence supports the first three edits. The client-impact result is missing from the source ledger, so the correct state is `NEEDS STORY INPUT`, never a fabricated outcome.


### GPTZero sentence-rationale record: 2026-09-11

Document: Dear ING eFX Sales Team,
Scan: Advanced, model 4.9b
Draft: minimal syntax revision, following the previous Expert Feedback result
Overall: AI 100%, Mixed 0%, Human 0%

AI Sentences surface:
- High impact: For eFX Sales, that is the filter I would use when a client needs to know what matters. Rationale was available on the selected row; the detector treated the role bridge as formal, task-oriented guidance.
- High impact: I had to decide which movement mattered and explain why. The selected-row rationale was not exposed after the adjacent row interaction; preserve as a factual decision sentence and log as no additional rationale available.
- High impact: Those reports went into quarterly strategy meetings. No additional rationale was exposed after the adjacent row interaction; it is a factual audience/consequence sentence.
- Low impact: I also compared more than 25 client profiles in Excel and Power BI. No additional rationale was exposed after the adjacent row interaction.
- Low impact: At BIDV, I wrote more than ten market insight reports on portfolios covering $40M+. No additional rationale was exposed after the adjacent row interaction.
- Low impact: What stayed with me was what happens after the forecast. No additional rationale was exposed after the adjacent row interaction.
- Low impact: I read ING's June 2026 FX Talking report. No additional rationale was exposed after the adjacent row interaction.
- Low impact: Dear ING eFX Sales Team, No “Why is it AI?” rationale was exposed; conventional salutation retained.
- Low impact: I would use the same check before explaining a market move to an eFX client. Labels: Task-Oriented, Rigid Guidance.
- Low impact: I tested that assumption in a debt-equity sensitivity and raised the risk before the documents went to the bank. Labels: Sophisticated Clarity, Mechanical Precision.
- Low impact: On another project, I saw that a bank's quarterly floating rate could spike based on the previous year's trend. Label: Formulaic Transitions.
- Low impact: Projects I had seen were between 18 and 25%, so I could not explain the gap. No additional rationale was exposed after the adjacent row interaction.
- Low impact: At FLC Group, a real-estate model once returned a 64% IRR. Labels: Overly Formal, Robotic Formality, Sophisticated Clarity, Mechanical Precision.
- Low impact: I want to learn that part of the job at ING. Labels: Lacks Creative Grammar, Task-Oriented.
- Low impact: In eFX Sales, that means explaining a market move to a client and helping them decide what it changes for them. Label: Rigid Guidance.
- Medium impact: Before we spoke with the banks, those reports helped us set the maximum bid price, the maximum amount we could borrow, and the risks we were willing to take. Labels: Functional Word Choice, Formulaic Transitions. The interface also displayed unrelated expanded list text, so only the named labels are retained.
- Low impact: I asked colleagues to go through the calculation with me before using it. Labels: Rigid Guidance, Lacks Creative Grammar, Task-Oriented. The displayed explanation stated that “before using it” indicates a practical approach to ensuring accuracy.
- Low impact: I also prepared one-page reports for internal board meetings. Label: Lacks Creativity.

AI Patterns: 0 instances of AI patterns found; no AI patterns detected.
AI Vocab: We did not find any common AI vocabulary in your text.

Expert Feedback after the revision:
- Overall: 20/25.
- What's working: the letter connects market-analysis experience directly to ING eFX Sales; examples show analytical judgement and client-facing relevance.
- Top feedback: tighten sentence-level phrasing; link each example more directly to ING eFX Sales; streamline the middle so each paragraph has one clear purpose.
- Audience & Voice: 4/5; tie more lines directly to what the eFX Sales audience needs.
- Clarity & Precision: 4/5; reduce repetition and smooth awkward phrasing.
- Coherence & Flow: 4/5; strengthen transitions and topic sentences.
- Purpose & Support: 4/5; make the fit visible faster.
- Structure & Format: 4/5; tighten the middle and sharpen the transition to the close.

Interpretation rules:
- Task-Oriented, Rigid Guidance, Predictable Syntax, Functional Word Choice, Formulaic Transitions, Robotic Formality, and Overly Formal are structure/register signals. Address them with a minimal merge, split, or concrete audience/decision link.
- Sophisticated Clarity, Mechanical Precision, Lacks Creativity, and Lacks Creative Grammar do not justify removing supported finance facts or adding metaphors. Protect exact numbers and technical terms.
- No vocabulary and no pattern findings prohibit a random word blacklist or synonym pass.

Current draft after this scan:
Dear ING eFX Sales Team,

I read ING's June 2026 FX Talking report. What stayed with me was what happens after the forecast. In eFX Sales, that means explaining a market move to a client and helping them decide what it changes for them. I want to learn that part of the job at ING.

At FLC Group, a real-estate model once returned a 64% IRR. Projects I had seen were between 18 and 25%, so I could not explain the gap. I asked colleagues to go through the calculation with me before using it. I also prepared one-page reports for internal board meetings. Before we spoke with the banks, those reports helped us set the maximum bid price, the maximum amount we could borrow, and the risks we were willing to take.

On another project, I saw that a bank's quarterly floating rate could spike based on the previous year's trend. I tested that assumption in a debt-equity sensitivity and raised the risk before the documents went to the bank. I would use the same check before explaining a market move to an eFX client.

At BIDV, I wrote more than ten market insight reports on portfolios covering $40M+. I also compared more than 25 client profiles in Excel and Power BI. Those reports went into quarterly strategy meetings. I had to decide which movement mattered and explain why. For eFX Sales, that is the filter I would use when a client needs to know what matters.

I would like to discuss how I could help ING's eFX Sales team make market data useful in client conversations.

Best,
Kien Phung

### Advanced-only continuation: 2026-09-11

The browser was explicitly returned from Proofread to Advanced Scan and kept on the Advanced routes only. No Expert Feedback scan was opened in this continuation.

Cycle A:
- Advanced Sentences after draft 6: overall AI 100%, Mixed 0%, Human 0%.
- High-impact sentences: “I had to decide which movement mattered and explain why.”, “Those reports went into quarterly strategy meetings.”, “At eFX Sales, I would make the same call about what a client needs to know first.”, “Dear ING eFX Sales Team,”.
- The opening and BIDV lines changed after the minimal syntax edit; the browser was rescanned without changing the finance facts.

Cycle B:
- Advanced Patterns before the final edit: 1 instance, “Everything in threes”. The source was the factual list of maximum bid price, maximum amount borrowed, and risks.
- Edit: preserved all three facts but split them into two sentences: the bid price and borrowing amount in one sentence, then the risks in a second sentence.
- Advanced Sentences after the edit: overall AI 100%, Mixed 0%, Human 0%.
- The current high-impact lines include: “I would use the same check before explaining a market move to an eFX client.”, “In quarterly strategy meetings, I decided which movement deserved attention and explained why.”, and the combined BIDV evidence sentence. These remain evidence-backed and were not changed solely to chase the classifier.
- Advanced Patterns after the edit: 0 instances; no AI patterns detected.
- Advanced Vocab after the edit: “We did not find any common AI vocabulary in your text.”
- The browser was returned to Advanced Sentences and left there.

Current browser draft:
Dear ING eFX Sales Team,

After reading ING's June 2026 FX Talking report, I kept thinking about what a client does with the forecast. At ING's eFX Sales desk, a forecast has to become a client decision. That is what I want to learn at ING.

At FLC Group, a real-estate model once returned a 64% IRR. Projects I had seen were between 18 and 25%, so I could not explain the gap. I asked colleagues to go through the calculation with me before using it. I also prepared one-page reports for internal board meetings. Before we spoke with the banks, those reports helped us set the maximum bid price and the maximum amount we could borrow. They also made the risks we were willing to take explicit.

On another project, a bank's quarterly floating rate could spike based on the previous year's trend. I tested that assumption in a debt-equity sensitivity and raised the risk before the documents went to the bank. I would use the same check before explaining a market move to an eFX client.

At BIDV, I wrote more than ten market insight reports on portfolios covering $40M+ and compared more than 25 client profiles in Excel and Power BI. In quarterly strategy meetings, I decided which movement deserved attention and explained why. At eFX Sales, I would make the same call about what a client needs to know first.

I would like to discuss how I could help ING's eFX Sales team explain market data to clients.

Best,
Kien Phung

Rule added:
GPT-PAT-02 | Source: GPTZero Advanced Patterns | Finding: Everything in threes in a factual decision list | Permitted edit: split the list while retaining every supported item | Forbidden edit: delete a material decision factor or add an invented factor | Status: active.
