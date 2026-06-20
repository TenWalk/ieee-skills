# Simulation Design (IEEE Communications)

## System and channel setup

Report enough that an independent group could regenerate the curves:

- **Topology / scenario:** numbers of antennas, users, cells, RIS elements, subcarriers; geometry
  (cell radius, user drop, distances) if path loss matters.
- **Channel model:** Rayleigh / Rician (K-factor) / Nakagami-m / correlated fading / mmWave
  cluster model; large-scale path loss exponent and shadowing if used; AWGN variance.
- **Signal / waveform:** modulation/coding, blocklength, bandwidth, carrier frequency, power
  budget, noise figure.
- **What is random vs fixed** per Monte-Carlo run (channel realizations random; topology often
  fixed or re-dropped — say which).
- **Define SNR/SINR precisely** (transmit SNR vs receive SNR, per-antenna vs total power). Most
  reviewer confusion on comms results comes from an undefined SNR axis.

A compact **simulation-parameters table** (parameter | value) is expected — put shared settings
there once, not repeated per scheme.

## Benchmark schemes — five roles, each labelled

| Role | What it is | Purpose |
|---|---|---|
| Proposed | Your scheme / algorithm | The contribution |
| Conventional / heuristic | Standard practical method (e.g., ZF, MRT, equal power, greedy) | Shows gain over common practice |
| Prior-art | Published scheme for the *same* setting | Shows competitiveness vs state of the art |
| Upper bound | Relaxed / exhaustive / genie-aided / perfect-CSI / convex relaxation | How close you are to the optimum |
| Lower bound / naive | Random, no-optimization, equal allocation | Shows the problem is nontrivial |

State which role each scheme plays. Run all schemes under the **same** power budget, CSI
assumption, bandwidth, and **same channel realizations** (paired comparison) — or declare the
difference. "w/o module X" variants are design-analysis curves (next section), not separate
prior-art.

## Design analysis — isolate one decision each

