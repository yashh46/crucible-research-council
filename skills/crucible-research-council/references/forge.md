# Forge: bounded improve-and-measure loop

Use this only when the objective can be measured, such as runtime, cost, file size, accuracy, conversion on a fixed test set, or a lint or test score.

## Before the first iteration

Write these down and don't change them mid-loop:

- **Metric and direction**, for example "p95 latency, lower is better".
- **Evaluator**: the exact command or procedure that produces the number.
- **Baseline**: run the evaluator on the untouched version at least twice so you can see the noise.
- **Minimum worthwhile gain**, for example "≥5%, and larger than the noise you observed".
- **Guardrails**: things that must not get worse (correctness tests pass, memory under X, output identical).
- **Scope**: which files or settings may change. Work on a copy or a branch, never the only copy.
- **Budget**: maximum iterations (default 5) and one evaluation held back for the final check.

## Each iteration

1. Pick the most promising candidate from the council's ranking.
2. Make one change. Keep it small enough that you know what caused the result.
3. Run the frozen evaluator.
4. **Keep** the change only if it beats the current best by at least the minimum gain *and* passes every guardrail. Otherwise revert it and log why.
5. Log the iteration: change, number, guardrails, kept or reverted.

## Stop when

- you hit the iteration budget,
- two iterations in a row produce no gain,
- a guardrail can't be satisfied, or
- the target is reached.

Then run the held-back final check on the winning version, and report the raw numbers next to the baseline.

## Tell apart

- **Failed idea**: the test ran and the idea didn't help.
- **Broken test**: the evaluator errored or measured the wrong thing.
- **Noise**: the difference is smaller than the run-to-run variation.

Only a failed idea is evidence against the idea.
