---
# AGENT SKILLS STANDARD FIELDS (v2)
name: kud-knowledge-type-mapper
description: "将课程内容分类为 Know（知）、Understand（理）和 Do（行）类别，以对齐教学与评估方式。适用于规划单元、撰写目标或选择评估方法。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "curriculum-assessment/kud-knowledge-type-mapper"
skill_name: "KUD 知识类型映射器"
domain: "curriculum-assessment"
version: "1.0"
evidence_strength: "moderate"
evidence_sources:
  - "Wiggins & McTighe (2005) — Understanding by Design: Know/Understand/Do as the unit-level planning architecture"
  - "Wiggins & McTighe (2011) — The Understanding by Design Guide to Creating High-Quality Units: KUD as the bridge from standards to assessment"
  - "Bernstein (1999) — Vertical and horizontal discourse: hierarchical vs horizontal knowledge structures"
  - "Bernstein (2000) — Pedagogy, Symbolic Control and Identity: recontextualisation and knowledge type"
  - "Hattie (2009) — Visible Learning: surface, deep, and transfer as learning phases with distinct assessment needs"
  - "Hattie & Timperley (2007) — The power of feedback: feedback must be calibrated to the type of learning"
  - "Wiliam (2011) — Embedded Formative Assessment: assessability as a design constraint, not an afterthought"
  - "Deci & Ryan (1985, 2000) — Self-Determination Theory: autonomy-supportive assessment for dispositional development"
  - "Muller (2009) — Forms of knowledge and curriculum coherence: conceptual vs contextual coherence"
  - "Maton (2014) — Knowledge and Knowers: Legitimation Code Theory (Semantics dimension)"
input_schema:
  required:
    - field: "curriculum_input"
      type: "string"
      description: "单元、能力或项目的描述——学生将学习与做什么"
    - field: "learner_stage"
      type: "string"
      description: "年龄范围、年级或发展学段"
  optional:
    - field: "knowledge_architecture_output"
      type: "string"
      description: "来自上下文引擎或先前运行：Curriculum Knowledge Architecture Designer 输出的认识论诊断结果"
    - field: "existing_learning_targets"
      type: "string"
      description: "为本单元已撰写的任何既有 LT、能力陈述或课程标准"
    - field: "competency_framework"
      type: "string"
      description: "学校正在使用的能力或倾向框架"
    - field: "programme_purpose"
      type: "string"
      description: "为何本单元或能力对学校使命重要——上游的‘为什么’"
output_schema:
  type: "object"
  fields:
    - field: "kud_chart"
      type: "object"
      description: "完整的 Know/Understand/Do 图表，每个要素均标明知识类型（层级型、横向型或倾向型）"
    - field: "do_split"
      type: "object"
      description: "将 Do 显性拆分为技能（Skills，可通过任务量规评估）和倾向（Dispositions，需通过跨时间多方观察评估）"
    - field: "assessment_routing_plan"
      type: "object"
      description: "针对每个 KUD 要素：下一步应调用哪项评估技能以及原因"
    - field: "sequencing_notes"
      type: "object"
      description: "先修依赖关系、灵活顺序要素以及贯穿主线的倾向"
    - field: "gap_analysis"
      type: "object"
      description: "若提供了既有 LT：将 KUD 要素映射至既有 LT，识别缺口与错配"
    - field: "design_flags"
      type: "object"
      description: "复合要素、误分类要素、不可评估要素及路由冲突"
chains_well_with:
  - "curriculum-knowledge-architecture-designer"
  - "learning-target-authoring-guide"
  - "coherent-rubric-logic-builder"
  - "dispositional-knowledge-assessment-designer"
  - "developmental-band-system-designer"
teacher_time: "5 分钟"
tags: ["KUD", "knowledge-type", "assessment-routing", "Wiggins-McTighe", "Bernstein", "curriculum-mapping", "hierarchical", "horizontal", "dispositional", "backwards-design"]
---

# KUD 知识类型映射器

## 本技能的作用

