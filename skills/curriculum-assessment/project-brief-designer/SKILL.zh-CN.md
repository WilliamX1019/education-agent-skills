---
# AGENT SKILLS STANDARD FIELDS (v2)
name: project-brief-designer
description: "设计项目式学习（PBL）简报，包含驱动性问题、里程碑与评估标准。适用于规划 PBL 单元、探究项目或延伸调查。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "curriculum-assessment/project-brief-designer"
skill_name: "项目简报设计器（PBL）"
domain: "curriculum-assessment"
version: "1.0"
evidence_strength: "moderate"
evidence_sources:
  - "Barron & Darling-Hammond (2008) — Teaching for meaningful learning: a review of research on inquiry-based and cooperative learning"
  - "Krajcik & Shin (2014) — Project-based learning: design features and key practices"
  - "Larmer, Mergendoller & Boss (2015) — Setting the Standard for Project Based Learning"
  - "Thomas (2000) — A review of research on project-based learning"
  - "Hmelo-Silver, Duncan & Chinn (2007) — Scaffolding and achievement in problem-based and inquiry learning"
input_schema:
  required:
    - field: "project_topic"
      type: "string"
      description: "项目所涉及的学科内容——学生将围绕什么展开学习"
    - field: "learning_objectives"
      type: "string"
      description: "学生通过项目应当发展的具体知识与技能"
    - field: "student_level"
      type: "string"
      description: "年龄/年级"
    - field: "project_duration"
      type: "string"
      description: "项目持续时长——例如 2 周、6 课时、半个学期"
  optional:
    - field: "subject_area"
      type: "string"
      description: "课程学科（跨学科项目可为多门学科）"
    - field: "real_world_connection"
      type: "string"
      description: "教师希望项目连接的具体真实世界情境、受众或问题"
    - field: "student_profiles"
      type: "array"
      description: "来自上下文引擎：包括先前学业水平、兴趣与特定需求在内的班级数据"
    - field: "available_resources"
      type: "string"
      description: "可用的技术、材料、社区联结与专业支持"
    - field: "curriculum_framework"
      type: "string"
      description: "来自上下文引擎：项目必须回应的相关课程标准"
output_schema:
  type: "object"
  fields:
    - field: "driving_question"
      type: "string"
      description: "贯穿整个项目驱动探究的开放性、真实问题"
    - field: "project_brief"
      type: "object"
      description: "学生收到的完整简报——情景、要求、里程碑与最终成品"
    - field: "milestone_sequence"
      type: "array"
      description: "带有显性教学节点的序列化检查点，确保学习通过项目真正发生"
    - field: "assessment_criteria"
      type: "object"
      description: "评估什么及如何评估——同时涵盖过程评估与成果评估"
    - field: "explicit_instruction_map"
      type: "array"
      description: "项目中何处需要显性教学——PBL 是与直接教学**协同**工作，而非替代它"
chains_well_with:
  - "backwards-design-unit-planner"
  - "competency-unpacker"
  - "criterion-referenced-rubric-generator"
  - "differentiation-adapter"
  - "scaffolded-task-modifier"
  - "curriculum-knowledge-architecture-designer"
  - "critical-thinking-task-designer"
teacher_time: "5 分钟"
tags: ["PBL", "project-based-learning", "inquiry", "driving-question", "authentic-assessment", "milestones"]
---

# 项目简报设计器（PBL）

## 本技能的作用

为项目式学习（PBL）设计一份完整的项目简报——包括驱动性问题、真实世界联结、结构化里程碑、显性教学节点以及评估标准——确保学生**通过**项目学到扎实的学科内容，而不仅仅是做出一个手工作品。核心设计原则在于：有效的 PBL 将真实的开放式探究与结构化教学结合起来；项目提供动机与语境，显性教学提供学生成功所需的知识与技能。输出是一份教师可直接发给学生的项目简报，外加一份面向教师的实施指南，标明何处需要直接教学、形成性评估与脚手架。AI 在此尤为关键，因为设计有效的 PBL 需要同时平衡真实性（让项目感觉真实）、严谨性（确保实质性学习发生）、结构性（设置防止跑偏的里程碑）与差异化（让所有学习者都能参与）——这是一项耗时且需要高度专业素养的多维设计挑战。

## 实证基础

