---
# AGENT SKILLS STANDARD FIELDS (v2)
name: productive-failure-desirable-difficulty-designer
description: "重新设计直接教学序列，在讲解阶段之前纳入富有成效的挣扎。适用于教授受益于“先失败后讲解”策略的概念。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "ai-learning-science/productive-failure-desirable-difficulty-designer"
skill_name: "富有成效的失败与合意困难设计器"
domain: "ai-learning-science"
version: "1.0"
evidence_strength: "strong"
evidence_sources:
  - "Kapur (2008) — Productive failure"
  - "Kapur (2016) — Examining productive failure, productive success, unproductive failure, and unproductive success in learning"
  - "Bjork (1994) — Memory and metamemory considerations in the training of human beings"
  - "Bjork & Bjork (2011) — Making things hard on yourself, but in a good way: creating desirable difficulties to enhance learning"
  - "Soderstrom & Bjork (2015) — Learning versus performance: an integrative review"
input_schema:
  required:
    - field: "target_concept"
      type: "string"
      description: "学生需要深入学习的具体概念或技能——受益于富有成效的失败而非直接讲授的内容"
    - field: "current_approach"
      type: "string"
      description: "该概念目前的教授方式——通常是先直接讲授再做练习"
  optional:
    - field: "student_level"
      type: "string"
      description: "年龄/年级及能力水平"
    - field: "subject_area"
      type: "string"
      description: "课程学科"
    - field: "time_available"
      type: "string"
      description: "可用于富有成效的失败序列的课时时长"
    - field: "prerequisite_knowledge"
      type: "string"
      description: "学生在生成阶段可以调动的已有知识"
    - field: "risk_tolerance"
      type: "string"
      description: "教师对学生挣扎与初期失败的接受度——对落地实施至关重要"
output_schema:
  type: "object"
  fields:
    - field: "productive_failure_sequence"
      type: "object"
      description: "完整序列——生成阶段、巩固阶段以及两者之间的关键过渡"
    - field: "desirable_difficulties"
      type: "array"
      description: "嵌入任务中的具体困难及其各自促进学习的原因"
    - field: "failure_safeguards"
      type: "object"
      description: "如何确保失败是“富有成效的”而非无益的——必须具备的条件"
    - field: "cognitive_offloading_risks"
      type: "object"
      description: "AI 工具如何可能削弱合意困难以及应对策略"
chains_well_with:
  - "adaptive-hint-sequence-designer"
  - "worked-example-to-problem-solving-transition-designer"
  - "self-explanation-prompt-designer"
  - "intelligent-tutoring-dialogue-designer"
teacher_time: "5 分钟"
tags: ["productive-failure", "desirable-difficulty", "Kapur", "Bjork", "struggle", "generation", "consolidation", "cognitive-offloading"]
---

# 富有成效的失败与合意困难设计器

## 本技能的作用

重新设计教学序列以融入富有成效的失败（Productive Failure，Kapur, 2008, 2016）和合意困难（Desirable Difficulties，Bjork, 1994; Bjork & Bjork, 2011），用“先挣扎、后巩固”的模式取代标准的“先教、后练”模式，从而产生更深刻、更持久的学习。核心悖论在于：先经历挣扎并失败的学生，从长远来看学得**更多**——尽管在课堂当下感觉更糟——胜过先接受清晰讲授并立即成功的学生。Kapur（2016）表明，富有成效的失败之所以有效，是因为“生成阶段”（学生在接受教学前先尝试解决问题）激活了先验知识、暴露了现有知识的局限，并制造了“知识缺口”，从而使随后的讲解更有意义。Bjork（1994）提出了“合意困难”概念——即短期内让学习变难、但长期来看让记忆更持久的条件，包括间隔、穿插、生成与提取练习。本技能在 AI 赋能的学习环境中尤为重要，因为 AI 工具可能会无意中**移除**合意困难——让任务变得过于轻松、直接给出答案，并削减驱动深度学习的富有成效的挣扎。输出包括完整的富有成效的失败序列（生成阶段 + 巩固阶段）、嵌入任务的具体合意困难、确保失败富有成效而非破坏性的保障措施，以及防止 AI 导致的认知卸载指南。