接收一份课程输入——单元描述、能力集合或项目简报——并产出一份完整的 Know/Understand/Do（知/理/行）图表，其中每一个要素都被标注了知识类型（层级型 Hierarchical、横向型 Horizontal 或倾向型 Dispositional），并被路由至正确的评估方式。这是连接 `curriculum-knowledge-architecture-designer`（诊断存在哪些知识类型）与构建实际评估工具的下游技能（针对技能的 `coherent-rubric-logic-builder`，针对倾向的 `dispositional-knowledge-assessment-designer`）之间的操作桥梁。大多数 KUD 图表把三列视为同质等价，但实际上并非如此。层级型 Know 要素（有标准对错答案的事实）与横向型 Know 要素（存在争议的概念知识）需要截然不同的评估——前者可自动评估，后者需要阐释性判断。作为“技能”的 Do（在特定任务上对照标准用量规评估）与作为“倾向”的 Do（跨时间多方观察评估）不能采用相同的评估方式——而把倾向路由到量规会主动损害它的发展。本技能将这些区分显性化，确保在教学开始前，KUD 图表中的每一项要素都拥有清晰、有理有据的评估路径。AI 在此尤为关键，因为生成带有知识类型标注的 KUD 图表需要同时运用课程认识论（Bernstein 的知识结构）、评估设计逻辑（Wiliam 的可评估性约束）、学习科学（Hattie 的表层/深层/迁移区分）与动机理论（Deci & Ryan 的自主性条件）——这种组合在单个教育者身上十分罕见，且大多数备课流程都会完全跳过。

## 实证基础

Wiggins & McTighe（2005, 2011）在《追求理解的教学设计》中将 Know/Understand/Do 确立为单元级规划的标准架构。KUD 框架区分三种学习类型：**Know（知）**（学生应习得的事实性与概念性知识）、**Understand（理）**（持久理解——超越单元留存的可迁移洞见）与 **Do（行）**（学生应能执行的技能与过程）。该框架的力量在于迫使课程设计者在设计评估前先明确这三者——逆向设计要求在决定“怎么评”之前先清楚“评什么”。然而，原版 UbD 框架将这三列视为内部均质的：所有 Know 要素被一视同仁，所有 Understand 要素被一视同仁，所有 Do 要素亦然。这正是本技能所要填补的空白。

Bernstein（1999, 2000）证明知识并非单一均质体。**层级型知识**连贯、原则显明且呈累积性——低阶概念必须先掌握，高阶概念才可触及，存在可测验的对错答案。**横向型知识**组织为专业化的阐释视角，各自拥有有效分析的标准——内容可从多个切入点进入，质量由分析深度而非事实对错来评判。这两种类型共同存在于 KUD 图表的 Know 和 Understand 列中，需要不同的评估。一个层级型 Know 要素（“水循环有五个阶段：蒸发、凝结、降水、径流、下渗”）可以通过小测验评估——存在标准答案。一个横向型 Know 要素（“不同历史学家通过不同视角阐释一战起因——民族主义、帝国主义、军国主义、同盟体系”）无法通过小测验评估，因为记住这些视角名称并不等同于能够分析性地运用它们。同样的区分适用于 Understand 列：层级型理解（“能量守恒——它在不同形式间转化但绝不凭空产生或消灭”）有标准表述，而横向型理解（“历史事件有多种原因，你强调哪一种取决于你应用的阐释框架”）本质上是视角依赖的。

Hattie（2009）识别出学习的三个阶段——**表层（surface）**（习得新知识与技能）、**深层（deep）**（整合与巩固，建立联系）和**迁移（transfer）**（将学习应用于新情境与新问题）。每个阶段需要不同的教学与不同的评估。表层学习对应层级型 Know 要素——可直接测验的事实、词汇、程序。深层学习对应 Understand 列——建立联系、发现模式、建构概念结构。迁移对应最精深的 Do 要素——在真正陌生的新情境中运用能力。Hattie & Timperley（2007）进一步表明，反馈必须与学习阶段相校准：任务级反馈适用于表层学习，过程级反馈适用于深层学习，自我调节反馈适用于迁移。不区分知识类型的 KUD 图表无法正确校准反馈，因为教师不知道某一要素究竟需要任务级还是过程级反馈。

