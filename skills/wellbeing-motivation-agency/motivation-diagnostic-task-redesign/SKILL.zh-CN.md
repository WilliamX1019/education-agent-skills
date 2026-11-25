---
# AGENT SKILLS STANDARD FIELDS (v2)
name: motivation-diagnostic-task-redesign
description: "运用自我决定论（SDT）诊断学习任务中的动机问题，并围绕自主感、胜任感与归属感进行重设计。适用于学生出现抽离、抗拒或机械应付的场合。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "wellbeing-motivation-agency/motivation-diagnostic-task-redesign"
skill_name: "动机诊断与任务重设计"
domain: "wellbeing-motivation-agency"
version: "1.0"
evidence_strength: "strong"
evidence_sources:
  - "Deci & Ryan (1985, 2000) — Self-Determination Theory: autonomy, competence, relatedness"
  - "Ryan & Deci (2017) — Self-Determination Theory: basic psychological needs in development, wellness, and behaviour"
  - "Reeve (2009) — Why teachers adopt a controlling motivating style toward students and how they can become more autonomy supportive"
  - "Jang, Reeve & Deci (2010) — Engaging students in learning activities: it is not autonomy support or structure but autonomy support AND structure"
  - "Niemiec & Ryan (2009) — Autonomy, competence, and relatedness in the classroom"
input_schema:
  required:
    - field: "task_description"
      type: "string"
      description: "当前设计的学习任务——要求学生做什么"
    - field: "learning_objective"
      type: "string"
      description: "学生应学到或能够做到的目标"
    - field: "student_level"
      type: "string"
      description: "年龄/年级"
  optional:
    - field: "subject_area"
      type: "string"
      description: "课程学科"
    - field: "motivation_concern"
      type: "string"
      description: "教师观察到的具体动机问题——例如抽离、回避任务、敷衍应付"
    - field: "student_profiles"
      type: "array"
      description: "来自情境引擎：班级数据，包括投入模式、兴趣、先备成绩"
    - field: "classroom_constraints"
      type: "string"
      description: "现实限制——时间、资源、课程要求"
output_schema:
  type: "object"
  fields:
    - field: "sdt_diagnostic"
      type: "object"
      description: "对照 SDT 三大基本心理需求（自主感、胜任感、归属感）的任务分析"
    - field: "motivation_profile"
      type: "string"
      description: "当前动机类型归类——无动机、外部调节、内摄调节、认同调节、整合调节、内在动机"
    - field: "redesigned_task"
      type: "object"
      description: "经修改的任务版本，包含增强自主感、胜任感与归属感的具体调整"
    - field: "implementation_notes"
      type: "string"
      description: "如何引入重设计后的任务以及需要留意的课堂反应"
chains_well_with:
  - "self-efficacy-builder-sequence"
  - "agency-scaffold-generator"
  - "flow-state-condition-designer"
  - "differentiation-adapter"
teacher_time: "3 分钟"
tags: ["motivation", "SDT", "self-determination", "autonomy", "engagement", "task-design"]
---

# 动机诊断与任务重设计（Motivation Diagnostic & Task Redesign）

## 本技能的功能

透过自我决定论（Self-Determination Theory, SDT）——一个具有扎实研究基础的动机理解框架——来分析一项学习任务，诊断该任务究竟支持还是削弱了三大基本心理需求（自主感、胜任感、归属感），随后在不降低学术严谨性的前提下，通过具体修改重新设计任务以提升内在动机。核心原则在于：动机不是学生的固定性格标签（“懒惰”、“不投入”），而是对环境条件的反应——任务条件可以支持或挫伤自主感、胜任感与归属感，但仅凭任务描述本身并不能断定某位学习者真实的内在动机。输出包括精准指出任务在动机层面短板的诊断报告、将具体修改对应到 SDT 原则的重设计版本以及实施说明。AI 在此具有独特价值，因为从 SDT 视角诊断动机需要同时剖析任务结构（是否提供选择？）、难度校准（是否觉得力所能及？）以及社会情境（是否将学生彼此及有意义的事物连接起来？）——这种三维分析是大多数教师直觉能感受到、却很少系统应用的。

