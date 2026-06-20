# Learning-Based Communications Papers (DL / DRL / Deep Unfolding)

Use this when the contribution is a **neural network or learning algorithm for a PHY/MAC task**
(CSI feedback, channel estimation, beamforming/precoding, signal detection, resource allocation,
power control, AP/beam selection). A learning-based comms paper is still a comms paper — same
System Model, same benchmark discipline, same no-fabrication rule — but it adds an architecture, a
training methodology, and a generalization/complexity story that reviewers specifically attack.

## Taxonomy — name which kind you are writing

| Kind | What it is | Typical tasks | Benchmark it must beat |
|---|---|---|---|
| **Data-driven (black-box)** | A generic DNN/CNN/GNN/Transformer maps input→output | CSI feedback (CsiNet-style), channel estimation, end-to-end autoencoder | Model-based estimator (LS/MMSE), conventional precoder (ZF/MRT) |
| **Model-driven (deep unfolding)** | Unroll an iterative algorithm (WMMSE/ADMM/SCA/ISTA/OAMP) into a fixed number of trainable layers | Beamforming, detection, sparse recovery, channel estimation | The *original* iterative algorithm (same problem, more iterations) |
| **Deep reinforcement learning (DRL)** | Agent learns a policy from reward over time/states | Dynamic resource allocation, power control, handover, beam tracking, scheduling | Optimization-based per-slot solution, heuristic policy |
| **Learning-aided / hybrid** | Learning replaces *one* expensive block inside a classical pipeline | Pruning the search, warm-starting an iterative solver, predicting active set | The full classical pipeline without the learned block |

The single most common reviewer complaint on data-driven papers is "why not a model-driven
approach with fewer parameters and built-in interpretability?" — if you chose black-box, justify it;
if you chose deep unfolding, say so explicitly, it is the more defensible default in comms.

## Why deep unfolding is the comms-favored framing

Unrolling WMMSE/ADMM/SCA into `L` trainable layers (each layer = one iteration with learnable
step sizes / regularizers) gives: far fewer parameters than a black-box net, interpretable layers
tied to a known algorithm, convergence intuition inherited from the parent algorithm, and usually
better generalization to unseen SNR/channel than a black-box net of similar size. State the parent
algorithm, what each layer computes, and **which quantities are learned vs fixed by the model**.

## Section architecture (how it differs from an optimization paper)

```
I.   Introduction        application → limits of iterative/model-based methods (complexity, latency,
                         CSI sensitivity) → why learning → contributions
II.  System Model        unchanged: topology → channel model → signal → metric (the metric becomes
                         the training objective, so define it precisely)
III. Problem Formulation state the optimization problem the network solves (even for black-box —
                         it anchors the loss and the benchmark)
IV.  Proposed Network /  architecture (layers, dimensions, parameter count) → input/output and
     Learning Solution   their normalization → loss function → training algorithm → complexity &
                         inference latency vs the model-based benchmark
V.   Numerical Results   training setup → performance vs model-based + learning benchmarks →
                         generalization tests → complexity/latency → ablation of architecture
```

Two structural rules: (1) **anchor the loss to a communications metric**, not an abstract proxy —
e.g. unsupervised loss = negative sum rate, or NMSE for estimation; (2) the network section must
state **parameter count and inference complexity**, because "fast at inference" is half the claim.

## Training methodology — the part reviewers check

Report enough that the result is reproducible and the comparison is fair:

- **Data = channel realizations.** State the channel model used to *generate* train/val/test sets,
  the number of samples in each, and that test channels are drawn independently of training. If real
  measured data, cite the dataset (e.g. DeepMIMO, a ray-tracing set) and the scenario.
- **Supervised vs unsupervised.** Supervised needs labels (e.g. MMSE estimate, optimal precoder
  from a solver) — say where labels come from. Unsupervised/self-supervised optimizes the comms
  metric directly (negative rate, NMSE) — preferred when labels are expensive or the optimum is
  unknown. Name which you use.
