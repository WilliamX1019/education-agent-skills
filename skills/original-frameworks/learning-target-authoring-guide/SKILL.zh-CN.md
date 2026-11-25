---
# AGENT SKILLS STANDARD FIELDS (v2)
name: learning-target-authoring-guide
description: "以精确、可观察的进阶语言跨发展阶段撰写某一能力的学习目标。适用于为基于能力的项目撰写“我能够（I can）”陈述。"
disable-model-invocation: true
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "original-frameworks/learning-target-authoring-guide"
skill_name: "使命驱动的学习目标撰写指南"
domain: "original-frameworks"
version: "2.0"
evidence_strength: "emerging"
evidence_sources:
  - "Manning — Learning Target Authoring Guide v4.0 (2026, original methodology)"
  - "Black & Wiliam (1998) — Assessment and classroom learning (clear learning intentions as prerequisite for formative assessment)"
  - "Wiggins & McTighe (2005) — Understanding by Design (backwards design, extended with Manning's upstream 'why' layer)"
  - "Bloom et al. (1956) — Taxonomy of educational objectives (observable verb hierarchy)"
  - "Vygotsky (1978) — Mind in society (ZPD — band statements specify upper edge of capability with support)"
input_schema:
  required:
    - field: "competency_name"
      type: "string"
      description: "正在被拆解为学习目标的宽泛能力"
    - field: "competency_definition"
      type: "string"
      description: "以“The ability to...（……的能力）”开头的一句话"
    - field: "band_range"
      type: "string"
      description: "该学习目标集覆盖的发展阶段范围——例如 A–D 阶段或 A–F 阶段"
    - field: "programme_purpose"
      type: "string"
      description: "为什么这项能力对本校使命至关重要——上游的“为什么”"
  optional:
    - field: "existing_draft"
      type: "string"
      description: "需要审阅并修订的任何现有学习目标措辞"
    - field: "subject_area"
      type: "string"
      description: "课程领域"
    - field: "assessment_context"
      type: "string"
      description: "学习目标将如何使用——汇报、项目评估或两者兼有"
output_schema:
  type: "object"
  fields:
    - field: "competency_review"
      type: "object"
      description: "这项能力是否恰当？是否服务于使命？它是真正的能力还是伪装的主题清单？"
    - field: "knowledge_type_classification"
      type: "object"
      description: "第0步：将每个浮现的学习目标分支分类为类型 1（层级性）、类型 2（水平/推理性）或类型 3（倾向性/践行性），附评估路径分配与复合知识类型检查"
    - field: "lt_decomposition"
      type: "object"
      description: "使能力可操作的 2–3 个学习目标，附每项的学理依据——包括必要时的知识类型拆分"
    - field: "lt_definitions"
      type: "object"
      description: "每个学习目标的一句话“我能够……”定义，附知识类型、评估路径与前置条件字段"
    - field: "band_statements_or_observation_indicators"
      type: "object"
      description: "类型 1 与类型 2：完整的 A–F 阶段陈述进阶。类型 3：各阶段的观察指标集（无量规）"
    - field: "quality_check"
      type: "object"
      description: "完整 v4.0 核对清单——单一构念、复合知识类型、无行内示例、可观察动词、纵向连贯性、横向连贯性、知识类型检查、评估路径核验"
    - field: "known_limitations"
      type: "object"
      description: "该学习目标集在何处最强；在何处仍需教师判断"
chains_well_with:
  - "developmental-band-system-designer"
  - "coherent-rubric-logic-builder"
  - "self-determined-project-design-protocol"
  - "curriculum-knowledge-architecture-designer"
  - "kud-knowledge-type-mapper"
  - "critical-thinking-task-designer"
  - "dispositional-knowledge-assessment-designer"
teacher_time: "5 分钟"
tags: ["learning-targets", "Manning", "competency", "authoring", "backwards-design", "observable-verbs", "band-statements", "progression", "knowledge-type", "observation-indicators", "Type-3", "multi-informant"]
---

# 使命驱动的学习目标撰写指南

## 本技能的功能

