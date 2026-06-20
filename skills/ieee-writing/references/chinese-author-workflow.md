# Chinese-Author Workflow (中文作者工作流)

Use when the user's input is Chinese, mixed Chinese-English, or organized as lab notes rather than
manuscript prose. The job is to transfer **intent and argument** into IEEE-style English — not to
translate clause by clause.

## Principles

1. **Translate meaning, not word order.** Chinese academic notes often stack clauses and lead with
   background. English IEEE prose leads with the message. Re-order to put the claim first.
2. **One Chinese paragraph may become several English sentences** (or the reverse). Restructure to
   "one paragraph, one job".
3. **Flag, do not invent.** If a note is vague ("效果很好", "有一定提升"), ask for the number or write
   `[PLACEHOLDER: quantify gain]`. Never invent a value to make the sentence read well.
4. **Keep the user's technical terms stable.** Establish the English term for each Chinese concept
   once and reuse it everywhere (see body-revision skill 14).

## Common Chinese-note patterns → English moves

| Chinese note pattern | English manuscript move |
|---|---|
| 背景铺垫很长，最后才说做了什么 | Lead with the contribution; compress background to the gap that motivates it |
| "我们提出了一种方法，可以……" | `We propose [Method], which [capability].` Name the method. |
| "实验证明效果好" | Replace with a quantified comparison vs. a named benchmark scheme, or flag for a number |
| "由于篇幅原因/简单起见，我们假设……" | Rewrite as a bounded assumption (general case → why valid here → adopted) |
| "本文的创新点有：……" | Format as the IEEE contributions list (verb-first, distinct, verifiable) |
| 口语化的"其实/我们发现其实" | Convert to a precise observation: `We observe that ...` |

## Output format for Chinese input

1. **Polished English first** — the submission-ready prose.
2. **中文说明** — a short note (in Chinese) explaining the major structural choices: what was
   re-ordered, what was merged or split, and why. Example:
   > 中文说明：把原文最后一句"我们提出了……"提到段首作为主旨句；背景两句压缩为一句，只保留引出
   > 空白的部分；"效果好"已标记为需要补充与基线对比的具体数值。
3. **需要你补充的内容（missing inputs）** — a Chinese list of anything that must come from the
   author (numbers, benchmark-scheme names, channel/simulation details) before the text is final.

## Quality checks specific to translated text

- No Chinglish calques ("more and more", "make a research", "as we all know").
- US English spelling and IEEE register (see `ieee-polishing`).
- Every "提升/改进" claim has a number or an explicit placeholder.
- Method and module names are in English and identical across sections.
- The contributions list reads as distinct, verifiable items, not a translated wish list.
