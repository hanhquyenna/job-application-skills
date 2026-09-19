# Humanizer voice-profile module

“Human” is not one tone. The target is the writer's observed habits. Build the profile from at least three approved samples when possible, and distinguish stable habits from a one-off phrase.

## Profile schema

```yaml
author: Kien Phung
language: English
register: direct professional
audience: hiring teams and finance stakeholders
sentence_length: short decisive sentences mixed with longer explanatory sentences
paragraph_rhythm: 2–5 sentences; one concrete event or decision per paragraph
openings: begin with a named report, event, or first-person observation
agency: name who noticed, checked, ran, raised, wrote, or decided
contractions: natural and selective
transitions: sparse; prefer time, cause, or contrast over formal signposts
punctuation: do not add em dashes or semicolons automatically
technical_terms: keep load-bearing finance and engineering terms when evidenced
stance: preserve uncertainty and first-person judgement
closings: concrete contribution plus a modest invitation to talk
avoid: inflated claims, generic praise, forced morals, poetic mic-drop lines
approved_anchors: ["I stopped at the number.", "I could not explain the gap.", "before letting it travel further."]
```

## What to measure from samples

Record ranges rather than forcing a target average:

- sentence-length distribution and the location of short sentences;
- paragraph length and whether the writer varies it;
- frequency of “I,” contractions, “And,” and “But” at sentence starts;
- punctuation rate, especially dashes, semicolons, parentheses, and colons;
- preferred verbs for noticing, checking, explaining, and deciding;
- how the writer states uncertainty, disagreement, and incomplete outcomes;
- opening and closing shapes;
- recurring domain nouns and words the writer never uses.

## Calibration loop

1. Ask the writer to mark one raw draft and one hand-edited version as a pair.
2. Extract the change: structure, rhythm, word choice, evidence, or register.
3. Add only repeatable preferences to the profile.
4. Test on an unseen passage with the facts frozen.
5. Read aloud and let the writer reject any change that is grammatically fine but unlike them.
6. Repeat until the edits stop improving or the writer's corrections become one-off exceptions.

Public humanizer projects report useful gains from 20 or more before/after pairs, but the number is a calibration heuristic. A short sample cannot justify invented quirks, personal history, or vocabulary.

## Voice versus facts

Voice controls cadence, register, directness, transitions, and emphasis. It does not authorize the model to import an anecdote, a result, an employer detail, or a named person's style from a sample. Every new proposition must be checked against [the source-of-truth module](source-of-truth.md).