本技能编码了由教育者、课程设计师及学习系统设计师 Gareth Manning 开发的原创实践者框架。与其他领域的技能不同，它并非源自同行评审研究传统，而是植根于对学习科学的深入研习、原创课程设计工作以及一线课堂测试。将其纳入本库，是因为该方法论逻辑连贯、可迁移且真正实用——同时出于学术诚实，需将实践者框架与经研究验证的方法加以区分。

本技能引导教育者或课程设计师为某项能力撰写一套完整、连贯的学习目标（LTs）——从上游追问该能力本身是否恰当出发，经过知识类型分类、拆解为 2–3 个学习目标，直到撰写出具有发展性、精确且可评估的阶段层面陈述（类型 1 与类型 2）或观察指标集（类型 3）。学习目标是连接宽泛能力（如“批判性思维”）与教师在学生作品中实际可观察、可评估表现之间的桥梁。若没有撰写良好的学习目标，基于能力的教育就会退化为要么模糊的印象，要么清单式的任务打卡。v4.0 方法论引入了一个强制性的分类步骤——**知识类型（Knowledge Type）**——它在撰写任何阶段陈述**之前**就决定了评估工具。这解决了基于能力的幸福感课程与项目式课程中最常见的单一失效模式：通过量规来评估倾向性目标，制造出有测量的幻觉却缺乏实质内容。产出是一套可直接用于规划与汇报的完整学习目标集，流程中内置了质量检查。该方法论汲取自 Black 与 Wiliam（1998）——清晰的学习意图是有效形成性评估的前提——并用 Manning 的上游“为什么”层级拓展了 Wiggins 与 McTighe（2005）的逆向设计：在问“学生应该学什么？”之前，流程先问“为什么这项能力对我们的使命至关重要？”

关键区分：学习目标（LT）描述的是**目的地**，而非**内容**。阶段陈述描述的是学生在某一发展周期结束时能做什么——它并不规定为了到达那里教什么内容。内容特异性存在于 KUD 图表与单元计划中。LT 约束的是“评估什么”；它不约束“教什么”。一个看似未指定具体内容的 LT 正是运作正常的体现——KUD 图表才是让内容显性化的恰当位置。

## 循证基础

Manning 通过迭代课程设计开发了《学习目标撰写指南》，记录于 v4.0（2026）版本中。该方法论旨在解决一个具体难题：大多数基于能力的课程都有撰写糟糕的学习目标。常见失效模式包括：使用不可观察动词的目标（“理解水循环”——你如何观察“理解”？）；伪装成能力的主题清单（“知道一战的起因”——这是内容，不是能力）；缺乏发展进阶的目标（每个阶段都是同一句话，只是硬加上“简单”和“复杂”）；同时评估多件事的复合目标（“分析并评估来源以构建论证”——学生究竟在哪个部分吃力？）；以及——最隐蔽的——通过量规评估倾向性目标（在情景任务上用量规打分无法告诉你学生是否发展出了该倾向，只能告诉你他们被要求时能否“表演”出来）。Black 与 Wiliam（1998）确立了有效的形成性评估需要清晰、共享的学习意图。如果教师自己都不清楚究竟在寻找什么，就无法提供有用反馈，学生也无法自我评估。LT 正是清晰度的基本单位：具体到足以评估，宽泛到足以跨多个项目与情境应用。Wiggins 与 McTighe（2005）提供了逆向设计框架，Manning 通过增加上游“为什么”层级对其进行了拓展。标准 UbD 从既定课程目标开始；使命驱动的逆向设计从学校使命开始并追问：为什么这项能力存在于我们的课程中？如果我们删掉它会失去什么？这种上游追问防止了课程中堆满“谁也说不清为什么保留但谁也不敢删”的能力。布鲁姆分类学（1956，2001年修订）提供了约束 LT 撰写的动词层级：可观察、可评估的动词（识别、描述、比较、解释、论证、分析、评估、创造）取代了不可观察的动词（理解、知道、欣赏、意识到）。Vygotsky（1978）的最近发展区（ZPD）为阶段层面界定提供了依据：每条阶段陈述描述的是学生在该发展阶段**在适当支持下**能做到的事——即 ZPD 的上沿。

## 输入模式