Barron & Darling-Hammond（2008）综述了探究式学习证据，总结出区分有效项目与“有趣但教育浅薄的活动”的设计特征：有效 PBL 连接到有意义的真实世界问题、要求学科思维（而不仅仅是搜集信息）、包含结构化里程碑，并在学生需要新知识或技能的节点融入显性教学。他们发现，当 PBL 补充而非替代直接教学时效果最佳——项目提供了使教学有意义的语境，而教学提供了使项目得以推进的工具。Krajcik & Shin（2014）总结了有效 PBL 的五项核心特征：驱动性问题（真实、开放、锚定现实议题）、情境化探究（嵌入有意义语境的调查）、协作、学习技术以及有形制品。他们强调驱动性问题是设计核心——它必须真正开放（而非预设唯一答案的问题）、与学生生活相连，且足够丰富以支撑持续探究。Larmer、Mergendoller & Boss（2015）来自巴克教育研究所，确立了“黄金标准 PBL”框架，包含七大要素：有挑战性的问题、持续探究、真实性、学生话语权与选择权、反思、批判与修改，以及公开成果。Thomas（2000）综述了 PBL 研究，发现其对内容知识与问题解决有正向效应，但也警告设计拙劣的项目会耗费大量时间却未能产生相应学习——结构与显性教学正是区分二者的关键因素。Hmelo-Silver、Duncan & Chinn（2007）证明，带脚手架的探究优于无脚手架的探究——学生需要结构化支持，而不仅仅是开放式任务。

## 输入规范

教师必须提供：
- **项目主题（Project topic）：** 项目围绕什么展开。*例如：“本地河流的水质” / “设计可持续城市” / “工业革命对劳动人民的影响” / “发起减少学校食物浪费的倡议活动”*
- **学习目标（Learning objectives）：** 学生应当学会什么。*例如：“理解水污染的成因与指标、应用科学检测方法（pH、溶解氧、硝酸盐水平）、基于证据得出结论、向受众传达科学发现” / “分析关于工作条件的一手与二手史料、运用证据建构历史论证”*
- **学生水平（Student level）：** 年级。*例如：“八年级” / “十年级”*
- **项目时长（Project duration）：** 持续时间。*例如：“3 周内 6 课时” / “半个学期（12 课时）”*

可选项（如可用则由上下文引擎注入）：
- **学科领域（Subject area）：** 课程学科
- **真实世界联结（Real-world connection）：** 教师希望嵌入的具体现实情境
- **学生画像（Student profiles）：** 班级数据、兴趣、需求
- **可用资源（Available resources）：** 技术、材料、社区联结
- **课程框架（Curriculum framework）：** 需回应的标准

## 提示词（Prompt）

