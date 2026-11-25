---
# AGENT SKILLS STANDARD FIELDS (v2)
name: lesson-study-cycle-designer
description: "设计从研究问题经由协同备课到研究课的完整课例研究循环。适用于规划课例研究（jugyou kenkyuu）或教师对教学实践的协同探究。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "professional-learning/lesson-study-cycle-designer"
skill_name: "课例研究循环设计器"
domain: "professional-learning"
version: "1.0"
evidence_strength: "strong"
evidence_sources:
  - "Stigler & Hiebert (1999) — The Teaching Gap: best ideas from the world's teachers for improving education in the classroom"
  - "Lewis, Perry & Murata (2006) — How should research contribute to instructional improvement? The case of lesson study"
  - "Dudley (2014) — Lesson Study: a handbook"
  - "Takahashi & McDougal (2016) — Collaborative lesson research: maximizing the impact of lesson study"
  - "Fernandez & Yoshida (2004) — Lesson Study: a Japanese approach to improving mathematics teaching and learning"
input_schema:
  required:
    - field: "teaching_challenge"
      type: "string"
      description: "本次课例研究将调查的具体教学难题或学生学习困难"
    - field: "subject_and_topic"
      type: "string"
      description: "研究课的学科、主题与年级"
    - field: "team_composition"
      type: "string"
      description: "课例研究小组成员——教师人数、教龄经验、学科背景"
  optional:
    - field: "student_level"
      type: "string"
      description: "学生的年龄/年级"
    - field: "available_time"
      type: "string"
      description: "团队拥有多少时间——会议次数、可用的脱产教研时间"
    - field: "previous_lesson_study"
      type: "string"
      description: "团队此前是否开展过课例研究"
    - field: "school_context"
      type: "string"
      description: "学校相关特征——学段、生源背景、改进重点"
    - field: "case_students"
      type: "string"
      description: "将作为观察焦点的3名“个案学生”——他们的画像"
output_schema:
  type: "object"
  fields:
    - field: "research_theme"
      type: "string"
      description: "课例研究调查的统领性问题"
    - field: "cycle_plan"
      type: "object"
      description: "完整的课例研究循环——规划、授课、观察、反思、修订"
    - field: "research_lesson_plan"
      type: "object"
      description: "专为协同观察设计的详尽研究课教案"
    - field: "observation_protocol"
      type: "object"
      description: "观察者应关注什么、如何记录观察以及如何组织课后研讨"
chains_well_with:
  - "instructional-coaching-conversation-guide"
  - "lesson-observation-protocol-designer"
  - "reflective-practice-prompt-generator"
  - "teacher-inquiry-cycle-designer"
  - "pedagogical-content-knowledge-developer"
teacher_time: "5 分钟"
tags: ["lesson-study", "jugyou-kenkyuu", "collaborative-planning", "research-lesson", "professional-learning"]
---

# 课例研究循环设计器

## 本技能的功能

设计完整的课例研究（Lesson Study）循环——这一源自日本（jugyō kenkyū，授业研究）的结构化协同过程：由教师团队共同设计一节“研究课”，由其中一名教师执教，其余教师观察**学生学习**（而非教师表现），随后团队共同分析学生实际学到了什么以及为什么。核心原则在于：课例研究是对**教学的研究（research INTO teaching）**，而非对**教师的评价（evaluation OF teachers）**——这节课属于整个团队，焦点在于学生学习（而非教师行为），目的是发展关于学生如何学习特定内容的共享专业知识。产出包括研究主题、带会议议程的循环计划、专为协同观察设计的研究课教案，以及聚焦个案学生的观察规程。AI 在此处具有独特价值，因为设计有效的课例研究循环需要同时理解日本原型模式（强调 *kyōzai kenkyū* 教材研究——对学科内容与课程的深入研习）以及非日本学校环境的现实约束（脱产教研时间、团队稳定性与课例研究经验可能有限）。

## 循证基础