教育者必须提供：
- **能力名称：** 宽泛的能力。*例如：“批判性思维” / “科学探究” / “协作问题解决” / “自我调节”*
- **能力定义：** 一句话。*例如：“分析信息、评估证据并构建有理有据论证的能力” / “跨不同情境监控并调整自身情绪与行为反应的能力”*
- **阶段范围：** 涵盖哪些阶段。*例如：“A–D 阶段（5–14岁）” / “B–D 阶段（8–14岁）” / “A–C 阶段（5–12岁）”*
- **项目宗旨：** 为什么这项能力至关重要。*例如：“我们的使命要求学生能够为需要他们的世界做出贡献——做出贡献需要批判性地思考复杂问题的能力，而不仅仅是全盘接受别人告诉他们的东西”*

可选（如有，由上下文引擎注入）：
- **现有初稿：** 需要修订的任何当前 LT 措辞
- **学科领域：** 课程领域
- **评估情境：** LT 将如何使用

## 提示词

````
You are authoring learning targets using Gareth Manning's methodology (Learning Target Authoring Guide v4.0). You must follow these rules PRECISELY — they are the quality standard for every LT produced.

═══════════════════════════════════════════════════════════════
STEP 0: KNOWLEDGE TYPE CLASSIFICATION (mandatory first step)
═══════════════════════════════════════════════════════════════

Before decomposition. Before writing band statements. Before anything else.

Every LT must be classified as one of three knowledge types. The classification determines the assessment instrument. Writing the LT before classifying it produces the single most common failure mode in competency-based wellbeing and project curricula: dispositional goals assessed through rubrics, creating the illusion of measurement without the substance.

THE THREE TYPES:

**Type 1 — Hierarchical Knowledge.** Concepts build on each other in a fixed sequence. Missing a prerequisite makes later content inaccessible, not merely harder.
- Indicators: prerequisite chains exist; errors at lower levels propagate upward; canonical sequencing logic; content cannot be reordered without loss.
- Assessment route: rubric with clear criteria, explanation tasks, vocabulary checks, knowledge tests.

**Type 2 — Horizontal Knowledge.** Organised around a central question or situation, illuminated through multiple disciplinary lenses. No single correct answer, but better and worse analyses. What develops cumulatively is not content but thinking sophistication.
- Indicators: multiple valid interpretive frameworks exist; reasoning quality determines assessment outcome; content can be entered from different points; analytical depth increases with experience.
- Assessment route: reasoning-quality rubric, scenario analysis, roleplay with novel situations, case studies, written analytical tasks. Transfer is the test.

**Type 3 — Dispositional Knowledge.** Capacities that develop gradually through sustained experience and exist only in enactment. Cannot be assessed through a single task. A rubric scored on a scenario task does not tell you whether a student has developed the disposition — it tells you whether they can perform it when asked.
- Indicators: the quality exists only across time and contexts; observation of the real behaviour (not a simulation) is required for valid evidence.
- Assessment route: multi-informant, longitudinal — teacher observation notes, student self-reflection, optional parent input, Strive data where applicable. Synthesised in developmental conversation. NOT a summative grade. NO RUBRIC.

CLASSIFICATION DECISION TREE — apply to EVERY emerging LT strand:

1. Does this LT describe content with a hard prerequisite sequence?
   YES → Type 1. Assessment: rubric / knowledge test.

2. Does this LT describe analytical or reasoning capability across multiple lenses?
   YES → Type 2. Assessment: reasoning-quality rubric, scenario task.

3. Does this LT describe a quality that only exists as it is enacted over time?
   YES → Type 3. Assessment: multi-informant observation. NO RUBRIC.

4. Does the statement contain elements from more than one type?
   YES → COMPOUND. Split before proceeding. Type 3 elements always go to the multi-informant observation pathway. Type 1 and Type 2 elements go to the rubric pathway. Each pathway has a separate LT.

5. Is this Type 3 LT dependent on Type 1 or Type 2 knowledge being in place first?
   YES → Knowledge-contingent. Name the prerequisite LTs explicitly.

KNOWLEDGE-CONTINGENT DISPOSITIONS:
A Type 3 disposition is knowledge-contingent when the student cannot develop the capacity without first having the Type 1 or Type 2 knowledge base in place. This is a sequencing requirement, not a design flaw.

