# System-Model Cheat-Sheet by Paradigm (RIS, NOMA, ISAC, near-field, ...)

Each emerging architecture has a System Model that reviewers expect to contain specific elements, a
distinctive optimization variable and constraint, and a signature metric. Getting these wrong is a
fast desk-reject signal. Use the row for your paradigm to check the model is complete; combine rows
for hybrids (e.g. RIS-NOMA, near-field ISAC). For *how* to write the System Model prose (signal
flow, notation, equation numbering) see `method.md`; this file is *what must be in it*.

General rule for every paradigm: define the channel as an equation, state what CSI is known and how
it is obtained, mark the optimization variables, and write the distinctive constraint explicitly —
that constraint is usually the source of non-convexity and the reason the paper exists.

## Reconfigurable intelligent surface (RIS / IRS)

- **Must contain:** the cascaded channel BS → RIS → user **and** any direct BS → user link; the RIS
  phase-shift matrix $\boldsymbol{\Theta} = \mathrm{diag}(e^{j\theta_1},\dots,e^{j\theta_N})$;
  number of elements $N$; passive vs active RIS (active adds amplification + noise).
- **Key variable / constraint:** the phase shifts $\theta_n$ under the **unit-modulus constraint**
  $|e^{j\theta_n}|=1$ (or discrete/finite-resolution phases) — the core non-convexity.
- **Typical metric:** sum rate / EE / received SNR vs number of RIS elements $N$.
- **Pitfalls:** omitting the direct link; assuming continuous phases without a finite-resolution
  check; ignoring how the cascaded CSI is estimated (a known hard problem — at least cite it);
  claiming a squared array gain ($N^2$) without the passive-beamforming alignment that earns it.

## Non-orthogonal multiple access (NOMA)

- **Must contain:** superposition coding at the transmitter; the **SIC decoding order** and the
  rule that sets it (usually by channel gain / effective gain); the rate of each user *after* SIC;
  the SIC-feasibility / decoding-order constraint.
