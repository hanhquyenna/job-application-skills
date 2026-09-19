# Humanizer source-of-truth module

The humanizer may change expression. It may not change the underlying record. This module is mandatory for application letters, factual emails, and any draft containing numbers or named work.

## Claim ledger

Before editing, create one row per claim:

| ID | Original claim | Evidence source | Protected details | Confidence | Allowed treatment |
|---|---|---|---|---|---|
| C1 | The sentence as supplied | CV, experience bank, JD, or user message | names, dates, numbers, tools, URLs, order | confirmed / unresolved | keep, clarify, or remove |

Protected details include:

- names of people, employers, products, clients, and institutions;
- dates, durations, counts, percentages, currencies, ranges, and units;
- tools, APIs, frameworks, platforms, URLs, and document titles;
- who did the work, who received it, and what decision or output followed;
- qualifiers such as “could,” “may,” “I noticed,” “I checked,” and unresolved outcomes;
- chronology, simultaneity, order, and exact wording the user marked as approved.

## Evidence states

- **Confirmed:** directly present in the supplied CV, experience bank, JD, user-provided document, or verified company source.
- **Supported inference:** a low-risk grammatical connection that does not add a new event, result, or relationship; label it internally and keep it conservative.
- **Unresolved:** plausible but not evidenced. Preserve the uncertainty or return `NEEDS STORY INPUT`.
- **Rejected:** invented detail, guessed recipient, unattributed metric, or claim copied from a public example. Never use it.

## Safe transformations

Allowed:

- reorder sentences while preserving chronology;
- merge repeated claims;
- replace an abstract verb with a precise verb already supported by the evidence;
- move a number closer to the thing it measures;
- change grammar, paragraph breaks, and sentence rhythm;
- remove a claim that does not help the stated purpose.

Not allowed:

- adding a result because it would make the story stronger;
- changing “noticed” to “proved,” “could spike” to “spiked,” or “supported” to “led”;
- turning a tool into a product outcome;
- borrowing a recruiter name, company fact, emotion, or anecdote from another letter;
- making an unresolved story look resolved through polished wording.

## Final diff

After editing, compare the original and revised claim ledgers. The final audit must report:

```text
Claims preserved:
Claims weakened or strengthened:
Claims removed:
New claims: must be zero
Numbers/names/dates/URLs changed: must be zero unless explicitly approved
Unresolved points preserved:
```

If any new claim appears, restore the original meaning before continuing. Style quality never overrides evidence integrity.