Example: Self-regulation is knowledge-contingent. A student cannot genuinely develop self-regulation strategies without first understanding what the stress response is (Type 1), and without having practised a repertoire of regulation strategies in structured situations (Type 2). The Type 3 observation is only valid evidence once the prerequisites are established.

Design rule: If an LT is Type 3 and knowledge-contingent, name the prerequisite LTs explicitly. Do not expect the disposition to develop before the prerequisites are taught.

═══════════════════════════════════════════════════════════════
LT WRITING RULES (non-negotiable)
═══════════════════════════════════════════════════════════════

1. **Every band statement begins "I can..."** — present tense, active voice, first person. **TYPE 3 EXCEPTION: Type 3 LTs do NOT use "I can..." band statements. They use observation indicator sets — see Mode 3 below.**
2. **No parentheses, no inline examples, no "such as" or "for example" anywhere.** Examples are provided separately in teaching guidance, never embedded in the LT statement itself. A statement with examples baked in becomes an implicit checklist.
3. **Single-construct rule.** Each statement describes ONE coherent capability. Test: "Could I assess these separately?" If yes, they must be separate LTs or separate statements. "Analyses sources and constructs arguments" violates this — analysis and argument construction are separately assessable.
4. **Compound knowledge-type rule.** If a statement contains elements from different knowledge types (e.g., one Type 2 and one Type 3 element), it MUST be split into separate LTs with separate assessment routes — REGARDLESS of whether each element passes the single-construct test on its own. This is the most common cause of assessment misrouting.
5. **Observable action verbs ONLY.** Use: identify, describe, compare, explain, justify, analyse, evaluate, create, design, plan, conduct, present, reflect. NEVER use: understand, know, appreciate, be aware of, effectively, sophisticated, well (without observable criteria).
6. **Progression uses LEVERS, not topic escalation.** The six progression levers: independence (how much support needed), complexity (how many variables or perspectives), scope (how broad the context), precision (how accurate or detailed), reasoning (how deep the justification), transfer (how far from the original context). Progression across bands is achieved by advancing one or more of these levers — NOT by changing the topic or adding content.
7. **2 LTs per competency is the default.** 3 only if the strands are genuinely distinct and cannot be collapsed without losing meaning. NOTE: If a competency contains both a Type 2 analytical strand and a Type 3 dispositional strand, these must become separate LTs with separate assessment routes. This may mean a competency that appeared to need 2 LTs actually needs 3. This is correct design, not inflation.
8. **The LT definition describes what ALL band levels do.** It is the generalised "I can..." statement that applies across every band. It is NOT a Band A statement. For Type 3 LTs, the definition must include a note that this LT is assessed through multi-informant observation.

═══════════════════════════════════════════════════════════════
REQUIRED FIELDS FOR EVERY LT
═══════════════════════════════════════════════════════════════

Every LT must include:
- **LT Name** (Title Case, noun-phrase style, stable across years)
- **LT Definition** (one sentence, "I can...")
- **Knowledge Type** (Type 1 / Type 2 / Type 3)
- **Assessment Route** (Rubric with clear criteria / Reasoning quality rubric / Multi-informant observation)
- **Prerequisites** (required for knowledge-contingent Type 3 LTs — name the Type 1/2 LTs that must be established first)
- **Band statements** (Type 1 and Type 2) OR **Observation indicator set** (Type 3)

═══════════════════════════════════════════════════════════════
THREE AUTHORING MODES
═══════════════════════════════════════════════════════════════

**Mode 1 — Plain-language decision targets**
Best for: judgement, choices, safety, credibility, reflection, ethics, communication, collaboration routines, and most Type 2 wellbeing LTs.
Default pattern: DO / CHECK / DECIDE
- DO: main action (one clear verb)
- CHECK: 1-3 simple checks (fit, risk, source, audience, constraints)
- DECIDE: outcome + short reason

**Mode 2 — Skill/proficiency targets**
Best for: academic disciplines, arts, performance, scientific practice. Also appropriate for Type 1 wellbeing science knowledge.
Defaults: one clear skill per band statement; complexity and independence increase across bands; avoid tool/menu lists.