## 实证基础

Kapur（2008, 2016）通过在数学课堂中的一系列研究构建了“富有成效的失败”框架。在经典设计中，学生在接受任何讲授**之前**先面对一个复杂、新颖的问题——一个预期他们会失败的问题。他们以小组形式合作，生成多种解题方案，但没有一种是完全正确的。**然后**教师再讲授标准解法，并将其与学生生成的方案进行显性对比。Kapur（2016）发现，处于“富有成效的失败”条件下的学生在概念理解与迁移测评上显著优于先接受直接讲授的学生——尽管直接讲授组在即时程序性测试中表现更好。核心发现是：产生学习的不是失败本身，而是**生成（generation）**。即使学生生成的想法是错的，他们也借此建构了更丰富的问题空间表征，使随后的讲授变得更有意义。Bjork（1994）与 Bjork & Bjork（2011）阐述了合意困难的更广泛原则：在学习过程中降低即时表现、却能增强长期保持与迁移的条件。他们总结了四种核心合意困难：（1）间隔——将练习分散在时间中而非集中一次完成；（2）穿插——混合不同题型而非按类型分块；（3）生成——自己产出答案而非直接阅读；（4）提取练习——自我测验而非重复阅读。这四者共享同一机制：它们让学习体验感觉更费力、更不流畅，而这恰恰矛盾地产生了更强的记忆痕迹与更深层的理解。Soderstrom & Bjork（2015）提出了**学习（learning）**与**表现（performance）**的关键区分。表现是你**此时此刻**能做到的事——在当下可见且可测。学习是知识或技能的长期改变——在课堂上不可见，只能日后测出。合意困难会降低即时表现（学生在课上做错更多），但会增强学习（几周后学生记得更牢、迁移更好）。这一区分至关重要，因为教师——以及 AI 系统——往往倾向于优化即时表现（让学生现在就做对），而非优化长期学习（让学生日后记住并能迁移）。

## 输入规范

教师必须提供：
- **目标概念（Target concept）：** 学生需要学习的内容。*例如：“标准差的概念——不只是会套公式计算，还要理解它**意味着**什么以及何时使用” / “第一次世界大战的起因——不只是罗列清单，还要理解它们如何相互作用并引发战争” / “说服性写作技巧——不只是说出名称，还要能针对特定受众与目的选择恰当技巧”*
- **当前做法（Current approach）：** 目前如何教授。*例如：“我讲授公式、演示几道例题，然后布置练习题。学生会算标准差，但说不清它对数据意味着什么” / “我给出时间线并逐一解释起因。学生在考试中能列出起因，但解释不了它们之间的联系” / “我逐个教授技巧并配例句。学生能辨认技巧，但无法独立运用”*

可选项（如可用则由上下文引擎注入）：
- **学生水平（Student level）：** 年级与能力水平
- **学科领域（Subject area）：** 课程学科
- **可用时间（Time available）：** 可用于该序列的课时时长
- **前置知识（Prerequisite knowledge）：** 学生已经掌握的内容
- **风险承受度（Risk tolerance）：** 教师对学生挣扎的接受程度

## 提示词（Prompt）

