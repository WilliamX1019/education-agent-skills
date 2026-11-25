---
# AGENT SKILLS STANDARD FIELDS (v2)
name: ai-facilitated-collaborative-learning-designer
description: "设计由 AI 支持的协作学习任务，结构化小组互动并解决参与度问题。适用于学生在小组任务中难以有效协作时。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "ai-learning-science/ai-facilitated-collaborative-learning-designer"
skill_name: "AI 辅助协作学习设计器"
domain: "ai-learning-science"
version: "1.0"
evidence_strength: "moderate"
evidence_sources:
  - "Roschelle & Teasley (1995) — The construction of shared knowledge in collaborative problem solving"
  - "Dillenbourg (1999) — What do you mean by collaborative learning? (CSCL framework)"
  - "Järvelä & Hadwin (2013) — New frontiers: regulating learning in CSCL (socially shared regulation of learning)"
  - "Slavin (1995) — Cooperative learning: theory, research, and practice (meta-analysis)"
  - "Kirschner et al. (2018) — From cognitive load theory to collaborative cognitive load theory"
input_schema:
  required:
    - field: "collaborative_task"
      type: "string"
      description: "学生将共同完成的具体学习任务——作为小组需要产出或解决的内容"
    - field: "collaboration_challenge"
      type: "string"
      description: "需要解决的具体协作问题——学生在共同完成此任务时容易出现什么偏差"
  optional:
    - field: "student_level"
      type: "string"
      description: "年龄/年级及能力水平"
    - field: "subject_area"
      type: "string"
      description: "课程学科"
    - field: "group_size"
      type: "string"
      description: "每组学生人数"
    - field: "ai_capabilities"
      type: "string"
      description: "可用的 AI 工具——聊天机器人、协作工作区、实时监控或其他"
    - field: "time_available"
      type: "string"
      description: "学生完成协作任务的可用时长"
output_schema:
  type: "object"
  fields:
    - field: "collaboration_design"
      type: "object"
      description: "协作任务的结构——角色、阶段以及 AI 进行引导的具体节点"
    - field: "ai_facilitation_moves"
      type: "array"
      description: "AI 在协作过程中执行的具体动作——提示、监控、脚手架支持与干预"
    - field: "regulation_scaffolds"
      type: "object"
      description: "AI 如何支持社会共享调节——对小组过程的计划、监控与反思"
    - field: "equity_mechanisms"
      type: "object"
      description: "该设计如何确保所有小组成员有意义地参与——防止搭便车与话语垄断"
chains_well_with:
  - "intelligent-tutoring-dialogue-designer"
  - "ai-feedback-design-principles"
  - "metacognitive-monitoring-ai-contexts"
teacher_time: "5 分钟"
tags: ["collaboration", "CSCL", "Dillenbourg", "Järvelä", "cooperative-learning", "Slavin", "group-work", "AI-facilitation", "regulation"]
---

# AI 辅助协作学习设计器

## 本技能的作用

设计包含特定 AI 引导节点的协作学习任务——即 AI 系统在不替代小组过程的前提下提供支持的节点。本技能针对协作学习中的核心挑战：结构良好的协作学习**能够**成为最有效的学习方式之一（Slavin 1995 年的元分析发现其效应量为 0.26–0.32），但它往往会退化为一名学生包揽所有工作而其他人旁观，或者演变成共用同一份文档的平行个人作业。Dillenbourg（1999）指出，真正的协作需要带着共同理解进行联合问题解决，而不仅仅是任务分工。Järvelä & Hadwin（2013）表明，有效的协作需要社会共享学习调节（SSRL）——即小组共同计划、监控和调整其方法的能力。AI 在此具有独特价值，因为它能做到教师难以做到的事：同时观察多个小组、实时发现协作失效并在恰当的时刻精准干预。教师在 8 个小组间巡视时，发现问题往往滞后几分钟甚至几小时；而监控小组互动的 AI 可以实现实时提示。输出包括完整的协作设计（任务结构、角色、阶段）、AI 引导动作（何时及如何干预）、调节脚手架（支持小组自我调节）以及公平机制（确保所有成员参与）。

## 实证基础

