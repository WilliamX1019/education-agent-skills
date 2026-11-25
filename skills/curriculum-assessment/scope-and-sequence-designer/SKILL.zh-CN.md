---
# AGENT SKILLS STANDARD FIELDS (v2)
name: scope-and-sequence-designer
description: "设计教学进度与范围大纲（Scope and Sequence），展示跨项目或跨学年的纵向与横向课程连贯性。适用于构建新项目、重构学科或确保进阶连贯。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "curriculum-assessment/scope-and-sequence-designer"
skill_name: "教学进度与范围设计器（Scope and Sequence Designer）"
domain: "curriculum-assessment"
version: "1.1"
evidence_strength: "moderate"
evidence_sources:
  - "Bruner (1960) — The Process of Education: spiral curriculum and vertical coherence"
  - "Wiggins & McTighe (2005) — Understanding by Design: backwards design applied to programme-level planning"
  - "Bernstein (1999) — Vertical and horizontal discourse: hierarchical knowledge sequencing"
  - "Hattie (2009) — Visible Learning: curriculum coherence as a high-effect variable"
  - "Muller (2009) — Forms of knowledge and curriculum coherence: conceptual vs contextual coherence"
  - "Maton (2013) — Making semantic waves: cumulative knowledge-building across a programme"
  - "Schmidt, Wang & McKnight (2005) — Coherence of the intended, implemented, and attained curriculum"
  - "Duschl, Schweingruber & Shouse (2007) — Taking Science to School: learning progressions as programme architecture"
  - "Kolb (1984) — Experiential Learning: experience as prerequisite for dispositional development"
  - "Bransford, Brown & Cocking (2000) — How People Learn: experiential readiness and conceptual framing"
  - "Flavell (1979) — Metacognition and cognitive monitoring: naming before practising metacognitive strategies"
  - "Kirschner, Sweller & Clark (2006) — Why minimal guidance during instruction does not work: explicit instruction for novices"
input_schema:
  required:
    - field: "subject_or_programme"
      type: "string"
      description: "学科或项目的名称与简短描述"
    - field: "developmental_bands"
      type: "string"
      description: "学校或项目使用的学段、年级或阶段结构（例如 A–D 学段、1–13 年级、预科至文凭阶段、幼儿至高中，或学校使用的任何其他发展架构——本技能不限于任何特定体系或年龄范围）"
    - field: "intended_outcomes"
      type: "string"
      description: "项目结束时学生应当达成的总体目标"
  optional:
    - field: "existing_units_or_competencies"
      type: "string"
      description: "任何已经到位的既有单元、能力或 LT"
    - field: "knowledge_architecture_output"
      type: "string"
      description: "若已运行 curriculum-knowledge-architecture-designer，提供其输出"
    - field: "time_available"
      type: "string"
      description: "每个学段每周的课时数或小时数"
    - field: "kud_charts"
      type: "string"
      description: "待排序 LT 的 KUD 图表（按学段列出 Know/Understand/Do）。先修关系推断的最丰富输入。Know 层揭示 T1 内容依赖；Understand 层揭示概念脚手架关系；Do 层揭示 T3 vs. T1/T2 区分。高置信度推断。以 Markdown 表格或结构化文本提供。"
    - field: "lt_types"
      type: "string"
      description: "每个 LT 或能力的 T1/T2/T3 分类。T1（层级型——先修驱动排序）、T2（横向型——分析性，排序约束较松）、T3（倾向型——适用体验准备度逻辑）。若未提供且未提供 kud_charts，本技能将从 LT 措辞中推断类型。"
    - field: "prerequisite_map"
      type: "string"
      description: "预先构建的、标明类型的 LT 间先修关系。每项标明为 hard（必须先修——逻辑依赖，不可协商）、soft_enabler（建议先修——丰富但不设卡）或 conceptual_accelerator（建议先修——使下游 LT 更易迁移）。若提供，则直接使用而不做推断。"
    - field: "sequencing_principles"
      type: "string"
      description: "项目特定的排序规则。例如 ‘T3 体验先于 T1 解释’、‘LT 6.1 前置作为 C1 与 C3 LT 的概念加速器’。当与本技能默认逻辑冲突时，这些规则优先。"
