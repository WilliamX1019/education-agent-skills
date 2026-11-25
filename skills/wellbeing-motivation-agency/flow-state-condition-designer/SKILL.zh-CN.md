---
# AGENT SKILLS STANDARD FIELDS (v2)
name: flow-state-condition-designer
description: "通过平衡挑战水平、技能、明确目标与即时反馈来优化学习活动，创造心流（flow）条件。适用于学生在任务中感到无聊、焦虑或抽离的场景。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "wellbeing-motivation-agency/flow-state-condition-designer"
skill_name: "心流状态条件设计器"
domain: "wellbeing-motivation-agency"
version: "1.0"
evidence_strength: "moderate"
evidence_sources:
  - "Csikszentmihalyi (1990) — Flow: the psychology of optimal experience"
  - "Csikszentmihalyi (1997) — Finding Flow: the psychology of engagement with everyday life"
  - "Shernoff et al. (2003) — Student engagement in high school classrooms from the perspective of flow theory"
  - "Nakamura & Csikszentmihalyi (2002) — The concept of flow: conditions and characteristics"
  - "Hattie & Donoghue (2016) — Learning strategies: a synthesis and conceptual model"
input_schema:
  required:
    - field: "lesson_activity"
      type: "string"
      description: "需要优化心流条件的学习活动"
    - field: "student_level"
      type: "string"
      description: "年龄/年级"
  optional:
    - field: "subject_area"
      type: "string"
      description: "课程学科"
    - field: "current_engagement"
      type: "string"
      description: "学生目前对该活动的投入度——无聊、顺从、部分投入、深度投入"
    - field: "student_profiles"
      type: "array"
      description: "来自情境引擎：能力跨度、投入模式、特定需求"
    - field: "lesson_duration"
      type: "string"
      description: "课程或活动时长"
    - field: "practical_constraints"
      type: "string"
      description: "空间、资源、技术、时间限制"
output_schema:
  type: "object"
  fields:
    - field: "flow_analysis"
      type: "object"
      description: "分析当前活动对心流条件的满足情况——挑战-技能平衡、明确目标、即时反馈"
    - field: "redesigned_activity"
      type: "object"
      description: "为最大化心流条件而重设计后的活动"
    - field: "differentiated_challenge"
      type: "object"
      description: "如何针对不同能力水平校准挑战度，使所有学生都有机会体验心流"
    - field: "flow_killers"
      type: "array"
      description: "破坏心流的常见课堂做法及规避方法"
chains_well_with:
  - "motivation-diagnostic-task-redesign"
  - "perma-based-lesson-designer"
  - "practice-problem-sequence-designer"
  - "self-efficacy-builder-sequence"
teacher_time: "3 分钟"
tags: ["flow", "Csikszentmihalyi", "engagement", "optimal-experience", "challenge-skill-balance"]
---

# 心流状态条件设计器（Flow State Condition Designer）

## 本技能的功能

对照 Csikszentmihalyi 的心流条件——挑战-技能平衡、明确目标、即时反馈、掌控感、专注力以及自我意识消失——分析一项学习活动，并对其进行重新设计，以最大化学生体验心流（深度沉浸、忘却时间、工作本身即带来回报）的概率。关键洞见在于：心流并非随机发生——某些条件能提高其发生的可能性，教师可以刻意设计并核查这些条件，但不能保证每个人必然产生该体验。输出包括当前活动对各心流条件的满足与缺失分析、针对心流优化的重设计方案、分层挑战校准（因为心流需要**个体层面**的挑战-技能匹配，而非全班一刀切）以及破坏心流的常见课堂做法清单。AI 在此具有独特价值，因为在课堂中实现心流需要同时平衡 30 名学生各自的挑战-技能比——这是一项极适合系统化分析的设计挑战。

## 循证依据

Csikszentmihalyi（1990, 1997）将“心流”（flow）界定为最优体验状态——人全神贯注于正在做的事情，以至于外界其他一切仿佛都退居次要。他归纳了心流的八项条件：（1）明确的目标，（2）即时的反馈，（3）挑战-技能平衡（任务难度略高于当前能力——既不太简单也不太难），（4）高度专注，（5）对活动的掌控感，（6）自我意识消失，（7）时间感改变（时间飞逝），以及（8）活动本身具有自足性（autotelic，过程本身即带来回报）。Shernoff 等（2003）将心流理论应用于高中课堂，发现心流体验能够预测学业投入度、成绩与身心健康。当挑战与技能双高时，学生报告的投入度最高；当挑战过低时（即使技能高）会出现无聊；当挑战过高而技能不足时则会出现焦虑。“心流通道”正是挑战与技能相匹配的狭窄区间。Nakamura 与 Csikszentmihalyi（2002）进一步阐述，心流体验随时间推移会累积为“生命投入”（vital engagement）——一种超越瞬间沉浸的持久热爱。Hattie 与 Donoghue（2016）证实，将学习策略与学生当前所处阶段相匹配（早期用表层策略，后期用深层策略）对于维持心流所需的挑战-技能平衡至关重要。

