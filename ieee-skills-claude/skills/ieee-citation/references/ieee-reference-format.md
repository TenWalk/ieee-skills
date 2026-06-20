# IEEE Reference Format — Entry Templates

Numbered list, in order of first citation. Author names: initials then surname. Up to six
authors; for more, give the first then "*et al.*". Journal/conference titles abbreviated.
Always confirm fields against the source; mark anything uncertain `[MISSING: ...]` — never invent.

> Journals vary on whether to include DOI, month, and issue number. These templates show the full
> form; trim to match the target journal's Author Kit.

## Journal article

```
[n] A. B. Author, C. D. Author, and E. F. Author, "Title of the paper," Abbrev. Journal Title,
    vol. X, no. Y, pp. ppp–ppp, Mon. YYYY, doi: 10.XXXX/XXXXXX.
```

Example:

```
[1] K. He, X. Zhang, S. Ren, and J. Sun, "Deep residual learning for image recognition,"
    IEEE Trans. Pattern Anal. Mach. Intell., vol. 42, no. 8, pp. 1234–1245, Aug. 2020,
    doi: 10.1109/TPAMI.2019.XXXXXXX.
```

## Conference paper

```
[n] A. B. Author and C. D. Author, "Title of the paper," in Proc. Abbrev. Conf. Name, City,
    Country, YYYY, pp. ppp–ppp.
```

Example:

```
[2] J. Devlin, M.-W. Chang, K. Lee, and K. Toutanova, "BERT: Pre-training of deep bidirectional
    transformers for language understanding," in Proc. NAACL-HLT, Minneapolis, MN, USA, 2019,
    pp. 4171–4186.
```

## Book

```
[n] A. B. Author, Title of Book, Xth ed. City, Country: Publisher, YYYY.
```

## Book chapter

```
[n] A. B. Author, "Title of chapter," in Title of Book, Xth ed., E. F. Editor, Ed. City,
    Country: Publisher, YYYY, pp. ppp–ppp.
```

## Thesis / dissertation

```
[n] A. B. Author, "Title of thesis," Ph.D. dissertation, Dept. Abbrev., Univ. Name, City,
    Country, YYYY.
```

(Use "M.S. thesis" for a master's thesis.)

## Online / website

```
[n] A. B. Author. "Title of page." Site Name. URL (accessed Mon. DD, YYYY).
```

## Standard

```
[n] Title of Standard, Standard Number, YYYY.
```

Example: `[3] IEEE Standard for Floating-Point Arithmetic, IEEE Std 754-2019, 2019.`

## Patent

```
[n] A. B. Inventor, "Title of patent," Country Patent Number, Mon. DD, YYYY.
```

## Preprint (arXiv)

```
[n] A. B. Author, "Title of the paper," YYYY, arXiv:XXXX.XXXXX.
```

## Dataset / software (DataCite-style, if the journal accepts it)

```
[n] A. B. Author, "Title of dataset," Repository, YYYY, doi: 10.XXXX/XXXXXX.
```

## In-text citation rules

- On-line square brackets, not superscript: "the approach in [5]".
- Multiple: "[1], [3], [5]"; consecutive range: "[2]–[6]".
- Cite in ascending order at each location: write "[2], [7]", not "[7], [2]".
- Author-prominent: "Smith *et al.* [12] showed..."; non-prominent: "...is well established [12]."
- Avoid the bracket-as-noun form ("in [12], they..."); prefer "the method of [12]".
- Every entry in the list must be cited at least once; every `[n]` in the text must resolve.

## Journal-title abbreviation (common IEEE)

Use IEEE's abbreviations; a few frequent ones:

| Full | Abbreviation |
|---|---|
| IEEE Transactions on Pattern Analysis and Machine Intelligence | IEEE Trans. Pattern Anal. Mach. Intell. |
| IEEE Transactions on Image Processing | IEEE Trans. Image Process. |
| IEEE Transactions on Signal Processing | IEEE Trans. Signal Process. |
| IEEE Transactions on Communications | IEEE Trans. Commun. |
| IEEE Transactions on Neural Networks and Learning Systems | IEEE Trans. Neural Netw. Learn. Syst. |
| IEEE Transactions on Industrial Electronics | IEEE Trans. Ind. Electron. |
| IEEE Journal on Selected Areas in Communications | IEEE J. Sel. Areas Commun. |
| IEEE Access | IEEE Access |
| Proceedings of the IEEE | Proc. IEEE |

If an abbreviation is unknown, flag it (`[CHECK ABBREV: ...]`) rather than guessing — IEEEtran's
BibTeX style can also abbreviate automatically (see `ieeetran-latex.md`).
