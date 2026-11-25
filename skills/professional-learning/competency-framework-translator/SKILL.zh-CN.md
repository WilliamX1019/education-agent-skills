---
# AGENT SKILLS STANDARD FIELDS (v2)
name: competency-framework-translator
description: "将 DigComp、GreenComp 或 ISTE 等外部能力框架转化为可直接用于课堂的教学活动。适用于在具体教学情境中落实框架标准。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "professional-learning/competency-framework-translator"
skill_name: "能力框架转化器"
domain: "professional-learning"
version: "1.0"
evidence_strength: "moderate"
evidence_sources:
  - "Wiggins & McTighe (2005) — Understanding by Design: translating standards into classroom practice"
  - "Marzano & Kendall (2007) — The New Taxonomy of Educational Objectives: operationalising competencies"
  - "European Commission (2022) — DigComp 2.2: the Digital Competence Framework for Citizens"
  - "Bianchi, Pisiotis & Cabrera (2022) — GreenComp: the European sustainability competence framework"
  - "UNESCO (2023) — Guidance for generative AI in education and research"
input_schema:
  required:
    - field: "framework_reference"
      type: "string"
      description: "待转化的外部能力框架——名称、具体能力领域及需处理的等级/描述语"
    - field: "target_context"
      type: "string"
      description: "教学情境——学科、年级以及教师希望学生用该能力“做什么”"
  optional:
    - field: "student_level"
      type: "string"
      description: "年龄/年级"
    - field: "subject_area"
      type: "string"
      description: "课程学科"
    - field: "framework_text"
      type: "string"
      description: "待转化的能力描述语实际文本——粘贴官方原文"
    - field: "integration_approach"
      type: "string"
      description: "该能力是独立教授、嵌入学科内容，还是作为跨学科成果评估"
    - field: "assessment_needs"
      type: "string"
      description: "教师需要如何评估该能力——形成性、终结性、档案袋、观察"
output_schema:
  type: "object"
  fields:
    - field: "translated_competency"
      type: "object"
      description: "改写为适合目标情境的具体、可观察指标的能力"
    - field: "progression_levels"
      type: "array"
      description: "3–4 个层级，展示该能力在发展中、胜任与进阶阶段的表现"
    - field: "classroom_tasks"
      type: "array"
      description: "要求学生展示该能力的具体任务或活动"
    - field: "assessment_criteria"
      type: "object"
      description: "如何评估学生是否发展了该能力——各层级的可观察指标"
chains_well_with:
  - "competency-unpacker"
  - "criterion-referenced-rubric-generator"
  - "backwards-design-unit-planner"
  - "project-brief-designer"
  - "curriculum-knowledge-architecture-designer"
  - "scope-and-sequence-designer"
teacher_time: "4 分钟"
tags: ["competency-frameworks", "DigComp", "GreenComp", "ISTE", "UNESCO-AI", "translation", "observable-indicators"]
---

# 能力框架转化器

## 本技能的功能

接收任意外部能力框架——DigComp（数字胜任力）、GreenComp（可持续发展）、ISTE 标准、UNESCO AI 能力框架、国家课程框架或任何其他基于能力的体系——并将其抽象描述语转化为针对特定学科与年级的课堂就绪型可观察指标、进阶层级、教学任务与评估标准。它解决的关键难题在于：能力框架是写给政策受众的，而非写给教师的；“批判性评估数据、信息与数字内容的可信度与可靠性”（DigComp 2.2）对政策分析师很有意义，但对八年级历史教师来说，却完全没有说明该教什么、布置什么任务或如何评估。产出是一份转化方案：同一项能力，表达为学生在不同水平上能“做（DO）”的具体事项，附带让能力可见的任务以及让能力可评估的标准。AI 在此处具有独特价值，因为这种转化需要同时理解框架的意图（能力真正要求什么）与课堂现实（该年龄段学生在这个学科、这些资源下能被期待做什么）。

## 循证基础

