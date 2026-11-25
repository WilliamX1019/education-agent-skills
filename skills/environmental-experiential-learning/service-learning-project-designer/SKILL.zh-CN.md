---
# AGENT SKILLS STANDARD FIELDS (v2)
name: service-learning-project-designer
description: "设计将真实社区需求与嵌入式课程学习相结合的服务性学习项目。适用于规划社区项目、公民参与或社会行动单元时。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "environmental-experiential-learning/service-learning-project-designer"
skill_name: "服务性学习项目设计师"
domain: "environmental-experiential-learning"
version: "1.0"
evidence_strength: "moderate"
evidence_sources:
  - "Billig (2000) — Research on K-12 school-based service learning: the evidence builds"
  - "Billig (2004) — Heads, hearts, and hands: the research on K-12 service learning"
  - "RMC Research Corporation (2007) — Impacts of Service Learning on Participating K-12 Students"
  - "Furco (2002) — Is service learning really better than community service?"
  - "Celio, Durlak & Dymnicki (2011) — A meta-analysis of the impact of service learning on students"
input_schema:
  required:
    - field: "community_need"
      type: "string"
      description: "项目所回应的真实社区需求或问题——与社区共同识别或由社区提出，而非由学校臆测"
    - field: "curriculum_connection"
      type: "string"
      description: "与服务相连的具体课程内容——项目中嵌入了哪些学术学习"
  optional:
    - field: "student_level"
      type: "string"
      description: "年龄/年级"
    - field: "community_partner"
      type: "string"
      description: "学校合作的社区组织、团体或个人"
    - field: "project_duration"
      type: "string"
      description: "项目持续时间——一天、一周、一学期、长期持续"
    - field: "school_context"
      type: "string"
      description: "学校是否已有服务性学习传统，还是首次尝试"
    - field: "student_voice"
      type: "string"
      description: "学生是否有权参与选择项目，还是已事先确定"
output_schema:
  type: "object"
  fields:
    - field: "project_design"
      type: "object"
      description: "完整的服务性学习项目——社区需求、课程连接、服务活动、反思结构、评估"
    - field: "community_partnership"
      type: "object"
      description: "学校与社区伙伴如何协作——真正的伙伴关系，而非慈善施舍"
    - field: "curriculum_integration"
      type: "object"
      description: "学术学习如何嵌入服务之中——学生“通过”服务学到什么，而非与服务割裂"
    - field: "reflection_structure"
      type: "object"
      description: "学生如何反思这段经历——服务前、服务中与服务后"
    - field: "assessment_plan"
      type: "object"
      description: "如何同时评估学术学习与公民素养发展"
chains_well_with:
  - "experiential-learning-cycle-designer"
  - "interdisciplinary-real-world-connection-mapper"
  - "ubuntu-collective-knowledge-task-designer"
  - "agency-scaffold-generator"
teacher_time: "4 分钟"
tags: ["service-learning", "Billig", "community", "civic-engagement", "experiential", "reflection", "social-responsibility"]
---

# 服务性学习项目设计师

## 本技能的作用

设计一个将真实社区服务与结构化学术学习相结合的服务性学习（service learning）项目——确保学生既能为社区做出有意义的贡献，又能在此过程中学习课程内容。借用 Furco (2002) 的关键区分：服务性学习“不是”社区服务（只有服务而无学术学习）、“不是”志愿活动（只有服务而无结构化反思），也“不是”实地考察（只有体验而无服务）。服务性学习整合了三大要素：真实的社区收益、与课程相连的学术学习，以及将两者连接起来的结构化反思。该方法借鉴了 Billig (2000, 2004) 的研究：只有当服务通过明确反思直接与课程目标相连时，才会产生最强的学业效应——而不是服务与学术各行其是、互不关联。输出包括完整项目设计、社区伙伴框架、课程整合计划、反思结构（服务前、服务中、服务后）以及评估方案。AI 在此尤为有价值，因为设计有效的服务性学习需要同时兼顾社区需求、课程要求、后勤限制以及将服务体验转化为学术学习的结构化反思——这是一个缺失任何一环都会削弱整体的复杂设计挑战。

