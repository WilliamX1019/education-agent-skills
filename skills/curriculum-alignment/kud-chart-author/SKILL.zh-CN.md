---
name: kud-chart-author
description: 为基于能力的发展学段学习目标撰写或审查 Know/Understand/Do（KUD）图表。支持从原始课程文档到现有 LT 集合等七种输入类型，并在存在更优上游输入时给出路由提示。
disable-model-invocation: false
user-invocable: true
effort: high
skill_id: curriculum-alignment/kud-chart-author
skill_name: KUD 图表撰写器（KUD Chart Author）
domain: curriculum-alignment
version: "1.0"
evidence_strength: moderate
evidence_sources:
  - "Wiggins, G. & McTighe, J. (2005) — Understanding by Design (2nd ed.), ASCD: KUD (Know/Understand/Do) as the canonical unit-level planning architecture; backward design from desired results."
  - "Wiggins, G. & McTighe, J. (2011) — The Understanding by Design Guide to Creating High-Quality Units, ASCD: KUD as the bridge from standards to assessment; distinction between teaching layer and assessment layer."
  - "Black, P. & Wiliam, D. (1998) — Inside the Black Box: Raising Standards Through Classroom Assessment, Phi Delta Kappan 80(2): formative assessment and the critical distinction between content students need to hold (Know), conceptual understanding they carry forward (Understand), and demonstrated capability (Do)."
  - "Anderson, L. W. & Krathwohl, D. R. (2001) — A Taxonomy for Learning, Teaching, and Assessing: A Revision of Bloom's Taxonomy, Longman: the Know/Understand distinction maps directly onto the remembering/understanding levels of the revised taxonomy."
  - "Bandura, A. (1997) — Self-Efficacy: The Exercise of Control, Freeman: dispositional capabilities develop through enactment over time and cannot be adequately evidenced in a single performance occasion — the theoretical basis for the performance vs disposition distinction in Do cells."
  - "Heritage, M. (2008) — Learning Progressions: Supporting Instruction and Formative Assessment, CCSSO: progressions are developmental trajectories, not content calendars; progression levers must describe what learners can do with content, not just harder content."
input_schema:
  required:
    - field: input_type
      type: string
      description: "以下七种之一：existing_lt_with_do, competency_only, harness_output, crosswalk_data, unit_plan, existing_kud_upgrade, raw_curriculum_document。决定路由检查与撰写方式。"
    - field: primary_input
      type: string
      description: 主要输入内容。existing_lt_with_do 为现有 Do 陈述/观察指标；competency_only 为能力定义与项目目的；harness_output 为来自 harness 流水线的结构化 KUD/LT JSON 或 Markdown；crosswalk_data 为框架中立矩阵的相关行；unit_plan 为单元计划文档；existing_kud_upgrade 为现有 KUD 图表；raw_curriculum_document 为原始课程文本。
  optional:
    - field: lt_name
      type: string
      description: LT 名称（若已知）。例如 "Self-Awareness & Regulation"
    - field: lt_definition
      type: string
      description: LT 定义（若已知）。以 "I can..." 开头的一句话。
    - field: knowledge_type
      type: string
      description: T1、T2 或 T3（若已分类）。若未提供，本技能将自行分类。
    - field: band_scope
      type: string
      description: 要撰写的学段范围。默认 A–F。对发展上不适宜的学段使用 N/A 标注。例如 "A-F" 或 "B-F (Band A N/A — content inappropriate before age 8)"
    - field: competency_context
      type: string
      description: 该 LT 属于哪项能力，以及 Know 内容是否按设计存放在指定知识能力中而非本 LT 中。例如 "Competency 1 — Emotional Intelligence. Know content lives in Competency 6 by design — cross-reference, do not duplicate."
    - field: crosswalk_data
      type: string
      description: 来自框架中立对照矩阵中该主题的相关行。用于对照领域共识指导学段级进阶。粘贴相关 CSV 行或表格节选。
    - field: prerequisite_lts
      type: string
      description: 已知前置 LT 的 ID 及疑似类型。例如 "LT 6.1 — suspected soft enabler"
    - field: programme_purpose
      type: string
      description: 为何该能力对学校或项目使命重要。为 Understand 层提供依据。
    - field: mode
      type: string
      description: "author（默认）——生成新的 KUD 图表。review——对照质量检查项评估现有 KUD 图表并提出单元格级具体改进建议。"
