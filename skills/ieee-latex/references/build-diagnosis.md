# IEEEtran Build Diagnosis

## Build sequence

Prefer the project's configured tool. If none exists:

```bash
pdflatex -interaction=nonstopmode main.tex
bibtex main
pdflatex -interaction=nonstopmode main.tex
pdflatex -interaction=nonstopmode main.tex
```

For `latexmk` projects:

```bash
latexmk -pdf -interaction=nonstopmode main.tex
```

Use XeLaTeX/LuaLaTeX only when the project already requires them. IEEEtran papers usually compile
with pdfLaTeX unless fonts or Unicode require otherwise.

## Files to inspect

- `.log`: fatal errors, missing files, undefined refs, overfull boxes, package conflicts.
- `.blg`: BibTeX errors, missing bibliography style, malformed `.bib` entries.
- `.aux`: whether citations/labels are written.
- PDF: visual check for figure size, references, equations, and page count.

## Common fatal errors

| Error | Likely cause | Fix |
|---|---|---|
| `File ... not found` | missing figure/style/bib path | fix relative path or restore file |
| `Undefined control sequence` | missing package or typo macro | add minimal package or fix command |
| `Runaway argument` | unclosed brace/environment | inspect preceding lines |
| `Emergency stop` | earlier syntax/file error | fix first real error, not the stop line |
| BibTeX `I couldn't open style file IEEEtran.bst` | missing bst or TeX install issue | install IEEEtran bst or use bundled template file |

## Undefined citations and references

- Undefined citation: key absent from `.bib`, typo in `\cite{}`, BibTeX did not run, or `.bib` not
  included.
- Undefined reference: missing `\label{}`, wrong label name, label placed before caption in figures,
  or LaTeX needs another run.
- `??` after full build means unresolved; do not ignore.

## BibTeX troubleshooting

IEEEtran setup:

```latex
\bibliographystyle{IEEEtran}
\bibliography{refs}
```

Common fixes:

- escape `&`, `%`, `_`, and unmatched braces in `.bib`;
- protect capitalization in titles only where needed: `{RIS}`, `{MIMO}`, `{CRB}`;
- avoid `biblatex`/`biber` unless the template explicitly uses it;
- remove duplicate keys;
- verify `.bib` encoding if non-ASCII author names break BibTeX.

## Overfull hboxes

Fix meaningful overfull boxes, especially in final PDF:

- break long equations with `aligned`, `split`, or `IEEEeqnarray`;
- shorten URLs/DOIs or let IEEE style handle them;
- avoid long unbreakable math symbols in captions;
- rephrase dense paragraphs instead of reducing font size;
- move wide tables to double column only when IEEE allows it.

Do not globally loosen typesetting (`\sloppy`) unless there is no better local fix.

## Figure/table problems

- Use `.pdf`/`.eps` vector figures for line art; avoid low-resolution screenshots.
- Put `\label{}` after `\caption{}`.
- Keep captions self-contained but concise.
- For two-column figures, use `figure*` only when necessary and check placement.
- Do not force floats with aggressive `[H]` unless the template and packages allow it.

## Clean rebuild

When stale aux files cause confusion, remove generated files only after preserving source:

```bash
latexmk -C
latexmk -pdf main.tex
```

Never delete source `.tex`, `.bib`, figures, or template files while cleaning.