```
You are an expert in project-based learning design, with deep knowledge of Barron & Darling-Hammond's (2008) research on inquiry-based learning, Krajcik & Shin's (2014) five key features of effective PBL, and Larmer, Mergendoller & Boss's (2015) Gold Standard PBL framework. You understand that effective PBL is NOT simply "do a project" — it is a carefully designed learning experience where authentic inquiry and explicit instruction work together so that students learn substantive content THROUGH the project.

CRITICAL DESIGN PRINCIPLE: PBL effects are strongest when projects include explicit instruction, not instead of it (Barron & Darling-Hammond, 2008; Hmelo-Silver et al., 2007). Every project brief you design must include specific points where the teacher provides direct instruction, modelling, or scaffolding. A project without structured teaching is an activity, not PBL.

Your task is to design a project brief for:

**Project topic:** {{project_topic}}
**Learning objectives:** {{learning_objectives}}
**Student level:** {{student_level}}
**Project duration:** {{project_duration}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Subject area:** {{subject_area}} — if not provided, infer from the topic and objectives.
**Real-world connection:** {{real_world_connection}} — if not provided, design an authentic connection that makes the project meaningful to students at this level.
**Student profiles:** {{student_profiles}} — if not provided, design for a mixed-ability class.
**Available resources:** {{available_resources}} — if not provided, assume standard classroom resources with internet access but no specialist equipment.
**Curriculum framework:** {{curriculum_framework}} — if not provided, align to the stated learning objectives.

Apply these evidence-based PBL design principles:

1. **Design a driving question (Krajcik & Shin, 2014):**
   - The driving question must be OPEN-ENDED — it should not have a single correct answer.
   - It must be AUTHENTIC — connected to real-world issues, audiences, or problems that matter beyond the classroom.
   - It must be FEASIBLE — students at this level can meaningfully investigate it within the time available.
   - It must REQUIRE the intended learning — students cannot answer the question without developing the knowledge and skills in the learning objectives.
   - Avoid pseudo-questions that have predetermined answers. "How can we reduce water pollution in our local river?" is open. "What are the three types of water pollution?" is not.

2. **Structure milestones with explicit instruction (Barron & Darling-Hammond, 2008; Hmelo-Silver et al., 2007):**
   - Break the project into 3–5 milestones, each with a clear deliverable.
   - At each milestone, identify: what students produce, what they need to know/be able to do, and WHERE EXPLICIT INSTRUCTION HAPPENS.
   - Instruction should be "just in time" — taught when students need it for the next phase of the project, not front-loaded as a lecture block followed by a project block.
   - Each milestone should include a formative check — how does the teacher know students are learning, not just producing?

3. **Ensure authentic audience and purpose (Larmer et al., 2015):**
   - The final product should be FOR someone — a real audience, a genuine purpose.
   - "Present your findings to the class" is weak. "Present your water quality report to the local council environmental officer" is strong.
   - If a real audience isn't available, create a realistic scenario that simulates one.

4. **Build in student voice and choice (Larmer et al., 2015):**
   - Students should have meaningful choices within the project — which aspect to investigate, how to present findings, which evidence to prioritise.
   - Choice should be structured, not unlimited — too much choice overwhelms; too little removes ownership.
   - The learning objectives are non-negotiable; the route to them includes choice.

5. **Design assessment for both process and product (Barron & Darling-Hammond, 2008):**
   - Assess the LEARNING, not just the PRODUCT. A beautiful poster with no substantive content should not score well.
   - Include process assessment: research logs, draft work, peer feedback, reflection.
   - Assessment criteria should be transparent from the start — students should know how they'll be assessed before they begin.
   - Product quality matters, but content understanding matters more.

6. **Include reflection and revision (Larmer et al., 2015):**
   - Build in structured reflection points: "What have you learned so far? What questions do you still have?"
   - Build in revision opportunities: students improve their work based on feedback before final submission.
   - Critique and revision is where much of the learning happens — not in the first draft.

Return your output in this exact format:

## Project Brief: [Project Title]

**Driving Question:** [The open-ended question that drives the project]
**For:** [Student level]
**Duration:** [Project duration]
**Subject:** [Subject area(s)]

### The Scenario

[A compelling, authentic description of the project context — who needs this, why it matters, what students will produce. Written in language appropriate for the student level. This is what students actually read.]

### What You Will Produce

[Clear description of the final product(s) and who the audience is]

### Milestones

For each milestone:
**Milestone [N]: [Name] — [Timing]**
- **What you produce:** [Deliverable]
- **What you'll need to learn:** [Knowledge/skills required]
- **Teacher instruction point:** [What the teacher explicitly teaches at this stage and why]
- **Formative check:** [How the teacher assesses learning at this stage]
- **Student choice:** [Where students have meaningful choice within this milestone]

### Assessment Criteria

**Your project will be assessed on:**
[Clear, transparent criteria — what counts, what doesn't, how much each element is worth]

**Process assessment (how you work):**
[What process elements are assessed — research quality, collaboration, reflection, revision]

**Product assessment (what you produce):**
[What product elements are assessed — content accuracy, argument quality, communication effectiveness]

### Explicit Instruction Map (Teacher Guide)

[For each milestone: what the teacher needs to teach, when, and how. This ensures the project includes genuine instruction, not just facilitation.]

### Differentiation Notes

[How the project can be adapted for different learners — extension challenges, support scaffolds, EAL modifications — while maintaining the same learning objectives]

### Known Design Choices

[Transparent notes about trade-offs in the design — what was prioritised, what was sacrificed, what the teacher should watch for]

**Self-check before returning output:** Verify that (a) the driving question is genuinely open-ended and requires the intended learning, (b) every milestone includes an explicit instruction point, (c) assessment criteria are transparent and prioritise content learning over product aesthetics, (d) student voice and choice are structured within each milestone, (e) the project includes reflection and revision opportunities, and (f) the project could not be completed without substantive learning — it's not possible to produce a good product by copying information without understanding it.
```

## 示例输出

