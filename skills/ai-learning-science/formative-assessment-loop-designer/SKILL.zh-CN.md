---
# AGENT SKILLS STANDARD FIELDS (v2)
name: formative-assessment-loop-designer
description: "设计自适应评估闭环，使学生的每一次作答都触发下一步教学动作。适用于构建技术增强的形成性评估循环。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "ai-learning-science/formative-assessment-loop-designer"
skill_name: "AI 系统形成性评估闭环设计器"
domain: "ai-learning-science"
version: "1.0"
evidence_strength: "strong"
evidence_sources:
  - "Black & Wiliam (1998) — Assessment and classroom learning (seminal meta-analysis)"
  - "Black & Wiliam (2009) — Developing the theory of formative assessment"
  - "Wiliam (2011) — Embedded formative assessment"
  - "VanLehn (2006) — The behavior of tutoring systems (inner loop vs. outer loop)"
  - "Shute & Zapata-Rivera (2012) — Adaptive educational systems"
input_schema:
  required:
    - field: "learning_objective"
      type: "string"
      description: "形成性评估闭环应当监控的具体学习目标——学生正在努力学习的内容"
    - field: "current_assessment_approach"
      type: "string"
      description: "当前情境下评估如何运作——教师何时检查理解、检查什么以及如何处理收集到的信息"
  optional:
    - field: "student_level"
      type: "string"
      description: "年龄/年级及能力水平"
    - field: "subject_area"
      type: "string"
      description: "课程学科"
    - field: "ai_system_capabilities"
      type: "string"
      description: "AI 系统能够做什么——实时监控、自适应提问、仪表盘报告或其他"
    - field: "class_size"
      type: "string"
      description: "系统需要同时支持多少名学生"
    - field: "assessment_frequency"
      type: "string"
      description: "评估数据的收集频率——持续、按任务、每日、每周"
output_schema:
  type: "object"
  fields:
    - field: "assessment_loop_design"
      type: "object"
      description: "完整的形成性评估闭环——评估什么、如何评估、何时评估以及如何处理结果"
    - field: "elicitation_strategies"
      type: "array"
      description: "如何引出学生理解——揭示思维的具体问题、任务和探查方式"
    - field: "interpretation_framework"
      type: "object"
      description: "如何解读学生作答——哪些模式表明理解、部分理解和迷思概念"
    - field: "response_actions"
      type: "object"
      description: "基于评估数据采取什么行动——由不同评估结果触发的具体教学动作"
chains_well_with:
  - "adaptive-hint-sequence-designer"
  - "ai-feedback-design-principles"
  - "learning-analytics-interpretation-guide"
  - "cognitive-tutoring-architecture-designer"
teacher_time: "5 分钟"
tags: ["formative-assessment", "Black-Wiliam", "assessment-loop", "adaptive", "feedback", "VanLehn", "inner-loop", "outer-loop"]
---

# AI 系统形成性评估闭环设计器

## 本技能的作用

为 AI 赋能的学习环境设计完整的形成性评估闭环——即持续引出学生理解证据、解读证据并实时调整教学的循环。Black & Wiliam（1998）的开创性元分析证明，形成性评估是教育中最有力的干预手段之一（效应量为 0.40–0.70），但**前提是**评估数据真正改变了接下来发生的事情。不会引发教学调整的评估只是一次测验。本技能设计整个闭环：评估什么（不只是答案，还有**思维**）、如何评估（揭示理解的问题、任务与探查）、如何解读结果（区分真正理解与表面表现），以及如何利用结果（针对特定评估模式的具体教学响应）。VanLehn（2006）区分了“内循环（inner loop）”评估（在每个解题步骤实时进行）和“外循环（outer loop）”评估（在任务层面、题目之间进行）。AI 系统独特之处在于能够胜任内循环评估——逐步监控学生推理并实时调整——而这正是产生最大学习收益的环节。

## 实证基础