Stigler 与 Hiebert（1999）通过《The Teaching Gap》将课例研究引入西方视野，表明日本教师通过规划、观察与分析研究课的协同循环持续改进实践。他们指出，课例研究的力量不在于单节课本身，而在于协同过程：教师发展出关于学生如何学习的共享专业知识，这些知识历经多年积累并传递给新教师。Lewis、Perry 与 Murata（2006）确定了课例研究改进教学的四条路径：增进学科知识、增进教学知识、提升观察学生的能力，以及更紧密的同事网络。Dudley（2014）为英国学校改编了课例研究，引入“个案学生（case students）”概念——精心挑选三名学生（一名高学业成就、一名中等、一名较低成就）作为观察焦点，使学生学习变得可见且易于追踪。Takahashi 与 McDougal（2016）强调，课例研究中最重要（也最常被跳过）的阶段是 *kyōzai kenkyū*——在备课之前对学科内容、课程与现有研究的深入研习。没有这一步，课例研究就沦为缺乏研究基础的普通集体备课。Fernandez 与 Yoshida（2004）记录了完整的日本课例研究流程，表明单次循环通常跨越数周包含 3–5 次会议，研究课本身只是更深层过程中的一个组成部分。

## 输入模式

教师必须提供：
- **教学挑战：** 待调查的问题。*例如：“学生能计算简单图形的面积，但无法将其应用于组合图形——他们看不出如何把组合图形拆分为更简单的图形” / “学生能识别文本中的语言特征，但无法解释其对读者的效果” / “七年级学生在科学课上难以写出充分展开的解释——他们能提出主张，但不用证据或推理来支撑”*
- **学科与主题：** 研究课涵盖的内容。*例如：“八年级数学——组合图形的面积” / “九年级英语——分析诗歌中的语言” / “七年级科学——撰写 CER（主张-证据-推理）解释”*
- **团队构成：** 谁参与其中。*例如：“3名数学教师，经验混合——1名新教师、1名5年教龄、1名教研组长” / “同一教研组的4名英语教师，均有丰富经验”*

可选（如有，由上下文引擎注入）：
- **学生水平：** 年级
- **可用时间：** 会议与脱产时间
- **既往课例研究经验：** 团队对该流程的经验
- **学校情境：** 学段、生源背景、改进重点
- **个案学生：** 3名焦点学生

## 提示词

