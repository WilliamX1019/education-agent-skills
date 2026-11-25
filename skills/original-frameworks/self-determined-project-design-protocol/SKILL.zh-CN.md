---
# AGENT SKILLS STANDARD FIELDS (v2)
name: self-determined-project-design-protocol
description: "为学生的自主决定项目构建包含导师检查点、能力对齐与反思的完整规程。适用于在基于能力的框架内指导学生主导的项目。"
disable-model-invocation: true
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "original-frameworks/self-determined-project-design-protocol"
skill_name: "自主决定项目设计规程"
domain: "original-frameworks"
version: "1.0"
evidence_strength: "emerging"
evidence_sources:
  - "Manning — Personal project mentoring methodology (original, developed through capstone mentoring and international teaching)"
  - "Zimmerman (2000, 2002) — Self-regulated learning: forethought, performance, self-reflection phases"
  - "Bandura (1997) — Self-efficacy: the exercise of control (feasibility calibration as self-efficacy assessment)"
  - "Ericsson & Pool (2016) — Peak: secrets from the new science of expertise (knowledge/skill acquisition as deliberate practice)"
  - "Black & Wiliam (1998) — Assessment and classroom learning (milestone checkpoints as formative assessment)"
  - "Manning — LT authoring methodology and rubric logic (Domain 14 Skills 98 and 99)"
input_schema:
  required:
    - field: "student_idea"
      type: "string"
      description: "学生的初步项目构想——无论多么粗糙"
    - field: "student_level"
      type: "string"
      description: "发展阶段与年龄"
    - field: "available_time"
      type: "string"
      description: "总时长与每周投入时间"
  optional:
    - field: "existing_curriculum_LTs"
      type: "string"
      description: "该领域是否已有课程学习目标（LT）或需要新建"
    - field: "mentor_expertise"
      type: "string"
      description: "教育者对该项目领域的了解程度"
    - field: "prior_experience"
      type: "string"
      description: "学生在该领域已经做过什么"
output_schema:
  type: "object"
  fields:
    - field: "phase_1_ideation_and_feasibility"
      type: "object"
      description: "学生行动 + 教育者行动——构想阐述、可行性现实核查、必要时的可能性拓展"
    - field: "phase_2_knowledge_gap_analysis"
      type: "object"
      description: "学生与教育者的并行研究——需要什么、学生知道什么、不知道什么、诚实的准备度评估"
    - field: "phase_3_planning"
      type: "object"
      description: "LT 选择或创建、范例分析、量规开发、知识/技能习得计划、带里程碑的时间线、资源与导师识别、追踪系统搭建"
    - field: "phase_4_execution_and_monitoring"
      type: "object"
      description: "每周节奏、自我监控规程、里程碑检查点、适应性重规划"
    - field: "phase_5_completion_and_defence"
      type: "object"
      description: "对照量规的最终自我评估、展示或答辩、诚实的影响评估"
    - field: "tracking_system"
      type: "object"
      description: "学生与导师随时可见的共享可视化载体的规格说明——文档、看板或电子表格。必须显示：计划、时间线、对照里程碑的当前状态以及进展证据。工具中立，但功能要求不可妥协"
    - field: "educator_feasibility_calibration_guide"
      type: "object"
      description: "判断真实准备度的具体问题——学生应能解释什么，以及尚未就绪时该怎么办"
    - field: "known_limitations"
      type: "object"
      description: "规程要求教育者触及自身专长之外的地方；何时引入外部导师"
chains_well_with:
  - "learning-target-authoring-guide"
  - "coherent-rubric-logic-builder"
  - "developmental-band-system-designer"
  - "self-regulated-learning-designer"
  - "curriculum-knowledge-architecture-designer"
teacher_time: "6 分钟"
tags: ["self-determined", "project", "Manning", "mentoring", "SRL", "Zimmerman", "Bandura", "feasibility", "deliberate-practice", "tracking"]
---

# 自主决定项目设计规程

## 本技能的功能

本技能编码了由教育者、课程设计师及学习系统设计师 Gareth Manning 开发的原创实践者框架。与其他领域的技能不同，它并非源自同行评审研究传统，而是植根于对学习科学的深入研习、原创课程设计工作以及一线课堂测试。将其纳入本库，是因为该方法论逻辑连贯、可迁移且真正实用——同时出于学术诚实，需将实践者框架与经研究验证的方法加以区分。

