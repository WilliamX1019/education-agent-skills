---
name: curriculum-crosswalk
description: 对比两个或以上带学段标签的课程框架，生成框架中立的主题矩阵以展示所有输入中的覆盖与缺口，并在提供参考框架时额外生成以参考框架为中心的 PLC 对照文档。
disable-model-invocation: false
user-invocable: true
effort: high
skill_id: curriculum-alignment/curriculum-crosswalk
skill_name: 课程框架对照（Curriculum Crosswalk）
domain: curriculum-alignment
version: "2.0"
evidence_strength: moderate
evidence_sources:
  - "Webb, N. L. (1997) — Criteria for Alignment of Expectations and Assessments in Mathematics and Science Education, CCSSO Research Monograph No. 6: the canonical four-dimension alignment framework (categorical concurrence, depth-of-knowledge consistency, range-of-knowledge correspondence, balance of representation); this skill operationalises categorical concurrence and range at the school-band level."
  - "Porter, A. C. (2002) — Measuring the content of instruction: Uses in research and practice, Educational Researcher 31(7), 3–14: the Surveys of Enacted Curriculum methodology for comparing intended vs enacted curricula across frameworks via common content taxonomies."
  - "Porter, A. C., Smithson, J., Blank, R. & Zeidner, T. (2007) — Alignment as a teacher variable, Applied Measurement in Education 20(1), 27–51: alignment indices and content-matrix methodology applied across standards documents."
  - "Case, B. J., Jorgensen, M. A. & Zucker, S. (2004) — Alignment in Educational Assessment, Pearson Assessment Report: practical alignment procedures that surface rather than hide framework differences — the rationale for the divergence and unique-content tables in this skill's output."
  - "Martone, A. & Sireci, S. G. (2009) — Evaluating alignment between curriculum, assessment, and instruction, Review of Educational Research 79(4), 1332–1361: literature review establishing that alignment studies should preserve framework distinctiveness rather than collapse to a lowest-common-denominator schema — the design principle behind this skill's refusal to produce a merged mega-framework."
input_schema:
  required:
    - field: comparison_frameworks_band_tagged
      type: string
      description: 包含两个或以上框架的数组，每个框架均由 Developmental Band Translator 生成。每个条目必须包含 source_metadata、band_tagged_kud（或等效的承载内容的条目）以及 band_tagged_lts。所有框架在主矩阵输出中均被视为平等参与者。
  optional:
    - field: reference_framework_band_tagged
      type: string
      description: 可选的指定参考框架，已使用 Developmental Band Translator 标注学段。若提供，本技能将同时生成框架中立矩阵与次级的以参考框架为中心的 PLC 对照文档；若省略，仅生成框架中立矩阵输出。
    - field: reference_framework_name
      type: string
      description: 用于输出标注的参考框架可读名称。若省略，默认取 reference_framework_band_tagged 元数据中的 source_name。
    - field: theme_taxonomy
      type: string
      description: 可选的预定义主题标签列表。若提供，本技能将把所有框架内容映射至这些主题，而非从输入中推导主题。覆盖模型自动推导的主题分组。在反复对变动输入运行本技能且需要跨次保持行标签一致时使用。
    - field: focus_bands
      type: string
      description: 将对照限制在部分学校学段内（例如针对中学 PLC 使用 "D,E"）。若省略，覆盖所有学段。
    - field: focus_themes
      type: string
      description: 限定特定主题领域（例如 "consent, relationships"）。若省略，对比全部内容。
    - field: plc_context
      type: string
      description: PLC 情境的简短描述（例如“D/E 学段幸福感团队正在为 2026 年 9 月规划做准备”）。用于在提供参考框架时微调次级 crosswalk_document 中的“PLC 讨论问题”板块。
