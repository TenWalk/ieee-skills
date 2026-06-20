# Matplotlib Patterns for IEEE Communications Figures

Signature comms result figures: **BER/outage vs SNR on a log y-axis**, **rate vs SNR/antennas**,
**convergence**, **CDF**, and the **analysis-line + simulation-marker overlay**. All sized to the
IEEE column.

## Setup — put these rcParams FIRST (font embedding + sizing)

```python
import matplotlib as mpl
import matplotlib.pyplot as plt
import numpy as np

mpl.rcParams.update({
    "font.family": "sans-serif",
    "font.sans-serif": ["Arial", "DejaVu Sans", "Liberation Sans"],
    "pdf.fonttype": 42,    # embed TrueType (avoid type-3) in PDF
    "ps.fonttype": 42,     # same for EPS/PS
    "svg.fonttype": "none",# keep text as <text> nodes in SVG
    "font.size": 8,        # base size; IEEE minimum ~8 pt at final size
    "axes.labelsize": 8,
    "axes.titlesize": 8,
    "legend.fontsize": 7,
    "xtick.labelsize": 7,
    "ytick.labelsize": 7,
    "axes.linewidth": 0.6,
    "lines.linewidth": 1.2,
    "lines.markersize": 4,
    "figure.dpi": 300,
})

# Column widths in inches
SINGLE_COL = 3.5     # 88.9 mm
DOUBLE_COL = 7.16    # 181.6 mm

# Colorblind-safe palette (Okabe–Ito)
CB = ["#0072B2", "#E69F00", "#009E73", "#D55E00", "#CC79A7", "#56B4E9", "#F0E442", "#000000"]
MARKERS = ["o", "s", "^", "D", "v", "P", "X", "*"]
LINESTYLES = ["-", "--", "-.", ":"]
```

## Save helper (vector primary + PNG preview; EPS for letters)

```python
def save_fig(fig, stem):
    fig.savefig(f"{stem}.pdf", bbox_inches="tight")          # primary vector
    fig.savefig(f"{stem}.png", dpi=300, bbox_inches="tight") # preview
    # fig.savefig(f"{stem}.eps", bbox_inches="tight")        # WCL/CL final upload wants EPS
```

## BER / SER vs SNR — log y-axis (the signature comms plot)

Use `semilogy`. Each scheme gets colour + marker + line style so it survives grayscale. The
high-SNR slope is the diversity order — keep the y-range wide enough to show it.

```python
fig, ax = plt.subplots(figsize=(SINGLE_COL, SINGLE_COL * 0.78))
for i, (label, ber) in enumerate(schemes.items()):   # schemes: dict[str, array], ber over snr_db
    ax.semilogy(snr_db, ber, color=CB[i], marker=MARKERS[i], linestyle=LINESTYLES[i % 4],
                label=label, markevery=max(1, len(snr_db)//8))
ax.set_xlabel("SNR (dB)")
ax.set_ylabel("Bit error rate")
ax.set_ylim(1e-5, 1e0)          # floor at the lowest reliably simulated BER — don't plot below it
ax.grid(True, which="both", linewidth=0.4, alpha=0.4)
ax.legend(frameon=False)
save_fig(fig, "fig_ber")
```

## Analysis (line) + simulation (markers) overlay — validates a derivation

Closed-form expression as a line with no markers; Monte-Carlo as markers with no connecting line,
same colour. Two proxy handles label "Analysis" vs "Simulation" without cluttering the legend.

```python
from matplotlib.lines import Line2D
fig, ax = plt.subplots(figsize=(SINGLE_COL, SINGLE_COL * 0.78))
for i, (label, d) in enumerate(results.items()):     # d = {"ana": array, "sim": array}
    ax.semilogy(snr_db, d["ana"], color=CB[i], linestyle="-")                 # analysis
    ax.semilogy(snr_db, d["sim"], color=CB[i], marker=MARKERS[i], linestyle="none")  # simulation
    ax.semilogy([], [], color=CB[i], marker=MARKERS[i], linestyle="-", label=label)  # legend proxy
style = [Line2D([0],[0], color="k", linestyle="-"),
         Line2D([0],[0], color="k", marker="o", linestyle="none")]
leg1 = ax.legend(style, ["Analysis", "Simulation"], frameon=False, loc="lower left")
ax.add_artist(leg1)
ax.legend(frameon=False, loc="upper right")           # scheme legend
ax.set_xlabel("Transmit SNR (dB)")
ax.set_ylabel("Outage probability")
ax.set_ylim(1e-4, 1e0)
ax.grid(True, which="both", linewidth=0.4, alpha=0.4)
save_fig(fig, "fig_outage_validation")
```

