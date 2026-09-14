# Methodology and provenance correction — 2026-09-14

This addendum corrects the methodology wording in the original v249 evidence
package. It does not change `predictions.json`, `eval_results.json`, any score
file, or the original commit history.

## Corrected result scope

The measured result remains 570/731 on the latest complete local run of the
pinned official evaluator, with a 569/731 repeat using the same prediction
bytes. It is an open-material, adaptive public-set evaluation. It is not a
claim of one-shot held-out generalization or organizer certification.

The prediction file remains bound by SHA-256:

`9541053225b56b9ace8d0738218ec1dec5d37d2409bbf8d93eb537423f0ba98f`

## What the reconstruction corrected

The original and later audits used broad categories such as
`PUBLIC_SOLUTION_RETRIEVAL` and `LEGACY_OR_UNTRACED`. Those were conservative
eligibility-policy labels based largely on route names and trace wording. They
were not a reconstruction of patch acquisition.

The superseding row-level ledger, `provenance-reconstruction-v1.json`, accounts
for all 731 submitted rows:

| Evidence class | Rows |
| --- | ---: |
| Archive-backed legacy trace | 148 |
| Current mechanism trace without temporal disclosure | 106 |
| Current residual/manual trace without temporal disclosure | 88 |
| Content-matched public-temporal repository trace | 371 |
| Public-temporal snapshot-batch lineage with overwritten attempt receipt | 18 |

There are 713 content-matched acquisition traces. The remaining 18 rows have a
known pre-freeze snapshot-batch origin artifact and a disclosed receipt gap.
Public repository history or public tests were used for 389 rows.

## Direct-answer chronology

The exact-answer comparison cohort was generated after the final predictions
were frozen. That cohort classified itself `GOLD_AIDED` and ineligible and was
not substituted into the submission. It cannot have caused the already-frozen
v249 prediction bytes.

The later comparison found that 44 submitted patches exactly equal the
upstream production answer diff. All 44 are already in the disclosed
public-temporal trace class; 34 passed and 10 failed. Exact byte equality is
comparison evidence, not by itself proof of acquisition from a gold field.

The chronology excludes that specific post-freeze comparison cohort. It does
not claim to prove the absence of every conceivable answer-bearing source.

## Adaptive evaluator use

The earlier statement that no task-level grader outcome affected patch choice
was too broad and is withdrawn.

A scan of 269 pre-freeze evaluator result files bound 785 observations to exact
candidate bytes. Seven final rows had a different candidate fail before the
final submitted patch was produced or selected:

| Instance | Final result |
| --- | ---: |
| `instance_NodeBB__NodeBB-76c6e30282906ac664f2c9278fc90999b27b1f48-vd59a5728dfc977f44533186ace531248c2917516` | pass |
| `instance_element-hq__element-web-33299af5c9b7a7ec5a9c31d578d4ec5b18088fb7-vnan` | pass |
| `instance_element-hq__element-web-b007ea81b2ccd001b00f332bee65070aa7fc00f9-vnan` | pass |
| `instance_flipt-io__flipt-b3cd920bbb25e01fdb2dab66a5a913363bc62f6c` | pass |
| `instance_flipt-io__flipt-c1fd7a81ef9f23e742501bfb26d914eb683262aa` | pass |
| `instance_flipt-io__flipt-c8d71ad7ea98d97546f01cce4ccb451dbcf37d3b` | fail |
| `instance_flipt-io__flipt-e2bd19dafa7166c96b082fb2a59eb54b4be0d778` | fail |

This is adaptive evaluator interaction. It is a distinct issue from direct
gold-patch retrieval and is now disclosed rather than being obscured by the
old blanket statement.

## Machine-verifiable correction

- Reconstruction file SHA-256:
  `c192a3ddd14eb0ec4cdf4687b4cc0024a8b8ed02ed66e55a364efe9158981bfc`
- Internal reconstruction root:
  `005f51f80866ab4a2cf0d4c0e4344486801fd74308e01583e1d5cf1932a277d4`
- Scope declared by the ledger: evidence reconstruction only; no organizer
  approval or eligibility decision

Future clean performance claims should come from a new run that freezes the
complete candidate cohort before any official result is read, forbids
same-task revision after measurement, and keeps public-temporal evidence in an
explicit predeclared lane.