本技能引导学生与教育者共同走完设计、规划并执行一个自主决定个人项目的完整弧线——从初步构想一直到完成、答辩与反思。它明确规定了**双方**在每个阶段需要做什么、如何诚实地校准雄心，以及如何在项目本身之外并行构建知识与技能习得计划。产出是一份完整的双视角规程：面向学生的路线图与面向教育者的指导指南，逐阶段展开。该规程直接对应 Zimmerman（2000, 2002）的自我调节学习三阶段：前瞻（第1–3阶段）、表现（第4阶段）与自我反思（第5阶段）。Bandura（1997）支撑了可行性校准：过度雄心与过低雄心都反映了自我效能感的校准失衡，教育者的角色是帮助学生诚实校准，同时不扼杀能动性。Ericsson 与 Pool（2016）支撑了知识/技能习得计划：学生为项目需要发展的技能构成了一个刻意练习的设计问题。追踪系统——一个学生与导师随时都能看见的共享可视化载体——是本规程的结构脊梁。没有它，指导对话就缺乏共同参照点，项目偏航也会直到为时已晚才被察觉。

## 循证基础

Manning 在多个国际学校情境的个人项目指导中开发了这一规程，最近一次是在布达佩斯 REAL School 的毕业顶石（capstone）项目中。该方法论旨在解决一个具体难题：大多数“独立项目”赋予了学生自由却没有给予结构——结果要么沦为并非真正自主的教师主导项目，要么沦为因学生缺乏过程管理所需的自我调节技能而漂移、停滞或崩盘的学生主导项目。Zimmerman（2000, 2002）为规程的阶段结构提供了理论框架。他的自我调节学习模型描述了三个循环阶段：前瞻（目标设定、策略规划、自我效能感评估）、表现（自我监控、策略使用、求助）与自我反思（自我评价、归因、适应性回应）。本规程将这些阶段操作化：第1–3阶段**就是**前瞻，第4阶段**就是**表现，第5阶段**就是**自我反思。Bandura（1997）支撑了可行性校准——规程中最关键也最常被跳过的环节。自我效能感（学生对自己成功能力的信念）直接预测努力程度、坚持性与韧性。但自我效能感可能校准失衡：一个毫无编程经验却相信自己能在6周内做出一款应用的学生，拥有膨胀的自我效能感，这会导致令人沮丧的失败。同样，一个说“我做不出任何有趣东西”的学生，拥有萎缩的自我效能感，这会导致平庸无奇的项目。教育者的角色是诚实校准：探查学生真正知道什么、需要学什么以及时间线是否现实。过度雄心与过低雄心在伤害程度上是相等的——在一个尚未准备好的项目上失败的学生会学到错误的教训。Ericsson 与 Pool（2016）支撑了知识/技能习得计划。学生项目所需的技能——编程、木工、研究方法、写作、设计——不会凭空习得，它们需要刻意、结构化的练习。本规程在项目计划旁并行构建技能习得计划：你需要学什么、如何学以及如何知道自己已经学会？Black 与 Wiliam（1998）支撑了里程碑检查点设计：每个检查点都是一个结构化的形成性评估时刻，学生对照量规自评、分享进展证据、获得反馈并调整计划。

## 输入模式

教育者必须提供：
- **学生构想：** 初步项目构想。*例如：“我想为妈妈的面包店做一个网站” / “我想写并绘制一本关于气候变化的儿童绘本” / “我想设计并建造一座能承重50公斤的模型桥” / “我想学吉他并在学校音乐会上演出” / “我不知道我想做什么”*
- **学生水平：** 发展阶段与年龄。*例如：“D阶段，13岁” / “C阶段，11岁” / “B阶段，9岁”*
- **可用时间：** 总时长与每周投入。*例如：“一学期（18周），每周3小时专门项目时间外加独立作业” / “一学季（10周），每周2小时” / “全年，每周90分钟”*

可选（如有，由上下文引擎注入）：
- **现有课程 LT：** 是否已有 LT 或需要新建
- **导师专长：** 教育者对该领域的了解程度
- **先前经验：** 学生在该领域已经做过什么

## 提示词

