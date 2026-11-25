---
# AGENT SKILLS STANDARD FIELDS (v2)
name: backwards-design-unit-planner
description: "采用逆向设计法规划教学单元，从预期学习结果出发，经由评估证据推导出学习活动。适用于基于标准开启新单元或重构现有单元。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "curriculum-assessment/backwards-design-unit-planner"
skill_name: "逆向设计单元规划器"
domain: "curriculum-assessment"
version: "1.0"
evidence_strength: "strong"
evidence_sources:
  - "Wiggins & McTighe (1998, 2005) — Understanding by Design"
  - "Wiggins & McTighe (2011) — The Understanding by Design Guide to Creating High-Quality Units"
  - "Tomlinson & McTighe (2006) — Integrating Differentiated Instruction and Understanding by Design"
  - "Hattie (2009) — Visible Learning: backward design and clarity of learning intentions"
  - "Biggs & Tang (2011) — Teaching for Quality Learning at University: constructive alignment"
input_schema:
  required:
    - field: "desired_outcomes"
      type: "string"
      description: "单元结束时学生应当理解、知道并能够做到的内容"
    - field: "student_level"
      type: "string"
      description: "年龄/年级"
    - field: "unit_duration"
      type: "string"
      description: "课时数或周数"
  optional:
    - field: "subject_area"
      type: "string"
      description: "课程学科"
    - field: "curriculum_framework"
      type: "string"
      description: "来自上下文引擎：需要回应的具体课程标准"
    - field: "student_profiles"
      type: "array"
      description: "来自上下文引擎：先前学业水平、已知漏洞、班级构成"
    - field: "available_resources"
      type: "string"
      description: "可用的关键文本、材料或资源"
output_schema:
  type: "object"
  fields:
    - field: "stage_1_desired_results"
      type: "object"
      description: "持久理解、核心问题、知识与技能"
    - field: "stage_2_assessment_evidence"
      type: "object"
      description: "证明理解的表现性任务与其他证据"
    - field: "stage_3_learning_plan"
      type: "object"
      description: "与阶段 1 和阶段 2 对齐的序列化学习活动"
    - field: "alignment_check"
      type: "string"
      description: "验证学习活动、评估与预期结果是否对齐"
chains_well_with:
  - "competency-unpacker"
  - "criterion-referenced-rubric-generator"
  - "formative-assessment-technique-selector"
  - "explicit-instruction-sequence-builder"
  - "curriculum-knowledge-architecture-designer"
  - "kud-knowledge-type-mapper"
  - "critical-thinking-task-designer"
  - "scope-and-sequence-designer"
teacher_time: "5 分钟"
tags: ["UbD", "backwards-design", "unit-planning", "curriculum", "alignment"]
---

# 逆向设计单元规划器

## 本技能的作用

根据教师的预期学习结果，生成完整的第 1–2–3 阶段“追求理解的教学设计（UbD）”单元结构：阶段 1 界定持久理解、核心问题与目标知识/技能；阶段 2 设计证明理解的评估证据（在规划任何教学活动之前）；阶段 3 序列化通向评估与预期结果的学习活动。逆向设计的核心洞见在于：评估设计必须先于教学设计——不是事后补救，而是对“成功是什么样子”的定义。AI 在此尤为关键，因为逆向设计要求同时在脑海中统筹全部三个阶段并确保它们之间紧密对齐——所评即所期，所教即所评。大多数教师设计的单元往往先想活动、最后想测验，这会导致教学与评估脱节。

## 实证基础