```
You are an expert in lesson study (jugyō kenkyū), with deep knowledge of Stigler & Hiebert's (1999) analysis of Japanese lesson study, Dudley's (2014) UK adaptation, Lewis, Perry & Murata's (2006) pathways of improvement, and Takahashi & McDougal's (2016) emphasis on kyōzai kenkyū (deep study of subject matter and curriculum). You understand that lesson study is fundamentally different from lesson observation: it is collaborative research INTO teaching and learning, not evaluation OF a teacher.

CRITICAL PRINCIPLES:
- The lesson belongs to the GROUP, not the individual who teaches it. The research lesson is "our lesson," not "my lesson being watched."
- Observers watch STUDENTS, not the teacher. The question is "What did students learn and how?" not "How well did the teacher perform?"
- The most important phase is the pre-lesson study of subject matter and curriculum (kyōzai kenkyū), not the lesson itself.
- Case students (Dudley, 2014) make observation manageable: observers track 3 specific students to understand how different learners experience the lesson.

Your task is to design a lesson study cycle for:

**Teaching challenge:** {{teaching_challenge}}
**Subject and topic:** {{subject_and_topic}}
**Team composition:** {{team_composition}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Student level:** {{student_level}} — if not provided, infer from the subject and topic.
**Available time:** {{available_time}} — if not provided, design for 4 meetings (realistic minimum) with one observation lesson.
**Previous lesson study:** {{previous_lesson_study}} — if not provided, assume the team is new to lesson study and include orientation.
**School context:** {{school_context}} — if not provided, design for general school application.
**Case students:** {{case_students}} — if not provided, guide the team in selecting their own case students.

Design the complete cycle:

1. **Meeting 1 — Research and goal-setting (kyōzai kenkyū):**
   - Define the research theme: what question about student learning are we investigating?
   - Study the subject matter: what does the curriculum say? What does the research say about how students learn this content? What are the known misconceptions?
   - Study existing approaches: how is this typically taught? What has worked and what hasn't?
   - Select case students: one high-attaining, one middle, one who typically struggles with this content. What do we predict each will find easy/difficult?

2. **Meeting 2 — Collaborative lesson planning:**
   - Design the research lesson collaboratively — every team member contributes.
   - The lesson plan must be unusually detailed: anticipated student responses at each stage, what the teacher will do if students respond in different ways, where the key learning moments are.
   - Design the observation schedule: who watches which case student? What are they looking for?

3. **Meeting 3 — The research lesson and post-lesson discussion:**
   - One team member teaches; others observe.
   - Observers sit near their assigned case student(s) and record: what the student does, says, writes, and appears to be thinking.
   - Post-lesson discussion (immediately after, 45–60 minutes): what did we learn about how students learn this content? Not "what could the teacher have done better" but "what did we observe about student learning?"

4. **Meeting 4 — Analysis and knowledge-building:**
   - What did we learn from this cycle?
   - What would we change if we taught this lesson again?
   - What implications does this have for our broader teaching of this topic/subject?
   - How do we share what we learned with colleagues who weren't in the team?

Return your output in this exact format:

## Lesson Study Cycle: [Research Theme]

**Teaching challenge:** [The problem being investigated]
**Subject and topic:** [What the research lesson covers]
**Team:** [Who is involved]

### Research Theme

[The overarching question the lesson study investigates — framed as a question about student learning]

### Cycle Plan

For each meeting:
**Meeting [N]: [Purpose] — [Suggested timing]**
- **Agenda:** [What the team does in this meeting]
- **Preparation needed:** [What team members should do before the meeting]
- **Key output:** [What the meeting produces]

### Research Lesson Plan

[A detailed lesson plan designed for collaborative observation — including anticipated student responses and observation focus points]

### Observation Protocol

**Case Student A (higher-attaining):** [What to watch for]
**Case Student B (middle-attaining):** [What to watch for]
**Case Student C (typically struggles):** [What to watch for]

**Recording format:** [How observers should record what they see]

### Post-Lesson Discussion Guide

[Structured questions for the post-lesson discussion — focused on student learning, not teacher evaluation]

**Self-check before returning output:** Verify that (a) the focus is on student learning, not teacher performance, (b) kyōzai kenkyū is included, (c) case students are specified, (d) the research lesson plan includes anticipated student responses, (e) the observation protocol is student-focused, and (f) the post-lesson discussion guide avoids evaluative language about the teacher.
```

## 示例输出

**场景：** *教学挑战：“八年级学生能计算简单图形（长方形、三角形）的面积，但在组合图形上吃力。他们看不出如何把组合图形拆分成更简单的图形——他们试图套用单一公式或干脆瞎猜。” / 学科与主题：“八年级数学——组合图形的面积” / 团队构成：“3名数学教师——1名新教师（第一年）、1名经验教师（8年）、1名教研组长（15年）。以前均未开展过课例研究。” / 可用时间：“3周内4次一小时会议，外加研究课本身”*

---

## 课例研究循环：学生如何学会拆分组合图形？

**教学挑战：** 学生能求简单图形面积，但不会将组合图形拆分为组成部分
**学科与主题：** 八年级数学——组合图形的面积
**团队：** 3名数学教师（新教师、经验教师、教研组长），初次接触课例研究

### 研究主题

**八年级学生是如何发展出将组合图形拆分为更简单图形以计算面积的能力的——又是什么阻碍了他们独立做到这一点？**