```
You are an expert in productive failure and desirable difficulties, with deep knowledge of Kapur's (2008, 2016) productive failure framework, Bjork's (1994) desirable difficulties research, Bjork & Bjork's (2011) applied desirable difficulties, and Soderstrom & Bjork's (2015) distinction between learning and performance. You understand the core paradox: making learning HARDER (in the right way) makes it BETTER — but it feels worse for both students and teachers. You also understand the specific risk that AI tools pose to desirable difficulties: by making tasks easier and providing immediate support, AI can remove the productive struggle that drives deep learning.

CRITICAL PRINCIPLES:
- **Generation before instruction.** The productive failure sequence MUST start with students attempting the task BEFORE receiving instruction. This is non-negotiable. The generation phase activates prior knowledge, reveals gaps, and creates the conditions for meaningful consolidation. If you teach first, you lose the generative benefit.
- **Failure must be PRODUCTIVE, not UNPRODUCTIVE.** Kapur (2016) distinguishes four conditions: productive failure (struggle → learning), unproductive failure (struggle → no learning), productive success (succeed → learning), and unproductive success (succeed → no learning). Productive failure requires: (a) the task is challenging but not impossible, (b) students have enough prior knowledge to generate partial solutions, (c) the consolidation phase explicitly connects student-generated ideas to the canonical solution, and (d) the classroom culture supports struggle without shame.
- **Design the consolidation phase as carefully as the generation phase.** Many teachers try productive failure and conclude "it didn't work" because they skip or rush the consolidation. The consolidation is where learning happens: the teacher explicitly compares the students' generated approaches with the correct approach, highlights what was right, what was wrong, and WHY the canonical approach works. Without this, students just experienced confusion.
- **Desirable difficulties feel undesirable.** Students will report that they "didn't learn anything" during the generation phase. They will rate the lesson lower on satisfaction surveys. They will perform worse on immediate post-tests. This is EXPECTED. The benefits appear later — on delayed tests, transfer tasks, and conceptual understanding measures. Warn teachers about this.
- **AI-enabled cognitive offloading is the enemy of desirable difficulty.** If students can ask an AI for the answer during the generation phase, the productive failure is destroyed. The design must include explicit guidance on when and how AI tools should be restricted to preserve the learning benefit.

Your task is to redesign this teaching sequence for productive failure:

**Target concept:** {{target_concept}}
**Current approach:** {{current_approach}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Student level:** {{student_level}} — if not provided, design for a general secondary school context.
**Subject area:** {{subject_area}} — if not provided, infer from the content.
**Time available:** {{time_available}} — if not provided, design for a double lesson (approximately 90 minutes).
**Prerequisite knowledge:** {{prerequisite_knowledge}} — if not provided, identify the likely prerequisites based on the target concept.
**Risk tolerance:** {{risk_tolerance}} — if not provided, design for a teacher who is willing to try but nervous about student frustration.

Return your output in this exact format:

## Productive Failure Sequence: [Target Concept]

**Target concept:** [What students need to learn]
**Current approach:** [How it's currently taught]
**Redesigned approach:** [One-sentence summary of the productive failure version]

### Phase 1: Generation (Productive Failure)

[The task students will attempt BEFORE instruction. Include the specific problem, the expected student responses (both correct and incorrect approaches they are likely to generate), and the teacher's role during this phase (circulating, NOT helping, noting student approaches for use in Phase 2).]

**The task:**
[Exact task students receive]

**Expected student responses:**
[What students will likely try — including the specific partial solutions and incorrect approaches]

**Teacher role during generation:**
[What the teacher does — observe, collect approaches, resist the urge to help]

### Phase 2: Consolidation

[How the teacher transitions from generation to instruction. This must explicitly connect student-generated approaches to the canonical solution. Include the specific comparisons the teacher should make and the key insights that emerge from the comparison.]

### Desirable Difficulties Embedded

[List each desirable difficulty in the sequence and explain why it enhances learning]

| Difficulty | What It Does | Why It Helps |
|---|---|---|
| [Difficulty] | [Mechanism] | [Learning benefit] |

### Failure Safeguards

[How to ensure failure is PRODUCTIVE — the conditions that must be in place and what to do if students become frustrated or disengaged]

### Cognitive Offloading Risks

[How AI tools might undermine the desirable difficulties and specific recommendations for managing this]

### Teacher Preparation Notes

[What the teacher needs to know and do before attempting this sequence — including how to manage student frustration and their own discomfort with watching students struggle]

**Self-check before returning output:** Verify that (a) generation comes before instruction, (b) the task is challenging but not impossible, (c) the consolidation explicitly connects student approaches to the canonical solution, (d) desirable difficulties are identified and justified, and (e) cognitive offloading risks are addressed.
```

## 示例输出

