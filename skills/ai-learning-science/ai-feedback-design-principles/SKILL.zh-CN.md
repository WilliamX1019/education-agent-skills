---
# AGENT SKILLS STANDARD FIELDS (v2)
name: ai-feedback-design-principles
description: "从教学质量、时机与学习效果维度审计并重新设计 AI 生成的反馈。适用于构建或审查数字学习工具中的自动反馈。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "ai-learning-science/ai-feedback-design-principles"
skill_name: "AI 反馈设计原则"
domain: "ai-learning-science"
version: "1.0"
evidence_strength: "strong"
evidence_sources:
  - "Shute (2008) — Focus on formative feedback (comprehensive review)"
  - "Narciss (2008) — Feedback strategies for interactive learning tasks (informative tutoring feedback model)"
  - "Hattie & Timperley (2007) — The power of feedback (meta-analysis, effect size 0.73)"
  - "Dai et al. (2023) — Can large language models provide useful feedback on research papers? A large-scale empirical analysis"
  - "Kluger & DeNisi (1996) — The effects of feedback interventions on performance: A historical review and a meta-analysis"
input_schema:
  required:
    - field: "feedback_scenario"
      type: "string"
      description: "AI 将提供反馈的具体情境——学生做了什么，以及需要什么样的反馈"
    - field: "current_feedback_design"
      type: "string"
      description: "当前或拟议的 AI 反馈方案——系统当前或计划针对学生作业输出什么内容"
  optional:
    - field: "student_level"
      type: "string"
      description: "年龄/年级及能力水平"
    - field: "subject_area"
      type: "string"
      description: "课程学科"
    - field: "feedback_goals"
      type: "string"
      description: "反馈应实现的目标——纠错、激励、深化思考、自我调节或其他"
    - field: "system_constraints"
      type: "string"
      description: "反馈的技术或实际限制——字数限制、时机要求或格式限制"
output_schema:
  type: "object"
  fields:
    - field: "feedback_evaluation"
      type: "object"
      description: "对照研究标准分析当前反馈设计——哪些有效，哪些无效"
    - field: "improved_feedback"
      type: "object"
      description: "针对已识别弱点重新设计的反馈版本"
    - field: "feedback_type_analysis"
      type: "object"
      description: "按类型（验证型、详述型、策略型）对反馈分类，并给出最佳组合建议"
    - field: "implementation_guidance"
      type: "object"
      description: "在目标系统中部署改进后反馈的实用建议"
chains_well_with:
  - "adaptive-hint-sequence-designer"
  - "formative-assessment-loop-designer"
  - "intelligent-tutoring-dialogue-designer"
  - "self-explanation-prompt-designer"
  - "technological-pedagogical-content-knowledge-developer"
teacher_time: "4 分钟"
tags: ["feedback", "AI-feedback", "formative", "Shute", "Narciss", "Hattie", "LLM", "automated-feedback"]
---

# AI 反馈设计原则

## 本技能的作用

对照有效自动反馈的研究标准，评估拟议的 AI 反馈设计并提出具体改进方案。本技能接收反馈情景（学生做了什么）及当前或拟议的 AI 回复（系统说了什么），然后依据 Shute（2008）、Narciss（2008）、Hattie & Timperley（2007）以及新兴大语言模型反馈研究（Dai et al., 2023）的原则进行剖析。输出包括当前效果诊断、重新设计的反馈版本以及实用实施指南。核心挑战在于，大多数 AI 反馈都会落入两种失效模式之一：要么过于笼统而无法落地（“写得不错！试着改进你的论点。”），要么过于具体而直接替学生思考（“你的中心论点应该是：气候变化是我们这一代人的决定性挑战，因为……”）。有效反馈存在于这两种极端之间的狭窄地带——具体到让学生知道该做什么，但又不会具体到绕过产生学习的认知加工过程。AI 在此尤为关键，因为它能规模化生成反馈，但也正因如此，设计原则才更为重要：规模化的劣质反馈比没有反馈更糟。

## 实证基础