子问题：
- 学生在课上的哪个节点“看见”了拆分？是什么触发了这一洞察？
- **不会**拆分图形的学生转而做了什么？他们尝试了哪些替代策略？
- 提前画出拆分辅助线是帮助学生学会了这项技能，还是绕过了学习？

### 循环计划

**第1次会议：研究与目标设定（教材研究 *kyōzai kenkyū*）——第1周，1小时**
- **议程：**
  1. 课例研究入门引导（15分钟）：教研组长说明流程。核心信息：这节课属于我们所有人；我们观察学生，而非教师；这是研究，而非考核。分发 Dudley（2014）的单页摘要。
  2. *Kyōzai kenkyū*——研习内容（25分钟）：团队一起做5道难度递增的组合图形题。留意：需要哪些数学知识？**我们自己**在哪里必须认真思考？团队在设计课程前应先像学习者一样体验数学。审阅八年级教学进度表：在这节课之前学生学过什么？之后学什么？
  3. 讨论已知困难（10分钟）：关于学生在这块如何吃力，我们知道什么？汇集经验：“学生看到组合图形时通常会做什么？”记录已知误解与难点。
  4. 挑选个案学生（10分钟）：从将要授课的班级中选出三名学生：学生 A（面积计算自信，可能较易掌握拆分）、学生 B（简单图形胜任，代表典型学生）、学生 C（在简单图形面积上吃力——面对组合图形可能不堪重负）。为每人写一份简要画像：预测他们各自觉得什么容易、什么困难。
- **会前准备：** 每位团队成员从自己的教学资源中带来 2–3 道组合图形题。执教研究课的教师提供附带简要学业成绩数据的班级名单。
- **核心产出：** 商定研究主题、选定个案学生、记录已知难点。

**第2次会议：协同备课——第1或第2周，1小时**
- **议程：**
  1. 重温研究主题与个案学生（5分钟）。
  2. 协同设计研究课（45分钟）：逐阶段构建教案。针对每个阶段，团队必须明确：教师做什么、学生做什么、我们预期每位个案学生会做什么，以及如果出现预期回应教师该如何应对。教案应比平时更详尽——因为它是为观察而设计的，每个瞬间都至关重要。
  3. 设计观察分工表（10分钟）：为每位观察者分配一名个案学生。制作简易记录单：包含三栏的表格——时间、学生做什么/说什么、这说明了他们怎样的理解。
- **会前准备：** 执教教师带来一份课程结构初稿。其他成员带来任务与资源构想。
- **核心产出：** 包含预期学生回应的完整研究课教案；明确观察分工。

**第3次会议：研究课与课后研讨——第2或第3周，授课时间 + 1小时**
- **研究课（50分钟）：** 一名教师执教（在第2次会议上商定——通常是自愿者，而非刻意选最资深或最年轻的）。其余两名教师观察。每位观察者坐在各自负责的个案学生附近，手持记录单。观察者**绝不**帮助学生、介入教学或与班级互动。他们只观察和记录。
- **课后研讨（紧接着课后进行，1小时）：**
  1. 执教教师首先发言（5分钟）：“我自己感觉这节课怎么样？我注意到了什么？”这体现对执教者的尊重，并让他们在听到反馈前先梳理感受。
  2. 每位观察者汇报自己的个案学生（共15分钟）：“以下是学生 A/B/C 在每个阶段所做的事。以下是我认为这说明了关于他们学习的什么。”基于证据——观察到了什么，而非主观臆断。
  3. 围绕研究主题展开讨论（25分钟）：“关于学生如何学会拆分组合图形，我们学到了什么？这节课在培养该技能上成功了吗？有什么令我们惊讶的地方？我们会改什么以及为什么？”
  4. 教学启示（15分钟）：“这对我们今后如何教授本主题意味着什么？我们学到了哪些超越这一节课的通用经验？”
- **核心产出：** 观察笔记、课后研讨纪要、教学启示清单。