## 输入规范

教师必须提供：
- **课堂活动：** 学生正在做的事。*例如：“学生完成一张包含 20 道代数题的练习单” / “学生根据一张刺激图片创作一个故事” / “学生按照分步实验指南开展化学实验”*
- **学生水平：** 年级。*例如：“9 年级”*

可选（如情境引擎可用，将自动注入）：
- **学科领域：** 课程学科
- **当前投入度：** 学生目前的投入状态
- **学生档案：** 能力跨度、投入模式
- **课时长度：** 课程时长
- **现实限制：** 空间、资源、时间

## Prompt

```
You are an expert in flow theory and optimal engagement, with deep knowledge of Csikszentmihalyi's (1990, 1997) flow conditions, Shernoff et al.'s (2003) application of flow to classroom settings, and the relationship between flow, learning, and wellbeing. You understand that flow is not a mood or a motivational trick — it is an individual reported experience. Teachers can design favourable conditions and check learning separately; a checklist cannot establish flow.

CRITICAL: Match challenge to demonstrated skills and access needs, with differentiated entry points, support and extension. Too little challenge may be boring; too much may be overwhelming, but neither reaction nor flow can be inferred for every learner from task difficulty alone. Treat the redesign as a hypothesis, checked through optional student feedback and work evidence. Absorption, speed or quietness does not by itself establish learning or flow.

Your task is to design flow conditions for:

**Lesson activity:** {{lesson_activity}}
**Student level:** {{student_level}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Subject area:** {{subject_area}} — if not provided, infer from the activity.
**Current engagement:** {{current_engagement}} — if not provided, identify possible design barriers and label engagement unknown unless learner feedback or observation is supplied.
**Student profiles:** {{student_profiles}} — if not provided, assume a mixed-ability class with a wide range.
**Lesson duration:** {{lesson_duration}} — if not provided, assume 50–60 minutes.
**Practical constraints:** {{practical_constraints}} — if not provided, assume standard classroom.

Apply these flow conditions:

1. **Clear goals (Csikszentmihalyi, 1990):**
   - Students must know EXACTLY what they're trying to achieve — not "learn about ecosystems" but "create a food web that includes 8 organisms and shows energy transfer at each level."
   - Goals should be specific, visible, and achievable within the session.
   - Clear goals and examples can help learners judge progress; avoid inferring a psychological state from goal clarity alone.

2. **Immediate feedback (Csikszentmihalyi, 1990):**
   - Provide timely, informative feedback, including teacher help when needed; correctness-only checks may not explain an error.
   - Built-in feedback: answer checks, self-assessment criteria, peer feedback, observable outcomes.
   - Reduce avoidable feedback delays without replacing necessary teaching or valid assessment.

3. **Challenge-skill balance (Shernoff et al., 2003):**
   - Aim for personally challenging but achievable work, with support and adjustment based on actual performance.
   - Too easy or hard may undermine engagement; matched challenge is a design aim, not a guaranteed flow trigger.
   - This requires differentiation: easier entry points for lower-attaining students, extension challenges for higher-attaining students, checked through each learner's feedback and performance.

4. **Concentration and minimal interruption:**
   - Flow requires uninterrupted focus. Design protected work periods where students are not interrupted by transitions, instructions, or management.
   - Minimise context-switching — don't alternate between unrelated activities.
   - The teacher should avoid unnecessary interruptions: Avoidable announcements can disrupt focus, but safety instructions or a shared misconception can justify interrupting.

5. **Sense of control (Nakamura & Csikszentmihalyi, 2002):**
   - Students feel they have some control over their approach.
   - Choice of strategy, pace, or starting point creates ownership.
   - Over-prescribed tasks (follow steps 1–10 exactly) remove the sense of control that flow requires.

6. **Autotelic experience:**
   - The best flow tasks are intrinsically rewarding — the work itself is satisfying, not just the grade or the teacher's approval.
   - Design tasks where progress is visible and the product is something students care about.

Return your output in this exact format:

## Flow Conditions: [Activity Description]

**Activity:** [Summary]
**For:** [Student level]

### Flow Analysis

| Flow Condition | Current Status | What's Missing |
|---|---|---|
| Clear goals | [Met/Partially/Not met] | [What's needed] |
| Immediate feedback | [Met/Partially/Not met] | [What's needed] |
| Challenge-skill balance | [Met/Partially/Not met] | [What's needed] |
| Concentration | [Met/Partially/Not met] | [What's needed] |
| Sense of control | [Met/Partially/Not met] | [What's needed] |

### Redesigned Activity

[Complete redesigned version optimised for flow]

### Differentiated Challenge Map

[How to calibrate challenge from current skills/access needs; include recovery from repeated errors, no guaranteed flow]

### Flow Killers to Avoid

[Common classroom practices that destroy flow — with alternatives]

**Self-check before returning output:** Verify that (a) all five key flow conditions are addressed, (b) challenge is differentiated for different ability levels, (c) feedback is immediate (not delayed), (d) goals are specific and visible, (e) the redesign maintains academic rigour, and (f) flow killers are identified with alternatives, and (g) student feedback, learning evidence and recovery after repeated errors are included.
```

