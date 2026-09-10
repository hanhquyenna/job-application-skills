---
name: kien-cover-letter
description: Activate whenever Kien provides a CV + job description together and asks for a cover letter, says "write a cover letter for X" / "cover letter for this role" / "pair this with a cover letter". Both the CV and the JD must come from Kien for that specific application — never assumed or reused from another skill's bank. Parses the JD, researches one concrete company hook, selects truthful stories from the supplied CV, and writes a concise, value-forward cover-letter draft. Hand the completed draft to humanizer for the separate final prose pass, then deliver plain text and a matching .docx.
---

# Kien's Cover Letter Skill — Story-First Draft

## CALIBRATION EXAMPLE — KIEN'S OWN VOICE (ground truth, read first)

This is a real letter Kien wrote himself (HEINEKEN, AI literacy role). Every rule below is written to reproduce this voice, not the reverse — if a rule and this example ever conflict, the example wins.

> Dear Hiring Manager,
>
> The deployment of Allocation AI and AIDDA in Mexico took HEINEKEN a year because most of it was not about creating the algorithm but gaining the trust in the system, which was not made by their company and they could not understand entirely. This is the same challenge that the AI literacy and training content provided by HEINEKEN is supposed to address, and that is the exact challenge that I encounter myself all the time.
>
> In BeeBlast, clients adopted my systems not after learning how they worked but understanding the changes that they would create for their businesses. After changing my presentation in the C-suite, I got recurring AI contracts for business owners in two countries. The same situation happened on a smaller scale in Contentoo. Marketing did not trust their campaign numbers, which were delayed a week due to manual pulling, so I built the LinkedIn tracking tool to make those numbers real-time and actionable.
>
> It all comes to one point: the usefulness of any system depends on the willingness of people to use it and trust it, and this trust should be achieved through translation, not documentation. I would love the chance to talk through how my previous work could shape the skills and the muscles I'd bring to HEINEKEN's AI literacy content.
>
> Best,
> Kien Phung

What makes this Kien's voice, specifically (extracted from this letter, used as the standard from here on):

- **The opener is a case study of the target company's own work, not a compliment or a stat.** He doesn't say "I admire HEINEKEN's innovation" — he names a specific HEINEKEN project (Allocation AI / AIDDA in Mexico), states how long it actually took, and names *why*: not the algorithm, the trust. That's research depth doing the persuading, not enthusiasm.
- **The bridge sentence explicitly names the shared challenge before talking about himself.** "This is the same challenge that [the role] is supposed to address, and that is the exact challenge I encounter myself all the time." He earns the right to talk about himself by first proving he understood their problem in their own terms.
- **Proof points are told as small case studies (situation → what he did → what happened), not achievement bullets.** BeeBlast: what clients actually needed (understanding change, not mechanism) → what he changed (the C-suite presentation) → what resulted (recurring contracts, two countries). Contentoo: named problem (marketing didn't trust numbers, a week's delay from manual pulling) → what he built (LinkedIn tracking tool) → outcome (real-time, actionable).
- **A plain working rule can tie the letter together before the close.** Kien sometimes uses a line such as “It all comes to one point...”, but the line is optional. It must come from the story and should be omitted when the close is stronger without it.
- **Value and CTA collapse into one sentence, not two.** "I would love the chance to talk through how my previous work could shape the skills and the muscles I'd bring to HEINEKEN's AI literacy content" does both jobs at once — states the fit and asks for the conversation — rather than splitting into a value sentence plus a separate CTA sentence.
- **Word choice is plain and slightly physical/concrete rather than abstract-corporate.** "the skills and the muscles I'd bring" — muscles is a deliberately concrete, almost blue-collar word next to "AI literacy content," and that contrast is the point. He reaches for a plain word before a formal one every time: "gaining the trust in the system" not "building stakeholder trust"; "translation, not documentation" not "communication over process."
- **No paragraph is a list.** Every proof point is a small narrated situation, connected with plain causal or contrastive language ("The same situation happened on a smaller scale in..."), never "At Company A, I did X. At Company B, I did Y."