## 循证基础

Billig (2000) 综述了 K-12 服务性学习研究，发现其对学业成就、公民责任和个人-社会发展具有中等正向效应。关键在于，她发现这些效应取决于质量指标：服务必须回应真实的社区需求（而非人为制造的需求），服务必须通过明确教学与课程内容相连，且学生必须在服务前、服务中和服务后参与结构化反思。缺乏这些质量指标的服务只能带来社区收益，却几乎不产生学习。Billig (2004) 进一步阐述了作用机制：服务性学习通过为学术内容提供真实语境（学生明白为什么这些内容重要）、培养公民身份认同（学生将自己视为社区贡献者）以及建立社会情感技能（同理心、合作、责任感）来发挥作用。Furco (2002) 做出了关键区分：社区服务侧重于“服务”（主要受益者是社区），实地教育侧重于“学习”（主要受益者是学生），而服务性学习将两者整合（学生与社区平等受益）。如果服务占主导而学习沦为事后点缀，那就是社区服务；如果学习占主导而服务只是幌子，那就是实地教育。真正的服务性学习使两者保持平衡。RMC Research Corporation (2007) 总结证据发现，高质量的服务性学习项目（具备结构化反思、课程连接与真实社区伙伴关系）对学业投入度、公民责任感和社交技能产生了积极影响——但低质量项目（一次性服务日、无反思、无课程连接）则未产生可测量的效应。Celio, Durlak & Dymnicki (2011) 对 62 项研究进行了元分析，发现学业成果的平均效应量为 d=0.27——效应温和但为正向，且具有结构化反思的项目效应显著更高。

## 输入模式

教师必须提供：
- **Community need（社区需求）：** 社区需要什么。*例如："The local food bank is struggling with donations — families in our area are experiencing food poverty" / "Elderly residents in the care home near our school are isolated — many have no visitors" / "The local park has become littered and overgrown — the community wants to restore it" / "Younger students in the primary school next door are struggling with reading — they need more reading partners"*
- **Curriculum connection（课程连接）：** 学生将学到什么。*例如："Persuasive writing and campaign design — Year 9 English" / "Data handling and analysis — Year 8 Maths" / "Ecosystems and biodiversity — Year 7 Science" / "Reading comprehension and fluency — Year 5 English"*

可选（如上下文引擎可用则自动注入）：
- **Student level（学生水平）：** 年级
- **Community partner（社区伙伴）：** 合作组织或团体
- **Project duration（项目时长）：** 持续时间
- **School context（学校背景）：** 服务性学习传统
- **Student voice（学生话语权）：** 学生拥有多少选择权

## Prompt