Wiggins & McTighe（1998, 2005）创立了“追求理解的教学设计（Understanding by Design，UbD）”，这是教育界应用最广泛的课程设计框架。该框架的核心论点是：课程应当从预期结果出发**逆向**设计，而不是从手头活动出发正向拼凑。阶段 1（预期结果）界定学生应当理解什么——不仅仅是记住或做到，而是在可迁移水平上真正理解。阶段 2（评估证据）决定哪些证据能证明这种理解——先于教学设计，从而使教学瞄准真实成果而非仅覆盖进度。阶段 3（学习计划）序列化通向被评估结果所需的一系列教学。Wiggins & McTighe（2011）为单元开发提供了实用指南，强调持久理解应当是超越本单元仍值得理解的可迁移观念，而核心问题应当真正开放——激发探究而非预设唯一答案。Biggs & Tang（2011）提出了“建构性对齐（constructive alignment）”——即学习结果、评估任务与教学活动必须保持一致，使所评即所教，所教为所评做准备。Hattie（2009）证实，学习意图与成功标准的清晰度是影响学生学业成就的最高杠杆因素之一。

## 输入规范

教师必须提供：
- **预期结果（Desired outcomes）：** 学生应理解、知道并能做什么。*例如：“学生将理解生物体如何通过自然选择适应环境，掌握关键词汇（适应、变异、自然选择、进化），并能解释特定生物的特征与其环境之间的关联。”*
- **学生水平（Student level）：** 年级。*例如：“九年级”*
- **单元时长（Unit duration）：** 单元长度。*例如：“6 课时（每课时 1 小时）” / “3 周”*

可选项（如可用则由上下文引擎注入）：
- **学科领域（Subject area）：** 课程学科
- **课程框架（Curriculum framework）：** 具体标准
- **学生画像（Student profiles）：** 先前学业水平、已知漏洞
- **可用资源（Available resources）：** 文本、材料、资源

## 提示词（Prompt）

```
You are an expert in curriculum design, with deep knowledge of Wiggins & McTighe's (1998, 2005) Understanding by Design framework, Biggs & Tang's (2011) constructive alignment, and Hattie's (2009) research on learning intentions and success criteria. You understand that effective unit design works BACKWARD from desired results — defining what students will understand first, then designing assessment evidence, then planning learning activities.

Your task is to design a UbD unit for:

**Desired outcomes:** {{desired_outcomes}}
**Student level:** {{student_level}}
**Unit duration:** {{unit_duration}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Subject area:** {{subject_area}} — if not provided, infer from the desired outcomes.
**Curriculum framework:** {{curriculum_framework}} — if not provided, design in general terms.
**Student profiles:** {{student_profiles}} — if not provided, assume a typical mixed-ability class.
**Available resources:** {{available_resources}} — if not provided, suggest appropriate resources.

Apply these evidence-based principles:

1. **Stage 1 — Desired Results (Wiggins & McTighe, 2005):**
   - **Enduring understandings:** Big ideas that are transferable beyond this unit. These are not facts to memorise but principles to understand. Frame as "Students will understand that..." statements.
   - **Essential questions:** Open, thought-provoking questions that guide inquiry throughout the unit. These should be genuinely debatable — not questions with a single right answer. They should recur throughout the unit, with students' answers deepening over time.
   - **Knowledge:** Specific facts, concepts, and vocabulary students will know.
   - **Skills:** Specific abilities students will be able to demonstrate.

2. **Stage 2 — Assessment Evidence (Wiggins & McTighe, 2005; Biggs & Tang, 2011):**
   - Design assessment BEFORE instruction. This is the core UbD principle.
   - **Performance task:** A rich, authentic task that requires students to demonstrate understanding through application — not just recall facts. The task should require transfer — applying learning to a new situation.
   - **Other evidence:** Additional assessment methods (quizzes, checks for understanding, observations) that gather evidence of knowledge and skills.
   - Assessment must be aligned to Stage 1 — every enduring understanding and essential question must be assessable through the evidence in Stage 2.

3. **Stage 3 — Learning Plan (Wiggins & McTighe, 2005):**
   - Sequence learning activities that build toward the Stage 2 assessments.
   - Use the WHERETO framework: Where are we going? Hook the student. Explore and equip. Rethink and revise. Evaluate. Tailor to individual needs. Organise for understanding.
   - Activities should be sequenced logically — building knowledge before applying it, scaffolding before independence.
   - Each activity should connect clearly to the Stage 2 assessment — if an activity doesn't prepare students for the assessment, question whether it belongs.

4. **Alignment check (Biggs & Tang, 2011):**
   - Verify that Stage 1 outcomes are assessed in Stage 2 and taught in Stage 3.
   - Flag any misalignment: outcomes that are stated but not assessed, or assessed but not taught.

Return your output in this exact format:

## Unit Plan: [Unit Title]

**For:** [Student level]
**Subject:** [Subject area]
**Duration:** [Unit duration]

### Stage 1: Desired Results

**Enduring Understandings**
[2–3 transferable understandings — "Students will understand that..."]

**Essential Questions**
[2–3 open, recurring questions that guide inquiry]

**Students will know:**
[Specific knowledge — facts, concepts, vocabulary]

**Students will be able to:**
[Specific skills]

### Stage 2: Assessment Evidence

**Performance Task**
[Description of the authentic assessment task, including: the scenario, what students produce, what the task assesses, and brief success criteria]

**Other Evidence**
[Additional assessment methods mapped to specific Stage 1 outcomes]

### Stage 3: Learning Plan

[Lesson-by-lesson or phase-by-phase sequence, showing: what happens, what it builds toward, and how it connects to Stage 2]

### Alignment Check

[Verification that all Stage 1 outcomes are assessed in Stage 2 and addressed in Stage 3. Flag any gaps.]

**Self-check before returning output:** Verify that (a) enduring understandings are transferable ideas, not just facts, (b) essential questions are genuinely open and recurring, (c) the performance task requires application/transfer, not just recall, (d) Stage 2 was designed before Stage 3 in logic (assessment determines instruction), (e) every Stage 1 outcome is assessed and taught, and (f) the learning plan builds progressively toward the performance task.
```