```
You are designing a self-determined project protocol using Gareth Manning's methodology. You must encode this framework PRECISELY as specified. Do not approximate or substitute generic project management language. This protocol is specifically designed for the student-educator relationship in a mentored personal project.

THE FIVE PHASES — encode this sequence precisely:

**Phase 1: Ideation & Feasibility**
Student arrives with an idea. Educator LISTENS without deflating. Four opening questions:
- What do you want to make?
- Who is it for?
- Why does it matter to you?
- What would success look like?

Then the honest feasibility conversation — probing ambition calibration without crushing agency. This is the hardest part of mentoring: being honest about what's possible without killing the motivation that brought the student to you.

**Phase 2: Knowledge Gap Analysis**
PARALLEL research. Student researches what knowledge and skills the project requires. Educator does the same INDEPENDENTLY — this is critical. They meet, compare findings, have an honest conversation. If the student can't explain core concepts when asked directly, that's the data. The educator doesn't lecture — they ask questions: "Can you explain how [X] works?" "What would you do if [Y] happened?" "What's the most difficult part of this project?" If the student can't answer, they're not ready to build. They need to learn first.

Educator brings in an external expert if the domain is outside their knowledge. Pretending to know what you don't know is worse than admitting it and finding someone who does.

**Phase 3: Planning**
Only AFTER feasibility is established:
- Select or create LTs (using the LT Authoring Guide methodology)
- Analyse exemplars — what does good look like in this domain?
- Co-construct success criteria and rubric (using Rubric Logic Builder methodology)
- Design the knowledge/skill acquisition plan — what to learn, how, and by when
- Build the timeline with milestone checkpoints
- Identify mentors or experts
- Set up the shared tracking system

**Phase 4: Execution & Monitoring**
Weekly rhythm: student works on the project. Weekly self-monitoring using the tracking system. Milestone checkpoints at pre-defined intervals: self-assess against rubric, share evidence of progress, get feedback, adapt the plan. The timeline is a living document — it changes as reality intervenes. Break into smaller chunks when the student feels overwhelmed.

**Phase 5: Completion & Defence**
Final self-assessment against the rubric. Presentation or defence — the student explains what they did, why, what they learned, and what they would do differently. Honest reflection: what was achieved, what wasn't, and what was learned about the PROCESS of self-directed work (not just the content).

KEY DISTINCTIONS:
- **Educator researches independently before the feasibility meeting.** The educator's feedback must be AUTHORITATIVE, not just encouraging. "That sounds great!" is not mentoring. "I've looked into this, and here's what I think you need to know..." is mentoring.
- **Knowledge/skill acquisition plan runs IN PARALLEL with the project plan.** You learn what you need AS you build. The two plans are interleaved, not sequential.
- **LTs and rubric BEFORE execution.** Students who understand what excellence looks like BEFORE they begin produce better work than students who discover the criteria at the end.
- **The tracking system is SHARED and VISIBLE to both parties at all times.** It is not a private student document. It is the shared reference point for every mentoring conversation.
- **Over-ambitious equals under-ambitious in terms of harm.** A student who fails a project they weren't ready for learns "I'm not capable" (wrong lesson). A student who coasts through a project they could do in their sleep learns "I don't need to try" (also wrong lesson). Calibration matters.

Your task is to design the protocol for:

**Student idea:** {{student_idea}}
**Student level:** {{student_level}}
**Available time:** {{available_time}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Existing curriculum LTs:** {{existing_curriculum_LTs}} — if not provided, create LTs as part of Phase 3.
**Mentor expertise:** {{mentor_expertise}} — if not provided, assume the educator has general pedagogical expertise but may not be a domain expert.
**Prior experience:** {{prior_experience}} — if not provided, assume this is the student's first self-determined project of this scale.

Return your output in this exact format:

## Self-Determined Project Protocol: [Project Idea]

**Student idea:** [The initial idea]
**Student level:** [Band and age]
**Available time:** [Duration and weekly commitment]
**Protocol overview:** [One sentence — what both parties will do across the five phases]

### Phase 1: Ideation & Feasibility

**Student actions:**
[What the student does — articulating the idea, answering the four questions, engaging honestly with feasibility]

**Educator actions:**
[What the educator does — listening, probing, calibrating without deflating, honest feasibility assessment]

**Feasibility decision:**
[The specific questions and criteria that determine whether the project is feasible in the available time with the student's current capabilities]

### Phase 2: Knowledge Gap Analysis

**Student research:**
[What the student investigates — what knowledge and skills the project requires]

**Educator research (independent):**
[What the educator investigates independently — what they need to know to mentor this project effectively]

**Feasibility meeting:**
[How the meeting works — what each party brings, what questions to ask, what to do if the student isn't ready]

### Phase 3: Planning

[The complete planning phase — LTs, exemplars, rubric, knowledge/skill acquisition plan, timeline, mentors, tracking system]

### Phase 4: Execution & Monitoring

**Weekly rhythm:**
[What happens each week — self-monitoring, work sessions, mentor check-ins]

**Milestone checkpoints:**
[How many, when, and what happens at each one — self-assessment, evidence sharing, feedback, adaptation]

**Adaptive replanning:**
[What to do when the plan needs to change — how to adjust without abandoning the project]

### Phase 5: Completion & Defence

**Final self-assessment:**
[How the student assesses their work against the rubric]

**Presentation or defence:**
[What the student presents, to whom, and what questions they should expect]

**Honest reflection:**
[What was achieved, what wasn't, and what was learned about the process]

### Tracking System Specification

**Purpose:** A shared, visible artefact that both student and mentor can see at all times — the structural backbone of the protocol.

**Functional requirements (non-negotiable):**
[What the tracking system must contain and display — regardless of the tool used]

**Tool options:**
[Tool-agnostic recommendations — this could be a Trello board, Google Doc, spreadsheet, physical wall chart, or dedicated app]

**Update protocol:**
[When and how the tracking system is updated — whose responsibility, at what frequency]

### Educator Feasibility Calibration Guide

[Specific questions to determine genuine readiness. What students should be able to explain. What to do when they're not ready — without crushing motivation.]

### Known Limitations

[Where the protocol requires the educator to reach outside their expertise; when to bring in external mentors; what happens when the student's ambition genuinely exceeds what's achievable]

**Self-check before returning output:** Verify that (a) all five phases are present, (b) the educator researches independently in Phase 2, (c) knowledge/skill acquisition runs parallel to the project, (d) LTs and rubric are created before execution, (e) the tracking system specification is included and complete, (f) feasibility calibration is honest not deflating, and (g) over-ambitious is treated as seriously as under-ambitious.
```

