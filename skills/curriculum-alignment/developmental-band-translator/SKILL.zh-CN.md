---
name: developmental-band-translator
description: 为经 harness 拆解的课程条目（KUD、LT、标准）标注学校的发展学段元数据，同时保留源文本原声与原标签。提供学段方案即可，本技能将据此推导出映射规则。
disable-model-invocation: false
user-invocable: true
effort: medium
skill_id: curriculum-alignment/developmental-band-translator
skill_name: 发展学段转换器（Developmental Band Translator）
domain: curriculum-alignment
version: "1.0"
evidence_strength: moderate
evidence_sources:
  - "Wiggins, G. & McTighe, J. (2005) — Understanding by Design (2nd ed.), ASCD: backward design establishes the principle that curriculum alignment begins from stated outcomes and works backward through learning targets; band-tagging is an alignment operation on that model."
  - "Wiggins, G. & McTighe, J. (2011) — The Understanding by Design Guide to Creating High-Quality Units, ASCD: KUD as the canonical unit of translation between frameworks."
  - "Vygotsky, L. S. (1978) — Mind in Society: The Development of Higher Psychological Processes, Harvard University Press: the Zone of Proximal Development provides the theoretical basis for developmental banding as an age-and-readiness construct rather than a pure age construct."
  - "Heritage, M. (2008) — Learning Progressions: Supporting Instruction and Formative Assessment, CCSSO: progressions are developmental rather than age-deterministic; band mappings must preserve this."
  - "Webb, N. L. (1997) — Criteria for Alignment of Expectations and Assessments in Mathematics and Science Education, CCSSO Research Monograph No. 6: alignment is multi-dimensional (categorical concurrence, depth-of-knowledge, range, balance) — band translation addresses only the age-range dimension and must not be mistaken for full alignment."
input_schema:
  required:
    - field: band_schema
      type: string
      description: "学校或项目的发展学段定义。必须包含学段标签、大致年龄或年级范围以及任何命名分组。示例：REAL School Budapest 使用 Bands A–F——A (Water+Air Dragons, K–2, 5–7岁)、B (Earth Dragons, G3–4, 7–9岁)、C (Fire Dragons, G5–6, 9–11岁)、D (Metal+Light Dragons, G7–8, 11–13岁)、E (G9–10, 13–15岁)、F (G11–12, 15–17岁)。"
    - field: kud_json
      type: string
      description: harness 生成的 KUD 文件（kud.json）。每条至少包含 item_id、content_statement、knowledge_type 和 source_block_id。
    - field: lts_json
      type: string
      description: harness 生成的 LT 文件（lts.json）。每个 LT 必须包含 lt_id、lt_name、lt_definition、kud_item_ids 和 knowledge_type。
    - field: progression_structure_json
      type: string
      description: harness 为源框架生成的 progression_structure.json。必须包含 band_labels 和 source_type。优先使用 user_age_range_override，其次使用原生 age_range_hint 或分学段 approximate_age_range；若扁平型能力/倾向框架两者均无，则采用基于描述符的试探性映射（低置信度并标记教师审查）。仅当没有任何路径支持合理映射时，在 skill_flags 返回 request_age_range_context 并中止；切勿捏造年龄。
  optional:
    - field: criterion_bank_json
      type: string
      description: 若还需标准层级的学段标注，提供 harness 生成的 criterion_bank.json。可选——若省略则仅标注 KUD 条目和 LT。
    - field: source_name
      type: string
      description: 用于输出溯源的可读来源名称（如 "UK DfE Statutory RSHE, July 2025"）。若省略，默认取 progression_structure.source_slug。
    - field: user_age_range_override
      type: string
      description: 用户显式提供的年龄范围映射，可在首次调用时或收到 request_age_range_context 后提供。在原生年龄范围或扁平框架描述符映射之前优先应用；保留原生标签与年龄，在 skill_flags 中记录用户提供的溯源，并标记与原生年龄的冲突供教师审查。