Wiggins 与 McTighe（2005）确立了标准与能力在教学与评估之前必须被“拆解（unpacked）”为可观察指标的原则。能力陈述是目的地；教师需要一张展示各阶段旅程样貌的地图。若不拆解，教师要么照本宣科教授学生听不懂的抽象措辞，要么把能力解释得过于宽泛以致失去意义。Marzano 与 Kendall（2007）提供了一个操作化能力的分类学——从提取（学生能回忆知识吗？）经由理解（能解释吗？）到分析（能比较、分类、评估吗？）再到知识运用（能在新情境中应用吗？）。这一分类学为进阶层级提供了脊梁。DigComp 2.2 框架（欧盟委员会，2022）是一个明确承认需要情境化的能力框架实例——它提供了8个熟练度等级，但指出必须针对具体教育情境进行适配。GreenComp（Bianchi et al., 2022）采取了类似路径，在高层面界定可持续发展能力，但要求学校将其转化为学科特定学习。UNESCO（2023）关于教育中生成式 AI 的指南引入了大多数课程框架尚不熟悉且亟需课堂级转化的 AI 素养能力。在所有这些案例中，框架与课堂之间的落差正是本技能所解决的问题。

## 输入模式

教师必须提供：
- **框架参考：** 哪个框架以及哪项能力。*例如：“DigComp 2.2 — 能力 1.2：评估数据、信息与数字内容” / “GreenComp — 能力领域：在可持续发展中拥抱复杂性” / “ISTE 学生标准 — 计算思维者” / “UNESCO AI 能力 — 理解 AI 伦理与负责任使用”*
- **目标情境：** 该能力将在何处教授。*例如：“九年级历史——学生评估关于一战起因的在线来源” / “七年级地理——学生理解气候变化的互联成因” / “十年级计算机科学——学生理解 AI 系统中的偏见”*

可选（如有，由上下文引擎注入）：
- **学生水平：** 年级
- **学科领域：** 课程学科
- **框架文本：** 官方能力措辞
- **整合方式：** 独立、嵌入或跨学科
- **评估需求：** 教师需要如何评估

## 提示词

```
You are an expert in competency frameworks and curriculum translation, with deep knowledge of Wiggins & McTighe's (2005) principles for unpacking standards, Marzano & Kendall's (2007) taxonomy for operationalising competencies, and specific familiarity with major competency frameworks including DigComp 2.2, GreenComp, ISTE Standards, UNESCO AI competency frameworks, and national curriculum systems. You understand that competency frameworks serve a policy purpose but require TRANSLATION for classroom use — and that the quality of this translation determines whether the competency is meaningfully developed or merely name-checked.

CRITICAL PRINCIPLES:
- **Observable indicators, not abstract statements.** "Critically evaluates digital sources" is abstract. "Given two websites about the same topic, identifies which is more credible by checking the author's credentials, the publication date, and whether claims are supported by evidence" is observable. Every translated indicator must describe something a teacher can SEE a student doing.
- **Progression, not binary.** Competencies develop over time. The translation must show what the competency looks like at different levels — not just "has it" or "doesn't have it" but "developing → competent → advanced." Each level must be qualitatively distinct (not just "more of the same").
- **Subject-specific, not generic.** "Evaluating sources" looks different in History (checking provenance, bias, context) than in Science (checking methodology, peer review, sample size) than in Media Studies (checking ownership, funding, audience). The translation must be specific to the stated subject and context.
- **Tasks that REQUIRE the competency.** The best way to assess a competency is through tasks that cannot be completed without demonstrating it. Design tasks where the competency is not optional but essential.
- **Honest about what the framework actually asks for.** Some framework descriptors are vague or contradictory. Where this is the case, acknowledge the ambiguity and provide a clear interpretation that serves the teacher's context.

Your task is to translate:

**Framework reference:** {{framework_reference}}
**Target context:** {{target_context}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Student level:** {{student_level}} — if not provided, infer from the target context.
**Subject area:** {{subject_area}} — if not provided, infer from the target context.
**Framework text:** {{framework_text}} — if supplied, reproduce it exactly as supplied and identify that provenance; do not imply independent verification of its official status. If absent, write "Exact source wording not supplied or verified" under Original Framework Wording and request the descriptor and version for fidelity checking. You may still draft a useful interpretation from the named framework and context, explicitly labelled provisional in the Translation and Framework Fidelity Check; never reconstruct text as an official quotation. If the source version is unspecified, say so rather than assume the latest edition.
**Integration approach:** {{integration_approach}} — if not provided, design for embedding in subject content (the most sustainable approach).
**Assessment needs:** {{assessment_needs}} — if not provided, design for formative assessment within lessons.

Return your output in this exact format:

## Competency Translation: [Framework — Competency Name]

**Framework:** [Which framework]
**Competency:** [Supplied name and reference; mark official status/version unverified where necessary]
**Translated for:** [Subject, year group, context]

### Original Framework Wording

[Exact supplied descriptor, labelled "Supplied text — official status not independently verified"; otherwise "Exact source wording not supplied or verified — please provide descriptor and version". No reconstructed official wording.]

### Translation: What This Means in [Subject] for [Year Group]

[Plain-English interpretation for this subject and age group, separate from the source wording; label provisional when exact descriptor/version is missing]

### Observable Indicators

For each level (3–4 levels):
**Level [N]: [Label — Emerging / Developing / Competent / Extending]**
- **The student can:** [Specific, observable actions — what you'd SEE them doing]
- **Evidence looks like:** [What their work, discussion, or behaviour would show]
- **The student cannot yet:** [What distinguishes this level from the next]

### Classroom Tasks

For each task (2–3):
**Task [N]: [Name]**
- **What students do:** [The task]
- **Why this task requires the competency:** [How it makes the competency visible]
- **What to look for:** [Observable indicators that the competency is being demonstrated]

### Assessment Criteria

[How to assess whether students are developing the competency — linked to the observable indicators at each level]

### Integration Notes

[How to embed this competency into existing subject teaching without creating a separate "competency lesson"]

### Framework Fidelity Check

[How well this translation represents the original framework intention — any interpretive choices made and why]

**Self-check before returning output:** Verify that (a) every indicator is observable — you can see or hear it, (b) progression levels are qualitatively distinct, (c) the translation is specific to the stated subject and year group, (d) tasks require the competency (it's not optional), (e) exact supplied wording is separated from interpretation and missing source/version or unverified official status is explicit, and (f) integration is practical — embeddable in existing teaching.
```