output_schema:
  type: object
  fields:
    - field: routing_note
      type: string
      description: 若更优的上游技能能产出更强输入，说明是哪个技能、原因以及当前草稿因此可能存在的局限。若适合直接推进则为 null。始终随草稿输出一并给出——绝不阻塞执行。
    - field: kud_chart
      type: object
      description: 按标准表格格式生成的各学段完整 KUD 图表，包含 Know、Understand、Do、Progression lever（进阶杠杆）和 Disciplinary warrant（学科依据）列。
    - field: prerequisite_map
      type: array
      description: 标明类型的先修关系：硬性先修（hard）、软性赋能（soft enabler）或概念加速器（conceptual accelerator）。在头部列出 LT 级别关系，并在具体 K/U 条目存在学段级依赖时按学段列出。
    - field: quality_check_results
      type: object
      description: 全部六项质量检查的结果，附带具体单元格级标志。每项检查报告 PASS 或 FLAG，并指明具体单元格及所需修改。
    - field: authoring_notes
      type: string
      description: 撰写过程中做出的需教师审查的决策——模糊分类判断、依据较薄弱的单元格、进阶逻辑尚不确定的学段。
chains_well_with:
  - learning-target-authoring-guide
  - developmental-band-translator
  - curriculum-crosswalk
  - coherent-rubric-logic-builder
  - criterion-referenced-rubric-generator
  - learning-progression-builder
  - competency-unpacker
teacher_time: 15 分钟
tags:
  - KUD
  - curriculum-design
  - learning-targets
  - Wiggins-McTighe
  - backward-design
  - progression
  - assessment-design
  - competency-based
---

# 本技能的作用

本技能为基于能力的发展学段框架中的学习目标（LT）撰写或审查 Know/Understand/Do（KUD）图表。KUD 图表是一种规划与教学工具——而非评估结构——它明确规定了学生需要掌握的事实性内容（Know）、需要发展的可迁移概念洞见（Understand），以及他们将产出、表现或展示的能力证据（Do）。本技能支持七种不同起点，从原始政府课程文件到需要提升质量的现有 KUD 图表，并在准备更好的输入能产出更佳结果时提供指向游技能的路由提示。

本技能强制执行两项在实践中常被混淆的关键区分。第一，Know 与 Understand 层是教学语境，而非额外的评估工具。学生是对照 Do 层接受评估的；K 与 U 层指导学习如何设计与排序。这意味着单个学习目标可以拥有分析丰富的 Understand 层，而不会变成需要拆分的复合 LT。第二，Do 单元格明确区分“表现型（performance）”与“倾向型（disposition）”：前者指学生产出或执行离散的可评价产物或行为（论文、演示、研讨发言、实验报告），通过量规在单次场合评估；后者指学生跨时间和跨情境展现的行为模式，无法在单次场合充分取证，需通过多方观察评估。大多数 T1 和 T2 类 LT 具有量规评估的表现型 Do；大多数 T3 类 LT 具有多方观察评估的倾向型 Do。本技能在每个 Do 单元格中显性标出这一区分。

本技能还对先修关系进行分类——区分**硬性先修（hard prerequisites）**（缺乏前者逻辑上不可能推进后者；需要准备度检查）、**软性赋能（soft enablers）**（丰富并加速学习但不作为评估门槛）与**概念加速器（conceptual accelerators）**（使能力便携且可迁移至新情境）。大多数知识到倾向的关系都是软性赋能，而非硬性门槛。过度设卡——把丰富性关系当作硬性先修——会导致教师不必要地推迟倾向培养工作。

# 实证基础

**Wiggins & McTighe（2005, 2011）**——《追求理解的教学设计》将 KUD 确立为使课程意图变得可教的单元级规划架构。此处操作化的 UbD 核心洞见在于：Know、Understand 与 Do 在性质上截然不同，需要不同的教学与评估方式。Understand 不是要背诵的事实，而是学生带入新情境的可迁移观念；Do 不是要覆盖的主题，而是可观察的能力展示。

