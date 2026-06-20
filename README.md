# ieee-skills

A bilingual (中文 / English) collection of Claude skills for writing **IEEE communications-journal**
papers — targeted at **JSAC, TWC, TC/TCOM, WCL, and CL** — and applicable to IEEE Transactions/letters
generally. Each `skills/ieee-*` directory is one installable unit centred on a `SKILL.md`. Copy the
whole folder, not only `SKILL.md`, because most skills depend on their `references/` files.

The design follows four ideas borrowed from mature skill collections and adapted to IEEE:

1. **Progressive disclosure** — a lean `SKILL.md` routes to detailed `references/*.md` only
   when needed, so context stays small but depth is unlimited.
2. **Section-aware logic** — abstract, introduction, method, results, discussion and
   conclusion each have their own moves, tense and hedging; the skills switch logic by section.
3. **Target-journal routing** — JSAC, TWC, TCOM/TC, WCL, and CL are not treated as a single
   template: the skills route by scope, evidence depth, and page strategy before drafting.
4. **Evidence-first, output-first** — never fabricate data, numbers, citations or limitations;
   always return something usable (prose, a `.bib`/`.tex` snippet, a figure script, a letter).

> IEEE differs from general "Nature-style" writing in concrete ways these skills enforce:
> numbered citations `[1]`, the IEEEtran template, an **Index Terms** block, Roman-numeral
> section headings, US English by default, and a more technical, less narrative register.
> Always defer to the **specific** journal's Author Kit when it conflicts with a default here.

## Skill index

| Skill | Purpose | Trigger keywords |
|-------|---------|------------------|
| [`ieee-writing`](skills/ieee-writing/README.md) | Draft or rebuild IEEE manuscript sections from claims, results, figures, or Chinese notes | "write IEEE paper", "write abstract/introduction/method", "restructure my draft", "正文撰写" |
| [`ieee-polishing`](skills/ieee-polishing/README.md) | Sentence-level polishing to IEEE style; Chinese→English translation | "polish", "IEEE style", "make it publishable", "润色", "改成英文" |
| [`ieee-citation`](skills/ieee-citation/README.md) | IEEE numbered references, BibTeX/IEEEtran formatting, Index Terms | "IEEE citation", "format references", "IEEEtran", "参考文献格式", "Index Terms" |
| [`ieee-experiments`](skills/ieee-experiments/README.md) | Comms simulation design: benchmark schemes, comms metrics, Monte-Carlo, analysis-vs-simulation validation, fairness boundaries | "benchmark schemes", "simulation setup", "Monte-Carlo", "对比方案", "蒙特卡洛仿真" |
| [`ieee-figure`](skills/ieee-figure/README.md) | Publication-grade result figures sized for IEEE columns (vector output, correct fonts) | "IEEE figure", "result plot", "publication figure", "结果图", "画图" |
| [`ieee-response`](skills/ieee-response/README.md) | Point-by-point reviewer response letters and cover letters | "response to reviewers", "rebuttal", "cover letter", "审稿回复", "回复审稿人" |
| [`ieee-letter`](skills/ieee-letter/README.md) | WCL/CL letters: single contribution, page budget, compression, EDICS | "WCL letter", "CL letter", "5-page letter", "投WCL", "压缩成letter", "通信快报" |

## Installation

### Claude Code / Cowork (plugin marketplace)

```bash
/plugin marketplace add <path-or-git-url-to-this-folder>
/plugin install ieee-skills
/reload-plugins
```

### Manual / other agents

Copy any `skills/ieee-*/` directory (with its `references/`) into your agent's skills folder,
e.g. `~/.claude/skills/` or `~/.codex/skills/`, then restart the agent.

## Suggested workflow across skills

```
ieee-writing      draft the argument and sections
   ↓
ieee-experiments  make the evidence (benchmark schemes, comms metrics, Monte-Carlo) match the claims
   ↓
ieee-figure       turn key results into IEEE-sized figures
   ↓
ieee-polishing    bring every sentence to IEEE style and US English
   ↓
ieee-citation     format references and Index Terms for IEEEtran
   ↓
ieee-response     after review, answer every comment point by point
```

For a **WCL/CL letter**, use `ieee-letter` as the spine instead of `ieee-writing`: it plans the
single contribution, the free-page budget, and any paid fifth-page decision first, then pulls in
`ieee-experiments`, `ieee-figure`, `ieee-polishing`, and `ieee-citation` (incl. EDICS for CL) as
above.

## Shared design principles

1. **Primary, journal-grounded rules** — formatting rules follow IEEE Author Center / IEEEtran
   conventions, not personal taste; where journals vary, the skill says "check the Author Kit".
2. **Explain the why** — every rule states its rationale so the model can judge edge cases
   instead of following rote MUSTs.
3. **No fabrication** — missing data, numbers, citations or limitations become explicit
   placeholders or questions, never invented content.
4. **Bilingual intent transfer** — Chinese author notes are translated by *meaning and argument*,
   not clause order, with brief Chinese notes explaining major structural choices.
5. **Self-contained and extensible** — each skill lives in its own directory; adding a skill
   requires no change to the others.

## Adding a new skill

1. Create `skills/ieee-<topic>/` with `SKILL.md` (frontmatter `name` + `description`) and
   `README.md`; add `references/*.md` for anything that would push `SKILL.md` past ~400 lines.
2. Add a row to the Skill index table above.
3. Keep the SKILL.md a *router*: a short core plus a "When to open extra files" table.

## Candidate skills (not yet built)

| Candidate | Scope |
|-----------|-------|
| `ieee-methods` | Reproducibility-checklist Methods writing, notation tables, complexity statements |
| `ieee-cover` | Stand-alone cover-letter and significance-framing assistant |
| `ieee-search` | Multi-source literature search and DOI verification with an MCP backend |
| `ieee-latex` | Full IEEEtran build, BibTeX troubleshooting, overfull-hbox and `??` reference checks |
