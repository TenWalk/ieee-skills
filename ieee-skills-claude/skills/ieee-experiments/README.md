# ieee-experiments

Design and audit the simulations of an IEEE communications paper (JSAC/TWC/TCOM/WCL/CL) so the
evidence matches the claims. Covers benchmark schemes, comms metrics, the Monte-Carlo protocol,
analysis-vs-simulation validation, fairness boundaries, imperfect-CSI robustness, and complexity
tables. For the results *narrative* use `ieee-writing`; for plots use `ieee-figure`.

## What it enforces

- Every contribution maps to a simulation that could falsify it (the evidence ladder:
  analysis-vs-simulation validation → performance vs benchmark schemes → parameter sweeps →
  design analysis ("w/o" variants) → convergence & complexity → robustness/limitations).
- Benchmark schemes grouped and labelled by role (conventional/heuristic, prior-art, upper/lower
  bound); the fairness boundary (same power budget, CSI assumption, bandwidth) stated in words.
- Metrics chosen to match the claim (BER/SER, outage/coverage, ergodic/sum rate, spectral and
  energy efficiency, diversity order), with the right axis (e.g. semilog BER vs SNR).
- Monte-Carlo protocol: enough channel realizations for the target error floor, the same channel
  seeds across all schemes for paired comparison, derived expression overlaid with markers.
- Empirical/ray-tracing/testbed evidence: environment, calibration, scenario split, baseline, and
  error distribution stated instead of treated as generic simulation.
- No fabricated numbers; gaps are listed as placeholders.

## Structure

```
ieee-experiments/
├── SKILL.md
├── README.md
└── references/
    ├── experiment-design.md   system/channel setup, benchmark schemes, design analysis, comms metrics, Monte-Carlo, validation, robustness
    └── tables-and-claims.md   table structure, table↔claim mapping, table/prose split, IEEE table style
```

## Output

A claim→simulation→metric→figure matrix, a categorised benchmark-scheme list, a design-analysis
("w/o") plan, the Monte-Carlo protocol, and a list of simulations still to run.
