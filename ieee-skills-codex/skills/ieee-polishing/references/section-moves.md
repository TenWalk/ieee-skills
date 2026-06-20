# Section Moves: Tense and Hedging (IEEE)

Tense and hedging are not free choices — each section has a default. Apply the row that matches
the sentence's section.

| Section | Default tense | Hedging / stance | Typical moves |
|---|---|---|---|
| **Abstract** | Present for the contribution; past for the result | Confident but exact; one quantified headline | "This article proposes...", "Simulation results showed a 3 dB SNR gain..." |
| **Introduction** | Present / present perfect for background; present for the contribution | State the gap firmly; claim the contribution plainly | "RIS-aided systems have advanced...", "However, existing schemes fail to...", "We propose..." |
| **Related Work** | Present perfect / past for what others did | Neutral, factual; criticise the *approach*, not the authors | "Prior schemes have used...", "These approaches are limited by..." |
| **System Model** | Present for the standing model | Declarative; no hedging on definitions | "The base station serves K users.", "The channel follows Rician fading." |
| **Problem Formulation** | Present | Declarative; state variables and class plainly | "We aim to maximize the sum rate.", "Problem (P1) is non-convex due to the coupled variables." |
| **Proposed Solution** | Present for the algorithm as a standing object; past for fixed choices | Declarative, precise; no hedging on your own design | "The algorithm alternately optimizes...", "We set the tolerance to 1e-3." |
| **Simulation setup** | Past | Factual | "We averaged over 1e4 channel realizations.", "Simulations used a Rician channel with K=5 dB." |
| **Numerical Results** | Past + the number | Report first, then interpret with calibrated verbs | "The sum rate improved to 18 bps/Hz.", "This indicates that..." |
| **Discussion** | Present for interpretation; past when referring to your results | Hedge interpretation to match evidence | "These results suggest...", "A likely explanation is..." |
| **Conclusion** | Past for what the paper did; present/future for implication | Bounded; no new claims | "We proposed...", "Future work will..." |

## Section-specific reminders

- **Abstract:** no citations, no undefined acronyms, no equations. One headline number.
- **Introduction:** ends with the contributions list and the paper-organization sentence; the
  language there is plain and verb-first ("We propose", "We formulate", "We derive", "We show").
- **System Model / Problem Formulation:** do not hedge definitions or your own design ("we may
  use" reads as indecision). State the model, the variables, and the problem class.
- **Proposed Solution:** label each transformation exact vs approximate; state the convergence
  target (KKT / stationary / global) plainly — do not over-claim optimality.
- **Numerical Results:** never report a number without saying what it means and how it supports the
  claim; but keep the *interpretation* verb calibrated to the strength of the evidence.
- **Discussion:** this is the right place for "may", "could", "a possible explanation". Honest,
  bounded limitations strengthen the paper.
- **Conclusion:** mirror the contributions list; introduce nothing new.

## Common cross-section errors

1. Present tense for a one-time simulation action ("we average" when it already ran).
2. Hedged statements in the System Model or Proposed Solution ("we could use AO" — say which you used).
3. Bare numbers in Numerical Results with no interpretation, or strong causal verbs on weak evidence.
4. Claiming global optimality for a stationary/KKT point (calibrate to what was proved).
5. New claims or new data appearing for the first time in the Conclusion.
6. Inconsistent tense within a single paragraph.