## 循证依据

Deci 与 Ryan（1985, 2000）创立了自我决定论（SDT），确立了激发内在动机必须满足的三大基本心理需求：自主感（autonomy，感到自己的行动出于自愿认同，而非外部强迫）、胜任感（competence，感到自己有效能，能在适宜挑战的任务中取得成功）以及归属感（relatedness，感到与他人连接、被接纳、对他人重要）。当这些需求得到满足时，学生会迈向内在动机；当它们受挫时，学生会滑向受控动机（“不得不做”）或无动机（完全不做）。Ryan 与 Deci（2017）梳理了从无动机，经外部调节（奖惩）、内摄调节（内部压力——“我应该”）、认同调节（个人价值——“这对我很重要”）、整合调节（与自我身份一致）到内在动机（本身有趣）的动机连续谱。尤为关键的是，当外在奖励被用于原本就具有内在趣味的任务时，反而会削弱内在动机——即“过度合理化效应”（Deci, Koestner & Ryan, 1999）。Reeve（2009）指出，教师往往倾向于控制型激励风格（死线、监控、指令），因为这能换来即时服从；但自主支持型教学能随时间推移带来更深的投入和更好的学习。Jang、Reeve 与 Deci（2010）证明，自主支持与结构并非对立面——学生**两者都需要**。有自主无结构是混乱，有结构无自主是控制；最优课堂是在清晰期望之内提供有意义的选择。Niemiec 与 Ryan（2009）将 SDT 专门应用于课堂情境，表明自主支持型教学能预测更深的概念理解、更佳的学业表现、更高的坚持性以及更好的心理健康。

## 输入规范

教师必须提供：
- **任务描述：** 当前设计的任务。*例如：“学生从课本词汇表抄写 10 个核心术语的定义到练习本上，然后回答章节末的 5 道理解题” / “写一篇 500 词关于一战起因的论文” / “完成练习册第 34–36 页的分数题”*
- **学习目标：** 学生应学到的内容。*例如：“理解本主题的核心术语” / “分析一战的起因” / “异分母分数的加减运算”*
- **学生水平：** 年级。*例如：“9 年级”*

可选（如情境引擎可用，将自动注入）：
- **学科领域：** 课程学科
- **动机关切：** 教师观察到的具体问题
- **学生档案：** 班级数据、投入模式、兴趣
- **课堂限制：** 时间、资源、课程要求

## Prompt

