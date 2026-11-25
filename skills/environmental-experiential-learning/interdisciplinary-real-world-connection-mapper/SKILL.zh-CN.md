---
# AGENT SKILLS STANDARD FIELDS (v2)
name: interdisciplinary-real-world-connection-mapper
description: "为现实世界问题或真实情境绘制跨学科课程连接图谱。适用于规划跨学科项目或将教学内容与现实议题相联系时。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "environmental-experiential-learning/interdisciplinary-real-world-connection-mapper"
skill_name: "跨学科现实连接映射器"
domain: "environmental-experiential-learning"
version: "1.0"
evidence_strength: "moderate"
evidence_sources:
  - "Barron & Darling-Hammond (2008) — Teaching for Meaningful Learning: a review of research on inquiry-based and cooperative learning"
  - "Drake & Burns (2004) — Meeting Standards Through Integrated Curriculum"
  - "Beane (1997) — Curriculum Integration: designing the core of democratic education"
  - "Rennie, Venville & Wallace (2012) — Integrating Science, Technology, Engineering, and Mathematics"
  - "Czerniak, Weber, Sandmann & Ahern (1999) — Literature review of science and mathematics integration"
input_schema:
  required:
    - field: "real_world_problem"
      type: "string"
      description: "需要多个学科共同应对的现实问题、议题或情境"
    - field: "primary_subject"
      type: "string"
      description: "教师自身的学科——发起这一跨学科连接的学科起点"
  optional:
    - field: "student_level"
      type: "string"
      description: "年龄/年级"
    - field: "available_subjects"
      type: "string"
      description: "哪些其他学科教研组愿意或能够参与协作"
    - field: "curriculum_constraints"
      type: "string"
      description: "每个学科必须覆盖的课程内容"
    - field: "time_frame"
      type: "string"
      description: "整合单元的持续时间"
    - field: "school_timetable"
      type: "string"
      description: "学校课表是否允许跨学科协作，还是各学科完全分科孤立"
output_schema:
  type: "object"
  fields:
    - field: "connection_map"
      type: "object"
      description: "展示现实问题如何连接多个学科的视觉与文字图谱"
    - field: "disciplinary_contributions"
      type: "array"
      description: "每个学科贡献什么——具体的知识与技能，以及课程标准对齐"
    - field: "integration_points"
      type: "array"
      description: "各学科在何处以及如何真正融合——不是平行教学，而是实质性整合"
    - field: "implementation_plan"
      type: "object"
      description: "如何实施——从单科教师自发连接，到全面的跨学科协作"
    - field: "assessment_approach"
      type: "object"
      description: "如何评估整合性理解——不是分科考核，而是评估综合运用多学科的能力"
chains_well_with:
  - "phenomenon-based-unit-anchor"
  - "project-brief-designer"
  - "service-learning-project-designer"
  - "ecological-inquiry-anchor-designer"
teacher_time: "4 分钟"
tags: ["interdisciplinary", "cross-curricular", "Barron", "Drake", "integrated-curriculum", "real-world", "PBL"]
---

# 跨学科现实连接映射器

## 本技能的作用

绘制现实世界问题或情境与解决该问题所需学科知识之间的连接图谱，生成一份实用的课程整合计划，展示每个学科的贡献、各学科真正交汇的连接点，以及如何在真实的学校课表限制下实施整合。该方法借鉴了 Barron & Darling-Hammond (2008) 关于探究式和有意义学习的研究，以及 Drake & Burns (2004) 的整合课程设计框架。核心洞察在于：现实世界的问题本质上是跨学科的——气候变化不只是“科学”，无家可归问题不只是“公民与心理健康课（PSHE）”，建筑项目不只是“数学”——学会综合运用多个学科来应对复杂问题的学生，比孤立学习每个学科的学生能形成更深层次的理解。然而，整合必须是“真实的”（每个学科都贡献不可或缺的内容），而不是“牵强的”（流于表面的虚假联系反而稀释了两个学科的深度）。输出包括连接图谱、附带课程对齐的学科贡献、具体整合点、实用实施计划以及评估方案。AI 在此尤为有价值，因为将一个现实问题同时映射到多个学科课程标准上，需要跨越多个学科领域的知识交叉索引——这项工作如果由教师个人跨部门沟通，往往需要耗费数小时。

## 循证基础

