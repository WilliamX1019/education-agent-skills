---
# AGENT SKILLS STANDARD FIELDS (v2)
name: developmental-band-system-designer
description: "设计映射学生从幼儿期到高中高年级成长轨迹的发展阶段系统。适用于为学校或项目构建基于能力的课程架构。"
disable-model-invocation: true
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "original-frameworks/developmental-band-system-designer"
skill_name: "发展阶段系统设计器"
domain: "original-frameworks"
version: "1.0"
evidence_strength: "emerging"
evidence_sources:
  - "Manning — Developmental band system (original, active implementation at REAL School Budapest)"
  - "Piaget (1952) — The origins of intelligence in children (developmental stages as rationale)"
  - "Vygotsky (1978) — Mind in society (ZPD applied to band-level specification)"
  - "Wiggins & McTighe (2005) — Understanding by Design (backwards design, extended with upstream 'why' layer)"
  - "Mixed-age grouping research (Lillard 2005, Montessori) — bands support rather than undermine mixed-age learning"
input_schema:
  required:
    - field: "school_mission"
      type: "string"
      description: "学校或项目的核心宗旨与价值观——课程必须服务的目标"
    - field: "age_range"
      type: "string"
      description: "阶段系统需要覆盖的完整年龄范围"
    - field: "programme_context"
      type: "string"
      description: "学习形态——项目式学习、分科教学、混合模式或其他"
  optional:
    - field: "existing_competency_framework"
      type: "string"
      description: "正在映射的任何现有框架——欧盟框架（GreenComp、EntreComp、LifeComp、DigComp）、UNESCO、国家课程或其他"
    - field: "mixed_age_groupings"
      type: "string"
      description: "学校是否采用混龄学习小组"
    - field: "subject_exceptions"
      type: "string"
      description: "需要比宽泛阶段更精细颗粒度的学科——通常是数学与语言习得"
output_schema:
  type: "object"
  fields:
    - field: "band_architecture"
      type: "object"
      description: "阶段数量、年龄/年级映射以及每个阶段划分的发展学理"
    - field: "developmental_rationale"
      type: "object"
      description: "为什么阶段划分在这些节点——认知与社会情感发展推理"
    - field: "competent_definition_logic"
      type: "object"
      description: "如何界定“胜任”在每个阶段的含义——不是主题列表，而是能力的发展性描述"
    - field: "exception_handling"
      type: "object"
      description: "哪些学科需要更精细的颗粒度及原因，附9级或类似精细系统的指导"
    - field: "mixed_age_implications"
      type: "object"
      description: "阶段系统如何支持而非削弱混龄学习"
    - field: "known_limitations"
      type: "object"
      description: "阶段划分较宽泛——部分学生会显著超前或滞后于所在阶段。如何诚实应对这一点"
chains_well_with:
  - "learning-target-authoring-guide"
  - "coherent-rubric-logic-builder"
  - "self-determined-project-design-protocol"
  - "curriculum-knowledge-architecture-designer"
  - "kud-knowledge-type-mapper"
  - "scope-and-sequence-designer"
teacher_time: "6 分钟"
tags: ["developmental-bands", "competency", "Manning", "curriculum-design", "Piaget", "backwards-design", "mixed-age", "band-system"]
---

# 发展阶段系统设计器

## 本技能的功能

本技能编码了由教育者、课程设计师及学习系统设计师 Gareth Manning 开发的原创实践者框架。与其他领域的技能不同，它并非源自同行评审研究传统，而是植根于对学习科学的深入研习、原创课程设计工作以及一线课堂测试。将其纳入本库，是因为该方法论逻辑连贯、可迁移且真正实用——同时出于学术诚实，需将实践者框架与经研究验证的方法加以区分。

本技能为基于能力的课程设计一套发展阶段（developmental band）系统——该框架明确“胜任（competent）”在每个宽泛发展阶段而非单个年级上的具体表现。它解决了大多数能力框架所忽视的一个难题：6岁儿童的“胜任”与12岁儿童的“胜任”之间的差异。UNESCO AI 能力框架、大多数国家课程文件以及 GreenComp、EntreComp 等框架在列出能力时均缺乏发展特异性——导致教师只能自行猜测“展现批判性思维”在7岁与14岁时分别意味着什么。其结果要么是不切实际的模糊期望，要么是伪装成发展进阶的任意主题清单。阶段系统通过将年龄归入宽泛的发展阶段（通常为4个，大致对应皮亚杰阶段）并在**每个**阶段明确界定“胜任”，解决了这一问题——既创造了扁平能力清单所缺乏的发展精确度，又避免了逐年标准的颗粒度过载。输出是一套面向学校或项目的完整阶段架构，包括阶段数量、发展学理、年龄/年级映射、界定各阶段“胜任”含义的逻辑，以及对需要比宽泛阶段更精细颗粒度学科的指导。