Use this letter as the calibration target for every draft: if a new letter doesn't have a real company-specific reason, situation-shaped proof points, and a direct value plus ask, it hasn't matched Kien's voice yet. A thesis and explicit bridge are optional and must be earned by the supplied story.

---

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

**Rule:** if the user hasn't given a real business-context fact and none is extractable from what they pasted, ask for one line before writing the opener. Never fabricate a company detail, and never fall back to generic praise ("your innovative culture") — that is the exact AI-slop failure mode this skill exists to avoid.

**Event-research gate:** before drafting, search the target employer's official newsroom, annual report, product or research site, and the job posting for a named initiative, launch, partnership, published report, or documented business problem. Record its title, date, what happened, and why it connects to the role. If a relevant event exists, use it in the opener instead of paraphrasing the JD. If the event is adjacent rather than directly part of the target team, label the connection carefully; never imply it was the same team or product. A posting contact is not automatically the addressee.

**Corollary from the recruiter source (Medium, "1,000 cover letters"): if there is genuinely nothing specific to say about this company or this fit, say so and suggest skipping the cover letter rather than manufacturing one.** A cover letter with no real signal hurts more than no cover letter.

### INPUT 4 — One real anecdote (the method proof)
Without this, every letter reads as a stacked list of achievements instead of a person. Per the FPRS authentic-cover-letter framework: a resume proves *what* happened, a cover letter has to prove *how* the person works and *why* — that means at least one small, specific, real moment, not a fourth metric. It doesn't need to be dramatic. A decision made under a deadline, a moment something almost didn't work, the actual reason a project got started, a piece of feedback that stuck.

**Rule:** if Kien hasn't given a real anecdote and none is extractable from what he's already shared this session, ask for one before drafting the body — same treatment as INPUT 3. One anecdote can be reused and reweighted across multiple letters in a batch; it does not need to be reinvented per company. Never invent a struggle, a feeling, or a "moment that broke my brain open" that Kien didn't actually describe — a fabricated origin story is a more damaging failure than a flat one, because it's a lie with his name on it, not just a boring paragraph.

---

## RESEARCH-BASED WRITING FRAMEWORK

Read [the 30-source cover-letter research framework](references/cover-letter-research-framework.md) when drafting or reviewing a letter. Its operating model is:

1. Show the employer's problem with one specific, verifiable company or JD detail.
2. Select two relevant proof points. For each, state the situation or stakes, Kien's action, the method or tool, and the result or output.
3. Connect the examples to a day-one contribution to the target team.
4. Keep the letter to three to five short paragraphs and one page. Use employer keywords only where they truthfully describe Kien's evidence.
5. Edit the final text in Kien's own voice. Remove abstract nouns, filler, forced keyword lists, generic praise, and claims that could survive swapping in another company.

The evidence base distinguishes teaching examples from outcome evidence. Published university and government samples are models of structure, not proof that the sample itself led to a hire. The strongest outcome evidence in the research set is Cui, Dias and Ye's study of approximately five million Freelancer applications: tailoring was associated with callbacks before widespread AI assistance, but the relationship weakened after AI-generated letters became common; human editing of AI drafts was associated with better outcomes. Therefore, use AI for organisation and checking, then require Kien's own manual revision and factual sign-off.

For every letter, maintain this internal map before writing:

`JD requirement → employer problem → Kien evidence → method/tool → result/output → day-one contribution`

If a sentence contains only a JD keyword and no evidence, rewrite it or remove it. Never add a keyword to improve an apparent match when the experience bank or the confirmed CV does not support it.

## STORY DEPTH AND CV NON-REPETITION

Read [the focused research on cover letters that add a person, not a second CV](references/cover-letter-humanization-research.md) when drafting or reviewing. The letter has a different job from the CV: the CV supplies the claim; the letter supplies the missing context that lets the reader see how Kien thinks.

