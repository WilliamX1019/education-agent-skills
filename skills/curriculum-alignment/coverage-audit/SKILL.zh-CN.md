---
name: coverage-audit
description: 接收一份课程框架与一份法定或认证要求清单；生成覆盖对照表、缺口摘要及 CSV，展示框架中哪些内容覆盖了每项要求以及缺口所在。
disable-model-invocation: false
user-invocable: true
effort: medium
skill_id: curriculum-alignment/coverage-audit
skill_name: 课程覆盖度审计
domain: curriculum-alignment
version: "1.0"
evidence_strength: moderate
evidence_sources:
  - "Webb, N. L. (1997) — Criteria for Alignment of Expectations and Assessments in Mathematics and Science Education, CCSSO Research Monograph No. 6: canonical alignment framework defining coverage dimensions (categorical concurrence, depth-of-knowledge, range, balance) used in this skill's classification of match strength."
  - "Porter, A. C. et al. (2002) — Measuring the content of instruction: Uses in research and practice, Educational Researcher 31(7), 3–14: curriculum mapping methodology for comparing intended vs enacted curricula across frameworks — the basis for this skill's row-per-requirement approach."
input_schema:
  required:
    - field: framework
      type: string
      description: 被审计的课程框架。支持 Developmental Band Translator 输出的带学段标签 JSON，或已标明能力与学习目标的纯 Markdown/文本。
    - field: requirements
      type: string
      description: 法定或认证要求清单。支持 Markdown、CSV 或纯文本。每项要求应可通过编号或标签识别。
  optional:
    - field: framework_name
      type: string
      description: 被审计框架的可读名称。
    - field: requirements_source
      type: string
      description: 法定或认证机构名称。
    - field: band_filter
      type: string
      description: 将审计范围限定在特定学段。
output_schema:
  type: object
  fields:
    - field: coverage_table
      type: string
      description: Markdown 表格——列为 Requirement ID、Requirement text、Covered by（框架学习目标或能力）、Band(s)、Evidence strength（direct/partial/indirect/none）、Notes。
    - field: coverage_csv
      type: string
      description: 与 coverage_table 相同数据的扁平 CSV 格式，供 Google Sheets 使用。
    - field: gap_summary
      type: string
      description: 散文段落，总结无覆盖或仅间接覆盖的要求。
    - field: coverage_statistics
      type: object
      description: 计数统计——总要求数、直接覆盖、部分覆盖、未覆盖。
chains_well_with:
  - curriculum-crosswalk
  - developmental-band-translator
  - scope-and-sequence-designer
teacher_time: 15 分钟
tags:
  - coverage-audit
  - accreditation
  - statutory-compliance
  - curriculum-alignment
  - gap-analysis
---

# 本技能的作用

本技能将一份课程框架对照一份法定或认证要求清单进行审计，并生成结构化的覆盖对照表，展示框架中哪些内容回应了每项要求以及证据强度如何。它保持框架中立：被审计的框架可以是任何学校的课程、任何教学大纲或任何能力框架。要求清单可以是法定指令、认证标准或学校需要满足的任何外部核查清单。两者均不预设为 REAL School、英国或其他任何特定语境。

本技能将每项要求的匹配划分为四个等级：直接覆盖（direct，框架明确回应了该要求）、部分覆盖（partial，框架回应了相关内容但非该具体要求）、间接覆盖（indirect，存在边缘相关内容）或无覆盖（none，框架内容完全未触及该要求）。这一四级量表遵循 Webb（1997）的“类别一致性（categorical concurrence）”逻辑，并将其操作化在要求层面而非试题层面。本技能对“覆盖”在此语境下的含义保持透明：即框架文档中的主题呈现（topical presence）。框架条目触及某要求主题，并不必然意味着该要求在课堂上被充分教授、评估或以预期认知深度实施。