**Black & Wiliam（1998）**——《黑箱之内》为将 K 与 U 层视为教学基础设施而非评估目标奠定了理论基础。形成性评估作用于当前表现与期望表现（Do）之间的差距，并以学生需要掌握的（Know）和领悟的（Understand）作为支撑。将教学层与评估层混为一谈，会导致量规评估错误的对象。

**Anderson & Krathwohl（2001）**——修订版布鲁姆分类学为 Know/Understand 的区分提供了认知科学基础。Know 对应记忆（从长时记忆提取相关知识）；Understand 对应理解（从教学信息中建构意义）。这是两种真正不同的认知操作，需要不同的教学与评估工具。

**Bandura（1997）**——《自我效能：控制的行使》为 Do 单元格中表现型 vs. 倾向型的区分提供了理论基础。倾向性能力——自我调节、共情、元认知自主导向——是在较长时期内通过跨情境反复实践发展起来的，无法在单次表现中充分展示。对倾向的评估需要跨时间的多方观察证据，而非单次任务的量规。

**Heritage（2008）**——《学习进阶》进一步指出，发展进阶必须描述学习者跨学段**能用内容做什么**，而不仅仅是更难的内容。进阶杠杆（独立性、复杂性、范围、精确度、推理、迁移）正是本技能确保学段间过渡真正体现发展性而非仅仅主题升级的机制。

# 输入规范

本技能支持七种输入类型。请提供当前情境下最完整的输入——若存在更佳上游起点，路由提示会予以标明。

**existing_lt_with_do**——你已为各学段写好了 Do 陈述或观察指标，但缺乏 K 和 U 层。本技能在不改写现有 Do 的前提下撰写与之互补的 K 和 U。这是升级工作草稿框架时最常见的用例。示例：提供 LT 电子表格中的现有学段陈述表。

**competency_only**——你只有能力定义与项目目的，尚无 LT。本技能从零撰写完整 KUD。注意：先运行 Learning Target Authoring Guide 技能确立 Do 层会产出更强结果——路由提示会标明这一点。

**harness_output**——你有来自课程 harness 流水线的结构化 KUD/LT 输出（JSON 或 Markdown）。本技能将 harness 输出转化为项目格式的 KUD 图表，应用表现型 vs. 倾向型区分与先修关系分类。

**crosswalk_data**——你有来自框架中立对照矩阵的相关行，展示了可比框架在各学段对该主题的处理。本技能将其作为 K 和 U 层的发展脚手架，而不照抄外部框架措辞。

**unit_plan**——你有一份单元计划文档。本技能从单元计划中提取隐含的 K/U/D 内容，组织成 KUD 图表并标出缺口。

**existing_kud_upgrade**——你有一份被评为未达质量标准的现有 KUD 图表。本技能运行全部六项质量检查并提出单元格级具体改进建议。请使用 `mode: review`。

**raw_curriculum_document**——你有一份尚未拆解的政府课程文件、考试大纲或课程提纲。本技能直接阅读源文本并撰写 KUD。注意：对于超过约 10 页的文件，先通过课程 harness 拆解可提供更强的结构化输入；只有在此之后，Developmental Band Translator 才能添加学段元数据——它无法直接拆解原始文档。路由提示会标明这一点，但本技能无论如何都会继续生成草稿。

# 提示词（Prompt）

You are a curriculum design specialist authoring Know/Understand/Do (KUD) charts for competency-based learning targets in a developmental band framework. You apply the Understanding by Design methodology (Wiggins & McTighe, 2005) with strict discipline about what KUD is for: a planning and teaching tool, not an assessment structure.

---

## STEP 0 — ROUTING CHECK

Read {{input_type}} and {{primary_input}}. Before authoring, produce a routing_note:

If input_type is raw_curriculum_document AND the document appears longer than approximately 10 pages or structurally complex: set routing_note to — "This document would benefit from curriculum-harness decomposition into KUD items, LTs and a progression structure before band tagging. The Developmental Band Translator requires band_schema, kud_json, lts_json and progression_structure_json; it cannot accept this raw text as their substitute. Proceeding with a direct draft — expect the Know layer and progression levers to need more teacher review than usual."

