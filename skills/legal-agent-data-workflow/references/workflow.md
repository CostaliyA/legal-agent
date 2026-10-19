# Production workflow reference

This reference distills the task-generation process documented in the adjacent [REPORT.html](../../../REPORT.html). It describes the reusable process; it does not claim that every stage was run for every selected task.

## Taxonomy coordinates

Choose a task by combining these coordinates:

1. **Jurisdiction and time:** legal system, governing authority, and law-as-of date. Keep U.S., U.K., and EU branches distinct; do not transfer legal rules between systems.
2. **Legal domain:** use the report's LAB-informed domain catalog as a coverage map, then extend it based on actual law-firm work and available primary sources.
3. **Operation:** cover work such as draft, knowledge retrieval, identify, review, compare, extract, redline, analyze, negotiate, and escalate. Preserve long-tail work rather than filling the dataset with only drafting and issue spotting.
4. **Work scenario:** specify who needs the work, what decision or transaction is pending, and what work product will be used.
5. **Evidence pattern:** choose the relationships that make the task meaningful: authority hierarchy, proposal/final distinction, contract/announcement reconciliation, entity alignment, state transition, condition/exception, timeline, or competing advocacy.
6. **Deliverable:** name a realistic artifact such as a memo, checklist, issue register, comparison schedule, client update, or compliance map.

Use LAB material to estimate category distribution and task style only. The generated task must have new query language, new scoring criteria, and independently sourced documents. Do not use LAB documents as task inputs.

## Source and graph construction

For each candidate source, record its issuing authority, URL or docket, title, date, effective date where applicable, version, retrieval date, and hash. Prefer official regulations, statutes, court opinions, filed records, executed agreements, and regulator materials. A source bundle should include enough decisive evidence to answer the task, plus realistic corroborating or peripheral material when it tests relevance judgment.

Classify every document's role. In particular:

- A court opinion controls its holding; party briefs show advocacy.
- A final rule controls over a proposal, subject to later amendments or judicial action.
- An executed contract controls over a simplified public announcement on contract terms.
- A hard negative is relevant-looking material that should not be mistaken for controlling evidence.
- Irrelevant material should be realistic and clearly unrelated to the scored question.

Represent the evidence path as:

`DocumentVersion → EvidenceSpan → EvaluableProposition → KnowledgePoint → Criterion → Deliverable`

Include source page, section, paragraph, or URL anchors; document role; law-as-of; and the applicable conditions or exceptions. Test that removing a decisive source makes at least one material conclusion unsupported. Merely splitting files or increasing page count does not create useful difficulty.

## Query and workspace design

Write the query as a short human attorney request. It should say what to do, for whom or about what, by what time, and in what form. Keep rubric wording and expected conclusions out of the query. Put relevant facts in the source workspace, including facts that create realistic cross-document conflicts or unresolved issues.

Before release, check that:

- The query matches the selected operation and deliverable.
- The necessary law and facts are present in readable materials.
- The source set has a plausible useful/noisy balance.
- The same case or source family is not duplicated merely to inflate the task count.
- The legal system and time cutoff are explicit and internally consistent.

## Rubric compilation

Compile criteria from graph propositions, not from a model answer. Each criterion should test one material assertion or deliverable feature and specify:

- What evidence-backed content earns a pass.
- What material error or omission earns a fail.
- Acceptable equivalent formulations.
- The supporting source span and proposition.
- Which section or decision in the work product depends on it.

Prefer a broad set of independent, material criteria (normally 30 or more when justified by the task). Do not pad with style preferences, duplicate the same fact across criteria, demand facts absent from the workspace, or make one criterion depend on several unrelated conditions. Keep a minimum-materiality test: would this requirement affect legal correctness, advice, implementation, or the client's decision?

## Automated construction loop

Use separate roles or prompts so that privileged construction information does not leak into the target solve:

1. **Taxonomy selection:** allocate a domain/operation/scenario slot.
2. **Research:** collect and freeze authentic sources with provenance.
3. **Source-role labeling:** classify authority and material relevance.
4. **Evidence graph:** extract spans and encode legal/factual relationships.
5. **Task/rubric compilation:** draft query, workspace, deliverable schema, criteria, and rubric mapping.
6. **Hint authoring:** provide neutral navigation and method guidance, not criterion text or conclusions.
7. **Hinted solver validation:** use a strong model to demonstrate that the documents support a complete answer.
8. **Independent judge:** score each criterion from the answer and cited evidence; run empty-answer or other negative controls.
9. **Failure attribution and revision:** classify each failure as solver capability, task design, rubric quality, or hint quality. Change only the diagnosed layer and version the change.
10. **No-hint release evaluation:** run the target model with only the natural query and workspace, then freeze and report the exact version and metrics.

The solver should not receive the private graph, expected answer, or rubric in a no-hint benchmark run. A hinted solve is a construction-time solvability test; it is not the released no-hint score.

## Verification gates

| Gate | Automated checks | Return to |
|---|---|---|
| Source | URLs/files readable, hashes stable, dates and versions known, duplicates checked, LAB source excluded | Research/source bundle |
| Graph | Each proposition has a source span; entity, time, condition, and exception edges connect | Source roles or evidence graph |
| Rubric | Atomicity, observability, no duplicates, evidence anchor valid, no unsupported demands | Rubric compiler |
| Solvability | Hinted answer complete, citations exist, no truncation, no unsupported material claims | Task, source, or hint layer as diagnosed |
| Judge | Per-criterion verdicts, negative control, repeatability, cross-judge when needed | Criterion wording or judge setup |
| Release | Frozen hashes, no-hint solve/judge, taxonomy coverage, family leakage, pooled and all-pass rates | Reject, revise, or release |

For legal authority conflicts the automated system cannot resolve, mark the case blocked or reject it from the release set. Do not infer correctness from a high aggregate score alone.

## Metrics and version integrity

Report at least:

- `criterion_pass_rate = passed criteria / evaluated criteria`.
- `task_all_pass_rate = tasks with every criterion passing / evaluated tasks`.
- Criterion errors separately from fails.
- Model, hint condition, rubric version, solver output hash, and evaluation timestamp.

These metrics answer different questions. A high criterion rate can coexist with a low all-task pass rate. If the query, materials, rubric, graph, hint, solver output, or judge setup changes, create a new version and rerun the affected evaluation. Preserve the prior result and explain any excluded or changed criteria; never relabel a post-hoc score as the original score.

## Secret handling and package layout

Read API credentials from the already configured secret store or environment variable. Never hardcode values, paste them into prompts, include them in shell command text, or write them into manifests, worklogs, reports, or output bundles. Persist model name and non-sensitive response metadata only when needed for reproducibility; redact credentials and avoid storing private reasoning traces in user-facing packages.

Keep the solver-visible task workspace separate from private evaluation assets. A practical package contains task/query/materials, private rubric and evidence graph, final model output, evaluation results, and a manifest. Include solver trajectories only when explicitly requested.