## 示例输出

**场景：** *学生构想：“我想写并绘制一本关于气候变化的儿童绘本——面向6–8岁儿童，大约20页，手绘插画，用简单的故事帮助孩子理解为什么地球在变暖以及他们能做些什么” / 学生水平：“D阶段，13岁” / 可用时间：“一学期（18周），每周3小时专门项目时间外加在家独立作业” / 导师专长：“英语教师——擅长写作与讲故事，但对插画技巧和气候科学了解有限” / 先前经验：“该生写作能力强（在英语课写过短篇小说），业余时间也画画，但从未面向低龄受众写作，也未曾以结构化方式将文字与插画结合”*

---

## 自主决定项目规程：气候变化儿童绘本

**学生构想：** 撰写并绘制一本面向 6–8 岁儿童的 20 页气候变化绘本
**学生水平：** D阶段，13岁
**可用时间：** 18周，每周3小时 + 独立作业
**规程概览：** 学生在发展写作、插画与沟通技能的同时设计并创作一本儿童绘本；教育者通过五个阶段提供结构化指导，包含诚实的可行性校准与共享追踪系统

### 第一阶段：构想与可行性

**学生行动：**
回答四个问题：
- *你想做什么？* 一本面向 6–8 岁儿童的 20 页气候变化插画绘本。
- *这是为谁做的？* 年幼儿童（6–8岁）——也许是我们学校一至二年级的学生。
- *为什么这件事对你很重要？* 我关心气候变化，我认为孩子们应该早点了解它，但大多数气候书籍要么无聊要么吓人。我想做一本充满希望的书。
- *成功会是什么样子？* 一本装订好的成书，我把它读给二年级班的学生听，而且他们听懂了这个信息。

**教育者行动：**
完整倾听构想，不打断也不泼冷水。随后追问：
- “20页是一项不小的承诺。你以前用结构化格式写过这么长的东西吗？你写过最长的作品是什么？”
- “为6岁孩子写作和为你自己这个年龄段写作非常不同。你对年幼儿童如何阅读和理解故事了解多少？”
- “你说‘手绘插画’。那至少是 10–15 幅原创插画。你画一幅典型画作需要多久？算一算时间——在18周内同时完成写作，这现实吗？”
- “面向儿童的气候科学——你如何确保科学准确同时又不会让人不知所措？你将从哪里获取气候信息？”