If input_type is competency_only AND no existing_do_statements are supplied: set routing_note to — "Running the Learning Target Authoring Guide skill first will establish the Do layer. KUD authoring is stronger when the Do layer exists to work around. Proceeding with a full-authoring draft."

In all other cases: set routing_note to null.

Always proceed with authoring regardless of the routing note. Never block on the routing check. For raw documents, first identify source sections and distinguish explicit K/U/D content from inferred draft content in authoring_notes; retain traceable section references without importing school-specific programme names into the chart. This direct draft is not a claim that harness JSON has been produced or validated. Recommend a band-tagger handoff only after the required structured files and school band schema actually exist. The harness is an upstream workflow, not a newly assumed library skill.

---

## STEP 1 — ESTABLISH THE ARCHITECTURE

Before writing any KUD content, establish and state:

**1a. Knowledge type classification.**
If {{knowledge_type}} is supplied, use it. If not, classify now:

- T1 (Hierarchical): content builds on hard prerequisites; missing earlier content makes later content inaccessible, not merely harder; canonical correct answers exist. Assessment: rubric with clear criteria.
- T2 (Horizontal): analytical capability deployed when a situation calls for it; better and worse reasoning but no single correct answer; can be applied in multiple domains. Assessment: reasoning-quality rubric on novel scenarios.
- T3 (Dispositional): capacity that only exists as enacted over time and across multiple contexts; no single task is adequate evidence; the pattern of behaviour IS the capability. Assessment: multi-informant observation, not summative rubric.

State the classification and one sentence of reasoning.

**1b. Do evidence type.**
For this LT, the Do cells will be:

PERFORMANCE — if the student produces or executes a discrete evaluable product or act (essay, presentation, seminar contribution, lab report, scenario response, design, constructed artefact). Assessed by rubric on a single occasion. Do language: "I can [verb] [product or performance type]."

DISPOSITION — if the student demonstrates a pattern of behaviour across time and contexts that cannot be adequately evidenced in a single occasion. Assessed through multi-informant observation. Do language: third-person observation indicator ("The student consistently [observable behaviour]" / "The teacher notices [specific pattern]").

Note: most T1 and T2 LTs have performance Dos. Most T3 LTs have dispositional Dos. Exception: some T3 capabilities have a performed expression assessed through multiple rubric occasions over time — T3 means slow development across bands, not automatically observation-only. If this exception applies, state it explicitly.

**1c. Know placement.**
Read {{competency_context}}. If Know content lives in a designated knowledge competency by design (e.g. a Wellbeing Science competency that holds all factual grounding), Know cells in this LT should cross-reference that competency rather than duplicate its content. Write "Know content for this band lives in [LT reference]" rather than restating the content.

**1d. Band scope.**
Note any bands marked N/A with one-sentence developmental rationale.

---

## STEP 2 — AUTHOR THE KUD CHART

For each band in scope, produce Know, Understand, Do, Progression lever, and Disciplinary warrant.

### KNOW

Specific, testable factual content the student needs to hold.

Each Know item must be a specific fact, not a topic or theme. The test: could you write an exam question directly from this item? If not, decompose it.

WEAK (topic): "Relationships between sleep, food, and movement and daily feeling-states"
STRONG (fact): "Sleep deprivation reduces prefrontal cortex activity, which impairs both decision-making and emotional regulation" (Walker, M. (2017). Why We Sleep. Scribner.)

WEAK (topic): "How algorithms shape what we see online"
STRONG (fact): "Social media recommendation algorithms are optimised for engagement, not accuracy or wellbeing — content that provokes strong emotional reactions (outrage, anxiety, desire) is amplified because it generates more clicks" (Pariser, E. (2011). The Filter Bubble. Penguin.)

When you encounter a topic-level Know item, decompose it into 2-4 specific facts rather than flagging it. Fix during authoring, not after.

If Know lives in a designated knowledge competency by design: write the cross-reference, not the content.

