# Sentence and Style Rules (IEEE)

## Sentence length and structure

- Target ≤ ~25 words; treat anything over ~30 as a defect to inspect. Long sentences hide the
  subject and the action.
- One idea per sentence. If a sentence has two independent clauses joined by "and"/"while" that
  each carry a claim, split them.
- Put the grammatical subject early and keep subject and verb close.
- Prefer a concrete subject ("the receiver", "the algorithm", "the sum rate") over "There is/are"
  and "It is ... that" openings.

## Voice

IEEE accepts both voices. Use whichever is clearer for the sentence:
- **Active** for the contribution and design: "We propose...", "The algorithm alternately
  optimizes...".
- **Passive** is fine for procedures where the agent is obvious: "The results were averaged over
  1e4 channel realizations." Do not contort a sentence into passive just to avoid "we".

## Tense (summary; see section-moves.md for the per-section table)

- Established facts / the proposed method as a standing object: present.
- What you did (simulations, derivations, procedures): past.
- Results: past, with the number ("the sum rate improved to 18 bps/Hz").

## Acronyms

- Define at first use in the body: "reconfigurable intelligent surface (RIS)", then "RIS".
- Do **not** put acronyms in the title; avoid undefined acronyms in the abstract (and if used
  there, define them again at first use in the body — the abstract is read separately).
- Do not define an acronym you use only once; just write it out.
- Use standard community acronyms; do not coin an acronym for a phrase used twice.

## Articles (a / an / the) — frequent non-native slip

- Singular countable nouns need an article or a determiner: "a scheme", "the channel", "this
  algorithm".
- "the" for a specific/previously introduced thing; "a/an" for first/general mention.
- No article for uncountable or general plural concepts: "Performance improves", "Fading channels...".

## Numbers and units

- SI units; a non-breaking space between number and unit: "10 ms", "3.5 dB", "5 GHz" (no space
  for "%" in IEEE: "92.4%").
- Spell out integers below 10 in running prose unless paired with a unit ("three benchmark schemes",
  "5 ms"). Be consistent.
- Use a leading zero: "0.5", not ".5". Use the en dash for ranges: "10–20".
- Report uncertainty consistently (mean ± std) and to a sensible number of significant figures.

## US English (IEEE house style)

`color, behavior, analyze, modeling, modeled, optimize, center, fiber, labeled, normalization,
generalize, minimize, traveled`. Avoid British forms (`colour, behaviour, analyse, modelling,
optimise, centre, fibre, labelled`). Note: IEEE is US English — the opposite of Nature.

## Words and habits to avoid

- Filler: "it is worth noting that", "as we all know", "obviously", "clearly", "in order to" (→
  "to"), "due to the fact that" (→ "because").
- Vague quantifiers: "some", "a lot of", "very", "quite", "significantly" (unless it denotes
  statistical significance with a test).
- Absolutes without proof: "always", "never", "optimal", "the best", "completely solves",
  "the first ever".
- Anthropomorphism: "the model thinks/wants/believes".
- Contractions ("don't", "it's"), "etc.", and "&" in formal prose.
- "novel" more than once or twice; let the contribution show novelty.

## Citation phrasing (IEEE numbered)

- Bracketed numbers by order of appearance: "Prior work [3], [4] ...". For ranges "[5]–[8]".
- Author-prominent: "Smith et al. [12] proposed ...". Non-prominent: "... has been studied
  [12]."
- Do not use the bracket as a noun: write "the method of [12]" or "the authors of [12]", not
  "in [12], they ...". (Some journals tolerate it; prefer the cleaner form.)
- Cite only sources actually read; do not pad. (Formatting the entries themselves: `ieee-citation`.)

## Quick reviewer-irritant checklist

1. A 40-word sentence with two claims.
2. "significantly" with no statistical test.
3. British spelling in a US-English journal.
4. Acronym used before definition, or defined in the title.
5. Missing article before a singular countable noun.
6. Over-claim verb ("prove", "guarantee") on single-experiment evidence.
