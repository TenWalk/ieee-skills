# ieee-polishing

Sentence-level polishing of academic prose to IEEE journal style, including Chinese→English
translation. This skill changes **wording, not facts** — it never adds claims, numbers, or
citations the author did not provide. For rebuilding the argument or a whole section, use
`ieee-writing` first.

## What it enforces

- US English (IEEE house style): color, analyze, modeling, behavior.
- Readable sentence length (≈ ≤ 25 words) and one idea per sentence.
- Section-appropriate tense and calibrated hedging (show → indicate → may).
- Acronym discipline, article correctness, precise verbs, removal of filler.
- IEEE numbered-citation phrasing `[n]`; SI units and number formatting.
- Overclaim detection (absolutes, unwarranted causation, unverified "first").

## Structure

```
ieee-polishing/
├── SKILL.md
├── README.md
└── references/
    ├── sentence-and-style.md   length, acronyms, articles, voice, units, US-English, words to avoid
    └── section-moves.md        tense + hedging per section
```

## Output

Plain, copy-pasteable text plus a short change log of substantive edits and flags for any
sentence that needs an author-supplied fact.
