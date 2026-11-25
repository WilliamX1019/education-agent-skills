---
# AGENT SKILLS STANDARD FIELDS (v2)
name: professional-development-session-designer
description: "运用成人学习原则设计具有教师积极参与的专业发展培训课程。适用于规划教师培训日（INSET）、持续专业发展（CPD）工作坊或教职工培训。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "professional-learning/professional-development-session-designer"
skill_name: "专业发展课程设计器"
domain: "professional-learning"
version: "1.0"
evidence_strength: "strong"
evidence_sources:
  - "Timperley et al. (2007) — Teacher Professional Learning and Development: Best Evidence Synthesis (BES)"
  - "Darling-Hammond, Hyler & Gardner (2017) — Effective Teacher Professional Development"
  - "Desimone (2009) — Improving impact studies of teachers' professional development"
  - "Kennedy (2016) — How does professional development improve teaching?"
  - "Knowles (1984) — Andragogy: adult learning theory"
input_schema:
  required:
    - field: "pd_topic"
      type: "string"
      description: "本场培训旨在发展的教学实践或知识"
    - field: "audience"
      type: "string"
      description: "参与者——教师人数、教龄范围、学科、角色"
    - field: "session_duration"
      type: "string"
      description: "培训持续时长——1小时、2小时、半天、全天"
  optional:
    - field: "session_purpose"
      type: "string"
      description: "举办本场培训的原因——新举措、改进重点、教师需求"
    - field: "current_practice"
      type: "string"
      description: "教师目前在该领域的做法——起点现状"
    - field: "school_context"
      type: "string"
      description: "相关学校特征——改进重点、督导评估、教师士气"
    - field: "follow_up_plan"
      type: "string"
      description: "培训结束后发生什么——教练辅导、同伴互听、后续场次"
    - field: "facilitator_expertise"
      type: "string"
      description: "谁主持本场培训及其在该主题上的专业水平"
output_schema:
  type: "object"
  fields:
    - field: "session_plan"
      type: "object"
      description: "运用成人学习原则的时间结构化培训方案"
    - field: "active_learning_tasks"
      type: "array"
      description: "要求教师“做”而非仅“听”的动手任务"
    - field: "practice_application"
      type: "object"
      description: "教师如何在自己课堂上应用所学——具体承诺"
    - field: "follow_through"
      type: "object"
      description: "培训后发生什么以延续学习——问责、支持、复盘"
chains_well_with:
  - "instructional-coaching-conversation-guide"
  - "lesson-study-cycle-designer"
  - "teacher-inquiry-cycle-designer"
  - "reflective-practice-prompt-generator"
  - "pedagogical-content-knowledge-developer"
  - "technological-pedagogical-content-knowledge-developer"
teacher_time: "4 分钟"
tags: ["CPD", "professional-development", "Timperley", "adult-learning", "INSET", "staff-training"]
---

# 专业发展课程设计器

## 本技能的功能

运用循证的成人学习原则设计专业发展（PD）课程——确保课程是主动的（教师动手**做**，而不仅仅是听）、与实践相连的（教师规划如何将所学应用于自己的课堂），并包含后续跟进（课后如何延续改变）。来自 Timperley 研究的核心洞察在于：大多数专业发展之所以失败，不是因为内容不对，而是因为**设计**不对：一场没有跟进、没有练习、没有问责的一次性讲座对教学带来的改变为零。产出是一份带时间结构的课程计划，包含主动学习任务、实践应用活动以及后续跟进计划。AI 在此处具有独特价值，因为设计有效的 PD 需要在有限时间内平衡内容传递（教师需要学到新东西）、积极投入（教师需要加工与应用它）以及实用规划（教师离开时需带走针对自己课堂的具体计划）。

## 循证基础

Timperley 等人（2007）对有效专业学习进行了迄今最全面的综合研究，发现有影响力的 PD 具备以下特征：（a）随时间持续（非一次性）；（b）聚焦教学实践与学生成果之间的联结；（c）让教师参与主动学习（非被动倾听）；（d）包含协作；（e）得到专家型引导支持；（f）将理论与实践整合。他们发现，PD 的**内容**不如**过程**重要——围绕重要主题但设计糟糕的培训，产生的改变还不如围绕更窄主题但设计精良的培训。Darling-Hammond、Hyler 与 Gardner（2017）确定了有效 PD 的七项特征：聚焦内容、主动学习、协作、有效实践示范、教练与专家支持、反馈与反思，以及持续时长。Desimone（2009）提出了一个核心概念框架：有效 PD 改变教师知识与信念 → 进而改变教学实践 → 进而改变学生成果。Kennedy（2016）指出，PD 改进教学不是靠塞入新技术，而是通过帮助教师理解某些方法**为什么**有效——即机制，而不仅仅是方法。Knowles（1984）确立了成人学习原则：当学习以问题为基础（而非抽象）、连接自身经验、提供选择且具有即时实践应用价值时，成人学得最好。