```
You are an expert in service learning design, with deep knowledge of Billig's (2000, 2004) research on K-12 service learning, Furco's (2002) distinction between service learning, community service, and field education, the RMC Research Corporation's (2007) quality indicators for effective service learning, and Celio, Durlak & Dymnicki's (2011) meta-analysis. You understand that service learning is NOT "doing something nice for the community and learning about it afterwards" — it is a carefully designed pedagogy where service and learning are INTEGRATED through structured reflection, each strengthening the other.

CRITICAL PRINCIPLES:
- **The community need must be GENUINE and identified WITH the community, not FOR them.** The school should not decide what the community needs and then offer it. Genuine partnership means asking: "What does your organisation need? How can our students help in a way that actually serves you?" If the service is designed primarily to benefit the students' learning and the community benefit is an afterthought, it's not service learning — it's field education wearing a charitable mask.
- **The curriculum connection must be DIRECT, not incidental.** "Students learn about food poverty" is incidental to helping at a food bank. "Students analyse food bank data to identify patterns in demand, use statistical methods to predict future need, and present findings to the food bank to improve their planning" is a direct curriculum connection — the academic work IS the service, and the service IS the academic work.
- **Reflection is the mechanism that connects service and learning.** Without reflection, service produces experience but not learning. Billig's research is clear: structured reflection — before service (what do we know? what do we expect?), during service (what are we noticing? what questions arise?), and after service (what did we learn? what changed?) — is what transforms service into education.
- **Reciprocity, not charity.** Service learning should position students and community members as PARTNERS, not as helpers and helped. The community contributes knowledge and expertise; the students contribute time and skills. Both benefit. A project where students feel sorry for the community and "help" them reinforces power imbalances. A project where students and community members work together on a shared problem develops civic partnership.
- **Quality over quantity.** A well-designed, deeply connected service learning project that lasts one week produces more learning than a superficial "service day" repeated monthly. Depth of service, depth of reflection, and depth of curriculum connection matter more than hours of service.

Your task is to design a service learning project for:

**Community need:** {{community_need}}
**Curriculum connection:** {{curriculum_connection}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Student level:** {{student_level}} — if not provided, infer from the curriculum connection.
**Community partner:** {{community_partner}} — if not provided, suggest appropriate community partners.
**Project duration:** {{project_duration}} — if not provided, design for a 2–3 week project.
**School context:** {{school_context}} — if not provided, design as a standalone project.
**Student voice:** {{student_voice}} — if not provided, build in student choice where possible.

Return your output in this exact format:

## Service Learning Project: [Community Need] × [Curriculum Connection]

**Community need:** [The genuine need being addressed]
**Curriculum connection:** [The academic learning embedded in the service]
**Reciprocity statement:** [How both the community and students benefit — balanced, not charitable]

### Community Partnership

**Partner:** [The community organisation or group]
**Their need:** [What they actually need, in their terms]
**Their contribution:** [What they bring to the partnership — knowledge, expertise, access, perspective]
**Student contribution:** [What students bring — time, skills, energy, fresh perspective]
**Partnership principles:** [How the relationship is structured — respectful, reciprocal, genuine]

### Curriculum Integration

**Academic objectives:** [What students learn through the service — specific curriculum content and skills]
**How service IS learning:** [The mechanism — how the academic work is embedded in the service activity itself, not separate from it]
**How learning IS service:** [The mechanism — how the academic work produces something the community actually needs]

### Project Design

**Phase 1 — Investigation and preparation**
[How students learn about the community need, connect with the community partner, and prepare for service]

**Phase 2 — Service and learning**
[What students do — the integrated service-learning activities]

**Phase 3 — Reflection and sharing**
[How students reflect on the experience and share what they've learned — with the community and with the school]

### Reflection Structure

**Before service:** [What students reflect on before they begin — preconceptions, expectations, questions]
**During service:** [How students reflect while serving — journals, discussions, observations]
**After service:** [How students reflect after completing the service — what changed, what they learned, what questions remain]

### Assessment Plan

**Academic assessment:** [How curriculum learning is assessed — using evidence from the service]
**Civic development assessment:** [How civic skills and dispositions are assessed — not graded but documented]
**Community feedback:** [How the community partner assesses the service — did it genuinely help?]

**Self-check before returning output:** Verify that (a) the community need is genuine, (b) the curriculum connection is direct, (c) reflection is structured before, during, and after, (d) the relationship is reciprocal, and (e) both the community and students benefit meaningfully.
```

## 示例输出

**场景：** *Community need: "The local food bank is struggling — demand has increased 40% in the last year, but they lack the data infrastructure to predict demand patterns, manage stock efficiently, or communicate their impact to funders. They need help analysing their distribution data and creating materials that communicate their impact." / Curriculum connection: "Year 9 Mathematics — data handling, statistical analysis, percentages, graphical representation, interpretation of real data sets" / Community partner: "The local food bank — a volunteer-run charity that distributes food parcels to approximately 200 families per week. The manager is willing to share anonymised distribution data and would welcome help with data analysis and impact reporting." / Project duration: "3 weeks"*

---

## 服务性学习项目：食物银行数据 × 九年级数学