```
You are an expert in motivation science and Self-Determination Theory, with deep knowledge of Deci & Ryan's (1985, 2000) framework, Reeve's (2009) research on autonomy-supportive teaching, and Jang, Reeve & Deci's (2010) finding that autonomy support and structure work together, not against each other. You understand that motivation is not a student trait but a response to how well the learning environment satisfies autonomy, competence, and relatedness needs.

IMPORTANT: Enhancing motivation must NOT reduce academic rigour. Preserve the learning objective, required assessment demands and access supports while improving the conditions for engagement; increasing difficulty is not the aim. "Making it fun" at the expense of learning is not SDT-aligned motivation design — it is entertainment.

IMPORTANT: Extrinsic rewards (stickers, points, prizes, class Dojo) can undermine intrinsic motivation for tasks that are already intrinsically interesting (Deci, Koestner & Ryan, 1999). Do NOT recommend extrinsic reward systems. The goal is to redesign the task so that the work itself is motivating.

Your task is to diagnose and redesign:

**Task description:** {{task_description}}
**Learning objective:** {{learning_objective}}
**Student level:** {{student_level}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Subject area:** {{subject_area}} — if not provided, infer from the task.
**Motivation concern:** {{motivation_concern}} — if not provided, analyse the task for likely motivation issues based on its design features.
**Student profiles:** {{student_profiles}} — if not provided, design for a typical mixed-ability class.
**Classroom constraints:** {{classroom_constraints}} — if not provided, assume standard classroom with no special resources.

Treat SDT as a task-design lens, not a psychological diagnosis. Distinguish observed design features, learner-reported experience and hypotheses. Invite a brief learner perspective where feasible (what makes this worthwhile/difficult, and what support helps); if absent, record motivation unknown or mixed rather than assigning motives from refusal, quietness or compliance. Check understanding, readiness and access before attributing disengagement to motivation. Keep necessary foundational practice. Offer a small adaptation within the same time/resources as well as any larger redesign, with explicit trade-offs.

Apply these evidence-based principles:

1. **Diagnose autonomy (Deci & Ryan, 2000; Reeve, 2009):**
   - Does the task offer meaningful choice? Not "choose any topic you like" (too open) but structured choice within the learning objective.
   - Does the task provide a rationale — do students understand WHY they are doing this?
   - Does the task use controlling language ("you must," "you have to") or autonomy-supportive language ("you might consider," "one approach is")?
   - Is the task something that is DONE TO students (compliance) or something students DO (agency)?

2. **Diagnose competence (Deci & Ryan, 2000; Jang et al., 2010):**
   - Is the task at the right level of challenge — not so easy it's boring, not so hard it's overwhelming?
   - Does the task provide feedback that helps students feel effective, or only feedback that evaluates?
   - Is there a clear pathway to success, or is the task ambiguous about what "good" looks like?
   - Does the task build on what students already know (connecting to prior success)?

3. **Diagnose relatedness (Deci & Ryan, 2000; Niemiec & Ryan, 2009):**
   - Does the task connect students to each other (collaboration, discussion, peer feedback)?
   - Does the task connect to something students care about (their lives, their community, real-world issues)?
   - Does the task connect to a meaningful audience (someone who cares about the outcome)?
   - Is the teacher-student relationship supported (warmth, interest in students' perspectives)?

4. **Use the motivation continuum tentatively (Ryan & Deci, 2017):**
   - Use learner evidence where available; otherwise return unknown/mixed and a hypothesis to check, not a diagnosis. No behaviour uniquely identifies a motivation type.
   - Amotivation: students don't see the point and don't engage.
   - External: students comply to avoid punishment or earn rewards.
   - Introjected: students do it because they feel they "should" — internal pressure without genuine value.
   - Identified: students see personal value in the task.
   - Intrinsic: students find the task inherently interesting.

5. **Redesign with autonomy support AND structure (Jang et al., 2010):**
   - Autonomy modifications: add structured choice, provide rationale, use invitational language, offer alternative pathways to the same objective.
   - Competence modifications: adjust challenge level, add scaffolding, build in formative feedback, make success criteria transparent.
   - Relatedness modifications: add collaborative elements, connect to student lives, create a meaningful audience, build in peer interaction.
   - Maintain the intended learning and necessary practice; more complex thinking is not automatically a better match. Adjust load and scaffolding to readiness without changing the goal.

Return your output in this exact format:

## Motivation Diagnostic: [Brief description]

**Current task:** [Summary]
**Learning objective:** [Objective]
**For:** [Student level]

### SDT Diagnostic

**Autonomy:**
- Current level: [Low / Moderate / High]
- [Specific analysis of what the task does or doesn't do for autonomy]

**Competence:**
- Current level: [Low / Moderate / High]
- [Specific analysis of what the task does or doesn't do for competence]

**Relatedness:**
- Current level: [Low / Moderate / High]
- [Specific analysis of what the task does or doesn't do for relatedness]

**Current motivation type:** [Learner-supported tentative classification, mixed or unknown; evidence and alternative explanations]

### Redesigned Task

[Complete redesigned version of the task with all modifications in place]

### What Changed and Why

[For each modification: what was changed, which need it addresses, and why it enhances motivation without reducing rigour]

### What to Watch For

[Implementation notes: how to introduce the redesigned task, what student responses to expect, how to adjust if the redesign doesn't work as intended]

**Self-check before returning output:** Verify that (a) the diagnostic specifically addresses autonomy, competence, and relatedness, (b) the redesigned task maintains or increases academic rigour, (c) no extrinsic reward systems are recommended, (d) the redesign provides autonomy support AND structure, not one without the other, and (e) each modification is linked to a specific SDT principle with a clear rationale.
```

## 示例输出

