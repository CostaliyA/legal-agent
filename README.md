# Selected 10 Legal Agent Tasks

本目录保存从已生成任务中筛选出的 10 道法律 Agent 任务，以及题目、材料、rubric、证据图谱和评测记录。设计依据与完整案例见 [REPORT.pdf](REPORT.pdf)，可复用的分阶段流程见 [skills/](skills/README.md)。deepseek-flash的正确率为1/10。

## 核心设计目标

围绕真实律所工作，构造“**可解、可证、可评分，但目标模型在 no-hint 下不一定能一次做对**”的训练任务。训练价值来自可学习的失败：任务要处在目标模型能力边界附近，不能简单到无训练价值，也不能因材料缺失或 rubric 不可判而变成噪声。

难度来自跨文件、跨权威、跨主体和跨时间的依赖，例如区分法院 holding 与当事人主张、对齐拟议规则与最终规则、核对后续文件是否改变法律状态。增加页数或拆分文件本身不构成有效难度。图谱把来源、证据 span、事实/规则命题、知识点与 rubric 连起来，让答案可追溯、失败可定位。

LAB benchmark 只用于了解任务分布和真实工作表达风格；**LAB 原始任务、rubric、答案和材料不作为新题输入**。本批按记录使用 v3 来源材料或独立网页来源，并保留来源 lineage。

## 造题流程

1. **Taxonomy 定位：** 按法域与时间、法律 domain、operation、律所场景、证据依赖模式和交付物确定题目槽位；参考 LAB 分布分配覆盖，不复制原题。
2. **知识点与真实材料：** 先确定要测试的规则、holding、要件、例外、程序状态和关键事实，再从权威网站或真实案件记录收集材料，记录 URL、日期、版本、hash 和页码/段落。
3. **材料角色与证据图谱：** 标记 decisive、corroborating、context、hard negative、irrelevant 或 mixed；把 `DocumentVersion → EvidenceSpan → EvaluableProposition → KnowledgePoint` 连通，保留权威层级、时间版本、条件和例外。
4. **编写 query 与 rubric：** 用自然律师交办口吻写简短 query（通常少于 50 词），把事实留在 workspace；由证据图谱生成原子化 pass/fail rubric，每条要求可观察、可定位、对交付物有实质影响。
5. **Hinted solvability 验证与修订：** 强模型可以使用中性 source-navigation / methodology hint 完成题目；judge 逐条打分并做空答等负例控制。按 solver、task、rubric、hint 四类原因定位失败，只修正对应层并对新版本重跑。
6. **No-hint release 评测：** 冻结 query、材料、图谱和 rubric 后，solver 只看 query 与 workspace；用 DeepSeek Flash 求解和评测，保存逐条结果，并分别报告 criterion pass rate 与 task all-pass rate。

失败分数不能作为删除 rubric 的理由。改变题目或 rubric 后要保留旧版及旧分数，并对新版本重新评测。各阶段的专用 Skill 与端到端入口见 [skills/README.md](skills/README.md)。

## DeepSeek Flash 评测结果

本批共 **10 道题、337 条 criterion**：通过 **297/337**。逐题 criterion 通过率的**算术平均为 88.68%**；按所有 rubric 项合并计算的**pooled 通过率为 88.13%**。整题所有 criterion 全通过的有 **1/10 道，task all-pass rate 为 10%**。两个通过率口径不同，因此同时报告。

| ID | 任务 | Operation | Criterion 通过 | 逐题通过率 | 整题全通过 |
|---|---|---|---:|---:|:---:|
| B02-svb-assumption | Extract SVB transfer and assumption terms | extract | 34/34 | 100.00% | 是 |
| B01-microsoft-activision | Identify Activision closing issues | identify | 30/36 | 83.33% | 否 |
| B03-tesla-conversion | Compare Tesla conversion rights | compare | 30/32 | 93.75% | 否 |
| B04-purdue-release | Draft Purdue creditor update | draft | 31/32 | 96.88% | 否 |
| B05-warhol-license | Draft Warhol licensing clearance note | draft | 29/32 | 90.63% | 否 |
| B06-private-fund-rules | Review private-fund rule tracker | review | 30/32 | 93.75% | 否 |
| B07-h1b-modernization | Draft H-1B filing checklist | draft | 34/36 | 94.44% | 否 |
| B09-moore-attribution | Draft Moore refund advice letter | draft | 30/32 | 93.75% | 否 |
| B10-great-lakes-policy | Identify Great Lakes coverage open items | identify | 26/32 | 81.25% | 否 |
| H-FUSION-01 | Telehealth Ad-Tech Data Sharing: HBNR Notification and FTC Section 5 Response Plan | draft | 23/39 | 58.97% | 否 |



## 数据与 Skill 目录

- `B*/`、`H-FUSION-01/`：题目、solver 可见材料、private rubric/图谱与逐题评测资料。
- [skills/README.md](skills/README.md)：一个总 workflow Skill 与八个阶段 Skill 的索引。
- [REPORT.pdf](REPORT.pdf)：完整设计报告、taxonomy 说明、证据图示、题目分析与下一轮改进方向。
- [manifest.json](manifest.json)：本批选题与评测汇总。