output_schema:
  type: object
  fields:
    - field: source_metadata
      type: object
      description: 来源名称、source_type、source_band_labels（保持不变）以及技能运行溯源（版本、时间戳、调用方）。
    - field: band_tagged_kud
      type: array
      description: 每条 KUD 条目及其 school_band（字符串或数组）、band_confidence、source_band_preserved、source_voice_preserved（始终为 true）、ambiguity_flag、teacher_review_flag 和 band_rationale。
    - field: band_tagged_lts
      type: array
      description: 每个 LT 及其 school_band（字符串或数组）、band_confidence、source_band_preserved、source_voice_preserved（始终为 true）、ambiguity_flag、teacher_review_flag 和 band_rationale。学段根据提示词中描述的聚合规则从 LT 下属的 KUD 条目继承。
    - field: band_tagged_criteria
      type: array
      description: 仅当提供了 criterion_bank_json 时出现。字段集与 LT 相同。除非某条标准显式收窄了年龄范围，否则继承父级 LT 的学段。
    - field: summary_counts
      type: object
      description: 按学校学段统计的条目数、模糊标志数、教师审查标志数和低置信度标签数。用于快速质量扫描。
    - field: skill_flags
      type: array
      description: 任何技能级警告（缺失年龄范围、需要全面教师审查的 CASEL 风格框架、若检测到任何改写发出的源声音保留警告）。
chains_well_with:
  - curriculum-crosswalk
  - kud-knowledge-type-mapper
  - learning-progression-builder
  - competency-framework-translator
  - scope-and-sequence-designer
teacher_time: 10 分钟
tags:
  - developmental-bands
  - curriculum-alignment
  - band-mapping
  - source-voice-preservation
  - Wiggins-McTighe
  - Vygotsky
  - ZPD
  - framework-translation
---

# 本技能的作用

本技能为外部课程——已由课程 harness 拆解为 KUD 条目、学习目标（LT）以及（可选）评价标准——标注学校的发展学段标签。学校的学段方案作为输入提供；本技能读取该方案，推导出从源框架年龄范围到学校学段范围的映射表，并将该映射应用于每一条数据。每条数据都会获得一个 `school_band` 值、一个置信度等级和诊断标志。源框架自身的学段标签会与新的学校学段标签一并原样保留，从而使输出始终可以追溯回原框架并对照解读。

本技能是一项**元数据操作**，而非内容操作。它不改写 KUD、LT 或标准，也不重新阐释源框架的意图。它唯一的工作是回答这个问题：“如果一位负责特定学校学段的教师打开这份框架，其中的哪些内容与他们相关？”当源学段跨越两个学校学段时，本技能刻意保持保守：同时分配两个候选学段、设置模糊标志并记录理据。下游技能——尤其是 Curriculum Crosswalk 技能和人类规划流程——会借助教师判断解决这些模糊性。

本技能处理三种常见的源结构情景。大多数来源具有显式学段结构（威尔士 CfW Progression Steps、新西兰课程等级、IB PYP/MYP/DP 阶段），可清晰映射，偶有边界模糊。有些来源具有形式上多段但实质压缩的结构（英国 RSHE 有四个关键阶段标签，但法定文件中只有两个实际年龄段），此时本技能先应用来源真实的双段结构，并通过 `source_band_preserved` 记录形式标签。少数来源完全没有学段结构（CASEL 及部分能力框架），此时本技能依据发展描述符而非年龄进行映射，并将每一条都标记为需教师审查。

# 实证基础

**Wiggins & McTighe（2005, 2011）**——《追求理解的教学设计（UbD）》将 KUD（知/理/行，Know/Understand/Do）确立为框架内容转化为可教内容的单元级架构，并将课程对齐定位为从既定结果出发的逆向设计操作。发展学段转换器正是在 UbD 指定的 KUD 层级上运行，并将学校学段分配视为逆向设计流水线中面向一线教师的一步。

**Vygotsky（1978）**——最近发展区（ZPD）奠定了以下理论基础：发展学段并非纯粹的年龄切分。处于特定学段的学习者是由“在支持下能做什么”来界定的，而不仅仅是生理年龄。这证明了本技能在标注时同时使用年龄范围与发展描述符证据的合理性，以及在缺乏年龄证据时仅凭描述符推理分配学校学段的合理性。

**Heritage（2008）**——学习进阶文献进一步指出，进阶是发展轨迹，而非日历时间表。本技能将学校学段视为轨迹路标。当源框架的原生进阶比学校更粗糙时（例如 RSHE 的双段结构 vs. 六学段学校方案），本技能通过模糊标志诚实保留这种粗糙度，而非强行制造虚假精确。

**Webb（1997）**——经典对齐框架定义了四个对齐维度：类别一致性、知识深度一致性、知识范围对应性、表征平衡性。学段转换主要处理**范围**维度（年龄跨度是否匹配？），并部分触及**类别一致性**。本技能不声称评估深度或平衡对齐；这一局限在 `skill_flags` 和“已知局限”中予以说明。

# 输入规范

**必填输入：** 本技能需要四项输入。下方的年龄语境规则明确了未变前置元数据中遗留的年龄范围描述：在请求缺失的原生年龄范围之前，先检查是否提供了覆盖参数以及是否适用扁平框架分支。