output_schema:
  type: object
  fields:
    - field: framework_neutral_matrix
      type: string
      description: 主输出。按主题 × 学段逐行排列的 Markdown 矩阵。行通过扫描全部输入框架推导——不会因为某个框架缺少某主题而将其排除。列为每个框架一列（地位平等）。空单元格显性标为“—”；任何框架的空单元格都是可见缺口，而非遗漏。
    - field: framework_neutral_matrix_csv
      type: string
      description: 学段粒度的主 CSV。列：theme、band，随后每个框架一列内容与一列 band_confidence，加上 gap_count（该主题 × 学段下为空的框架数量）与 notes。每个主题 × 学段组合占一行。
    - field: framework_neutral_summary_matrix
      type: string
      description: 摘要粒度的 CSV。每个主题占一行（而非按学段），展示哪些框架覆盖它以及覆盖的学段范围。专为快速扫视跨框架覆盖情况而设计。
    - field: theme_grouping_flags
      type: array
      description: 标记供人工审查的歧义主题分组数组。每条包含：主题标签、归入其下的源主题、分组决策理据。将阐释不确定性显性化，而非隐藏在已知局限中。
    - field: crosswalk_document
      type: string
      description: 次级输出——仅当提供 reference_framework_band_tagged 时生成。供教师或 PLC 主持人直接使用的 Markdown 文档。包含五个必需板块（趋同、分歧、独有内容、排序差异、PLC 讨论问题）外加说明框架与范围的简短引言。
    - field: crosswalk_convergence_csv
      type: string
      description: 次级输出——仅当提供 reference_framework_band_tagged 时生成。扁平 CSV，每行对应一个 LT × 学段 × 对比框架配对。列：lt_id, lt_name, band, reference_content, comparison_framework, comparison_content, comparison_source_label, confidence, issue_type, notes。comparison_content 为空表示未找到对应项。
    - field: skill_flags
      type: array
      description: 技能级警告（重叠不足以产生有意义趋同、上游模糊率超过 50% 的框架、focus_bands 排除了某个框架的全部内容、框架过多导致输出难以阅读等）。
    - field: internal_trace
      type: object
      description: 保留用于调试和技能串联的非散文元数据——参与对比的框架 ID、各板块条目数、学段覆盖矩阵、主题推导日志。不包含在主输出或次级输出文档中。
chains_well_with:
  - developmental-band-translator
  - learning-progression-builder
  - scope-and-sequence-designer
  - curriculum-knowledge-architecture-designer
  - gap-analysis-from-student-work
teacher_time: 30 分钟
tags:
  - curriculum-alignment
  - crosswalk
  - framework-comparison
  - Webb-alignment
  - Porter-content-analysis
  - PLC
  - source-voice-preservation
---

# 本技能的作用

本技能对比两个或以上带学段标签的课程框架，并生成一份框架中立的主题矩阵作为主输出。其输入来自 Developmental Band Translator 技能的输出——每个框架一份输出。每个框架都被视为平等参与者：出现在任何框架中的主题都会作为矩阵中的一行，而某框架在特定“主题 × 学段”下的缺失会显性显示为“—”缺口，而非被忽略。这使得主输出不仅能揭示框架间的共识，还能清晰暴露任何框架的缺失之处。

如果同时提供了参考框架，本技能还会额外产出一份次级的、以参考框架为中心的对照文档——一份教师或 PLC 主持人可直接打开用于专业研讨的 Markdown 文档，按五个必需板块组织：趋同（Convergence）、分歧（Divergence）、独有内容（Unique Content）、排序差异（Sequencing Differences）以及 PLC 讨论问题（Questions for PLC）。仅当提供参考框架时，才会生成该次级文档及其配套 CSV。

本技能刻意采取“加法”而非“减法”原则。它不会把各框架合并成单一综合大纲，也不会把表述改写成统一腔调。每个框架的内容都以其原始措辞原封不动地出现在输出中，并具名归因。这一设计决策植根于 Martone & Sireci（2009）：掩盖框架独特性的对齐工作会丢失 PLC 做出规划决策最需要的信息。

本技能对“跨框架共识”与“跨框架巧合”做出严格区分。两个框架在同一学段涉及同一主题，只有当它们以可比的深度与意图处理该主题时，才构成趋同。在不明确的情况下，本技能会将该配对标记为*表面趋同，需教师确认（apparent convergence, teacher confirmation needed）*，而不会默默将其计为一致。

# 实证基础