Black & Wiliam（1998）对形成性评估研究进行了最具影响力的综述，分析了超过 250 项研究，发现效应量在 0.40 到 0.70 之间——高于大多数教育干预措施。他们将形成性评估定义为“教师和/或其学生开展的所有活动，这些活动提供信息作为反馈，用于修改他们正在进行的教与学活动”。核心洞见在于：**评估**本身不是最有价值的部分——**修改教学**才是。没有教学调整的数据收集只是换了个标签的终结性评估。Black & Wiliam（2009）提出了更精细的理论框架，确定了形成性评估的五项核心策略：（1）明确并分享学习意图与成功标准，（2）设计能引出学习证据的有效课堂讨论与任务，（3）提供推动学习者前进的反馈，（4）激活学生成为彼此的教学资源，以及（5）激活学生成为自己学习的主人。所有五项策略都包含一个循环：引出 → 解读 → 行动。Wiliam（2011）将这一框架转化为实用的课堂策略，强调形成性评估必须**嵌入**教学之中——不是额外附加的活动，而是检查、调整和响应的持续过程。他认为有效形成性评估的最大障碍不是数据收集，而是**数据使用**：教师经常收集了数据，却没有据此改变教学。VanLehn（2006）分析了辅导系统的行为，识别出评估闭环的两个层级。“外循环”在题目之间运行：学生完成一道题后，系统决定下一步做什么（另一道类似题、更难的题、复习或新主题）。“内循环”在题目内部运行：在每一步，系统评估学生作答并提供反馈、提示或脚手架。VanLehn 发现内循环是决定 ITS 有效性的更重要因素——在步骤级进行评估和响应的系统显著优于仅在题目级评估的系统。Shute & Zapata-Rivera（2012）综述了自适应教育系统，发现最有效的系统将持续评估与即时教学自适应结合起来——创造了一个“紧凑”的形成性评估闭环，最大限度缩短了评估与响应之间的时间间隔。

## 输入规范

教师必须提供：
- **学习目标（Learning objective）：** 学生正在努力学习的内容。*例如：“理解面积与周长的区别——何时使用哪一个、如何计算以及为什么它们相互独立（一个图形可以面积大而周长小，反之亦然）” / “写出能提出清晰主张而非仅陈述事实或宣布主题的有效主题句” / “理解供求关系——价格变化如何影响供给量与需求量，以及均衡价格如何决定”*
- **当前评估方式（Current assessment approach）：** 目前如何检查理解。*例如：“我在课末用一张 3 道题的离堂小测（exit ticket）检查。如果大多数学生做对就继续下一课，否则下节课重教” / “我在周末批改作文并给出书面反馈” / “AI 系统每 10 道题给一次小测，但不会根据结果改变后续内容”*

可选项（如可用则由上下文引擎注入）：
- **学生水平（Student level）：** 年级与能力水平
- **学科领域（Subject area）：** 课程学科
- **AI 系统能力（AI system capabilities）：** 技术能够支持的功能
- **班级规模（Class size）：** 学生人数
- **评估频率（Assessment frequency）：** 多久收集一次数据

## 提示词（Prompt）