- **`band_schema`**——学校或项目的发展学段定义。必须包含学段标签、大致年龄或年级范围以及任何命名分组。本技能读取它来构建映射表；它不预设任何特定学段体系。*示例*：“REAL School Budapest uses Bands A–F — A (Water+Air Dragons, K–2, ages 5–7), B (Earth Dragons, G3–4, ages 7–9), C (Fire Dragons, G5–6, ages 9–11), D (Metal+Light Dragons, G7–8, ages 11–13), E (G9–10, ages 13–15), F (G11–12, ages 15–17).”
- **`kud_json`**——KUD 文件。每条必填字段：`item_id`、`content_statement`、`knowledge_type`、`source_block_id`。本技能使用 `source_block_id` 在进阶结构中查找该区块的原生学段标签。
- **`lts_json`**——LT 文件。每个 LT 必填字段：`lt_id`、`lt_name`、`lt_definition`、`kud_item_ids`、`knowledge_type`。LT 按最大跨度规则（见提示词）从其下属 KUD 条目继承学段。
- **`progression_structure_json`**——进阶结构。必填：`band_labels` 与 `source_type`；使用顶层 `age_range_hint` 或分学段 `approximate_age_range` 进行基于年龄的映射。若缺失原生年龄，先检查 `user_age_range_override` 与下方的扁平框架分支。仅当两者均无法提供合理映射时，才请求年龄语境并中止。

**可选输入：**

- **`criterion_bank_json`**——若提供，评价标准也会被标注。除非内容收窄到更具体的年龄信号，否则标准继承其父级 LT 的学段。
- **`source_name`**——用于输出元数据的友好名称。
- **`user_age_range_override`**——用户提供的年龄范围映射；可在首次调用时或收到 `request_age_range_context` 后提供。在无年龄检查之前优先将其作为映射语境应用，保留原生标签，并在 `skill_flags` 中记录其用户提供状态及与原生年龄的任何冲突。

**必填输入示例：** REAL School Budapest 对 `uk-statutory-rshe` 运行时：`band_schema` = "REAL School Budapest uses Bands A–F — A (Water+Air Dragons, K–2, ages 5–7), B (Earth Dragons, G3–4, ages 7–9), C (Fire Dragons, G5–6, ages 9–11), D (Metal+Light Dragons, G7–8, ages 11–13), E (G9–10, ages 13–15), F (G11–12, ages 15–17)"；`kud_json` = 279 条目的 KUD 文件；`lts_json` = 44 个 LT 的文件；`progression_structure_json` = 声明 `band_labels: ["End of Primary (Year 6)", "End of Secondary (Year 11)"]`、`source_type: "national_statutory_curriculum"` 及年龄范围分别为 5–11 和 11–16 的结构文件。

# 提示词（Prompt）

You are a curriculum band-translation assistant. Your task is to tag an external framework — already decomposed by the curriculum harness — with a school's developmental band labels, while preserving the source's own voice and labels completely unchanged.

## School band schema

Read the supplied `band_schema` carefully. It defines the school's band labels, grade spans, age ranges, and any named groupings. All band assignments you produce must use the band labels exactly as defined in that schema.

## Procedure

1. **Read the progression structure and choose mapping context.** Preserve `source_type` and `band_labels`. First apply an explicit `user_age_range_override` as user-supplied mapping context, without rewriting native labels or ages; flag any conflict with native ranges for teacher review. Otherwise use native `age_range_hint` or per-band `approximate_age_range`. If neither exists and this is a competency/dispositional framework with no native age structure, use the conservative flat-framework branch below. Only if none of these routes supports mapping, emit `request_age_range_context` in `skill_flags`, do not tag anything, and stop. Do not invent ages.
2. **Build a band-mapping table for this source.** Using the `band_schema` and the mapping context selected in step 1 (or the flat-framework descriptors), identify which school bands overlap with each source band. Where a source band's age range spans multiple school bands, list all overlapping school bands as candidates and note the ambiguity. Where the source band maps cleanly to one school band, record low ambiguity. Record this mapping table in your reasoning before proceeding; every tagging decision in steps 3–5 must trace back to it.
3. **Tag every KUD item.**
   - Look up its `source_block_id` to find the source band.
   - Apply the band-mapping table to get candidate school bands.
   - `school_band`: single band as a string if unambiguous; array of bands if ambiguous.
   - `band_confidence`: `high` if single school band and source age range ≤ the school's narrowest band span; `medium` if two school bands; `low` if three or more, or if derived by developmental-descriptor inference only.
   - `source_band_preserved`: the exact native label from the source (e.g. "Key Stage 2", "End of Primary", "Progression Step 3").
   - `source_voice_preserved`: always `true`. If you would need to rewrite the content to make it fit a school band, do NOT rewrite — instead set this to `false` and add a skill flag. This field exists to prove no rewriting occurred.
   - `ambiguity_flag`: `true` if `school_band` is an array.
   - `teacher_review_flag`: `true` when (a) `school_band` spans three or more bands, (b) confidence is `low`, (c) `source_type` is a dispositional/competency framework with no age-banding (e.g. CASEL), or (d) the content statement contains developmental language that would narrow the band beyond what the source label allows, or (e) a user-supplied override conflicts with native age ranges.
   - `band_rationale`: one sentence explaining the assignment.