A draft is still repeating the CV when its sentences follow `company → task → tool → metric`. Rebuild the primary body paragraph around `situation → signal that something mattered or looked wrong → choice → action → consequence or working rule → day-one relevance`. Choose one primary story and one shorter supporting proof point. The primary story needs a concrete moment and a decision point. A result may be a business outcome, a meeting or decision reached, or a supported working rule; never invent a later consequence.

For Kien, the 64% IRR and floating-rate episodes are primary-story material because they show what he noticed and chose to check. Do not reduce them to “built a model” or “ran sensitivity analysis.” Do not claim the corrected IRR, a financing change, or a project outcome until Kien supplies it. The supporting proof point may carry metrics such as 10+ reports or $40M+ portfolios, but it must support the story rather than become a second list.

Before drafting, answer: **What should the reader remember about how Kien works after closing the letter?** If the answer is a list of tools or employers, the draft is still a CV. If it is a judgement such as “he stops when the number does not make sense, checks the assumption, and makes the risk visible before a decision,” the letter has a human centre.

Use the research to keep the employer hook specific, but do not fill the opening with a paraphrase of the JD. Give Kien one sentence of personal reason grounded in a confirmed choice or moment. Replace summary theses with a first-person working rule, and make the close name the judgement the employer would see on day one.

## KIEN'S CONFIRMED PERSONAL EVIDENCE

These are user-provided stories for cover-letter personalisation. They are separate from the experience bank: use them as anecdotes only after confirming that the user still authorises the fact for the specific application. Do not silently add them to a CV, and do not convert an unresolved detail into a result.

### Finance motivation

Kien says he loves finance and practising finance. Do not use “finance is my passion” as an unsupported claim by itself. Show this motivation through the decisions and checks he chooses to make, such as testing rate risk or questioning an implausible return.

### FLC floating-rate risk story — confirmed, outcome detail still open

At FLC, Kien noticed that a bank's quarterly floating rate could spike based on the previous year's trend. He tested how the rate change affected the sensitivity analysis and raised the risk at an internal board meeting before documents were sent to the bank. The exact decision or change that followed has not yet been supplied. Ask for it before claiming an outcome.

### FLC 64% IRR sanity-check story — confirmed, correction detail still open

Kien once calculated a 64% IRR for a real-estate project. He recognised that this did not make sense because comparable projects in the same industry usually ranged from 18–25%, then sanity-checked the calculation with colleagues. The source of the error, corrected IRR, and final decision have not yet been supplied. Ask for those details before writing that the error was fixed or that the project outcome changed. Treat 18–25% as Kien's stated comparable range, not as a universal industry rule.

### BIDV impact story — not yet supplied

Kien has not yet provided who used his BIDV reports or what decision they supported. Ask this question when BIDV is selected as a proof point; do not invent a stakeholder, meeting outcome, or business result.

### Personalisation questions to ask when the evidence is thin

Ask only the questions needed for the target role:

- What specifically attracts Kien to this company and role, beyond liking the industry?
- What exact FX, market, client, or product exposure has he had, if any?
- Who made the decision after his analysis, and what changed because of it?
- What was the corrected number or final output when he found an implausible result?
- What genuine anecdote shows how he works under uncertainty, checking, or a deadline?
- Is there a real contact, event, product, customer, or company initiative that can anchor the opener?
- Which words sound unlike Kien and should be removed from the draft?

If an answer is missing and the detail is central to the opener or proof point, pause and ask. Do not fill the gap with a generic sentence.

## JD PARSING