```
You are an expert in formative assessment design for AI-enabled learning environments, with deep knowledge of Black & Wiliam's (1998, 2009) formative assessment framework, Wiliam's (2011) practical implementation strategies, VanLehn's (2006) inner-loop/outer-loop distinction, and Shute & Zapata-Rivera's (2012) adaptive assessment systems. You understand that formative assessment is not a type of test — it is a PROCESS of continuously eliciting evidence of understanding and using that evidence to adjust instruction. You also understand VanLehn's critical finding: assessment and feedback at the STEP level (inner loop) is dramatically more effective than assessment at the TASK level (outer loop).

CRITICAL PRINCIPLES:
- **Assessment must change instruction.** If the assessment data doesn't lead to a different instructional response, it's not formative — it's just a test. For every assessment point, specify WHAT CHANGES based on the result. "If the student gets it right, move on" is insufficient. "If the student gets it right, increase difficulty by X; if wrong in way A, respond with action A; if wrong in way B, respond with action B" — that's formative.
- **Assess THINKING, not just answers.** A correct answer might hide a misconception (right answer, wrong reasoning). An incorrect answer might contain valuable partial understanding. The assessment must probe the reasoning BEHIND the answer. In an AI system: require students to show working, explain their thinking, or select from options that reveal specific reasoning patterns.
- **Inner-loop assessment is more powerful than outer-loop.** VanLehn (2006): assessing at each problem step (and responding immediately) produces better learning than assessing only at the end of a problem. Design the loop to operate at the step level where possible.
- **Use multiple elicitation methods.** Don't rely solely on correct/incorrect. Use: diagnostic questions (MCQs where each wrong answer maps to a specific misconception), explanation prompts ("Why did you choose that?"), confidence ratings ("How sure are you?"), and process observations (how long did they take? did they use a hint?).
- **The assessment loop must be TIGHT.** The shorter the delay between assessment and instructional response, the more effective the formative process. An AI system can respond in seconds. Exploit this advantage — don't collect data now and act on it next week.

Your task is to design a formative assessment loop for:

**Learning objective:** {{learning_objective}}
**Current assessment approach:** {{current_assessment_approach}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Student level:** {{student_level}} — if not provided, design for a general secondary school context.
**Subject area:** {{subject_area}} — if not provided, infer from the objective.
**AI system capabilities:** {{ai_system_capabilities}} — if not provided, design for an AI system that can present problems, monitor responses, provide feedback, and adapt problem selection in real time.
**Class size:** {{class_size}} — if not provided, assume a class of 30 students working individually on AI-enabled devices.
**Assessment frequency:** {{assessment_frequency}} — if not provided, design for continuous inner-loop assessment with outer-loop checks every 5-10 problems.

Return your output in this exact format:

## Formative Assessment Loop: [Learning Objective]

**Objective:** [What students are learning]
**Current approach:** [How assessment works now]
**Redesigned approach:** [How the formative loop works — one-sentence summary]

### Loop Architecture

[The complete assessment loop structure — inner loop (step-level) and outer loop (task-level)]

**Inner Loop (within each problem):**
[What is assessed at each step, how, and what the response is]

**Outer Loop (between problems):**
[What is assessed after each problem/set of problems, and how it determines what comes next]

### Elicitation Strategies

[The specific methods for surfacing student understanding — not just "quiz them" but the SPECIFIC question designs, process observations, and explanation prompts]

**Strategy [N]: [Name]**
- **What it assesses:** [What aspect of understanding]
- **How it works:** [The specific mechanism]
- **Example:** [A concrete example for this learning objective]
- **What to look for:** [What different responses reveal about understanding]

### Interpretation Framework

[How to interpret student responses — the decision rules that connect assessment evidence to instructional actions]

| Evidence Pattern | What It Probably Means | Confidence | Instructional Response |
|---|---|---|---|
| [Pattern] | [Interpretation] | [High/Moderate/Low] | [What the system does next] |

### Response Actions

[The specific instructional adjustments triggered by different assessment results — not just "reteach" but exactly how to reteach]

### Teacher Dashboard

[What the teacher needs to see — the key metrics and alerts that inform teacher-level decisions, separate from the AI's real-time responses]

### Loop Validation

[How to check that the assessment loop is actually improving learning — the meta-assessment of the assessment]

**Self-check before returning output:** Verify that (a) every assessment point triggers an instructional response, (b) thinking is assessed not just answers, (c) inner-loop assessment is included, (d) multiple elicitation methods are used, and (e) the loop is tight (minimal delay between assessment and response).
```

## 示例输出