4. **Tag every LT.** An LT's school band is the union of its constituent KUD items' bands (max-span rule). If any constituent is ambiguous, the LT is ambiguous. `teacher_review_flag` fires if any constituent has it or if the LT aggregates across three or more school bands.
5. **Tag criteria** (if `criterion_bank_json` supplied). Each criterion inherits its parent LT's band unless its content narrows it. Same field set as LTs.
6. **Emit summary counts and skill flags.** Count items per school band, ambiguity flags, teacher-review flags, and low-confidence tags. Emit a skill flag for any source where >50% of items are ambiguous (signals a structural mismatch worth reviewing).

## Source-voice preservation rule (hard constraint)

You are **tagging** content, not rewriting it. Do not paraphrase, shorten, or "translate" content statements, LT definitions, or criterion descriptions into the school's preferred prose style. Keep source content exactly as written. The only new text you generate is `band_rationale`.

## CASEL / flat-framework handling

If `source_type` indicates a competency or dispositional framework with no age structure (e.g. CASEL), and no `user_age_range_override` was supplied:
- Set `teacher_review_flag: true` on every item. If a descriptor does not support narrowing, retain all plausible school bands, explain the uncertainty, and ask for teacher context rather than guessing a precise age.
- Set `band_confidence: low` on every item.
- Base `school_band` on the developmental sophistication of the descriptor, mapped to the school bands from the supplied `band_schema`: early-developmental content (emotion-labeling, basic self-regulation) → earliest bands in the schema; mid-developmental content (perspective-taking, collaborative problem-solving) → mid-range bands; late-developmental content (systems-level social awareness, abstract ethical reasoning) → later bands in the schema.
- Emit `skill_flag: casel_style_framework_full_teacher_review_required`.

## Inputs

- `band_schema`: {{band_schema}}
- `source_name`: {{source_name}}
- `progression_structure_json`: {{progression_structure_json}}
- `kud_json`: {{kud_json}}
- `lts_json`: {{lts_json}}
- `criterion_bank_json`: {{criterion_bank_json}}
- `user_age_range_override`: {{user_age_range_override}}

Produce the band-tagged output as a single JSON object conforming to the output schema. Do not rewrite source content. Do not invent bands the source cannot support.

# 示例输出

**情景：** REAL School Budapest 学段方案作为 `band_schema` 传入。来源：英国 DfE 法定 RSHE（2025 年 7 月），`progression_structure.band_labels = ["End of Primary (Year 6)", "End of Secondary (Year 11)"]`，`source_type = "national_statutory_curriculum"`。

**示例输入节选**（因篇幅所限此处省略必填的 KUD 与 LT 文件；实际运行时必须提供）：

```json
{
  "band_schema": "REAL School Budapest uses Bands A–F — A (Water+Air Dragons, K–2, ages 5–7), B (Earth Dragons, G3–4, ages 7–9), C (Fire Dragons, G5–6, ages 9–11), D (Metal+Light Dragons, G7–8, ages 11–13), E (G9–10, ages 13–15), F (G11–12, ages 15–17). Bands are defined primarily by grade level; ages are approximate.",
  "source_name": "UK DfE Statutory RSHE, July 2025",
  "progression_structure_json": "{ \"band_labels\": [\"End of Primary (Year 6)\", \"End of Secondary (Year 11)\"], \"source_type\": \"national_statutory_curriculum\", \"age_range_hint\": { \"End of Primary (Year 6)\": \"5–11\", \"End of Secondary (Year 11)\": \"11–16\" } }"
}
```

**输出节选**（下方汇总计数仅覆盖这 3 条 KUD 条目和 1 个 LT）：