## 循证基础

Manning 在布达佩斯 REAL School 的课程设计工作中开发了这一阶段系统，旨在解决一个具体实践难题：当学校采用基于能力的课程（尤其是采用项目式学习与混龄分组的学校）时，需要知道“胜任”在不同发展阶段长什么样——但现有能力框架并未提供这一点。例如，一所使用 GreenComp 的学校会发现，框架指定“拥抱复杂性与可持续性”为一项能力，却未说明这对6岁孩子与14岁孩子分别意味着什么。阶段系统填补了这一空白。皮亚杰（Piaget, 1952）的认知发展阶段提供了发展锚定，用作学理依据而非僵化教条：A阶段（约5–7岁）对应前运算晚期——具体、自我中心、基于知觉；B阶段（约8–10岁）对应具体运算期——对具体事物的逻辑运算、分类、序列化；C阶段（约10–12岁）对应形式运算早期——萌芽的抽象推理、假设性思考；D阶段（约12–14岁）对应发展中的形式运算期——系统性推理、元认知、抽象分析。这些只是大致对应，而非死板规定——任何年龄组内部的发展差异都很大。Wiggins 与 McTighe（2005）提供了 Manning 所拓展的逆向设计框架。标准 UbD 从课程目标开始逆向推进：目标 → 评估 → 教学。Manning 的拓展增加了一个上游的“为什么”层级：使命 → 价值观 → 课程必须优先什么 → 课程必须**不**优先什么 → 能力选择 → 学习目标拆解 → 阶段界定。这种“使命驱动的逆向设计”意味着每条阶段陈述都可以追溯回学校的使命。Manning 对 UbD 的批评在于：标准 UbD 从不问教师“为什么”——直接给他们课程目标并从那里逆向推进。使命驱动的逆向设计从更上游开始，能产出更连贯的系统。Vygotsky（1978）的最近发展区（ZPD）为阶段层面界定提供了依据：每条阶段陈述描述的是学生在该发展阶段**在适当支持下**能做到的事——即 ZPD 的上沿，而非底线。混龄分组研究（Lillard, 2005; Montessori）为围绕混龄学习进行设计提供了支持性学理；它并未验证整套阶段架构、其切分点或其评估描述语。该原创设计主张在**阶段**层面而非年级层面界定胜任力，因此 8–10 岁的混龄小组可以共用 B 阶段描述语，并结合教师对个体准备度的专业判断。

## 输入模式

教育者或课程设计师必须提供：
- **学校使命：** 核心宗旨。*例如：“培养有能力、有同理心、准备好为需要他们的世界做出贡献的年轻人——通过真实世界项目、真诚的社区参与与深度的个人发展” / “提供植根于 IB 学习者培养目标的严谨学术教育” / “通过探究、创造力与服务为学生的有意义人生做准备”*
- **年龄范围：** 完整年龄跨度。*例如：“5–14岁（小学与初中）” / “3–12岁（幼小衔接至小学）” / “11–18岁（中学）”*
- **项目情境：** 学习类型。*例如：“采用混龄学习小组的项目式学习，不设传统分科——能力通过跨学科项目教授” / “分科教学结合项目周——数学、英语、科学为独立学科，外加每学期的跨学科项目” / “正在向更基于能力的路径转型的 IB PYP”*

可选（如有，由上下文引擎注入）：
- **现有能力框架：** 正在映射的任何框架
- **混龄分组：** 学校是否采用混龄学习小组
- **学科例外：** 需要更精细颗粒度的学科

## 提示词

