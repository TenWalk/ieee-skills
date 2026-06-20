# Metadata Verification and BibTeX

## Required metadata by type

Journal article:

- authors in order;
- title exactly as published;
- journal abbreviation target;
- year, volume, issue, page range or article number;
- DOI when available.

Conference paper:

- authors, title, conference name, location if available, year, pages, DOI if available.

Preprint:

- authors, title, arXiv ID, year, version if relevant, and whether it is also published.

Dataset/software:

- creators, title, repository, year, DOI or URL, version.

## Verification rules

- Treat DOI, volume, issue, pages, and article number as factual fields. Do not guess.
- If title capitalization differs, preserve the source title in BibTeX and let IEEEtran style
  format it where appropriate.
- If a preprint later has a journal version, cite the journal version unless the preprint contains
  essential different content.
- If a DOI lookup and publisher page disagree, prefer the publisher page and flag the discrepancy.

## BibTeX skeletons

Journal:

```bibtex
@article{key,
  author  = {Author, A. B. and Author, C. D.},
  title   = {Title},
  journal = {IEEE Trans. Commun.},
  year    = {2026},
  volume  = {[MISSING]},
  number  = {[MISSING]},
  pages   = {[MISSING]},
  doi     = {[MISSING]}
}
```

Conference:

```bibtex
@inproceedings{key,
  author    = {Author, A. B. and Author, C. D.},
  title     = {Title},
  booktitle = {Proc. IEEE ICC},
  year      = {2026},
  pages     = {[MISSING]},
  doi       = {[MISSING]}
}
```

arXiv:

```bibtex
@misc{key,
  author        = {Author, A. B. and Author, C. D.},
  title         = {Title},
  year          = {2026},
  eprint        = {2601.00000},
  archivePrefix = {arXiv},
  primaryClass  = {cs.IT}
}
```

## Citation-key rules

Use stable keys: `surnameYearKeyword`, e.g., `zhang2026risCrb`. Avoid keys based only on title words
that may change between preprint and publication.

## Output verification status

Mark every reference:

```text
VERIFIED: all required metadata checked against publisher/DOI/arXiv
PARTIAL: title/authors/year checked; pages/volume/DOI missing
UNVERIFIED: discovered by search only; do not cite until verified
```

Pass final formatted references to `ieee-citation`.