**情景：** *项目主题：“本地河流的水质” / 学习目标：“理解水污染的成因与指标、应用科学检测方法（pH、溶解氧、硝酸盐水平）、评价证据以得出结论、向非专业受众传达科学发现” / 学生水平：“八年级” / 项目时长：“4 周内 8 课时” / 学科领域：“科学” / 真实世界联结：“本地河流近期出现藻类暴发增多的报告——一个真实的本地议题”*

---

## 项目简报：河流健康调查

**驱动性问题：** 我们本地的河流有多健康，我们应当为此采取什么行动？
**适用对象：** 八年级科学
**时长：** 4 周内 8 课时
**学科：** 科学（融合地理与沟通表达元素）

### 项目情景

近几个月来，Arden 河附近的居民注意到水面上生长的绿藻越来越多，尤其是在 Millbrook 工业区附近。一些遛狗的居民报告说，他们的狗喝了河水后生病了。地方教区议会希望了解发生了什么——但他们缺乏科学专业知识。

他们需要一支科学家团队来：
1. 检测河流不同点位的水质
2. 查明导致问题的原因
3. 用通俗易懂的语言解释发现
4. 提出具体的行动建议

你们的团队已受托开展这项调查。你们的发现将整理成一份面向教区议会的科学报告——他们关心这条河流，但没有科学背景。你们的报告必须既**科学准确**，又能让非专业人士**完全读懂**。

### 你们将产出什么

**最终成果：** 一份提交给教区议会的科学报告（800–1200 词），包含：
- 附带数据的水质检测发现
- 对数据含义的清晰解释
- 关于河流健康状况的循证结论
- 具体的行动建议

**受众：** 教区议会（需要依据你们的发现做出决策的非专业成年人）

**展示：** 每个团队向全班做 5 分钟报告摘要汇报，教师扮演教区议会成员进行现场提问。

### 里程碑

**里程碑 1：理解水质——第 1–2 课时**
- **产出：** 一份研究摘要（1 页），识别水质的关键指标及影响因素。至少包含 4 项指标，并解释每项指标“健康”与“不健康”水平分别是什么样子。
- **需要学习的内容：** 水质在科学上的含义、核心指标（pH、溶解氧、硝酸盐/磷酸盐水平、生物指标）、河流污染成因以及什么是富营养化。
- **教师讲授节点：** 第 1 课时——关于水质指标的直接教学。教师讲解 pH、溶解氧、硝酸盐和磷酸盐，并用示意图展示过量营养盐如何引发藻华（富营养化）。这是学生无法在有限时间内独立发现的基础知识。第 2 课时——教师示范如何阅读和解读水质数据表，演示“正常”范围是什么样子以及如何发现异常读数。
- **形成性检查：** 第 2 课时末离堂小测：“一份河流水样显示 pH 6.2、溶解氧 4mg/L、硝酸盐水平 25mg/L。这条河健康吗？至少使用两项指标解释你的推理。”这检验学生能否解读数据，而不仅仅是背诵指标名称。
- **学生选择权：** 团队自选两项作为调查重点的指标（所有团队都必须涵盖 pH 与溶解氧；可根据兴趣自选额外聚焦指标）。

**里程碑 2：采集与记录数据——第 3–4 课时**
- **产出：** 一份完整的数据表，包含至少 3 个采样点的水质测量值，准确记录单位与重复测量值。
- **需要学习的内容：** 如何使用检测设备（pH 计、溶解氧探头、硝酸盐试纸）、如何设计公平实验（采样时控制变量）、如何在表格中准确记录数据。
- **教师讲授节点：** 第 3 课时——教师演示每种检测设备，示范正确操作流程与常见错误。学生在去河边前先用配制好的水样练习。这是一项需要显性示范的实操技能——学生无法靠瞎摸索学会使用溶解氧探头。第 4 课时——简短讲授公平实验：为什么要在同一深度采样、做重复读数并记录环境条件。这连接到控制变量的更广泛科学方法。
- **形成性检查：** 教师在数据采集期间巡视检查：读数是否带上了正确单位？学生是否进行了重复测量？学生能否解释**为什么**要在河流的多个点位采样？（如果学生解释不出原因，说明他们只是在机械走流程而不理解科学推理。）
- **学生选择权：** 团队基于自己关于“哪里污染可能最严重”的假设，在批准区域内自选采样点，并必须科学论证其选点理由。

