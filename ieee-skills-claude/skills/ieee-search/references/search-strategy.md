# IEEE Communications Search Strategy

## Query families

Build at least three query families so the search does not miss adjacent terminology:

```text
System/task: "RIS beamforming imperfect CSI", "cell-free massive MIMO fronthaul", "ISAC CRB rate"
Method: "successive convex approximation", "deep unfolding WMMSE", "semantic communication"
Metric: "outage probability", "sum rate", "energy efficiency", "NMSE", "rate-CRB tradeoff"
Venue/date: site:ieeexplore.ieee.org TWC 2024, JSAC special issue, arXiv 2025
```

For Chinese notes, translate the mechanism, not just the nouns. "鲁棒波束成形" may need "robust
beamforming", "imperfect CSI", and "channel uncertainty".

## Source priority

1. IEEE Xplore / publisher page for final metadata.
2. DOI resolver or Crossref for DOI and bibliographic fields.
3. arXiv record for preprints and version dates.
4. Author manuscript / institutional repository when publisher page is inaccessible.
5. Google Scholar-like sources only as discovery aids; verify elsewhere.

## Venue routing

- JSAC: search the selected area/special issue theme and recent special issues.
- TWC: wireless systems, channel realism, deployment/ray tracing/testbed evidence.
- TCOM: closed forms, detection/estimation/coding, information-theoretic or algorithmic depth.
- WCL/CL: concise related letters; check whether the result has already appeared as a short result.

## Screening criteria

Keep a paper if it shares at least one of:

- same problem setting and assumptions;
- same benchmark metric;
- same algorithmic mechanism;
- same analytical expression/performance metric;
- same data/testbed/ray-tracing environment.

Discard or background-only if it shares only buzzwords but not the technical setting.

## Novelty-check discipline

Use safe language:

- "Prior works on X mainly assume Y; this paper considers Z."
- "Different from [n], which optimizes A under B, this work optimizes C under D."
- "In the searched literature, we did not find a study that jointly considers X and Y under Z."

Avoid:

- "first ever" unless the user explicitly wants that risk and the search is broad enough;
- "no work has studied" after a narrow keyword search;
- citing irrelevant work just to inflate coverage.

## Search log

For serious literature work, return a compact log:

```text
Date searched | Source | Query | Hits screened | Included papers | Notes
```

This makes the novelty claim defensible and repeatable.