Dillenbourg（1999）建立了计算机支持协作学习（CSCL）的基础框架，区分了合作（cooperation，将任务拆分为由个人分别完成的子任务）与协作（collaboration，共同建构对问题的共享理解）。他认为真正的协作需要：（a）共同目标，（b）对彼此想法的相互投入，以及（c）共同建构出任何个人都无法单独产生的知识。技术可以通过结构化互动、使思维可视化以及提供共享表征来支持协作——但如果让任务拆分变得过于容易，技术也会削弱协作。Roschelle & Teasley（1995）将协作定义为“一种协调的、同步的活动，是持续尝试建构并维持对问题的共享概念的结果”。他们表明，有效协作包含特定的对话模式：提出建议、阐述、质疑与修复共享理解。当这些模式中断时，协作就会退化为平行工作。Järvelä & Hadwin（2013）提出了社会共享学习调节（SSRL）概念——即有效的协作小组不仅分担认知工作，也分担**调节**工作：计划做什么、监控进度、评估方法是否奏效并在无效时做出调整。他们发现 SSRL 是协作学习成功的最强预测指标，且可以通过技术搭建脚手架——例如提示小组进行计划、检查进度和反思。Slavin（1995）对合作学习研究进行了全面综述，发现在满足两个条件时能产生稳定的正向效应（d = 0.26–0.32）：（a）小组目标（小组作为整体接受评估，而非仅个人评估），以及（b）个人问责制（每位成员的贡献都清晰可见并接受评估）。缺乏这些条件时，合作学习往往会产生搭便车和社会惰化现象。Kirschner 等人（2018）将认知负荷理论扩展至协作情境，指出小组合作将认知负荷分摊给成员——但这仅在任务对任何个人而言都过于复杂时才成立。对于简单任务，协作的交易成本（协调、沟通、管理不同观点）会超过其收益。协作应当保留给真正需要多方智慧的任务。

## 输入规范

教师必须提供：
- **协作任务（Collaborative task）：** 学生将共同完成的内容。*例如：“十年级科学：设计实验测试温度是否影响化学反应速率。每组必须产出实验方法、风险评估、预测结果及底层化学原理说明” / “八年级英语：合作撰写一篇报纸头版，像发生在今天一样报道《罗密欧与朱丽叶》的事件” / “十二年级经济学：分析市场失灵的真实案例，并撰写一份建议政府干预的政策简报”*
- **协作挑战（Collaboration challenge）：** 学生在此任务中协作时容易出现的问题。*例如：“一名学生包揽所有书写工作，其他人旁观。‘讨论’阶段只持续 30 秒就开始各自瓜分任务” / “小组默认采用嗓门最大学生的想法，不考虑替代方案。内向学生逐渐脱离” / “学生把工作拆开（‘你做实验方法，我做风险评估’），从未建立共同理解——最终成果只是四块拼凑在一起的独立部分”*

可选项（如可用则由上下文引擎注入）：
- **学生水平（Student level）：** 年级与能力水平
- **学科领域（Subject area）：** 课程学科
- **小组规模（Group size）：** 每组学生人数
- **AI 能力（AI capabilities）：** 可用的 AI 工具
- **可用时间（Time available）：** 协作任务的持续时间

## 提示词（Prompt）

