---
# AGENT SKILLS STANDARD FIELDS (v2)
name: teacher-inquiry-cycle-designer
description: "设计从研究问题经由数据收集到循证行动的教师实践者探究循环。适用于启动行动研究、教师主导的调查或专业探究。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "professional-learning/teacher-inquiry-cycle-designer"
skill_name: "教师探究循环设计器"
domain: "professional-learning"
version: "1.0"
evidence_strength: "strong"
evidence_sources:
  - "Timperley (2011) — Realizing the Power of Professional Learning"
  - "Timperley et al. (2007) — Teacher Professional Learning and Development: Best Evidence Synthesis"
  - "Cochran-Smith & Lytle (2009) — Inquiry as Stance: practitioner research for the next generation"
  - "Dana & Yendol-Hoppey (2014) — The Reflective Educator's Guide to Classroom Research"
  - "Earl & Katz (2006) — Leading Schools in a Data-Rich World"
input_schema:
  required:
    - field: "inquiry_question"
      type: "string"
      description: "教师希望调查的问题——关于其实践及对学生学习的影响"
    - field: "teacher_context"
      type: "string"
      description: "教师处境——学科、年级、专业学习目标"
  optional:
    - field: "student_level"
      type: "string"
      description: "年龄/年级"
    - field: "available_time"
      type: "string"
      description: "教师可投入该探究的时间——一学期、一学年"
    - field: "data_available"
      type: "string"
      description: "教师已有或可收集的数据——测验分数、学生作品、问卷、观察"
    - field: "collaboration"
      type: "string"
      description: "教师是独立开展还是团队合作"
    - field: "school_support"
      type: "string"
      description: "学校是否有结构化探究项目，还是教师独立开展"
output_schema:
  type: "object"
  fields:
    - field: "inquiry_design"
      type: "object"
      description: "完整探究循环——问题、基线、干预、证据收集、分析、结论"
    - field: "data_plan"
      type: "object"
      description: "收集什么数据、何时收集、如何收集——务实且可管理"
    - field: "analysis_framework"
      type: "object"
      description: "如何分析数据——寻找什么模式、如何得出结论"
    - field: "sharing_plan"
      type: "string"
      description: "如何与同事分享发现——将学习扩散至教师个体之外"
chains_well_with:
  - "reflective-practice-prompt-generator"
  - "lesson-study-cycle-designer"
  - "instructional-coaching-conversation-guide"
  - "professional-development-session-designer"
  - "pedagogical-content-knowledge-developer"
  - "technological-pedagogical-content-knowledge-developer"
teacher_time: "4 分钟"
tags: ["inquiry", "Timperley", "practitioner-research", "action-research", "data-informed", "professional-learning"]
---

# 教师探究循环设计器

## 本技能的功能

设计一个结构化的教师探究循环——一种实践者研究形式，教师借此调查关于自身实践及其对学生学习影响的特定问题、收集证据、分析发现并得出指导未来教学的结论。来自 Timperley 研究的核心原则在于：当教师探究其实践对学生成果的**影响（IMPACT）**，而不仅仅是反思自己做了什么时，最有力量的专业学习才会发生。产出包括完整探究设计（问题、基线、干预、证据收集、分析、结论）、务实的数据计划（收集什么与何时收集——在教学工作量内可承受）、分析框架以及分享发现的计划。AI 在此处具有独特价值，因为设计一个严谨又可管理的探究需要在研究标准（有效问题、恰当证据、公平分析）与现实教学约束（时间有限、研究训练有限、探究需服务于学习而非仅服务于调查）之间取得平衡。

## 循证基础

Timperley（2011）将教师探究置于有效专业学习的核心，主张最有力的专业学习循环是：识别学生学习需求 → 识别教师需要学什么 → 参与专业学习 → 在实践中应用 → 评估对学生的影响 → 精炼。这就是探究——对教与学之间关系的系统性调查。Timperley 等人（2007）发现，最有效的专业发展项目让教师主动调查新实践对学生的影响——不仅仅是实施策略，更要检验它们是否奏效。Cochran-Smith 与 Lytle（2009）提出了“作为立场的探究（inquiry as stance）”——认为探究不是一次性项目，而是一种专业倾向：一种面向质疑、调查与从实践中学习的习惯性取向。Dana 与 Yendol-Hoppey（2014）为课堂研究提供了实用指导，强调教师探究无需达到学术期刊研究标准——它是务实的、情境特异的，旨在改进教学而非产出普适性知识。Earl 与 Katz（2006）区分了“数据驱动（data-driven）”决策（让数据发号施令）与“数据知情（data-informed）”决策（将数据作为与专业判断并列的输入之一）。教师探究正是数据知情的——数据照亮问题，但由教师进行解读。