## Achievable / sum rate vs SNR — linear y-axis

```python
fig, ax = plt.subplots(figsize=(SINGLE_COL, SINGLE_COL * 0.72))
for i, (label, rate) in enumerate(schemes.items()):  # rate (bps/Hz) over snr_db
    ax.plot(snr_db, rate, color=CB[i], marker=MARKERS[i], linestyle=LINESTYLES[i % 4],
            label=label, markevery=max(1, len(snr_db)//8))
ax.set_xlabel("Transmit SNR (dB)")
ax.set_ylabel("Sum rate (bps/Hz)")
ax.legend(frameon=False)
ax.grid(True, linewidth=0.4, alpha=0.4)
save_fig(fig, "fig_sumrate")
```

## Performance vs a system parameter (antennas / users / RIS elements)

```python
fig, ax = plt.subplots(figsize=(SINGLE_COL, SINGLE_COL * 0.72))
for i, (label, y) in enumerate(schemes.items()):     # y over n_antennas
    ax.plot(n_antennas, y, color=CB[i], marker=MARKERS[i], linestyle=LINESTYLES[i % 4], label=label)
ax.set_xlabel("Number of antennas $N$")
ax.set_ylabel("Energy efficiency (Mbit/J)")
ax.legend(frameon=False)
ax.grid(True, linewidth=0.4, alpha=0.4)
save_fig(fig, "fig_vs_antennas")
```

## Convergence — objective vs iteration

```python
fig, ax = plt.subplots(figsize=(SINGLE_COL, SINGLE_COL * 0.72))
for i, (label, obj) in enumerate(runs.items()):      # obj over iteration index
    ax.plot(np.arange(1, len(obj)+1), obj, color=CB[i], marker=MARKERS[i],
            linestyle=LINESTYLES[i % 4], label=label, markevery=max(1, len(obj)//8))
ax.set_xlabel("Iteration")
ax.set_ylabel("Objective (sum rate, bps/Hz)")
ax.legend(frameon=False)
ax.grid(True, linewidth=0.4, alpha=0.4)
save_fig(fig, "fig_convergence")
```

## NMSE vs SNR — learning-based estimation/feedback (log y-axis)

Channel-estimation / CSI-feedback accuracy. NMSE is usually plotted in dB (`10*log10`) on a linear
axis, or as a ratio on `semilogy`. Compare the learned method against LS/MMSE on the same axes.

```python
fig, ax = plt.subplots(figsize=(SINGLE_COL, SINGLE_COL * 0.78))
for i, (label, nmse_db) in enumerate(schemes.items()):   # nmse_db (dB) over snr_db
    ax.plot(snr_db, nmse_db, color=CB[i], marker=MARKERS[i], linestyle=LINESTYLES[i % 4],
            label=label, markevery=max(1, len(snr_db)//8))
ax.set_xlabel("SNR (dB)")
ax.set_ylabel("NMSE (dB)")
ax.legend(frameon=False)
ax.grid(True, linewidth=0.4, alpha=0.4)
save_fig(fig, "fig_nmse")
```

To show **generalization**, plot the training-SNR range as a shaded band and let the test curve
extend beyond it, so the reader sees behaviour on unseen SNR:

```python
ax.axvspan(train_snr_min, train_snr_max, color="0.85", alpha=0.5, zorder=0)
ax.text(0.02, 0.04, "train range", transform=ax.transAxes, fontsize=6, color="0.4")
```

## Training loss vs epoch (learning convergence)

The learning analogue of the objective-vs-iteration curve. Plot train and validation loss together;
the gap between them is the generalization signal. Use a log y-axis if the loss spans decades.

```python
fig, ax = plt.subplots(figsize=(SINGLE_COL, SINGLE_COL * 0.72))
ax.plot(epochs, train_loss, color=CB[0], linestyle="-",  label="Training loss")
ax.plot(epochs, val_loss,   color=CB[1], linestyle="--", label="Validation loss")
ax.set_xlabel("Epoch")
ax.set_ylabel("Loss (negative sum rate)")   # or NMSE — name the comms metric, not just "loss"
ax.legend(frameon=False)
ax.grid(True, linewidth=0.4, alpha=0.4)
save_fig(fig, "fig_training_loss")
```

Label the y-axis with the **communications metric** the loss represents (NMSE, negative sum rate),
not a bare "loss" — it ties the training curve to the paper's claim.

## Rate–CRB tradeoff region (the signature ISAC plot)