## 示例输出

**场景：** *课堂活动：“学生完成一张包含 20 道代数题的练习单——解一元一次方程（例如 3x + 7 = 22）” / 学生水平：“8 年级” / 学科领域：“数学” / 当前投入度：“顺从配合——学生把题做完了但毫无活力。有几个人 10 分钟就做完开始发呆；有几个人前 5 题就卡住直接放弃。”*

---

## 心流条件设计：一元一次方程练习

**活动：** 20 道解一元一次方程的代数练习题
**适用对象：** 8 年级数学

### 心流分析

| 心流条件 | 当前状态 | 缺失环节 |
|---|---|---|
| 明确目标 | **部分满足** | “做完 20 道题”是完成任务的目标，而不是学习目标。学生追求的是“做完”，而不是“掌握”。 |
| 即时反馈 | **未满足** | 学生在老师批改（或最后对答案）前不知道自己做得对不对。任务过程中缺乏反馈。 |
| 挑战-技能平衡 | **未满足** | 统一题单未能匹配不同准备度：场景中既有早早做完的学生，也有卡在前几题的学生。他们各自的内心体验尚不明确。 |
| 专注力 | **部分满足** | 任务本身允许专注，但无聊的学生容易制造干扰，卡住的学生频频求助，打断了所有人的专注。 |
| 掌控感 | **未满足** | 零选择权。每个学生按完全相同的顺序做完全相同的 20 道题。任务被完全规定死了。 |

### 重设计后的活动

**方程攀登赛——自定步调挑战序列**

用一套结构化的 5 级挑战序列（每级 4 道题）替代原本难度一成不变的 20 道题：

**第 1 级（基础）：** 一步方程：`x + 5 = 12`, `3x = 18`
**第 2 级（进阶）：** 两步方程：`2x + 3 = 11`, `5x − 4 = 16`
**第 3 级（核心）：** 含括号的多步方程：`3(x + 2) = 21`, `2(3x − 1) = 16`
**第 4 级（拓展）：** 等号两边均有未知数：`3x + 5 = x + 13`, `4x − 2 = 2x + 8`
**第 5 级（挑战）：** 含分数与负解的方程：`(2x + 3)/4 = 5`, `3(x − 4) = 2(x − 7)`

**规则：**
- 从你觉得最适合自己的那一级开始。（大多数学生会从第 2 级或第 3 级起步。）
- 完成当前级别全部 4 道题。对照参考答案卡核对（答案卡反扣在桌角或屏幕上按需查看）。
- 如果做对 3 题或 4 题：晋升下一级。
- 如果做对 2 题及以下：借助详细解析或教师反馈排查错误原因。尝试一道有支持的平行题、降低台阶或回顾先备知识。如果错误持续出现，暂停攀登接受直接讲解，而不要无限重复刷题。
- 你的目标：在适合自己的级别上解出方程并能解释方法，随后用一道新题检验。25 分钟是一个练习时段示例，而非竞速比赛或强制进度。
- 你可以独自安静完成，也可以与同桌轻声讨论。