## 输入模式

教师必须提供：
- **探究问题：** 想调查什么。*例如：“在每节课开头使用提取练习是否能提高我九年级学生对核心科学词汇的记忆保持？” / “当我用随机点名替代‘举手回答’时，学生参与度会发生什么变化？” / “提供书面成功标准如何影响七年级学生创意写作的质量？”*
- **教师背景：** 其处境。*例如：“九年级科学，5年教龄，对记忆与保持研究感兴趣” / “新教师，七年级英语，正为参与度不均而苦恼”*

可选（如有，由上下文引擎注入）：
- **学生水平：** 年级
- **可用时间：** 探究持续时长
- **可用数据：** 可获取的数据
- **协作形式：** 个人或团队
- **学校支持：** 结构化项目或独立开展

## 提示词

```
You are an expert in teacher inquiry and practitioner research, with deep knowledge of Timperley's (2011) inquiry cycle, Cochran-Smith & Lytle's (2009) inquiry as stance, Dana & Yendol-Hoppey's (2014) practical classroom research methods, and Earl & Katz's (2006) data-informed professional practice. You understand that teacher inquiry is PRACTICAL research — designed to improve teaching, not to produce academic publications. It must be rigorous enough to produce trustworthy findings but manageable enough to fit within a teaching workload.

CRITICAL PRINCIPLES:
- **The question must be about IMPACT, not just practice.** "Am I using retrieval practice?" is about practice. "Does my use of retrieval practice improve student retention?" is about impact. Impact questions are more useful because they focus on what matters: student learning.
- **The inquiry must be MANAGEABLE.** A teacher conducting inquiry alongside a full teaching load cannot collect data with the rigour of a university researcher. Design data collection that fits within existing routines — using student work, existing assessments, and brief observations rather than creating additional workload.
- **Baseline before intervention.** The teacher needs to know the starting point before they can measure change. What does student learning look like BEFORE the new practice is introduced?
- **Multiple sources of evidence.** No single data source is sufficient. Triangulate: student work + teacher observation + student voice. If all three point in the same direction, the finding is trustworthy.
- **Honest conclusions.** The inquiry should report what was FOUND, not what was hoped for. If the intervention didn't work, that's a valuable finding — it prevents the teacher from persisting with an ineffective practice.

Your task is to design a teacher inquiry for:

**Inquiry question:** {{inquiry_question}}
**Teacher context:** {{teacher_context}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Student level:** {{student_level}} — if not provided, infer from the question.
**Available time:** {{available_time}} — if not provided, design for a one-term inquiry (10–12 weeks).
**Data available:** {{data_available}} — if not provided, identify manageable data sources.
**Collaboration:** {{collaboration}} — if not provided, design for a solo inquiry with optional peer review.
**School support:** {{school_support}} — if not provided, design as an independent inquiry.

Return your output in this exact format:

## Teacher Inquiry: [Question]

**Question:** [The inquiry question]
**Teacher:** [Context]
**Duration:** [How long]

### Inquiry Design

**Phase 1 — Baseline (Weeks 1–2):**
[What data to collect before the intervention starts]

**Phase 2 — Intervention (Weeks 3–8):**
[What the teacher will change in their practice and how]

**Phase 3 — Evidence Collection (Throughout):**
[What data to collect during the intervention — practical, manageable sources]

**Phase 4 — Analysis (Weeks 9–10):**
[How to analyse the evidence — what to look for, how to compare to baseline]

**Phase 5 — Conclusions (Weeks 11–12):**
[How to draw conclusions and decide what to do next]

### Data Plan

| Data Source | What It Shows | When to Collect | Time Required |
|---|---|---|---|
| [Source 1] | [What it reveals] | [Timing] | [Time cost] |
| [Source 2] | | | |
| [Source 3] | | | |

### Analysis Framework

[How to make sense of the data — what patterns to look for, how to compare baseline and post-intervention, how to handle mixed results]

### Sharing Plan

[How to share findings with colleagues — not as a formal presentation but as practical professional knowledge]

### Honest Caveats

[What the inquiry can and cannot prove — the limitations of a small-scale classroom inquiry]

**Self-check before returning output:** Verify that (a) the question is about impact on student learning, (b) baseline data is collected before the intervention, (c) multiple data sources are used, (d) the data plan is manageable within teaching workload, (e) the analysis framework is honest about limitations, and (f) the sharing plan spreads the learning beyond the individual teacher.
```

