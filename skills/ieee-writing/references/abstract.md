# Abstract + Index Terms (IEEE)

## Goal

A self-contained paragraph a reviewer can read in 30 seconds and know: the problem, the gap,
what you did, the single strongest quantitative result, and what it enables. IEEE transaction
abstracts are typically **150–250 words**; WCL/CL letters are much tighter, commonly **75–100
words** under current ComSoc guidance. Use **one paragraph**, with **no citations, no undefined
abbreviations, no equations, no figure/table references**.

## Default structure

```
1. Context / problem      one or two sentences on the system/task and why it matters
2. Gap                    the specific limitation of current schemes
3. Approach               what you propose (name it), in one or two sentences
4. Key result             the single strongest, quantified outcome vs. a benchmark scheme
5. Implication / boundary what it enables, and the scope (CSI/channel) where it holds
```

Sentence skeletons:

- `[System/task] is essential for [application], yet [current schemes] [limitation].`
- `This [paper/article] proposes [scheme/algorithm], a [type] that [core idea].`
- `[Scheme] [mechanism, e.g. jointly optimizes ...] to [effect, e.g. maximize the sum rate].`
- `Simulation results show that [scheme] [quantified gain, e.g. an X dB SNR gain / near-optimal
  sum rate] over [benchmark scheme], achieving [number] [metric, e.g. bps/Hz].`
- `These results indicate that [implication], under [boundary, e.g. the considered CSI model].`

## Variants for method/algorithm papers

Pick one when the contribution is technical rather than empirical:

- **challenge → contribution**: state the technical challenge, then the one idea that resolves it.
- **challenge → insight → contribution**: add the key observation that motivates the method.
- **multiple contributions**: when there are two genuinely separate advances, name each once.

Keep at most one quantitative headline result in the abstract; save the rest for Results. For a
letter, cut the context and implication to one sentence each and preserve the problem, one result,
and boundary.

## Index Terms

Immediately after the abstract:

```
Index Terms—<term a>, <term b>, <term c>, <term d>, <term e>.
```

- 5–8 terms, **alphabetical order**, lower case except proper nouns and acronyms.
- Prefer IEEE Taxonomy / established community terms over invented phrases (improves indexing
  and discoverability). If the target journal supplies a controlled keyword list, use it.
- Mix levels: the task, the method family, the application domain, and the channel/system model.

## Common failure modes (check before returning)

1. Abstract contains a citation, an abbreviation defined nowhere, or `Fig.`/`Table` reference.
2. The "key result" is qualitative ("significantly better") with no number.
3. The first sentence is a textbook truism instead of this paper's problem.
4. Over-claim: "first", "optimal", "solves" — downgrade unless literally proven.
5. Word count outside the target journal's stated limit, especially an overlong WCL/CL abstract.
6. The abstract promises something the paper does not deliver — align with the contributions list.

## Output

Return the abstract, then the Index Terms line, then a one-line word count and a note on any
number used as the headline result (so the user can confirm it is real and matches the paper).
