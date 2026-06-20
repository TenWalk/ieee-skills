# IEEE Figure Specification

> These are robust defaults from IEEE graphics guidance. Always check the **target journal's**
> Author Center / graphics checklist, since limits (especially color-in-print and exact dpi)
> vary.

## Size (design at final print size)

| Layout | Width |
|---|---|
| Single column (IEEEtran 2-column class) | ~3.5 in / 88.9 mm |
| Double column / full text width | ~7.16 in / 181.6 mm |
| Max height (within text block) | ~9.69 in / 246 mm |

Height is chosen for aspect ratio; keep figures as short as the data allows. Designing at final
width is the single most important rule — it makes fonts and markers end up the right size.

## Resolution and file format

- **Vector (preferred for plots/line art):** PDF or EPS. Text stays selectable; scales cleanly.
- **Raster (photos, rendered scenes):** ≥ 300 dpi for color/grayscale; ≥ 600 dpi for line art;
  ~600–1200 dpi for combination line+halftone. PNG/TIFF.
- Embed all fonts. Avoid type-3 fonts; use TrueType/Type-1 (see matplotlib-patterns.md).

## Fonts and text

- Sans-serif (Arial / Helvetica / DejaVu Sans) is safe and legible at small sizes.
- Minimum ~8 pt at final size for axis labels, ticks, legend; keep all panels consistent.
- Match text sizes across figures in the paper — do not let one figure have tiny text.
- Spell out axis quantities with units, e.g., "Transmit SNR (dB)", "Sum rate (bps/Hz)".

## Communications axis and curve conventions

- **Log y-axis for error/outage:** BER, SER, FER, and outage/coverage probability are plotted with
  a logarithmic y-axis (`semilogy`); show enough decades that the high-SNR slope is visible.
- **The slope is information:** the high-SNR slope of a BER/outage curve is the diversity order —
  do not crop the SNR range so short that the slope cannot be read.
- **Define the SNR axis:** state transmit vs receive SNR, total vs per-antenna power — in the label
  or caption. An ambiguous SNR axis is the most common comms-figure reviewer complaint.
- **Analysis vs simulation:** plot the closed-form expression as a line and Monte-Carlo points as
  markers (same colour); a small legend distinguishes "Analysis" from "Simulation". The overlap is
  evidence the derivation is correct — never draw markers on a line you did not actually simulate.
- **Floor the error axis** at the lowest BER/outage you have enough Monte-Carlo error events to
  estimate; do not extend a curve into unestimated territory.
- **Learning curves:** NMSE is plotted in dB vs SNR (compare the learned method to LS/MMSE); shade
  the training-SNR range to expose generalization to unseen SNR. Label a training-loss y-axis with
  the communications metric it represents (NMSE, negative sum rate), not a bare "loss".
- **ISAC dual-metric / tradeoff:** plot the communication metric against the sensing metric (rate
  vs CRB), each curve a Pareto boundary; CRB usually on a log axis with the estimated parameter and
  unit named (e.g. "Root-CRB of angle (deg)"). Include the orthogonal-split baseline. For
  beampatterns, gain in dB vs angle with target directions marked; validate a CRB by overlaying the
  estimator RMSE as markers on the CRB line.

## Color and grayscale

- Use a **colorblind-safe** palette (e.g., Okabe–Ito, or matplotlib `tab10` used carefully).
- Encode each series **redundantly**: colour **plus** marker shape / line style / hatch, so the
  figure is readable when printed in black and white.
- Many IEEE journals print in grayscale (color free online, sometimes a fee in print). Verify a
  grayscale conversion is still unambiguous.
- Avoid red/green as the only distinction; avoid rainbow colormaps for quantitative data — use
  perceptually uniform maps (viridis, cividis) for heatmaps.

## Multi-panel layout

- Label panels (a), (b), (c) — lower case in parentheses — consistent with text references.
- Each panel answers a distinct question; no two panels duplicate information.
- Align axes and share scales across panels where comparison is intended.
- Keep whitespace tight but leave room for labels; do not crop ticks or legends.

## Captions (IEEE)

- Figure caption goes **below** the figure (tables get captions above).
- Number with Arabic numerals: "Fig. 1." Caption is a sentence that states what the figure shows.
- Define panel letters and any abbreviation/marking in the caption; the figure should be
  understandable without hunting through the body.

## Pre-submission checklist

1. Figure width equals the target column width; text ≥ 8 pt at that size.
2. Vector output with embedded fonts (no type-3); EPS for WCL/CL final upload.
3. Series distinguishable in grayscale (redundant encoding).
4. Error/outage curves on a log y-axis; SNR axis defined (transmit vs receive).
5. Axes labelled with units (dB, bps/Hz, ...); legend present and unambiguous.
6. Analysis-vs-simulation overlay where a closed form is derived; markers only where simulated.
7. Panels labelled (a)/(b)/...; caption below; "Fig. n" numbering.
8. Only real data plotted; any placeholder clearly marked.