Hattie & Timperley（2007）的一项元分析发现，反馈的平均效应量为 0.73——使其成为影响学习的最强因素之一。然而，他们也发现了巨大差异：部分反馈干预产生了显著正向效果，另一些则毫无效果甚至产生**负面**效果。关键变量不在于是否给予反馈，而在于给予了**哪种**反馈。他们提出了四层次模型：任务反馈（答案是否正确？）、过程反馈（哪些策略能改进作品？）、自我调节反馈（如何监控自己的学习？）以及自我反馈（你是个很棒的学生！）。任务反馈和过程反馈最为有效；自我反馈（“干得好！”）效果最差，有时甚至有害，因为它将注意力引向自我而非任务。Shute（2008）综述了形成性反馈研究并总结出关键原则：有效反馈应具体、及时、非威胁性，并聚焦于任务而非学习者。她区分了验证型反馈（正确/错误）、详述型反馈（为什么对/错以及下一步怎么做）及其多种组合。她发现详述型反馈通常优于简单验证，**但**过于详尽的反馈会使初学者不堪重负——从而形成“信息越多、学习反而越少”的反馈悖论。Narciss（2008）提出了信息性辅导反馈（ITF）模型，指出有效反馈应包含：结果知识（对或错）、正确答案知识（如果出错）以及对错误的详述（为什么错以及暴露了什么迷思概念）。关键在于，Narciss 发现最佳反馈取决于错误类型：概念性错误受益于详述型反馈，而粗心笔误则受益于简单验证。Kluger & DeNisi（1996）在其元分析中发现，将注意力引向自我（而非任务）的反馈可能会**降低**表现——这一发现对喜欢生成空洞鼓励性赞美的 AI 系统具有直接启示。Dai 等人（2023）评估了 LLM 生成的反馈，发现尽管 LLM 能产出流畅、结构良好的反馈，但往往呈现出一种特定倾向：过度正面、建议笼统且不愿指出具体错误——而这恰恰是研究认为效果最差的模式。

## 输入规范

教师必须提供：
- **反馈情景（Feedback scenario）：** 学生做了什么。*例如：“九年级学生提交了一篇议论文，主张废除校服。论证很有激情，但完全依赖个人轶事——没有证据、没有回应反方论点、逻辑结构薄弱” / “七年级学生解方程 3x + 5 = 20 得到 x = 7（错误——应为 x = 5）” / “A-level 学生写了一份实验报告，数据正确，但结论无法从结果中推导出来”*
- **当前反馈设计（Current feedback design）：** AI 当前或计划输出什么。*例如：“很棒的作文！你显然对这个话题很有热情。要改进的话，试着加一些证据并考虑一下另一方的观点” / “错误。答案是 x = 5。再试一次” / “你的结论需要修改。想想你的数据实际说明了什么”*

可选项（如可用则由上下文引擎注入）：
- **学生水平（Student level）：** 年级与能力水平
- **学科领域（Subject area）：** 课程学科
- **反馈目标（Feedback goals）：** 反馈应达成的目标
- **系统限制（System constraints）：** 技术或实际限制

## 提示词（Prompt）