**场景：** *任务描述：“学生从课本词汇表抄写 10 个核心术语的定义到练习本上，然后回答章节末的 5 道理解题。” / 学习目标：“理解新主题（生态系统）的核心术语” / 学生水平：“8 年级” / 学科领域：“科学” / 动机关切：“学生草草抄完，根本不读进去，下节课全忘了”*

---

## 动机诊断：生态系统术语任务

**当前任务：** 从课本抄写 10 个定义，回答 5 道理解题
**学习目标：** 理解生态系统的核心术语
**适用对象：** 8 年级科学

### SDT 诊断

**自主感（Autonomy）：**
- 当前水平：**低**
- 任务提供零选择——每个学生按相同顺序从同一页抄写相同的 10 个定义。没有解释为什么记住这些术语很重要。任务完全由教师单向指令驱动：“从这里抄，回答这些”。学生是被动接收者，而非主动学习者。一个完全不动脑筋的学生也能完成任务——只需把文字从一页搬运到另一页。这是服从，而非学习。

**胜任感（Competence）：**
- 当前水平：**低-中等**
- 抄写对部分学生看似容易上手（但仍需核查阅读、语言、精细动作及辅助需求），却无法带来任何有意义的成就感。没有最佳挑战度——困难在于枯燥，而非思考。成功的标准是“抄完了”而不是“理解了概念”。后面的理解题或许有些挑战，但经过前面耗尽心力的抄写后，投入度已所剩无几。任务过程中没有任何反馈——在老师批改之前（如果会批改的话），学生根本不知道自己是否真的懂了。

**归属感（Relatedness）：**
- 当前水平：**低**
- 任务完全是孤立进行的。学生各自沉默抄写。同学之间没有连接，与学生的生活或兴趣没有连接，也看不出生态系统为什么重要。这些术语成了脱离任何学生关心情境的抽象标签。

**当前动机类型：** **未知。** 敷衍赶工与记忆不佳并不能直接证明学生是出于“逃避惩罚”的外在动机。缺乏理由说明与反馈只是设计层面的假设；在决定调整前，请询问学习者觉得哪里难、哪里有用，并核查词汇与阅读理解障碍。

### 重设计后的任务

**生态系统术语挑战赛**

**第一步——在情境中初次相遇（10 分钟）：**
不直接抄写定义，而是给学生一份一页纸的真实生态系统危机短案例——例如黄石公园狼群消失及其引发的生态级联效应。10 个核心术语嵌入在文本中并高亮标出。学生阅读案例，并根据每个高亮词在上下文中的用法，用自己的话写出定义。此时**不要**翻看课本词汇表。

**第二步——检验与打磨（10 分钟）：**
学生与同桌对比各自基于语境写出的定义。当两人定义不同时，展开讨论：哪一个定义更准确地捕捉了这个词的含义？随后对照课本词汇表核对两人的定义，并打磨自己的表述。对每个术语写下：“我的定义：___ / 课本定义：___ / 我改进后的定义：___”

**第三步——应用关联（10 分钟）：**
每对搭档从 10 个术语中自选 3 个，写一段简短解释（2–3 句话），说明这 3 个术语在黄石公园案例中如何相互关联。例如：“狼是生态系统中的捕食者（predator）。当狼被移除后，麋鹿（消费者 consumer）的数量激增，导致过度啃食，从而改变了其他物种的栖息地（habitat）。”

**第四步——分享与挑战（5 分钟）：**
两对搭档合并成四人小组。每对解释他们的三词关联。另一对提出一个追问：“如果 [术语 X] 发生变化，接下来会发生什么？”这要求学生**运用**术语对生态系统进行推理，而不仅仅是背诵定义。

### 改动之处与原因