output_schema:
  type: "object"
  fields:
    - field: "knowledge_progression_map"
      type: "object"
      description: "针对每种知识类型（层级型、横向型、倾向型）：它如何跨学段发展、何时引入什么，以及学段间的先修依赖是什么"
    - field: "vertical_coherence_check"
      type: "object"
      description: "针对层级型知识：引入每个新概念前先修基础是否到位？针对横向型知识：思维复杂性是否跨学段递增？针对倾向型知识：发展机会是否贯穿整个项目且呈累积性？"
    - field: "horizontal_coherence_check"
      type: "object"
      description: "在每个学段内部：各知识类型之间是否平衡？学段内各单元是相互联结还是各自孤立？"
    - field: "sequencing_rationale"
      type: "string"
      description: "针对每个 LT 的位置安排，用一句话解释驱动该决策的排序逻辑：硬性先修 / 软性脚手架 / 体验准备度 / 给定原则 / 无依赖。"
    - field: "gaps_and_overlaps"
      type: "object"
      description: "序列中缺失的要素、未增加复杂度而简单重复的要素，以及学生容易挣扎的学段过渡"
    - field: "design_flags"
      type: "object"
      description: "缺乏清晰进阶逻辑却跨越多学段的复合能力、缺乏足够知识前提的倾向性目标，以及缺乏显性思维培养的横向要素"
    - field: "inferred_prerequisite_map"
      type: "array"
      description: "当未提供 prerequisite_map 时出现。列：lt_a、relationship_type（hard/soft_enabler/conceptual_accelerator/none）、lt_b、rationale、confidence（high/medium/low）。标记为推断结果——在当作权威约束前需学科专家与教师审查。"
    - field: "sequencing_constraints"
      type: "array"
      description: "区分硬性约束排序（不可协商——违反即构成先修错误）与推荐排序（教师可调）。列：lt_or_competency、constraint_type（hard/recommended）、rationale。"
    - field: "sequencing_principles_output"
      type: "string"
      description: "所应用的排序原则，写成教师可采纳、修改或拒绝的可读清单。包含默认原则及任何提供的项目特定原则。使本技能的推理透明且可调。"
    - field: "sequencing_questions_for_teacher"
      type: "array"
      description: "针对每个 teacher_discretion_flag 条目，提供 2–3 个具体可操作的问题，供教师在敲定排序决策前回答。让教师判断变得可操作，而非仅仅口头承认。"
    - field: "teacher_discretion_flags"
      type: "array"
      description: "推荐排序仅属软性偏好、应由教师判断主导最终决策的 LT。包含所有体验准备度依赖情境的 T3 倾向性 LT。"
    - field: "prerequisite_violations"
      type: "array"
      description: "拟议序列违反硬性先修关系的情形。若无则为空数组。每条违规说明被打破的约束、当前拟议排序以及所需修正。"
    - field: "confidence_level"
      type: "string"
      description: "总体置信度——高（提供了 prerequisite_map 或 KUD 图表）、中（提供了带类型的 LT，无 KUD 或图谱）、低（仅提供能力定义或原始文档）。附带一句话说明什么能提高置信度。"
chains_well_with:
  - "curriculum-knowledge-architecture-designer"
  - "kud-knowledge-type-mapper"
  - "kud-chart-author"
  - "learning-target-authoring-guide"
  - "developmental-band-system-designer"
  - "backwards-design-unit-planner"
  - "competency-unpacker"
  - "learning-progression-builder"
  - "gap-analysis-from-student-work"
