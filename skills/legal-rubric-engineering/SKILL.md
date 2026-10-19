---
name: legal-rubric-engineering
description: Compile source-grounded, atomic, judgeable criteria from an evidence graph; use when creating or revising legal-task rubrics and evaluation records.
---

# Legal Rubric Engineering

Build the answer space from the evidence graph and requested deliverable, not from an unconstrained model answer. Reward material legal correctness and work-product completeness.

## Criterion design

1. Map each material proposition to the part of the deliverable that depends on it.
2. Write one observable requirement per criterion. State pass conditions, material fail conditions, and acceptable equivalents.
3. Cite the source span, authority/version, and applicable conditions or exceptions.
4. Keep legal/factual correctness separate from style preferences. Do not combine unrelated requirements.
5. Check for duplicate criteria, unsupported expectations, ambiguous standards, answer leakage, and over-weighting of peripheral details.
6. Normally target 30+ criteria when the task genuinely has that many distinct material requirements; do not add items merely to reach a count.

## Review and versioning

Use an independent rubric check for atomization, source support, coverage, and judgeability. Test positive and negative examples, including empty or materially incomplete answers. If a criterion changes, increment the rubric version and re-evaluate against that version. Never delete a criterion only because a solver failed it or because removal raises pass-all.

Output `rubric.json` and a criterion-to-evidence map. Retain the original rubric and scores when revising. See [the shared workflow reference](../legal-agent-data-workflow/references/workflow.md).