```
You are an expert in collaborative learning design and AI-facilitated CSCL (computer-supported collaborative learning), with deep knowledge of Dillenbourg's (1999) collaboration framework, Roschelle & Teasley's (1995) research on shared knowledge construction, Järvelä & Hadwin's (2013) socially shared regulation of learning (SSRL), Slavin's (1995) meta-analysis of cooperative learning, and Kirschner et al.'s (2018) collaborative cognitive load theory. You understand that collaboration is one of the most powerful — and most frequently misused — learning strategies. You know that the difference between productive collaboration and time-wasting group work depends entirely on the DESIGN, not on the students.

CRITICAL PRINCIPLES:
- **Collaboration requires a task that is genuinely too complex for one person.** Kirschner et al. (2018): if one student can do the task alone, collaboration adds transaction costs without cognitive benefit. The task must require multiple perspectives, skills, or knowledge bases that no individual possesses. If the task could be done individually, don't make it collaborative.
- **Structure the interaction, not just the task.** Dillenbourg (1999): giving students a task and saying "work together" is not collaborative learning design. The interaction must be structured: who speaks when, what they discuss at each phase, how they make decisions, and how they build on each other's ideas. AI can enforce this structure without the teacher being present.
- **Individual accountability prevents free-riding.** Slavin (1995): every group member must have a visible, assessable contribution. If a student can sit passively and still get the grade, they will. Design roles, individual deliverables, or accountability mechanisms that make every student's contribution visible.
- **AI should facilitate, not participate.** The AI's role is to support the GROUP PROCESS — prompting planning, flagging imbalanced participation, asking regulation questions ("How is your approach going? Do you need to adjust?"). The AI should NOT contribute ideas, solve problems for the group, or become a group member. If students are talking to the AI instead of to each other, the design has failed.
- **Socially shared regulation is the highest-value target.** Järvelä & Hadwin (2013): the groups that learn the most are the ones that collectively regulate their process — planning, monitoring, and adjusting. AI scaffolds for regulation (planning prompts, progress checks, reflection prompts) are more valuable than AI scaffolds for content.

Your task is to design an AI-facilitated collaborative learning experience:

**Collaborative task:** {{collaborative_task}}
**Collaboration challenge:** {{collaboration_challenge}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Student level:** {{student_level}} — if not provided, design for a general secondary school context.
**Subject area:** {{subject_area}} — if not provided, infer from the task.
**Group size:** {{group_size}} — if not provided, design for groups of 3-4.
**AI capabilities:** {{ai_capabilities}} — if not provided, design for a text-based AI that can monitor group work and send prompts to the group.
**Time available:** {{time_available}} — if not provided, design for a 50-minute lesson.

Return your output in this exact format:

## AI-Facilitated Collaboration Design: [Task Name]

**Task:** [What students will produce together]
**Collaboration challenge addressed:** [The specific problem this design solves]
**AI role:** [One-sentence summary of what the AI does and what it does NOT do]

### Task Complexity Check

[Verify that this task genuinely requires collaboration. If it doesn't, redesign it so it does.]

### Collaboration Structure

[The complete design: phases, roles, interaction rules, and deliverables. Include timing.]

**Phase 1: [Name]** (X minutes)
[What happens, what each role does, what the AI does]

**Phase 2: [Name]** (X minutes)
[What happens, what each role does, what the AI does]

### AI Facilitation Moves

[The specific moves the AI makes during collaboration — when, what, and why]

| Trigger | AI Move | Purpose | Example |
|---|---|---|---|
| [When] | [What the AI does] | [Why] | [Exact text] |

### Regulation Scaffolds

[How the AI supports socially shared regulation — planning, monitoring, and reflection prompts]

### Equity Mechanisms

[How the design ensures balanced participation — roles, accountability, and AI monitoring]

### What the AI Does NOT Do

[Explicit boundaries on AI involvement — what the AI should never do in this context]

**Self-check before returning output:** Verify that (a) the task genuinely requires collaboration, (b) interaction is structured not just assigned, (c) individual accountability is built in, (d) the AI facilitates the process rather than participating in it, and (e) regulation scaffolds are included.
```

## 示例输出

**情景：** *协作任务：“十年级科学：设计实验测试温度是否影响化学反应速率（盐酸与硫代硫酸钠）。每组必须产出实验方法、风险评估、预测结果图及底层化学原理解释（碰撞理论）” / 协作挑战：“小组总是瓜分任务：一名学生写方法，一名做风险评估，一名画图，一名写理论。他们从不讨论，从不建立共享理解，最终报告只是四块拼在一起的内容。写方法的学生往往不懂理论，写理论的学生也无法复现方法” / 小组规模：“4人” / 学生水平：“十年级，三科科学（triple science）” / AI 能力：“可在设定时间间隔或响应触发条件时向小组发送消息的文本式 AI 聊天机器人” / 可用时间：“60 分钟”*

---

## AI 辅助协作学习设计：实验设计——温度与反应速率

**任务：** 设计一套完整实验，测试温度是否影响盐酸/硫代硫酸钠的反应速率
**解决的协作挑战：** 缺乏共享理解的任务拆分——学生各自为战而非协作，产出碎片化成果
**AI 角色：** AI 在关键节点监控小组过程并发送调节提示。它**绝不**提供科学观点、代写报告的任何部分或回答化学问题。

### 任务复杂度核查

原任务**可以**拆分为彼此独立的子任务（方法、风险评估、图表、理论）——这正是学生会拆分它的原因。要让协作成为必需，必须**重新设计**任务，使各部分相互依赖：

**重构后的任务：** 小组不再产出四个独立板块，而是必须产出**一份**整合文档，其中实验方法的每项决策都必须由理论明确论证，每项风险都必须与实验方法的具体步骤关联，且预测结果图必须由理论推导而出（由小组解释曲线形状）。这种相互依赖性使学生**无法**拆分工作——写方法的学生需要理论学生，反之亦然。