teacher_time: "15 分钟"
tags: ["scope-and-sequence", "curriculum-coherence", "vertical-coherence", "learning-progressions", "programme-design", "Bruner", "spiral-curriculum", "knowledge-types", "prerequisite-sequencing", "KUD-charts"]
---

# 教学进度与范围设计器（Scope and Sequence Designer）

## 本技能的作用

接收项目描述与发展学段结构，产出一份连贯的教学进度与范围大纲（Scope and Sequence）——绘制各学段教授什么、按什么顺序教授，并给出排序决策的明确理据。本技能适用于任何教育阶段：幼儿至高中、本科、专业发展项目或任何其他分阶段学习架构。大多数教学进度表只是清单：把主题分配到各年级，却没有连贯逻辑说明为什么该主题放在那里、它建立在什么之上，又为后续什么做准备。本技能产出植根于三种知识类型的结构化进阶：层级型要素按先修逻辑排序，确保在引入下一层前基础知识始终到位；横向型要素按逐步提升思维复杂性排序，而非年复一年在同一水平重复相同思维动作；倾向型要素作为持续主线绘制，并显性指明倾向有意义发展前必须到位的知识前提。当提供了 KUD 图表、LT 类型或预建先修图谱时，本技能直接应用它们；未提供时，则推断先修关系并标出每项推断的置信度。结果是一份每个要素都有理有据、且每项建议的认识论地位都清晰透明的项目规划。AI 在此尤为关键，因为连贯的项目设计需要同时跨学年追踪先修链条、监控学段内外知识类型平衡，并识别孤立看单个单元时看不见的缺口与重叠——这种系统化交叉核查在真实课程规划中认知负荷极高且经常被跳过。

## 实证基础

Bruner（1960）确立了螺旋式课程（spiral curriculum）的基础原则：核心观念应跨年级以不断提升的复杂性反复重访，每一次重访都建立在先前接触之上，而非简单重复。如果教学进度表重访一个主题却未提高认知要求，那不是螺旋——那是原地踏步。螺旋原则以不同方式应用于三种知识类型：层级型知识通过在稳固基础上叠加新复杂度来螺旋上升——先分数后代数、先细胞生物后遗传学；横向型知识通过提高应用于反复出现主题的分析思维复杂度来螺旋上升——在 A 学段识别视角的学生，到 D 学段应当能评价与比较分析框架；倾向型知识则不以同样方式螺旋，而是通过贯穿全项目的实践行动持续发展，尽管支撑倾向表达的知识在每个学段都会深化。

Schmidt、Wang & McKnight（2005）分析了高绩效教育体系的课程连贯性，发现连贯课程共有三大特征：**聚焦**（更少主题、更深教学）、**严谨**（每一层级都有恰当挑战）以及**连贯**（主题在学段内和跨学段间逻辑相连）。缺乏连贯性——主题毫无进阶逻辑地忽现忽隐——的体系表现持续落后。他们对进度表设计最重要的发现是：连贯性不仅是纵向属性（B 学段是否建立在 A 学段之上？），也是横向属性（B 学段内部的各要素是否彼此联结？）。一个项目可能纵向排序完美，但如果每个学段内的单元彼此孤立，它依然缺乏连贯性。

Duschl、Schweingruber & Shouse（2007）发展了**学习进阶**概念：关于学生理解如何跨学年发展的实证描述，每一级都具体建立在上一级之上。他们的研究确立了进阶不会自动发生——它需要刻意课程设计，使所教内容匹配学生的学习准备度。学习进阶在层级型知识领域（数学、早期阅读、部分科学领域）研究最充分，其先修结构已获广泛实证。对于横向与倾向型领域，进阶的实证基础较薄弱，必须基于发展原则来建构，而非依赖特定学习序列的复制研究。

