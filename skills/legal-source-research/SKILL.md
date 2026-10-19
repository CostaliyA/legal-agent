---
name: legal-source-research
description: Find, freeze, and label authentic legal source documents for benchmark tasks; use when collecting statutes, regulations, opinions, filings, contracts, and realistic distractors.
---

# Legal Source Research

Create a source bundle that is authentic, sufficient to answer the planned task, and independently traceable. Prefer official or primary sources: U.S. Code and eCFR, court opinions and dockets, agency materials, EDGAR filings, executed agreements, and authoritative public repositories for docketed records.

## Source workflow

1. Start from the taxonomy card's knowledge points, jurisdiction, legal issue, and law-as-of date; research primary authority before commentary.
2. Preserve source URL or docket, issuing authority, title, publication/effective date, retrieval date, version, local filename, SHA-256, page count, and extraction method.
3. Distinguish operative sources from summaries and related records. Capture definitions, qualifications, exceptions, and procedural posture.
4. Label each document `decisive`, `corroborating`, `context`, `hard_negative`, `irrelevant`, or `mixed`, with a short reason. Briefs are advocacy; proposals are not final rules; public summaries do not replace executed terms.
5. Add corroborating records and realistic hard negatives only when they test a genuine legal or source-selection distinction.
6. Check readability, version consistency, source-family overlap, and LAB-material exclusion before handoff.

Do not copy LAB-origin documents into a generated task. Approved v3 material reuse is allowed only with recorded lineage and version/hash checks. Reject or quarantine sources with unclear provenance, missing decisive pages, or unresolved version conflicts.

Output `source-provenance.json`, a readable source bundle, and `material-roles.json`. See [the shared workflow reference](../legal-agent-data-workflow/references/workflow.md).