## 输入模式

教师或 PD 负责人必须提供：
- **PD 主题：** 培训关于什么。*例如：“在全校推行提取练习” / “运用形成性评估提升教学响应性” / “在主流课堂中支持有特殊教育需求（SEND）的学生” / “提升教师反馈的质量”*
- **受众：** 谁参加。*例如：“30名教师，跨学科，从新入职教师（ECT）到资深教职工” / “英语教研组8名成员，均有丰富经验” / “全体60名教职工，教师培训日（INSET）”*
- **课程时长：** 多长时间。*例如：“放学后1小时” / “2小时 INSET 培训” / “全天——6小时”*

可选（如有，由上下文引擎注入）：
- **培训目的：** 为什么举办
- **当前实践：** 教师已经在做什么
- **学校情境：** 改进重点、教职工士气
- **后续计划：** 培训后发生什么
- **引导者专长：** 谁主持及其背景

## 提示词

```
You are an expert in professional development design, with deep knowledge of Timperley et al.'s (2007) Best Evidence Synthesis on professional learning, Darling-Hammond et al.'s (2017) features of effective PD, Desimone's (2009) conceptual framework, Kennedy's (2016) research on how PD improves teaching, and Knowles' (1984) adult learning principles. You understand that most PD fails because it is designed as a presentation (passive, one-off, disconnected from practice) when it should be designed as a learning experience (active, sustained, connected to the teacher's own classroom).

CRITICAL DESIGN PRINCIPLES:
- **The 20/80 rule:** No more than 20% of session time should be the facilitator talking. At least 80% should be teachers DOING: discussing, planning, practising, analysing, creating. If you design a session that is mostly presentation, you have failed.
- **Start from teachers' experience (Knowles, 1984).** Adults learn by connecting new knowledge to existing practice. The session must begin with what teachers already know and do, not with what they should do.
- **End with a specific classroom commitment.** Every teacher should leave with a concrete plan: "In my Year 8 lesson on [topic] next [day], I will try [specific strategy]." Vague takeaways ("I'll try to use more formative assessment") produce no change.
- **Plan the follow-through.** A session without follow-up is professional entertainment, not professional development. What happens next week, next month?
- **Respect teachers' time and intelligence.** Teachers are professionals with deep expertise. Don't patronise. Don't over-simplify. Don't pretend the solution is easy when it's complex.

Your task is to design a PD session on:

**PD topic:** {{pd_topic}}
**Audience:** {{audience}}
**Session duration:** {{session_duration}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Session purpose:** {{session_purpose}} — if not provided, infer from the topic.
**Current practice:** {{current_practice}} — if not provided, build in an activity that surfaces current practice.
**School context:** {{school_context}} — if not provided, design for a general school context.
**Follow-up plan:** {{follow_up_plan}} — if not provided, recommend a follow-up structure.
**Facilitator expertise:** {{facilitator_expertise}} — if not provided, design for a facilitator with good knowledge of the topic.

Return your output in this exact format:

## PD Session: [Topic]

**Topic:** [What teachers will learn]
**Audience:** [Who attends]
**Duration:** [How long]

### Session Overview

[One paragraph: what teachers will learn, do, and leave with]

### Session Plan

For each phase:
**[Time block]: [Phase name]**
- **Facilitator does:** [What the facilitator says/does — kept brief]
- **Teachers do:** [What teachers actively do — the main activity]
- **Purpose:** [Why this phase matters for the learning]
- **Resources needed:** [Materials, handouts, technology]

### Active Learning Tasks

[Detailed description of the 2–3 key active tasks — what teachers do, how it's structured, what it produces]

### Practice Application

[How teachers plan to apply the learning in their own classroom — a specific planning activity]

### Follow-Through Plan

[What happens after the session — coaching, peer observation, check-in meeting, follow-up session]

### Facilitator Notes

[Tips for the facilitator — how to manage the session, common challenges, how to handle resistance]

**Self-check before returning output:** Verify that (a) at least 80% of session time is active (teachers doing, not listening), (b) the session starts from teachers' existing practice, (c) every teacher leaves with a specific classroom commitment, (d) follow-through is planned, and (e) the session respects teachers' professionalism.
```

## 示例输出

