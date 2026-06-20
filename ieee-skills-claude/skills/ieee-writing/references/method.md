# System Model, Problem Formulation, and Proposed Solution (IEEE Communications)

## Goal

Let a reviewer reconstruct the system, the optimization problem, and the algorithm — and judge why
each part exists. Describe **signal/information flow**, not a symbol dump. A reader should always
know: what is transmitted, how the channel transforms it, what is received, what is being
optimized, and why the proposed solution is valid.

## Default structure (transactions: JSAC/TWC/TCOM)

```
II.  System Model
       network/topology → channel model → transmit & receive signal → performance metric
III. Problem Formulation
       objective + every constraint (with meaning) → problem class → why it is hard
IV.  Proposed Solution / Algorithm
       reformulation/transformation → algorithm → convergence → complexity
(V.) Performance Analysis        (analytical papers: derive outage/BER/rate; proofs → appendix)
```

Number the sections with Roman numerals (IEEEtran). For an analysis paper, Performance Analysis
replaces or precedes the algorithm; for an optimization paper, the algorithm is the core.

## System Model — describe the signal flow

State, in order: the network/topology (nodes, antennas, users), the channel model (fading,
path loss, what is known/estimated), the transmitted signal, and the received signal with noise.
Then **define the performance metric** (SINR, rate, outage, EE) as an equation, because the whole
paper optimizes or analyses it.

Weak (symbol dump):

> Let **H** be the channel, **w** the beamformer, **s** the symbol, **n** the noise.

Strong (signal flow):

> The base station precodes the symbol $s_k$ with beamformer $\mathbf{w}_k$ and transmits
> $\sum_k \mathbf{w}_k s_k$ over the channel $\mathbf{h}_k$, so user $k$ receives
> $y_k = \mathbf{h}_k^{H}\sum_j \mathbf{w}_j s_j + n_k$. The resulting SINR (1) determines the
> achievable rate (2), which the design in Section III maximizes.

For each quantity, answer: *where does it come from, how is it transformed, what does it feed?*

For an emerging architecture (RIS, NOMA, ISAC, near-field, movable/fluid antenna, cell-free,
mmWave/hybrid, semantic), `references/system-model-paradigms.md` lists the model elements reviewers
expect, the distinctive variable/constraint, the signature metric, and the common pitfalls.

## Problem Formulation — objective and constraints carry meaning

Write the optimization problem with a numbered display, then explain **each constraint in words**
(power budget, QoS/rate floor, unit-modulus for phase shifters, etc.). Classify the problem
(convex / non-convex / MINLP / fractional) and say **why it is hard** — coupling, non-convex
constraint, integer variables. This sets up the solution and pre-empts "why not just solve it
directly?".

## Proposed Solution — the transformation chain is the contribution

Make the path from the hard problem to a solvable one explicit and motivated:

> The non-convex coupling in (P1) is handled by [SCA / SDR / fractional programming (Dinkelbach) /
> ADMM / alternating optimization]; each subproblem is convex and solved by [CVX / closed form].

Then give an **algorithm box** (inputs, iteration, stopping criterion, output), and **state
convergence and complexity** (proofs and the formal claim go to `references/theory-and-proofs.md`).
Do not bury the key transformation inline — it is what the reviewer evaluates.

If the "solution" is a neural network or learning algorithm (DL / deep unfolding / DRL) rather than
an optimization algorithm, the section becomes **Proposed Network**: architecture, loss tied to a
comms metric, training methodology, and inference complexity vs the model-based benchmark — see
`references/learning-based-comms.md`.

## General form before simplification

When the model makes an assumption (perfect CSI, single antenna, independent fading), do not write
`we assume X for simplicity`. Acknowledge the general case, then justify within scope:

```
In the general case, [full model, e.g., imperfect CSI / correlated fading].
Under the considered conditions, [why the simplification is reasonable].
We therefore adopt [simplified model].
The neglected effect [e.g., estimation error] is examined in [robustness simulation / future work].
```

This shows you know the boundary and lowers reviewer risk.

## Assumptions as boundary conditions, not shortcuts

For each assumption (perfect CSI, block fading, ideal hardware), make explicit: the scenario it
applies to, what it excludes, whether the excluded case affects the main conclusion, and where a
simulation or discussion covers the boundary. Prefer:

> Perfect CSI is assumed to isolate the gain of the proposed design; the impact of channel
> estimation error is evaluated separately in Section V.

## Equation numbering — number only the skeleton

Comms papers are equation-heavy; numbering everything makes the body loose. **Number** the
channel/received-signal model, the metric definition (SINR/rate/outage), the optimization problem
(P1), the main reformulation, any derived closed form, and anything referenced later. **Inline or
leave unnumbered** routine algebra, intermediate substitutions, and one-off definitions. Rule of
thumb: if nothing later refers to it and it is just a definition, do not number it.

Notation hygiene (comms convention):
- Bold lower case = vectors ($\mathbf{h}$), bold upper case = matrices ($\mathbf{H}$),
  calligraphic = sets ($\mathcal{K}$); $(\cdot)^{T}$, $(\cdot)^{H}$, $\|\cdot\|$,
  $\mathbb{E}[\cdot]$, $\mathcal{CN}(0,\sigma^2)$.
- Define every symbol once at first use; a notation table or a "Notation" paragraph at the end of
  the Introduction helps for symbol-heavy papers.
- Do not reuse a symbol for two meanings; do not rename a quantity between System Model and
  Numerical Results.

## Distinguish optimization variable, channel input, and auxiliary variable

State clearly which quantities are **optimization variables** (what the algorithm solves for),
which are **given** (channel, noise, budget), and which are **auxiliary/slack** variables
introduced by a reformulation. Do not let an auxiliary variable read as part of the system model.

## Common failure modes

1. System model is a symbol list with no signal flow; the metric is never defined as an equation.
2. The optimization problem appears with no statement of which variables are optimized or why it is
   hard.
3. The key reformulation (SCA/SDR/...) is buried inline; the reader cannot see the contribution.
4. Convergence/complexity asserted with no argument (see `references/theory-and-proofs.md`).
5. A symbol is used before definition, or renamed between sections.
6. Simulation trivia (SNR points, trial count) placed in the model instead of Numerical Results.

## Output

Return the section prose/LaTeX, a note on which equations you numbered and why, and a list of every
new symbol with its definition and role (variable / given / auxiliary) so the user can confirm
notation consistency.
