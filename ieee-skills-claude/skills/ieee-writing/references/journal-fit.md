# Target-Journal Fit: JSAC, TWC, TCOM, WCL, and CL

Use this file before drafting when the target journal is named, uncertain, or strategically
important. The same technical contribution should be framed differently for a JSAC special issue,
a full wireless transaction, a communications-theory transaction, or a short letter.

Always verify the current Author Kit / Call for Papers before submission. This file captures robust
writing and review expectations, not immutable production rules.

## Fast routing

| Target | Best fit | Writing consequence | Evidence consequence | Common rejection risk |
|---|---|---|---|---|
| **JSAC** | A timely topic that fits a specific special issue or selected area, often with system-level or architectural significance | State the special-area problem and why the contribution matters beyond one narrow parameter setting | Broader evidence: analysis/simulation plus scenario breadth, system insight, or architectural implication | A technically sound paper reads like a generic TWC/TCOM submission and does not fit the issue theme |
| **TWC** | Wireless systems, PHY/MAC design, channel modeling, radio maps, measurements, ISAC, RIS, cell-free, UAV, mmWave/THz, learning for wireless | Put channel/topology realism and wireless operating regimes early; make assumptions and CSI boundaries explicit | Strong simulations, parameter sweeps, realistic channels, robustness, and, when claimed, measurement/testbed or ray-tracing validation | The system model is too idealized, baselines are weak, or the wireless deployment evidence is thin |
| **TCOM / TC** | Communications theory, coding/modulation, detection, estimation, information/semantic communication, analytical performance, algorithms | Lead with the formal problem, derivation, theorem, receiver/encoder design, or complexity argument | Closed forms/proofs where relevant, complexity, and Monte-Carlo validation of every derived expression | Claims are empirical only, proofs are missing, or the method is not tied to a communications metric |
| **WCL** | A single wireless communications result that can be judged quickly | Compress to one contribution; no standalone Related Work; state "In this letter..." and cut secondary variants | 2-4 decisive figures/tables, possibly one compact experiment/testbed result if it is central | Too many contributions, weak page discipline, or missing validation of the one result |
| **CL** | A single concise communications result across the broader ComSoc scope | Same letter logic as WCL, plus CL-specific submission details such as EDICS and optional double-anonymous handling | One core proof/design/measurement plus the minimum comparison needed to make it credible | The result needs transaction-level space, EDICS/anonymity details are mishandled, or the evidence is too thin |

## Target-specific writing moves

### JSAC

- Open from the selected area's agenda, not only from a generic application. A JSAC paper should
  make the reviewer feel that the paper belongs in the special issue.
- Add an explicit **fit sentence** in the Introduction or cover letter: this paper contributes to
  `[selected area]` by resolving `[technical bottleneck]` in `[system setting]`.
- Prefer a broader contribution architecture: framework + algorithm/analysis + system insight.
  If the work is only an incremental optimization in a standard setup, consider TWC or TCOM instead.
- The contributions list may include a system-level insight, dataset/testbed, or architectural
  implication, but every item still needs evidence.

### TWC

- Treat the System Model as a reviewer trust test: topology, channel, path loss, mobility, CSI,
  resource budget, and SNR definition must be reproducible.
- Put realism checks in the evidence ladder: imperfect CSI, hardware/quantization, mismatched
  channel, deployment geometry, train/test split, or measurement/testbed validation when claimed.
- Learning-based wireless papers must report dataset generation, train/validation/test separation,
  generalization, parameter count, and inference latency against the model-based benchmark.
- Do not let an AI model replace the wireless problem. The loss, metrics, and baseline must remain
  communications-native.

### TCOM / TC

- Make the formal contribution visible: theorem, closed-form expression, receiver/decoder,
  modulation/coding design, convergence proof, or complexity reduction.
- State assumptions inside theorem/proposition statements, not only in prose.
- If the paper derives outage/BER/SEP/rate/coverage, the first results figure should validate the
  expression with Monte-Carlo markers and the claimed asymptotic slope.
- Avoid a pure "simulation wins" story unless the method itself is an algorithmic/theoretical
  communications contribution with a clear complexity or optimality argument.

### WCL and CL

- A letter is a **single-result paper**. If the draft has two independent contributions, split the
  work or target a transaction.
- Current ComSoc letter guidance uses a short abstract (typically 75-100 words) and a 5-page maximum
  with page charges beyond the free page budget; verify the target's live Author Kit.
- The fifth page is a strategic choice, not a license to write a small transaction. Use it for a
  proof, a compact experiment, or a critical figure, not for extended literature review.
- Drop the paper-organization paragraph unless the journal explicitly asks for it; a letter should
  be navigable without one.

## Decision checklist

1. Does the target journal match the paper's **scope** before formatting is considered?
2. Does the contribution need a special-issue fit statement (JSAC), wireless realism (TWC), formal
   analytical depth (TCOM), or single-result compression (WCL/CL)?
3. Are page and abstract limits checked against the current Author Kit rather than copied from memory?
4. Does every target-specific claim have target-specific evidence: theme fit, channel realism,
   proof/validation, or concise letter-level comparison?
5. If the paper is rejected for "incremental contribution," would a different target and framing
   be more honest than adding adjectives?

## Output

Return a short `Target-fit note` before drafting:

```
Target-fit note:
- Recommended target: [JSAC/TWC/TCOM/WCL/CL]
- Why it fits: [scope + contribution type]
- Required emphasis: [special issue fit / wireless realism / proof depth / one-result compression]
- Evidence still needed: [target-specific gaps]
```