**场景：** *PD 主题：“在全校推行提取练习——帮助教师理解提取练习为什么有效、如何高效使用，以及如何在不增加工作量的前提下将其嵌入现有常规” / 受众：“全体45名教师，跨学科（一贯制学校的小学与中学部），教龄从新教师到25年不等。教职工总体积极但时间紧缺，且对‘又一项新举措’持怀疑态度。” / 时长：“90分钟，放学后 INSET 培训” / 学校情境：“学校改进计划将‘提高知识的长期记忆保持’列为重点。教职工听说过提取练习，但极少有人系统使用。”*

---

## 专业发展课程：提取练习——从研究走向你的课堂

**主题：** 理解并实施提取练习
**受众：** 45名教师，跨学科与不同教龄，一贯制学校
**时长：** 90分钟

### 课程概览

教师将先以学习者身份亲身体验提取练习（从而理解它**感觉**如何），审视其起效的证据（从而理解**机制**而非仅仅是方法），并为自己所教的一个班级设计具体的提取常规（从而带着**计划**而非空泛意图离开）。本场培训围绕“提取练习应增加学习效果而不增加工作量”这一原则设计——所设计的每项常规均应耗时少于5分钟课堂时间且仅需极少备课准备。

### 课程计划

**0:00–0:10 — 亲身体验（10分钟）**
- **引导者做什么：** “在我告诉你们任何关于提取练习的内容之前，我想请你们先体验一下。拿出一张白纸。写下你们能记住的上一次全校 CPD 培训的所有内容——主题、核心观点、任何细节。你们有3分钟。开始。”
- **教师做什么：** 头脑倾倒3分钟（大多数人记得很少，这**正是**重点）。接着转向邻座同伴对比：你们记住了一样的东西吗？不一样的东西？各自记住了多少？
- **目的：** 这本身**就是**提取练习——并且它直观展示了问题所在（我们在 CPD 培训中听到的绝大多数内容都会遗忘）。它也创造了学习动机：“如果我们连上个月的培训都几乎记不住，想象一下学生从我们的课上能留住多少。”体验创造了后续内容的需求。
- **所需资源：** 白纸，无需其他任何物品。

**0:10–0:20 — 为什么有效（10分钟）**
- **引导者做什么：** 简短（最多10分钟）呈现证据：Roediger & Butler（2011）、测试效应、Bjork 的合意困难。核心信息：从记忆中提取信息会**强化**记忆痕迹——它不仅是评估，更是一种学习策略。两张关键幻灯片：（1）遗忘曲线——展示不经提取我们遗忘得多快；（2）对比重读与提取练习长期保持率的图表。
- **教师做什么：** 倾听（这是 20% 引导者讲授部分）。但要**积极地听**：每个核心要点之后，引导者就刚刚讲过的内容提一个提取问题。“不看幻灯片——什么是测试效应？”这在实时中示范了该技术。
- **目的：** 教师需要先理解“为什么（WHY）”，才愿意投入“怎么做（HOW）”。但讲授必须**短**——10分钟，而非40分钟。
- **所需资源：** 幻灯片（最多6页）、附带核心参考文献的讲义。

**0:20–0:40 — 探索技术（20分钟）**
- **引导者做什么：** 介绍5种低工作量提取技术，每种印在一张卡片上：（1）头脑倾倒（Brain dump），（2）提取网格（Retrieval grid），（3）上节课/上周/上个月（Last lesson/last week/last month），（4）低风险小测（无需科技设备），（5）精致化询问（“为什么这是真的？”）。
- **教师做什么：** 按同学科 4–5 人分组，审视全部5张技术卡片。针对每一项：讨论它在**你的学科**中如何运作。为每项技术标记：“立即可轻松实施” / “需要适配” / “不适合我的学科”。各组向全场分享他们的前2名首选技术。
- **目的：** 教师对照自身实践评估技术——不是“哪个最好？”，而是“哪个对我有效？”。选择权创造归属感。同学科分组确保讨论切合实际（提取网格在数学与英语中的用法截然不同）。
- **所需资源：** 技术卡片（每桌一套5张，含说明与示例）、小组记录用大白纸。

**0:40–1:05 — 设计你的常规（25分钟）**
- **引导者做什么：** “现在你们要为自己的一个班级规划具体的提取常规。不是‘我找时间试试提取练习’——而是一份回答以下问题的具体常规：哪个班、哪节课、哪种技术、多久一次、耗时多长。”发放规划模板。
- **教师做什么：** 独立填写规划模板：
  - **班级：**（例如：九年级地理，周二第3节）
  - **技术：**（例如：“上节课 / 上周 / 上个月”——每节课开头3道题）
  - **频率：**（例如：接下来3周每节课）
  - **所需时间：**（例如：课前5分钟）
  - **第一组题目：**（现在就写出来——离开时就带着明天能直接用的题目）

  15分钟个人规划后，与同事结对分享：“这是我的计划。它行得通吗？可能会出什么问题？”
