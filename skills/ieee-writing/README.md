# ieee-writing

Draft and rebuild IEEE-journal manuscript sections from author claims, results, figures,
notes, or Chinese drafts. This skill is for **argument construction** — building the paper's
logic — not sentence-level grammar (use `ieee-polishing` for that).

## What it produces

Section drafts (abstract, Index Terms, introduction with a contributions list, related work,
system model, problem formulation, proposed solution/algorithm, performance analysis with
theorems/proofs, numerical results narrative, discussion, conclusion, title), full outlines, and a
claim–evidence map that flags any unsupported claim or missing input.

## How it is organised

`SKILL.md` is a lean router. It carries the IEEE section defaults and a "When to open extra
files" table; detailed templates, sentence skeletons and revision rules live in `references/`:

```
ieee-writing/
├── SKILL.md
├── README.md
└── references/
    ├── abstract.md                        Abstract structure + Index Terms; method-paper variants
    ├── journal-fit.md                     JSAC/TWC/TCOM/WCL/CL routing, evidence depth, page strategy
    ├── introduction.md                    Backward→forward logic, versioned templates, contributions list
    ├── method.md                          System model, problem formulation, proposed solution: signal flow, notation, algorithm box
    ├── system-model-paradigms.md          Per-paradigm System Model cheat-sheet (RIS, NOMA, ISAC, near-field, movable antenna, cell-free, mmWave, semantic)
    ├── learning-based-comms.md            DL/deep-unfolding/DRL for PHY/MAC: architecture, training, loss tied to metric, generalization & complexity
    ├── theory-and-proofs.md               Optimization transformations (AO/SCA/SDR/FP/ADMM), theorems/proofs, convergence & complexity
    ├── results-discussion-conclusion.md   Numerical-results evidence ladder, interpretation, bounded conclusion
    ├── body-revision.md                   16 general revision skills: flow, compression, term consistency
    └── chinese-author-workflow.md         中文笔记 → 投稿级英文 + 中文说明
```

## Key rules enforced

- Evidence first: no invented data, numbers, citations, benchmark schemes, novelty, or limitations.
- IEEE structure: Roman-numeral sections, explicit contributions list, paper-organization
  paragraph, US English, numbered citations `[n]`, equations numbered only for the skeleton.
- One paragraph, one job; first sentence states the message.
- Calibrated claims: verb strength matches evidence strength.
- Bilingual: translate Chinese intent and argument, not clause order.

## Relationship to other skills

Use `ieee-experiments` to decide what evidence to run, `ieee-figure` for result plots,
`ieee-citation` for reference formatting, and `ieee-response` after peer review.
