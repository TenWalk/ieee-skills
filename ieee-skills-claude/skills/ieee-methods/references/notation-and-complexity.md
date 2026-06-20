# Notation, Algorithm Boxes, and Complexity Statements

## Notation table

Use a notation table when the paper has many matrices, sets, or optimization variables. Keep it
compact and useful:

```text
Symbol | Size/domain | Meaning | First used
M | integer | number of BS antennas | Sec. II
K | integer | number of users | Sec. II
h_k | C^{M x 1} | channel vector from BS to user k | (1)
w_k | C^{M x 1} | beamforming vector for user k | (2)
```

Rules:

- Define scalars, vectors, matrices, sets, and operators consistently.
- Use bold lowercase for vectors and bold uppercase for matrices if the manuscript follows that
  convention.
- State whether `||.||` is Euclidean, Frobenius, or spectral norm when ambiguity matters.
- Do not create a table for five obvious symbols; it costs space.

## Equation numbering

Number only equations that carry the argument:

- signal model and received signal;
- objective and constraints;
- main theorem/proposition/corollary;
- update rule or loss function used later;
- performance metric used in figures.

Do not number every intermediate definition. If the text never refers to it, leave it unnumbered.

## Algorithm box checklist

An IEEE algorithm box should include:

```text
Input: channel estimates, power budget, tolerance epsilon, maximum iterations Imax
Initialize: feasible variables and objective value
Repeat:
  1. solve/update block A
  2. solve/update block B
  3. update objective and stopping gap
Until: gap <= epsilon or iteration = Imax
Output: optimized variables and achieved metric
```

State which steps are exact, approximate, relaxed, randomized, or learned. If a subproblem is solved
by CVX/MOSEK, say so in the text rather than hiding it inside the box.

## Convergence statements

Match the claim to the proof:

| Evidence | Safe statement |
|---|---|
| Monotonic bounded objective | "the objective sequence converges" |
| SCA/MM conditions satisfied | "the iterates converge to a stationary/KKT point" |
| Convex problem solved exactly | "the global optimum of the convex subproblem is obtained" |
| Exhaustive search / proven convex original problem | "global optimum" |
| Only empirical objective curve | "the algorithm converged within N iterations in the tested settings" |

Never call an alternating/SCA solution globally optimal unless the original problem is convex or the
proof actually establishes global optimality.

## Complexity analysis

Give big-O in problem dimensions. Define variables first:

```text
Let M, K, N, and I denote the number of antennas, users, RIS elements, and outer iterations,
respectively. The dominant cost of each iteration is solving the semidefinite subproblem with
matrix dimension N, whose worst-case complexity is O(N^{6.5}). Hence, the total complexity is
O(I N^{6.5}) plus lower-order beamforming updates.
```

For learning-based methods, separate:

- training cost (offline, often high);
- inference cost (online, relevant to deployment);
- parameter count and FLOPs/multiplications;
- latency measured on named hardware if latency is claimed.

## Complexity table

Use a small table when complexity is a contribution:

```text
Scheme | Per-iteration / inference complexity | Iterations | Notes
Proposed AO | O(I (K^3 + M^3)) | I | tolerance epsilon
WMMSE | O(I_w K^3) | I_w | same stopping rule
Learned unfolding | O(L P) | L layers | P multiplications per layer
```

Avoid fake precision. If a solver has a conservative worst-case bound but practical runtime is much
smaller, report both clearly.