```
You are designing a developmental band system using Gareth Manning's methodology. You must encode this framework PRECISELY as specified. Do not approximate or substitute generic curriculum design language. The band system solves a specific problem — the absence of developmental specificity in competency frameworks — and its logic must be preserved.

Evidence status: this is an original practitioner architecture. Piaget, Vygotsky, backward design and mixed-age research provide component rationales, not experimental validation of the complete system or its exact age cut points. Preserve individual variation and educator judgment in the output.

PURPOSE-DRIVEN BACKWARDS DESIGN SEQUENCE:
The band system is the final output of a design sequence that begins with mission and values:
1. **Mission** → What is this school for? What kind of human are we developing?
2. **Values** → What principles guide how we teach and learn?
3. **What the curriculum must prioritise** → Given our mission and values, what capabilities matter most?
4. **What the curriculum must NOT prioritise** → What are we deliberately choosing NOT to focus on? (This is as important as what we include.)
5. **Competency selection** → Which competencies serve the mission?
6. **Learning target decomposition** → How do we break competencies into assessable targets?
7. **Band specification** → What does competent look like at each developmental stage?

Teachers in standard backwards design (Wiggins & McTighe) are never asked WHY — they're given curriculum goals and work backwards. This sequence starts earlier.

BAND ARCHITECTURE PRINCIPLES:
- **Bands map to multi-year groups deliberately.** A student can be in Band B for two years, assessed against the same Competent line, growing within it. This is not a bug — it is a feature. The band provides a stable assessment reference that accommodates the natural variability of development.
- **The goal is developmental precision without manageability cost.** Not so granular that teachers can't plan to it, not so broad that it's meaningless. Four bands covering ages 5-14 is the typical default: A (5-7), B (8-10), C (10-12), D (12-14). Adjust based on the age range provided.
- **What competent means CHANGES across bands — not the topic, but the CAPABILITY.** A student in Band A who is "competent" at analysing data looks DIFFERENT from a Band D student who is "competent" at analysing data. Band A: "I can sort objects into groups using one given criterion." Band D: "I can analyse a dataset to identify patterns, outliers, and possible explanations." Same competency, different developmental expression.
- **"Spiky learners" over "well-rounded students."** The band system supports depth and strength, not uniformity. A student who is Band D in science and Band B in writing is not broken — they are developing unevenly, which is normal. The system should support this rather than forcing all dimensions to the same level.

CRITIQUE OF FLAT COMPETENCY LISTS:
Encode why this problem matters. UNESCO, GreenComp, EntreComp, LifeComp, DigComp — these frameworks list competencies without developmental specificity. A teacher reading "Demonstrates systems thinking" has no idea what this means for a 7-year-old. The cost: teachers either (a) set expectations too high (using the framework's adult-facing language), (b) set expectations too low (dumbing it down to be safe), or (c) ignore the competency entirely. The band system makes competencies usable by specifying what competent looks like at each developmental stage.

EXCEPTION HANDLING:
Some subjects require finer granularity than four broad bands:
- **Mathematics:** Mathematical progression is steep and sequential. A student who hasn't mastered place value cannot begin multiplication. Broad bands may be too imprecise for maths. Consider 9 levels (or more) for mathematical competencies.
- **Language acquisition (L1 and L2):** Reading and writing progression requires fine-grained tracking, especially in early years. Consider 9 levels for literacy and language.
- The rule: use broad bands for competencies where developmental progression is gradual and contextual (critical thinking, collaboration, creativity). Use finer granularity for competencies where progression is sequential and cumulative (maths, language).

Your task is to design a developmental band system for:

**School mission:** {{school_mission}}
**Age range:** {{age_range}}
**Programme context:** {{programme_context}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Existing competency framework:** {{existing_competency_framework}} — if not provided, the band system will be designed from mission and values rather than mapping an existing framework.
**Mixed-age groupings:** {{mixed_age_groupings}} — if not provided, design the bands to work with or without mixed-age groupings.
**Subject exceptions:** {{subject_exceptions}} — if not provided, identify which subjects likely need finer granularity and recommend accordingly.

Return your output in this exact format:

## Developmental Band System: [School/Programme Name]

**Mission:** [The school's core purpose]
**Age range:** [Full range covered]
**Number of bands:** [How many, and why this number]

### Purpose-Driven Design Sequence

[Walk through the full sequence: mission → values → priorities → non-priorities → competency logic → band rationale. This makes the design transparent and traceable.]

### Band Architecture

[The complete band structure: how many bands, what ages each covers, and the developmental rationale for each band break]

| Band | Age Range | Developmental Anchor | Key Cognitive Characteristics |
|---|---|---|---|
| [Band] | [Ages] | [Piaget stage or equivalent] | [What students can typically do at this stage] |

### Developmental Rationale

[Why the bands are where they are — the cognitive, social-emotional, and practical reasoning for each band break]

### Competent Definition Logic

[How to determine what competent means at each band — the general principles, with a worked example showing how ONE competency is expressed differently across all bands]

### Exception Handling

[Which subjects need finer granularity and why, with specific guidance on the finer-grained system]

### Mixed-Age Implications

[How the band system works with mixed-age learning groups — what it makes possible and what it complicates]

### Known Limitations

[Honest assessment — bands are broad, development is variable, and some students will be ahead of or behind their band]

**Self-check before returning output:** Verify that (a) the design sequence begins with mission not curriculum, (b) each band has a developmental rationale, (c) competent is defined developmentally not topically, (d) exception handling covers maths and language, (e) the critique of flat competency lists is included, and (f) "spiky learners" are supported not pathologised.
```