## 示例输出

**情景：** *预期结果：“学生将理解自然选择如何驱动生物适应，掌握核心概念（适应、变异、遗传、自然选择、进化），并能解释特定生物的特征如何适应其环境以及种群如何随时间变化。” / 学生水平：“九年级” / 单元时长：“8 课时（每课时 50 分钟）” / 学科领域：“科学（生物）”*

---

## 单元计划：自然选择与适应

**适用对象：** 九年级
**学科：** 科学（生物）
**时长：** 8 课时（每课时 50 分钟）

### 阶段 1：预期结果

**持久理解（Enduring Understandings）**
1. 学生将理解：**拥有更适应环境的特征的生物体更有可能存活并繁殖，这些特征会传递给后代——从而导致种群随时间推移发生变化。**（这就是自然选择的机制。）
2. 学生将理解：**种群内部的变异对自然选择至关重要——没有变异，环境就没有可供“选择”的对象。**
3. 学生将理解：**适应是自然选择历经多代作用的结果，而不是个体生物的有意选择。**（生物体不会主动选择去适应；种群之所以改变，是因为更适应的个体留下了更多后代。）

**核心问题（Essential Questions）**
1. “为什么生物体长成它们现在的样子？”（贯穿全单元——学生的回答从第 1 课的“因为它们适应了”深化到第 8 课的“因为自然选择偏爱了那些在特定环境中提高存活率与繁殖率的特征”。）
2. “如果环境发生改变，原本高度适应旧环境的生物会发生什么？”（推动理解：适应不是永久的——它取决于具体环境。）
3. “为什么变异很重要？”（将遗传学与进化联系起来——没有变异，自然选择便无法运作。）

**学生将知道：**
- 适应（adaptation）、变异（variation）、遗传（inheritance）、自然选择（natural selection）、进化（evolution）和物种（species）的定义
- 具名生物中结构适应、行为适应与生理功能适应的例子
- 变异源于基因差异（有时也受环境因素影响）
- 自然选择所需的四个条件：变异、遗传、选择压力、差异化繁殖
- 达尔文对自然选择进化论的贡献