Wiggins & McTighe（2005）将逆向设计应用于项目级规划：从项目末端的预期结果出发，逆向推导每个阶段必须到位什么才能达成这些结果。在教学进度层面，这意味着最终学段的期望决定了前面每个学段必须教授什么——不是为了直接应试，而是为了夯实使最终结果得以实现的知识与能力基础。

Bernstein（1999）与 Muller（2009）为按知识类型排序奠定了理论基础。**层级型知识**具有内在排序逻辑：概念必须按先修顺序教授，因为后续概念确实依赖于先前概念——在学生理解细胞分裂前无法教授遗传规律。**横向型知识**不以同样方式存在先修链条——不同分析视角可按多种顺序引入——但它确实存在**复杂性进阶**：学生应从识别视角走向通过视角分析，再走向跨视角评价与综合。按不断提升的分析需求（而非先修依赖）来排序横向知识，是本技能做出的关键区分之一。

Maton（2013）补充了语义波概念：有效的知识建构需要在抽象原则与具体案例之间跨项目往返移动，而不仅仅在单节课内。全程停留在抽象层面的进度表产出脱节的理论知识；全程停留在具体层面的进度表产出缺乏概念发展的经验。跨项目的语义剖面应展现出在具体与抽象间移动的能力不断增强——早期学段主要处理具体案例与简单抽象，后期学段则应能流畅地在多个抽象层级间操作并刻意切换。

Hattie（2009）将课程连贯性识别为影响学生学业成就的高效应变量。学生体验为相连、累积旅程的项目，比每年都像重新开始、新内容与过去毫无明显关联的项目产出更好的结果。这正是投入教学进度设计的现实依据：项目整体的连贯性比其中任何单个单元的质量更能预测学生成果。

Bransford、Brown & Cocking（2000）与 Kolb（1984）确立了倾向型排序的**体验准备度原则**：已经实践过某种倾向的学生，在接触对其的解释时会将其体验为对亲身经历的印证，而非空洞抽象。对于社会情绪倾向能力，体验通常应先于解释。Flavell（1979）指出一个重要例外：对于元认知与反思型 LT，在练习前先显性命名策略能提升练习质量。Kirschner、Sweller & Clark（2006）提供了反方观点，认为初学者在许多领域受益于先显性教学后练习——本技能承认这一张力，并在适用的任何地方将其标为教师酌情决定。

## 输入规范

教育者必须提供：
- **学科或项目（Subject or programme）：** 名称与简短描述。*例如：“幸福感，REAL School Budapest” / “科学，7–13 年级” / “跨学科人文，预科至文凭” / “幼儿数学，3–6 岁”*
- **发展学段（Developmental bands）：** 学段、年级或阶段结构。*例如：“A–D 学段（约 5–15 岁）” / “7–13 年级” / “基础、中级、高级、文凭” / “托班、小班、一年级、二年级”*
- **预期结果（Intended outcomes）：** 项目结束时学生应达到的总体目标。*例如：“学生发展自我调节、能动性、关怀他人，以及理解自身幸福感的科学素养” / “学生发展科学推理、实验设计能力以及大学深造所需的知识基础”*

可选项（如可用则由上下文引擎注入）：
- **既有单元或能力（Existing units or competencies）：** 任何已经到位的单元、能力或 LT
- **知识架构输出（Knowledge architecture output）：** 来自 `curriculum-knowledge-architecture-designer`（若已运行）
- **可用时间（Time available）：** 各学段每周小时数或课时数
- **KUD 图表（KUD charts）：** 待排序 LT 的 KUD 图表（分学段 Know/Understand/Do）。先修推断的最丰富输入——Know 层揭示 T1 内容依赖，Understand 层揭示概念脚手架关系，Do 层揭示 T3 vs. T1/T2 区分。高置信度推断。
- **LT 类型（LT types）：** 每个 LT 或能力的 T1/T2/T3 分类。若未提供且未提供 `kud_charts`，本技能从 LT 措辞推断类型。
- **先修图谱（Prerequisite map）：** 预先构建的标明类型的 LT 间先修关系，标明为 `hard`、`soft_enabler` 或 `conceptual_accelerator`。若提供，直接使用。
- **排序原则（Sequencing principles）：** 项目特定排序规则，冲突时覆盖默认逻辑。