**Webb（1997）**——四维度对齐框架（类别一致性、知识深度一致性、知识范围对应性、表征平衡性）是课程与评估对齐工作的经典参照。本技能在学校学段层面操作化了类别一致性（框架是否涉及相同主题？）与范围（适龄区间是否匹配？）。知识深度与平衡性刻意不自动评估；“PLC 讨论问题”板块将这些留待人类研讨。

**Porter（2002）与 Porter 等人（2007）**——《已实施课程调查》方法论确立了框架对比需要一套共同的内容分类体系。主题分类体系——无论是通过 `theme_taxonomy` 提供还是从全部输入框架中推导——承担了这一角色。本技能继承了 Porter 方法论对透明性与可辩护性的承诺：每张表中的每个单元格都能追溯回具体框架中的具体条目。

**Case、Jorgensen & Zucker（2004）**——评估中的实用对齐程序明确建议对齐研究应保留框架差异而非掩盖差异。框架中立矩阵正是为此而设：参考框架单元格为“—”的主题行，与它匹配其他框架的行具有同等的信息价值。只展示重叠部分的对照表会抹去最重要的规划信号。

**Martone & Sireci（2009）**——该综述文章确立：对齐研究应保留框架独特性，而不是坍缩为一个最低公分母式的单一图式。本技能拒绝产出合并后的超级框架，并坚持以各自原声展示每个框架的内容，正是直接源于这一发现。

# 输入规范

**必填输入：** 本技能需要一项必填输入：

- **`comparison_frameworks_band_tagged`**——由两个或以上 Developmental Band Translator 输出组成的数组。该数组中的所有框架在主矩阵输出中均被视为平等参与者。超过四个框架时，次级文档中的趋同表会变得过于庞大，本技能将发出 `too_many_frameworks_for_readable_output` 警告标志。

**可选输入：**

- **`reference_framework_band_tagged`**——若提供，本技能同时产出框架中立矩阵**与**次级的以参考框架为中心的 `crosswalk_document` 和 `crosswalk_convergence_csv`。参考框架在主矩阵中作为平等的一列出现。若省略，仅产出框架中立矩阵输出。
- **`reference_framework_name`**——用于输出标题与表格列的参考框架可读标签。
- **`theme_taxonomy`**——预定义的主题标签列表。若提供，所有框架内容都将映射到这些标签，而非从输入中推导主题。在针对变动输入反复运行本技能并需要跨次保持行标签一致时使用。
- **`focus_bands`**——用逗号分隔的学校学段列表，用于限定输出范围（例如针对中学 PLC 使用 `"D,E"`）。这些学段之外的内容将从所有表格中排除，但在引言中予以说明。
- **`focus_themes`**——自由文本主题限制（例如 `"consent, relationships"`）。本技能通过关键词与语义相似度匹配筛选条目；匹配日志保留在 `internal_trace` 中。
- **`plc_context`**——一两句话描述 PLC 受众与目的。用于在提供参考框架时微调次级 `crosswalk_document` 的“PLC 讨论问题”板块。

**示例（提供参考框架）：** REAL School Budapest D/E 学段幸福感 PLC 为 2026 年 9 月规划做准备时，可传入：`reference_framework_band_tagged` = REAL School 幸福感框架带学段标签输出；`comparison_frameworks_band_tagged` = [带学段标签的英国 DfE 法定 RSHE、带学段标签的威尔士 CfW 健康与幸福感]；`reference_framework_name = "REAL School Budapest Wellbeing Framework"`；`focus_bands = "D,E"`；`plc_context = "D/E 学段幸福感团队正在审查 2026-27 学年规划的覆盖缺口"`。三个框架在主矩阵中作为平等列出现，REAL School 的任何缺口单元格均显示为“—”。

**示例（不提供参考框架）：** 课程团队在设计新教学进度前对比三份已发布框架时，可仅传入 `comparison_frameworks_band_tagged` = [带学段标签的 IB MYP Health、带学段标签的英国 RSHE、带学段标签的威尔士 CfW H&W]。主矩阵平等展示三者；不生成次级对照文档。

# 提示词（Prompt）

You are a curriculum crosswalk assistant. You compare multiple band-tagged frameworks and produce a framework-neutral topic matrix as your primary output, and optionally a reference-centric crosswalk document as a secondary output.