## 示例输出

**场景：** *框架参考：“DigComp 2.2 — 能力 1.2：评估数据、信息与数字内容。熟练度等级 3（中级）：'Can compare and critically evaluate the credibility and reliability of specific sources of data, information and digital content'” / 目标情境：“九年级历史——学生使用在线来源研究一战起因。教师希望学生评估找到的网站和来源的可信度，而不是简单地复制 Google 第一条结果。” / 学科领域：“历史” / 整合方式：“嵌入一战研究单元——而非独立的数字素养课”*

---

## 能力转化：DigComp 2.2——评估数字来源

**框架：** DigComp 2.2（欧洲数字胜任力框架）
**能力：** 1.2——评估数据、信息与数字内容（熟练度等级 3）
**转化目标：** 九年级历史——评估关于一战起因的在线来源

### 原始框架措辞

提供文本（官方状态未经独立核验）："Can compare and critically evaluate the credibility and reliability of specific sources of data, information and digital content"。场景将其标明为 DigComp 2.2 熟练度等级 3（欧盟委员会，2022）；将其作为官方引文前请对照该版本核对。

### 转化：这在九年级历史中意味着什么

在九年级历史中，这意味着：当学生在线研究一个历史主题时，他们能够评估一个网站或数字来源在历史学意义上是否可信与可靠——检查撰写者是谁（以及是否具备专业资质）、何时发布（以及是否具时效性）、引用了什么证据（以及主张是否得到支撑），以及是否存在影响其可靠性的偏见或特定目的。这并非通用的数字素养技能——它是历史学家所践行的**史料评估**应用于数字来源。历史学家会问：谁制作了它？为什么？什么证据支持它？它与其他来源是一致还是矛盾？学生应对网站提出同样的问题。

### 可观察指标

**等级 1：萌芽——认识到来源可信度很重要**
- **学生能够：** 区分不同类型的在线来源（网站、博客、新闻文章、社交媒体帖子），并理解并非所有来源都同等可靠。能识别来源是否有具名作者。
- **证据表现为：** 当被问及“你在哪里找到这条信息的？”时，学生能说出源名称及类型。可能会说“我不确定这是否可靠”，但尚不能解释原因。
- **学生尚不能：** 使用具体标准评估可信度，或给出“它看起来很可信”或“它是第一条搜索结果”之外的理由。

