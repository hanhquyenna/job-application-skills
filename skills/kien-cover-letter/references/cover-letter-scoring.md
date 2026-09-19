# Cover-letter barrier and persuasion rubric

Use this rubric after the JD and evidence map are complete and before formatting. It evaluates whether a reader can understand the candidate's judgement, evidence, and reason for applying. It is a revision aid, not a prediction of hiring or an AI-detector result.

## 1. Hard barriers

A draft is `HOLD` if any critical barrier fails. A high numeric score cannot override a failed barrier.

| Barrier | Pass condition | Typical failure |
|---|---|---|
| Active JD | The role, location, seniority, application route, and JD source are current and recorded. | The letter uses a stale or inferred role. |
| Evidence traceability | Every factual claim maps to approved candidate evidence; numbers, tools, employers, dates, and uncertainty are unchanged. | A tool keyword becomes an invented responsibility or result. |
| Story integrity | One primary story contains a real event or signal, Kien's decision, the action/method, and a supported consequence or honest unresolved result. | `At Company X` becomes a task/tool/metric list, or a result is invented to complete the arc. |
| Employer reason | The opening contains one concrete, traceable company or team detail, or the research log records that no suitable detail was available and Kien approved a direct role-based opening. | The company name can be swapped without changing the paragraph. |
| Role bridge | The letter connects the story to at least two high-priority JD requirements and states a plausible day-one contribution. | It repeats the CV without explaining why the evidence matters here. |
| Voice and integrity | The draft survives a read-aloud and humanizer audit without stock application filler, detector-chasing edits, fake errors, or changed meaning. | The prose is polished but generic, or is made awkward to evade a detector. |
| Length and format | It meets the requested limit and has no formatting defect that hides content. | Overlong letter, decorative layout, or broken output. |

If a barrier is `FAIL`, return the blocker and the smallest missing input or revision needed. Do not silently downgrade it to a score.

## 2. Weighted persuasion score (100 points)

Score each dimension from 0 to 5 using the anchors below, then calculate `points = rating / 5 × weight`.

| Dimension | Weight | 0 | 3 | 5 |
|---|---:|---|---|---|
| Employer hook and understanding | 20 | No employer-specific detail | Names a real detail but connection is thin | Names a verified, role-relevant event/problem and shows why Kien noticed it |
| Story tension and progression | 25 | No event or decision | Event and action exist but the reason for the choice is unclear | Reader sees the signal, Kien's choice, method, consequence/rule, and the turn into the role |
| Evidence credibility | 20 | Unsupported or inflated | Mostly traceable but scope or result is vague | Concrete facts, numbers, constraints, and honest uncertainty are all preserved |
| Role relevance and day-one value | 20 | No link to the JD | Some requirements match but contribution is generic | Two or more priority requirements are evidenced and the contribution is specific |
| Personal motivation | 10 | Generic enthusiasm | Interest is stated with limited personal reason | A supplied personal reason or reaction explains why this team and work matter |
| Natural voice and readability | 5 | Templated or hard to read | Clear but noticeably polished or repetitive | Sounds like Kien's approved sample: direct, uneven, concrete, and easy to read aloud |

### Minimum floors

A letter is not `SEND` unless it also reaches: story ≥4/5, evidence ≥4/5, role relevance ≥4/5, employer hook ≥3/5, and voice ≥3/5. A weak personal-motivation score can be repaired with one supplied detail; it cannot be filled with invented passion.

### Decision bands

- **85–100: SEND** only when every critical barrier passes and no factual issue remains.
- **75–84: REVISE** the lowest-scoring dimension, then rescore. Do not run a synonym-only pass.
- **0–74: REBUILD** the hook or story selection. Ask for missing evidence when the primary story cannot reach 4/5.
- **Any critical barrier fail: HOLD** regardless of total points.

## 3. Review order and report

1. Check barriers first.
2. Score the six dimensions with one evidence sentence per rating.
3. Run the JD requirement matrix and factual diff separately; ATS keyword coverage is diagnostic and cannot increase the persuasion score by itself.
4. State the decision, the lowest dimension, and one concrete edit or missing fact.
5. After a revision, rescore only the changed dimensions plus all barriers; keep the prior score visible for comparison.

Use this report shape:

```text
Barrier status: PASS / HOLD
- Active JD: ...
- Evidence traceability: ...
- Story integrity: ...
- Employer reason: ...
- Role bridge: ...
- Voice and integrity: ...
- Length and format: ...

Persuasion score: __/100
- Employer hook (20): __/5 — evidence/reason
- Story progression (25): __/5 — evidence/reason
- Evidence credibility (20): __/5 — evidence/reason
- Role relevance (20): __/5 — evidence/reason
- Personal motivation (10): __/5 — evidence/reason
- Natural voice (5): __/5 — evidence/reason
Decision: SEND / REVISE / REBUILD / HOLD
Next action: one specific edit or one missing user-supplied fact.
```

## Why these gates exist

The rubric follows recurring guidance from university career centers: use concrete claims, show that the candidate researched the employer, connect evidence to the job, and keep the letter concise ([Broad Institute communications lab](https://mitcommlab.mit.edu/broad/commkit/cover-letter-for-a-job/), [Dartmouth Center for Career Design](https://careerdesign.dartmouth.edu/resources/cover-letter-guide/), [University of Wisconsin SuccessWorks](https://successworks.wisc.edu/wp-content/uploads/sites/39/2017/05/Cover-Letter-Basics-Packet-June2013.pdf)).

It gives personal motivation its own dimension because research from Tilburg University found that AI mainly improved generic cover-letter sections while doing less for personal motivation and clarity ([Tilburg University](https://www.tilburguniversity.edu/current/press-releases/ai-improves-cover-letters-worsens-matching-labor-market)). It keeps natural voice separate because expert editors can identify AI idiosyncrasies and prefer meaningful human edits over automatic polishing ([LAMP study](https://arxiv.org/abs/2409.14509)). It deliberately excludes detector scores: OpenAI reported that its own classifier was unreliable and retired it ([OpenAI](https://openai.com/index/new-ai-classifier-for-indicating-ai-written-text/)).

Anonymous Reddit examples can suggest patterns such as a specific company detail, a concrete proof point, and a reason the work matters, but they are not outcome evidence. Do not use claimed success rates from example sites to award points.