## 提示词（Prompt）

```
You are a curriculum sequencing specialist producing scope and sequence recommendations for competency-based developmental band programmes. You apply three distinct sequencing logics based on content type and prerequisite relationships. You are explicit about the epistemic status of every recommendation — distinguishing hard constraints from soft preferences from teacher professional judgement calls.

---

STEP 0 — INPUT ASSESSMENT AND ROUTING

Assess input state before producing any output:

STATE A — prerequisite_map supplied: Use directly. Highest confidence. Proceed.

STATE B — kud_charts supplied (no prerequisite_map): Infer from KUD charts. High confidence. Proceed.

STATE C — LTs with lt_types supplied (no KUD, no map): Infer from LT content and types. Medium confidence. Proceed with confidence flags.

STATE D — only competency definitions supplied: Low confidence. Produce output with disclaimer: "Prerequisite inference from competency definitions alone is unreliable. Running KUD Chart Author skill first will produce substantially more reliable sequencing." Proceed with low confidence flagged throughout.

STATE E — only subject name and intended outcomes supplied: Decline to produce a scope and sequence. Output: "Insufficient inputs for reliable sequencing. Recommended sequence: (1) Run Learning Target Authoring Guide to produce LTs. (2) Run KUD Chart Author to produce KUD charts. (3) Return here." Do not produce a sequence in State E.

---

STEP 1 — PREREQUISITE MAP

1a. If prerequisite_map supplied: use directly. Skip to Step 2.

1b. Inference from KUD charts (State B):
For each pair of LTs:
- Know layers: if LT A's Know content is directly required by LT B's Know or Understand layer — hard prerequisite.
- Understand layers: if LT A's Understand makes LT B's Understand richer and more portable — conceptual_accelerator.
- Do layers: if LT A is T1 and LT B is T3, and T1 explains why the T3 disposition works — soft_enabler.
- No meaningful dependency — none.
Confidence: high for Know-layer dependencies, medium for Understand-layer inferences.

1c. Inference from LT content and types (State C). Apply by type combination:

T1 → T1: Would a student lacking LT A's content be unable (not just hindered) to access LT B? If yes: hard. If enriching but not gating: soft_enabler. Example: "Understanding the stress response mechanism (T1) is a hard prerequisite for evaluating stress management interventions (T1)."

T1 → T3: T1 content explaining why a T3 disposition works is typically a conceptual_accelerator, not a hard prerequisite. The disposition can develop through practice without explanation — the explanation makes it transferable. Example: "Neuroscience of emotion regulation (T1) is a conceptual accelerator for self-regulation practice (T3)."

T2 → T3: Typically a soft_enabler. Example: "Reflective decision-making (T2) enriches metacognitive self-direction (T3) but does not gate it."

T3 → T3: Usually soft. One T3 disposition rarely makes another logically inaccessible. Example: "Self-awareness (T3) is a soft enabler for empathy (T3)."

T2 → T2: Rarely hard prerequisites — usually parallel. Flag as none unless clear content dependency exists.

Confidence for all State C inferences: medium.

1d. Always include with inferred maps: "These relationships were inferred from LT content and types. Subject expert review is required before treating inferred hard prerequisites as non-negotiable — particularly in mathematics, science, and language acquisition where prerequisite structures are non-obvious from text alone."

---

STEP 2 — THREE SEQUENCING LOGICS

HARD PREREQUISITE LOGIC
Applies to: T1 LTs with hard prerequisites in the map.
Rule: prerequisite LT must appear earlier. Non-negotiable. Violation = PREREQUISITE_VIOLATION error, not a suggestion.
Output: constraint_type: hard in sequencing_constraints.

SOFT SCAFFOLD LOGIC
Applies to: soft_enabler and conceptual_accelerator relationships.
Rule: place enabler/accelerator earlier where possible. When not possible, flag the trade-off in sequencing_rationale.
Output: constraint_type: recommended. Teacher can adjust.

EXPERIENTIAL READINESS LOGIC
Applies to: T3 dispositional LTs.
Default rule: experience of the capability should generally precede T1/T2 content that explains it. Students who have practised a disposition encounter the explanation as confirmation of lived experience, not abstraction. (Bransford, Brown & Cocking (2000). How People Learn. National Academies Press. Kolb (1984). Experiential Learning. Prentice Hall.)

Exception — metacognitive and reflective T3 LTs: For LTs in metacognition and reflection, light conceptual framing before practice may be warranted. Naming metacognitive strategies explicitly before practising them improves practice quality. (Flavell (1979). Metacognition and cognitive monitoring. American Psychologist, 34(10), 906-911.) Flag metacognitive T3 LTs as candidates for concept-first sequencing in sequencing_questions_for_teacher.

Counterargument to acknowledge in output: explicit instruction research (Kirschner, Sweller & Clark (2006). Why minimal guidance during instruction does not work. Educational Psychologist, 41(2), 75-86.) argues novice learners benefit from explicit instruction before practice. Experiential readiness default applies most strongly to social-emotional dispositional capabilities. Do not apply to T1 LTs.

Output: flag T3 ordering as constraint_type: recommended with teacher_discretion_flag.

SEQUENCING PRINCIPLES OVERRIDE
If {{sequencing_principles}} supplied: apply after the three default logics. Where a supplied principle conflicts with a default, the principle wins — but flag the conflict: "Supplied principle [text] overrides the default [logic name] recommendation for [LT name]. If intentional, no action needed. If not, review the supplied principle."

---

STEP 3 — KNOWLEDGE ARCHITECTURE DIAGNOSIS

Before producing the full sequence, identify what types of knowledge are present in this programme. If a knowledge architecture output is provided, use it. If not, conduct a rapid diagnosis: what are the hierarchical elements that have prerequisite chains, what are the horizontal elements that require thinking sophistication to develop, and what are the dispositional elements that develop continuously across the programme? List the major elements under each type. The sequencing logic for each type is fundamentally different and must be treated separately.

---

STEP 4 — FULL SEQUENCE CONSTRUCTION

Apply the three sequencing logics from Step 2 to place every LT or competency in a band. For each placement:
- State the constraint_type: hard or recommended
- State the sequencing_rationale in one sentence: which logic drove the decision
- Flag any teacher_discretion items (all T3 ordering, all soft scaffold decisions)

---

STEP 5 — COHERENCE CHECKS

VERTICAL COHERENCE: For hierarchical elements: is every concept introduced after its prerequisites are secured? For horizontal elements: is analytical sophistication genuinely increasing, or are students doing the same thinking with slightly harder content? For dispositional elements: are development opportunities present throughout? Flag every break.

HORIZONTAL COHERENCE: Within each band: is there appropriate balance between knowledge types? Are units connected or siloed? Would a student finishing this band have the knowledge, thinking, and dispositional development needed to succeed in the next band?

---

STEP 6 — SEQUENCING PRINCIPLES OUTPUT

Write a readable list of principles applied:
- The three default logics, stated plainly
- Any programme-specific principles supplied
- The metacognitive T3 exception
- Invitation: "Review these principles. If any do not match your programme's philosophy or your knowledge of your students, adjust the sequence accordingly."

---

STEP 7 — SEQUENCING QUESTIONS FOR TEACHER

For each teacher_discretion_flag item, produce 2-3 specific actionable questions. Examples:

For T3 LT ordering:
- "Have students in this band encountered [capability] in practice already through projects or earlier band experience?"
- "What did last term's unit foreground — does the recommended sequence build on that or require a context shift?"
- "Are there students new to this band who would lack the experiential base the recommended order assumes?"

For soft scaffold decision:
- "Is [accelerator LT] already established for most students from prior experience, making early placement less critical?"

For metacognitive T3 LT:
- "Have students been explicitly introduced to metacognitive vocabulary before? If yes, experience-first may be less important."
- "Does this term's project create natural metacognitive moments that would give conceptual framing something to attach to?"

---

STEP 8 — DESIGN FLAGS AND RECOMMENDATIONS

Identify gaps (important elements missing from the sequence), overlaps (elements repeated without progression), transitions where students are likely to struggle, and compound competencies that appear to span multiple bands without clear progression logic. For each flag, provide a specific recommendation.

---

STEP 9 — INPUTS

subject_or_programme: {{subject_or_programme}}
developmental_bands: {{developmental_bands}}
intended_outcomes: {{intended_outcomes}}
existing_units_or_competencies: {{existing_units_or_competencies}}
kud_charts: {{kud_charts}}
lt_types: {{lt_types}}
prerequisite_map: {{prerequisite_map}}
sequencing_principles: {{sequencing_principles}}
time_available: {{time_available}}
knowledge_architecture_output: {{knowledge_architecture_output}}

---

Return your output in this exact format:

## Scope and Sequence: [Programme Name]

**Programme:** [Summarised]
**Developmental bands:** [Band structure]
**Intended outcomes:** [Summarised]
**Time available:** [If provided; otherwise "Not specified"]
**Input state:** [A/B/C/D — one sentence on what was supplied and confidence level]

### Confidence Level

[Overall confidence — high/medium/low — with one sentence on what would raise confidence]

### 0. Prerequisite Map

[If prerequisite_map supplied: "Using supplied map." List relationships.]
[If inferred: table with columns lt_a | relationship_type | lt_b | rationale | confidence]
[Always include inferred-map disclaimer if applicable]

### 1. Knowledge Architecture Diagnosis

**Hierarchical elements:**
[List with brief description of each]

**Horizontal elements:**
[List with brief description of each]

**Dispositional elements:**
[List with brief description of each]

**Architecture summary:**
[Overall profile — what proportion of the programme is hierarchical, horizontal, and dispositional, and what does this mean for sequencing]

### 2. Sequencing Constraints

| LT or Competency | Constraint Type | Rationale |
|---|---|---|
| [LT] | hard / recommended | [One sentence] |

### 3. Recommended Sequence with Rationale

[For each LT or competency: band placement, sequencing_rationale (one sentence per item), teacher_discretion_flag if applicable]

### 4. Prerequisite Violations

[Empty if none: "No prerequisite violations detected."]
[If present: violation, current proposed ordering, required correction]

### 5. Coherence Checks

**Vertical coherence:**
[Hierarchical / horizontal / dispositional — flag breaks]

**Horizontal coherence:**
[Per band — balance, connections, readiness for next band]

### 6. Sequencing Principles

[Readable list — default logics, programme-specific principles, metacognitive T3 exception, invitation to adjust]

### 7. Teacher Discretion Flags and Questions

[For each flagged item: the flag, then 2-3 specific actionable questions]

### 8. Design Flags and Recommendations

**Gaps:** [Missing elements — with recommendation]
**Overlaps:** [Repeated without progression — with recommendation]
**Difficult transitions:** [With recommendation]
**Compound competencies:** [With recommendation]
**Priority actions:** [3–5 highest-impact changes, in order]

**Self-check before returning output:** Verify that (a) input state is assessed before any output is produced and State E is declined, (b) every hard prerequisite has constraint_type: hard and a prerequisite_violations check is included, (c) every T3 dispositional ordering is flagged for teacher discretion, (d) the metacognitive T3 exception is identified where relevant, (e) the inferred prerequisite map disclaimer is included whenever inference was used, (f) the sequencing_principles output makes the skill's reasoning transparent and adjustable, (g) sequencing questions are specific and actionable (not generic), and (h) confidence_level is stated with a clear statement of what would raise it.
```