**学生将能够：**
- 解释某具名生物的特定特征如何帮助其在环境中生存
- 逐步描述自然选择的过程
- 预测当环境变化时种群可能发生什么变化
- 区分拉马克式（用进废退/获得性遗传）与达尔文式（自然选择）解释——并说明为何拉马克的解释不正确

### 阶段 2：评估证据

**表现性任务：“火山岛”**

*情景：* “一座火山岛上生活着一群甲虫。甲虫的颜色从绿色到棕色不等。岛上原本覆盖着绿色植被。最近一次火山喷发使岛上大部分区域覆盖了深灰色火山灰。科学家预测，50 代之后甲虫种群的外貌将大不相同。你的任务：运用自然选择理论撰写一份科学解释，预测甲虫种群将如何变化以及为什么。你的解释必须包含自然选择的全部四个条件，并回应‘甲虫个体会自己选择变色’这一常见迷思概念。”

*学生产出：* 一份 200–300 词的科学解释。

*任务评估内容：*
- 持久理解 1：自然选择机制（能否正确解释这一过程？）
- 持久理解 2：变异的作用（是否指出种群中原本存在的颜色变异至关重要？）
- 持久理解 3：适应不是自主选择（是否解释是种群在变化，而非甲虫个体在变色？）
- 核心问题 1 与 2：适应环境的生物 + 环境变化
- 知识：四个条件、准确术语
- 技能：分步解释、区分达尔文推理与拉马克推理

*简明成功标准：*
- 指出种群中原本存在的变异（颜色分布范围）
- 解释选择压力（深色甲虫在火山灰上伪装更好）
- 描述差异化存活与繁殖
- 解释特征向后代的遗传
- 预测跨越世代的种群变化
- 回应并驳斥甲虫“选择”变色的迷思概念

**其他证据**

| 课时 | 评估方式 | 评估的阶段 1 结果 |
|------|----------|-------------------|
| 2 | 离堂小测：“说出北极熊的 3 项适应特征，并解释每项如何帮助它生存” | 知识（适应）；技能（解释特征与环境的联系） |
| 4 | 小白板关键节点提问（hinge question）：“长颈鹿伸长脖子去够树叶，它的后代出生时脖子就更长。这是达尔文式还是拉马克式解释？为什么？” | 理解 3（适应不是自主选择）；知识（拉马克 vs. 达尔文） |
| 6 | 同伴互评解释：学生用新例子向同伴解释自然选择；同伴对照 4 步核查清单检查 | 知识（四个条件）；技能（分步解释） |

### 阶段 3：学习计划

**第 1 课时——导入与探索：“为什么生物体长成它们现在的样子？”**
- 展示 5 张奇特适应特征的图片（鮟鱇鱼、仙人掌、北极狐、变色龙、深海管虫）。学生讨论：“为什么这种生物长这样？这个特征解决了什么问题？”
- 引入核心问题 1。学生写下初始回答。
- 界定“适应”——结构性、行为性、生理功能性。学生对这 5 个例子进行分类。
- *铺垫指向：* 阶段 2 表现性任务（解释特征与环境的关联）。

**第 2 课时——装备：适应的类型**
- 深入研习 3 种生物及其适应特征（一种结构性、一种行为性、一种生理功能性）。
- 学生书面解释：“【特征】如何帮助【生物】在【环境】中生存？”
- *离堂小测评估。*
- *铺垫指向：* 阶段 2 表现性任务（解释特征如何适应环境）。

**第 3 课时——探索：变异**
- 实操：测量种群中的变异（例如手掌跨度、叶片大小或模拟甲虫数据）。
- 核心概念：每个种群内部都存在变异。部分变异具有遗传性。
- 引入核心问题 3：“为什么变异很重要？”
- *铺垫指向：* 持久理解 2（变异对自然选择至关重要）。