本技能产出三项成果：供专业学习共同体（PLC）或认证准备使用的 Markdown 覆盖表、便于电子表格筛选的对应 CSV，以及用于叙事报告的散文体缺口摘要。`coverage_statistics` 对象则提供便于快速扫视的汇总计数。这些产出是人类专业判断的脚手架——旨在减少课程协调员查找证据的时间，而非取代确认证据所需的专业判断。

# 实证基础

**Webb（1997）**——经典的四维度对齐框架将“类别一致性”确立为基础覆盖维度：框架与要求清单究竟是否涉及相同主题？本技能采用 Webb 的逻辑对匹配强度进行分类，止步于类别一致性与范围。知识深度对齐——框架是否以要求的认知深度回应某一要求——明确不在本技能范围内，并在“已知局限”中标明为人类判断任务。

**Porter 等人（2002）**——《已实施课程调查（Surveys of Enacted Curriculum）》方法论确立了本技能覆盖表中“每项要求占一行”的做法：每项要求拥有独立一行，将框架内容映射到要求上，而非反过来。这确保了没有框架覆盖的要求（缺口行）与强覆盖的要求同样醒目，避免输出自然偏向于围绕框架**已涵盖**的内容、而非要求清单**所索要**的内容来组织。

# 输入规范

**必填输入：**

- **`framework`**——被审计的课程框架。支持 Developmental Band Translator 输出的带学段标签 JSON（用于学段级筛选），或包含能力与学习目标的纯 Markdown/文本。若带学段标签，本技能可通过 `band_filter` 将审计限定于特定学段。若为纯文本，则不区分学段审计全部框架内容。
- **`requirements`**——法定或认证要求清单。支持 Markdown、CSV 或纯文本。每项要求应带有标识符（编号、代码或标签）用于 Requirement ID 列。若缺少标识符，本技能会分配稳定的顺序 ID（R001, R002, …）并在引言中注明。

**可选输入：**

- **`framework_name`**——用于输出标题的可读标签。
- **`requirements_source`**——法定或认证机构名称，用于输出标题。
- **`band_filter`**——将审计限定于特定学段（例如 `"D,E"`）。仅在 `framework` 为带学段标签 JSON 时相关。若省略，则检索全部框架内容。

**必填输入示例：** REAL School Budapest 对照英国 RSHE 法定要求（2025 年 7 月）审计其幸福感课程：`framework` = REAL School Wellbeing Framework（带学段标签或 Markdown）；`requirements` = 英国教育部（DfE）法定 RSHE 要求清单；`framework_name = "REAL School Budapest Wellbeing Framework"`；`requirements_source = "UK DfE Statutory RSHE, July 2025"`。输出将把每一条 RSHE 法定条目列为一行，并将匹配的 REAL 框架内容（如有）映射到对应行，按证据强度分级。

# 提示词（Prompt）

You are a curriculum coverage-audit assistant. Your task is to audit a curriculum framework against a requirement list and produce a structured coverage table, a gap summary, and coverage statistics.

## Procedure

1. **Read the requirements list.** For each requirement, confirm it has a stable identifier. If identifiers are absent, assign sequential IDs (R001, R002, …) and note in your output preamble. Record every requirement before searching the framework — do not skip any.
2. **Read the framework.** If band-tagged, note the band labels and apply `band_filter` if supplied. If plain text, treat all content as a single pool.
3. **For each requirement, search the framework** for content that addresses it:
   - **Direct** — the framework explicitly and substantively addresses the requirement. The framework item's topic, framing, and intent match the requirement's topic, framing, and intent closely. A teacher could point to this item as evidence of coverage without qualification.
   - **Partial** — the framework addresses related content but not the specific requirement. The topic overlaps but the framing, depth, or scope differs. A teacher could point to this item as partial evidence but would need to add context.
   - **Indirect** — the framework contains content tangentially related to the requirement. The topic is adjacent but not the same. Evidence is inferential, not direct.
   - **None** — no framework content touches the requirement. This is a gap row.