**里程碑 3：分析证据与得出结论——第 5–6 课时**
- **产出：** 一份数据分析文档，包含：用恰当图表呈现的数据、对数据显示内容的书面解读，以及有证据支撑的河流健康结论。
- **需要学习的内容：** 如何为不同数据选择恰当图表类型、如何识别数据中的模式与异常值、如何撰写循证结论（主张 → 证据 → 推理）。
- **教师讲授节点：** 第 5 课时——教师使用样本数据集（**不是**学生自己的数据）示范如何分析水质数据。演示：对比不同点位选用柱状图 vs. 展示沿河变化选用折线图、识别模式含义（“随着我们从工业区向下游移动，溶解氧下降——这表明……”），以及区分相关与因果。第 6 课时——教师提供“主张-证据-推理（CER）”框架，并出声思考示范撰写一段结论，演示如何将数据连接到主张。
- **形成性检查：** 每个团队在第 6 课时结束前提交一段结论草稿（仅一段）。教师连夜审阅并给出针对性书面反馈，指出结论是否真正得到了所引证据的支撑。这是关键学习时刻——学生能否用数据支撑科学论证？
- **学生选择权：** 团队自选数据的视觉呈现方式（图表类型、排版、突出哪些对比）。同时自选在结论中重点强调哪些他们认为最重要的发现。

**里程碑 4：面向非专业受众沟通——第 7–8 课时**
- **产出：** 最终报告（800–1200 词）与 5 分钟展示摘要。
- **需要学习的内容：** 如何向非专业人士传达科学发现——在不失准确性的前提下将技术语言转化为通俗解释，为决策型受众组织报告结构。
- **教师讲授节点：** 第 7 课时——教师并排展示两段示例：一段写给科学家（“升高的 NO₃⁻ 浓度 28mg/L 提示存在人为富营养化”），一段写给教区议会（“河里的硝酸盐水平高于应有水平。硝酸盐就像藻类的肥料——当浓度超过 10mg/L 时，藻类就会失控疯长”）。学生找出差异并练习“翻译”自己分析中的一段话。这是一项需要示范的具体沟通技能。
- **形成性检查：** 第 7 课时同伴互评：每个团队阅读另一组的报告草稿并回答三个问题：（1）没有科学背景能看懂这些发现吗？（2）有清晰的行动建议吗？（3）哪一部分还需要更多解释？随后各组依据同伴反馈修改，于第 8 课时最终提交。
- **学生选择权：** 团队自选最终报告的版式与结构（在字数范围内），并自选展示方式（全员发言、一人主讲其他人答疑等）。

### 评估标准

**你的项目将从以下维度评估：**

**过程评估（占总分 30%）：**
- 研究质量（里程碑 1）：是否准确识别并解释了水质指标？（10%）
- 数据采集（里程碑 2）：数据记录是否准确、包含重复测量并带有正确单位？（10%）
- 反思与修改：是否根据同伴反馈改进了报告？做出了哪些具体修改及为什么？（10%）

**成果评估（占总分 70%）：**
- 科学准确性（25%）：发现是否正确？结论是否得到数据支撑？是否正确解释了水污染的科学原理？
- 循证论证（20%）：是否将数据用作证据？推理是否清晰？结论是否从证据推导而出？
- 面向受众的沟通（15%）：非专业人士能否读懂报告？是否在不失准确性的前提下转化了科学语言？
- 行动建议（10%）：建议是否具体、现实且基于研究发现？

**注意：** 报告的视觉美工设计**不予**评估。一份科学扎实但纯文本朴素的报告，得分高于设计华丽但科学薄弱的报告。请把时间花在理解与论证上，而不是装饰上。

### 显性教学图谱（教师指南）

| 课时 | 显性教学内容 | 目的 | 时间分配 |
|------|-------------|------|----------|
| 1 | 水质指标、富营养化过程 | 学生开展调查前所需的基础知识 | 25 分钟直接讲授 + 20 分钟引导研究 |
| 2 | 阅读并解读水质数据表 | 程序性技能：如何读懂数值数据 | 15 分钟示范 + 30 分钟样本数据练习 |
| 3 | 设备演示与公平实验 | 需要示范的实操技能——无法安全自学 | 20 分钟演示 + 25 分钟监督练习 |
| 4 | 简短回顾变量与采样设计 | 将实操与科学方法相连 | 10 分钟讲授 + 实地采样 |
| 5 | 数据分析：图表选择、模式识别 | 分析技能：从数据走向意义 | 20 分钟样本数据集示范 + 25 分钟引导分析 |
| 6 | 用于科学结论的 CER 框架 | 写作技能：组织循证论证 | 15 分钟示范 + 30 分钟带反馈起草 |
| 7 | 向非专业人士传达科学 | 沟通技能：受众意识 | 15 分钟示范 + 30 分钟修改润色 |
| 8 | —（学生展示与最终提交） | 评估与成果庆典 | — |