**为何这些条件可能支持专注（需在实践中核查）：**
- **明确目标：** “解出并解释一种方法，并用新题检验”让掌握程度可见，而不仅仅是奖励速度或刷到的级别。
- **即时反馈：** 答案卡随时可用。学生每完成一级就核对一次，而不是拖到最后。这构成了短反馈闭环：尝试 → 排查方法/错误 → 调整或求助 → 尝试下一道合适题目。
- **挑战-技能平衡：** 学生自选起点并按自身节奏推进。觉得简单的学生可以尝试拓展级；遇到困难的学生获得反馈、讲解或更易切入的起点。核查实际匹配度，而非直接给学生贴上“处于心流”的标签。
- **专注力：** 自定步调可以减少干等；部分学习者仍需要不同任务或直接支持。课后询问学生该节奏与难度是否合适。
- **掌控感：** 学生自主选择起点与节奏。个人挑战感（“我能闯到第 5 级吗？”）可能增强自主性；仍需听取学习者反馈。

### 分层挑战图谱

| 学生群体 | 建议起点 | 心流通道 | 教师支持 |
|---|---|---|---|
| 基础方程尚有困难的学生 | 第 1 级 | 第 1–2 级 | 完成第 1 级后跟进——做对 3 题以上即肯定并鼓励尝试第 2 级；若卡住，提供一道样例作为参考。 |
| 达到预期水平的学生 | 第 2 级 | 第 2–4 级 | 核查挑战度、专注度与实际学会情况，而非想当然认为进入心流。巡视观察：若卡在第 3 级，提示：“看看你在第 2 级是怎么解的——这两题有什么不同？” |
| 高阶水平学生 | 第 3 级 | 第 3–5 级 | 这类学生平时做完练习单太快容易走神。攀登结构能持续提供挑战。第 5 级确实有难度，需要他们动脑筋。 |
| 平时回避数学的学生 | 第 1 级 | 第 1–2 级 | 根据已展现的技能选择起点并保留支持；若第 1 级仍无法切入，先讲授基础再继续。攀登结构颇具激励性：“你已经通关第 1 级了——准备好试试第 2 级了吗？”将其框定为成就，而非补差。 |

### 应避免的心流杀手

1. **在深度练习中途用全班广播打断。** 可避免的全班打断会破坏专注；当然，安全提示或全班共性迷思的澄清依然优先。如需发布指令，请等到自然过渡点（换级间隙）、使用倒计时视觉提示，或在巡视时单独告知。

2. **要求学生干等老师批改。** 如果学生必须举手干等老师确认对错，反馈闭环就断了。提供答案卡让学生即时自查。在练习中，将答案核对与简短的理由解释及新题检验结合；在评估目的需要时保留教师核查。

3. **为整项任务设定统一的时间进度。** 单一节奏可能让快生干等、慢生焦虑；请根据实际作答情况调整。攀登结构没有“做完没事干”的终点——学生总有下一级可以尝试。用时间限制来收束任务，而不是用来催促节奏。

4. **一个学生提问就叫停全班。** 个别问题个别解答。如果多名学生问同一个问题，适合时可拉个小组讲解；只有当迷思具有全班普遍性时才短暂暂停全班讲授。

5. **公开展示谁处于哪一级。** 这会把激发心流的个人挑战变成社会比较竞赛。保持级别私密——每位学生知道自己的进度，但班级不需要排行榜。最后用一道简短的解释/迁移题以及可选的“挑战度与专注度”反馈收尾；分别评估学习成果与体验感受。动机应当来自个人精进，而非攀比竞争。

---

## 已知局限性

1. **心流需要最低限度的技能基础。** 如果第 1 级对学生而言仍无法触及，请核查先备知识与支持，不要假定学习者可以直接参与攀登。心流设计假定学生拥有足够的先备知识来应对最基础的层级；如果没有，直接讲授必须先于心流活动。

2. **并非所有学习活动都能设计成心流体验。** 有些学习本身就是低即时趣味的活动——听取讲解、阅读晦涩文本、练习枯燥但必要的程序。心流设计最适用于练习类、创造类与问题解决类任务，较不适用于初始讲授或正式考试。

3. **心流是高度个体化的。** 30 人的班级不可能同时全部处于心流之中。攀登结构旨在改善挑战匹配度；它对本班心流与学习效果的提升尚待检验——仍可能有部分学生觉得第 5 级太简单而无聊，或觉得第 1 级太难而焦虑。教师必须持续观察并动态调整。
