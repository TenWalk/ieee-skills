# Reproducibility Checklist for IEEE Communications Methods

Use this checklist when writing or auditing a methods/system-model/results-setup section. Include
only items relevant to the paper; do not pad a short letter with unnecessary machinery.

## System and signal model

- Topology: cells, antennas, users, RIS elements, subcarriers, sensing targets, or network nodes.
- Geometry: distances, cell radius, deployment region, user distribution, mobility assumptions.
- Channel: fading law, path loss, shadowing, correlation, Rician K-factor, mmWave/THz cluster
  model, near-field model, or ray-tracing source.
- Signal flow: transmitted symbol/vector, precoder, channel transformation, receiver observation,
  noise variance, decoding/estimation step.
- SNR/SINR definition: transmit vs receive SNR, total vs per-antenna power, bandwidth and noise
  figure when used.
- CSI assumption: perfect/imperfect/statistical/local/global, estimation-error model, feedback
  overhead.

## Simulation-parameter table

Use one compact table with shared settings:

```text
Parameter | Value | Note
Number of BS antennas M | [value] | total or per subarray
Number of users K | [value] | user drop model
Carrier frequency | [value] GHz | if path loss or testbed matters
Bandwidth | [value] MHz | if rate/noise power matters
Noise power / variance | [value] | define normalization
Path-loss exponent | [value] | cite or justify
Monte-Carlo realizations | [value] | independent channel draws
Stopping tolerance | [value] | for iterative algorithms
```

Put constants here once. Prose should explain why the settings expose the claim.

## Randomization and Monte-Carlo

- State what is randomized per run: channels, user positions, noise, data symbols, block fading.
- State what is fixed: topology, training set, test set, random seed policy, target positions.
- Use the same channel realizations across schemes for paired comparison unless impossible.
- For BER/outage tails, ensure enough trials for the lowest plotted probability.

## Optimization and solver details

- Solver/toolbox: CVX/MOSEK/Gurobi/custom code/version when relevant.
- Initialization: random, feasible heuristic, previous solution, SDR randomization count.
- Stopping criterion: tolerance, max iterations, monotonic objective threshold.
- Feasibility handling: projection, penalty, constraint violation tolerance.
- Runtime environment: CPU/GPU and language only when runtime or latency is a claim.

## Learning-based methods

- Dataset generation: channel model, train/validation/test sizes, SNR range, user/antenna ranges.
- Split policy: independent test channels; held-out environments for ray-tracing/radio maps when
  claimed.
- Architecture: layer count, dimensions, activation, parameter count, unfolded iterations if any.
- Loss: tied to a communications metric such as NMSE, negative sum rate, outage proxy, or BER.
- Training: optimizer, learning rate, batch size, epochs, early stopping, normalization.
- Inference: FLOPs or multiplications, latency, memory, comparison to the model-based method.

## Empirical/ray-tracing/testbed details

- Evidence type: measurement, channel sounding, ray tracing, emulation, over-the-air testbed.
- Environment: map/source, material model, carrier frequency, antenna pattern, grid resolution.
- Hardware: RF chain, sampling rate, calibration, bandwidth, synchronization, collection time.
- Baselines: simulation prediction, interpolation/statistical baseline, or prior measurement method.
- Data availability: repository, access limits, or enough details for an independent sanity check.

## Final audit

1. Could another group reproduce the main curve without asking for hidden settings?
2. Are all symbols, dimensions, and units defined before use?
3. Are solver/training/randomization details sufficient for the claimed result?
4. Is each simplifying assumption tied to the studied regime or a robustness check?
5. Are values real author-provided values, not invented placeholders?