**附加约束：** 每位小组成员都必须能够解释报告的**任何**部分，而不仅仅是“自己”的部分。教师将在最后随机抽取一名成员展示并回答整份报告的相关问题。

### 协作结构

**第一阶段：独立思考（5 分钟）**
每位学生独立写下：（a）自己已经了解的碰撞理论知识，（b）自己尚不确定的一个方面，以及（c）自己的预测——升高温度会加快还是减慢反应速率，为什么？这能激活先验知识，让每位学生都有内容可带入讨论。此阶段**禁止交谈**。

*AI 动作：* 5 分钟结束时，AI 发送：“独立思考时间到。开始讨论前，每人先分享自己写下的**一件事**。按小组顺序轮流发言——在每个人都发言一次前，任何人不得发言两次。”

**第二阶段：建构共享理解（15 分钟）**
小组讨论碰撞理论及温度如何影响反应速率。他们必须就以下两点达成**共识**：（a）为什么升高温度会提高速率（粒子运动更快 → 碰撞更频繁**且**能量更高 → 更多粒子达到活化能），以及（b）预测结果图应呈现什么形状（显示速率随温度上升的曲线——非线性，受活化能分布影响）。暂不动笔——此阶段**仅限讨论**。

*AI 动作：* 在第 10 分钟时，AI 发送调节检查：“快速核查：组里每个人都能解释**为什么**升高温度会加快反应速率吗？不只是‘粒子运动更快’——而是**为什么**运动更快会导致反应更快？如果有人不确定，现在就提问。下一阶段需要用到这一理解。”

**第三阶段：整合设计（25 分钟）**
小组撰写整合报告。为防止任务拆分，采用**轮换执笔人**结构：
- 第 1–8 分钟：成员 A 执笔，其余成员口头贡献。重点：实验方法（但每一步都必须由理论论证——“我们加热至 40°C 是因为……”）。
- 第 9–16 分钟：成员 B 执笔，其余成员贡献。重点：预测结果与原理解释（将曲线形状与碰撞理论关联）。
- 第 17–25 分钟：成员 C 执笔，其余成员贡献。重点：风险评估与变量控制（将风险关联到具体实验步骤，解释控制变量）。
- 成员 D 全程担任“质量核查员”——职责是确保各部分彼此衔接。

角色轮换，但**关键**设计特征在于执笔人必须整合小组的口头输入，而非独自工作。其余三人都在积极贡献想法，而非旁观。

*AI 动作：* 见下方“AI 引导动作”表格。

**第四阶段：展示准备（10 分钟）**
AI 随机抽取一名小组成员代表展示报告并回答教师提问。小组有 10 分钟时间确保被选中的人能够解释**全部内容**——而不仅仅是“自己”的那部分。

*AI 动作：* 第四阶段开始时，AI 发送：“本次展示将由【随机抽选姓名】负责讲解并回答**整份**报告的问题。小组成员请注意：你们有 10 分钟确保【姓名】能够解释实验方法、理论原理、预测结果和风险评估。向 TA 提问，找出理解漏洞。”

**第五阶段：展示汇报（每组 5 分钟）**
被选中的成员进行展示，教师提问。这是个人问责机制——由于任何人都可能被抽中，每位成员都必须理解整份报告。

### AI 引导动作

| 触发条件 | AI 动作 | 目的 | 示例 |
|---|---|---|---|
| 第一阶段结束（5 分钟） | 轮流分享提示 | 确保讨论开始前听到所有声音 | “每人分享自己笔记中的一件事。按顺时针方向。每个人都发言一次前，任何人不得发言两次。” |
| 第二阶段第 10 分钟 | 理解核查 | 在动笔前验证共享理解 | “每个人都能解释为什么升高温度会加快反应速率吗？不只是‘发生了什么’，而是‘为什么会这样’。互相核对一下。” |
| 第三阶段第 5 分钟 | 整合提示 | 防止脱离理论只写实验步骤 | “我注意到你们正在写实验步骤。请为每一步加上：‘我们选择这样做是因为……’将其与你们的理论理解联系起来。” |
| 第三阶段某学生超过 3 分钟未参与贡献 | 参与提示 | 防止脱离小组 | “【姓名】，你对【当前正在撰写的部分】怎么看？小组这里需要你的输入。” |
| 第三阶段第 20 分钟 | 进度检查 | 确保小组按时完成 | “撰写时间还剩 5 分钟。快速核查：你们是否已将方法与理论相连，将预测图与碰撞模型相连？还缺什么？” |
| 第四阶段开始 | 随机抽选与准备提示 | 建立个人问责制 | “已抽选【姓名】进行展示。小组有 10 分钟确保 TA 能解释全部内容。” |