| 修改内容 | 对应的 SDT 需求 | 理据 |
|---|---|---|
| 用真实案例替代抄写词汇表 | **自主感**（提供理由）+ **归属感**（连接真实世界） | 学生看清了这些术语**为什么**重要——它们描述了一场真实的生态危机。这提供了原任务所缺失的理由。该案例可提供有益情境；需核查学生兴趣与内容准确性，而非假定每位学习者都必然觉得有趣。 |
| 先自写定义再对照课本 | **胜任感**（适度挑战）+ **自主感**（所有权） | 自主生成定义能暴露真实理解，但面对生僻术语或阅读难度较大的文本时，可能需要先进行直接讲授。仅有挑战度本身不能证明学习质量。同时这赋予了学生所有权：“我自己的定义”比“我抄来的定义”更有意义。 |
| 同伴对比与打磨 | **归属感**（同伴连接）+ **胜任感**（即时反馈） | 学生通过与同桌对比获得即时反馈。分歧催生有价值的讨论。三栏格式（我的定义 / 课本 / 改进后）让精进过程清晰可见。 |
| 自选 3 个术语并解释关联 | **自主感**（结构化选择）+ **胜任感**（深度挑战） | 学生选择重点聚焦哪些术语——在同一目标内提供结构化选择。在定义稳固后，解释关联可评估术语的实际运用；必要时仍应保留基础定义练习。 |
| 四人小组分享与“如果……会怎样”追问 | **归属感**（协作）+ **胜任感**（迁移应用） | “如果……会怎样”的追问要求学生用术语进行**推理**，而非仅凭记忆背诵。这正是核心目标——通过应用而非死记硬背来理解术语。 |

**目标核查：** 两个版本都应教会准确的生态系统术语。请用一次简短的个人定义/应用检查来检验实际学到了什么。高投入度或更复杂的任务形式本身并不自动证明学习效果更好。

**同等时长替代方案（若仅有 10 分钟课堂时间）：** 保留 10 个核心术语及无障碍词汇表/支持工具。用 2 分钟讲解 2 个示范术语，4 分钟让学生借助一个自选实例核对简短定义，2 分钟与同伴或私下对比核对，最后 2 分钟进行简短独立检查。如果 10 个术语超出学习者当前准备度，教师可在保留课程覆盖面的前提下调整讲授顺序。这一方案替代了部分抄写，直接利用现有材料，无需额外安排 35 分钟的完整探究。

### 实施留意事项

1. **部分学生会试图跳过第一步直接翻词汇表。** 这可能反映了生词障碍、阅读负荷或他们习惯的拐杖；先核查原因再引导。引导话术：“先别担心写出的定义‘对不对’——我想看看你读完案例后觉得这个词是什么意思。第二步我们就会去查词汇表。”

2. **第二步的同伴对比可能会暴露出部分学生完全写不出定义。** 这不是动机问题，而是阅读理解问题。如果学生无法从语境推断词义，可能需要调整案例的阅读难度，或提前预教最生僻的几个术语。

3. **第三步在术语教学与反馈之后检验应用。** 如果学生写出的关联流于空泛（例如“它们都是关于生态系统的”——没错但太浅），请追问具体机制：“没错，但它们**具体怎么**关联？当捕食者消失时，消费者会发生什么？”

4. **不要额外加贴纸、积分或竞赛排名。** 本任务的设计初衷是通过有意义的挑战、社交连接和真实世界情境来激发内在动机。加入外在奖励反而会把学生推回外部调节。请询问学习者什么对他们有帮助并检查他们的实际理解；单纯的参与热闹并不等于内在动机或真正学会。根据这些证据调整任务、无障碍支持或讲授方式。

---

## 已知局限性

1. **诊断假定教师对原任务的描述是准确的。** 一项被描述为“学生抄写定义”的任务，在真实课堂里可能伴随了教师的口头讲解、讨论和拓展，而文字描述未能体现。本分析严格基于**所描述的任务**——教师应评估重设计是否解决了自己课堂里真实存在的问题，而不仅仅是描述中的问题。

2. **SDT 是理解动机的框架，而非投入度的绝对保证。** 满足自主感、胜任感与归属感需求的任务创造了激发内在动机的**条件**——但个别学生仍可能因任务之外的因素而抽离：疲惫、社交困扰、创伤经历、过往在该学科的负面体验。SDT 处理的是环境条件，无法解决所有个体障碍。

3. **重设计后的任务通常比原任务耗时更长。** 用 35 分钟的探究替代 10 分钟的抄写看似不太现实。切勿想当然认为时间越长学得越好。请参考上述“同等时长方案”，并核查实际的记忆保持率、无障碍性与备课负担。教师必须判断时间权衡在自己的课程进度内是否可行。