## 示例输出

**场景：** *探究问题：“在每节课开头使用提取练习是否能提高我九年级学生对核心科学词汇的记忆保持？” / 教师背景：“九年级科学，5年教龄，对认知科学与记忆研究感兴趣，注意到学生在特定主题词汇上吃力，课与课之间容易遗忘核心术语” / 可用时间：“一学期——10周” / 可用数据：“前两个主题的单元末测试分数（基线对比）、学生练习本以及教师自己的授课记录”*

---

## 教师探究：提取练习与词汇保持

**问题：** 在每节课开头使用提取练习是否能提高九年级学生对核心科学词汇的记忆保持？
**教师：** 九年级科学，5年教龄
**时长：** 10周（一学期）

### 探究设计

**第一阶段——基线（第 1–2 周）：**
在引入提取练习之前，先收集当前词汇保持率的基线数据：
- 在新学期**开头**、开始任何新授课之前，进行一次简短词汇小测（来自上一主题的10个核心术语）。这测量了学生在假期/间隔期间保留了多少词汇。
- 审阅**前两个**主题的单元末测试分数。学生在依赖词汇的题目上表现如何？这提供了历史对比数据。
- 询问学生（简短问卷，3个问题）：“你如何复习科学？当你忘记一个核心词时，你会怎么做？你对科学词汇有多自信？”这捕捉了干预前的学生感知。

**第二阶段——干预（第 3–8 周）：**
在每节科学课开头引入5分钟的提取练习常规：
- “上节课 / 上周 / 上个月”格式：黑板上展示3道题。学生凭记忆在迷你小白板或练习本专门区域作答。教师核对答案、纠正错误，然后进入正课。总时长：最多5分钟。
- 题目专门聚焦词汇：“‘光合作用’是什么意思？” / “用‘酶’造一个能表明你理解它的句子” / “‘呼吸作用’与‘呼吸’有什么区别？”
- 教师保留一份记录：问了哪些问题、正确作答的学生百分比。这每节课只需30秒（在便利贴上划正字计数）。

**第三阶段——证据收集（贯穿全程）：**
1. **每周提取数据：** 教师的授课日志——正确回答词汇题的学生百分比。追踪干预的6周，观察准确率是否上升。
2. **中期词汇小测（第6周）：** 针对当前主题的10词小测，在与基线小测相同条件下进行。这提供了直接对比。
3. **单元末测试（第8周）：** 将学生在词汇相关题目上的表现与前两次单元末测试（基线数据）对比。
4. **学生声音（第8周）：** 重复第1周的3题问卷。学生对词汇的自信度变化了吗？学生注意到提取常规了吗？

**第四阶段——分析（第 9–10 周）：**
对比：
- 基线词汇小测分数（第1周） vs. 中期小测分数（第6周）：保持率提高吗？
- 单元末测试词汇题分数（当前主题，有提取练习） vs. 先前主题分数（无提取练习）：词汇依赖题目的表现提高了吗？
- 每周提取数据：是否存在趋势？第8周答对的学生是否比第3周更多？
- 学生问卷：自陈自信度是否改变？

**第五阶段——结论（第 10–11 周）：**
诚实回答探究问题：
- 如果数据在多个来源上均显示改善（小测分数上升、测试表现上升、提取准确率呈上升趋势、学生感觉更自信）：得出结论，提取练习似乎改善了该班级的词汇保持。
- 如果数据呈混合态势（小测分数提高但测试表现未变）：调查原因。可能解释：测试未孤立出词汇（其他因素影响了分数），或提取练习改善了短期保持但尚未转化为长期（需要持续更久）。
- 如果数据显示无改善：诚实报告。可能解释：5分钟“剂量”不够、题目未瞄准正确词汇，或词汇保持取决于提取练习之外的因素。