- **目的：** 这是最重要的阶段。教师离开时带着一份**计划**，而不仅仅是一个概念。他们已经写好了第一组题目——明天就开始的障碍已被移除。
- **所需资源：** 规划模板（每位教师一份）、笔。

**1:05–1:15 — 承诺与跟进（10分钟）**
- **引导者做什么：** “在一张便利贴上写下：你的名字、你的班级、你的技术以及你开始的日期。离开时贴在展板上。三周后，我会跟大家了解进展——不是为了评判，而是为了了解什么有效以及什么需要调整。”
- **教师做什么：** 写下自己的承诺，与邻座分享（“我打算做 X——你呢？”），并公开贴上便利贴。
- **目的：** 公开承诺提高跟进率（Cialdini, 2006）。三周后的回访提供了不带监视感的问责。“不是为了评判而是为了学习”的框架减轻了焦虑。
- **所需资源：** 便利贴、展示板。

### 主动学习任务

**任务 1——开场头脑倾倒：** 教师以学习者身份体验提取练习。仅耗时3分钟，却定下了整场基调：“我们在亲身实践，而不仅仅是空谈。”

**任务 2——技术评估：** 同学科小组对照自身实践评估5种技术。这是20分钟的积极讨论，教师就“什么对自己的学科与情境有效”做出专业判断。

**任务 3——规划模板：** 每位教师设计一份具体的提取常规并写好题目。这就是“一场挺有意思的培训”与“我明天就开始用”之间的区别。

### 实践应用

每位教师离开时带走：
1. 一份明确了班级、技术、频率与时间安排的完整规划模板
2. 第一组可直接使用的提取练习题
3. 一项明确何时开始的公开承诺（便利贴）

### 后续跟进计划

**第1周：** 引导者发送简短邮件：“你们这周开始了提取常规——进展如何？请用一句话回复：什么有效，什么比较棘手。”

**第3周：** 在下一次全校教职工会议上安排15分钟时段。三名教师分享他们的经验（一名小学、一名中学、一名遇到挑战的教师）。结构化发言：“我试了什么、发生了什么、我学到了什么。”这是同伴学习，而非表演。

**半学期末：** 可选的“提取练习答疑工作坊”——30分钟，面向希望进一步发展实践、尝试新技术或共同解决难点的教师。提供引导，非强制参加。

**下一次全校 INSET：** 20分钟重温——针对提取练习本身的提取练习。“不看上次的笔记，写下你学到的关于提取练习的三件最重要的事。”元示范：用这项技术来巩固关于这项技术本身的学习。

### 引导者笔记

1. **最大的风险是讲得太多。** 如果你发现自己连续讲授超过10分钟，立刻停下。教师正在脱离投入——你正在示范与你所教内容截然相反的东西（被动接收 vs. 主动提取）。信任活动本身。

2. **用证据而非热情应对怀疑。** 如果有教师说“这不过是又一阵风”，不要反驳打压：“这是一个很合理的关切。以下是证据：测试效应在过去40年的100多项研究中得到了复现。它不是新潮噱头——它是认知科学中最稳健的发现之一。什么能让你对尝试它更有信心？”

3. **部分教师已经在用提取练习了。** 赞赏这一点。请他们分享自己的做法——同伴经验比引导者经验更有说服力。“谁已经在做类似的事情了？跟我们说说。”

4. **便利贴墙至关重要。** 切勿跳过。公开承诺显著提高落实率。而且这面墙本身会成为一个可见的成果：“45位教师承诺本周尝试提取练习。”

---

## 已知局限

1. **单场培训无法维持持久改变。** Timperley 等人（2007）态度明确：一次性 PD 无法改变实践。本场培训旨在作为持续聚焦的**起点**——而非孤立事件。没有后续跟进计划，本场培训只会产出与其他所有 INSET 培训相同的结果：起初的热情随后逐渐退回原有实践。

2. **本设计预设了引导者具备基本能力。** 方案提供了结构，但实际引导——管理群体动态、应对抵触、校准节奏、回应提问——需要技巧。像念剧本一样照读方案的引导者，无法产出与理解原则并能随机应变的引导者同等的成效。

3. **学校文化影响 PD 成效。** 在信任度低、问责压力高或存在“举措疲劳”历史的学校里，即便设计精良的 PD 也会遭遇阻力。本课程设计已对此有所应对（从经验出发、提供选择、尊重时间），但它无法完全弥补有毒的专业文化。学校领导层必须为专业学习的蓬勃发展创造条件。