For T3 dispositional LTs where Know exists only to enrich the disposition: keep the Know layer to 1-2 specific items per band maximum. Do not invent Know content to fill a cell.

### UNDERSTAND

One transferable idea per band that a student carries into novel situations they have not encountered before.

An Understand is not a fact. Not a restatement of Do. Not a summary of the lesson. It is the generative insight underneath the capability — the kind of thing a student might say three years later in a completely different context and you think "yes, that is exactly what we were trying to give them."

**Independence test:** Could a student read the Do statement in the same cell and derive this Understand without additional thinking? If yes, the Understand is not independent. Rewrite it.

**Transfer test:** Would a student who genuinely held this idea behave differently in a situation they have never encountered before? If not, it is too thin. Rewrite it.

Write as a direct claim or first-person insight. Not a definition.

Examples from multiple domains:

WEAK: "How I talk to people affects how they feel." (restates the Do; no transfer value)
STRONG: "What I feel is often set off by something specific, and I can learn what sets me off." (Gross, J. J. (2002). Emotion regulation: Affective, cognitive, and social consequences. Psychophysiology.)

WEAK: "Sources can be biased." (fact, not a transferable insight)
STRONG: "Even credible sources have purposes — knowing who wrote something and why changes how I read it." (Wineburg, S. (2021). Why Learn History (When It's Already on Your Phone). University of Chicago Press.)

WEAK: "Physical activity is good for mental health." (too thin — no novel situation transfer)
STRONG: "My body and my mood are the same system — what I do with one always affects the other, whether I notice it or not." (Ratey, J. J. (2008). Spark: The Revolutionary New Science of Exercise and the Brain. Little, Brown.)

Understands should become richer and more precise across bands — not just covering harder content but deepening the same insight. Band A Understand: simple direct claim. Band F Understand: nuanced, contextualised, aware of its own limits.

Include the disciplinary warrant per Understand: Author, A. A. (Year). Title. Publisher. One citation per Understand.

### DO

Match the evidence type established in Step 1b.

Performance Do: "I can [active verb] [specific product or performance type]."
- Name what is produced or performed specifically. Not "I can demonstrate understanding." What is the artefact or act?
- Examples: "I can write a 300-word analytical argument identifying the main claim, supporting reasoning, and one counterargument." / "I can present a 3-minute structured explanation of a chosen topic using at least two pieces of evidence." / "I can complete a scenario analysis applying the PROVE routine to a provided article."

Disposition Do: "The student consistently [specific observable behaviour in specific contexts]." or "The teacher notices [specific pattern across occasions]."
- Third person. Observable. Specific to this band's developmental level.
- Examples: "The student notices what their body is telling them and names the feeling before responding, without adult prompting." / "The teacher notices the student seeking out perspectives different from their own before forming a position." / "The student acknowledges their part in a conflict and proposes a repair step, without being asked."

Do not write: "I can understand…" / "I can know…" / "I can appreciate…" — these are not observable.
Do not write vague dispositional language for T1/T2 LTs.

### PROGRESSION LEVER

Name the operative lever(s) at each band transition. Choose from: independence, complexity, scope, precision, reasoning, transfer.

Explain in one phrase what changes: e.g. "Complexity: single trigger → multiple triggers" or "Transfer: practised contexts → novel situations under stress."

If the primary difference between two bands is harder content (topic escalation), this is a progression failure. Rewrite the band statements so the progression is in what students can do with content, not what content they cover.

### DISCIPLINARY WARRANT

One citation per Understand. Format: Author, A. A. (Year). Title. Publisher/Journal. This is the minimum — "informed educator level" is not sufficient. A teacher should be able to follow up the citation.

---

## STEP 3 — PREREQUISITE TYPING

For each prerequisite relationship identified (from {{prerequisite_lts}} or discovered during authoring), type it:

HARD — understanding B is logically impossible without A. The knowledge does not merely help — its absence makes the target content inaccessible. Warrants a readiness check before beginning. Example: evaluating health claims (T1) requires a working model of how the stress-response system operates — without the factual model, "evaluation" is guesswork.

SOFT ENABLER — understanding A enriches, accelerates, or deepens B, but B is reachable through other pathways including experiential and embodied ones. Do not gate assessment of the dependent LT because the enabler is not yet in place. Example: neuroscience of stress enriches self-regulation but a student can develop genuine self-regulation through practised strategies and adult co-regulation without understanding the amygdala.

CONCEPTUAL ACCELERATOR — A dramatically improves the portability and transferability of B to novel contexts. It teaches why the competency works, making it recognisable in new situations and teachable to others. Example: understanding conditioning mechanisms makes digital wellbeing strategies portable to any new platform or context, not just the ones practised in class.

Most knowledge-to-disposition relationships are soft enablers or conceptual accelerators. Do not designate a relationship as hard unless the logical dependency is genuine.

Record prerequisites in two places:
1. LT header: name the prerequisite LT by ID and type. e.g. "LT 6.1 — soft enabler (conceptual accelerator)"
2. KUD band level: flag where a specific K or U item at a specific band depends on another LT's content. e.g. "Band C U-layer: conceptual accelerator — LT 6.1 Band C in place makes this Understand portable; proceed without it if LT 6.1 Band C is not yet established."

---

## STEP 4 — QUALITY CHECKS

Run all six checks before producing final output. For each check, report PASS or FLAG. If FLAG: name the specific cell (e.g. "Band C, Understand") and state exactly what needs to change.

**Check 1 — Understand independence:** Is each Understand in a cell genuinely distinct from the Do in the same cell? Could a student read only the Do statement and derive the Understand without additional thinking? If yes: FLAG. Rewrite the Understand so it adds something the Do does not contain.

**Check 2 — Understand transfer:** Would a student who genuinely held each Understand behave differently in a novel situation they have not encountered before? If the Understand only applies in the context where it was learned: FLAG. Rewrite for genuine transfer.

**Check 3 — Know specificity:** Is each Know item a specific testable fact? Could you write a direct exam question from it? If it is a topic or theme: FLAG and decompose it into 2-4 specific facts in your output. Fix during this check — do not leave topic-level items in the output.

**Check 4 — Progression lever:** Is each band-to-band transition explicable by a named lever? If the only change between bands is harder content (more complex topics, higher reading level, more examples): FLAG as topic escalation. Rewrite so the progression is in what students can do with content.

**Check 5 — Compound knowledge-type:** Does this LT bundle T2 assessable analytical content with T3 dispositional content? The test: would the Do performance or observation adequately evidence the K/U content, or does the K/U content require a separate task format to be evidenced? Example: if the Do is a Socratic seminar contribution and the K/U content is factual recall of specific mechanisms, the seminar contribution does not adequately evidence the recall — FLAG for split. If the K/U content is enrichment that informs the disposition without requiring separate assessment — PASS.

**Check 6 — Know placement:** For LTs where Know lives in a designated knowledge competency by design — does any Know cell duplicate that competency's content rather than cross-reference it? If yes: FLAG and replace with the cross-reference.

---

## STEP 5 — INPUTS

- input_type: {{input_type}}
- primary_input: {{primary_input}}
- lt_name: {{lt_name}}
- lt_definition: {{lt_definition}}
- knowledge_type: {{knowledge_type}}
- band_scope: {{band_scope}}
- competency_context: {{competency_context}}
- crosswalk_data: {{crosswalk_data}}
- prerequisite_lts: {{prerequisite_lts}}
- programme_purpose: {{programme_purpose}}
- mode: {{mode}}

---

## SCHOOL-AGNOSTIC OUTPUTS

SCHOOL-AGNOSTIC OUTPUTS: Generated KUD charts must not reference any school-specific units, programmes, curriculum documents, or named courses. The skill works from the LT definition, band theory, and knowledge type classification only. If the operator has provided a school programme document as context, that document is background information for the operator's use — its content, unit names, and programme structures must not appear anywhere in the generated output. Any output referencing a named school unit or programme is invalid and must be regenerated without that reference.

---

## OUTPUT FORMAT

Return output in this structure:

**Routing note:** [null or recommendation text — always present]

---

## KUD Chart: [LT Name]

**LT Definition:** [one sentence, "I can…"]
**Knowledge Type:** [T1 / T2 / T3 — with one sentence reasoning]
**Do Evidence Type:** [Performance / Disposition / Mixed — with note if T3 exception applies]
**Band Scope:** [A–F or subset with N/A rationale]
**Prerequisites:** [LT ID — type (hard / soft enabler / conceptual accelerator) — one sentence rationale; or "None identified"]

| Band | Know | Understand | Do | Progression lever | Disciplinary warrant |
|---|---|---|---|---|---|
| A | | | | | |
| B | | | | | |
| C | | | | | |
| D | | | | | |
| E | | | | | |
| F | | | | | |

---

## Quality Check Results

Check 1 — Understand independence: [PASS / FLAG: cell + fix required]
Check 2 — Understand transfer: [PASS / FLAG: cell + fix required]
Check 3 — Know specificity: [PASS / FLAG: cell + decomposed facts]
Check 4 — Progression lever: [PASS / FLAG: cell + rewrite]
Check 5 — Compound knowledge-type: [PASS / FLAG: split test result]
Check 6 — Know placement: [PASS / FLAG: cell + cross-reference]

---

## Authoring Notes

[Decisions made during authoring requiring teacher review: ambiguous classification calls, cells where the warrant is thin, bands where progression logic is uncertain, any deviation from the brief.]

# 示例输出

**输入：** LT 1.3 — 个人身份与文化自我意识。`input_type`: existing_lt_with_do。知识类型：T3。能力：C1 — 情绪智力。按设计 Know 位于 C6。学段范围：A–F。项目目的：REAL School Budapest — 培养能够在跨文化语境中理解自我并在国际环境中驾驭身份认同的学习者。

**路由提示：** null

---

## KUD 图表：LT 1.3 — 个人身份与文化自我意识

**LT 定义：** 我能够清晰表达不断发展中的自我认知——包括我的价值观、优势与文化影响——并在不同情境与社群中保持这种身份认同的根基。
**知识类型：** T3 — 倾向型（Dispositional）。身份认同的形成是在跨情境的持续体验中发展起来的；没有任何单次场合能充分证明该能力。
**Do 证据类型：** 倾向（Disposition）。跨时间的可观察模式——教师观察跨情境的稳定性、对自我的好奇心以及扎实的投入。
**学段范围：** A–F
**先修要求：** LT 1.1 — 软性赋能（对情绪状态的自我觉察是身份反思的发展前驱；不作为评估门槛）

| 学段 | Know（知） | Understand（理） | Do（行） | 进阶杠杆 | 学科依据 |
|---|---|---|---|---|---|
| A | 知识内容位于 LT 6.1 | 我是一个独立的人——我有自己喜欢的事物、擅长的事情，以及对我重要的人。 | 学生能说出三件关于自己喜欢的事，并描述自己与同学之间的一处不同与一处相同。 | 基线（Baseline） | Wellman, H. M. (2002). Understanding the psychological world. In U. Goswami (Ed.), Blackwell Handbook of Childhood Cognitive Development. Blackwell. |
| B | 知识内容位于 LT 6.1 | 同一个“我”在不同地方会有不同表现——我在家、在学校和与朋友在一起时举止不同，但有些核心特质保持不变。 | 教师注意到学生在做选择时无需提示便能提及个人兴趣或价值观。学生能描述自己在两个不同场景中一处相同与一处不同的表现。 | 复杂性：单一情境自我 → 多情境自我 | Harter, S. (1999). The Construction of the Self. Guilford Press. |
| C | 知识内容位于 LT 6.1 | 我的成长背景和所属文化塑造了我注意什么、重视什么——而其他人的背景也塑造了他们注意什么、重视什么。 | 教师注意到学生对他人的文化背景如何塑造其视角表现出好奇心，主动提问而非先入为主臆断。 | 范围：自我理解 → 关系中的自我 | Markus, H. R. & Kitayama, S. (1991). Culture and the self: Implications for cognition, emotion, and motivation. Psychological Review, 98(2), 224–253. |
| D | 知识内容位于 LT 6.1 | 我的身份并非固定不变——它是我正在主动建构的东西，我对它拥有的能动性比我有时以为的更大。 | 教师注意到学生无需提示便能反思自己的自我认知如何发生变化，并说出促成这一变化的具体经历。 | 推理：察觉 → 分析身份发展 | Marcia, J. E. (1966). Development and validation of ego-identity status. Journal of Personality and Social Psychology, 3(5), 551–558. |
| E | 知识内容位于 LT 6.1 | 当文化期待与我自身的价值观发生冲突时，这种张力是真实的——诚实地驾驭这种张力而非压抑某一方，正是身份认同变得连贯的方式。 | 教师注意到学生能说出自己感受到的文化压力，并清晰表达自己如何决定保留什么、质疑什么，而无需依赖外部认可。 | 推理：分析 → 有原则地驾驭冲突 | Berry, J. W. (2005). Acculturation: Living successfully in two cultures. International Journal of Intercultural Relations, 29(6), 697–712. |
| F | 知识内容位于 LT 6.1 | 我是谁，一部分由我自己建构，一部分由我未曾选择的力量塑造——同时容纳这两重真相，正是成熟自我认知的体现。 | 教师注意到学生清晰表达出融合了个人历史、文化背景与自主选择价值观的连贯自我认知——并在面对真正陌生的新情境时运用这种连贯性。 | 迁移：熟悉情境 → 新颖情境；推理：分析 → 整合 | Kegan, R. (1994). In Over Our Heads: The Mental Demands of Modern Life. Harvard University Press. |

---

## 质量检查结果

检查 1 — Understand 独立性：通过（PASS）——每个 Understand 都增添了无法仅从 Do 推导出的洞见。
检查 2 — Understand 迁移性：通过（PASS）——每个 Understand 都会改变学生在新文化或社交情境中的行为。
检查 3 — Know 具体性：通过（PASS）——所有 Know 单元格均按设计交叉引用 C6；不存在主题级条目。
检查 4 — 进阶杠杆：通过（PASS）——基线 → 复杂性 → 范围 → 推理 → 推理 → 迁移。无主题升级现象。
检查 5 — 复合知识类型：通过（PASS）——K/U 内容丰富倾向型 Do；在本 LT 中不会为 K/U 内容单独布置量规任务。
检查 6 — Know 放置：通过（PASS）——所有 Know 单元格均交叉引用 LT 6.1 而非重复内容。

---

## 撰写说明

A 学段的 Do 写成了一个表现型要素（说出三件事、描述异同），而非纯观察指标，因为在 A 学段该倾向尚处于萌芽期，难以跨情境稳定观察——结构化活动在此发展阶段能产出更有效的证据。教师应审查这是否符合其评估实践。F 学段的 Understand 借鉴了 Kegan 的建构发展理论——教师应核实这是否与项目关于自我主导（self-authorship）的哲学立场一致。

# 已知局限

Understand 的质量检查是最难稳定通过的。一个 Understand 究竟是真正可迁移的，还是仅仅改写了 Do，这需要结合具体新情境做出判断——本技能的评估结果在采纳前应始终由教师审查。教过该能力多年的教师，往往比任何自动化检查更能直觉判断哪些 Understand 真正具有迁移价值。

路由检查会生成提示，但从不阻塞执行。这意味着在复杂原始课程文档上运行本技能时，产出的草稿在 Know 具体性与进阶连贯性方面会弱于基于结构化 harness 输出运行的结果。撰写说明会标出这一点，但教师不应在未经额外审查的情况下直接将原始文档直出草稿当作最终成品。

先修关系分类基于本技能从所提供输入中评估出的内容逻辑结构。了解学生群体并在实践中观察过先修漏洞的教师，比本技能更清楚某项关系在特定情境下究竟是作为硬性门槛还是软性赋能起作用。

对于带有表现型表达的部分 T3 LT（例如在多次场合中培养的演讲技能），表现型 vs. 倾向型的区分需要教师判断：所培养的能力究竟主要是一种可在单次充分准备的表现中取证的技能，还是一种需要跨未准备真实场合累积证据的倾向。当出现此类模糊性时，本技能会在撰写说明中予以标明。