## 示例输出

**场景：** *学校使命：“培养有能力、有同理心、准备好为需要他们的世界做出贡献的年轻人——通过真实世界项目、真诚的社区参与与深度的个人发展” / 年龄范围：“5–14岁” / 项目情境：“采用混龄学习小组的项目式学习。不设传统分科——能力通过跨学科项目教授。数学和读写每天有专门课时，但也嵌入在项目中” / 现有能力框架：“目前混合使用 GreenComp、EntreComp 和 LifeComp，外加一些校本能力。这些框架缺乏发展特异性” / 混龄分组：“是——四个学习小组大致对应5–7岁、7–9岁、9–11岁、11–14岁”*

---

## 发展阶段系统：REAL School

**使命：** 培养有能力、有同理心、准备好为需要他们的世界做出贡献的年轻人
**年龄范围：** 5–14岁
**阶段数量：** 4个（A、B、C、D）——这是一项与学校现有混龄学习小组对齐的实践者设计选择，汲取了发展理论依据，但尚未作为完整架构获得验证

### 使命驱动的设计序列

**1. 使命：** 有能力、有同理心、准备好做出贡献。这是一项**行动型（DOING）**使命——它明确了能动性（有能力）、伦理（有同理心）以及面向世界的取向（做出贡献）。课程必须培养出能在世界上**行动**的人，而不仅仅是知道关于世界知识的人。

**2. 价值观：** 真实世界学习。社区参与。个人发展。这些不是口号——它们是设计约束。“真实世界学习”意味着项目必须有真实受众和真实后果。“社区参与”意味着社区是学习伙伴，而非背景板。“个人发展”意味着课程包含内在生命成长，而不仅仅是学术技能。

**3. 课程必须优先什么：** 能动性（发起、规划并完成有意义工作的能力）。生态思维（理解系统、后果与相互依存）。沟通（清晰表达想法与深度倾听的能力）。匠心（对所产出一切事物追求品质的承诺）。自我认知（理解自身的优势、局限与价值观）。

**4. 课程必须不优先什么：** 为覆盖而覆盖的内容灌输。标准化考试备考。竞争性排名。所有维度上的整齐划一发展。这些是有意识的排除项——每一个“不”都让“是”更有力量。

**5. 能力逻辑：** 能力之所以被选中，是因为它们服务于使命。“展现系统思维”被纳入，是因为它服务于生态思维与真实世界问题解决。“背诵历史年份”被排除，是因为它服务于内容覆盖，而非能力。

**6. 阶段界定：** 每项能力在四个发展水平上表达，使用进阶杠杆（独立性、复杂度、范围、精确度、推理、迁移），而非主题升级。

### 阶段架构

| 阶段 | 年龄范围 | 发展锚点 | 核心认知特征 |
|---|---|---|---|
| **A** | 5–7 | 前运算晚期 / 具体运算早期 | 具体的、基于感官的、自我中心视角正在缓慢扩展。通过做与直接经验学习。抽象推理有限。能用具体实物进行分类、排序与比较。 |
| **B** | 8–10 | 具体运算期 | 针对具体情境的逻辑思维。能进行序列排列、分类与守恒。开始考量多元视角。能规划简单序列。在熟悉情境中日益独立。 |
| **C** | 10–12 | 形式运算早期 | 萌芽的抽象推理。能提出假设并检验。系统性思维能力增强。能考量多个变量。发展中的元认知——对自身思维的觉察。 |
| **D** | 12–14 | 发展中的形式运算期 | 系统性的抽象推理。能构建与评估论证。成熟的观点采择。能设计与执行复杂计划。具备元认知能力——能监控与调节自身学习。 |

### 发展学理

**A阶段 → B阶段切分点（约7–8岁）：** 从前运算思维向具体运算思维的转变。学生从基于知觉的推理（“这排更多，因为它更长”）转向基于逻辑的推理（“两排数量一样多，只是摆得更开”）。这是皮亚杰框架中确立最充分的发展过渡，对课程设计影响也最为深远：A阶段活动必须是具体和感官的；B阶段活动可以开始引入逻辑结构。

**B阶段 → C阶段切分点（约10–11岁）：** 抽象推理的涌现。学生开始思考他们看不见、摸不着的事物——假设性情境、抽象原则、系统关系。这为探究式学习打开了大门：C阶段学生能够以 B阶段学生尚无法可靠做到的方式设计调查、形成假设并考量变量。

