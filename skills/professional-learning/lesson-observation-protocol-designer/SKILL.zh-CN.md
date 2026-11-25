---
# AGENT SKILLS STANDARD FIELDS (v2)
name: lesson-observation-protocol-designer
description: "设计聚焦的听课观察规程，包含具体的“观察要点（look-fors）”与证据收集方法。适用于规划同伴互听、教练听课或发展性随堂听课。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "professional-learning/lesson-observation-protocol-designer"
skill_name: "听课观察规程设计器"
domain: "professional-learning"
version: "1.0"
evidence_strength: "moderate"
evidence_sources:
  - "Darling-Hammond (2010) — Evaluating Teacher Effectiveness: how teacher performance assessments can measure and improve teaching"
  - "Hill, Charalambous & Kraft (2012) — When rater reliability is not enough: teacher observation systems and a case for the generalizability study"
  - "Wragg (2012) — An Introduction to Classroom Observation"
  - "O'Leary (2014) — Classroom Observation: a guide to the effective observation of teaching and learning"
  - "Coe et al. (2014) — What Makes Great Teaching? Review of the underpinning research"
input_schema:
  required:
    - field: "observation_focus"
      type: "string"
      description: "待观察的具体教学实践或学习侧面——不是“面面俱到”，而是一个聚焦的透镜"
    - field: "observation_purpose"
      type: "string"
      description: "为什么进行此次观察——发展性、教练辅导、同伴学习、质量保障、研究"
  optional:
    - field: "teacher_context"
      type: "string"
      description: "教龄经验、学科、任何相关背景"
    - field: "student_level"
      type: "string"
      description: "所教年龄/年级"
    - field: "subject_area"
      type: "string"
      description: "课程学科"
    - field: "observation_duration"
      type: "string"
      description: "完整一节课、推门听课（15分钟）还是学习漫步（5分钟）"
    - field: "school_context"
      type: "string"
      description: "学校的听课文化——支持性、高风险还是新举措推行"
output_schema:
  type: "object"
  fields:
    - field: "observation_protocol"
      type: "object"
      description: "完整规程——看什么、怎么记、忽略什么"
    - field: "look_fors"
      type: "array"
      description: "与焦点挂钩的具体、可观察指标——“好”在实践中长什么样"
    - field: "recording_format"
      type: "object"
      description: "观察期间如何捕捉证据——结构化笔记、频次统计、时间抽样"
    - field: "feedback_framework"
      type: "object"
      description: "如何构建课后反馈对话——基于证据、具体且面向未来"
chains_well_with:
  - "instructional-coaching-conversation-guide"
  - "lesson-study-cycle-designer"
  - "reflective-practice-prompt-generator"
  - "explicit-instruction-sequence-builder"
  - "pedagogical-content-knowledge-developer"
  - "technological-pedagogical-content-knowledge-developer"
teacher_time: "3 分钟"
tags: ["observation", "look-fors", "feedback", "professional-development", "evidence-based"]
---

# 听课观察规程设计器

## 本技能的功能

针对特定教学实践设计一份聚焦的、循证的听课观察规程——提供清晰的“观察要点（look-fors）”（实践运作中的可观察指标）、结构化的记录格式，以及课后反馈对话的框架。核心原则在于观察应当是**聚焦的**（寻找特定事物，而非“面面俱到”）、**基于证据的**（记录所见所闻，而非主观评判）和**发展性的**（为教师带来学习，而不仅仅是打分）。产出是一份观察者可直接带进教室的即用型规程，外加一份课后对话反馈框架。AI 在此处具有独特价值，因为设计有效的观察要点需要将抽象教学实践（“有效提问”）转化为可观察的具体指标（“教师提问后至少等待3秒再接受回答”）——这种转化需要兼备研究知识与一线教学经验。

## 循证基础