## Step 1 — Read all frameworks and extract all topics

For each framework in `comparison_frameworks_band_tagged` (and `reference_framework_band_tagged` if supplied), list every band-tagged item: school band(s), content statement, source-band label, and knowledge type if present. Produce a combined topic list spanning all frameworks. No topic is excluded at this step.

## Step 2 — Group topics into coherent themes

If `theme_taxonomy` is supplied, map every topic from Step 1 to the nearest theme in that taxonomy. Do not invent new themes; flag unplaceable topics in `theme_grouping_flags`.

If `theme_taxonomy` is not supplied, derive themes from the full combined topic list. Group by semantic similarity and disciplinary coherence. Apply `focus_themes` filter (if supplied) after grouping.

For any grouping decision that is genuinely ambiguous — two frameworks addressing a topic at very different grain sizes, or content that plausibly belongs in two themes — add an entry to `theme_grouping_flags`. Each entry must include: the theme label, the source topics grouped under it, and the rationale for the grouping decision. Do not silently collapse ambiguous cases.

## Step 3 — Build the theme × band × framework matrix

For each theme × band combination in scope (all bands, or `focus_bands` if supplied), find the relevant content statement from each framework. If a framework has no content for that theme × band, the cell is "—". An empty cell for the reference framework is a visible gap — do not omit it.

Record for each non-empty cell: the verbatim content statement, the source-band label (e.g. "End of Secondary", "Progression Step 4"), and a band_confidence value (high / medium / low) reflecting upstream ambiguity from the Developmental Band Translator.

## Step 4 — Produce the matrix outputs

Produce three outputs:

**`framework_neutral_matrix`** — A Markdown table. Rows: theme × band. Columns: Theme, Band, then one column per framework (all on equal footing, including reference framework if supplied). Cells: verbatim content with source-band label in parentheses, or "—". Each "—" in any column is a visible gap.

**`framework_neutral_matrix_csv`** — A flat CSV at band level. One row per theme × band. Columns: theme, band, then for each framework: `[framework_name]_content` and `[framework_name]_band_confidence`, plus `gap_count` (integer: number of frameworks with "—" for this row), `notes`.

**`framework_neutral_summary_matrix`** — A summary CSV at theme level (one row per theme, not per band). Columns: theme, then for each framework: `[framework_name]_covers` (yes/no/partial) and `[framework_name]_band_range` (e.g. "D–E", "A–C", or "—").

Also produce **`theme_grouping_flags`** — the array of ambiguous grouping entries from Step 2.

## Step 5 — Produce secondary outputs (only if reference framework supplied)

If `reference_framework_band_tagged` was supplied, produce the secondary reference-centric outputs using the following logic:

**`crosswalk_document`** — A Markdown document for direct use by a PLC facilitator. Contains a short preamble and these five sections:

1. **Convergence table** — content that the reference framework and at least one comparison framework address at the same school band. Columns: Band; Reference content (verbatim); Comparison framework; Comparison content (verbatim); Confidence (high / medium / apparent-only).
2. **Divergence table** — content that the reference framework and at least one comparison framework *both* address but at *different* school bands. Columns: Topic; Reference band; Reference content (verbatim); Comparison framework; Comparison band; Comparison content (verbatim); Source label; Band-gap (in band units).
3. **Unique-content table** — content present in only one framework. One subsection per framework.
4. **Sequencing-difference notes** — prose description of meaningful differences in how the frameworks sequence related content. Focus on differences with planning implications.
5. **Questions for PLC** — 6–10 numbered questions grounded in specific cells from the tables above. Do NOT answer them.

**`crosswalk_convergence_csv`** — A flat CSV. One row per LT × band × comparison framework pairing. Columns: lt_id, lt_name, band, reference_content, comparison_framework, comparison_content, comparison_source_label, confidence, issue_type, notes. Every convergence, divergence, and unique-content row appears. Empty comparison_content is data, not an omission.

If `reference_framework_band_tagged` was not supplied, omit both `crosswalk_document` and `crosswalk_convergence_csv` entirely.

## Step 6 — Produce skill_flags and internal_trace

