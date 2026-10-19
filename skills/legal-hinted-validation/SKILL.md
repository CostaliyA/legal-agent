---
name: legal-hinted-validation
description: Validate legal-task answerability with a strong solver, neutral hints, criterion judging, negative controls, and versioned failure attribution; use during construction before no-hint evaluation.
---

# Hinted Solvability Validation

Use hints as construction-time scaffolding to test whether the task is answerable from its materials. Hints may explain source navigation and method, but must not disclose expected conclusions, rubric language, or a model answer.

## Validation loop

1. Give a strong solver the natural query, solver-visible workspace, and neutral navigation/methodology hint. Withhold private rubric, graph, and gold answer.
2. Check completion, requested format, citations, unsupported claims, missing materials, ambiguous terms, and time/version handling.
3. Have a judge score each criterion independently against the rubric and relevant evidence spans. Run an empty-answer or other negative control to detect reward leakage.
4. Attribute each failure to one layer: solver capability, task design, rubric quality, or hint quality. Record the evidence.
5. Revise only the supported layer. If the task, materials, rubric, or hint changes, version it and rerun affected solve and judge gates.
6. Require the hinted solve to demonstrate a supported answer path before release evaluation.

Preserve original criteria and results. Low pass rate alone does not show that a criterion is wrong. Keep API credentials in the configured secret store or environment; never write credential values to prompts, logs, or artifacts.

Store hint version, solver/judge model names, output, criterion verdicts, negative-control results, failure attribution, and revision diff. See [the shared workflow reference](../legal-agent-data-workflow/references/workflow.md).