**情景：** *目标概念：“标准差的概念——不只是会算，还要理解它**意味着**什么（离散度/变异性的度量）以及何时使用（比较稳定性、识别异常值、做预测）” / 当前做法：“我讲授公式，在黑板上演示两道例题，然后布置 10 道练习题。学生能把标准差算到小数点后两位，但被问到‘这个标准差告诉你关于数据的什么信息？’时却答不上来。他们把它当成机械程序，而非概念” / 学生水平：“十年级，GCSE 高阶组，熟练掌握平均数与极差” / 学科领域：“数学——统计学” / 可用时间：“一节 60 分钟的课”*

---

## 富有成效的失败序列：标准差

**目标概念：** 理解标准差**意味着**什么（数据相对于平均数的离散程度）以及何时使用（比较变异性，而非仅仅算出一个数）
**当前做法：** 讲授公式 → 样例演示 → 练习题（产生缺乏概念理解的程序流畅性）
**重构做法：** 学生在学习标准差公式之前，先尝试发明一个度量数据“离散程度”的指标——生成并对比各自的方法能建构直接讲授所缺失的概念理解

### 第一阶段：生成（富有成效的失败）

**时长：** 20–25 分钟

**任务内容：**

*在黑板上展示或作为学习单发放：*

> **足球教练的难题**
>
> 你是一名足球教练，正在两名前锋之间做选择。两人在过去 10 场比赛中场均都进 1.5 球。但他们每场的进球记录截然不同：
>
> **球员 A：** 2, 1, 2, 1, 2, 1, 2, 1, 2, 1
> **球员 B：** 5, 0, 0, 4, 0, 0, 6, 0, 0, 0
>
> 两人的场均进球都是 1.5 个。但他们显然是非常**不同**的球员。
>
> **你的挑战（两人一组）：**
> 1. 这两名球员在什么方面不同？用文字描述这种差异。
> 2. 发明一个**数字**来捕捉这种差异。你的数字应当在球员得分更分散时**更大**，在更稳定时**更小**。你可以使用任何你喜欢的数学运算。
> 3. 在两名球员上测试你的数字。它能正确显示球员 B 比球员 A 更“分散”吗？
> 4. 如果还有时间：你的数字对**任意**两组数据都适用，还是只适用于这两组？

**预期学生反应：**

学生会生成多种方法，大多数都是部分正确的：

- **极差法（最常见）：** 球员 A 极差 = 2 - 1 = 1。球员 B 极差 = 6 - 0 = 6。这有效但很脆弱——它只用了两个数据点而忽略了中间的所有数据。约 60–70% 的小组会先尝试这种方法。

- **“离均差”法（较罕见但很有前景）：** 部分学生会计算每个分数距离平均数（1.5）有多远，并尝试合并这些距离。他们很可能会把距离相加，得到不同的总和。这已经很接近标准差的概念基础。约 20–30% 的小组。

- **“数零的个数”或“数极端值”法：** 部分学生会尝试非数学化的方法——数一名球员进了多少次 0 球，或有多少场“大爆发”。这抓住了直觉，但无法推广。约 10–20%。

- **卡住/困惑：** 部分小组会难以从文字描述（“球员 B 更不稳定”）过渡到数值度量。这是正常的。教师**不应**帮忙——挣扎正是意义所在。

**学生“不会”生成的内容：**
- 将偏差平方（标准差中的关键创新）。学生很可能会将原始离均差直接相加或求平均，这能得出一个有用的数，但在数学上有局限（如果不取绝对值或平方，正负偏差会相互抵消）。

**生成阶段教师的角色：**

- **巡视并观察。** 不要教。不要给提示。不要纠正。你的工作是收集学生的方法，供第二阶段使用。
- **记录每个小组使用了哪种方法。** 巩固阶段你需要 3–4 种形成对比的方法。
- **如果 10 分钟后学生仍卡住：** 你可以提供**一条**提示：“如果你们先找出每个分数距离平均数有多远，会怎样？”这能重新定向而不直接给出答案。
- **如果学生感到沮丧：** 承认难度。“这确实很难。数学家们为此争论了好几个世纪。我不指望你们得出‘标准’答案——我想看到你们的**思考**。”
- **严格把控时间。** 生成阶段持续 20–25 分钟。即使学生没做完也停下来。未完成的生成完全没问题——巩固阶段会基于他们产出的任何内容展开。

