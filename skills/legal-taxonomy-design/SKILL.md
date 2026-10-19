---
name: legal-taxonomy-design
description: Map legal-agent tasks to jurisdiction, legal domain, operation, work scenario, evidence pattern, and deliverable; use when planning benchmark coverage or allocating a task-generation batch.
---

# Legal Taxonomy Design

Build a coverage map that resembles real law-firm work while keeping task slots distinct. Use the LAB snapshot to estimate category frequencies and task phrasing only; do not use its task materials as seeds.

## Method

1. Set the legal system and law-as-of convention first. This project is U.S.-first; keep U.K. and EU branches separate.
2. Choose a legal domain based on actual firm work and available source material.
3. Choose an operation that changes the work: draft, knowledge retrieval, identify, review, compare, extract, redline, analyze, negotiate, escalate, or a long-tail operation.
4. Bind it to a concrete scenario, client need, decision point, and named deliverable.
5. Specify the evidence pattern: authority hierarchy, multiple-document reconciliation, time/version change, entity alignment, legal condition/exception, procedural posture, or open issue.
6. Allocate batch quotas across domain × operation. Track task count, query length, legal system, document roles, and source family to avoid concentration and duplicate cases.

Every slot must correspond to recognizable attorney work. A legal question with no client context or work product is not a sufficient task slot. Difficulty should come from dependency depth and meaningful state changes, not obscure law or extra pages.

Output a taxonomy card with jurisdiction, law-as-of, domain, operation, scenario, evidence pattern, deliverable, source-family plan, and planned rubric breadth. For details, see [the shared workflow reference](../legal-agent-data-workflow/references/workflow.md) and [the design report](../../REPORT.html).