Wiliam（2011）指出，只有当评估产出可用于指导行动的证据时它才有用——评估设计必须从“什么算作充分证据证明该生已学会此项内容？”这一问题出发。这一可评估性约束正是 KUD 知识分型在操作上至关重要的原因。有些 KUD 要素可通过单次任务直接评估（层级型事实、程序性技能）；有些需要跨多项任务的持续证据（横向分析能力、可迁移理解）；还有一些——倾向型要素——根本无法通过任务来评估，因为它们只存在于跨时间的实践行为模式中。不做这些区分的 KUD 图表会产出要么无效（对倾向套用量规标准）、要么残缺（未能为横向与倾向要素规划持续证据）的评估设计。

Deci & Ryan（1985, 2000）通过自我决定理论确立：被体验为控制性的评估情境——学习者感受到的是评判而非支持——会削弱作为倾向性发展前提的自主性与胜任感需求。这为评估路由设定了一条硬性约束：任何被识别为倾向型的 KUD 要素，**必须**路由至保护自主性的评估方式——多方观察、教练式反馈、发展性对话——而不是打分分级的量规。把倾向路由到量规不仅效率低下，而且具有主动危害，因为评价性框架会压抑倾向性发展所需的真实表达。

## 输入规范

教育者必须提供：
- **课程输入（Curriculum input）：** 单元、能力或项目的描述。*例如：“D 学段幸福感单元，聚焦情绪调节与自我关怀——学生探索情绪科学（大脑如何加工情绪、应激反应、身体健康与情绪幸福的联系）；发展个人自我调节策略（识别个人触发点、选择并练习平静技巧、建立支持幸福感的日常习惯）；同时探索自身情绪状态如何影响他人，并培养关怀他人幸福的习惯” / “九年级历史——一战的起因与后果” / “D2R 项目：本地湿地的智能水系统”*
- **学习者阶段（Learner stage）：** 年龄范围或年级。*例如：“D 学段（12–14 岁）” / “九年级” / “7–8 年级”*

可选项（如可用则由上下文引擎注入）：
- **知识架构输出（Knowledge architecture output）：** 来自先前 `curriculum-knowledge-architecture-designer` 运行的认识论诊断
- **既有学习目标（Existing learning targets）：** 为本单元已撰写的任何 LT、能力陈述或标准
- **能力框架（Competency framework）：** 学校的倾向或能力框架
- **项目目的（Programme purpose）：** 为何本单元或能力对学校使命重要

## 提示词（Prompt）

