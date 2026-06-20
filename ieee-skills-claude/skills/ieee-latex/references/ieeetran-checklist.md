# IEEEtran Submission Checklist

## Document class and front matter

Typical journal setup:

```latex
\documentclass[journal]{IEEEtran}
```

Check the target author kit before changing options. Some venues/templates have special options for
draft, peer review, compsoc, technote, or conference mode.

Front matter:

- title concise and not overloaded with acronyms;
- author block matches submission anonymity policy;
- abstract one paragraph, no citations/equations/undefined acronyms;
- `\begin{IEEEkeywords} ... \end{IEEEkeywords}` or template-specific Index Terms block;
- EDICS included for CL if required by the current submission system.

## Section structure

- Roman-numeral numbered sections are automatic in IEEEtran.
- Letter papers usually avoid a standalone Related Work section and organization paragraph.
- Appendices are acceptable in transactions but often poor fits for WCL/CL; confirm target rules.
- Acknowledgment placement follows template instructions and anonymity policy.

## Equations and algorithms

- Number only equations referenced later.
- Use `\label{}` after the equation environment begins and reference with `\eqref{}`.
- Use `IEEEeqnarray` or `aligned` for long equations; avoid shrinking math fonts.
- Algorithm packages can conflict with IEEE style; keep captions and numbering consistent.

## Figures and tables

- Single-column width is about 3.5 in; double-column width about 7.16 in.
- Use vector PDF/EPS for plots and readable fonts at final size.
- `\label{}` follows `\caption{}`.
- Table captions go above tables; figure captions go below figures.
- Avoid vertical rules in tables unless the target template already uses them.

## References

- Use `IEEEtran.bst` unless the journal template says otherwise.
- References are numbered by first citation order.
- Every bibliography entry must be cited; every citation must resolve.
- Use `ieee-citation` for field formatting and abbreviation decisions.

## Page and production checks

- Verify page count against the target journal and letter rules.
- Check no final PDF text says `??`, `[?]`, "Citation undefined", or "Reference undefined".
- Check all figures are present, not cropped, and legible in grayscale.
- Check overfull boxes visible in equations/tables/captions.
- Check metadata: title, authors, affiliations, funding, acknowledgments, ORCID when required.

## Final response format for an audit

```text
IEEEtran checklist:
- Front matter: pass / issue
- References: pass / issue
- Figures/tables: pass / issue
- Page limit: pass / issue
- Remaining author decisions: ...
```