**情景：** *学习目标：“理解面积与周长的区别——何时使用哪一个、如何计算以及为什么它们相互独立（一个图形可以面积大而周长小，反之亦然）” / 当前评估方式：“我在不同的课上分别教授面积和周长，然后发一张有 20 道计算题（10 道面积、10 道周长）的练习单。我批改后，如果超过三分之一的学生在任一部分低于 7/10 就重教。主要问题在于学生在练习单上能正确计算两者，但在考试中却会**混淆**它们——被问及面积时用了周长公式，反之亦然。计算本身不是问题；知道**该用哪个**计算才是问题。” / 学生水平：“六年级” / 学科领域：“数学——测量” / AI 系统能力：“能够呈现题目、接收自由文本和选择题作答、记录作答时长、提供反馈并自适应选题的 AI 辅导系统。还能展示图形图片/示意图。” / 评估频率：“持续”*

---

## 形成性评估闭环：面积 vs. 周长

**目标：** 理解何时使用面积与周长、各自如何计算以及为何它们相互独立
**当前方式：** 分开教学 → 混合计算练习单 → 批改并重教
**重构方式：** 持续评估闭环，使用将概念理解与程序流畅性分离的诊断性问题，在计算前先探查**该用哪种**计算

### 闭环架构

**内循环（每道题目内部）：**

第 1 步——**识别检查：** 在学生进行任何计算之前，系统先问：“这是一道求面积的题还是求周长的题？你是怎么知道的？”这是**核心**评估点。最常见的错误（用错公式）正发生在**这一步**，而不是计算过程中。系统先评估学生的概念识别，再允许其继续。

第 2 步——**方法检查：** 识别之后，系统问：“你将计算什么？用一句话描述你的方法。”这能揭示学生是否知道所识别概念对应的程序。正确识别出“面积”却描述“我要把所有边加起来”的学生，虽然识别正确，但存在程序性错误。

第 3 步——**计算检查：** 学生执行计算，系统核查数值答案。若正确则继续；若错误，判断误差是算术失误（方法正确但算错）还是概念性错误（应用了错误方法）。

第 4 步——**单位检查：** 系统检查学生是否使用了正确单位（面积用 cm²，周长用 cm）。即使数值正确，单位错误也可能暴露概念混淆。

**外循环（每 5 道题一次）：**

每完成 5 道题后，系统回顾内循环作答模式：
- **若识别准确率 ≥ 80%：** 提升难度（更复杂图形、应用题、比较题）
- **若识别准确率 < 60%：** 切换至概念建构任务（比较周长相同但面积不同的图形）
- **若识别准确但计算常错：** 针对正确识别的概念提供计算练习
- **若模式混杂：** 呈现旨在精准定位具体混淆点的诊断题

### 引出策略

**策略 1：识别优先问题**
- **评估内容：** 学生是否知道题目问的是**哪一种**度量
- **运作方式：** 呈现一道应用题，在要求计算**之前**先问“这是在问面积还是周长？”这把概念识别与程序执行分离开来。
- **示例：** “一位农民想在一块长 20 米、宽 15 米的长方形田地四周建栅栏。这是一道面积题还是周长题？”随后再单独问：“算出答案。”
- **观察重点：** 正确识别“周长”的学生（因为建栅栏 = 绕着外圈围）vs. 说“面积”的学生（他们可能被“田地”这个词或两个维度数据触发了误判）

**策略 2：诊断性选择题**
- **评估内容：** 错误答案背后的具体迷思概念
- **运作方式：** 设计一道每个错误选项都对应一种特定错误的题目。学生的选择能揭示其推理过程，而不仅仅是正确与否。
- **示例：** “一个长方形长 8cm、宽 5cm，它的面积是多少？”选项：（a）40 cm² [正确]，（b）26 cm [错算成了周长]，（c）26 cm² [错算了周长但用了面积单位]，（d）13 cm [只算了半周长]。每个错误选项诊断不同的问题。
- **观察重点：** （b）= 算错了度量；（c）= 算错了度量**且**不理解单位含义；（d）= 周长理解不完整。

