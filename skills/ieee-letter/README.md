# ieee-letter

Write or compress an **IEEE communications letter** — IEEE Wireless Communications Letters
(WCL) or IEEE Communications Letters (CL). A letter is a single-contribution paper under a tight
page budget, not a shortened transactions paper. For full transactions papers (JSAC/TWC/TCOM) use
`ieee-writing`.

## What it enforces

- **One contribution**, stated once: one algorithm, one closed-form expression, one scheme, or one
  decisive finding. Two contributions → it is a transactions paper.
- **The free-page budget as a design constraint**: a page budget planned before drafting, core-first,
  with any paid fifth page treated as a strategic decision.
- **No standalone Related Work**; prior work folded into the Introduction's gap.
- **2–4 decisive vector figures/tables**, with an analysis-vs-simulation overlay when the letter derives an expression.
- **WCL vs CL differences**: EDICS (CL only), page-charge handling, and the double-anonymous option
  (CL) handled explicitly.
- No fabricated numbers, channel models, or benchmark schemes; gaps become placeholders.

## Structure

```
ieee-letter/
├── SKILL.md
├── README.md
└── references/
    ├── letter-format.md         keep-vs-cut by section, the single-contribution test, EDICS, anonymity, checklist
    └── compression-tactics.md   safe→risky cut order, structural cuts, honest LaTeX fitting, re-check pass
```

## Output

The letter (IEEEtran LaTeX if requested), a per-section page-budget estimate against the free-page
budget and the 5-page maximum, a claim–evidence map, and a cut list of what was removed (or must be)
to fit.

## Relationship to other skills

Use `ieee-writing` for the section-level argument (applied compressed), `ieee-experiments` for the
simulation content, `ieee-figure` for the figures, `ieee-citation` for references and EDICS, and
`ieee-response` for the cover and reviewer-response letters.