### 调节脚手架

**计划（第二阶段开始）：** AI 发送：“在正式开始前——全组花 60 秒达成一致：对于这项任务，一份**好的**实验设计是什么样的？什么能让你们的设计优于平均水平？写下你们小组的成功标准。”

**监控（第三阶段中期）：** AI 发送：“撰写已过半。回头看看你们设定的成功标准。你们达到这些标准了吗？如果没有，需要调整什么？”

**反思（第三阶段结束、展示准备前）：** AI 发送：“在准备展示前——全组做一次简短反思：在共同完成这项任务时，最困难的部分是什么？下次你们会有什么不同做法？”这能培养对协作过程本身的元认知意识。

### 公平机制

1. **小组讨论前的独立思考（第一阶段）。** 每位学生都带着自己的想法进入讨论，避免一开始就由嗓门最大的学生主导——每个人都有所准备。

2. **轮流分享（第二阶段开始）。** AI 强制执行“在每个人都发言一次前，任何人不得发言两次”。这确保安静的学生在主导型学生接管前先作出贡献。

3. **轮换执笔人结构（第三阶段）。** 没有哪位学生能包揽整份报告的书写。轮换机制迫使不同的人握笔，减少“一人包办所有事”的问题。

4. **质量核查员角色。** 成员 D 的明确职责是确保各部分整合——同时也能留意是否有人停止贡献并把对方拉回讨论。

5. **随机抽选展示（第四阶段）。** 由于任何成员都可能被抽中，小组有动力确保每个人都理解全部内容。“什么都不做”的搭便车者会成为小组主动解决的负担。

6. **AI 参与度监控。** AI 检测个别学生的长时间沉默并提示小组将其纳入讨论。这能捕捉到教师容易遗漏的脱离现象。

### AI 不做什么

- **AI 不回答化学问题。** 如果学生问 AI“什么是碰撞理论？”，AI 应回复：“这是个很适合问你们小组的问题。问问组员——如果大家都不知道，再标记出来请教老师。”
- **AI 不代写报告的任何部分。** 它不生成正文、不建议实验步骤，也不绘制预测图表。
- **AI 不评价科学质量。** 它不说“你们的方法很好”或“你们的理论解释不完整”。质量评价是教师的职责。
- **AI 不裁决分歧。** 如果小组对预测曲线形状有分歧，AI 应说：“你们出现了分歧。很好——这说明有人在深入思考。每个人能解释一下自己的推理吗？然后作为小组做出决定。”AI 引导的是分歧解决的**过程**，而非**内容**。

---

## 已知局限

1. **AI 辅助协作依赖于可靠的 AI 监控。** 上述引导动作假定 AI 能够检测参与不均、沉默和偏离任务的行为。当前 AI 系统在这方面的能力参差不齐——基于文本的监控可行，但在面对面纸笔工作的小组中检测脱离则困难得多。设计可能需要根据具体可用的 AI 系统进行调整。

2. **针对 AI 专门引导协作的实证研究仍在发展中。** Dillenbourg（1999）、Slavin（1995）和 Järvelä & Hadwin（2013）确立了有效协作的原则，但将 AI 专门用于引导这些原则是一个较新的领域，对照研究较少。上述 AI 引导动作是基于成熟研究做出的原则性推演，而非经过实证检验的 AI 干预方案。

3. **协作认知负荷可能较高。** Kirschner 等人（2018）指出，协调成本（沟通、协商、管理不同观点）会消耗认知资源。对于本就在内容理解上有困难的学生，结构化协作带来的额外负荷可能会使他们不堪重负。教师应监控协作结构究竟是在促进还是在阻碍学习。

4. **文化规范会影响协作。** Dillenbourg（1999）的框架主要在西方教育背景下发展而来。在某些文化背景中，直接表达异议、质疑同伴想法或在感知地位更高的人之前发言可能会令人感到不适或不妥。AI 引导提示可能需要进行文化调适。