**等级 2：发展中——识别基本可信度标记**
- **学生能够：** 检查网站是否有具名作者，识别来源是个人博客、教育网站还是新闻文章，并注意到来源何时在没有证据的情况下提出主张。
- **证据表现为：** 学生的研究笔记包含来源 URL **以及**作者/机构名称。当被问及“这是一个好来源吗？”时，学生能给出至少一个理由（“它来自一所大学”或“我找不到是谁写的”）。
- **学生尚不能：** 对比两个来源以评估哪一个更可靠，或识别微妙的偏见（例如关于一战起因的民族主义视角）。

**等级 3：胜任——评估并比较来源**
- **学生能够：** 对比同一主题的两个或多个来源，并指出哪一个更可信，给出具体理由。能识别基本偏见（“这个网站由德国遗产组织运营——他们呈现德国视角的方式可能与英国来源不同”）。能核查主张是否得到来源所引证据的支持。
- **证据表现为：** 学生的研究笔记对每个来源作出评估：“我使用这个来源是因为[理由]，但不使用那个是因为[理由]。”在书面作品中，学生基于可信度而非便利性选择来源（不只是用 Google 第一条结果）。
- **学生尚不能：** 识别复杂的偏见（例如来源选择本身如何塑造叙事），或评估来源主张背后的方法论。

**等级 4：拓展——批判性评估可信度、偏见与目的**
- **学生能够：** 分析数字来源的目的与受众（“这是为英国受众纪念一战百年而写的——其目的是纪念而非分析，这影响了它纳入和排除了什么”）。能在多个来源之间交叉核对主张以检查一致性。能清晰阐述为什么即使可信的来源也可能不完整或有偏见。
- **证据表现为：** 学生的研究明确讨论可靠性：“来源 A（BBC History）和来源 B（维基百科）都指出斐迪南大公遇刺触发了一战，但来源 C（一篇期刊文章）论证暗杀是催化剂而非根源。来源 C 在分析上更有用，因为它区分了导火索与深层原因。”
- **学生尚不能：** 带着完整的史学史意识评估数字档案馆中的一手史料（这属于高中高阶/大学水平）。

### 课堂任务

**任务 1：史料大比拼（Source Showdown）**
- **学生做什么：** 给学生4个关于一战起因的网站——一个是来源扎实的教育网站（如 BBC History），一个是无引用的个人博客，一个是立场鲜明的民族主义遗产网站，还有一个是维基百科词条。学生必须**为了他们的历史论文**将这4个来源从最可靠到最不可靠排序，并用来自来源的具体证据论证每一名的排位。
- **为什么该任务需要该能力：** 如果不评估可信度、核查证据并对比来源，学生就无法完成排序。从任何单一来源抄写都无法回答这个问题——任务强制要求评估。
- **观察要点：** 学生是否引用了来源的具体特征（作者资质、证据、偏见），还是给出笼统理由（“它看起来很专业”）？他们是否区分了不同类型的不可靠（无证据 vs. 有偏见的证据 vs. 过时）？

**任务 2：研究日志（The Research Log）**
- **学生做什么：** 在独立研究一战起因期间，学生为所使用的每一个来源填写研究日志。日志有四栏：来源（URL + 作者）、可信度核查（为什么我信任或不信任该来源）、我从中采纳的内容（具体信息），以及局限性（该来源没有告诉我什么或可能出错之处）。
- **为什么该任务需要该能力：** 研究日志让来源评估变得**可见**。一名不经评估就从第一条 Google 结果抄写的学生，其“可信度核查”栏将是空的——教师一眼就能看到缺口。
- **观察要点：** 学生是否在可信度核查栏填入了具体理由，还是留空或只写“好来源”？他们是否记录了局限性？

**任务 3：事实核查挑战（Fact-Check Challenge）**
- **学生做什么：** 给学生一段来自不可靠来源的关于一战的短文（其中混合了准确信息、3处事实错误与2处作为事实呈现的偏见解读）。学生必须识别：什么是准确的、什么是不准确的，以及什么是被当作事实呈现的观点。他们必须至少使用另一个来源来核实每项主张。
- **为什么该任务需要该能力：** 该任务要求学生批判性评估具体主张、与其他来源交叉核对并区分事实与解读——这正是 DigComp 能力应用于历史内容的核心。
- **观察要点：** 学生能否识别错误与偏见，还是不加批判地全盘接受短文？他们是否进行了交叉核对（使用另一个来源核实），还是仅凭自身预设？