Barron & Darling-Hammond (2008) 综述了关于探究式和合作学习的研究，发现当学生将多学科知识应用于真实问题时，学习会更加深入。他们总结了有效跨学科教学的设计原则：问题必须真正复杂（需要多重视角）、每个学科的贡献必须具有实质性（不能流于形式），而且整合必须对学生可见（学生应当理解“为什么”需要多个学科）。Drake & Burns (2004) 提出了课程整合的三个层次：多学科（multidisciplinary，各学科围绕同一主题但保持独立）、跨学科（interdisciplinary，在各学科间强调共同技能或概念）以及超学科（transdisciplinary，由现实情境组织学习，学科服务于情境）。他们认为，超学科层次的整合最有效，但跨学科层次最具可操作性——而任何层次的整合都胜过完全孤立。Beane (1997) 从民主教育原则出发倡导课程整合：现实世界的问题不会按学科打包出现，公民需要综合运用多个知识领域才能有效参与民主生活。Rennie, Venville & Wallace (2012) 专门研究了 STEM 整合，发现整合能提升学生的参与度与相关性感知，但必须精心设计以避免“稀释”单个学科。Czerniak 等 (1999) 综述了科学与数学的整合，发现其对学生态度有积极影响，对学业成就有中等正向影响，但也警告称设计不当的整合可能会削弱两个学科的理解深度。

## 输入模式

教师必须提供：
- **Real-world problem（现实世界问题）：** 真实情境。*例如："Our school wants to reduce its energy consumption by 20% — how?" / "A local developer wants to build houses on the green space behind the school — should the council approve it?" / "Water quality in the local river is declining — what's causing it and what can be done?" / "Our community has a food waste problem — where does the waste come from and how can it be reduced?"*
- **Primary subject（主学科）：** 教师所教学科。*例如："I'm a Science teacher" / "I'm a Geography teacher" / "I'm a Maths teacher" / "I'm a DT teacher"*

可选（如上下文引擎可用则自动注入）：
- **Student level（学生水平）：** 年级
- **Available subjects（可用学科）：** 哪些教研组可以协作
- **Curriculum constraints（课程限制）：** 各学科必须教授的内容
- **Time frame（时间跨度）：** 持续时间
- **School timetable（学校课表）：** 协作可能性

## Prompt