Darling-Hammond（2010）指出，教师观察在基于标准（关联清晰准则）、基于证据（扎根于可观察行为而非主观印象）且具有发展性（旨在改进实践而非仅仅评级）时最为有效。她强调，观察的质量取决于规程的质量——模糊的标准只会产出模糊的反馈。Hill、Charalambous 与 Kraft（2012）证明，观察信度取决于聚焦度：寻找特定、明确界定实践的观察者，比关注“整体教学质量”的观察者能给出一致性高得多的评定。Wragg（2012）为课堂观察方法提供了奠基性指导，区分了结构化观察（对照预设准则系统记录）与非结构化观察（开放式叙事）。他主张采用结构化方法，因为它们能产出更可靠、更可用的证据。O'Leary（2014）质疑将听课观察用作绩效管理的做法，主张观察在用于专业学习时最有力量——即教师互相听课、接收具体反馈并用它来发展自身实践。Coe 等人（2014）在《What Makes Great Teaching?》中确定了对学生成果拥有最强实证基础的实践：学科内容知识、教学质量（包括提问、反馈与评估）、课堂氛围与课堂管理。这些为观察期间“看什么”提供了实证基础。

## 输入模式

教师必须提供：
- **观察焦点：** 看什么。*例如：“检查理解——教师在进入下一教学环节前如何评估学生是否理解？” / “思考时间与学生参与——有多少学生积极参与回答问题？” / “独立练习期间的反馈——教师巡视时对学生说了什么？”*
- **观察目的：** 为什么。*例如：“发展性——教练循环的一部分，将提问作为商定焦点” / “同伴观察——两位教师互听以分享实践” / “质量保障——学校领导层监测新反馈政策的落实”*

可选（如有，由上下文引擎注入）：
- **教师背景：** 经验、学科、背景
- **学生水平：** 年级
- **学科领域：** 具体学科
- **观察时长：** 完整一节课、推门听课或学习漫步
- **学校情境：** 听课文化

## 提示词

```
You are an expert in classroom observation and teacher development, with deep knowledge of Darling-Hammond's (2010) framework for teacher evaluation, Hill et al.'s (2012) research on observation reliability, Wragg's (2012) observation methods, O'Leary's (2014) developmental approach, and Coe et al.'s (2014) evidence on effective teaching practices. You understand that the value of an observation depends almost entirely on the quality of the protocol — what the observer looks for and how they record it determines what they learn and what feedback they can provide.

CRITICAL PRINCIPLES:
- **Focused, not comprehensive.** An observer cannot meaningfully assess "teaching quality" in one lesson. A focused lens on ONE aspect of practice produces much more useful evidence than a general sweep. The protocol must specify what to look for AND what to ignore.
- **Evidence, not judgement.** The protocol should guide the observer to record what they SEE and HEAR, not what they THINK about it. "The teacher asked 12 questions in 10 minutes, 9 of which were closed" is evidence. "The questioning was weak" is judgement. Evidence can be discussed; judgement provokes defensiveness.
- **Look-fors must be observable.** "The teacher has high expectations" is not observable. "The teacher sets a timer for the task and says 'I expect you to complete all 5 questions'" is observable. The protocol must translate research-based practices into things an observer can actually see and hear.
- **The feedback conversation matters as much as the observation.** The protocol must include guidance for the post-observation conversation — how to share evidence, how to prompt reflection, how to agree on next steps.

Your task is to design an observation protocol for:

**Observation focus:** {{observation_focus}}
**Observation purpose:** {{observation_purpose}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Teacher context:** {{teacher_context}} — if not provided, design a protocol that works for any teacher.
**Student level:** {{student_level}} — if not provided, design for general classroom observation.
**Subject area:** {{subject_area}} — if not provided, design for cross-subject use.
**Observation duration:** {{observation_duration}} — if not provided, design for a full-lesson observation (50–60 minutes).
**School context:** {{school_context}} — if not provided, design for a developmental purpose (not performance management).

Return your output in this exact format:

## Observation Protocol: [Focus Area]

**Focus:** [What the observer is looking for]
**Purpose:** [Why this observation is happening]
**Duration:** [How long]

### Before the Observation

[What the observer should know, do, or prepare before entering the classroom]

### Look-Fors

For each look-for (4–6):
**Look-for [N]: [Observable indicator]**
- **What to watch/listen for:** [Specific, observable behaviour]
- **Evidence of strong practice:** [What this looks like when done well]
- **Evidence of developing practice:** [What this looks like when it's not yet strong]
- **How to record:** [Tally, time-stamp, verbatim quote, or narrative note]

### Recording Template

[A structured format the observer can use during the observation]

### Post-Observation Feedback Framework

[How to structure the feedback conversation — evidence-based, specific, forward-looking]

### What NOT to Look For

[What to deliberately exclude from this observation — to maintain focus]

**Self-check before returning output:** Verify that (a) every look-for is observable (you can see or hear it), (b) the protocol distinguishes evidence from judgement, (c) the recording format is practical (can be used in real-time), (d) the feedback framework is evidence-based and developmental, and (e) the protocol is focused — it looks for specific things, not everything.
```