Performance-based Do tasks — presentations, physical demonstrations, structured performances, observable skill execution — are a sub-type of Mode 2. They are assessed through performance rubrics applied to the observable execution, not through multi-informant observation (Mode 3, T3 only) and not through analytical reasoning rubrics (which assess reasoning quality, not execution quality). Use the criterion-referenced rubric generator for performance-based Do tasks. Common examples: oral presentations, debate performances, physical education demonstrations, practical science procedures, musical or artistic performances.

**Mode 3 — Observation indicator sets (Type 3 ONLY)**
Best for: ALL Type 3 dispositional LTs. This mode is mandatory for Type 3 — not optional.
Structure: a set of specific, observable, third-person indicators that describe what the disposition looks like when present, calibrated to each band. These are NOT assessed with a rubric — they inform the observation notes and the developmental conversation.

Format:
```
LT Name: [Dispositional quality]
Knowledge Type: Type 3
Assessment Route: Multi-informant observation

Band A indicators — the teacher notices:
- The student [specific observable behaviour at Band A level]
- The student [specific observable behaviour at Band A level]

Band B indicators — the teacher notices:
- The student [specific observable behaviour]
- The student [specific observable behaviour]

Band C indicators — the teacher notices:
- The student [specific observable behaviour]
- The student [specific observable behaviour]

Band D indicators — the teacher notices:
- The student [specific observable behaviour]
- The student [specific observable behaviour]

Band E indicators — the teacher notices:
- The student [specific observable behaviour]
- The student [specific observable behaviour]

Band F indicators — the teacher notices:
- The student [specific observable behaviour]
- The student [specific observable behaviour]

Knowledge-contingent prerequisites: [Name the Type 1/2 LTs, if applicable]
```

Type 3 developmental progression: Indicators at Band D describe more sophisticated, self-directed, and cross-context manifestations of the disposition. At Band A they describe simpler, more immediate, adult-scaffolded manifestations. The progression uses the same levers (independence, complexity, scope, reasoning, transfer) — but they describe what the teacher observes, not what the student performs for assessment.

Type 3 evidence pathway:
- Teacher observation notes: brief, dated, specific indicator. Third-person. Stored in a retrievable form. At least one counterexample observation per unit (an observation that surprised the teacher or contradicted their existing view of the student).
- Student self-reflection: open questions calibrated to developmental band — not self-grading.
  - Band A: name a moment when you tried something hard
  - Band B: describe one pattern you noticed in yourself this term
  - Band C: compare what you noticed with what your teacher observed
  - Band D: analyse a pattern across contexts and explain what shifted
  - Band E: evaluate how your capacity has developed over the past year — what has changed, what conditions made change possible, and what has remained resistant to change
  - Band F: construct an account of your development across high-stakes real-world contexts over an extended period — what patterns hold, what conditions still challenge you, and what remains unresolved
- Parent/caregiver noticing prompts (optional): three plain-language "what do you notice?" questions sent home two weeks before developmental conversations.
- Strive data (where applicable): behavioural record of actual habit enactment.
- Synthesised in the developmental conversation. NOT a summative grade.

Student-generated single-point rubric (Type 3 supplement): At the start of each unit, the student writes one sentence describing what "doing this well" looks like for them. This becomes the reference point for teacher observation and developmental conversations — not a school-wide criterion. Bands A-B generate this collaboratively with the teacher. Bands C-D write it independently. Band D students review and revise at mid-unit as a metacognitive act. The value of the student-generated single-point rubric is in the act of generation — the student articulating what doing this well looks like for them — not in scoring. It is never used for grading.

═══════════════════════════════════════════════════════════════
DECOMPOSITION LOGIC
═══════════════════════════════════════════════════════════════

A competency is too broad to assess directly. It must be decomposed into 2-3 LTs that together COVER the competency and are individually ASSESSABLE. The decomposition should feel natural — like cutting a diamond along its grain, not chopping it into arbitrary pieces.

Test the decomposition:
- **Coverage test:** Do the LTs together cover the full meaning of the competency? Is anything missing?
- **Distinctness test:** Are the LTs genuinely different capabilities, or are they different ways of saying the same thing?
- **Assessability test:** Can each LT be assessed through observable student work (Type 1/2) or multi-informant observation (Type 3)?
- **Knowledge-type test:** Does each LT contain only ONE knowledge type? If a single LT bundles Type 2 and Type 3 elements, split it — regardless of whether it passes the single-construct test.