4. **Produce `coverage_table`** — one row per requirement, with columns: Requirement ID | Requirement text | Covered by | Band(s) | Evidence strength | Notes.
5. **Produce `coverage_csv`** — the same data as coverage_table in flat CSV format. Column names exactly: requirement_id, requirement_text, covered_by, bands, evidence_strength, notes.
6. **Write `gap_summary`** — one prose paragraph summarising the requirements in the none and indirect rows. Group related gaps thematically if possible. State total count of none and indirect rows.
7. **Produce `coverage_statistics`** — counts: total_requirements, directly_covered, partially_covered, not_covered (none rows only). Include indirectly_covered as a separate count.

## Classification discipline

When classifying evidence strength, err toward conservatism. A match that requires the auditor to make an inferential leap beyond what the framework text directly states should be classified as partial or indirect, not direct. The skill's job is to give an honest starting point for professional review, not to maximise the apparent coverage score. A framework that looks fully covered by aggressive classification is not useful to an accreditor or a curriculum coordinator trying to find real gaps.

## Inputs

- `framework`: {{framework}}
- `requirements`: {{requirements}}
- `framework_name`: {{framework_name}}
- `requirements_source`: {{requirements_source}}
- `band_filter`: {{band_filter}}

Produce a JSON object with fields: coverage_table (markdown string), coverage_csv (CSV string), gap_summary (string), coverage_statistics (object).

# 示例输出

**情景：** REAL School Budapest 幸福感框架对照英国 RSHE 法定要求审计，`band_filter = "D,E"`。

**`coverage_table`**（展示 8 行）：

| Req ID | 要求文本 | 覆盖条目 | 学段 | 证据强度 | 备注 |
|---|---|---|---|---|---|
| RSHE-D-01 | "the characteristics of positive and healthy friendships… respect, honesty, trust, loyalty, kindness, generosity, boundaries, privacy, consent and the management of conflict" | "Students can identify healthy and unhealthy relationship patterns and articulate why each is so." | D | direct | 主题与意图高度匹配。 |
| RSHE-D-02 | "the concepts of, and laws relating to, sexual consent, sexual exploitation, abuse, grooming, coercion, harassment" | "Students understand consent as an ongoing, reversible, affirmative process." | D | partial | 框架从发展视角探讨同意；法定要求包含法律框架与更广泛的伤害类别，框架中未显性体现。 |
| RSHE-D-03 | "the facts about the full range of contraceptive choices, efficacy and options available" | — | — | none | 在 D 或 E 学段无框架内容涉及避孕。 |
| RSHE-D-04 | "the impact of pornography on attitudes to sex, relationships and gender" | — | — | none | 框架中无直接对应条目。E 学段数字幸福感内容触及媒体影响，但未具体涉及色情内容。 |
| RSHE-D-05 | "how the different sexually transmitted infections (STIs), including HIV/AIDs, are transmitted, how risk can be reduced" | — | — | none | 在 D 或 E 学段未识别到性传播感染（STI）相关内容。 |
| RSHE-E-01 | "how to seek, and recognise, support for mental health and wellbeing" | "Students can identify when to seek help for themselves or a peer and know at least two trusted routes." | D | partial | 框架在 D 学段涉及此内容；法定要求置于中学末期。E 学段无对应条目——属于错误学段的部分覆盖。 |
| RSHE-E-02 | "the impact of viewing harmful content" | — | — | indirect | E 学段数字幸福感内容泛泛涵盖技术使用与幸福感影响；未具体针对有害内容。 |
| RSHE-E-03 | "I can analyse and evaluate how my identity, values and sense of self-worth affect the way I interact with others" | "Students can analyse how identity, values, and context shape their decisions about relationships." | E | direct | 在正确学段上主题与意图高度匹配。 |

**`coverage_csv`**（对应行）：