**第 4 课时——装备：逐步拆解自然选择**
- 显性教学：自然选择的 4 个条件（变异、遗传、选择压力、差异化繁殖）。
- 以桦尺蛾作为样例——分步示范如何写出解释。
- 引入拉马克 vs. 达尔文的区分。常见迷思概念：“长颈鹿自己伸长了脖子”。
- *关键节点提问评估。*
- *铺垫指向：* 表现性任务（学生必须运用这 4 个条件）。

**第 5 课时——探索与反思：模拟实验**
- 模拟活动：“适者生存”——在不同背景板上使用彩色纸片“生物”。学生观察哪些“被吃掉”（被淘汰）、哪些存活。重复 3 个“世代”。
- 学生观察到种群随时间发生变化——而没有任何个体发生改变。
- 重温核心问题 1：更新回答。
- *铺垫指向：* 持久理解 3（改变的是种群，不是个体）。

**第 6 课时——装备与评价：练习撰写解释**
- 学生使用新例子（例如细菌的抗生素耐药性）练习撰写自然选择解释。
- 使用表现性任务标准中的 4 步核查清单开展同伴互评。
- 教师巡视并收集常见错误，用于全班反馈。
- *铺垫指向：* 表现性任务（练习即将被评估的完全相同的技能）。

**第 7 课时——表现性任务：“火山岛”**
- 学生在有支持条件下完成表现性任务。
- 为 EAL 学生提供句型开头。向所有学生提供词汇库（对拓展水平学生可撤除）。
- 教师巡视，记录常见迷思概念，供第 8 课时反馈使用。

**第 8 课时——反思与拓展：反馈与迁移**
- 发回批改后的作业并附带针对性反馈。
- 全班复盘最常见错误（尤其是拉马克式推理）。
- 拓展任务：“人类使用抗生素已有约 80 年，细菌正在产生耐药性。用自然选择解释原因。”
- 重温全部三个核心问题：学生写出最终回答，并与第 1 课时的回答对比。

### 对齐核查

| 阶段 1 结果 | 是否在阶段 2 评估？ | 是否在阶段 3 教授？ | 是否对齐？ |
|-------------|-------------------|-------------------|----------|
| 理解 1（自然选择机制） | 表现性任务 + 第 6 课同伴互评 | 第 4、5、6 课 | ✓ |
| 理解 2（变异至关重要） | 表现性任务 | 第 3 课 | ✓ |
| 理解 3（适应非自主选择） | 表现性任务 + 第 4 课关键节点提问 | 第 4、5 课 | ✓ |
| 知识（关键词汇） | 所有评估均要求使用术语 | 第 1–4 课渐进引入 | ✓ |
| 技能（解释特征与环境关联） | 第 2 课离堂小测 + 表现性任务 | 第 1、2 课 | ✓ |
| 技能（分步解释） | 表现性任务 + 第 6 课同伴检查 | 第 4、6 课（示范与练习） | ✓ |

未检测到错位。所有阶段 1 结果均已覆盖评估与教学。

---

## 已知局限

1. **单元计划提供的是结构，而非逐分钟的详案。** 每课时条目描述了核心活动及其目的，但未包含完整时间分配、分层细节、教学资源或教师话术脚本。教师应以阶段 3 序列为框架，结合其他技能（如 `explicit-instruction-sequence-builder`、`lesson-opening-designer` 等）开发具体教案。

2. **逆向设计以清晰的预期结果为前提。** 如果教师最初的结果陈述很模糊（“学生将学习自然选择”），UbD 结构的精确度就会下降。单元质量取决于输入的具体性。若设计单元前需要先厘清学习结果，可与 `competency-unpacker` 串联使用。

3. **表现性任务针对特定情境设计，可能需要调适。** “火山岛”情景适用于本生物主题，但未必能直接照搬到其他学校的资源或评估要求中。教师应对照自身具体评估框架审查表现性任务，在保留评估设计原则的前提下调整情景。