═══════════════════════════════════════════════════════════════
QUALITY CHECKLIST (must pass before output)
═══════════════════════════════════════════════════════════════

Format checks:
- [ ] Every Type 1 and Type 2 band statement begins with "I can..."
- [ ] Every Learning Target Definition begins with "I can..."
- [ ] Every Competency Definition begins with "The ability to..."
- [ ] All statements are present tense, active voice
- [ ] Type 3 LTs use observation indicator format, not rubric band statements

Prohibition checks:
- [ ] No parentheses anywhere in the set
- [ ] No inline examples in band statements
- [ ] No inline examples in Learning Target Definitions
- [ ] No "such as" or "for example" anywhere
- [ ] No content inventories (lists of topics/tools/periods)
- [ ] No vague quality descriptors without observable criteria

Construct checks:
- [ ] Single-construct rule passes for all band statements
- [ ] Could pass the "assess separately?" test
- [ ] Compound knowledge-type check: no statement bundles Type 2 and Type 3 elements

Knowledge type checks:
- [ ] Every LT has a Knowledge Type field (Type 1 / Type 2 / Type 3)
- [ ] Every LT has an Assessment Route field that matches its knowledge type
- [ ] Type 3 LTs do not have rubric band statements
- [ ] Knowledge-contingent Type 3 LTs have prerequisite LTs named
- [ ] No Type 3 element is buried inside a Type 1 or Type 2 LT statement

Coherence checks:
- [ ] Vertical coherence: clear A-F progression for all LTs
- [ ] Horizontal coherence: each Learning Target Definition accurately describes what all its band levels do
- [ ] Progression uses appropriate levers (independence / complexity / scope / reasoning / transfer)

Language checks:
- [ ] Language is plain and assessable throughout
- [ ] Age-appropriate for all bands
- [ ] Consistent spelling convention (UK or US)
- [ ] Consistent terminology across the set
- [ ] Strong action verbs (avoid understand / know / appreciate)

Completeness checks:
- [ ] All cells filled (or explicitly marked N/A with rationale)
- [ ] Notes used only for teacher clarifications, not hidden examples
- [ ] Knowledge Type and Assessment Route fields completed for every LT

═══════════════════════════════════════════════════════════════
PRE-SUBMISSION SELF-CHECK PROTOCOL
═══════════════════════════════════════════════════════════════

Before returning output, complete this protocol:

1. Read all Learning Target Definitions aloud. Do any contain content lists? Flag and fix.
2. Apply the "such as" test. Could you insert "such as" naturally anywhere? If yes, you have an implicit list. Remove it.
3. Check for compound statements. Count the "and" conjunctions. Does each one join a single coherent capability, or two assessable actions? Fix any violations.
4. Apply the compound knowledge-type test. For every "and" in every statement: do the two elements belong to the same knowledge type? If one element is Type 2 (analysable in a scenario) and another is Type 3 (only evidenced through real enactment over time), the statement is a compound knowledge-type violation. Split it.
5. Verify horizontal alignment. For each LT, does the definition describe what ALL band levels do? If not, revise.
6. Quality descriptor audit. Highlight all quality adjectives. Are they tied to observable criteria? If not, replace them.
7. Assessment route verification. For each LT: is the named assessment route actually capable of producing valid evidence for this kind of knowledge? A multi-informant observation route for a Type 1 knowledge LT is as wrong as a rubric for a Type 3 disposition.

═══════════════════════════════════════════════════════════════

Your task is to author a complete LT set for:

**Competency name:** {{competency_name}}
**Competency definition:** {{competency_definition}}
**Band range:** {{band_range}}
**Programme purpose:** {{programme_purpose}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Existing draft:** {{existing_draft}} — if provided, review and revise against the quality rules. If not provided, author from scratch.
**Subject area:** {{subject_area}} — if not provided, design the LTs to work across subjects.
**Assessment context:** {{assessment_context}} — if not provided, design for use in both project assessment and reporting.

Return your output in this exact format:

## Learning Target Set: [Competency Name]

**Competency:** [Name]
**Definition:** [One sentence, "The ability to..."]
**Programme purpose:** [Why this matters for the mission]
**Number of LTs:** [2 or 3, with rationale — including knowledge-type split rationale if applicable]

### Competency Review

[Is this competency right? Does it serve the mission? Is it a genuine capability or a topic list in disguise? If the competency needs reframing, say so before proceeding.]

### Step 0: Knowledge Type Classification

[For each emerging LT strand, run the classification decision tree. State the knowledge type, the assessment route, and the reasoning. If any strand is compound, flag it and split before proceeding. If any Type 3 strand is knowledge-contingent, name the prerequisites.]

| LT Strand | Knowledge Type | Assessment Route | Reasoning |
|---|---|---|---|
| [Strand 1] | Type [1/2/3] | [Route] | [Why this classification] |
| [Strand 2] | Type [1/2/3] | [Route] | [Why this classification] |

### LT Decomposition

[The 2-3 LTs, with rationale for each and evidence that the decomposition passes the coverage, distinctness, assessability, and knowledge-type tests]

**LT1: [Name]**
- **Definition:** "I can [generalised statement that applies across all bands]"
- **Knowledge Type:** Type [1/2/3]
- **Assessment Route:** [Route]
- **Prerequisites:** [For knowledge-contingent Type 3 only; otherwise "N/A"]
- **Rationale:** [Why this strand exists as a separate LT]

**LT2: [Name]**
- **Definition:** "I can [generalised statement]"
- **Knowledge Type:** Type [1/2/3]
- **Assessment Route:** [Route]
- **Prerequisites:** [If applicable]
- **Rationale:** [Why this strand exists]

### Band Statements / Observation Indicators

[FOR TYPE 1 AND TYPE 2 LTs — use band statement table:]

**LT[n]: [Name]**
Knowledge Type: Type [1/2]
Assessment Route: [Route]
Authoring Mode: [Mode 1 or Mode 2]

| Band | Statement | Progression Lever(s) |
|---|---|---|
| A | I can [Band A statement] | [Which lever(s)] |
| B | I can [Band B statement] | [Which lever(s)] |
| C | I can [Band C statement] | [Which lever(s)] |
| D | I can [Band D statement] | [Which lever(s)] |

[FOR TYPE 3 LTs — use observation indicator format:]

**LT[n]: [Name]**
Knowledge Type: Type 3
Assessment Route: Multi-informant observation
Prerequisites: [Named Type 1/2 LTs, if knowledge-contingent]

Band A indicators — the teacher notices:
- The student [specific observable behaviour]
- The student [specific observable behaviour]

Band B indicators — the teacher notices:
- The student [specific observable behaviour]
- The student [specific observable behaviour]

Band C indicators — the teacher notices:
- The student [specific observable behaviour]
- The student [specific observable behaviour]

Band D indicators — the teacher notices:
- The student [specific observable behaviour]
- The student [specific observable behaviour]

Band E indicators — the teacher notices:
- The student [specific observable behaviour]
- The student [specific observable behaviour]

Band F indicators — the teacher notices:
- The student [specific observable behaviour]
- The student [specific observable behaviour]

Student self-reflection prompts:
- Band A: [prompt]
- Band B: [prompt]
- Band C: [prompt]
- Band D: [prompt]
- Band E: [prompt]
- Band F: [prompt]

### Quality Check

[Run every statement through the full v4.0 checklist. Flag any issues.]

**Format checks:**
- [ ] Every Type 1/2 band statement begins with "I can..."
- [ ] Every LT Definition begins with "I can..."
- [ ] Every Competency Definition begins with "The ability to..."
- [ ] All statements present tense, active voice
- [ ] Type 3 LTs use observation indicator format, not rubric band statements

**Prohibition checks:**
- [ ] No parentheses anywhere
- [ ] No inline examples in band statements or definitions
- [ ] No "such as" or "for example" anywhere
- [ ] No content inventories
- [ ] No vague quality descriptors without observable criteria

**Construct checks:**
- [ ] Single-construct rule passes
- [ ] Compound knowledge-type check passes: no statement bundles elements from different knowledge types

**Knowledge type checks:**
- [ ] Every LT has a Knowledge Type field
- [ ] Every LT has an Assessment Route that matches its knowledge type
- [ ] Type 3 LTs do not have rubric band statements
- [ ] Knowledge-contingent Type 3 LTs have prerequisites named
- [ ] No Type 3 element is buried inside a Type 1 or Type 2 LT

**Coherence checks:**
- [ ] Vertical coherence (clear A-F progression)
- [ ] Horizontal coherence (LT definition describes all band levels)
- [ ] Progression uses levers, not topic escalation

**Language checks:**
- [ ] Plain, assessable language throughout
- [ ] Consistent spelling convention
- [ ] Strong action verbs only

**Completeness checks:**
- [ ] All cells filled or marked N/A with rationale
- [ ] Knowledge Type and Assessment Route fields completed for every LT

### Known Limitations

[Where the LT set is strongest and where teacher judgment will still be needed]

**Self-check before returning output:** Run the full pre-submission protocol: (a) read all definitions aloud — any content lists? (b) "such as" test — could you insert it anywhere? (c) compound statement check — count the "and" conjunctions, (d) compound knowledge-type test — do elements on either side of "and" belong to the same knowledge type? (e) horizontal alignment — does the definition describe all band levels? (f) quality descriptor audit — all adjectives tied to observable criteria? (g) assessment route verification — is the named route capable of producing valid evidence for this knowledge type?
````

## 示例输出

当需要完整的批判性思维与自我调节示例以对比类型 2 阶段陈述与类型 3 观察路径时，请阅读 [references/worked-examples.zh-CN.md](references/worked-examples.zh-CN.md)。

**精简节选——评估路径：**

| LT 分支 | 知识类型 | 评估路径 | 推理依据 |
|---|---|---|---|
| 证据分析 | 类型 2 | 推理质量量规 | 存在多种有效的分析框架；推理质量决定结果；没有单一正确答案；分析深度随经验增长。向新情境的迁移是检验标准。 |
| 有理有据的论证 | 类型 2 | 推理质量量规 | 论证质量通过推理老练度而非正误来评估；存在多种合理立场；发展的是构建与捍卫立场的能力，而非背诵正确答案。 |

未检测到类型 3 要素。作为**倾向**的批判性思维（自发质疑的习惯，而不仅仅是被要求时才质疑）是一种真实且重要的能力——但它不是本项能力所测量的内容。如果项目希望捕捉批判性思考的倾向，那需要一个拥有自身观察路径的独立类型 3 学习目标。

A阶段指标——教师注意到：
- 当感到沮丧时，学生接受成人的安抚或重定向，并开始回到活动中
- 在非结构化的真实情境中，学生在成人提示下使用一个已命名的平复策略

---

## 已知局限

1. **这是一套实践者方法论，而非同行评审框架。** LT 撰写规则是在课堂实施中开发并精炼的，而非通过对照实验研究得出。它们植根于成熟的评估研究（Black & Wiliam, Bloom, Wiggins & McTighe），但具体规则（单一构念、无行内示例、进阶杠杆、知识类型分类）是 Manning 的原创综合。

2. **应用学习目标需要专业判断。** 一套撰写良好的 LT 提供了结构，但评估某份具体学生作品是否达到某一阶段陈述（类型 1/2），或某个观察模式是否构成某种倾向的证据（类型 3），仍然需要教师的专业判断。LT 减少了主观性——但无法消除主观性。

3. **“每项能力2个 LT”的默认设置未必适用于所有能力。** 部分能力自然拆解为2个分支；另一些则难以干净地拆解。知识类型拆分可能需要3个 LT，即便表面上看似2个就够了。本方法论提供了检验标准（覆盖度、区分度、可评估性、知识类型），但设计师必须自行判断何时遵循默认设置、何时偏离。

4. **类型 3 评估比类型 1 或类型 2 更难实施。** 多信息源观察需要基础设施（可检索的笔记、自我反思规程、发展性对话排期），而大多数学校尚未建立这些基础设施。这是一个真实约束。应对之道不是为了图省事而把类型 3 LT 塞进量规——那只会制造测量的幻觉。应对之道是逐步建设基础设施。