- **Key variable / constraint:** power-allocation coefficients under the **SIC decoding
  constraints** (a stronger user must be able to decode a weaker user's signal first).
- **Typical metric:** sum rate, cell-edge/weak-user rate, fairness (min-rate), outage per user.
- **Pitfalls:** asserting a fixed decoding order without justifying it; ignoring imperfect SIC
  (residual interference) — reviewers expect a robustness check; comparing only to OMA without a
  fair total-power/bandwidth split; for MIMO-NOMA, hand-waving the cluster/user pairing.

## Integrated sensing and communications (ISAC)

- **Must contain:** the **dual-functional waveform/signal** shared by sensing and comms; the
  communication channel/rate model **and** the sensing model (target response, echo, the parameter
  estimated — angle/range/velocity); the shared resource (power, antennas, bandwidth, frame).
- **Key variable / constraint:** the transmit beamformer/covariance optimized for *both* functions,
  under a sensing-quality constraint (max CRB / min sensing-SINR / beampattern similarity).
- **Typical metric:** dual — a comms metric (rate) **and** a sensing metric (**CRB**/detection),
  reported as a **rate–CRB tradeoff region** (see `ieee-experiments`).
- **Pitfalls:** reporting only the communication side; using beampattern matching where CRB is
  expected; not stating the power/aperture split; treating the design as two orthogonal allocations
  (that is the *baseline*, not the contribution).

## Near-field communications (XL-MIMO / holographic)

- **Must contain:** the **spherical-wavefront** channel model (steering depends on **both angle and
  distance**), not the planar far-field approximation; the Rayleigh/Fraunhofer distance that
  justifies operating in the near field; beam-focusing (focal point) rather than beam-steering.
- **Key variable / constraint:** beamfocusing weights exploiting the extra **distance dimension**;
  often a per-element or subarray constraint for an extremely large aperture.
- **Typical metric:** rate / spatial DoF / number of resolvable users in range-angle, vs aperture.
- **Pitfalls:** using a far-field steering vector while claiming near-field gains (contradiction);
  not stating the boundary distance that makes the regime "near field"; ignoring the extra
  beam-focusing DoF that is the whole point.

## Movable / fluid antenna systems (MA / FAS)

- **Must contain:** the **antenna position(s)** as variables over a defined region/port set; the
  position-dependent channel model; the spatial-correlation model across positions; minimum
  inter-antenna spacing.
- **Key variable / constraint:** antenna positions (continuous region or discrete ports) under a
  **movement-region and minimum-spacing constraint** — jointly optimized with beamforming/power.
- **Typical metric:** rate / SNR / outage vs movable region size or number of ports.
- **Pitfalls:** an unrealistic position-to-channel map (no correlation model); ignoring the
  spacing/region limit; claiming gains without comparing to a fixed-antenna array of equal aperture.

## Cell-free massive MIMO

- **Must contain:** many distributed **access points (APs)** serving all users (no cells); the
  fronthaul to the **central processing unit (CPU)**; the cooperation level (fully centralized vs
  the user-centric/scalable cluster); per-AP power constraints; uplink pilot / channel estimation.
- **Key variable / constraint:** per-AP precoding/combining and power under **per-AP power
  constraints** and a stated cooperation/fronthaul level.
- **Typical metric:** per-user / 95%-likely (cell-edge) rate — the cell-free selling point —
  spectral and energy efficiency.
- **Pitfalls:** assuming full centralization while claiming scalability; ignoring fronthaul cost /
  quantization; reporting only sum rate and hiding the fairness (cell-free's whole point is the
  worst-user rate); not specifying the AP-selection / clustering rule.

## mmWave / hybrid beamforming

- **Must contain:** the **hybrid analog–digital** architecture (few RF chains $N_{RF} \ll N$);
  the analog phase-shifter network; the sparse/clustered mmWave channel (Saleh–Valenzuela);
  fully-connected vs partially-connected/subarray structure.
- **Key variable / constraint:** the analog precoder under the **constant-modulus (phase-only)
  constraint** plus the **RF-chain count** limit, with a digital precoder on top.
- **Typical metric:** spectral efficiency vs SNR / number of RF chains; gap to the fully-digital
  upper bound.
- **Pitfalls:** ignoring the constant-modulus constraint on analog phases; using a rich (non-sparse)
  channel for mmWave; not comparing to the fully-digital bound; forgetting the RF-chain budget.

## Semantic communications

- **Must contain:** the **semantic encoder/decoder** (often DNN-based) and what "semantic
  information" means for the task; the (possibly shared) **knowledge base**; the task the system
  serves (classification, reconstruction, VQA); the channel between encoder and decoder.
- **Key variable / constraint:** encoder/decoder parameters and transmission rate under a
  task-performance constraint; channel-adaptive coding.
- **Typical metric:** **task-level** metric (accuracy, BLEU, PSNR/SSIM, semantic similarity) vs
  SNR/bandwidth — *not* BER; often a rate–task-accuracy tradeoff.
- **Pitfalls:** evaluating with BER instead of a task/semantic metric; not defining the knowledge
  base or how it is shared; no robustness to channel variation; comparing only to a separate
  source–channel coding baseline without matched bandwidth. (This is also a learning-based paper —
  see `learning-based-comms.md`.)

## How to use this file

1. Identify the paradigm(s); read the matching row(s).
2. Check the System Model contains every "must contain" element, as equations where stated.
3. Make the "key variable / constraint" explicit — it is the non-convexity that justifies the
   solution section.
4. Confirm the metric matches the paradigm's signature; cross-check the figure plan in
   `ieee-experiments` / `ieee-figure`.
5. Sweep the pitfalls before drafting — each is a common reviewer objection.

Never invent a channel model, constraint, or metric to fill a row — if the user's setup lacks one
(e.g. no direct-link assumption stated for RIS), flag it as `[AUTHOR INPUT NEEDED]`, don't assume.
