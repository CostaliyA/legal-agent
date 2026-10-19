---
name: legal-evidence-graph
description: Build a version-aware evidence graph linking legal propositions to primary source spans and task criteria; use when a task depends on multiple documents, actors, dates, rules, or exceptions.
---

# Legal Evidence Graph

Turn the frozen source bundle into a traceable representation of what the task asks the solver to determine. Keep the graph private unless the task explicitly tests graph use.

## Graph construction

1. Extract legal rules, holdings, procedural posture, factual propositions, dates, actors, conditions, exceptions, and unresolved issues.
2. Create a `DocumentVersion` node for each source, including role, authority, effective date, jurisdiction, and hash.
3. Create `EvidenceSpan` nodes with page/section/paragraph or URL anchors and faithful excerpts or descriptions.
4. Create atomic `EvaluableProposition` nodes stating one answerable claim, its support, limitation, and contradiction/failure condition.
5. Group propositions under `KnowledgePoint` nodes and connect them to expected deliverable sections or decisions.
6. Represent relationships such as `SUPPORTED_BY`, `CONTRADICTED_BY`, `APPLIES_IF`, `SUPERSEDES`, `ASSERTED_BY`, `PART_OF`, and cross-document entity alignment where useful.

Use the path `DocumentVersion → EvidenceSpan → EvaluableProposition → KnowledgePoint → Criterion → Deliverable`. Every criterion must trace to a valid span, and every span must point to the correct source version. Distinguish advocacy from authority and proposed, operative, amended, vacated, and historical law.

## Graph gates

- Check referential integrity and dangling edges.
- Check that each proposition has evidence and that relevant limitations are represented.
- Run a decisive-source ablation: remove one decisive source and confirm that a material conclusion becomes unsupported.
- Include only relationships that change reasoning or evaluation.

Output `evidence-graph.json` and/or `knowledge-graph.json` with source hashes and graph version. See [the shared workflow reference](../legal-agent-data-workflow/references/workflow.md).