**策略 3：概念对比任务**
- **评估内容：** 学生是否理解面积与周长是**相互独立**的
- **运作方式：** 展示两个图形，问“哪个面积更大？哪个周长更长？”，且两问的答案**不同**（一个面积大，另一个周长长）。这能测试最深层的概念理解。
- **示例：** 图形 A：10cm × 2cm 的长方形（面积 20，周长 24）。图形 B：5cm × 5cm 的正方形（面积 25，周长 20）。“哪个面积更大？哪个周长更长？”正确答案：B 面积更大，A 周长更长。
- **观察重点：** 两问都选同一个图形的学生很可能认为面积与周长正相关（“图形越大，什么都越大”）。这是最需要纠正的迷思概念。

**策略 4：信心校准作答**
- **评估内容：** 元认知准确性——学生是否知道自己是否真的懂
- **运作方式：** 作答后，学生评估信心（确定 / 觉得是 / 猜的）。系统追踪校准度：高信心 + 答错 = 迷思概念（坚信错误观念）；低信心 + 答对 = 脆弱知识（蒙对或不确定）。
- **示例：** 学生自信地在一道围栅栏问题中选“周长”→ 正确且自信 = 扎实理解。学生不确定地选“周长”→ 正确但不确定 = 发展中的理解，需要更多练习。
- **观察重点：** 持续的高信心错误表明存在根深蒂固的迷思概念，需要直接正面冲击，而非仅仅多做练习。

### 解读框架

| 证据模式 | 可能含义 | 置信度 | 教学响应 |
|---|---|---|---|
| 识别正确、计算正确、单位正确 | 对该题型有扎实理解 | 高 | 提高难度——更复杂图形、多步问题或对比任务 |
| 识别正确、计算错误 | 程序性漏洞，非概念混淆 | 高 | 提供计算脚手架——学生知道该做**什么**，但算术出错 |
| 识别错误（面积↔周长混淆） | 核心概念混淆——学生无法可靠区分两个概念 | 高 | **停止**计算练习。切换至概念建构：对比、定义、视觉演示、真实生活情境 |
| 简单题识别正确，应用题识别错误 | 脆弱的概念知识——能在显性语境下识别，但不能在应用语境下识别 | 中 | 增加带显性识别提示的应用题（“这是关于铺满表面还是绕着边缘走一圈？”） |
| 数值正确但单位错误（如 40 cm 而非 40 cm²） | 可能理解概念，但不理解维度的数学表征 | 中 | 直接教学解释为何面积使用平方单位（衡量单位正方形的个数） |
| “更大面积”和“更大周长”对比选同一个图形 | 认为面积与周长存在固定正相关 | 高 | 关键干预：展示多个面积增大但周长减小的反例（及反之） |
| 高信心 + 持续出错 | 根深蒂固的迷思概念 | 高 | 认知冲突：呈现一个推翻其信念的案例，并要求其解释矛盾 |
| 低信心 + 作答正确 | 正在形成但尚脆弱的理解 | 中 | 更多带即时正面反馈的练习，在提升能力的同时建立信心 |

### 响应动作

**动作 1：概念建构模式（由识别错误触发）**
AI 从计算练习切换为概念建构活动：
- 展示一个长方形并提问：“对于这个图形，面积是什么意思？周长是什么意思？请通过点击/高亮指给我看。”（面积 = 内部表面，周长 = 外部边缘）
- 呈现真实生活情景：“你想粉刷一面墙——面积还是周长？你想给一幅画装框——面积还是周长？你想给房间买地毯——面积还是周长？”
- 使用“同周长、不同面积”演示：展示三个周长都是 24cm 但面积截然不同的图形（1×11, 4×8, 6×6）。提问：“周长怎么可能相同而面积却不同？”

**动作 2：程序巩固模式（由识别正确但计算错误触发）**
AI 针对**正确识别**的概念提供带脚手架的计算练习：
- 面积：在计算前显示网格覆盖层，让学生先数方格，再渐隐网格。
- 周长：在相加前沿着图形外围显示箭头，再渐隐箭头。
- 两者：提供即时计算反馈并展示纠正步骤。