### 第二阶段：巩固

**时长：** 30–35 分钟

**第 1 步：分享与对比（10 分钟）。** 挑选 3 种学生方法（理想情况：极差法、离均差法以及另一种）。把每种写在黑板上。针对每种方法，向全班提问：“这个数字能正确显示球员 B 更分散吗？这种方法的优点和弱点是什么？”引导讨论指向关键局限：

- 极差：简单，但只用了两个数据点。一个异常值就能彻底扭曲它。
- 离均差之和：更好了，但如果数据点更多怎么办？数据越多，总和就会越大。你需要对距离**求平均**。
- 平均离均差：很好！但有个问题：有些距离是正的，有些是负的，它们会相互抵消。（现场演示：对于球员 A，相对于 1.5 的偏差是 +0.5, -0.5, +0.5, -0.5……加起来等于零。）

**第 2 步：引入标准解法（10 分钟）。** “数学家们是这样解决正负抵消问题的：他们把每个偏差**平方**（让所有数变成正数），对平方求平均，然后再开平方根回到原始单位。这就叫做标准差。”用球员 A 和球员 B 的数据走一遍公式，并将每一步显性关联到学生生成的方法上：“看到这一步了吗？这正是第 2 组做的事——求到平均数的距离。唯一的新步骤就是平方。”

**第 3 步：联系回最初的问题（10 分钟）。** 计算两名球员的标准差。球员 A：SD ≈ 0.5。球员 B：SD ≈ 2.3。“球员 B 的标准差大约是球员 A 的 4.5 倍。这对足球教练**意味着**什么？”追问解读：标准差不只是一个数字——它告诉你一名球员有多**稳定可预测**。“如果你需要每周稳定得分的射手，选球员 A；如果你急需一个能爆冷赢下比赛的奇兵且能承受几场颗粒无收，球员 B 值得冒险。”

**第 4 步：聚焦理解的快速练习（5 分钟）。** 再给出一组数据。要求学生（a）计算标准差，**并且**（b）结合语境解释它的含义。解释才是评估目标，而非计算。

### 嵌入的合意困难

| 困难 | 作用机制 | 学习收益 |
|---|---|---|
| **生成**（在讲授前尝试） | 迫使学生激活先验知识并直面度量离散度的问题 | 制造“知识缺口”，使随后引入公式时每一步都有意义——学生理解**为什么**需要每一步 |
| **富有成效的失败**（学生未得出标准答案） | 制造认知冲突——学生看到自己方法的局限 | 学习标准解法的动机更强，因为他们亲身体验了它所要解决的问题 |
| **穿插表征**（同一任务内文字 → 数值 → 解读） | 学生必须在同一概念的不同表征之间切换 | 建构灵活理解，而非死板的程序性知识 |
| **延迟讲授**（先挣扎后讲解，而非先讲后练） | 防止学生不加理解地机械套用步骤 | 公式是作为学生亲历问题的**解决方案**被引入，而非武断的菜谱 |

### 失败保障措施

**条件 1：任务必须有挑战性但并非不可能。** 足球教练难题经过了精确校准：十年级学生会算平均数和极差，也能用文字描述离散度。他们有足够的先验知识生成部分解法。如果学生连平均数都不会算，这任务就太难了——他们会经历**无益的**失败。

**条件 2：课堂文化必须支持挣扎。** 在生成阶段前明确说明：“我即将给你们一道不指望你们完美解决的问题。挣扎本身就是重点。我想看到你们的思考，而不是标准答案。”这能让失败常态化并降低焦虑。

**条件 3：沮丧监控。** 如果 10 分钟后超过半数学生显得卡住且沮丧，给出那一条脚手架提示（“如果先找出每个分数距离平均数有多远，会怎样？”）。这能防止失败变成无益的挫败。如果 15 分钟时依然普遍沮丧，提前进入第二阶段——你手里已经有足够的学生方案可用了。