## 示例输出

**场景：** *观察焦点：“检查理解——具体而言，教师在进入课堂下一阶段前如何评估学生是否掌握了内容。他们是在检查所有学生，还是只检查举手的志愿者？” / 观察目的：“发展性——教练循环的一部分。教师已将‘响应式教学’确定为自己的发展焦点。本次观察旨在收集其当前检查理解实践的证据。” / 教师背景：“教龄4年，九年级地理” / 观察时长：“完整一节课（55分钟）”*

---

## 听课观察规程：检查理解

**焦点：** 教师在继续推进前如何检查学生是否理解——检查了谁、如何检查以及如何处理收集到的信息
**目的：** 发展性——教练循环，教师自选的发展焦点领域
**时长：** 完整一节课（55分钟），九年级地理

### 观察前准备

1. **与教师确认焦点。** 课前确认：“我这次专门观察你如何检查理解——何时检查、如何检查以及你如何处理这些信息。我不会去看其他任何方面。”这能减轻焦虑，并确保教师清楚预期。

2. **获取教案。** 询问教师：“你预计在课上的哪些节点检查理解？你希望了解什么？”这为观察者提供了背景，并标出了计划中的检查点（教师也可能会随机检查，这同样重要）。

3. **选择座位。** 坐在教室后方或侧面，确保能同时看到教师与学生。你需要观察学生的反应（而不仅仅是教师的提问），因此能看到学生面部表情、小白板和书面作业的位置至关重要。

### 观察要点（Look-Fors）

**观察要点 1：检查了多少名学生？**
- **看什么/听什么：** 当教师检查理解时，所用技术是从**所有**学生那里收集信息，还是仅从举手志愿者那里收集？统计每次检查涉及多少名学生。
- **成熟实践的证据：** 全班技术：迷你小白板配合“3-2-1-亮板”（所有学生同时作答）、出口卡（每位学生书写）、随机点名（非举手者）。教师从 80% 以上的学生那里收集了数据。
- **发展中实践的证据：** “懂了的举手？”（自我报告，而非证据）。“有问题吗？”（依赖学生自己知道哪里不懂）。只有 3–5 名学生回应，而 20 多人未被检查。
- **如何记录：** 针对每次检查时刻，记下：所用技术、大致回应学生人数，以及该回应是要求**展示**理解，还是仅**声称**理解。

**观察要点 2：检查的是哪种类型的理解？**
- **看什么/听什么：** 该检查测试的是回忆（学生能记住说过的话吗？）、程序性应用（他们能做出来吗？），还是概念性理解（他们能解释为什么吗？）？
- **成熟实践的证据：** 要求学生解释、应用或展示的问题与任务——而非仅仅复述。“向我展示你会如何计算该地区的人口密度”（应用） vs. “什么是人口密度？”（回忆）。
- **发展中实践的证据：** 仅测试表层回忆的检查：“谁能说说我们刚才讲的人口密度是什么？”学生可以复述定义而不理解它。
- **如何记录：** 对每次检查分类：回忆 / 应用 / 解释。记下原原本本的问题或任务。

**观察要点 3：时机——教师何时检查？**
- **看什么/听什么：** 教师是在进入下一阶段**之前**检查（诊断性——用于决定下一步做什么），还是只在课堂**末尾**检查（终结性——为时已晚无法调整）？
- **成熟实践的证据：** 检查发生在过渡节点——在教师讲解完一个概念之后、学生独立练习之前；在有指导的练习之后、放手独立作业之前。检查是一个决策点：“我是继续推进、重新讲解还是差异化？”
- **发展中实践的证据：** 只在最后检查（下课铃响时的出口卡），或根本不检查（教师看到学生点头就假设懂了）。
- **如何记录：** 为每次检查时刻打上时间戳。记下它在课程序列中的位置（讲解期间 / 指导练习后 / 独立作业前 / 课末）。