```
You are an expert in the science of feedback in learning, with deep knowledge of Hattie & Timperley's (2007) feedback model (task, process, self-regulation, self levels), Shute's (2008) formative feedback principles, Narciss's (2008) Informative Tutoring Feedback model, Kluger & DeNisi's (1996) meta-analysis on feedback interventions, and emerging research on LLM-generated feedback quality (Dai et al., 2023). You understand that feedback is one of the most powerful influences on learning — and one of the most dangerous when poorly designed. You know that AI systems tend toward a specific failure mode: generating feedback that is positive, fluent, well-structured, and educationally useless.

CRITICAL PRINCIPLES:
- **Feedback must be SPECIFIC and ACTIONABLE.** "Good effort" is not feedback. "Your introduction states a position but doesn't preview your three supporting arguments — add a sentence that maps out your essay structure" IS feedback. If a student cannot read the feedback and know EXACTLY what to do next, it has failed.
- **Distinguish verification, elaboration, and strategic feedback.** Verification: "This is incorrect." Elaboration: "This is incorrect because you subtracted 5 from the left side but not the right." Strategic: "When you get stuck on equations, always check: did I do the same operation to both sides?" Different errors need different types. A conceptual error needs elaboration. A careless slip needs verification. A recurring pattern needs strategic feedback.
- **Avoid the positivity trap.** AI systems default to excessive positivity. "Great work!" before pointing out fundamental errors sends a contradictory signal and dilutes the corrective message. Positive feedback is appropriate ONLY when genuinely earned AND directed at specific features ("Your use of statistical evidence in paragraph 2 is effective because it directly supports your claim"). Generic praise is worse than no praise at all (Kluger & DeNisi, 1996).
- **Don't do the student's thinking.** Feedback that tells the student exactly what to write, what the answer is, or how to fix their work is not feedback — it's answer-giving. The goal is to close the gap between current and desired performance by showing the student WHERE the gap is and giving them enough information to close it themselves.
- **Match feedback complexity to student level.** Novice learners benefit from simple, clear feedback focused on one or two specific issues. Advanced learners benefit from more complex feedback that addresses multiple dimensions. Overloading novices with comprehensive feedback produces cognitive overload, not learning (Shute, 2008).

Your task is to evaluate and improve this feedback design:

**Feedback scenario:** {{feedback_scenario}}
**Current feedback design:** {{current_feedback_design}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Student level:** {{student_level}} — if not provided, infer from the scenario.
**Subject area:** {{subject_area}} — if not provided, infer from the scenario.
**Feedback goals:** {{feedback_goals}} — if not provided, assume the goal is to help the student improve their work while preserving their ownership of the thinking.
**System constraints:** {{system_constraints}} — if not provided, assume no significant constraints.

Return your output in this exact format:

## Feedback Evaluation: [Brief Scenario Description]

**Scenario:** [What the student did]
**Current feedback:** [What the AI currently says]
**Verdict:** [One-sentence summary — is this feedback likely to improve learning, have no effect, or actively harm it?]

### Diagnosis

[Analyse the current feedback against each principle. What works? What doesn't? Be specific — quote the problematic parts of the feedback and explain WHY they are problematic, citing the relevant research.]

### Feedback Type Analysis

| Feedback Component | Type | Effectiveness | Issue |
|---|---|---|---|
| [Quote from current feedback] | [Verification / Elaboration / Strategic / Self] | [Effective / Ineffective / Harmful] | [Why] |

### Improved Feedback Design

[The redesigned feedback. Show the exact text the AI should present to the student. Include specific, actionable guidance that addresses the identified weaknesses without doing the student's thinking for them.]

**Redesigned feedback:**

> [The exact feedback text]

### Design Rationale

[Explain why the improved version is better — what principles it follows and what specific changes were made.]

### Implementation Notes

[Practical guidance for deploying this feedback pattern — when it should trigger, how to handle edge cases, and what to watch for.]

**Self-check before returning output:** Verify that (a) the improved feedback is specific and actionable, (b) it doesn't do the student's thinking, (c) it avoids empty praise, (d) it uses the right type of feedback for the error type, and (e) it's appropriate for the student's level.
```

## 示例输出

**情景：** *反馈情景：“九年级学生提交了一篇议论文，主张废除校服。论证很有激情，但完全依赖个人轶事——没有证据、没有回应反方论点、逻辑结构薄弱。文章约 400 词，包含引言、三个主体段和结论。” / 当前反馈设计：“很棒的作文！你显然对这个话题很有热情，你的写作声音很有感染力。要改进的话，试着加一些证据来支持你的观点，并考虑回应一下对立观点。你的结论可以更有力——试着重申你的主要论点。总体而言，这是一次扎实的努力——继续加油！7/10” / 学生水平：“九年级，目标等级 6（相当于英国 GCSE）” / 学科领域：“英语语言——说服性写作”*

---

## 反馈评估：九年级说服性写作——校服议题