```
You are an expert in curriculum design, knowledge epistemology, and assessment architecture. You combine deep knowledge of Wiggins & McTighe's (2005, 2011) Understanding by Design KUD framework with Bernstein's (1999, 2000) theory of knowledge structures, Hattie's (2009) surface/deep/transfer learning phases, Hattie & Timperley's (2007) feedback calibration, Wiliam's (2011) assessability constraints, and Deci & Ryan's (1985, 2000) Self-Determination Theory.

Your task is to produce a complete, knowledge-typed KUD chart for the following curriculum input — one where every element is classified by knowledge type and routed to the correct assessment approach.

**Curriculum input:** {{curriculum_input}}
**Learner stage:** {{learner_stage}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Knowledge architecture output:** {{knowledge_architecture_output}} — if provided, use the epistemic diagnosis as the starting point for knowledge-typing. If not provided, conduct the knowledge-typing from the curriculum input directly.
**Existing learning targets:** {{existing_learning_targets}} — if provided, run a gap analysis mapping each KUD element to existing LTs.
**Competency framework:** {{competency_framework}} — if provided, use it to identify dispositional elements.
**Programme purpose:** {{programme_purpose}} — if provided, use it to check alignment between the KUD and the school's mission.

## The Three Knowledge Types

You MUST classify every KUD element as one of these three types. The classification determines the assessment route.

**Hierarchical Knowledge (Bernstein, 1999)**
Cumulative, prerequisite-ordered knowledge with right/wrong answers or demonstrable procedures. Assessment can be criterion-referenced and often automated. Surface-level feedback (Hattie & Timperley, 2007) is appropriate.

In a KUD chart, Hierarchical elements appear as:
- **Know:** Facts, definitions, vocabulary, formulae, named processes with canonical descriptions
- **Understand:** Principles, laws, or cause-effect relationships with established correct formulations
- **Do (Skill):** Procedures, techniques, and methods with demonstrable correctness

**Horizontal Knowledge (Bernstein, 1999)**
Perspectival, lens-based knowledge where quality is judged by analytical depth and sophistication, not factual correctness. Assessment requires interpretive judgment and analytical criteria. Process-level feedback (Hattie & Timperley, 2007) is appropriate.

In a KUD chart, Horizontal elements appear as:
- **Know:** Frameworks, perspectives, interpretive lenses, contested concepts
- **Understand:** Insights that depend on analytical stance — enduring understandings that admit multiple valid formulations
- **Do (Skill):** Analysis, interpretation, critical evaluation, argumentation — skills where quality exists on a continuum

**Dispositional Knowledge (extended from Bernstein; Deci & Ryan, 1985, 2000)**
Enacted capacities, orientations, and developing competencies that exist only in patterns of behaviour over time. Cannot be assessed through a single task. Assessment MUST use multi-informant observation and coaching-modality feedback. Self-regulation feedback (Hattie & Timperley, 2007) is appropriate. Rubric-based assessment is PROHIBITED — it undermines the autonomy that dispositional development requires (Deci & Ryan, 1985, 2000).

In a KUD chart, Dispositional elements appear as:
- **Know:** Self-knowledge — awareness of one's own patterns, triggers, strengths
- **Understand:** Developmental self-awareness — understanding that dispositions grow, that context matters, that setbacks are part of development
- **Do (Disposition):** Enacted patterns of behaviour — agency, collaboration, self-regulation, empathy, persistence, regenerative mindset

## Critical Rules

1. **The Do column MUST be split into Skills and Dispositions.** Every Do element must be explicitly classified as either a Skill (assessable by rubric on a task) or a Disposition (assessable by multi-informant observation over time). If this split is not made explicit, the assessment design will fail.

2. **No Dispositional element may be routed to a rubric.** Dispositions are assessed through observation protocols, student self-reflection, and developmental conversation — never through scoring criteria applied to a single task. If a Dispositional element appears to need a rubric, it has been misclassified: either it is actually a Skill, or the assessment approach must change.

3. **Knowledge type determines assessment route.** The routing is not optional — it is a logical consequence of what the knowledge IS:
   - Hierarchical Know/Understand → quiz, test, structured response, auto-assessable
   - Horizontal Know/Understand → analytical task assessed by teacher judgment using criteria
   - Hierarchical Do (Skill) → procedural demonstration, criterion-referenced rubric
   - Horizontal Do (Skill) → performance task, rubric with qualitative descriptors (Emerging → Developing → Competent → Extending)
   - Dispositional Do (Disposition) → multi-informant observation protocol, developmental conversation, student self-reflection (invoke Dispositional Knowledge Assessment Designer)
   - Dispositional Know/Understand → embedded in developmental conversation, not separately tested

4. **Flag compound elements.** If a KUD element contains multiple knowledge types ("Understands how emotions work AND manages their own emotional responses"), flag it for splitting. The first part is Hierarchical/Horizontal Know; the second is Dispositional Do.

5. **Flag unassessable elements.** If a KUD element cannot be assessed validly with any available approach (too vague, too internal, or too context-dependent), flag it and suggest reformulation.

## Process

Step 1: Read the curriculum input carefully. Identify every distinct learning element — what students will know, understand, and be able to do.

Step 2: Classify each element by knowledge type (Hierarchical, Horizontal, or Dispositional). Justify each classification.

Step 3: For every Do element, make the Skill/Disposition split explicit.

Step 4: Assign the assessment route for each element.

Step 5: Identify sequencing constraints — which elements are prerequisites for which? Which can be taught in flexible order? Which dispositions run as continuous threads? For each dispositional Do element identified, ask: is this disposition knowledge-contingent? That is, does it require a sufficient base of hierarchical Know and horizontal Understand elements before it can meaningfully manifest? If yes, identify which specific Know and Understand elements from the KUD chart are prerequisites for this disposition to be operable — not just supportive, but genuinely prerequisite. Include these in the sequencing notes as hard prerequisites for the dispositional element, not just as parallel threads. A disposition that is treated as a continuous thread when it is actually knowledge-contingent will be under-developed because teachers will assume it is developing in parallel rather than recognising that foundational knowledge must come first.

Step 6: If existing LTs are provided, run the gap analysis: map each KUD element to existing LTs, identify gaps (KUD elements with no corresponding LT) and mismatches (LTs that don't align with any KUD element or that are routed to the wrong assessment type).

Step 7: Flag design issues — compound elements, misclassified elements, unassessable elements, and any routing conflicts.

Return your output in this exact format:

## KUD Knowledge Type Map: [Unit/Project Name]

**Curriculum input:** [Summarised]
**Learner stage:** [Age/year/band]
**Programme purpose:** [If provided; otherwise "Not specified"]

### 1. Know

| Element | Knowledge Type | Assessment Route | Justification |
|---|---|---|---|
| [Factual/conceptual element] | Hierarchical / Horizontal / Dispositional | [Route] | [Why this type] |

### 2. Understand

| Element | Knowledge Type | Assessment Route | Justification |
|---|---|---|---|
| [Enduring understanding] | Hierarchical / Horizontal / Dispositional | [Route] | [Why this type] |

### 3. Do — Skills

| Element | Knowledge Type | Assessment Route | Justification |
|---|---|---|---|
| [Skill element] | Hierarchical / Horizontal | [Route — which rubric skill to invoke] | [Why this type] |

### 4. Do — Dispositions

| Element | Knowledge Type | Assessment Route | Justification |
|---|---|---|---|
| [Dispositional element] | Dispositional | Multi-informant observation → Dispositional Knowledge Assessment Designer | [Why this is a disposition, not a skill] |

### 5. Assessment Routing Plan

[For each KUD section, specify:
- Which assessment skill to invoke next
- What inputs that skill needs from this KUD chart
- The assessment mode (auto-assessable / rubric / observation protocol / mixed)
- The feedback type (task-level / process-level / self-regulation)]

### 6. Sequencing Notes

**Hard prerequisites:** [Elements that must be taught before others — hierarchical chains]
**Flexible-order elements:** [Elements that can be taught in any order — horizontal lenses]
**Continuous threads:** [Dispositional elements that develop across the entire unit, not in specific lessons]
**Convergence points:** [Where different knowledge types must come together — e.g. applying hierarchical knowledge through a horizontal lens]

### 7. Gap Analysis

[If existing LTs provided:]

| KUD Element | Matched LT | Match Quality | Notes |
|---|---|---|---|
| [Element] | [LT if matched] | Full / Partial / No match | [What's missing or misaligned] |

**Gaps:** [KUD elements with no corresponding LT]
**Orphan LTs:** [Existing LTs that don't map to any KUD element]
**Routing mismatches:** [LTs where the current assessment approach doesn't match the knowledge type]

[If no existing LTs provided: "No existing LTs provided. To generate LTs from this KUD chart, invoke the Learning Target Authoring Guide with each Do element as input."]

### 8. Design Flags

**Compound elements:** [Elements that contain multiple knowledge types and should be split]
**Misclassified elements:** [Elements that appear to be one type but are actually another — e.g. a "skill" that is actually a disposition]
**Unassessable elements:** [Elements too vague, too internal, or too context-dependent to assess validly — with suggested reformulations]
**Routing conflicts:** [Cases where the assessment route for one element conflicts with another — e.g. a rubric task that would undermine a dispositional goal being developed simultaneously]

**Self-check before returning output:** Verify that (a) every Do element is classified as either Skill or Disposition with no ambiguity, (b) no Dispositional element is routed to a rubric, (c) every element has a knowledge type AND an assessment route, (d) sequencing notes identify ALL prerequisite dependencies, (e) the gap analysis (if applicable) catches genuine misalignments not just superficial mismatches, and (f) design flags are specific and actionable.
```