```csv
requirement_id,requirement_text,covered_by,bands,evidence_strength,notes
RSHE-D-01,"the characteristics of positive and healthy friendships… respect, honesty, trust, loyalty, kindness, generosity, boundaries, privacy, consent and the management of conflict","Students can identify healthy and unhealthy relationship patterns and articulate why each is so.",D,direct,Strong topical and intent match.
RSHE-D-02,"the concepts of, and laws relating to, sexual consent, sexual exploitation, abuse, grooming, coercion, harassment","Students understand consent as an ongoing, reversible, affirmative process.",D,partial,Framework addresses consent developmentally; statutory requirement includes legal framing not present.
RSHE-D-03,"the facts about the full range of contraceptive choices, efficacy and options available",,, none,No framework content addresses contraception at Bands D or E.
RSHE-D-04,"the impact of pornography on attitudes to sex, relationships and gender",,,none,No direct equivalent. Digital wellbeing content is adjacent but not specific.
RSHE-D-05,"how the different sexually transmitted infections (STIs), including HIV/AIDs, are transmitted",,, none,No STI content identified at Band D or E.
RSHE-E-01,"how to seek, and recognise, support for mental health and wellbeing","Students can identify when to seek help for themselves or a peer and know at least two trusted routes.",D,partial,Addressed at Band D not E; partial coverage at wrong band.
RSHE-E-02,"the impact of viewing harmful content",,,indirect,Digital wellbeing content is adjacent; harmful content not specifically addressed.
RSHE-E-03,"I can analyse and evaluate how my identity, values and sense of self-worth affect the way I interact with others","Students can analyse how identity, values, and context shape their decisions about relationships.",E,direct,Close topical and intent match.
```

**`gap_summary`**：在抽样的 8 项要求中，有 3 项在 D、E 学段完全无覆盖（none），另有 1 项仅为间接覆盖（indirect）。无覆盖行主要集中在性健康内容上：避孕选择（RSHE-D-03）、性传播感染传播与预防（RSHE-D-05）以及色情与有害内容（RSHE-D-04 与 RSHE-E-02，后者仅为间接覆盖）。这些构成了中学阶段的实质性法定缺口。此外，心理健康求助要求（RSHE-E-01）虽有部分满足，但落在了比法定位置更早的学段，意味着 E 学段要求本身未获回应。

**`coverage_statistics`**：
```json
{
  "total_requirements": 8,
  "directly_covered": 2,
  "partially_covered": 2,
  "indirectly_covered": 1,
  "not_covered": 3
}
```

# 已知局限

**主题覆盖不等同于深度等效。** 在 `coverage_table` 中显示为与某要求“direct（直接）”匹配的框架条目，仅证明该主题出现在框架文档中。它并不证明该主题是按要求所期望的深度教授的、按要求所期望的方式评估的，或按认证机构所寻求的复杂程度实施的。Webb（1997）的知识深度维度——框架内容的认知要求是否匹配要求的认知要求——超出本技能范围。被归类为直接覆盖的表格行是专业审查的起点，而非结论。

**提交任何认证材料前均需人类专业判断。** 本技能为课程协调员或认证审查员的工作生成脚手架。覆盖分类是通过对照框架文本进行模式匹配生成的；尚未经过相关监管领域合格专业人员的审查。在将此输出用于支撑认证主张之前，具备资质的专业人员必须逐一审查每个直接覆盖和部分覆盖行，并确认在认证机构对要求的解读下该匹配依然成立。本技能明确不能替代此类审查。

**本技能无法评估已教授、已评估或已实施的课程。** 框架输入描述的是“预期课程（intended curriculum）”——即学校文档声称将要教授的内容。本技能是文档对照文档的审计。它无法判断框架内容是否在课堂上实际交付、是否被评估，或已实施课程是否与书面框架一致。表格中的覆盖仅代表纸面覆盖。认证机构与法定督学通常需要已实施课程的证据，而不仅仅是书面课程证据；本技能仅支持文档审查阶段。