**社区需求：** 当地食物银行缺乏数据分析能力——他们收集了发放数据，却无法分析数据以预测需求、管理库存或向资助方展示其社会影响
**课程连接：** 九年级数学——统计分析、百分比、图表呈现以及真实数据集的解读
**互惠声明：** 食物银行贡献真实数据、关于食物匮乏的专业知识以及让数学变得有意义的真实语境；学生贡献数据分析技能、时间和新鲜视角。食物银行获得一份影响力报告与数据看板；学生通过真实使命发展数学能力。

### 社区伙伴关系

**合作方：** 当地食物银行
**他们的真实需求（按其原话）：** "We know demand is increasing but we can't show the funders exactly how much, or predict when we'll run out of specific items. We collect the data on paper forms but nobody has time to analyse it. If we could show the council and funders a clear picture of our impact, we'd be more likely to secure funding."
**他们的贡献：** 经匿名化处理的发放数据（何时向谁发放了什么）、关于当地食物匮乏的专业知识、让项目具有意义的真实语境、开放食物银行供参访、愿意向学生介绍他们的工作。
**学生的贡献：** 数学分析技能（数据清洗、统计分析、图表呈现）、时间（连续 3 周的数学课），以及产出食物银行能够实际使用的影响力报告和数据看板。
**伙伴原则：** 食物银行是“客户”，而不是“慈善施舍对象”。学生是在回应真实需求、提供专业服务（数据分析）。所有产出在对外使用前均由食物银行经理审阅批准。学生在食物银行内不拍照，也不识别服务对象身份。

### 课程整合

**学术目标：** 收集、整理并分析真实数据。计算百分比和百分比变化。为真实数据制作恰当的统计图表（柱状图、折线图、饼图）。解读统计规律并清晰传达发现。九年级数据处理全部课程目标均通过食物银行数据落实。

**服务本身“就是”学习：** 学术工作本身就是服务。学生不是“学完数学顺便帮一下食物银行”——他们是“通过”帮助食物银行来学习数学。数据分析本身就是有价值的服务。算出的每一个百分比、绘制的每一张图表、识别出的每一条规律，都直接服务于食物银行对影响力数据的需求。数学课与服务之间没有割裂。

**学习本身“就是”服务：** 数学产出（影响力报告、数据看板、需求预测）对食物银行真正有用。经理将在资助申请中使用影响力报告；需求预测将帮助规划库存采购；数据可视化图表将展示在食物银行内，向志愿者和捐赠者呈现他们工作的成效。

### 项目设计

**第 1 阶段——调查与准备（第 1 周）**

*第 1 课：理解需求。*
食物银行经理来到学校（或发送视频致辞），介绍食物银行的工作内容、服务对象、需求变化情况以及他们希望学生提供什么帮助。学生提问。经理分享匿名化数据集（纸质表格或电子表格）。

关键时刻：学生看到原始数据，意识到它杂乱、不完整且真实——与课本数据完全不同。这正是数学挑战所在：如何从不完美的真实数据中提炼意义？

*第 2 课：熟悉数据。*
学生分组审视数据集。里面包含什么？缺失了什么？是如何组织的？学生清洗数据：识别缺失项、对物品分类、建立可用的电子表格。这是“真实的”数据处理——专业人士日常在做、而课本练习从不包含的数据工作。

*第 3 课：规划分析。*
每个小组负责一个分析问题：
- A 组："How has demand changed over the last 12 months?"（百分比变化、折线图）
- B 组："What types of food are most in demand?"（频数分析、饼图）
- C 组："Are there seasonal patterns in demand?"（跨月对比、柱状图）
- D 组："How many families are served per week, and is this increasing?"（均值、趋势线）
- E 组："Where do referrals come from?"（分类数据、柱状图）

**第 2 阶段——服务与学习（第 2 周）**

*第 4–5 课：数据分析。*
各组开展分析。这是高强度的数学工作：计算百分比、绘制图表、解读规律。教师巡视，按需穿插微课讲解（如何计算百分比变化、如何识别趋势、如何选择合适的图表类型），并确保数学严谨性。

与课本练习的关键区别在于：数据是真实的。答案事关重大。如果 A 组算出需求增长了 43%，这不是一道课本答案——而是食物银行需要知道的关于他们社区的真实事实。

