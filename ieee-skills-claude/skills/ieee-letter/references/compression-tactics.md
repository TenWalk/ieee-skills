# Compression Tactics: Cutting a Draft to Letter Length

Use when an existing draft exceeds the free-page budget or the current 5-page maximum. The goal is
a letter that still makes its one contribution land — not a transactions paper with sentences
deleted at random. Cut in the order below: each earlier step removes words without touching the
argument; only the last steps risk it.

## Safe-to-risky cut order

1. **Repeated numbers and definitions.** A value stated in prose and again in a table → keep the
   table, delete the prose number ("all schemes use the parameters in Table I").
2. **Table↔prose duplication.** Let tables carry numbers and prose carry reasons. Do not re-list
   parameters the table already holds.
3. **Over-fine implementation detail.** Solver settings, tolerances, and step-by-step bookkeeping
   that a reader does not need to reproduce the idea.
4. **Redundant figures.** Two figures answering the same question → keep one. Parameter-sweep
   galleries → keep the single sweep that supports the claim.
5. **Non-essential explanatory sentences.** Background the gap already implies; restatements of a
   result the figure shows.
6. **Standard derivation steps.** Replace a textbook manipulation with a citation and a one-line
   "after standard manipulation, ...". Move nothing to an appendix — letters rarely have one.
7. **Last resort — the core.** Only after 1–6: compress the result analysis and the core model.
   Never delete the contribution, the model the result needs, or the conclusion's tie-back.

Do **not** cut first: the problem motivation, the core model, the algorithm box / theorem, the
key result explanation, or the fairness-boundary sentence. Those are the letter.

## Structural cuts (bigger savings)

- **Delete the standalone Related Work section.** Fold the one or two essential comparisons into the
  Introduction's gap. This alone often recovers half a page.
- **Collapse the contributions list** into one or two sentences. A numbered 4-item list in a letter is
  padding.
- **Drop the paper-organization paragraph** (a letter is short enough to navigate without it) — unless
  the author kit requires it.
- **Merge System Model and Problem Formulation** if the problem is short: state the model, then the
  objective and binding constraints, in one section.
- **Cut secondary lemmas and variants.** A letter proves the one main result; supporting lemmas are
  sketched or cited, not stated and proved in full.

## Sentence-level density (without losing meaning)

- "in order to" → "to"; "due to the fact that" → "because"; "it is worth noting that" → delete.
- Remove hedges and fillers ("very", "quite", "obviously", "as we all know").
- One idea per sentence, subject early — short sentences fit the column better and read faster.
- See `ieee-polishing` for the full density rules; apply them as a pass, not as the primary cut.

## LaTeX/IEEEtran fitting (use sparingly, never to deceive)

Legitimate space recovery:

- Size figures to single-column (~3.5 in) instead of double when the curve is still readable.
- Use `\subref`/subfigures to combine related panels into one float.
- Tighten figure captions to one sentence; move the explanation to the prose that references it.
- Remove vertical space from over-spaced equation arrays; inline routine equations that nothing
  references later.

Do **not** shrink fonts, alter `\baselinestretch`, narrow margins, or use negative `\vspace` to game
the limit — IEEE production rejects these and a reviewer notices. If the content genuinely does not
fit within the free budget, decide whether the paid fifth page is justified. If it does not fit
within the current maximum, the letter has too much in it: cut content or move to a transactions
paper.

## After compressing — re-check

- Each remaining paragraph still has a job (gap, model, core result, result explanation, tie-back).
- Every `Fig.`/`Table`/`Eq.`/`Section` cross-reference still resolves; no `??` in the PDF.
- Equation numbering is continuous; no later text cites a deleted equation.
- Scheme names, notation, and metric names are still consistent after the edits.
- The one contribution is still stated clearly and supported by surviving evidence.
