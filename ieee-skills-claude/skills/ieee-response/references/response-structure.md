# Point-by-Point Response Structure

## The letter's skeleton

```
[Date]
Manuscript ID: [####]
Title: [...]

Dear Editor [and Reviewers],

We thank the editor and reviewers for their careful reading and constructive comments. We have
revised the manuscript accordingly; the main changes are: (1) ..., (2) ..., (3) .... Below we
respond to each comment point by point. Reviewer comments are in italics; our responses follow in
plain text, and changes to the manuscript are quoted in "quotation marks" with their location.

--- Reviewer 1 ---
R1.1 [quoted comment]
     Response: ...
R1.2 [quoted comment]
     Response: ...

--- Reviewer 2 ---
...

We believe these revisions have substantially improved the manuscript and hope it is now suitable
for publication.

Sincerely,
[Authors]
```

## Comment IDs — one concern per ID

Split each review into atomic points. A reviewer paragraph that raises three issues becomes R2.1,
R2.2, R2.3. This makes coverage checkable and lets you reference one reply from another
("as addressed in R1.2"). Never merge two distinct concerns into one reply to save space — the
reviewer will notice the one you dodged.

## The reply shape: thank → change → location

Every reply has the same three beats:

1. **Acknowledge** the point in one clause (agreement, thanks, or a brief restatement showing you
   understood it).
2. **State what you did** — the concrete action, not an intention.
3. **Point to it** — quote the new/edited text and give its location ("Section III-B, para 2"),
   or name the new table/figure.

> *R2.3: The paper does not report how the gain varies across channel realizations.*
> Response: We agree this is important. We reran all main simulations over 1e4 independent channel
> realizations and now report the averaged curves with confidence bounds in Fig. 4. The text reads:
> "Averaged over 1e4 realizations, the proposed scheme achieves a 3.2 dB SNR gain over the strongest
> benchmark scheme at a BER of 1e-4." (Section V-A, Fig. 4.)

## Action patterns

### ACCEPT_TEXT — reviewer is right

Make the change, quote it. Short and clean; do not over-thank or over-explain. The quoted edit
is the proof.

### SOFTEN_CLAIM — overclaim flagged

Narrow the wording and show the before/after intent.

> Response: We have tempered this claim. "Our method solves X" now reads "Our method improves X
> under the assumptions in Section III." (Abstract; Section I, contribution C2.)

### ADD_EVIDENCE — needs an experiment

If run: describe it and point to the new table/figure. If not yet run: be honest.

> Response: [AUTHOR INPUT NEEDED] This requires a new simulation under imperfect CSI, which we will
> add in revision. Planned: same setup as Fig. 3, reporting sum rate vs. SNR under a bounded CSI
> error model.

Do not claim a result you do not have. A marked open item is recoverable; a fabricated number is
a retraction risk.

### CLARIFY — the reviewer misread

A misunderstanding usually means the text misled. Fix the text first, then explain — do not blame
the reviewer for "not reading carefully."

> Response: We apologize for the lack of clarity. We have rewritten the relevant passage to make
> the assumption explicit: "...". To clarify the original point: ... (Section III-A.)

### DISAGREE — the reviewer is mistaken

Allowed, but be respectful, lead with evidence, and still make a small edit so the reviewer sees
their reading was anticipated.

> Response: We respectfully see this differently. [Evidence: result/citation/derivation.]
> Nonetheless, since the point was not obvious, we have added a sentence making our reasoning
> explicit. (Section V, para 1.)

Never: "the reviewer is wrong", "as any expert knows", sarcasm, or silence.

### DEFER — out of scope

Acknowledge, justify the boundary briefly, and record it as a limitation/future work so it is
visible in the paper, not just the letter.

> Response: This is a valuable direction. It falls outside the present scope (single-cell
> setting); we now note it explicitly in Limitations (Section VI) as future work.

## Traceability and consistency

- Keep a coverage table while drafting: `Comment ID → action → manuscript anchor → status`. Submit
  nothing until every row has an anchor or an open-item flag.
- If you use a colored-diff or "changes highlighted" PDF, say so in the opening paragraph and make
  the letter's quotes match the highlights exactly.
- Cross-check at the end: every "we added/changed/now report ..." in the letter must correspond to
  real text in the revised manuscript. Mismatches are the fastest way to lose a reviewer's trust.

## Tone rules

- Open and close with genuine thanks; reviewers are unpaid.
- "We" throughout; address reviewers in the third person inside the letter body.
- Calm and specific beats defensive and vague. Short replies for easy points; reserve length for
  the hard ones.
- Match the reviewer's register: a technical objection gets a technical answer, not a paragraph of
  gratitude.

## Bilingual author note

Triage and reason about comments in Chinese if that is faster, but the submitted letter is in the
same (US) English register as the paper — see ieee-polishing. Keep a Chinese gloss of each reply
for your own records so you can verify the English says what you mean; do not submit the gloss.