## 示例输出

当你需要完整的幸福感项目示例（包括学段安排、推断先修关系、连贯性核查与教师问题）时，请阅读 [references/worked-examples.zh-CN.md](references/worked-examples.zh-CN.md)。

**精简节选——推断序列中的置信度：**

**输入状态：** 状态 D——仅提供了能力定义，未提供 KUD 图表、LT 类型或先修图谱。中等偏低置信度。通过 KUD Chart Author 提供 KUD 图表将大幅提升排序可靠性。

### 置信度

中等偏低。先修关系是根据能力定义与知识领域惯例推断的。提供 KUD 图表（分学段 Know/Understand/Do）会将层级关系的置信度提升至高。在将任何推断出的硬性先修视为不可协商条件前，需由学科专家进行审查。

---

## 已知局限

1. **本技能产出的教学进度与范围大纲是规划文档，而非已实施课程。** 一份连贯的书面序列并不能保证连贯的教学——实施取决于教师理解排序逻辑并在各班级与年级间做出一致决策。`sequencing_rationale` 输出正是为了分享给教师而设计的，因为实施连贯性要求他们理解要素**为何**被放在那里，而不仅仅是教什么。

2. **学习进阶在某些领域（早期数学、阅读发展、科学推理）有坚实实证基础，而在另一些领域（幸福感、创意艺术、跨学科思维）则较为薄弱。** 当特定学习进阶的实证基础薄弱时，本技能会基于发展原则产出合乎逻辑的进阶——但该进阶应被视为有待通过实施与评估数据检验的假设，而非研究已证明的定论。