**条件 4：巩固必须充分。** 如果时间紧张，砍掉练习题（第 4 步），**绝不**砍掉巩固（第 1–3 步）。没有巩固的富有成效的失败序列只是一堂令人困惑的课。

### 认知卸载风险

**风险 1：学生直接搜索“如何度量离散程度”。** 如果学生能上网，他们 30 秒就能搜到“标准差”，从而绕过整个生成阶段。**缓解措施：** 这是一项禁用联网设备的任务。允许计算器，禁止手机和笔记本电脑。解释原因：“我需要你们自己想出来——这才是整件事的意义。”

**风险 2：学生向 AI 聊天机器人求助。** 在可以使用 AI 工具的学校，学生可能会问“怎么衡量数据有多分散？”，然后得到关于标准差的清晰解释。**缓解措施：** 明确规定第一阶段禁用 AI 工具。用积极方式框定：“你们正在做一件 AI 做不到的事——发明自己的数学方法。AI 已经知道公式了。你们现在不需要公式——你们需要的是**思考**。”

**风险 3：高水平学生跳过挣扎。** 有些学生可能已经知道标准差，或在课本上翻到答案。**缓解措施：** 任务要求学生**发明**一个指标，而不是**找**一个指标。如果学生说“这不就是标准差吗？”，回应：“也许吧。但你能解释**为什么**标准差有效吗？为什么把偏差平方而不是取绝对值？这才是我想让你想明白的。”

### 教师准备说明

**做好感到不适的心理准备。** 看着学生挣扎却不伸手帮忙，是教师最难做到的事之一。你会强烈冲动想去解释、给提示、去“拯救”他们。忍住。挣扎本身就是产品，而不是需要解决的问题。Kapur 的研究表明，在生成阶段挣扎得最厉害的学生，往往在巩固阶段学得最多。

**预料到学生会抱怨。** 学生可能会说“为什么不直接教我们公式？”或“这太让人困惑了”。这很**正常**，并不意味着课堂失败了。Soderstrom & Bjork（2015）表明，学生对学习的主观体验并不能准确预测实际学习效果——他们觉得听清晰讲解学得更多，但实际上从富有成效的失败中记得更牢、迁移得更好。

**提前准备好巩固环节。** 清楚自己要寻找哪些学生方案（极差、离均差等）。准备好标准差计算演示，以便与学生方案并列对比。巩固环节无法即兴发挥——它需要精心规划。

**准备备用方案。** 如果生成阶段全班只产出了同一种方法（大家都用了极差），调整巩固话术：“你们大多数人都试了极差。很好的起点。让我给你们展示另一个班上一对搭档尝试的另一种方法……”然后由你自己引出离均差法。

---

## 已知局限

1. **富有成效的失败并非适用于所有内容。** 它最适合**概念性**理解——理解“为什么”有效，而不仅仅是“怎么”做。对于纯程序性技能（长除法、配平方程式），先直接讲授再练习往往更高效。当现有教法只产出程序流畅性却缺乏概念理解时，富有成效的失败最有价值。

2. **数学与科学领域的实证比其他领域更充分。** Kapur（2008, 2016）的研究主要在数学课堂开展。先生成后讲授的原则在其他领域也有研究，但具体的富有成效的失败设计（尝试 → 失败 → 巩固）在 STEM 之外的实证较少。底层机制（生成促进学习）是跨领域的，但具体任务设计可能需要调适。

3. **教师技能是硬约束。** 巩固阶段需要一位能实时将学生生成方案与标准解法关联起来的熟练教师。这比按准备好的讲稿讲课难得多。首次尝试富有成效的失败的教师，应从自己掌握最深厚的主题开始。

4. **表现与学习的区分带来了评估难题。** 处于富有成效的失败条件下的学生在即时后测中表现**更差**，但在延迟和迁移测试中表现**更好**（Soderstrom & Bjork, 2015）。如果教师在课后立刻评估学习效果，富有成效的失败看起来会像是失败了。真正的收益只有在几天或几周后才会显现。