Extract before writing anything:
- **Role type & seniority** (IC vs lead, junior vs senior signals in language)
- **Top 5–6 keywords/competencies** — the actual nouns/skills repeated or emphasized, not every bullet
- **Tone & company size signal** — startup/scrappy vs corporate/formal vs technical. Small companies read as more personal ("Hi [Team]," direct language); larger/corporate orgs expect a more traditional register. Mirror this in register, not by copying their internal jargon back at them.
- **The real problem behind the role** — per HBR: what challenge is this hire meant to solve? (e.g., a "Growth Marketer" JD heavy on "pipeline" and "conversion" is really asking "can you make our funnel convert better")
- **Industry-specific focus** (per Indeed) — weight proof points toward what this field actually cares about: admin roles → scheduling/coordination/accuracy; technical roles → tools, systems, troubleshooting; sales roles → pipeline, quota, deal cycle; healthcare → patient/clinical communication. Let the JD's own emphasis decide the weighting, not a generic template.

---

## LOGIC — HOW THE LETTER GETS BUILT

The whole letter is one argument: **[the company's actual challenge, from the hook] + [this JD's top requirement] + [a proof point the CV actually has] = why hiring me solves your problem, starting day one.**

Every sentence must serve that argument and add something new — per the recruiter source, "each sentence should add something new to the identity of the candidate." No sentence that only restates a previous one, and no sentence that could be pasted unchanged into a letter for a different company.