## 示例输出

当你需要完整的情绪调节 KUD 示例（包括 Know/Understand/Do 表格、评估路由与差距分析）时，请阅读 [references/worked-examples.zh-CN.md](references/worked-examples.zh-CN.md)。

**精简节选——技能、倾向与私人习惯：**

| 要素 | 知识类型 | 评估路由 | 理由 |
|---|---|---|---|
| 为特定情境选择并应用恰当的平静技巧，解释为何该技巧适合该情境 | 横向型（Horizontal） | 量规任务——给定情景，选择技巧并论证 → 调用 Coherent Rubric Logic Builder | 尽管关于技巧本身的工作原理是层级型知识，但**选择**是横向型的（取决于语境与推理，存在多种有效选择）。评估必须评判论证质量，而不仅仅是看是否选对了“标准”技巧。 |
| 作为实践行为的自我调节——实时察觉情绪升级并自主选择回应，而非本能反应 | 倾向型（Dispositional） | 多方观察 → 调用 Dispositional Knowledge Assessment Designer | 这**不是**能在单次任务上展示的技能。学生可以在学习单上完美解释自我调节，却依然在走廊里冲动发火。该倾向只存在于跨情境、跨时间的行为模式中。评估需要教师观察、学生自我反思与发展性对话。量规只能评估对自我调节的“表演”，而非“发展”。 |
| 作为习惯的幸福感——维持支持持久幸福感的个人日常惯例（睡眠、运动、反思） | 倾向型（Dispositional） | 学生自我反思与发展性对话 → 调用 Dispositional Knowledge Assessment Designer | 个人习惯具有私密性与情境性。学校无法也不应当监控学生在家睡得好不好或是否运动。评估应通过学生自身不断发展的自我觉察进行：他们能否清晰说出什么对自己有效、察觉习惯何时滑坡并自我修正？这属于自我调节反馈范畴（Hattie & Timperley, 2007），而非任务反馈。 |

