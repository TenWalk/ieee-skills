# Letter Format: What a Letter Keeps vs. What It Cuts (WCL / CL)

A letter and a transactions paper share the same IEEE register but make opposite space decisions.
The transactions paper develops; the letter delivers. Use this file to decide, section by section,
what survives the free-page budget and the 5-page maximum.

## The single-contribution test

Before drafting, name the one advance in a sentence. A letter that passes the test has exactly one
of:

- a **new algorithm** for a problem (with convergence and a complexity order), **or**
- a **new closed-form expression** (outage/BER/rate/coverage) with an asymptotic insight, **or**
- a **new scheme/architecture** with one decisive performance result, **or**
- a **new finding** that overturns or sharpens a known result.

If the draft develops two of these, it is a transactions paper. Do not try to fit both into a
letter — one will be under-supported and a reviewer will reject on depth. Route to `ieee-writing`.

## Section-by-section: keep vs. cut

| Section | Letter keeps | Letter cuts (vs. transactions) |
|---|---|---|
| **Introduction** | the gap (prior work folded in) + the one contribution | the standalone Related Work section; the 4-item numbered contributions list; long motivation |
| **System Model** | only the symbols the core result uses; the performance metric | general channel/topology the result does not exercise; secondary scenarios |
| **Problem Formulation** | the objective + binding constraints; the problem class in one line | constraint-by-constraint exposition; alternative formulations |
| **Proposed Scheme / Analysis** | the one algorithm box OR the one theorem + its proof sketch | secondary lemmas; full appendix proofs (letters rarely have appendices); multiple variants |
| **Simulation Results** | 2–4 decisive figures/tables, claim-first; one validation + one key comparison | parameter-sweep galleries; redundant tables; design-analysis ("w/o") unless it is the contribution |
| **Conclusion** | 3–4 sentences | future-work paragraphs; restated results |

## Introduction in a letter

The transactions introduction ends with a numbered contributions list and a paper-organization
paragraph. The letter does neither by default:

- **Fold prior work into the gap.** Two or three sentences: what exists, the specific limitation,
  the technical cause. Cite tightly; a letter's reference list is short.
- **State the contribution in 1–2 sentences**, verb-first: `In this letter, we propose/derive
  [advance], which [benefit]. Unlike [prior schemes], it [distinction].` A numbered 4-item list reads
  as padding in a letter.
- **Drop the organization paragraph** unless the journal expects it (CL/WCL usually do not need it in
  a short letter). Verify in the author kit.

## The core section is the paper

In a letter, Section III (proposed scheme or analysis) plus Section IV (results) are where the
contribution lives. Budget them generously and compress I–II to protect them:

- **Algorithm letter:** the reformulation (named, labelled exact/approximate) → the algorithm box →
  one sentence each on convergence target and per-iteration complexity order. The box itself is the
  contribution; keep it complete.
- **Analysis letter:** assumptions → the derivation (compressed; cite standard steps) → the theorem
  (closed form) → an asymptotic corollary (diversity order / DoF / high-SNR slope). The corollary is
  the insight a reviewer remembers — keep it even if the full derivation is sketched.

## Figures and tables in a short letter

- **2–4 figures/tables total by default.** One validates the analysis (closed-form line +
  Monte-Carlo markers) if the letter derives an expression; one shows the single most important
  comparison vs benchmark schemes. A compact experimental/testbed figure is justified only when it
  is central evidence, not extra decoration.
- **Vector format (EPS/PDF)**, readable at single-column width (~3.5 in). See `ieee-figure` for the
  rcParams and BER-vs-SNR/convergence patterns.
- **Tables are expensive in a letter.** A simulation-parameters table is usually worth it; a
  complexity-comparison table only if complexity is part of the contribution. Otherwise put the few
  parameters in prose.

## EDICS (IEEE Communications Letters)

CL requires an **EDICS** (Editor's Decision Information Classification System) category at
submission; WCL does not. Pick the EDICS code(s) that match the contribution from the journal's
current EDICS list (on the CL submission page) and place them where the author kit specifies. If
unsure, choose the single best-fitting category and tell the user to confirm against the live list —
do not invent a code. (Reference/keyword mechanics: `ieee-citation`.)

## Anonymity (double-anonymous option)

CL offers a double-anonymous review option; if the user chooses it, scrub author names, affiliations,
funding that identifies the group, and self-citations phrased in the first person ("our previous work
[x]" → "the work in [x]"). WCL is single-blind by default. Confirm the current policy in the author
kit.

## Pre-submission letter checklist

1. Exactly one contribution; it is stated once, clearly, in the Introduction.
2. No standalone Related Work section; prior work is in the gap.
3. Within the free-page budget unless the paid fifth page is explicitly justified; never over the
   current 5-page maximum.
4. 2–4 decisive vector figures/tables; the derived expression (if any) is validated by a simulation
   overlay.
5. Fairness boundary of comparisons stated in one sentence.
6. EDICS selected (CL); anonymity handled if double-anonymous (CL).
7. US English, numbered citations `[n]`, consistent notation and scheme names.
8. No over-claim ("first", "optimal", global optimality for a stationary point) beyond what is proved.