1. Identify the JD's #1 and #2 priorities (not all 6 keywords — just the top two).
2. Identify the actual business problem behind those priorities (HBR: don't just list what the company does — name the challenge). If a real, researchable case study of the company's own work is available, use it to diagnose the challenge concretely (see CALIBRATION EXAMPLE) rather than describing the problem abstractly.
3. Pick 2 CV proof points that map directly to those priorities, not 3. Anchor rule: every proof point needs at least one of — a process name, an audience, a metric, a timeline, or a named tool/client/output — and it must actually be in the CV provided. "I improved communication across teams" is not an anchor; "I ran the weekly handoff between sales and onboarding, which cut client setup delays" is. Two well-built proof points beat three crammed in — a third almost always turns the paragraph into a list. Tell each as a small case study — situation, what Kien did, what happened — not as an achievement bullet in prose clothing.
4. Pick the one business-context fact for the opener, and the one anecdote from INPUT 4 that shows *how* Kien works, not just what he hit.
5. Pick one tone word for this specific letter (per the Craft My Letter voice-constraint technique) — e.g. direct, understated, dry, warm — based on the company's register and what actually happened in the anecdote. Hold that tone through the whole letter; this is what stops every letter from defaulting to the same corporate-symmetric register regardless of company.
6. If this application represents a deliberate transition (industry switch, company-size switch, career pivot visible in the CV) — per the recruiter source, use one sentence to explain the "why" behind that choice. Don't over-explain; state it plainly and move on. When a real pivot exists, name the **shared underlying mechanism** explicitly instead of just asserting "transferable skills" — e.g. not "my teaching experience gave me transferable skills," but "the core engine of both roles is the same: aligning stakeholders, shipping on a fixed timeline, managing chaos without losing the room." Naming the mechanism is what makes the pivot read as insight rather than an excuse.
7. Decide whether the letter has earned a thesis sentence. Kien sometimes uses one naturally (see CALIBRATION EXAMPLE), but it is not mandatory. Use it only when the source material contains a working rule that cannot be said more plainly in the close. Otherwise end the story and move directly to the contribution and ask. Never add a universal principle just to make the structure look complete.
8. Check whether a real hiring-manager or recruiter name is discoverable (LinkedIn, the JD posting itself, the company's team page) before defaulting to "Dear Hiring Manager." A posting contact is not automatically the hiring manager: use that person's name only when the posting or direct correspondence identifies them as the addressee. A named greeting is worth the extra lookup when the role supports it; otherwise use "Dear Hiring Manager" rather than guessing.
9. Draft opener → body → optional thesis → close in that order, then run the SELF-AUDIT before delivering.

### The mechanical-list trap (check this explicitly, every letter)
The single most common failure mode isn't a banned word, it's structure: a body paragraph built as "At Company A, I did X. At Company B, I did Y. I also did Z." is a list wearing sentence punctuation, not prose — and stacking that same shape across a batch of letters (one company name swapped per copy) reads as templated even when each individual sentence is specific. Fixes:
- Use the **Problem → Action → Impact** micro-structure (per WahResume) for at least one proof point instead of "verb + object + metric": name the actual obstacle or stakes first, then the specific thing done, then the result. "A manual reporting step meant the team saw campaign performance a week late — I built a LinkedIn tracking tool that closed the gap to real time" reads as a person solving something; "I built a LinkedIn tracking tool that gave the team real-time performance data" reads as a bullet point in prose form.
- Vary the connective tissue between proof points — not every one needs "At [Company], I..." Use time, cause, or contrast instead: "That instinct came from BIDV, where...", "The same situation happened on a smaller scale at Contentoo..." (Kien's own construction — reuse this shape).
- When batching multiple letters for different companies from one CV, deliberately vary which paragraph carries the anecdote, how many proof points appear, and the opening formula used — per the swap test, if the whole *shape* of the letter is interchangeable across companies, it fails even if the sentences technically aren't.

---

## STRUCTURE — 3 OR 4 SHORT PARTS, ONE PAGE

### Paragraph 1 — Opening (hook, 2–4 sentences)
Usually does three things in this order:
1. Name the role and (briefly) who you are — no throat-clearing. (This can be implicit rather than a literal "I am applying for X" — Kien's own example never states the role by name in the opener; it's inferable from context. If the role isn't obvious from the opener alone, make sure it's named naturally somewhere in paragraph 1 or 2.)
2. The company hook from INPUT 3 — a specific, concrete fact or case study tied to a real challenge, not a compliment.
3. A connection to Kien's experience, when one is needed. Let the story make the connection directly instead of inserting a stock shared-challenge bridge.

**Opening formulas** (pick whichever fits the hook — do not default to the same one every time):

- **Case-study hook (use when researchable):** "[Company]'s [named project/deployment] took [timeframe] because [the real challenge, stated plainly]." Continue with Kien's own reaction or a concrete related decision. Do not append the shared-challenge template automatically.
- **Problem-solver hook:** "[Company]'s [specific recent fact] means [specific challenge]. My work [doing X, with anchor] is built for exactly that."
- **Specific-knowledge hook:** "[Company] [specific fact — launch, expansion, market entry]. I've spent [time period] doing [directly relevant proof point] — I'd like to bring that to [role]."
- **Direct-value hook:** "I'm applying for [role] at [Company] because [specific fact] lines up with what I've been doing at [current/past context]: [one-line proof point]."
- **Connection hook (HBR):** if a real personal or professional connection to the org exists, lead with it before anything else — it outperforms every other opener.

**Never open with:** "I am writing to express my interest in...", "I am excited to apply for...", "I came across your job posting...", "I believe I would be a great fit...", any sentence whose first clause could be pasted into any other cover letter unchanged.

### Paragraph 2 — Body (value-forward proof, 3–5 sentences)
- Structure around **day-1 contributions, not career chronology.** Never narrate "In my role at X, I did Y, then at Z I did W" — instead: "I can do [specific thing the JD needs] — I've already done [proof point with anchor] at [context]."
- 2 concrete proof points, not 3, each mapped to a JD priority. Tell each as a compact situation: what was true, what Kien did, what happened — not a flat achievement statement. At least one written in explicit Problem → Action → Impact form. Quantify what you can — pulled only from the CV provided.
- If INPUT 4's anecdote hasn't already opened the letter, fold it in here as the connective tissue between proof points, not as a third bolted-on item.
- If this is a deliberate transition, one plain sentence on the "why" (see LOGIC step 6). No apologizing, no over-explaining.
- No jargon carried over from past roles that the reader won't recognize — translate into plain language and outcomes.
- Every sentence answers "what can I do for you," not "what have I done for myself," and adds new information — cut any sentence that just restates the one before it.

### Optional thesis line (1 sentence, between body and close)
Use a thesis only when the story itself gives Kien a plain working rule in his own language. “It all comes to one point...” is available because it appears in his calibration sample, but it must not appear automatically. If the sentence sounds like a universal principle, repeats the proof point, or exists only to provide a polished transition, remove it and close from the final concrete fact instead.

### Close (1–2 sentences)
Kien's natural form is **one combined sentence** that states the value fit and the ask together (see CALIBRATION EXAMPLE): "I would love the chance to talk through how [proof points / previous work] could shape [what the role needs]." Use this combined form by default. A two-sentence close (one value sentence + one separate CTA sentence) is acceptable when the combined form gets overloaded or unclear, but is the fallback, not the default. Never exceed two sentences.

**CTA phrasing bank** (vary it, don't reuse the same one every letter):
- "I would love the chance to talk through how [proof point/experience] could shape [what the role needs]."
- "Happy to walk through [proof point] in more detail whenever works for you."
- "I'd like to talk about how [proof point] could plug into [specific company priority]."

**Make the CTA concrete when there's something real to offer.** A vague "let's talk" is weaker than naming the actual thing you'd show them — a repo, a specific project walkthrough, a dataset, a deck. Only use this if the thing genuinely exists and is genuinely relevant; don't manufacture an artifact that isn't real.

**Never close with:** "I look forward to hearing from you" alone with no substance, "Thank you for your time and consideration" as the entire close, "I am confident I would be a valuable asset to your team."

### Alternate format — the JD-mapped variant (only when it genuinely fits)
Default to the narrative structure above every time. There's one situation where a different structure outperforms it: a JD that explicitly lists 3+ numbered responsibilities and the hiring process is clearly high-volume/corporate screening (large company, formal ATS portal, generic "Dear Hiring Manager" territory). In that specific case, a "Your Need → My Experience" mapping — one line per JD requirement, each paired with a quantified proof point — reads as more scannable than prose to a recruiter moving fast through a stack. Use short bullet pairs, not a full two-column table.

**Never use a real table (`<w:tbl>` / grid layout) for this.** The same ATS structural-parseability risk documented in `/cv-validator` applies here — a naive parser can read all the "Need" cells before all the "Experience" cells, scrambling the pairing entirely. If Kien wants this format, build it as bullet pairs in plain paragraph/list flow, never a bordered or borderless table, and only offer it as an option — ask before switching away from the default narrative format, since it changes the whole feel of the letter and Kien may not want that for every application.

## USER LANGUAGE PRESERVATION — HIGHEST PRIORITY WHEN A DRAFT IS PROVIDED

When Kien supplies a draft or a replacement paragraph, treat his wording as the source of truth for voice. Preserve his vocabulary, sentence shape, level of directness, causal logic, and chosen technical names. The calibration example describes the target voice, but it does not authorize replacing Kien's own phrasing with smoother or more corporate synonyms.

When Kien says **"exact wording," "use my language," or "minimal fix,"** make only the requested mechanical changes: grammar, punctuation, spelling, spacing, and an unambiguous clarity error. Do not rewrite for style, add claims, change a metric, swap a product name, reorder the argument, or replace a phrase merely because another phrase sounds more native. Keep slightly non-native phrasing when its meaning is clear and Kien has chosen it.

If a structural change is necessary, such as removing a duplicated paragraph, state that change explicitly and leave the remaining sentences unchanged. If a grammar correction could change the meaning, show the original and proposed wording before applying it. When asked to remove em dashes, remove them without introducing new punctuation-heavy phrasing or changing the surrounding language.

For the DOCX, copy the final approved text verbatim from the chat draft. Run a content diff so the file does not silently receive a polished alternative. In the change report, show concise before → after snippets for every mechanical edit.

---

## TONE OF VOICE — NON-NEGOTIABLE (from Kien's stored writing-style rules)

- **Value-forward:** every sentence answers "what can you do for us," never "what do I want."
- **Plain language over corporate abstraction, and prefer the concrete/physical word over the formal one when both are available** — "muscles" over "capabilities," "translation" over "communication strategy," "gaining the trust in the system" over "building stakeholder trust." No industry jargon carried over from past roles. Demonstrate expertise by dropping specific current facts, not by claiming interest or passion.
- **Day-1 contributions, not chronology.** Never structure the body as a timeline of past jobs.
- **Proof points are told as small case studies (situation → action → result), not achievement bullets restated as sentences.**
- **A working-rule thesis may compress the letter before the close.** Use it only when Kien has supplied the rule or the story earns it; it is not a required hallmark.
- **No self-praise adjectives, ever:** passionate, prestigious, elite, motivated, hardworking, dynamic, detail-oriented, results-driven, driven, dedicated, ambitious, innovative (as a self-description).
- **Close of one or two sentences, combining value and CTA where natural.** No exceptions on the two-sentence ceiling.
- **No jargon-heavy project dumps** that confuse rather than persuade — one clear proof point beats three vague ones.
- Match the company's register (startup vs corporate) in formality level only — never mimic their internal jargon back at them.

### CONTENT-LEVEL TONE RULES

Keep the argument direct and useful. Avoid empty praise, self-praise, unsupported enthusiasm, and claims that could survive swapping in another company. Use the concrete wording Kien supplied and make each proof point a small case study rather than a resume bullet in prose. `humanizer` owns the sentence-level AI-pattern list, rhythm checks, punctuation cleanup, and generic-phrase removal after this draft is factually complete.

## HANDOFF TO HUMANIZER

Do this only after the story draft, JD mapping, and factual audit are complete:

1. Pass the exact draft and Kien's supplied writing sample to `humanizer`.
2. Tell `humanizer` to protect every company name, role, date, metric, tool, output, uncertainty, and phrase Kien marked exact.
3. Allow changes to sentence rhythm, connectors, punctuation, and paragraph shape only when they preserve the same facts, story order, and meaning. It may remove generic or AI-sounding language, but it may not add a hook, thesis, result, keyword, or employer fact. Require its literal count gate and one Signal I audit loop before it returns the text.
4. Run that prose pass once. Return to this skill only for the final JD, evidence, date, metric, recipient, and length checks. If the prose is still empty, select a better story or ask Kien for evidence instead of asking for another synonym pass.
5. Build the DOCX from the final approved text verbatim and run the content diff described below.

The goal is a letter with a concrete moment, a decision Kien actually made, and a clear reason the story matters to this employer. If the draft is thin after sentence-level cleanup, return to story selection or ask Kien for evidence; do not pad it.

## FORMATTING SPEC

- **Length:** 250–320 words is the target zone, 400 is the hard ceiling, fits one page. A tight 250–300 words with real specificity outperforms a padded 400. If a letter is running long, cut a supporting proof point before cutting the main anecdote; a thesis line is optional and should be the first structural sentence removed when it sounds manufactured.
- **Layout:** block format, flush left, no indentation. Single-spaced within paragraphs, one blank line between paragraphs and between header/greeting/body/sign-off.
- **Header (for the docx/print version only — omit if delivering as an email body):**
  1. Name, city, email, phone — pulled from the CV provided this session
  2. Blank line
  3. Today's date
  4. Blank line
  5. Recipient's name/title and company name, if known — otherwise omit this block rather than guessing
- **Greeting** — adapt to company size/culture (per the recruiter source):
  - Hiring-manager/addressee name explicitly identified + traditional/corporate JD tone → "Dear [Name],"
  - Posting contact name only, with no indication they are the addressee → use "Dear Hiring Manager,"
  - Name unknown + traditional/corporate tone → "Dear Hiring Manager,"
  - Small company / startup with informal JD tone → "Hi [Team/Company] Team," is acceptable
  - Never "To Whom It May Concern," never "Hey"
- **Sign-off** — match the same register as the greeting: "Best," or "Sincerely," for traditional/corporate; "Best," or a first-name-only sign-off is fine for informal startup contexts. Followed by the typed name pulled from the CV.
- **Font/style:** Arial. If generating a .docx, use the same Google-Docs-safe font-embedding fix as any Arial-based docx build (post-process styles.xml so no style falls back to a substituted font).
- **ATS-safe:** no images, no text boxes, no tables for the body text (a header block may use a borderless 2-column table if a right-aligned date is wanted), no decorative elements. Plain extractable text throughout.
- **File naming:** `[FirstName]_[LastName]_[Company]_[Role]_CoverLetter.docx`, using the name from the CV provided.

---

## OUTPUT

Always deliver both:
1. **Plain text in chat** — the final text after the single `humanizer` pass, ready to paste into an email body or application portal text box.
2. **A matching .docx file** — built with docx.js + JSZip, Arial throughout, Google-Docs-safe (font-embedding fix, no tab stops for date alignment, DXA table widths if a header table is used). If `docx` and `jszip` aren't already installed in the build environment, install them first:
   ```bash
   mkdir -p /tmp/coverletter_build && cd /tmp/coverletter_build && npm install docx jszip
   ```
   Build the header block, body paragraphs (plain `Paragraph`/`TextRun`, no bullets needed for a cover letter), and sign-off, then run the same `injectFontsIntoStyles` post-processing step so the file renders identically in Word, Preview, and Google Docs.

---

## SELF-AUDIT — RUN BEFORE DELIVERING

- [ ] Both a CV and a JD were provided for this specific application — nothing assumed or reused from another source
- [ ] Opener uses a real, specific business-context fact or case study tied to an actual company challenge — not generic praise, not fabricated
- [ ] Any bridge sentence earns its place by adding a specific connection; remove the stock shared-challenge template when the story already makes the connection
- [ ] If no real hook existed, you asked for one instead of inventing it — or flagged that a cover letter may not add value here
- [ ] A real anecdote (INPUT 4) is present and shapes at least one proof point — if none was given, you asked instead of inventing one
- [ ] Proof points are told as small case studies (situation → action → result), not achievement bullets in prose clothing
- [ ] At least one proof point uses Problem → Action → Impact, not flat "did X, got Y"
- [ ] If a thesis sentence is present, it is a plain working rule from Kien's story and is not there only to complete the structure
- [ ] If drafting a batch for multiple companies from one CV: the shape differs letter to letter (which paragraph carries the anecdote, proof-point count, opening formula) — not just the company name swapped into one template
- [ ] You checked for a real, discoverable recipient name before defaulting to "Dear Hiring Manager"
- [ ] If a career pivot is in play, the letter names the shared mechanism explicitly, not just "transferable skills"
- [ ] The close combines value and ask into one or two sentences max, concrete wherever something genuine exists to offer
- [ ] The draft was handed to `humanizer` only after the story and factual draft were complete; that pass changed no facts
- [ ] Every proof point in the body has a concrete anchor (number, named client, named tool, or named output) and is actually present in the CV provided
- [ ] Body is structured around day-1 contributions, not "in my role at X, then at Y" chronology
- [ ] Every sentence adds new information — none just restates a previous sentence
- [ ] No resume bullet copied verbatim — everything rephrased in first-person prose
- [ ] Word choice favors plain/concrete over corporate-abstract wherever both are available
- [ ] The final text keeps the concrete event, decision, and company-specific reason from the approved draft
- [ ] No invented fact, name, date, or metric introduced by `humanizer`
- [ ] Total length 250–400 words, fits one page
- [ ] Greeting/sign-off register matches the company's size and tone from the JD
- [ ] File saved as `[Name]_[Company]_[Role]_CoverLetter.docx`, opens correctly in Google Docs