3. **本技能产出的是推荐序列，无法强制执行。** 在真实学校中，教学进度受制于排课限制、师资变动、资源可用性与情境决策，这些现实因素往往会覆盖理想序列。输出应被视为设计目标——随后由课程团队根据现实约束决定实施能多大程度贴近它。

4. **用于排序的三类型知识框架是一种简化。** 真实知识要素常位于类型边界上，边界案例的排序逻辑需要本技能能提示却无法替代的专业判断。当要素出于排序目的被归为某一主要类型时，应显性说明分类理由，使教师理解背后的推理。

5. **教学进度与范围设计永远不会“彻底完工”。** 随着学生推进项目，评估数据会揭示序列在何处奏效、在何处制造缺口或挣扎。本设计器基于当前知识产出最佳可用计划——至少应每年结合真实学生成果数据审查并修订一次。`gap-analysis-from-student-work` 技能是将此类数据反馈回序列修订的天然工具。

6. **若未提供 `prerequisite_map`，所有先修关系均从 LT 内容与类型推断。** 推断对 T1 内容依赖最可靠，对 T3 倾向关系最不可靠。对于具有正式标明先修的项目，务必提供 `prerequisite_map`——不要依赖推断来做硬性约束决策。

7. **T3 倾向性 LT 的排序本质上是教师专业判断问题，无法仅从课程文档完全解决。** 本技能提供原则并将决策标出供审查。体验准备度默认规则对社会情绪倾向型 LT 有充分支持，但在其他领域存在争议。请使用 `sequencing_principles` 进行覆盖。

8. **专业领域中推断出的先修图谱需要学科专家审查。** 在数学、科学和语言习得中，仅凭 LT 文本往往看不出先修结构。这些领域中推断出的图谱是专家审查的起点，而非权威图谱。

9. **本技能拒绝仅凭学科名称与预期结果产出结果（状态 E）。** 基于不足输入产出的进度表会制造一种虚假的结构感，日后修改起来比从头开始更难。请先运行 `learning-target-authoring-guide` 和 `kud-chart-author`。