**动作 3：整合迁移模式（由持续成功触发）**
AI 引入多步问题与对比问题：
- “同时求出这个图形的面积**和**周长。哪个数值更大？这让你感到意外吗？”
- “设计一个面积为 24cm² 的长方形。它的周长是多少？你能设计另一个面积相同但周长不同的长方形吗？”
- 要求学生根据语境自行判断需要哪种度量的应用题。

### 教师仪表盘

教师需要看到：

**班级概览：**
- 处于各模式（概念建构 / 程序巩固 / 整合迁移）的学生百分比
- 全班最常见的错误模式（如果 60% 的学生都在混淆面积和周长，这就需要全班干预）
- 卡住的学生（在概念建构模式下做了 10 道以上仍无改善——可能需要教师介入）

**个体预警：**
- “学生 X 信心很高但识别准确率仅 40%——存在根深蒂固的迷思概念，建议教师面谈”
- “学生 Y 已在程序模式停留 15 分钟——计算准确率未见提升，请检查底层数感漏洞”
- “学生 Z 已完成所有整合任务——已准备好接受拓展（组合图形、圆、表面积）”

**核心指标：识别准确率 vs. 计算准确率。** 如果班级识别准确率低于 70% 而计算准确率高于 80%，当前的评估方式（计算练习单）正在掩盖真正的问题。教师应优先开展概念工作，而不是布置更多计算练习。

### 闭环验证

如何检验评估闭环是否真正有效：

1. **识别任务的前后测对比。** 在 AI 闭环开始前，进行一次 5 道题的纯识别小测（不做计算）。经过 2 次 AI 闭环练习后重复该小测。如果识别准确率没有提高，说明闭环中的概念建构响应需要重新设计。

2. **迁移测试。** 在 AI 序列结束后，给出一道 AI 从未用过的新题型（例如估算一张包装纸是否够包一份礼物——需要在陌生情境下理解面积）。如果学生能够迁移，说明闭环正在建立理解，而不仅仅是训练熟悉题型。

3. **延迟测试。** 在 AI 序列结束两周后，再次给出同样的识别小测。如果分数大幅下降，说明闭环只产生了**短期**表现，而非**长期**学习。考虑在闭环中加入间隔提取（在学生继续学习后续内容后偶尔穿插回访面积/周长识别）。

---

## 已知局限

1. **形成性评估闭环需要持续的数据流。** 上述设计假定 AI 系统能够实时评估学生作答并立即自适应调整。采用批处理（收集数据、夜间分析、明天再调整）的系统无法实现内循环。外循环仍然可行且有价值，但内循环评估带来的学习收益（VanLehn, 2006）需要实时处理。

2. **解读框架具有概率性。** 为周长题选择“面积”的学生**很可能**存在概念混淆——但也可能只是看错了题、点错了选项或不认识“perimeter（周长）”这个词。系统绝不应仅凭单次作答就下定论。上述解读框架使用作答**模式**（多道题）来建立诊断置信度。

3. **Black & Wiliam（1998）的元分析涵盖了广泛的形成性评估实践。** 其效应量（0.40–0.70）适用于广义的形成性评估，而非特指由 AI 实施的形成性评估。原则是可靠的，但 AI 形成性闭环在**这一**具体情境下的效应量尚未经过实证测量。该设计是循证启发的，而非实证已证明的。

4. **教师仪表盘数据可能造成信息过载。** 上述仪表盘提供了关于个体学生与班级模式的详细信息。在 30 人的班级中这是可管理的；在 120 人的年级中，数据量可能令人应接不暇。面向更大规模的仪表盘设计需要更激进的筛选与摘要机制。

5. **评估闭环可能无意中窄化课程。** 如果 AI 闭环完全聚焦于面积 vs. 周长的识别与计算，学生可能在这一具体技能上表现出色，却错失了更广泛的数学理解（作为概念的测量、与其他主题的联系）。Wiliam（2011）警告说，形成性评估应当服务于学习，而非定义学习。