The communications analogue of an ablation: build reduced variants of your own scheme that each
remove or replace exactly one design choice ("Proposed w/o phase optimization", "Proposed with
fixed power"), everything else fixed. Cover every design choice the Introduction claims as a
contribution. A variant that changes two things at once proves nothing — split it.

## Metrics — match the claim

Pick the metric that the claim is actually about, plus a probing secondary metric:

| Claim is about | Headline metric | Add |
|---|---|---|
| Reliability | BER / SER / FER (vs SNR, **semilog y**) | error floor, diversity order (slope) |
| Link/system throughput | Achievable/sum/ergodic rate, spectral efficiency (bps/Hz) | per-user rate, cell-edge rate |
| Outage / coverage | Outage probability, coverage probability (vs SNR/threshold) | CDF of SINR or rate |
| Efficiency | Energy efficiency (bits/J), power consumption | complexity order, runtime |
| Latency / freshness | Delay, age of information (AoI), throughput | tail (percentile) latency |
| Optimization quality | Objective value vs benchmark / upper bound | optimality gap, convergence speed |
| Estimation / feedback (learning) | NMSE (vs SNR), cosine similarity / GCS for CSI | bits/overhead, downstream rate or BER |
| Learning inference cost | Parameter count, FLOPs/multiplications per inference | latency vs iterative benchmark at matched performance |
| Sensing / ISAC | CRB / root-CRB (estimation), $P_d$/$P_{fa}$ (detection) | estimation RMSE overlay, rate–CRB tradeoff region (see Sensing and ISAC evaluation) |

Define every metric (or cite it) and state the averaging. State whether higher or lower is better.

## Monte-Carlo protocol

- Average each point over a stated number of **independent channel realizations** (e.g., 10^4–10^6;
  enough that the curve is smooth, especially for low BER/outage — a 10^-5 BER needs ≫10^5 trials).
- Use the **same realizations across all schemes** so differences are not sampling noise (paired).
- For very low error/outage, say how many trials and consider importance sampling; do not plot a
  point you have too few error events to estimate.
- Where helpful, show confidence (smooth curve usually suffices; report trial count in the caption
  or setup table).

## Analysis-vs-simulation validation (analytical papers)

The signature comms figure: **analytical expression as a line, Monte-Carlo as markers** on the
same axes. Their overlap validates the derivation — this is the evidence, not a formality.

- Overlay every closed-form result the paper derives (outage, BER, rate, coverage).
- Check the **asymptotic regime** (high SNR): confirm the slope equals the claimed diversity
  order / multiplexing gain / DoF, and label it.
- If theory and simulation diverge, find out why before submitting — a mismatch a reviewer spots
  is fatal; one you explain (e.g., finite-blocklength effect) is fine.

## Convergence and complexity (iterative algorithms)

For SCA / ADMM / alternating optimization / fractional programming / Dinkelbach:

- **Convergence:** plot objective (or its surrogate) vs iteration; state monotonicity and the
  stopping criterion. If you proved convergence, the curve illustrates it.
- **Complexity:** give per-iteration order in big-O of the problem dimensions (antennas, users,
  variables), and compare to benchmark schemes in a small table. Runtime is a useful supplement
  but is hardware-dependent — order is the portable claim.

## Learning-based evaluation (DL / deep unfolding / DRL)

A learning-based comms paper must clear three extra rungs the model-based papers do not. Plotting
"lower NMSE than LS" alone is under-evaluation.

- **Benchmark against the model-based method, not a weak heuristic.** Compare to LS/MMSE
  (estimation/feedback), WMMSE/ZF/SDR (beamforming), or the iterative solver you replace — same
  channel realizations, same CSI assumption. For **deep unfolding**, also run the parent algorithm
  to convergence (performance ceiling) and to `L` iterations (matched-complexity comparison).
- **Generalization is the signature learning test.** Train at one condition, test at unseen ones:
  SNR outside the training range, different number of users/antennas, a mismatched channel model
  (train Rayleigh, test Rician/measured), different correlation. Off-distribution collapse is the
  top reviewer kill-shot — show graceful degradation or state the limit explicitly.
- **Complexity and inference latency vs the model-based benchmark.** Speed is half the claim:
  give parameter count, FLOPs/multiplications per inference, and latency at matched performance.
  Order (big-O) is the portable claim; keep training cost and inference cost separate.
- **Architecture ablation:** remove/shrink one design choice at a time (number of unfolded layers
  `L`, a residual/attention block, the model-driven module). Sweeping `L` is the canonical
  deep-unfolding ablation — it shows how few iterations the learned version needs.
- **Train/test hygiene:** test channels drawn independently of training; state train/val/test
  sizes and the channel model (or cite the dataset, e.g. DeepMIMO). Same fixed realizations for
  train and test = memorization, not generalization.

## Empirical, ray-tracing, and testbed evidence

Recent wireless papers, especially in TWC and letters with measurement claims, often combine
simulation with ray-tracing, hardware experiments, emulation, or over-the-air testbeds. Treat these
as evidence with their own reproducibility rules; do not describe them as generic simulations.

- **Name the evidence type.** Distinguish analytical simulation, ray-tracing data, channel
  sounding/measurement, network emulation, and over-the-air testbed results. Each has a different
  error source.
- **Describe the environment.** For ray tracing or radio maps, state the 3D model/source, carrier
  frequency, material assumptions, antenna pattern, grid/resolution, transmitter/receiver locations,
  and calibration procedure. For measurements, state hardware, bandwidth, sampling/calibration,
  deployment geometry, and collection time.
- **Separate train/validation/test by scenario when learning is involved.** A random sample split
  over the same map is weaker than a held-out environment, floor, route, user region, or channel
  condition.
- **Compare against the right baseline.** AI-generated radio maps should be compared against ray
  tracing/measurement and a simple interpolation/statistical baseline; testbed claims need the
  corresponding simulation or analytical prediction where possible.
- **Report error distributions, not only averages.** CDFs, percentile error, cell-edge/worst-region
  behavior, and spatial heatmaps often reveal failure modes hidden by mean NMSE or mean rate.
- **State data/code availability or constraints.** If the dataset or hardware trace cannot be
  released, say so and provide enough parameters for an independent sanity check.

For a WCL/CL letter, include empirical/testbed evidence only when it is central to the one
contribution. A compact setup paragraph plus one decisive figure is usually better than a long
measurement narrative.

## Sensing and ISAC evaluation (dual metrics + the tradeoff curve)

An integrated sensing and communications (ISAC) paper is judged on **two metrics at once** — a
communication metric and a sensing metric — and on the **tradeoff** between them. Showing only the
communication side (or only a beampattern) is the most common ISAC under-evaluation.

**Sensing metrics, in rough order of reviewer preference:**

| Metric | What it measures | Note |
|---|---|---|
| **CRB / root-CRB** | Lower bound on estimation error (angle, range, velocity) | The dominant, most-defensible sensing metric — a fundamental bound, not a design artifact |
| Estimation RMSE | Actual estimator error (MUSIC, ML) | Overlay on the CRB to validate it, exactly like analysis-vs-simulation |
| Detection prob. $P_d$ / false-alarm $P_{fa}$, ROC | Target-detection performance | For detection-framed sensing; sweep threshold for the ROC |
| Radar/sensing SINR | Echo SINR at the sensing receiver | A design proxy; pair with CRB where possible |
| Beampattern MSE / matching error | Distance from a desired transmit beampattern | A *proxy*, weaker than CRB — reviewers increasingly ask for CRB instead |

Prefer **CRB over beampattern matching**: the beampattern is a design target, the CRB is the
information-theoretic estimation limit. If you report beampattern, add CRB unless space forbids.

**The tradeoff is the signature ISAC result.** Communication and sensing compete for the same
power/aperture/waveform, so the contribution is usually a *boundary*, not a single point:

- **Rate–CRB (or SR–CRB) region / Pareto boundary.** Generate it by **maximizing the rate subject
  to a maximum-CRB (or minimum sensing-SINR) constraint, then sweeping that constraint** — each
  constraint value gives one boundary point. Weighted-sum scalarization (vary the weight) is the
  alternative. State which you used.
- Plot communication metric on one axis, sensing metric on the other; each curve is one scheme,
  and "up-and-to-the-right" (or toward the origin for CRB) dominates.
- Include the **sensing-only** and **communication-only** corner points as anchors, and a
  time/power-splitting baseline (orthogonal resource division) as the lower bound the joint design
  beats.

**Fairness for ISAC:** declare the shared budget split — total transmit power, antennas/aperture,
bandwidth, and frame structure — identical across schemes, and state whether sensing and comms
share the waveform or are separated. The dual-functional waveform's whole point is that it is *not*
two orthogonal allocations, so the orthogonal split is the benchmark to beat, not the setup.

## Robustness and sensitivity

- **Imperfect CSI:** the most-expected robustness test in comms — re-run with channel estimation
  error (state the error model/variance) and show graceful degradation.
- **Hardware impairments / quantization:** phase-noise, finite-resolution phase shifters, PA
  nonlinearity, ADC bits, where relevant to the contribution.
- **Parameter mismatch / sensitivity:** sweep a key parameter (K-factor, correlation, number of
  RIS elements) and show the scheme is not knife-edge.

## Reproducibility (IEEE expectation)

- Put all simulation parameters in one table; state the channel model and SNR definition exactly.
- State solver/toolbox (e.g., CVX, MOSEK) for optimization, and any random-seed handling.
- Give enough that an independent group could regenerate the main curve.

## Pre-submission audit

1. Does every contribution have a result that could falsify it?
2. Is each benchmark scheme's role labelled and the shared constraint stated?
3. Do Monte-Carlo markers match every derived expression, with the asymptotic slope checked?
4. Does each design-analysis variant isolate exactly one decision?
5. Is the SNR axis defined, and the realization count adequate for the lowest plotted point?
6. For iterative algorithms, are convergence and complexity-order both shown?
7. For empirical, ray-tracing, or testbed results, are environment, calibration, train/test split,
   and baseline evidence stated?
8. Could a reader regenerate the main curve from the parameters table?