```
You are an expert in interdisciplinary curriculum design, with deep knowledge of Barron & Darling-Hammond's (2008) research on meaningful learning, Drake & Burns' (2004) framework for integrated curriculum (multidisciplinary, interdisciplinary, transdisciplinary), Beane's (1997) democratic argument for curriculum integration, Rennie, Venville & Wallace's (2012) STEM integration research, and Czerniak et al.'s (1999) science-mathematics integration review. You understand that interdisciplinary teaching is NOT "themed weeks" where subjects coincidentally address the same topic — it is the deliberate design of learning where multiple disciplines genuinely contribute to understanding a complex real-world problem.

CRITICAL PRINCIPLES:
- **The problem must genuinely require multiple disciplines.** If the problem can be fully addressed by one subject, integration is unnecessary and artificial. A genuine interdisciplinary problem is one where removing any contributing subject leaves the understanding incomplete.
- **Each subject's contribution must be SUBSTANTIVE, not tokenistic.** "Let's do fractions about the environment" is tokenistic — Maths is being used as a surface-level illustration, not contributing substantive mathematical thinking. "Analyse the energy consumption data using percentage change to determine which areas of the school waste the most energy" is substantive — Maths provides analytical tools that are genuinely needed.
- **Integration points must be SPECIFIC and IDENTIFIED.** Vague integration ("these subjects relate to the same topic") produces parallel teaching, not integrated learning. Specific integration ("the Science investigation produces data that the Maths analysis uses to draw conclusions that the Geography contextualises") produces genuine cross-disciplinary understanding.
- **Start from where the school IS, not where it should be.** Full transdisciplinary integration requires timetable flexibility, team planning time, and cross-departmental collaboration. Many schools have none of these. The implementation plan must offer a spectrum: from single-teacher connections (a Science teacher referencing Maths concepts) to full cross-curricular projects (multiple departments coordinating a shared unit).
- **Integration should STRENGTHEN individual subjects, not dilute them.** The most common criticism of interdisciplinary teaching is that it produces shallow understanding of multiple subjects rather than deep understanding of one. Good integration does the opposite: students learn MORE deeply about supply-demand dynamics when they encounter them through a real economic problem, not less deeply.

Your task is to map the interdisciplinary connections for:

**Real-world problem:** {{real_world_problem}}
**Primary subject:** {{primary_subject}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Student level:** {{student_level}} — if not provided, design for lower secondary (Years 7–9).
**Available subjects:** {{available_subjects}} — if not provided, identify the 3–4 most relevant subjects.
**Curriculum constraints:** {{curriculum_constraints}} — if not provided, identify natural curriculum alignment.
**Time frame:** {{time_frame}} — if not provided, design for a 2-week unit.
**School timetable:** {{school_timetable}} — if not provided, provide implementation options for both collaborative and siloed timetables.

Return your output in this exact format:

## Interdisciplinary Connection Map: [Problem]

**Real-world problem:** [The authentic situation]
**Primary subject:** [The teacher's discipline]
**Connected subjects:** [Other subjects that contribute]
**Integration level:** [Multidisciplinary / Interdisciplinary / Transdisciplinary — and why]

### Connection Map

[Visual or descriptive map showing how the problem connects to each subject — what each contributes]

### Disciplinary Contributions

For each subject (3–5):
**[Subject]: [What it contributes]**
- **Knowledge:** [Specific content students learn through this problem]
- **Skills:** [Disciplinary skills developed]
- **Curriculum alignment:** [How this addresses specific curriculum requirements]
- **Why this subject is necessary:** [What understanding would be missing without it]

### Integration Points

[Specific, identified points where one subject's output becomes another's input — the moments of genuine cross-disciplinary connection]

### Implementation Plan

**Option A — Single teacher (no cross-departmental collaboration needed):**
[How one teacher can make connections to other subjects within their own teaching]

**Option B — Coordinated teaching (subjects teach the same problem simultaneously but in their own lessons):**
[How 2–3 teachers coordinate timing and share the problem context]

**Option C — Full collaboration (subjects co-plan and co-teach):**
[How a full cross-curricular project could work if the school supports it]

### Assessment Approach

[How to assess integrated understanding — a task that requires drawing on multiple disciplines]

**Self-check before returning output:** Verify that (a) the problem genuinely requires multiple disciplines, (b) each subject's contribution is substantive, (c) integration points are specific and identified, (d) the implementation plan is realistic with multiple options, and (e) the integration strengthens rather than dilutes individual subjects.
```

## 示例输出

**场景：** *Real-world problem: "Our school wants to reduce its energy consumption by 20% over the next year. The headteacher has asked students to investigate where energy is used, identify the biggest opportunities for reduction, and propose a realistic action plan." / Primary subject: "I'm a Science teacher — Year 9" / Available subjects: "Maths, Geography, and DT are all interested. English has said they could contribute if we need persuasive writing." / Time frame: "3 weeks — approximately 15 lessons across the involved subjects"*

---

## 跨学科连接图谱：校园节能降耗

**现实世界问题：** 将学校能耗降低 20%——调查、分析并提出行动方案
**主学科：** 科学（九年级）
**关联学科：** 数学、地理、设计与技术（DT）、英语
**整合层次：** 跨学科（Interdisciplinary）——各学科保持其学科严谨性，但围绕共享问题进行协调。在最终提案阶段接近超学科（Transdisciplinary），要求学生综合所有学科的成果。

### 连接图谱

```
                    校园能源问题
                           |
        ┌──────────┬───────┴───────┬──────────┐
        │          │               │          │
      科学        数学            地理        设计与技术
   （能源如何    （数据分析      （能源背景    （设计解决
    运作，审计    与建模）        ——全球与     方案——保温、
    建筑能耗）                    本地）       照明、控制）
        │          │               │          │
        └──────────┴───────┬───────┴──────────┘
                           │
                         英语
                  （传达提案——
                   说服校长）
```

### 学科贡献

**科学：能源在我们学校是如何运作的？**
- **知识：** 能量形式、能量传递、绝热保温、电能消耗、供暖系统。学生学习学校“为什么”消耗能源（供暖、照明、计算机、烹饪），以及能源如何被浪费的科学原理（墙体、窗户、屋顶的热量散失；待机功耗；低效照明）。
- **技能：** 科学调查（开展能源审计）、测量（温度记录、电表读数）、假设检验（"Which room loses heat fastest and why?"）
- **课程对齐：** 九年级物理——能量转移、能量守恒、热绝缘、功率与能量计算
- **为何该学科不可或缺：** 没有科学，学生就无法理解能源使用和损耗的物理机制。他们可能知道学校用了很多电，但不理解能源去哪儿了或为什么会损耗——这意味着他们的提案只能是猜测，而不是工程方案。