**`skill_flags`** — Emit warnings for: insufficient overlap to produce meaningful convergence; framework with >50% upstream ambiguity; `focus_bands` excluding all content in one framework; more than four frameworks producing unwieldy secondary output; fewer than 3 items remaining after filtering in any framework.

**`internal_trace`** — Framework ids compared, item counts per section, band-coverage matrix, theme derivation log (or taxonomy mapping log if `theme_taxonomy` was supplied), focus filter match log.

## Output format (hard constraints)

- `framework_neutral_matrix` and `crosswalk_document`: Markdown only. No JSON, no YAML, no field names, no `{variable}` placeholders.
- All framework content quoted verbatim. Do not paraphrase, shorten, or translate content statements. Quote marks around exact source text.
- Attribute every content statement to its source framework by name.
- Preserve source-band labels alongside school bands in every table row.
- If an item's band assignment was ambiguous upstream (multi-band), list every relevant band, not just one.

## Source-voice preservation (hard constraint)

Every content statement you reproduce must appear exactly as it did in the band-tagged input. Quote it. Attribute it. Do not rewrite it to match another framework's style. This is not stylistic — it is the crosswalk's core integrity property.

## Inputs

- `reference_framework_band_tagged`: {{reference_framework_band_tagged}}
- `reference_framework_name`: {{reference_framework_name}}
- `comparison_frameworks_band_tagged`: {{comparison_frameworks_band_tagged}}
- `theme_taxonomy`: {{theme_taxonomy}}
- `focus_bands`: {{focus_bands}}
- `focus_themes`: {{focus_themes}}
- `plc_context`: {{plc_context}}

Produce `framework_neutral_matrix`, `framework_neutral_matrix_csv`, `framework_neutral_summary_matrix`, and `theme_grouping_flags` in all cases. Produce `crosswalk_document` and `crosswalk_convergence_csv` only if `reference_framework_band_tagged` was supplied. Always produce `skill_flags` and `internal_trace`.

# 示例输出

**情景：** D/E 学段幸福感 PLC，将 REAL School Budapest 幸福感框架（参考框架，通过 `reference_framework_band_tagged` 传入）与英国 DfE 法定 RSHE 和威尔士 CfW 健康与幸福感（在 `comparison_frameworks_band_tagged` 中）对比。`focus_bands = "D,E"`。

---

## (a) `framework_neutral_matrix_csv` — 5 行示例

注意：第 4 行（STI 与避孕）中 REAL School 单元格为“—”，使缺口显性化。

```csv
theme,band,REAL_School_Wellbeing_content,REAL_School_Wellbeing_band_confidence,UK_RSHE_content,UK_RSHE_band_confidence,Welsh_CfW_content,Welsh_CfW_band_confidence,gap_count,notes
Consent Understanding,D,"Students understand consent as an ongoing, reversible, affirmative process.",high,"the concepts of, and laws relating to, sexual consent, sexual exploitation, abuse, grooming, coercion",medium (End of Secondary spans C–E),—,—,1,Welsh CfW has no direct consent content at PS3/PS4
Mental-health Help-seeking,D,"Students can identify when to seek help for themselves or a peer and know at least two trusted routes.",high,"where to get advice e.g. family, school and/or other sources",low (End of Primary — band D is out of RSHE's intended range),—,—,1,RSHE places this 2 bands earlier; placed here for nearest-band comparison
Digital Wellbeing,E,"Students can evaluate the wellbeing effects of their own technology use and adjust it.",high,—,—,"I can make informed decisions about how to use digital technologies… to enhance my physical health and well-being",medium (PS3 spans C–D),1,Welsh CfW places this 1–2 bands earlier; no RSHE coverage at E
STI and Contraception,E,—,—,"the facts about the full range of contraceptive choices, efficacy and options available",high (End of Secondary),—,—,2,Reference framework gap — REAL School has no content matching this theme at Band E
Natural Environment and Wellbeing,D,—,—,—,—,"I can explain the benefits of spending time in the natural environment for my health and well-being",high (PS3),2,Reference framework gap — theme absent in both REAL School and UK RSHE at Band D
```

---

## (b) `framework_neutral_summary_matrix` — 3 行示例

