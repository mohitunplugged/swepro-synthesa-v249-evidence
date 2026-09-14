# Synthesa SDLC — SWE-bench Pro open-material evaluation

This package contains a complete 731-instance prediction set and the output of a
complete local run of the official SWE-bench Pro evaluator.

## What this evidence legitimately demonstrates

The principal product evidence in this package is operational, not a
leaderboard rank. It demonstrates that Synthesa SDLC can run a large software
change campaign through a deterministic, model-free control path; freeze one
final patch for every task; execute a pinned evaluator; and retain enough
machine-readable evidence to reproduce the measurement and later audit and
correct the campaign's methodology.

This matters independently of who authors a candidate patch. A human engineer,
an AI coding agent, or a deterministic mechanism can supply work to the same
residual, verification, provenance, and replay controls. This package directly
exercises the deterministic/model-free path. It does **not** measure an AI
uplift, a human-productivity uplift, or customer return on investment; those
claims require a separate controlled comparison.

The result is therefore evidence for these narrower capabilities:

- large-campaign orchestration with a frozen final output set;
- reproducible execution against a content-pinned evaluation environment;
- row-level provenance and explicit disclosure of missing receipts;
- separation of patch production from independent verification; and
- auditable correction without deleting or rewriting the original record.

Future customer-impact evidence should compare the same unseen tasks with and
without Synthesa while holding the human team or AI model, tools, budget, and
grader constant. Until that study is complete, this repository makes no causal
claim that Synthesa improves completion rate, engineering time, quality, or
cost.

## Result

- Latest complete official-method run: **570 / 731 resolved (77.9754%)**
- Candidate success: **570 / 731 (77.9754%)**
- Independent repeat result with the same frozen predictions: **569 / 731
  (77.8386%)**
- Observed repeat range: **569–570 resolved**

The one-result variation occurred in the holdout partition. This is a frozen
historical result from an adaptive public-set campaign, not a one-shot held-out
measurement. A 2026-09-14 reconstruction found seven task IDs where a different
candidate failed the local official grader before the final patch was produced
or selected. See [CORRECTION_2026-09-14.md](CORRECTION_2026-09-14.md).

## Method

- Dataset: SWE-bench Pro public test set, 731 instances
- Official harness: `scaleapi/SWE-bench_Pro-os`
- Harness commit: `ca10a60a5fcae51e6948ffe1485d4153d421e6c5`
- Evaluator SHA-256:
  `bb5d4c5486be296e464e695df3747064aaa3bb197394bc6d39980634afec2034`
- Execution: local Docker using the official per-instance images
- Patch producer: custom deterministic/model-free Synthesa SDLC pipeline
- Final evaluation input: one frozen patch per instance
- Campaign construction: adaptive local official-evaluator use
- Same-task post-failure replacement observed: 7 instances

`predictions.json` is byte-identical to the frozen prediction file.
`eval_results.json` merges the three disjoint official partition outputs.

## Evaluation classification

This is an **open-material, adaptive evaluation** of a deterministic
patch-production pipeline, scored with the official evaluator. Public task
materials and public repository history/tests were used during construction.
Accordingly, this result is not presented as a clean-room, unseen-task,
contamination-resistant, static pass@1, or organizer-approved leaderboard
result.

The older `provenance-audit.json` is retained as historical evidence but its
`PUBLIC_SOLUTION_RETRIEVAL` label was a post-hoc policy heuristic, not an
acquisition reconstruction. The superseding `provenance-reconstruction-v1.json`
accounts for every submitted row:

- 148 archive-backed legacy traces
- 106 current mechanism traces without temporal disclosure
- 88 current residual/manual traces without temporal disclosure
- 371 content-matched public-temporal repository traces
- 18 public-temporal snapshot-batch lineages whose earlier attempt receipts
  were overwritten by later campaign runs

A direct exact-answer comparison cohort was generated after the prediction
bytes were frozen, marked `GOLD_AIDED`, and kept out of the submission. It
therefore could not have produced the frozen prediction file. The reconstruction
records 44 exact upstream-production-diff matches as an orthogonal comparison;
byte equality alone does not establish how a patch was acquired.

## Files

- `predictions.json`: all 731 submitted patches
- `eval_results.json`: all 731 Boolean evaluator outcomes
- `manifest.json`: roots, counts, evaluator pins, and recorded form values
- `provenance-audit.json`: retained historical policy audit; superseded for
  acquisition-provenance claims
- `provenance-reconstruction-v1.json`: current 731-row evidence reconstruction
- `CORRECTION_2026-09-14.md`: correction, limitations, and responsible claim
- `*-grade-spec.json` and `*-grade-execution.json`: sealed official evaluator
  commands and successful execution receipts
- `*-score.json`: rooted per-partition summaries
- `prediction-freeze.json` and `prediction-freeze-verification.json`: prediction
  preregistration evidence
- `prior-score-569.json`: the independent 569-result repeat

There are no LLM chat trajectories for this deterministic/model-free pipeline.
