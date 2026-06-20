# Tables and Claim Mapping

## In communications, most results are figures

PHY/network comms papers carry their evidence mainly in **figures** (BER/outage/rate vs SNR);
tables are reserved for the simulation-parameters list, complexity-order comparison, and occasional
summary numbers. Pick a table only when the data is categorical or a few discrete numbers; pick a
figure for any sweep. The claim-mapping discipline below applies to both.

## One figure/table, one question

Before building a figure or table, name the question it answers: validation (theory vs simulation),
performance vs benchmarks, a parameter sweep, design analysis, convergence, or complexity. If two
answer the same question, merge or cut. A reader should know from the caption alone what it proves.

## Map every figure and table to a claim

Build a matrix and keep it until submission:

```
Contribution / claim              Evidence (figure/table)            Status
C1 derived outage is correct      Fig. 3 (analysis vs simulation)    done
C2 scheme beats prior-art         Fig. 4 (sum rate vs SNR)           done
C3 each design choice is needed   Fig. 5 ("w/o" variants)            to run
C4 low complexity                 Table II (per-iter complexity)     done
```

If a claim has no evidence row, either run the simulation or soften the claim. If a figure/table
maps to no claim, cut it.

## Table / prose division of labour

- **Tables/figures carry facts**: schemes, settings, and numbers/curves.
- **Prose explains** principle, reason, and what the numbers mean.
- Do not restate every number in prose; reference the figure and interpret the trend:
  "Fig. 4 shows a consistent gain across the SNR range, indicating ...".
- Settings shared by all schemes go in one place (the parameters table), not repeated per scheme.

## Reading a results figure aloud (the analysis paragraph)

Each comparison paragraph: what was observed → what it means → how it supports the claim. Not "the
proposed scheme gains 3 dB" alone, but "the proposed scheme achieves a ~3 dB SNR gain over ZF
across the whole range, and the curves share the same high-SNR slope, indicating the gain comes
from the joint design rather than from a change in diversity order."

## IEEE table conventions

- Caption **above** the table (IEEEtran style); figures get captions **below**.
- Number tables with Roman numerals (Table I, Table II) — IEEEtran default.
- Bold or otherwise mark the best result per column; state in the caption what bold means.
- Keep decimals consistent down a column; do not over-report precision.
- Use `booktabs`-style rules (top/mid/bottom), no vertical rules, for a clean IEEE look.
- Keep the table within column or page width; for wide tables use `table*` (double-column float).
- Define non-obvious column abbreviations in the caption or a footnote.
- Put units in the column header, not in every cell.

## Two common comms tables

A **complexity comparison** (the most common comms table):

```latex
\begin{table}[t]
  \centering
  \caption{Per-iteration computational complexity. $N$: antennas, $K$: users.}
  \label{tab:complexity}
  \begin{tabular}{lc}
    \toprule
    Scheme & Per-iteration complexity \\
    \midrule
    ZF (conventional)      & $\mathcal{O}(N^2 K)$ \\
    Prior-art [12]         & $\mathcal{O}(N^3 K)$ \\
    \textbf{Proposed}      & $\mathcal{O}(N^2 K + K^3)$ \\
    \bottomrule
  \end{tabular}
\end{table}
```

A **simulation-parameters table** (put shared settings here once):

```latex
\begin{table}[t]
  \centering
  \caption{Simulation parameters.}
  \label{tab:params}
  \begin{tabular}{ll}
    \toprule
    Parameter & Value \\
    \midrule
    Carrier frequency      & 28 GHz \\
    Antennas $N$ / users $K$ & 64 / 8 \\
    Channel model          & Rician, $K$-factor $=$ 5 dB \\
    Noise power            & $-94$ dBm \\
    Monte-Carlo trials     & $10^4$ \\
    \bottomrule
  \end{tabular}
\end{table}
```

## Checks

1. Every figure/table maps to a stated claim.
2. Caption position correct (above for tables, below for figures).
3. Best-result marking defined; complexity given in big-O of stated dimensions.
4. No number duplicated between figure/table and prose.
5. Decimals consistent within a column; SNR axis and trial count stated.