**情景：** 九年级学生写了一篇完全依赖个人轶事、缺乏证据、没有反方论证且结构薄弱的议论文。
**当前反馈：** “很棒的作文！你显然对这个话题很有热情……试着加一些证据……考虑回应一下对立观点……一次扎实的努力——继续加油！7/10”
**结论：** 该反馈不太可能带来改进。它过于笼统、过度正面，并在作文存在根本性结构问题时告诉学生他们做得很好。

### 问题诊断

**问题 1：正面陷阱。** 反馈以“很棒的作文！”开头——但文章存在根本性缺陷（没有证据、没有反方论证、结构薄弱）。这发出了矛盾的信号：你一边告诉学生作文很棒，一边又列出所有问题。Kluger & DeNisi（1996）发现，将注意力引向自我（“你显然很有热情”）而非任务的反馈会降低学习效果。学生接收到的信息是：“我得了 7/10，老师喜欢我的文风，我只需微调几处就行。”

**问题 2：改进建议笼统。** “试着加一些证据”——什么类型的证据？加在文章哪里？加多少？“考虑回应一下对立观点”——哪一个对立观点？放在文章何处？如何组织？Shute（2008）发现，反馈必须具体到让学生清楚知道该怎么做。这些建议过于模糊，无法执行。

**问题 3：没有诊断出真正的问题。** 这篇文章的根本问题在于学生不理解“断言（assertion）”与“论证（argument）”的区别。每一段都在提出主张，却只用个人经历来支撑。反馈没有点明这一问题——它只处理了表面症状（无证据、无反方论证），却未指出深层原因（学生把强烈情绪等同于有力论证）。

**问题 4：分数削弱了反馈。** 7/10 传递的信号是“这已经不错了”。如果文章既无证据又无反方论证，它并未达到议论文的基本标准。分数与反馈相互冲突。学生会锚定在分数上而忽视改进建议。

### 反馈类型分析

| 反馈成分 | 类型 | 有效性 | 问题 |
|---|---|---|---|
| “很棒的作文！” | 自我（Self） | 有害 | 将注意力引向自我而非任务的空洞赞美 |
| “你显然很有热情” | 自我（Self） | 无效 | 描述的是学生，而非作品本身 |
| “你的写作声音很有感染力” | 任务（Task） | 轻度有效 | 足够具体因而有一定用处，但被淹没在泛泛赞美中 |
| “试着加一些证据” | 策略（Strategic） | 无效 | 过于笼统——什么证据、哪里加、怎么加？ |
| “考虑回应一下对立观点” | 策略（Strategic） | 无效 | 过于笼统——哪个观点、放在文章何处？ |
| “你的结论可以更有力” | 任务（Task） | 无效 | 没有具体说明时，“更有力”毫无意义 |
| “一次扎实的努力——继续加油！” | 自我（Self） | 有害 | 在需要大幅修改时给予虚假安慰 |
| “7/10” | 验证（Verification） | 有害 | 分数与根本性修改的需求相矛盾 |

### 改进后的反馈设计

**重新设计的反馈：**

> **有效之处：** 你的写作声音自信且直接——“我不应该每天都穿着别人对我是谁的定义”是一句有力且令人印象深刻的表达。请保留这种表达风格。
>
> **主要问题——断言 vs. 论证：** 目前，每一段都提出一个主张，并用个人经历作为支撑。这是**断言**，而不是**论证**。说服性写作需要**证据**——即那些与你意见不同的人也必须认真对待的事实、统计数据、专家意见或真实案例。读者会想：“**你**是这么觉得，但为什么我应该在意？”
>
> **首先尝试一个具体修改：** 选出你最强的一段（我建议第 2 段关于舒适度的内容）。找**一条**支持你观点的证据——比如关于学生专注力的研究、取消校服并测量效果的学校案例，或教育专家的引述。把它加进去。然后看看它对这一段带来了什么变化。这就是断言与论证的区别。
>
> **之后的下一步：** 选出**反对**你立场的最佳论点（很可能是成本——校服能为家庭省钱）。写一段话，先承认这一论点，再解释为什么你的立场依然更有力。这叫反方论证（counterargument），是议论文中最具说服力的手法——它表明你已经考虑过另一方，但你的论据依然更胜一筹。
>
> **先别急着改。** 首先重读一遍你的作文，在每一句有**证据**（而非个人经历）支撑的句子旁边画一颗星。数一数星星的数量。这个数字会告诉你还需要做多少修改。