Communication metric on one axis, sensing metric (CRB, usually in dB or log) on the other; each
curve is the Pareto boundary of one scheme, swept over the constraint. Add the orthogonal-split
baseline the joint design beats. Lower CRB and higher rate is better (up and to the left here).

```python
fig, ax = plt.subplots(figsize=(SINGLE_COL, SINGLE_COL * 0.78))
for i, (label, d) in enumerate(schemes.items()):   # d = {"rate": array bps/Hz, "crb": array}
    ax.plot(d["rate"], d["crb"], color=CB[i], marker=MARKERS[i], linestyle=LINESTYLES[i % 4],
            label=label)
ax.set_yscale("log")                       # CRB spans decades; log y is usual
ax.set_xlabel("Sum rate (bps/Hz)")
ax.set_ylabel("Root-CRB of angle (deg)")   # name the estimated parameter and its unit
ax.legend(frameon=False)
ax.grid(True, which="both", linewidth=0.4, alpha=0.4)
save_fig(fig, "fig_rate_crb_tradeoff")
```

## Transmit beampattern (gain in dB vs angle)

```python
fig, ax = plt.subplots(figsize=(SINGLE_COL, SINGLE_COL * 0.72))
for i, (label, gain_db) in enumerate(schemes.items()):  # gain_db over angle_deg (-90..90)
    ax.plot(angle_deg, gain_db, color=CB[i], linestyle=LINESTYLES[i % 4], label=label)
for a in target_angles:                     # mark the sensing directions
    ax.axvline(a, color="0.6", linestyle=":", linewidth=0.6)
ax.set_xlabel("Angle (deg)")
ax.set_ylabel("Beampattern gain (dB)")
ax.set_xlim(-90, 90)
ax.legend(frameon=False)
ax.grid(True, linewidth=0.4, alpha=0.4)
save_fig(fig, "fig_beampattern")
```

## ROC / detection probability (sensing)

```python
fig, ax = plt.subplots(figsize=(SINGLE_COL, SINGLE_COL * 0.78))
for i, (label, d) in enumerate(schemes.items()):   # ROC: d = {"pfa": array, "pd": array}
    ax.plot(d["pfa"], d["pd"], color=CB[i], marker=MARKERS[i], linestyle=LINESTYLES[i % 4],
            label=label, markevery=max(1, len(d["pfa"])//8))
ax.set_xscale("log")                        # Pfa usually log
ax.set_xlabel("False-alarm probability $P_{fa}$")
ax.set_ylabel("Detection probability $P_d$")
ax.set_ylim(0, 1)
ax.legend(frameon=False, loc="lower right")
ax.grid(True, which="both", linewidth=0.4, alpha=0.4)
save_fig(fig, "fig_roc")
```

For CRB validation, overlay the **estimator RMSE as markers on the CRB line** (same colour),
exactly like the analysis-vs-simulation overlay above — the agreement validates the bound.

## CDF (of SINR, rate, or AoI)

```python
fig, ax = plt.subplots(figsize=(SINGLE_COL, SINGLE_COL * 0.72))
for i, (label, samples) in enumerate(schemes.items()):
    xs = np.sort(samples)
    cdf = np.arange(1, len(xs)+1) / len(xs)
    ax.plot(xs, cdf, color=CB[i], linestyle=LINESTYLES[i % 4], label=label)
ax.set_xlabel("Per-user rate (bps/Hz)")
ax.set_ylabel("CDF")
ax.set_ylim(0, 1)
ax.legend(frameon=False)
ax.grid(True, linewidth=0.4, alpha=0.4)
save_fig(fig, "fig_cdf")
```

## Multi-panel (label panels a, b)

```python
fig, axs = plt.subplots(1, 2, figsize=(DOUBLE_COL, DOUBLE_COL * 0.38))
# ... plot on axs[0], axs[1] ...
for ax, tag in zip(axs.ravel(), ["(a)", "(b)"]):
    ax.text(-0.12, 1.02, tag, transform=ax.transAxes, fontweight="bold", va="bottom")
fig.tight_layout()
save_fig(fig, "fig_panels")
```

## Reminders

- Set rcParams **before** plotting.
- BER/outage/error curves use **semilog y** (`semilogy`), with `grid(which="both")`.
- Analysis = line, simulation = markers, same colour; never fabricate the overlap.
- Do not plot a BER/outage point you have too few Monte-Carlo error events to estimate — floor the
  y-axis at the lowest reliable value.
- Define the SNR axis exactly (transmit vs receive); spell out units (dB, bps/Hz, Mbit/J).
- Keep all figures in a paper at the same base font size; re-render at target width, don't shrink.
- Plot only the user's real numbers; never invent points to "complete" a trend.
