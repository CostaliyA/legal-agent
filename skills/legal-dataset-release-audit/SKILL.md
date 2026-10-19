---
name: legal-dataset-release-audit
description: Audit provenance, benchmark leakage, score integrity, and package completeness before releasing legal-agent training or evaluation data; use at dataset freeze and export.
---

# Legal Dataset Release Audit

Audit the exact frozen version that will be shared or used for training. Verify source lineage and score history rather than relying on a summary claim.

## Audit checklist

- Confirm jurisdiction, law-as-of date, source lineage, hashes, document roles, and readable materials.
- Confirm no LAB-origin task, rubric, answer, or source document entered the generated task. LAB may inform taxonomy and style distribution only.
- Confirm v3 material reuse is identified and its version/hash is retained.
- Check query style, task/domain/operation tags, source-family duplicates, and taxonomy coverage.
- Check graph integrity, source-span anchors, and task/rubric criterion ID agreement.
- Confirm every score points to the correct solver output and rubric version; distinguish original scores from post-revision scores.
- Recompute pooled criterion rate and task all-pass rate. Handle fails, errors, and incomplete runs consistently.
- Ensure hints, rubrics, graphs, expected answers, trajectories, and solver-visible files are separated for the intended package.
- Scan reports and exported files for API credentials. Include only safe model metadata; never include credential values.
- Produce a manifest with task IDs, versions, source lineage, score counts, hashes, and exclusions.

If a check fails, block release or return the defect to its owning stage. Do not silently edit scores, criteria, or lineage during packaging. Preserve the audit result and exact release manifest. See [the shared workflow reference](../legal-agent-data-workflow/references/workflow.md).
