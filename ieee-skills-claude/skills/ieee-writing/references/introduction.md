# Introduction Writing Guide (IEEE)

## Goal

Write Section I so a reviewer understands, in order: the task and why it matters, how prior
methods work and exactly where they fail (with the technical reason), the gap this paper
closes, your approach and why it works, an explicit **contributions list**, and a one-sentence
**paper-organization** paragraph. The IEEE introduction ends with the contributions list — this
is a genre expectation, not optional.

## Think backward first, then write forward

### Backward reasoning (answer these before writing a word)

1. What technical problem do we solve, and why is there no established solution? *(most important)*
2. What are the contributions (a new method, a new task/benchmark, a new module on an existing
   pipeline, a new theoretical result, or a new empirical finding)?
3. Why do these contributions actually resolve the challenge, and what new insight do they give? *(important)*
4. How do we walk the reader through prior methods so the gap feels inevitable, not asserted?

### Forward story (write in this order)

1. Introduce the task and its applications.
2. Use prior methods to lead to the exact technical challenge — limitation **and** its
   technical cause.
3. Present the proposed approach as the response to that challenge.
4. State the technical advantage and the new insight explicitly.
5. List contributions.
6. State paper organization.

## Section skeleton

```latex
\section{Introduction}
% Task and application importance
% How prior methods work, their limitation, and the technical reason (the challenge)
% Our approach for solving the challenge, and why it works (the insight)
% Contributions list
% Paper organization
```

## Part A — Task and application

Choose by how familiar the task is to the journal's readership:

- **A1 (niche task):** define the task in one sentence (`what output` from `what input`), then
  give 2–3 application scenarios.
  - `[Task] aims to estimate/recover/predict [output] from [input].`
  - `[Task] underpins applications such as [x], [y], and [z].`
- **A2 (familiar task):** skip the definition; open with application importance, optionally add
  the target requirement (data rate / latency / reliability / energy efficiency).
- **A3 (new setting of a known task):** start general, then narrow to this paper's setting and
  fix its exact input/output and boundary. Recommended when the setting is itself a contribution.

## Part B — Technical challenge of prior methods *(the crucial part)*

Purpose: discuss **around the exact challenge you solve**, build curiosity about how to solve
it, and make your motivation clear. A challenge = an observable limitation **plus** its
technical cause.

**Warning:** do not present a naive solution first and then describe your improvement over it.
That framing makes even good work read as an incremental patch and kills reviewer curiosity.

- **B1 (existing task, existing methods):** challenge chain — general challenge → traditional
  methods + limitation → recent methods (1) + limitation with reason → recent methods (2) +
  limitation with reason. Make the **final** limitation exactly the one you solve.
  - `This problem is particularly challenging because ...`
  - `Traditional methods ... However, they ... because ...`
  - `Recently, ...-based methods ... However, they still ... because ...`
- **B2 (insight has classical roots):** mainstream methods + limitation → a classical line that
  already hints at your insight → why it is still insufficient → modern methods + the unresolved
  reason → bridge to your method.
- **B3 (novel task, no direct prior methods):** define the challenge directly and decompose it.
  - `Our goal is to ... This is challenging for [N] reasons. First, ... Second, ... Finally, ...`
  - For each point: state the observable limitation and the technical reason.

## Part C — Proposed approach and contributions

Answer before writing: What challenge does the approach solve? What is the contribution? Why
does it work in essence? What is the advantage over prior methods?

- **C1 (one contribution, multiple advantages):** name the framework, point to the framework
  figure, state the key novelty in one sentence, give concrete steps (`Specifically, ...`), then
  list advantages (`In contrast to prior methods, ...`; `A further advantage is ...`).
- **C2 (two contributions):** framework + novelty → contribution 1 + advantage → remaining
  challenge (`However, ...`) → contribution 2 as the response.
- **C3 (new module on an existing pipeline):** start from the prior pipeline → introduce the one
  new module as the key innovation → give the observation that motivates it (`We observe that ...`)
  → explain the mechanism → compare against generic alternatives.
- **C4 (observation-driven):** state the key innovation first → one intuitive observation as
  motivation → implementation → advantage and empirical gain.

Skeletons:

- `In this paper, we propose [Method], a novel [type] for [task].`
- `Our key idea is to [insight].`
- `Specifically, [Method] [step 1]; [step 2]; and [step 3].`
- `In contrast to prior methods that [behaviour], [Method] [different behaviour], which [benefit].`

**Not recommended:** hiding a simple pipeline behind abstract insights and many new terms to
fake novelty. Reviewers read this as shallow. Prefer to explain the core contribution clearly.

## Part D — Contributions list (IEEE genre requirement)

After the approach paragraphs:

```
The main contributions of this [paper/article] are summarized as follows:
1) We propose [scheme/algorithm] for [system/problem], which [key idea].
2) We [formulate the problem / derive a closed-form expression for outage/BER/rate / prove
   convergence], which [what it enables or reveals].
3) Simulation results show [headline result, e.g. an X dB SNR gain / near-optimal sum rate /
   the claimed diversity order], [significance].
```

Rules:
- 2–4 items. Each item is a **distinct** contribution, not a restatement of the same idea.
- Lead each with a verb (`We propose / formulate / derive / prove / show`).
- Make each contribution **verifiable** by something later in the paper (a theorem, an algorithm, a
  simulation figure); do not list claims the analysis or simulations cannot support.
- The last item is often the simulation validation. Quantify it if a clean headline number exists.
- Do not inflate routine derivation steps into separate "contributions".

## Part E — Paper organization

One short paragraph:

```
The remainder of this [paper/article] is organized as follows. Section II describes the system
model. Section III formulates the problem and presents the proposed algorithm. Section IV reports
the numerical results. Section V concludes the paper.
```

Adjust to the actual section count. Omit only if the target journal explicitly discourages it.

## Quick quality checklist

1. Does the first sentence of each paragraph state its message?
2. Does each paragraph carry exactly one message?
3. Are the technical challenge, its cause, and your resolving mechanism all explicit?
4. Is every contribution backed by something later in the paper?
5. Is terminology identical to the Method, Experiments, figures and tables?
6. Did you avoid "first/optimal/in all cases" unless literally proven?
7. Are citations numbered `[n]` and ordered by first appearance (see `ieee-citation`)?