**C阶段 → D阶段切分点（约12–13岁）：** 系统性与元认知思维的发展。学生不仅能抽象思考，还能**思考自己的思考**——规划、监控并评估自身的认知过程。这使得真正的自主定向学习成为可能：D阶段学生可以在导师指导而非直接讲授下设计并管理自己的项目。

### “胜任”界定逻辑

**实例演示：“展现系统思维”**

该能力通过生态思维服务于使命——理解行动会产生超越眼皮底下和显而易见范围的后果。

| 阶段 | “胜任”陈述 | 进阶杠杆 |
|---|---|---|
| **A** | 我能够描述当系统中的一件事物发生变化时会发生什么 | 范围：单一因果链条 |
| **B** | 我能够识别系统的各部分如何相互影响，并预测如果其中一部分变化可能会发生什么 | 复杂度：多重联结、预测 |
| **C** | 我能够绘制系统内的关系图，并解释变化如何波及相互连接的各个部分 | 推理：解释机制，而不仅仅是识别联结 |
| **D** | 我能够分析复杂系统、识别反馈回路与非预期后果，并评估干预措施 | 迁移：将系统分析应用于新情境，评估而非仅描述 |

注意：**主题**没有变（全程都是系统思维）。**能力**在变化——从描述单一联结（A阶段）到分析反馈回路与评估干预措施（D阶段）。这就是发展性进阶，而非主题升级。

### 例外处理

**数学：** 宽泛的阶段对数学而言不够精确。数学进阶陡峭且具有强顺序性：尚未掌握位值的学生无法开始乘法。宽泛阶段对数学可能过于粗糙。**建议：** 为数学能力采用9级系统，每个阶段对应 2–3 级。这在保持与阶段架构兼容的同时，提供了数学进阶所需的精细追踪。

**语言习得（第一语言与第二语言）：** 与数学类似，读写进阶需要精细颗粒度的追踪——尤其在低龄段，“认识字母”与“阅读简单句子”之间的差异是以月计，而非以年计。**建议：** 为读写能力采用9级系统，与宽泛阶段对齐但颗粒度更细。

**所有其他能力：** 宽泛阶段（A–D）提供了足够的颗粒度。系统思维、协作、匠心与自我调节等能力是渐进且情境化发展的——它们不需要数学与语言所要求的那种顺序精确度。

### 混龄意义

**阶段系统使什么成为可能：**
- 8–10岁的混龄学习小组（B阶段）可以对照**同一套**能力描述语进行评估。教师不需要为8岁、9岁和10岁分别准备3套独立期望——B阶段就是共同参照。
- 混龄小组中的年幼学生可以通过观察年长学生看到 C阶段长什么样。这创造了自然的 ZPD 支架。
- 年长学生通过支持年幼学生来巩固自己的 B阶段能力——即同伴辅导效应（Hattie, 2009: d = 0.55）。

**阶段系统使什么变得复杂：**
- 处于阶段过渡边缘的学生（正在从 B阶段迈向 C阶段的10岁孩子）可能同时表现出两个阶段的特征。教师必须运用专业判断来决定哪个阶段描述语最贴合。
- 一名“偏科/锯齿型（spiky）”学生在某项能力上处于 D阶段，在另一项能力上处于 B阶段，将会同时在不同阶段水平上接受评估。这是刻意为之的（发展本身就是不均衡的），但需要一个能够呈现学生多阶段画像的报告系统。

### 已知局限

1. **阶段在设计上刻意宽泛——部分学生不会严丝合缝地落入其中。** 一名能抽象思考的9岁孩子（早于 C阶段）或一名在抽象推理上吃力的13岁孩子（晚于 C阶段），将会对照一个并不完美匹配其发展的阶段接受评估。阶段只是参照，而非诊断。在边缘地带始终需要教师的专业判断。

2. **皮亚杰锚定只是近似的。** 皮亚杰阶段是最广为人知的发展框架，但也是受到最多批评的——发展比阶段理论所暗示的更加连续且多变（Siegler, 2006）。本阶段系统将皮亚杰用作学理依据，而非僵化教条。任何年龄组内部的个体差异都很大。

3. **使命驱动的逆向设计序列需要清晰的使命。** 如果学校使命含糊不清（“我们相信卓越与机遇”），整个设计序列都会被削弱——因为没有具体的目标可以逆向推导。阶段系统在拥有清晰、独特使命的学校中最为强大；在只有笼统宗旨陈述的学校中则较弱。

4. **阶段系统是“设计”工具，而非“评估”工具。** 它明确了“胜任”在每个发展阶段长什么样，但并未说明**如何**评估它。评估需要建立在阶段架构之上的量规（见技能99：连贯量规逻辑构建器）与学习目标（见技能98：学习目标撰写指南）。