- **Loss function** tied to the metric: NMSE for estimation/feedback; negative sum rate / negative
  EE for beamforming; cross-entropy / BER surrogate for detection; cumulative reward for DRL. Write
  the loss as an equation.
- **Training config:** optimizer (Adam), learning rate and schedule, batch size, epochs, train SNR
  (single value or a range — this drives generalization), early-stopping criterion, framework.
- **DRL specifics:** state/action/reward definition (reward must encode the comms objective and
  constraints, often via penalty), algorithm (DQN/DDPG/PPO/SAC), exploration, episode/step
  structure, and how constraints (power, QoS) are enforced.

## Evaluation — three things beyond "we win on the metric"

A learning paper that only shows "lower NMSE than LS" is under-evaluated. Add:

1. **Generalization (the signature learning test).** Train at one condition, test at unseen ones:
   SNR not seen in training, different number of users/antennas, a mismatched channel model
   (trained Rayleigh, tested Rician/measured), different correlation. A method that collapses
   off-distribution is the top reviewer kill-shot — show graceful degradation or state the limit.
2. **Complexity and inference latency vs the model-based benchmark.** The usual selling point of
   learning is speed: give parameter count, FLOPs/multiplications per inference, and wall-clock or
   per-sample latency against the iterative benchmark at matched performance. Order (big-O) is the
   portable claim; runtime is hardware-dependent but expected.
3. **Architecture ablation.** Remove/shrink one design choice at a time (number of unfolded layers,
   a residual connection, the attention block, the model-driven module) — the learning analogue of
   the "w/o" variant. Sweeping the number of unfolded layers `L` is the canonical deep-unfolding
   ablation: it shows how few iterations the learned version needs.

## Benchmarks specific to learning-based comms

Beyond the five standard roles (see `ieee-experiments`), a learning paper must include:

- **The model-based method it replaces** — LS/MMSE for estimation, WMMSE/ZF/SDR for beamforming,
  the iterative solver for unfolding. Same problem, same CSI, same channel realizations.
- **For deep unfolding:** the parent iterative algorithm run to convergence (many iterations) as
  the performance ceiling, and run to `L` iterations as the matched-complexity comparison.
- **Optionally a black-box net** of comparable size, to justify a model-driven design.

## No-fabrication rules (learning-specific)

- Do not invent NMSE/BER/rate numbers, loss curves, or a "converged" training curve. Mark unrun
  results `[PLACEHOLDER: NMSE vs SNR, trained Rayleigh]`.
- Do not claim generalization you did not test. "Generalizes to unseen SNR" requires a test at
  unseen SNR in the paper.
- Do not report inference speedup without stating the hardware and what is being compared
  (training cost is separate from inference cost — keep them distinct).
- State the training set size and channel model honestly; a result that only holds for one
  synthetic channel is a bounded result, not a general one.
- Do not call a black-box network "interpretable"; reserve that for model-driven/unfolded designs
  and only when each layer maps to an algorithm step.

## Common failure modes

1. The loss is an abstract MSE with no link to the communications metric the paper claims to
   improve.
2. Train and test channels are drawn from the same fixed realizations — the "generalization" is
   memorization.
3. The complexity claim ("low complexity", "real-time") has no parameter count, FLOP count, or
   latency comparison.
4. A black-box net is compared only to a weak heuristic, never to the proper model-based method
   (LS/MMSE/WMMSE) it purports to beat.
5. The number of unfolded layers `L` is fixed with no ablation, so the reader cannot tell whether
   the model-driven structure actually helps.
6. DRL reward is described in words only; state/action/reward are not defined as the formal tuple,
   so the result is not reproducible.

## Output

Return the section prose/LaTeX, the loss written as an equation, a table of the network's parameter
count and per-inference complexity vs the model-based benchmark, and a list of which
generalization/ablation tests the claims require (flag any not yet run as `[PLACEHOLDER]`).
