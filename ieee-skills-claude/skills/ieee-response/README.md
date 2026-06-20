# ieee-response

Draft the two letters an IEEE submission needs: the point-by-point response to reviewers and the
cover letter to the editor. For the manuscript edits these letters promise, use
`ieee-writing`/`ieee-polishing`; for reviewer-requested experiments, use `ieee-experiments`.

## What it enforces

- Every comment numbered (R1.1, R1.2, ...) and answered in order — nothing skipped.
- Every "we changed X" anchored to quoted revised text or a section/line reference.
- Cooperative tone; disagreement allowed but evidence-backed and paired with a small text change.
- No fabricated experiments, results, or citations; unfinished work marked `[AUTHOR INPUT NEEDED]`.
- Response letter and revised manuscript say the same thing.

## Structure

```
ieee-response/
├── SKILL.md
├── README.md
└── references/
    ├── response-structure.md   comment IDs, triage/action model, reply templates, tone, traceability
    └── cover-letter.md         cover-letter structure for new + revised submissions, required statements
```

## Output

A point-by-point response letter, a cover letter, and a coverage checklist mapping every comment to
its action and its anchor in the revised manuscript.