**第4次会议：分析与知识建构——第3周，1小时**
- **议程：**
  1. 审阅课后研讨纪要（10分钟）：我们得出了什么结论？
  2. 修订教案（20分钟）：如果再教一次这节课，我们会改什么？写出一份修订版教案——这不是为了让原执教者“做得更好”，而是团队的集体理解改进了这节课。
  3. 提炼可迁移知识（15分钟）：关于学生如何学习组合图形面积，我们学到了哪些可应用于其他主题的规律？（例如：“必须先给学生**没有**拆分辅助线的组合图形——过早展示辅助线会绕过思考。这一原则可能同样适用于其他多步骤问题。”）
  4. 规划分享（15分钟）：如何将所学分享给未参与小组的同事？在教研组会上做简短汇报？一份单页摘要？执教修订版课程供其他教师观摩？
- **核心产出：** 修订版教案、可迁移洞察、分享计划。

### 研究课教案

**课题：拆分组合图形以计算面积**
**时长：50分钟**

**第一阶段——激活先验知识（8分钟）：**
展示三个标有尺寸的简单图形（长方形、三角形、平行四边形）。学生在迷你小白板上计算每个图形的面积。“3，2，1，亮板。”
- *预期：学生 A 迅速全对。学生 B 算对长方形和三角形，在平行四边形上可能犹豫。学生 C 可能在三角形公式上卡壳。*
- *观察焦点：学生 C 记得面积公式吗？如果不记得，组合图形任务将无法企及——教师可能需要提供公式参考卡。*

**第二阶段——未经讲授的问题挑战（12分钟）：**
展示一个标有尺寸的组合 L 形，**不带任何拆分辅助线**。“求这个图形的面积。你可以用任何喜欢的方法。先独立思考3分钟，再与同伴对比。”
- *预期：学生 A 可能立刻或略作思考后看出拆分方式。学生 B 很可能会尝试找一个单一公式，意识到行不通，然后要么卡住要么尝试切分图形。学生 C 可能感到不知所措而无法下笔。*
- ***这是核心观察时刻。** 在被展示拆分方法之前，学生尝试了什么策略？精确记录每位个案学生在这3分钟内所做的一切。*
- *教师招式：**切勿**提前展示拆分。静默巡视。如果学生 C 在2分钟后完全卡住，轻声提示：“你能把这个图形切分成你已经认识的图形吗？”——这是轻推，而非答案。*

**第三阶段——分享策略（8分钟）：**
“谁找到了算出它的方法？上来展示给我们看。”挑选学生分享——优先选择采用不同拆分方式的学生（横向切分 vs. 纵向切分 vs. 补全大长方形相减法）。如果没人拆分出来，教师示范：“如果我在这里画一条线会怎样？我得到了什么图形？”
- *预期：多种拆分策略将会涌现。讨论：它们算出的答案一样吗？哪种最简单？为什么？*
- *观察焦点：当学生 B 看到同伴的策略时，他的理解是否发生了变化？当展示策略时，学生 C 是理解了策略，还是仅仅照抄步骤？*

**第四阶段——新图形的有指导练习（12分钟）：**
三个难度递增的组合图形。学生结对合作。针对每个图形：第一步，先画出拆分辅助线（暂不计算）。教师巡视，在学生计算前先检查拆分。
- *预期：学生 A 会觉得拆分很直接。学生 B 能搞定图形1和2，但在图形3（有多种拆分方式）上可能吃力。学生 C 也许能照搬方法拆分图形1，但迁移到图形2时卡壳。*
- *观察焦点：学生 C 是在独立拆分，还是在抄袭同伴？这是研究主题的关键证据——这名学生能**看见**拆分，还是在遵循一个自己并不理解的程序？*

**第五阶段——独立应用（8分钟）：**
最后一道组合图形题，独立完成。不讨论、无同伴协助。这是诊断性检验：每位学生能否独立拆分并计算？
- *观察焦点：每位个案学生独立产出了什么？将其与第二阶段（讲授前）的产出对比——发生了什么变化？*

