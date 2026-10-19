---
name: legal-nohint-evaluation
description: Run and report a frozen legal-agent task evaluation without hints or private answer information; use to measure target-model performance for benchmark release or RL data selection.
---

# No-Hint Legal Task Evaluation

Measure the solver on the natural attorney query and authentic task workspace alone. For this project, use DeepSeek Flash for both solve and judge unless the user specifies otherwise.

## Protocol

1. Freeze and hash the query, task definition, documents, and rubric version.
2. Send the solver only the query and solver-visible workspace. Exclude hints, private graph, rubric, expected answer, and evaluator notes.
3. Save the final answer separately from any trajectory or API metadata. Record model, task version, run time, and a non-sensitive output hash.
4. Judge each criterion independently where feasible, using its evidence anchor. Record pass, fail, or error with a concise reason; do not collapse errors into fails.
5. Run a negative control and check unsupported material claims.
6. Report pooled criterion pass rate and task all-criteria-pass rate, plus per-task counts and evaluation conditions.

If a model call is truncated, fails to stop cleanly, or misses the requested output, mark the run incomplete and do not treat missing judgments as passes. A changed task or rubric requires a fresh evaluation. Keep credentials out of command text, prompts, reports, and output packages.

See [the shared workflow reference](../legal-agent-data-workflow/references/workflow.md) for release gates and metric definitions.