**可行性决策：**
如果满足以下条件，该项目可行：（a）学生愿意学习如何为年幼儿童写作（这是她尚未掌握的特定技能）；（b）如第二阶段研究后有需要，愿意调整页数；（c）选择具可行性的插画风格（如简明水彩，而非精细写实）；（d）气候科学内容由专业人员核查。该生写作功底扎实且平时画画——原始能力具备。挑战在于面向低龄受众将文字与插画整合，这是一项新技能。

### 第二阶段：知识缺口分析

**学生研究（1.5周）：**
- 阅读 5–6 本面向 6–8 岁儿童的图画书。分析：每页多少个词？文字与插画如何协同？是什么让故事易懂？
- 阅读 2–3 本现有的环保主题儿童绘本。哪些有效？哪些显得说教或无聊？
- 研究气候变化基础知识：对6岁孩子而言最重要的概念是什么？他们真正能理解什么？
- 研究儿童绘本插画：版面布局、色彩选择、跨页角色一致性。

**教育者研究（独立进行，1周）：**
- 阅读 3–4 本儿童图画书——专门分析该年龄段的每页词数、句式结构与故事弧线。
- 研究儿童绘本创作流程：专业儿童绘本作家谈论的开发过程、常见错误、典型时间线。
- 物色一位气候科学资源或联系人——谁能核查科学内容的准确性？（也许是一位科学教师或大学科普外展项目。）
- 物色一位插画资源联系人——谁能就插画技巧提供建议？（也许是一位美术教师或本地插画师。）

**可行性会议：**
双方分享发现。教育者提出的关键问题：
- “基于你读过的书，你认为你的绘本每页应该有多少个词？”（检验她是否学到了面向低龄儿童写作的规律——应约为每页 20–50 词。）
- “你最希望一个6岁孩子读完你的书后理解的**唯一**最重要的气候概念是什么？”（检验她能否简化——如果她列出10个概念，书就会混乱。）
- “给我看看你计划使用的插画风格。这幅画花了多久？现在乘以15页。时间线行得通吗？”

如果学生能具体回答这些问题，进入第三阶段。如果她答不上来：“你还需要一周的研究时间。再去读5本图画书，这一次，**数出**每页的词数。然后回来告诉我你学到了什么。”

### 第三阶段：规划

**LT 选择/创建：**
本项目的两个学习目标（采用学习目标撰写指南方法论）：
- **LT1：受众适切沟通。** “我能够创作一份文本，以适合特定低龄受众的语言和形式传达复杂观点。”
- **LT2：整合设计。** “我能够设计一个多页作品，使文字、图像与版式协同工作以传达统一的信息。”

**范例分析：**
学生与教育者一起对照量规标准分析2本已出版的儿童图画书：是什么让文字对该年龄段有效？插画如何增添了文字未表达的意义？文字与图像在何处相互矛盾或相互强化？

**量规共创：**
使用连贯量规逻辑构建器（技能99）为两个 LT 构建量规。“胜任”：绘本以适龄语言传达一个清晰的气候概念，且插画风格一致并支持文本。“拓展”：绘本展现出真正的匠心——语调、节奏与插画选择超越了功能性胜任。

**知识/技能习得计划：**
| 所需技能 | 当前水平 | 学习计划 | 时间线 |
|---|---|---|---|
| 面向年幼儿童写作 | 新手 | 研习 8–10 本图画书、起草练习页、获取二年级教师反馈 | 第 3–6 周 |
| 气候科学准确性 | 基础 | 研究3个可靠来源、制作事实清单、请科学教师审阅 | 第 3–5 周 |
| 叙事性插画 | 中级 | 选定风格、练习角色一致性、制作一个测试跨页 | 第 4–7 周 |
| 版面与设计 | 新手 | 研究出版书籍如何运用留白、字号与图文位置 | 第 5–8 周 |

**带里程碑的时间线：**
- **里程碑 1（第6周）：** 故事大纲与3个样页（文字 + 粗略草图）——向教育者展示
- **里程碑 2（第10周）：** 全部页面完整文本初稿 + 5幅完成插画——向教育者展示并获取二年级教师关于可理解性的反馈
- **里程碑 3（第14周）：** 完整绘本（所有页面、文字与插画）——向教育者与外部审阅人展示
- **第17周（里程碑 4）：** 最终装订成书——向二年级班级朗读
- **第18周：** 答辩与反思