**第六阶段——反思（2分钟）：**
“写一句话：求任何图形（哪怕很复杂）面积的窍门是什么？”
- *预期：优秀的回答会说类似“把它拆成你已经知道怎么算的图形”。较弱的回答会说“套公式”（说明他们尚未抓住“拆分”这一核心策略）。*

### 观察规程

**个案学生 A（高学业成就）：** 观察：在第二阶段多快看出拆分。他们使用的是拆分还是另一种策略（如把图形补成一个大长方形再做减法）？在第四阶段，他们是否找到了**多种**拆分法？在第五阶段，他们拆分得是否流利？

**个案学生 B（中等学业成就）：** 观察：他们在第二阶段（讲授前尝试）**最先**尝试了什么。是卡住、套单一公式还是瞎猜？在第三阶段，是什么引发了“顿悟”时刻——看到同伴的方法还是教师的示范？在第四阶段，他们能否迁移到新图形，还是只照搬第三阶段的方法？

**个案学生 C（通常吃力）：** 观察：在第二阶段他们能否切入任务？如果不能，他们做了什么（干等、抄袭、瞎猜、求助）？在第三阶段讲授之后，他们是理解了拆分还是只照着步骤做？在第五阶段，他们能独立完成吗？这名学生的体验最能告诉我们这节课是否真正成功。

**记录格式：**
| 时间/阶段 | 学生做什么/说什么/写什么 | 这说明了他们怎样的理解 |
|---|---|---|

### 课后研讨指南

**第一轮——执教者的声音（5分钟）：**
“在听观察者汇报之前，[教师姓名]：你自己感觉这节课怎么样？你注意到了什么？”

**第二轮——个案学生汇报（15分钟）：**
“观察者1：跟我们说说学生 A——你在每个阶段观察到了什么？”
“观察者2：跟我们说说学生 B……”
“观察者3：跟我们说说学生 C……”
（只谈证据——所见所闻，不对执教教师做评判。）

**第三轮——研究主题讨论（25分钟）：**
- “在课上的哪个节点学生‘看见’了拆分？是什么触发的？”
- “不会拆分的学生转而做了什么？他们尝试了哪些替代策略？”
- “第三阶段教师的示范是帮助学生 C 理解了拆分，还是他只是照抄了步骤？”
- “第二阶段（未经讲授的问题挑战）有价值吗？在展示方法前先经历挣扎是促进还是阻碍了学习？”
- “有什么让我们感到惊讶的？”

**第四轮——教学启示（15分钟）：**
- “如果我们再教一次这节课，我们会改变哪**一件事**以及为什么？”
- “关于学生如何学习拆分图形，我们学到了哪些适用于更广泛教学的规律？”
- “我们还有哪些未解的问题？”

**重要：研讨规范。** 在任何时刻，讨论都不应变成针对教师个人的“你本该……”或“如果你当时……就好了”。所有评论都围绕**这节课**（属于整个团队）和**学生学习**（研究焦点）。建议使用的句式开头：“我注意到学生 B……” / “这节课似乎……” / “下次，**我们**可以试试……”

---

## 已知局限

1. **课例研究需要受保护的教研时间。** 四次一小时会议外加听课时间是一笔不小的投入。在没有专门专业学习时间的学校里，课例研究极难持续。上述循环代表最低配置——日本课例研究循环往往跨越数月。学校必须明确分配时间，而非指望教师自己挤时间。

2. **课例研究需要信任文化。** 被同事观摩是令人感到脆弱的。如果学校文化偏向考核评判（听课意味着打分而非学习），教师就不会有足够的安全感开展真正的课例研究。引导者（通常是团队中最资深的成员）必须积极捍卫研讨规范：研究，而非评价。

3. **课例研究积累知识的速度较慢。** 单次循环产出的洞察有限。课例研究的力量在于累积效应——历经数年的重复循环建立起关于学生如何学习的深厚专业知识。学校应承诺将课例研究作为持续实践，而非一次性活动。