**显性教学总时长：** 8 课时中约 120 分钟。其余时间为结构化探究、协作工作与形成性评估。这**不是**“老师先讲 2 节课，然后学生自己做 6 节课项目”——教学贯穿全程，在学生需要时精准交付。

### 差异化说明

**拓展：** 提前完成里程碑的学生可以调查额外指标（如无脊椎动物多样性等生物指标）、将自己的发现与同类河流的公开数据对比，或为不同受众撰写第二版报告（例如给地理课学习河流的五年级学生看的版本）。

**支持：** 在第 1 课时前开展简短课前预习，提前教授水质词汇。提供已填好单位与列标题的数据记录模板。提供带有板块标题和每段句型开头的报告结构模板。这些脚手架结构化了输出，而未降低分析要求——学生依然必须自己解读数据并得出结论。

**EAL：** 提供附带日常语言定义的关键科学术语表。在书面解释旁配以富营养化过程的视觉示意图。允许学生在用英语写作前先用母语讨论发现。为 CER 段落提供句框：“Our data shows that ___. This suggests ___ because ___.”

**ADHD：** 将每节课的任务拆分为更短的片段，设置清晰的“完成”检查点。提供项目里程碑的视觉时间线。实地考察期间分配明确角色（设备管理员、数据记录员）以提供专注焦点与结构。

### 已知设计权衡

1. **河流情景基于真实的本地议题。** 如果河流/议题与你的本地情况不符，请调适情景——设计原则适用于任何真实环境议题。关键要求是问题必须是**真实的**（或真实模拟的），而非生造的。

2. **报告权重高于展示。** 报告占评估的 70%；展示是一项沟通练习，而非表现性评估。这避免了用公开演讲自信度替代科学理解的效度威胁（参见 `assessment-validity-checker`）。

3. **刻意将视觉设计排除在评估之外。** 这是一项有意选择，旨在防止学生把时间花在美化装饰而非科学探究上。同时它也消除了社会经济障碍（彩印、设计软件条件）和公平性障碍（不惩罚阅读障碍或精细动作困难的学生）。

4. **每个里程碑都要求显性教学。** 这是最重要的设计特征。PBL 研究一致表明，缺乏结构化教学的项目只能带来投入度而无法产出相应学习（Thomas, 2000）。如果拿掉这些教学节点，项目就会沦为普通活动——学生会从网站复制粘贴信息拼凑报告，而不是真正理解科学。

5. **四周是本项目的最低可行时长。** 更短的时间线要么迫使砍掉数据采集（移除了真实探究），要么砍掉修改周期（移除了关键学习机会）。如果时间受限，应减少采样点数量，而非砍掉里程碑。

---

## 已知局限

1. **PBL 的质量高度依赖于驱动性问题。** 生成的驱动性问题力求开放、真实并需要预期学习——但教师应评估它是否真正能打动自己的特定学生。在一个班级奏效的问题，在另一个班级可能反响平平。教师可能需要调适驱动性问题以贴近学生兴趣与本地语境。

2. **真实世界联结需要本地知识。** 项目简报基于给定主题与现实联结生成情景，但教师比任何 AI 都更了解自己的社区、本地资源与潜在外部合作伙伴。生成的情景应被视为强有力的起点，经本地化调适（将通用细节替换为具体地名、场所与议题）后效果更佳。

3. **PBL 并不适用于所有学习目标。** 有些内容更适合通过直接教学、练习与提取来教授——尤其是学生在开展调查前所需的基础知识（Hmelo-Silver et al., 2007）。PBL 最适合涉及应用、分析、评价与沟通的目标——而不适合主要旨在习得事实性知识的目标。教师在使用本技能前，应先判断 PBL 是否适合既定目标。

4. **显性教学图谱是指南，而非死剧本。** 建议的教学节点指明了**何处**需要教学，但无法规定适用于每个班级的唯一教学法。教师必须运用专业判断决定讲授多少、如何回应项目中浮现的迷思概念，以及何时暂停项目以补充原设计未预见到的教学。
