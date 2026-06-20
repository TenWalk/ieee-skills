# IEEEtran + BibTeX Setup

## Document class and bibliography

```latex
\documentclass[journal]{IEEEtran}   % options: conference, journal, technote, etc.

% ... body ...

\bibliographystyle{IEEEtran}
\bibliography{refs}                  % refs.bib in the same folder
```

`IEEEtran.bst` handles numbering by order of appearance, name formatting ("J. K. Author"),
"*et al.*" truncation, and venue abbreviation. Use BibTeX (or biber configured for it) — do not
hand-number the list when using LaTeX.

## In-text citation

```latex
as shown in \cite{he2016deep}
multiple: \cite{he2016deep, devlin2019bert}
range collapses automatically: \cite{a,b,c,d}  ->  [1]–[4]
```

Load `cite.sty` (often already pulled in) so multiple/consecutive citations sort and compress:
`\usepackage{cite}`.

## Common BibTeX entry types and required fields

```bibtex
@article{key,
  author  = {K. He and X. Zhang and S. Ren and J. Sun},
  title   = {Deep residual learning for image recognition},
  journal = {IEEE Trans. Pattern Anal. Mach. Intell.},
  volume  = {42},
  number  = {8},
  pages   = {1234--1245},
  year    = {2020},
  month   = aug,
  doi     = {10.1109/TPAMI.2019.XXXXXXX}
}

@inproceedings{key,
  author    = {J. Devlin and M.-W. Chang and K. Lee and K. Toutanova},
  title     = {{BERT}: Pre-training of deep bidirectional transformers for language understanding},
  booktitle = {Proc. NAACL-HLT},
  address   = {Minneapolis, MN, USA},
  pages     = {4171--4186},
  year      = {2019}
}

@book{key,
  author    = {S. Boyd and L. Vandenberghe},
  title     = {Convex Optimization},
  publisher = {Cambridge Univ. Press},
  address   = {Cambridge, U.K.},
  year      = {2004}
}

@phdthesis{key,
  author = {A. B. Author},
  title  = {Title of thesis},
  school = {Dept. Elect. Eng., Univ. Name},
  address= {City, Country},
  year   = {YYYY}
}

@misc{key,
  author       = {A. B. Author},
  title        = {Title of the paper},
  year         = {2024},
  eprint       = {2401.01234},
  archivePrefix= {arXiv}
}
```

Field notes:
- `author`: separate names with " and "; use initials + surname. Protect capitals/acronyms in
  titles with braces, e.g. `{BERT}`, `{CNN}` — otherwise BibTeX lowercases them.
- `pages`: en-dash via `--`.
- `month`: use the three-letter macros (`jan`, `feb`, ...), unquoted.
- Leave a field **out** if unknown rather than inventing it.

## Automatic venue abbreviation

`IEEEtran.bst` does not abbreviate by itself; supply already-abbreviated `journal`/`booktitle`
strings, or use `IEEEabrv.bib` string definitions:

```latex
\bibliography{IEEEabrv,refs}
```

and in `refs.bib`: `journal = IEEE_J_PAMI,` (a string defined in `IEEEabrv.bib`). Use this only
if you have `IEEEabrv.bib`; otherwise write the abbreviation directly.

## Index Terms in IEEEtran

```latex
\begin{IEEEkeywords}
beamforming, energy efficiency, reconfigurable intelligent surface, resource allocation, sum rate
\end{IEEEkeywords}
```

5–8 terms, alphabetical, lower case except proper nouns/acronyms.

## EDICS (required for IEEE Communications Letters)

EDICS (Editor's Decision Information Classification System) is a submission-time subject
classification, separate from Index Terms. **IEEE CL requires it; WCL does not** (verify against the
current author kit). It routes the paper to the right editor, so pick the closest category, not the
most flattering one.

- Choose 1–3 codes from the journal's **current EDICS list** (on its submission page) — the list is
  journal-specific and changes; do not reuse another journal's codes.
- Enter EDICS where the submission system asks, not in the manuscript body (unless the kit says so).
- **Never invent an EDICS code.** If unsure, pick the single best match and tell the author to
  confirm against the live list.

## Pre-submission citation checks

1. Compile twice (LaTeX → BibTeX → LaTeX → LaTeX) so all `[n]` resolve.
2. No `[?]` in the PDF (means an undefined `\cite` key).
3. Every entry is cited; no orphan entries (IEEEtran lists only cited ones with `\bibliography`).
4. Acronyms in titles preserved (brace protection worked).
5. Page ranges use en-dashes; DOIs resolve.
6. Author count: confirm "*et al.*" truncation matches the journal's rule (often >6).

## Troubleshooting

- **Lowercased title acronym** → brace it: `{IEEE}`, `{LSTM}`.
- **Wrong name order** → ensure "and"-separated names; IEEEtran reformats to initials + surname.
- **Citations not compressing to a range** → add `\usepackage{cite}`.
- **`??` for a reference** → undefined key or BibTeX not re-run; rebuild the full sequence.
