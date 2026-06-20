# Body-Text Revision Skills

A set of general principles for **revising and compressing** an existing manuscript body, distilled
from cross-disciplinary engineering/CS writing practice. Use when the user asks to tighten,
shorten, restructure, or de-confuse text that already exists. The aim is not fewer sentences but
sentences that each carry a clear function.

## 1. Problem logic before method structure

Establish why the problem deserves this treatment before introducing method modules. The reader
must understand the relationships inside the problem before the method can look reasonable.
Pattern: `phenomenon/background → limitation of current handling → the overlooked relation →
therefore a new framework is needed`. Check: before any module appears, does the reader already
know what structural problem it solves?

## 2. Information flow, not module stacking

Describe how information moves and is used, not a list of parts. Answer: from where, transformed
how, into which task, why it helps the goal. (See `method.md` for the worked example.)

## 3. General form, then the adopted simplification

Acknowledge the general case, justify the simplification within scope, then adopt it, and note the
neglected part as something examined in robustness or future work. Avoids arbitrary-looking
assumptions.

## 4. Assumptions as boundary conditions, not shortcuts

For each assumption: which scenario it applies to, what it excludes, whether the exclusion affects
the main conclusion, and whether an experiment/discussion covers it. Prefer "under the considered
scenario, X isolates the main mechanism" to "we assume X for simplicity".

## 5. Number only the skeleton equations

Number the core model, problem definition, main objective, main loss, and anything referenced
later. Inline simple definitions and routine operations. If nothing refers to it and it is only a
definition, it usually needs no number.

## 6. When compressing, cut repetition before argument

Safe compression order: repeated numbers/definitions → table-vs-prose duplication → over-fine
implementation detail → non-essential explanatory sentences → only last, the results analysis and
core model. Do **not** cut first: problem motivation, core model, method information flow, key
experiment explanations, or the conclusion's tie-back.

## 7. Table and prose: divide the labour

Tables list facts (parameters, settings, categories, comparison entries, numbers). Prose explains
principle, logic and reason. If a number is in the table, do not repeat it in prose; write "all
schemes use the simulation parameters in Table X" instead of re-listing carrier frequency, antenna
count, channel model, and number of realizations.

## 8. Separate final task, auxiliary task, intermediate variable

Mark which task the paper is evaluated on, which only supports training, and which is an internal
state. Do not let an auxiliary task read as an equal contribution.

## 9. Results map to problem–method–mechanism, not just performance

A complete results story includes analysis-vs-simulation validation (the derived expression is
correct), overall performance vs benchmark schemes (effective), design analysis / "w/o" variants
(each design choice is needed), parameter sweeps (the gain holds across SNR / antennas / users),
robustness (stable under mild assumption violation, e.g. imperfect CSI), and convergence/complexity.
Each figure answers one explicit question.

## 10. Declare the fairness boundary of benchmark schemes

When comparisons are not strictly equivalent, say so. State which schemes are conventional/heuristic,
which are prior-art, which are upper/lower bounds, and the shared resource constraint (same power
budget, CSI assumption, and bandwidth). Pre-empts the reviewer's fairness objection.

## 11. Explain phenomena, do not restate numbers

Each results paragraph: what was observed → what it means → how it supports the design/claim.
"A beats B" → "A beats B, indicating the removed path contributes to the decision rather than
merely adding capacity."

## 12. Conclusion ties back to the main thread

The conclusion returns to: what problem, what key observation, what method, what was verified,
what boundary remains. It does not re-introduce equations, modules, or large number dumps.

## 13. Preserve narrative function when compressing

Each paragraph has a job (raise the problem, define the model, explain an assumption, give the
algorithm, state convergence/complexity, ensure fairness, explain a result, tie back a
contribution). Identify the job first, then cut within it. Content can shrink while the job
survives; if the job is deleted, the body fractures. Post-compression checks: does each sentence
follow from the previous one? are variables defined before use? does each algorithm step have
explicit input/output? do the simulations map to the stated contributions? does the conclusion
answer the introduction?

## 14. Keep terminology consistent

One concept, one name — across task name, scheme name, module name, variable name, benchmark-scheme
name, figure legend, and metric name. Do not call a scheme A in the table, B in the prose, and C in
the legend. Consistency matters more than varied phrasing.

## 15. Re-check cross-references and numbering after every edit

After deleting an equation, table, or section, re-check: equation numbering still continuous; no
later text cites a deleted equation; every `Table`/`Fig.`/`Section`/`Equation` label still exists;
no `??` in the compiled PDF. This is a mandatory mechanical pass before submission.

## 16. Style serves credibility, not complexity

Good academic sentences have a clear subject, a clear action, clear variables, an explicit causal
relation, no exaggeration, and no unprovable absolutes. Avoid `significantly superior in all
scenarios`, `completely solves`, `fully general`, `optimal`, `revolutionary`. Prefer `under the
considered setting`, `provides evidence that`, `indicates that`, `is used to`, `is designed to`.

---

## One-line summary

`Problem logic before method; general model before simplification; narrative chain before cutting
repetition; mechanism before performance; consistent terms before elegant phrasing.`
