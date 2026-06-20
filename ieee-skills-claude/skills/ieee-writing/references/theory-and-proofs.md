# Optimization, Theorems, and Proofs (IEEE Communications)

For the two analytical cores of comms papers: the **optimization solution** (how a hard problem is
made solvable) and the **formal results** (theorems/lemmas with proofs, convergence, complexity).

## Optimization: name the difficulty, then the transformation

A reviewer judges an optimization paper on whether the reformulation is correct and motivated.
State the difficulty in (P1), then the transformation that removes it.

| Difficulty | Common transformation | What to state |
|---|---|---|
| Non-convex coupling between blocks | Alternating optimization (AO) / BCD | each block convex; convergence of the alternation |
| Non-convex objective/constraint | Successive convex approximation (SCA) | the surrogate, that it is a tight lower/upper bound, monotonic convergence to a KKT point |
| Quadratic/rank in beamforming | Semidefinite relaxation (SDR) | the relaxation, and whether the solution is rank-one (tight) or needs Gaussian randomization |
| Ratio objective (EE, SINR) | Fractional programming / Dinkelbach / quadratic transform | equivalent parametric problem; convergence of the outer loop |
| Coupled constraints, distributed | ADMM / dual decomposition | the splitting, the update steps, convergence conditions |
| Integer/combinatorial | Relaxation + rounding, branch-and-bound, matching | optimality gap or that it is a heuristic |

Always say which transformation is **exact** (equivalent) and which is an **approximation/bound**;
do not let an approximation read as an equivalence. If the result is a stationary/KKT point, say so
— do not claim global optimality unless you proved it.

## Algorithm box

Present the iterative method as a numbered algorithm: inputs (channel, budget, tolerance),
initialization, the iterate updates, the stopping criterion, and the output. Reference it as
"Algorithm 1" in the text. Keep notation identical to the System Model.

## Theorem / lemma / proposition — what each is for

- **Lemma:** a supporting result used to prove a theorem (e.g., convexity of a subproblem).
- **Proposition:** a self-contained minor result (e.g., a closed-form optimal power).
- **Theorem:** a main analytical result (e.g., the outage probability expression, convergence,
  optimality, the diversity order).
- **Corollary:** a direct consequence (e.g., the high-SNR slope from the outage theorem).

State each formally (assumptions in the statement), then prove. Put short proofs inline; move long
proofs to an **Appendix** ("The proof is given in Appendix A."), which is standard IEEEtran. Every
theorem must be either proved or explicitly cited.

```latex
\begin{theorem}\label{thm:outage}
Under [stated assumptions], the outage probability of the proposed scheme is
$P_{\mathrm{out}} = [\text{closed form}]$.
\end{theorem}
\begin{IEEEproof}
[derivation, or] See Appendix A.
\end{IEEEproof}
```

## Convergence and complexity claims

For every iterative algorithm, the paper must address both:

- **Convergence:** state what converges (objective, iterate) and to what (a stationary point, a KKT
  point, the global optimum). For SCA/AO, the standard claim is monotonic improvement of the
  objective and convergence to a KKT point — give the one-paragraph argument or cite the standard
  result. Illustrate with a convergence curve (see `ieee-figure`).
- **Complexity:** give per-iteration complexity in big-O of the problem dimensions (antennas $N$,
  users $K$, RIS elements $M$, variables), times the iteration count if known. Compare to benchmark
  schemes in a small table (see `ieee-experiments`). Order is the portable claim; runtime is
  hardware-dependent supplement.

## Validate analysis with simulation

A derived expression is not trusted until Monte-Carlo markers sit on its curve. Plan that overlay
when you derive outage/BER/rate/coverage (see `ieee-experiments` and `ieee-figure`), and check the
asymptotic slope matches the claimed diversity order / DoF.

## No fabrication

Do not invent a proof, assert a transformation is tight without showing it, claim global optimality
for a stationary point, or claim a diversity order the simulation does not show. If a step is
incomplete, mark `[PROOF GAP: ...]` and tell the user, rather than writing a hand-wave that a
reviewer will catch.

## Checks

1. The difficulty in the formulation is named, and the transformation that removes it is explicit.
2. Each transformation is labelled exact vs approximate; optimality claims match what is proved.
3. Every theorem/lemma is proved or cited; long proofs in an appendix.
4. Convergence target stated (KKT/stationary/global) and complexity given in big-O of dimensions.
5. Every derived expression has a planned simulation overlay.