### 数据计划

| 数据来源 | 展示内容 | 何时收集 | 所需时间 |
|---|---|---|---|
| 基线词汇小测（10词） | 干预前保持水平 | 第1周 | 10分钟课堂时间，15分钟批改 |
| 每周提取日志（划正字） | 提取准确率趋势 | 每节课（第 3–8 周） | 每节课30秒 |
| 中期词汇小测 | 干预中期保持率 | 第6周 | 10分钟课堂时间，15分钟批改 |
| 单元末测试（孤立出词汇题） | 干预后表现 | 第8周 | 已属于常规评估一部分 |
| 学生问卷（3个问题） | 学生对词汇自信度的感知 | 第1周与第8周 | 5分钟课堂时间 |

**额外总耗时：** 10周内总计约90分钟（在常规教学之外）。这是完全可管理的。

### 分析框架

**寻找趋同点。** 如果全部四个数据来源（小测、测试、每周日志、学生声音）指向同一方向，发现就比较稳健。如果它们分歧，调查原因。

**使用简单对比。** 这不是统计学论文。对比均值：“基线词汇小测平均分为 4.2/10，中期为 7.1/10。”对比比例：“第3周 45% 的学生答对提取题。到第8周升至 78%。”视觉化呈现（每周提取准确率的简易折线图）能让趋势一目了然。

**对归因保持诚实。** 你无法证明是提取练习**导致**了改善。其他因素也在同时变化（学生学了新内容、与教师更熟悉、一学期内自然成熟）。你**能够**说的是：“在引入提取练习期间，词汇保持率有所提高，且学生报告感觉更自信。这与关于提取练习的研究一致，表明值得继续。”

### 分享计划

**非正式：** 在教研组会上与科学组同事分享发现（15分钟）。展示数据、描述常规、邀请提问。主动分享提取题库。

**结构化：** 撰写一页纸摘要：问题 → 我做了什么 → 我发现了什么 → 下一步我打算做什么。贴在教师休息室的专业学习展板上（如有）或通过邮件分享。

**实践性：** 主动为感兴趣的同事示范提取常规。更好的做法是：邀请一位同事专门来观摩你的一节课，看看提取常规在实际中的运作。

### 诚实警示

1. **这是一项小规模探究，而非对照实验。** 没有对照组（一个未接受提取练习的平行班）。你不能断然将改善归因于提取练习——其他因素可能也起了作用。这是实践者探究的常见局限——但发现对于指导**你自己的**实践依然极具价值。

2. **教师既是研究者又是实践者。** 你希望干预奏效（你相信提取练习），这会产生偏见。对自己保持诚实：如果数据未显示改善，抵制找借口将其解释掉的诱惑。阴性发现与阳性发现同样有价值。

3. **一学期可能不够长。** 提取练习的效应在更长周期内最为显著（Roediger & Butler, 2011）。如果一学期后结果温和，在断定提取练习对你的学生无效之前，请考虑将探究延长至第二学期。

---

## 已知局限

1. **教师探究具有情境特异性。** 一位教师在某一所学校的一个班级进行的探究结果，无法泛化到所有情境。教师探究的价值在于它产出**本地知识**——直接适用于教师自身实践的知识，即便它不能被宣称为普适真理。

2. **探究需要一个真正的问题。** 如果教师早已认定提取练习有效，只是用探究来印证这一信念，探究就失去了价值。真正的探究需要真正的不确定性：“我认为这可能有效——让我去查明。”如果教师并非真正开放地接受“干预可能无效”的可能性，探究就变成了辩护，而非调查。

3. **数据收集绝不能损害教学。** 如果探究的数据要求变得过于繁重以至于降低了教学质量，探究就适得其反了。上述数据计划特意设计为极简——但一旦教师觉得任何数据收集不可持续，就应果断放弃。一项严谨度略低但真正完成并落地的探究，比一项设计完美却在第4周半途而废的探究更有价值。
