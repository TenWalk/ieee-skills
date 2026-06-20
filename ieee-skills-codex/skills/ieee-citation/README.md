# ieee-citation

Format references and in-text citations to IEEE style, and prepare Index Terms and IEEEtran
bibliography setup. Converts raw references, `.bib` files, or DOIs into correct IEEE entries.

## Key rules

- Numbered citations `[n]` in **order of first appearance**; the reference list follows that order
  (not alphabetical).
- Author names as "J. K. Author"; "*et al.*" beyond six authors.
- Abbreviated journal/conference names (e.g., *IEEE Trans. Image Process.*).
- **No fabricated metadata** — missing fields are flagged, never invented.
- Defers to the target journal's Author Kit where conventions differ.

## Structure

```
ieee-citation/
├── SKILL.md
├── README.md
└── references/
    ├── ieee-reference-format.md   entry templates for every source type + in-text rules
    └── ieeetran-latex.md          IEEEtran setup, .bib entry types/fields, Index Terms, pitfalls
```

## Output

A numbered IEEE reference list (or a `.bib` block for LaTeX), in-text citation fixes, flags for
missing fields, and Index Terms on request.