```json
{
  "source_metadata": {
    "source_name": "UK DfE Statutory RSHE, July 2025",
    "source_type": "national_statutory_curriculum",
    "source_band_labels": ["End of Primary (Year 6)", "End of Secondary (Year 11)"],
    "skill_version": "1.0",
    "run_timestamp": "2026-04-20T14:05:00Z"
  },
  "band_tagged_kud": [
    {
      "item_id": "blk_0002_item_01",
      "content_statement": "Young people understand the correct terms for different parts of the body",
      "knowledge_type": "Type 1",
      "school_band": ["A", "B", "C"],
      "band_confidence": "low",
      "source_band_preserved": "End of Primary (Year 6)",
      "source_voice_preserved": true,
      "ambiguity_flag": true,
      "teacher_review_flag": true,
      "band_rationale": "Source groups all primary-age content into one band spanning ages 5–11; REAL Bands A–C cover this same range (5–7, 7–9, 9–11 respectively)."
    },
    {
      "item_id": "blk_0346_item_03",
      "content_statement": "Pupils can communicate their boundaries about physical contact and privacy needs",
      "knowledge_type": "Type 2",
      "school_band": ["A", "B", "C"],
      "band_confidence": "low",
      "source_band_preserved": "End of Primary (Year 6)",
      "source_voice_preserved": true,
      "ambiguity_flag": true,
      "teacher_review_flag": true,
      "band_rationale": "Statutory End-of-Primary expectation covering ages 5–11; maps to REAL Bands A–C."
    },
    {
      "item_id": "blk_0210_item_02",
      "content_statement": "Students understand the concepts of, and laws relating to, sexual consent",
      "knowledge_type": "Type 1",
      "school_band": ["D", "E", "F"],
      "band_confidence": "low",
      "source_band_preserved": "End of Secondary (Year 11)",
      "source_voice_preserved": true,
      "ambiguity_flag": true,
      "teacher_review_flag": true,
      "band_rationale": "End-of-Secondary covers ages 11–16; REAL Bands D (11–13), E (13–15), and F (15–17) overlap this range; the partial overlap with F is retained for teacher review."
    }
  ],
  "band_tagged_lts": [
    {
      "lt_id": "cluster_01_lt_01",
      "lt_name": "Identifying Body Parts and Privacy",
      "school_band": ["A", "B", "C"],
      "band_confidence": "low",
      "source_band_preserved": "End of Primary (Year 6)",
      "source_voice_preserved": true,
      "ambiguity_flag": true,
      "teacher_review_flag": true,
      "band_rationale": "Aggregated from 4 KUD items all tagged End of Primary; max-span = REAL Bands A–C."
    }
  ],
  "summary_counts": {
    "total_kud_items": 3,
    "total_lts": 1,
    "kud_by_band": {"A-B-C_ambiguous": 2, "D-E-F_ambiguous": 1},
    "lts_by_band": {"A-B-C_ambiguous": 1},
    "teacher_review_flagged": 4,
    "low_confidence": 4
  },
  "skill_flags": [
    "high_ambiguity_rate_structural: 100% of items are ambiguous because source has 2 bands spanning 3 school bands each. This is expected for national_statutory_curriculum sources with compressed band structures; do not treat as a quality failure. Downstream planning must resolve via teacher judgement."
  ]
}
```

# 已知局限

**本技能不进行构念对齐。** 仅凭两个条目被标为同一学校学段，并不意味着它们教授的是同一件事。Webb（1997）的类别一致性与知识深度维度超出范围。本技能回答的是“这是否适龄？”，而非“这是否匹配学校的学习意图？”。Curriculum Crosswalk 技能处理框架之间的关系，但构念对齐仍需人工判断。

**本技能无法自行消解模糊性。** 当源框架的学段结构比学校更粗糙时——尤其是英国 RSHE 的双段结构或任何学段数少于学校方案的框架——本技能刻意保留模糊性而非臆测。高模糊率（RSHE 对照六学段方案时高达 100%）是对源框架粒度的诚实报告，而非质量故障。它们将在下游由教师判断解决，这正是 `teacher_review_flag` 存在的意义。

**发展描述符推断（CASEL 案例）只是近似值。** 当框架没有年龄分段时，本技能以传入的 `band_schema` 为指南按描述符映射——早期发展描述符 → 方案中最早期学段；系统级描述符 → 较后期学段。这些只是基于描述符的临时起点，并非经过验证的年龄常模或框架特定定论。以此方式标注的内容应被视为教师审查的脚手架，而非已验证的映射。

**本技能假设输入已通过 harness 验证。** 它不会重新验证源拆解结果。如果上游 harness 产出了损坏的 KUD 或 LT 文件（前置图谱存在环、缺少 `content_statement` 等），本技能会把这些错误作为带学段标签的无效输出透传下去。调用本技能前请先运行 harness 自身的质量校验门禁。