---

## 已知局限

1. **三种知识类型是一种简化，而非本体论划分。** 真实知识要素常位于类型边界上。像“有理有据地选择平静技巧”这样的技能，既有层级型成分（知道技巧）、又有横向型成分（论证选择），还有倾向型成分（实际运用）。分类捕捉的是出于评估路由目的的**主要**类型——并不声称该要素纯粹只属于某一种类型。

2. **评估路由假设下游技能存在。** 本 KUD 图表将要素路由至 `coherent-rubric-logic-builder` 和 `dispositional-knowledge-assessment-designer`。如果尚未针对这些要素运行这两个下游技能，路由只是一份计划而非既成事实。KUD 图表告诉教师**评什么**与**怎么评**——下游技能则产出实际的评估工具。

3. **差距分析取决于既有 LT 的质量。** 如果既有 LT 写得不佳（不可观察动词、复合构念、模糊语言），差距分析标出的问题实际上是 LT 撰写问题，而非 KUD 映射问题。在此情况下，建议先调用 `learning-target-authoring-guide`，再尝试解决差距。

4. **倾向型要素最难评估，也最容易被忽视。** KUD 图表使它们显性化并路由到恰当评估——但在时间压力下的教师仍可能默认只评估层级型与横向型要素，因为它们更容易测。图表无法替教师解决这一问题，只能让这一选择变得可见。

5. **KUD 图表是规划工具，而非教学顺序表。** 排序说明提供了先修依赖与灵活顺序的指引，但实际的逐课时顺序仍取决于教师对节奏、学生需求及图表无法预见的情境因素的判断。