**观察要点 4：教师拿到信息后“做了”什么？**
- **看什么/听什么：** 检查之后，教师是否做出了调整？还是不管结果如何照常推进？
- **成熟实践的证据：** 教师检查（小白板显示 60% 正确），停下来，重新讲授：“我看出来你们中有些人对这个还不太确定。让我换种方式再演示一遍。”**或者**教师检查，看到 90% 正确，继续推进：“太棒了——你们掌握了，我们继续。”检查结果决定了**下一个**教学决策。
- **发展中实践的证据：** 教师检查，看到结果参差不齐，依然照常推进：“好的，不错，我们看下一部分。”收集了数据却未使用。这是有诊断而无形成性作用。
- **如何记录：** 针对每次检查，记下：数据显示了什么 **以及** 教师接下来做了什么。下一步行动是否对数据做出了回应？

**观察要点 5：学生对检查的投入度**
- **看什么/听什么：** 学生是否认真对待检查？他们是在真诚尝试，还是匆匆应付、抄袭或敷衍？
- **成熟实践的证据：** 学生充分投入检查任务——思考、书写、讨论。检查已成为学生看重的常规，因为他们知道教师会用它来帮助自己。
- **发展中实践的证据：** 学生敷衍作答、抄袭邻座或根本不回应。检查沦为毫无感知价值的例行仪式。
- **如何记录：** 记录每次检查期间的学生投入水平，估算大致参与率。

### 记录模板

| 时间 | 所用检查技术 | 被检查学生数 | 类型（回忆/应用/解释） | 数据显示结果 | 教师下一步行动 | 是否响应？(是/否) |
|---|---|---|---|---|---|---|
| | | | | | | |
| | | | | | | |

同时记录：检查性问题的逐字原话（一字不差地记下来）。

### 课后反馈框架

**第 1 步——分享证据，而非评判（5分钟）：**
“以下是我记录的情况。你在课上一共检查了 [X] 次理解。使用的技术有 [列表]。回应的学生人数从 [Y 到 Z] 不等。以下是你提出的问题原话：[逐字引用]。”

出示记录模板，让教师阅读。

**第 2 步——邀请反思（10分钟）：**
“看着这些数据，你注意到了什么？”（让他们自己分析。）
“你觉得哪一次检查对你的教学最有用？为什么？”
“有没有哪一次你检查了，并利用所得信息改变了接下来的教学？”
“有没有哪些时刻你希望自己当时检查了却没检查？”

**第 3 步——确定一个具体下一步（10分钟）：**
“基于我们看到的，你下次最想改变或尝试的**一件事**是什么？”
下一步应当具体且可实现：例如，“在讲解与练习的过渡节点使用迷你小白板，在放手让学生独立作业前检查所有学生。”

**第 4 步——规划跟进（5分钟）：**
“你打算什么时候尝试？需要我来观察那个具体时刻吗？我们可以对比一下数据。”

### 不看什么

在本次观察中，刻意**忽略**：
- 教师学科知识的质量（非本次焦点）
- 行为管理（除非直接影响检查理解）
- 教具或墙面展示的质量
- 教师的表达风格、自信度或个人魅力
- 学生在笼统意义上是否“投入”（仅关注对检查任务的投入）

聚焦于**一个**侧面能产出深刻、有用的证据；把注意力分散到所有方面只会产出浅层印象。

---

## 已知局限

1. **单次观察只是一个快照。** 一节课未必能代表教师的常态实践。教师可能因为被听课而表现不同（观察者效应）。该规程应跨多次观察使用，以建构可靠图景。

2. **反馈质量取决于观察者的技能。** 一份设计精良的规程若落在以评判语气传递反馈的观察者手中，只会引发防御而非成长。反馈框架引导对话，但观察者必须接受培训，以基于证据的对话而非评价的方式传递反馈。

3. **发展性观察与绩效管理观察需要不同路径。** 本规程专为发展性目的设计。如果将同一规程用于高风险绩效考核，教师就会为观察者“表演”而非自然教学，数据也会失真。学校应将发展性听课与问责性考核分离开来。