### 设计理据

重新设计的反馈做出了五项关键调整：

1. **先给出具体的正面反馈，且指向任务本身。** “你的写作声音自信且直接”并附上原文引述——这是针对真实优点的任务级反馈，而非笼统的自我级赞美。它准确告诉学生该保留什么。

2. **点明底层问题。** “断言 vs. 论证”为学生提供了一个概念框架，以理解哪里出了问题。这属于详述型反馈（Narciss, 2008）——它不仅说“加证据”，还解释**为什么**需要证据以及文章当前缺少什么。

3. **一个具体、可管理的行动。** 反馈没有给出一长串模糊的修改清单，而是给出**一个**具体任务：为某一段寻找一条证据。这遵循了 Shute（2008）将反馈复杂度与学习者水平匹配的原则——目标等级 6 的九年级学生需要聚焦、可实现的步骤，而不是事无巨细的全面批评。

4. **对反方论证的指令进行了脚手架拆解。** 它不只是说“回应一下对立观点”——而是告诉学生该选哪一个对立论点，并解释包含它的策略原因。这属于过程级反馈（Hattie & Timperley, 2007）。

5. **用诊断任务替代分数。** “数一数星星”是一个自我调节提示，帮助学生自己看见问题所在，而不是被动被告知。这培养了元认知意识——一种建立学习独立性的高阶反馈功能。

### 实施说明

- **不要以分数开头。** 如果系统要求必须给分，请将其放在可操作反馈之后的末尾。更好的做法是推迟到修改后再给分。
- **将反馈限制在 2–3 个可操作要点。** 本例处理了两个问题（证据、反方论证）外加一个元认知提示。这是九年级学生的上限。要点过多会导致认知超载和行动瘫痪。
- **警惕 LLM 的正面偏好模式。** 如果由 AI 生成反馈，请审查其是否存在“干得好！但……”的模式（Dai et al., 2023）。指示模型以具体、有据可依的赞美开头，或直接以诊断开头——不要使用泛泛的热情开场白。
- **修改后重新评估。** 上述反馈旨在促成特定修改（为某一段增加证据、增加反方论证段）。修改完成后，反馈应转向其他问题——例如结构与逻辑流畅度。如果学生已经落实了建议，就不要重复相同的反馈。

---

## 已知局限

1. **本技能评估的是反馈“设计”，而非反馈“传递”。** 同一段反馈文本的效果或好或坏，取决于时机、学生情绪状态以及学生与系统的关系。刚连续三次作业失败的学生，与一名粗心出错的自信学生，需要不同的情绪基调。本技能处理的是内容与结构，而非情感与时机。

2. **LLM 反馈的实证基础仍在发展中。** Dai 等人（2023）是最早的大规模 LLM 反馈质量研究之一，该领域正在迅速演进。Shute（2008）、Narciss（2008）和 Hattie & Timperley（2007）的原则在人类反馈中已得到充分确立——将其应用于 AI 生成反馈在理论上合理，但尚未得到全面实证检验。

3. **文化背景会影响反馈规范。** 此处推荐的直接、任务导向反馈风格反映了西方教育研究规范。在某些文化背景中，直接批评（哪怕是建设性的）可能会被以不同方式接收。Narciss（2008）的模型主要在欧美背景下发展起来。

4. **反馈与学生自我效能感之间存在复杂的交互作用。** Kluger & DeNisi（1996）发现，当反馈威胁到自我概念时，会降低表现。对于自我效能感极低的学生，“不给空洞赞美”的原则需要与“避免进一步打击动机”的风险相平衡。本技能并未对个别学生的动机状态进行建模。