**数学：能耗有多少，节能效果如何量化？**
- **知识：** 百分比变化（计算 20% 的降幅）、数据分析（阅读和解读能源账单）、统计图表（能耗随时间变化的柱状图、折线图）、比例推理（单位成本、估算节能规模）、财务建模（干预成本与长期节余对比）
- **技能：** 数据收集与分析、百分比计算、绘制与解读图表、财务建模（简单投资回收期计算）
- **课程对齐：** 九年级数学——百分比、数据处理、比例、真实数据集的解读
- **为何该学科不可或缺：** 没有数学，能源问题只能停留在模糊描述（“我们用得太多了”）。有了数学，学生就能量化："Heating accounts for 62% of our energy bill. If we improve roof insulation, we could reduce heating costs by 18%, saving approximately £4,200 per year. The insulation would cost £12,000, so it pays for itself in 2.9 years." 数字让提案具有可信度，让决策基于证据。

**地理：语境中的能源——为什么这件事重要？**
- **知识：** 能源来源（学校电力从何而来——国家电网、化石燃料、可再生能源）、碳足迹（将能耗换算为二氧化碳排放量）、全球能源不平等（我校生均能耗 X 千瓦时；肯尼亚一所学校为 Y）、可持续发展（SDG 7：经济适用的清洁能源）
- **技能：** 地理探究、跨尺度比较（本地学校 → 国家能源政策 → 全球能源不平等）、批判性评估数据来源
- **课程对齐：** 九年级地理——能源资源、可持续发展、发展差异、环境管理
- **为何该学科不可或缺：** 没有地理，能源问题就只是纯技术问题。地理提供了“语境”：为什么节能除了省钱之外还如此重要？我们的能源消耗会带来什么环境后果？我们的处境与其他国家的学校相比如何？地理将项目从单纯的工程练习转化为可持续发展探究。

**设计与技术（DT）：我们可以建造什么解决方案？**
- **知识：** 隔热材料与特性、LED 照明设计、基础电子学（定时器、传感器、控制装置）、可持续设计原则、面向环境性能的材料选择
- **技能：** 设计流程（识别问题 → 研究 → 设计 → 原型制作 → 测试 → 评估）、原型制作、技术绘图、材料测试
- **课程对齐：** 九年级设计与技术——材料、设计中的可持续性、系统与控制
- **为何该学科不可或缺：** 没有设计与技术，学生只能发现问题，却无法设计解决方案。设计与技术将项目从分析（“我们学校浪费能源”）推向行动（“这是我们可以实际安装的门窗防风条/人体感应照明开关/窗户隔热板原型”）。

**英语：我们如何说服校长？**
- **知识：** 说服性写作技巧（信誉 ethos、情感 pathos、逻辑 logos）、报告写作（正式语域、结构化论证）、演讲技巧（向决策者推介方案）
- **技能：** 说服性写作、受众意识、正式语域、用证据构建论证
- **课程对齐：** 九年级英语——面向特定目的与受众写作、说服技巧、非虚构写作
- **为何该学科不可或缺：** 学生的提案需要“说服”校长和校董会。一个技术上再出色但表达混乱的提案也会失败。英语提供了让其他学科贡献得以落地的沟通能力。

### 整合连接点

| 整合点 | 学科 A 产出…… | 学科 B 利用它来…… |
|---|---|---|
| **能源审计数据** | 科学课开展审计（温度读数、电表数据、热量散失观察） | 数学课分析数据（百分比构成、图表、趋势分析） |
| **量化节能效益** | 数学课计算每项干预措施的潜在节余（千瓦时与英镑） | 设计与技术课利用节余数据排定方案设计优先级（高影响力优先） |
| **碳排放语境** | 地理课计算当前能耗的碳足迹 | 科学课借此解释不同能源的环境影响 |
| **原型性能测试** | 设计与技术课测试隔热原型材料并测量效果 | 科学课利用能量传递原理评估测试结果 |
| **最终提案** | 所有学科共同提供证据与分析 | 英语课将提案结构化为面向校长的说服性文件 |

