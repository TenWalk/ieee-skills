# ieee-figure

Produce publication-grade result figures sized and styled for IEEE journals. For *which*
experiments/metrics to plot, use `ieee-experiments`.

## What it enforces

- Column-correct sizing: single ≈ 3.5 in (88.9 mm), double ≈ 7.16 in (181.6 mm), designed at
  final size.
- Vector output (PDF/EPS) with embedded fonts; high-res raster only for photos (≥300 dpi color,
  ≥600 dpi line art).
- Minimum ~8 pt text at print size; redundant encoding (colour + marker/linestyle/hatch);
  colorblind- and grayscale-safe.
- One panel per question; self-explanatory with the caption; figure caption **below**.
- Only real data — no fabricated points.

## Structure

```
ieee-figure/
├── SKILL.md
├── README.md
└── references/
    ├── ieee-figure-spec.md       sizing, resolution, fonts, colour, formats, layout, checklist
    └── matplotlib-patterns.md    rcParams + sizing + palettes + bar/line/error-bar/heatmap patterns
```

## Output

A runnable matplotlib script using the user's data, a vector file plus a PNG preview, a one-line
caption draft, and size/font/grayscale confirmation.