```csv
theme,REAL_School_Wellbeing_covers,REAL_School_Wellbeing_band_range,UK_RSHE_covers,UK_RSHE_band_range,Welsh_CfW_covers,Welsh_CfW_band_range
Consent Understanding,yes,D,yes,C–E (End of Secondary),no,—
STI and Contraception,no,—,yes,C–E (End of Secondary),no,—
Natural Environment and Wellbeing,no,—,no,—,yes,C–D (PS3)
```

---

## (c) `theme_grouping_flags` — 2 条示例

```json
[
  {
    "theme": "Consent Understanding",
    "source_topics_grouped": [
      "REAL School: 'Students understand consent as an ongoing, reversible, affirmative process.'",
      "UK RSHE: 'the concepts of, and laws relating to, sexual consent, sexual exploitation, abuse, grooming, coercion, harassment, rape'"
    ],
    "rationale": "Both address consent but at different epistemic grains and framing — REAL School frames consent developmentally; UK RSHE frames it propositionally and in law. Grouped under one theme for matrix comparability, but these may represent genuinely distinct learning goals. Flagged for human review."
  },
  {
    "theme": "Digital Wellbeing",
    "source_topics_grouped": [
      "REAL School: 'Students can evaluate the wellbeing effects of their own technology use and adjust it.'",
      "Welsh CfW: 'I can make informed decisions about how to use digital technologies… to enhance my physical health and well-being'"
    ],
    "rationale": "Both concern technology and wellbeing, but REAL School frames this as a self-regulation competency while Welsh CfW frames it as a health-literacy decision skill. Grouped under one theme but the pedagogical intent differs. A school treating these as one topic may be collapsing a meaningful distinction."
  }
]
```

---

## (d) 次级输出说明

`crosswalk_document` 是次级的、可供 PLC 直接使用的 Markdown 文档，仅当提供 `reference_framework_band_tagged` 时生成。生成时，它遵循与 1.0 版相同的五板块结构（趋同、分歧、独有内容、排序差异、PLC 讨论问题），以 REAL School 作为参考列。该文档的示例内容遵循与 1.0 版示例相同的格式——可参见该版示例表格。关键差异在于该文档如今处于次级位置：框架中立矩阵始终优先生成，并作为主要分析产出。

# 已知局限

**本技能不评估知识深度对齐。** Webb 的知识深度维度超出自动化对比的范围。本技能能看出两个框架都在同一学段涉及“同意（consent）”，但无法可靠判断它们是否处于相同的认知深度。“PLC 讨论问题”板块正是用于展开知识深度讨论的地方。置信度为“仅表面（apparent-only）”的趋同正是为此而显性标出。

**主题推导是最依赖主观判断的步骤。** 将来自多个框架的主题归类为连贯主题具有阐释性，而非机械操作。两个框架以截然不同粒度谈论“自我调节”时，是否应归入同一主题行见仁见智——本技能提出的是阐释性建议，而非权威分类。`theme_grouping_flags` 将不确定的案例显性化供人工审查，而非隐藏起来。在针对变动输入反复运行时，使用 `theme_taxonomy` 输入以保持行标签一致。

**本技能会继承上游模糊性。** 当 Developmental Band Translator 为条目标注多个候选学校学段时（英国 RSHE 的两段式结构常见此情况），矩阵会把这种模糊性带入每个单元格。上游模糊率高的框架会产出包含许多跨多学段行的矩阵，这虽然诚实，但阅读难度更大。当上游超过 50% 的条目跨多学段时，本技能会发出技能警告标志。

**本技能不合并框架。** 这是有意为之（Martone & Sireci, 2009）。本技能不会产出综合统一的大纲，也不会给出单一的推荐教学顺序。这些都是基于本输出、但必须由人类做出的规划决策。

**主题匹配并非完美。** 本技能依据内容陈述的语义相似度配对条目。假阴性（因措辞差异巨大而漏掉的真实匹配）和假阳性（表面词汇重叠但教学意图不同）都有可能发生。`apparent-only` 置信度层级用于提示假阳性风险；`theme_grouping_flags` 和“PLC 讨论问题”板块则用于兜底假阴性风险。本技能是教师阅读源文档的脚手架，而非替代品。