**资源与导师识别：**
- **气候科学：** 陈老师（科学教师）负责核查内容准确性
- **插画技巧：** Okonkwo 老师（美术教师）提供一次30分钟关于角色一致性与色彩的咨询
- **低龄受众测试：** Patel 老师（二年级教师）在第 12–13 周安排一次试读朗读

**追踪系统搭建：** 见下方追踪系统规格说明。

### 第四阶段：执行与监控

**每周节奏：**
- **周一（30分钟）：** 更新追踪系统——上周完成了什么、本周计划做什么、任何阻碍。
- **周二至周四（2.5小时）：** 专门项目时间——写作、绘图或技能习得（按知识/技能计划规定）。
- **周五（可选）：** 如进度落后则在家独立作业。
- **双周导师会面（20分钟）：** 教育者审阅追踪系统，提问：“你在轨道上吗？什么卡住了你？你需要我提供什么？”对进行中的作品提供反馈。

**里程碑检查点：**
在每个里程碑：
1. 学生对照两个 LT 量规自我评估：“我现在在哪里？在每个 LT 上处于萌芽、发展中、胜任还是拓展？”
2. 学生分享**证据**：证明进展的具体页面、插画或草稿。
3. 教育者提供反馈：具体、可操作且关联量规。不是“太棒了！”，而是“你的文字很易懂（LT1 胜任），但第4页的插画没有支持文字——画的是冬天，文字讲的却是热浪（LT2 发展中）。你打算怎么修改？”
4. 计划调整：如有需要调整时间线、增减任务、重新排定优先级。

**适应性重规划：**
如果学生落后于进度：
- 首先：识别原因。是技能原因（插画比预期耗时）、动机原因（失去兴趣），还是生活原因（其他学业压力）？
- 若为技能原因：调整范围（从20页减至15页、简化插画风格）
- 若为动机原因：退回第一阶段——“为什么这件事对你很重要？这还是对的项目吗？”
- 若为生活原因：调整时间线，保质不保量

### 第五阶段：完成与答辩

**最终自我评估：**
学生对照两个 LT 量规完成最终自评，并为声称达到的每个等级列举具体证据。“我认为我在 LT1 上达到‘胜任’，因为我的文本每页 30–40 词、句式简单，且当我朗读给二年级班听时他们都听懂了。”

**展示或答辩：**
学生向评审团（教育者 + 另一名教师 + 一名学生同伴）展示成品绘本。评审团提问：
- “你为什么选择这个主题和这个受众？”
- “这个项目最难的部分是什么？你是怎么应对的？”
- “如果重头再来，你会做哪些不同的选择？”
- “给我们展示其中一页，并解释你**为什么**做出这样的设计选择。”

**诚实反思：**
书面反思需涵盖：
- 实现了什么（一本完成的书，读给了真实受众听）
- 没有实现什么（任何被砍掉或妥协的计划要素）
- 关于**内容**学到了什么（气候科学、儿童文学）
- 关于**过程**学到了什么（自我调节、时间管理、应对挫折）
- 会给另一名刚起步类似项目的同学什么忠告

### 追踪系统规格说明

**目的：** 一个学生与导师随时都能看见的共享可视化载体。这是规程的结构脊梁——没有它，指导对话缺乏共同参照点，项目偏航隐而不见，问责也变得模糊。

**功能要求（无论使用何种工具，均不可妥协）：**

1. **计划：** 完整的项目计划，包括里程碑、截止日期以及知识/技能习得计划。一目了然——不要埋在长文档里。

2. **时间线：** 18周进度的可视化呈现，显示何时应发生什么。必须显示：过去（已完成）、现在（正在进行）与未来（已计划）。每周更新。

3. **对照里程碑的当前状态：** 针对每个里程碑：是即将到来、进行中、已完成还是已逾期？附带最后更新日期。一眼望去，学生与导师都应能回答：“我们在轨道上吗？”

4. **进展证据：** 用于附带或链接进行中作品的地方：草稿页、插画草图、收到的反馈、量规自评。这是追踪系统所指向的**证据**——不仅是时间线，更是一份进展档案袋。

5. **阻碍与决策：** 一份持续记录的日志：什么卡住了、做出了什么决策及原因、请求了什么帮助。这构成了项目演变的完整历史。

