# Synthesa SDLC — SWE-bench Pro public submission

This package contains a complete 731-instance prediction set and the output of a
complete local run of the official SWE-bench Pro evaluator.

## Result

- Latest complete official-method run: **570 / 731 resolved (77.9754%)**
- Candidate success: **570 / 731 (77.9754%)**
- Independent repeat result with the same frozen predictions: **569 / 731
  (77.8386%)**
- Observed repeat range: **569–570 resolved**

The one-result variation occurred in the holdout partition. No task-level grader
outcome was used to alter a patch or choose between patches.

## Method

- Dataset: SWE-bench Pro public test set, 731 instances
- Official harness: `scaleapi/SWE-bench_Pro-os`
- Harness commit: `ca10a60a5fcae51e6948ffe1485d4153d421e6c5`
- Evaluator SHA-256:
  `bb5d4c5486be296e464e695df3747064aaa3bb197394bc6d39980634afec2034`
- Execution: local Docker using the official per-instance images
- Patch producer: custom deterministic/model-free Synthesa SDLC pipeline
- Pass@1: one frozen patch per instance
- Hidden grader feedback to synthesis: none
- Task-level hidden-result selection: none

`predictions.json` is byte-identical to the frozen submitted prediction file.
`eval_results.json` merges the three disjoint official partition outputs and is
the file intended for the leaderboard submission form.

## Provenance disclosure

The content-matched audit classifies the 731 submitted rows as follows:

- 188 `PUBLIC_TASK_AND_BASE_DERIVED`
- 349 `PUBLIC_SOLUTION_RETRIEVAL`
- 194 `LEGACY_OR_UNTRACED`

The second category used public repository solution history. The third category
predates the current trace format and therefore lacks a content-matched current
trace. These categories are disclosed in full in `provenance-audit.json`; this
package does not claim organizer approval for them. The official repository says
patches may be generated with a harness of choice, while the benchmark's stated
goal is generalization rather than solution recall, so final leaderboard
eligibility is left to the benchmark organizers with this disclosure attached.

## Files

- `predictions.json`: all 731 submitted patches
- `eval_results.json`: all 731 Boolean evaluator outcomes
- `manifest.json`: roots, counts, evaluator pins, and proposed form values
- `provenance-audit.json`: content-matched provenance audit
- `*-grade-spec.json` and `*-grade-execution.json`: sealed official evaluator
  commands and successful execution receipts
- `*-score.json`: rooted per-partition summaries
- `prediction-freeze.json` and `prediction-freeze-verification.json`: prediction
  preregistration evidence
- `prior-score-569.json`: the independent 569-result repeat

There are no LLM chat trajectories to claim for this deterministic/model-free
pipeline. The submission form's optional trajectories field can be left blank.
