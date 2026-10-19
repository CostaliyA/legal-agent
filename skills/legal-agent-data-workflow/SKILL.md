---
name: legal-agent-data-workflow
description: Orchestrate the end-to-end creation, validation, evaluation, and release of source-grounded legal-agent RL tasks; use when building a batch or coordinating task-generation stages.
---

# Legal Agent Data Workflow

Use this as the entry point for a complete legal-agent dataset run. Keep each task traceable from taxonomy choice through public-source evidence, query, rubric, model evaluations, and released package. LAB may inform taxonomy and operation mix, but its task text, rubrics, answers, and source documents must not become task inputs.

## End-to-end sequence

1. Define jurisdiction/time and choose a domain × operation × work scenario × evidence pattern × deliverable. Invoke [legal-taxonomy-design](../legal-taxonomy-design/SKILL.md).
2. Select knowledge points, collect authentic primary materials, preserve provenance, and label material roles. Invoke [legal-source-research](../legal-source-research/SKILL.md).
3. Turn the source bundle into a version-aware evidence graph. Invoke [legal-evidence-graph](../legal-evidence-graph/SKILL.md).
4. Write a natural attorney query and prepare the solver-visible workspace. Invoke [legal-task-authoring](../legal-task-authoring/SKILL.md).
5. Compile an atomic rubric from graph propositions and source spans. Invoke [legal-rubric-engineering](../legal-rubric-engineering/SKILL.md).
6. Prove answerability with neutral hints, strong-model solve, criterion judging, negative controls, failure attribution, and versioned revision. Invoke [legal-hinted-validation](../legal-hinted-validation/SKILL.md).
7. Freeze the candidate and run no-hint target evaluation; report criterion pass rate and task all-pass rate separately. Invoke [legal-nohint-evaluation](../legal-nohint-evaluation/SKILL.md).
8. Audit provenance, leakage, score integrity, and package completeness before release. Invoke [legal-dataset-release-audit](../legal-dataset-release-audit/SKILL.md).

When a gate fails, return to the stage responsible for the defect. Do not revise another layer just to raise scores. A changed query, source set, graph, rubric, hint, or solver setup creates a new version and requires affected evaluations to be rerun.

## Project invariants

- Keep legal systems separate. This project starts with U.S. law; U.K. and EU branches need their own sources, terminology, authority hierarchy, and version handling.
- Use LAB only for category distribution and task style. Exclude LAB-origin documents and do not copy LAB query, rubric, or answer text.
- Reuse approved v3 materials only with source lineage and version/hash recorded.
- Make queries sound like real attorney requests, ordinarily under 50 words. Keep legal details and evidence in the workspace rather than enumerating rubric answers.
- Prefer 30 or more independently supported rubric criteria when justified; do not pad the rubric.
- Separate solver-visible task materials from private graph, hints, rubric, expected answer, and judge information.
- Keep API credentials in the configured secret store/environment. Never include credential values in prompts, shell commands, files, worklogs, reports, manifests, or output packages.
- Preserve original scores and version history. Never remove failed criteria solely to make a task pass.

For taxonomy, source roles, graph model, automated loop, and verification gates, read [references/workflow.md](references/workflow.md). The design source is [../../REPORT.html](../../REPORT.html).