*第 6 课：参访食物银行（如条件允许）。*
学生参访食物银行，亲眼看到运营流程：食物如何分类、食物包如何组装、家庭如何领取，并与志愿者交流。这为数据赋予了人文语境——数字背后是一个个真实的人。参访之后，学生带着焕然一新的动力与理解回到分析工作中。

**第 3 阶段——反思与分享（第 3 周）**

*第 7 课：编制影响力报告。*
各组将分析结果汇总成一份完整的影响力报告。每组贡献各自板块（含数据、图表和解读）。全班共同撰写引言与结论。报告按专业格式排版——这是食物银行将用于申请资助的正式文件。

*第 8 课：向食物银行汇报。*
食物银行经理再次来到学校（或学生前往食物银行）。学生展示他们的发现。经理回应："This is exactly what we needed. We can use this graph in our next funding application. Your demand prediction will help us plan stock orders."

*第 9 课：反思与评估。*
开展结构化最终反思（见下文）及个人评估任务。

### 反思结构

**服务前（第 1 课）：**
- "What do you know about food banks? Who uses them and why?"
- "What preconceptions do you have about people who use food banks? Where do these come from?"（挑战关于贫困的刻板印象——这是公民学习维度）
- "What do you expect the data to show? Make a prediction: has demand increased or decreased? By how much?"

**服务中（第 4–6 课）：**
- "What surprised you in the data? Did anything challenge your expectations?"
- "How does the real data compare to textbook data? What's different? What makes it harder?"
- 参访后："What did you see today that the data doesn't show? What can numbers capture and what can't they?"

**服务后（第 9 课）：**
- "What mathematical skills did you use that you didn't realise you'd need?"
- "How did working with real data for a real purpose change how you approached the Maths?"
- "Has your understanding of food poverty changed? How? What questions do you still have?"
- "What does it mean that mathematical skills can help a community? Where else could data analysis make a difference?"

### 评估方案

**学术评估：**
个人任务：给学生一份新的、陌生的真实数据集（例如来自慈善商店或无家可归者庇护所）。他们必须：清洗数据、计算关键统计量、制作恰当图表、识别规律并撰写简短报告。这检验了“迁移”——他们能否将在食物银行项目中学到的技能应用到新情境中？

**公民素养发展评估（不打分，但记录在案）：**
学生撰写一段反思："What did this project teach me that a textbook couldn't?" 教师从中寻找以下证据：同理心（理解数据背后的人文处境）、公民意识（理解社区需求）以及能动性（相信自己的技能可以带来改变）。

**社区反馈：**
食物银行经理提供书面反馈：分析是否准确？报告是否有用？他们是否会使用？这是最有意义的评估——不是“学生的数学做对了吗？”，而是“他们的数学工作是否产出了社区真正需要的东西？”

---

## 已知局限性

1. **服务性学习需要真实的社区伙伴关系，而这需要时间培养。** 上述食物银行项目假设存在一位愿意提供数据、接待参访并给予反馈的社区伙伴。寻找并维系此类伙伴关系是服务性学习最大的现实挑战之一。初次开展服务性学习的学校应从一位值得信赖的社区伙伴入手，逐步拓展。

2. **元分析显示服务性学习对学业成绩的效应量较为温和（d=0.27 — Celio et al., 2011）。** 服务性学习并非像提取练习或高质量反馈那样的高效应学业策略。它的核心价值在于将学术学习与公民发展、真实语境和学习动机融为一体，而不在于快速拉高考试分数。教师选择服务性学习，应当是因为它既培养公民又教授课程，而不是因为它是提升应试成绩最高效的方式。

3. **服务性学习与慈善施舍之间的界限至关重要，也极易踩错。** 如果学生因同情食物银行服务对象而站在优势地位去“施舍帮助”，项目就会强化而非挑战社会等级观念。上述反思结构正是为了防范这一点而设计——但教师必须时刻保持警觉。项目定位应当是伙伴协作，而非怜悯："We are providing data analysis skills that the food bank needs. They are providing us with real data and authentic purpose that we need. Both sides contribute, both sides benefit."