### 评估标准

| 标准 | 萌芽 | 发展中 | 胜任 | 拓展 |
|---|---|---|---|---|
| 识别来源特征 | 区分来源类型（博客、新闻、学术） | 说出来源类型并检查作者/证据 | 基于作者、证据与目的评估可信度 | 分析目的与受众如何塑造来源内容 |
| 比较来源 | 认识到来源可能存在差异 | 注意到不同来源说法不同 | 给出具体理由按可靠性排序来源 | 跨多个来源交叉核对主张以识别共识与分歧 |
| 觉察偏见 | 理解来源可能带有偏见 | 识别明显偏见（“这太片面了”） | 指出偏见如何影响具体主张（“该来源指责德国是因为……”） | 解释即使是看似平衡的来源也涉及筛选与框架建构 |
| 在自身作品中运用评估 | 引用了来源但未评估 | 引用来源并附带基本可信度说明 | 基于可信度筛选来源并注明局限 | 将来源评估整合进自己的论证（“根据更可靠的来源 A……”） |

### 整合说明

该能力**不应**作为脱离历史的独立“数字素养”课来教授。相反：
- **一战单元第1课：** 当全班研究起因时引入“史料大比拼”任务。将其框定为“历史学家的工作”——评估来源正是历史学家所做的事。
- **贯穿整个单元：** 要求每项独立研究任务都填写研究日志。巡视时检查它——花30秒扫一眼“可信度核查”栏，就能知道学生是在评估还是只是在抄写。
- **单元末：** “事实核查挑战”同时充当历史知识检查与数字能力评估。

该能力是**通过**学科内容而非**在学科之外**培养的。学生学习评估数字来源是因为他们需要它——他们正在研究一战，需要可靠信息。数字能力与历史技能相互强化。

### 框架保真度检查

本初稿结合以下情境化处理对场景提供的 DigComp 2.2 等级 3 措辞进行了解读。官方措辞与等级归属仍需对照原版文献核对：
- **“可信度（Credibility）”** 通过历史学透镜解读：作者资质、证据引用、偏见、目的。在科学情境中，可信度则会侧重方法论与同行评审。
- **“可靠性（Reliability）”** 被解读为跨来源的一致性与证据强度——而不仅仅是来源是否“看起来值得信赖”。
- **“数字内容（Digital content）”** 被解读为研究过程中遇到的网站与在线资源，而非社交媒体或即时通讯（在媒介研究情境中这将是另一番转化）。

与 DigComp 的预期联结是明确的，但框架保真度仍有待对照原始文献与教育者审阅；具体任务与等级属于课堂设计判断。换一门学科将会产出同一项能力的不同转化。

---

## 已知局限

1. **能力框架会定期更新。** DigComp 已从 1.0 演进到 2.2；GreenComp 相对较新；UNESCO AI 指南也将持续演变。转化必须标明所依据的版本而非想当然地假定其为最新版；教师应核对适用于自身环境的版本，并在描述语变更时予以调整。

2. **部分框架刻意保持模糊。** 框架描述语是为多种情境（小学、中学、职业教育、成人教育）及多个国家撰写的。这种概括性是设计使然，而非缺陷——但它意味着转化不可避免地涉及解读。本技能对解读选择保持透明，但教师应核实该转化是否与本校或本学区的框架解读一致。

3. **能力框架不是课程。** 能力框架描述了学生应能做什么，但没有说明如何教、何时教或如何评。本转化提供了这些要素，但它们是受框架启发的教学决策，而非由框架硬性规定。教师应调整任务与标准以契合自身具体课程与学生。

4. **并非所有框架都有同等坚实的实证基础。** DigComp 与 GreenComp 是通过利益相关方协商而非教育研究试验开发的政策框架。它们所描述的能力合情合理且重要，但其具体描述语与熟练度等级并未像 Hattie 的效应量那样经过实证验证。教师应将框架描述语视为有用的组织结构，而非经科学确立的学习进阶规律。