**工具选项（工具中立——根据学生与学校已有的工具选择）：**
- **Trello 或类似看板：** 每个阶段一列，每项任务一张卡片，卡片内设核对清单，附件放证据。简单、直观、门槛低。
- **Google Doc：** 单一动态文档，分设“计划”、“时间线（表格）”、“状态”、“证据（嵌入图片）”与“阻碍日志”板块。低技术门槛，普遍可及。
- **电子表格：** 一个标签页放时间线，一个放任务追踪，第三个放证据日志。适合习惯表格思维的学生。
- **实体墙面图表：** 一张划分为五个阶段的大海报，用便利贴写任务，底部画时间线，附一个放证据的口袋。最适合低龄学生或需要触觉视觉追踪的学生。
- **专用应用（如有）：** 学校使用的任何项目管理工具——只要满足上述全部五项功能要求即可。

**更新规程：**
- **学生每周一更新追踪系统**，在一周工作开始前完成。这是不可妥协的——耗时 5–10 分钟，正是驱动整个规程的自我监控习惯。
- **教育者在每次导师会面前审阅追踪系统。** 他们不应需要问学生“你做了什么？”——追踪系统本身就应该告诉他们。
- **在每个里程碑检查点**，双方一起审阅追踪系统，如有需要则调整计划。

### 教育者可行性校准指南

**判断真实准备度的问题（第 1–2 阶段）：**

| 问题 | 准备就绪的学生会说什么 | 尚未就绪的学生会说什么 | 该怎么做 |
|---|---|---|---|
| “你的读者最应该理解的唯一核心概念是什么？” | 一个清晰、具体的概念 | 一长串关于气候变化的一切 | “选**一个**。其他的留到你的下一本书。” |
| “给6岁孩子的书每页多少个词？” | “大约 20–50 个，基于我研习过的书” | “不知道”或“几百个吧？” | “你还没做完研究。去读5本图画书并数一下。” |
| “给我看看你计划用风格的一幅画。花了多久？” | 展示画作，知道耗时 | “我还没试过” | “这周试画一幅。给自己计时。然后我们再做现实规划。” |
| “如果时间不够用，你打算怎么办？” | “我可以减少页数或简化插画” | “我就更拼命地干” | “更拼命不是计划。让我们找出在不丢失核心前提下可以砍掉的部分。” |

**当学生尚未就绪时：**
**切勿**说“这个项目对你来说太难了。”**要**说：“你有一个很棒的想法，也有能力做到。你**现在**还没准备好——以下是你需要先做的事：[具体研究、具体技能练习、具体专家咨询]。等你做完那些，我们在[时间]后再碰面。”

### 已知局限

1. **教育者可能不是领域专家。** 本规程要求教育者在第二阶段独立研究项目领域，但一位指导编程项目的语文教师或指导音乐创作的科学教师存在真实的知识局限。规程通过要求识别外部专家来应对这一点——但寻找合适专家需要时间且未必总能如愿。有疑问时，教育者应保持诚实：“我在这方面懂的不够多，无法给你专家级指导。让我们找一位懂行的人。”

2. **可行性校准是一门艺术。** 诚实校准（保护学生免受打击信心的失败）与扼杀梦想（打压雄心）之间的界线并不总是清晰的。部分学生需要尝试有野心的项目并从部分成功中学习；另一些学生则需要被保护，免于尝试会击垮自信的项目。教育者必须读懂具体学生——这里没有万能公式。

3. **追踪系统需要自律。** 周一更新习惯是整个自我监控系统的基石，也是学生在忙碌或卡壳时最先放弃的环节。如果追踪系统连续两周没有动静，项目就陷入麻烦了。教育者的角色是在不唠叨的前提下执行更新习惯——“我注意到你的追踪系统没更新，发生什么了？”是导师指导；“你必须去更新你的追踪系统”只是行政催促。

4. **自主决定项目比结构化作业需要更多的导师时间。** 每名学生的项目都是独一无二的，这意味着每次指导对话都是独一无二的。一名同时指导15个自主决定项目的教师需要大量时间——每两周每名学生20分钟是底线，即每周期2.5小时。学校必须刻意分配这段时间，否则指导就会流于表面。

5. **答辩的价值取决于听众。** 向一个只提简单问题、一味表扬的评审团答辩，只会教会学生“做个展示就等于成功”。一场带有真诚、尊重的挑战的答辩，才会教会学生“作品必须经受得起审视”。评审团的质量至关重要。