### 实施计划

**方案 A——单科教师（无需跨教研组协作）：**
科学教师在自己的科学课内完成以下安排：
- 将能源审计作为科学调查开展（第 1–2 周）
- 纳入基础数据分析，同时明确提及数学概念："We need to calculate percentage change — you've done this in Maths"
- 引入地理语境："Our school's energy use contributes to carbon emissions — you may be studying this in Geography"
- 将说服性提案设为家庭作业："Write a letter to the headteacher recommending ONE change, with evidence from your audit"

这不需要任何跨部门协调。科学教师在自己的课堂中主动建立与其他学科的联系，而不要求其他学科必须参与。

**方案 B——协调教学（4 个学科在各自课堂同步围绕同一问题教学）：**
四个学科在相同的 3 周时间窗口内，各自在自己的课时中教授校园能源问题：
- **第 1 周：** 科学课开展能源审计。数学课开始分析学校能源账单数据。地理课从全球视角引入能源议题。设计与技术课开始调研隔热和照明方案。
- **第 2 周：** 科学课通过共享电子表格将审计数据交给数学课。数学课分析并可视化数据。地理课使用该数据计算碳足迹。设计与技术课根据科学和数学的发现设计原型方案。
- **第 3 周：** 设计与技术课测试原型。数学课计算投资回收期。英语课帮助学生撰写正式提案。所有学科共同支持最终展示。

这需要：单元开始前召开一次 30 分钟的跨学科备课会、一个用于存放数据的共享数字文件夹，以及大致的进度同步（科学课第 1 周的审计必须在数学课第 2 周的分析之前完成）。

**方案 C——全面协作（协同备课与联合授课）：**
各学科在关键课节合并授课：
- 科学 + 数学联合讲授能源审计（科学提供方法论，数学提供分析工具）
- 地理 + 英语联合指导提案写作（地理提供环境语境，英语提供沟通框架）
- 设计与技术 + 科学联合指导原型测试（设计与技术负责制作，科学负责测量）
- 最终展示设为联合专场，学生小组向校长现场汇报（真实受众）

这需要：课表灵活性、共享备课时间以及学校领导层的支持。这是效果最强的方案，但在组织上也最具挑战性。

### 评估方案

**能源行动提案（整合性评估）：**

学生小组向校长提交一份正式提案，建议采取具体行动将学校能耗降低 20%。提案必须包含：

1. **能源审计证据**（科学）：我们测量了什么、发现了什么、能源在哪里被浪费
2. **数据分析**（数学）：量化的节余、图表、投资回收期计算
3. **环境语境**（地理）：为什么这很重要——碳足迹、全球背景
4. **附带原型的解决方案**（设计与技术）：我们推荐什么、如何设计、测试结果如何
5. **说服性沟通**（英语）：正式语域、结构化论证、清晰建议

提案按以下维度评估：证据准确性、分析质量、语境深度、方案可行性以及表达清晰度。每个学科评估其学科贡献；整合能力则通过整体提案的质量来评估。

**真正的检验：** 校长是否采纳了提案？当学生向拥有真正决策权的真实受众汇报时，评估就具备了真实的利害关系。

---

## 已知局限性

1. **跨学科整合在中学阶段存在结构性困难。** 分科课表、教研组壁垒、各自独立的备课时间以及教师个人考核机制，都与跨学科整合背道而驰。上述三套实施方案正视了这一现实——方案 A 在任何学校都能落地，而方案 C 需要许多学校并不具备的高度结构灵活性。

2. **如果设计不当，整合会稀释单个学科（Czerniak et al., 1999）。** 最常见的失败模式是各学科对共享问题只作出浅尝辄止的表面贡献，而非实质性贡献。“在数学课上算算环保百分比”（一节课、低挑战）远不如“运用百分比变化、统计图表和财务建模分析真实的学校能源数据”（多节课、真正的数学思维）。每个学科在整合语境中都必须守住自身的学科标准。

3. **并非所有现实问题都与所有学科同等契合。** 上述能源问题自然连接科学、数学、地理、设计与技术和英语，但它与音乐、体育或外语并不天然契合。强行拉拢不能自然做出贡献的学科，反而会削弱整合的质量。让四个学科实现真正的深度整合，远胜于把八个学科生硬地拼凑在一起。
