---
# AGENT SKILLS STANDARD FIELDS (v2)
name: assessment-validity-checker
description: "从构念效度、信度以及与学习目标的对齐度三个维度审计拟议评估方案。适用于在部署前审查或质量把关评估任务。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "curriculum-assessment/assessment-validity-checker"
skill_name: "评估效度核查器"
domain: "curriculum-assessment"
version: "1.0"
evidence_strength: "strong"
evidence_sources:
  - "Wiliam (2011) — Embedded Formative Assessment"
  - "Messick (1989) — Validity in educational measurement: a unified validity framework"
  - "Kane (2006) — Validation as argument-based approach"
  - "Brookhart (2003) — Developing measurement theory for classroom assessment purposes and uses"
  - "Stobart (2008) — Testing Times: the uses and abuses of assessment"
input_schema:
  required:
    - field: "assessment_description"
      type: "string"
      description: "拟议评估的描述——学生做什么、如何评分"
    - field: "intended_learning"
      type: "string"
      description: "该评估声称要测量的内容"
    - field: "student_level"
      type: "string"
      description: "年龄/年级"
  optional:
    - field: "subject_area"
      type: "string"
      description: "课程学科"
    - field: "assessment_purpose"
      type: "string"
      description: "形成性、终结性、诊断性或评价性"
    - field: "marking_approach"
      type: "string"
      description: "评估如何评分——量规、评分标准、整体判断"
    - field: "stakes"
      type: "string"
      description: "评估的利害关系——低利害（指导教学）、高利害（打分、汇报）"
output_schema:
  type: "object"
  fields:
    - field: "validity_analysis"
      type: "object"
      description: "对构念效度、内容效度和后果效度的分析"
    - field: "reliability_analysis"
      type: "string"
      description: "对评分者间信度与内部一致性的分析"
    - field: "threats_identified"
      type: "array"
      description: "识别出的具体效度威胁及其解释"
    - field: "recommendations"
      type: "array"
      description: "针对已识别威胁的具体修改建议"
chains_well_with:
  - "criterion-referenced-rubric-generator"
  - "formative-assessment-technique-selector"
  - "competency-unpacker"
  - "backwards-design-unit-planner"
  - "curriculum-knowledge-architecture-designer"
  - "kud-knowledge-type-mapper"
teacher_time: "3 分钟"
tags: ["validity", "reliability", "assessment-design", "quality-assurance", "measurement"]
---

# 评估效度核查器

## 本技能的作用

从三个维度评估拟议的评估方案：效度（它是否真的测量了声称要测量的内容？）、信度（不同阅卷人给出的分数是否一致？）以及真实性（任务是否有意义，是否要求真正展示预期学习？）。输出识别具体的效度威胁——构念无关变异（评估测量了声称之外的其他东西）、构念代表性不足（评估未充分覆盖声称要测量的内容）以及后果效度问题（评估带来的非预期负面效应）——并为每项威胁提供具体、可操作的修改建议。AI 在此尤为关键，因为大多数教师设计的评估都包含没有显性分析框架就难以察觉的效度威胁——例如，设计“阅读理解”测试的教师可能无意中测成了写作测试，而“科学理解”评估实际测的可能是读写能力。

## 实证基础

Messick（1989）将效度概念统一为单一框架：效度不是测验本身的属性，而是测验分数**解释与使用**的属性。测验在抽象意义上无所谓“有效”或“无效”——它是**针对特定人群的特定用途**而言有效。这意味着每项评估都必须对照其预期用途加以评估。Wiliam（2011）将这一框架应用于课堂评估，表明教师设计评估中最常见的效度威胁是构念无关变异（construct-irrelevant variance）——即评估测量了预期构念之外的东西。例如，一项旨在评估“对气候变化理解”的小组展示，实际测量的可能更多是公开演讲自信度、小组动态与技术技能，而非气候变化理解。Kane（2006）提出了基于论证的验证（validation-as-argument）方法：评估的效度取决于从任务 → 作答 → 分数 → 解释 → 决策这一推理链条的强度。链条中的任何薄弱环节都是效度威胁。Brookhart（2003）为课堂情境调适了测量理论，指出课堂评估无需达到标准化测验同等的心理测量学标准，但仍必须证明它测量了所声称的内容。Stobart（2008）强调了后果效度（consequential validity）——评估对学习的影响。如果一项评估驱使学生转向表层学习、考试焦虑或策略性应付行为而非真正投入，其后果效度就受损了。

## 输入规范

教师必须提供：
- **评估描述（Assessment description）：** 学生做什么及如何评分。*例如：“学生撰写一篇 500 词关于一战起因的论文，按包含四项标准的量规评分：历史知识、分析论证、证据运用和书面表达” / “学生完成一份关于光合作用的 30 道选择题测试” / “学生制作一张关于健康饮食的海报并向全班展示”*
- **预期学习（Intended learning）：** 评估声称要测量的内容。*例如：“对一战起因的理解以及建构历史论证的能力” / “光合作用的知识与理解” / “对营养与健康饮食的理解”*
- **学生水平（Student level）：** 年级。*例如：“十年级”*

可选项（如可用则由上下文引擎注入）：
- **学科领域（Subject area）：** 课程学科
- **评估目的（Assessment purpose）：** 形成性、终结性、诊断性或评价性
- **评分方式（Marking approach）：** 如何评分
- **利害关系（Stakes）：** 评估的后果

## 提示词（Prompt）

```
You are an expert in educational assessment and measurement, with deep knowledge of Messick's (1989) unified validity framework, Wiliam's (2011) approach to classroom assessment validity, Kane's (2006) argument-based validation, and Stobart's (2008) work on consequential validity. You understand that validity is not a property of the test itself but of the interpretation and use of the scores — an assessment is valid FOR a specific purpose, and the same assessment may be valid for one purpose but invalid for another.

Your task is to evaluate the validity of:

**Assessment description:** {{assessment_description}}
**Intended learning:** {{intended_learning}}
**Student level:** {{student_level}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Subject area:** {{subject_area}} — if not provided, infer from the assessment description.
**Assessment purpose:** {{assessment_purpose}} — if not provided, infer from the description and stakes.
**Marking approach:** {{marking_approach}} — if not provided, note that marking approach affects reliability and recommend one.
**Stakes:** {{stakes}} — if not provided, analyse for both low-stakes and high-stakes use.

Analyse across these dimensions:

1. **Construct validity (Messick, 1989):**
   - Does the assessment task actually require demonstration of the intended learning?
   - **Construct-irrelevant variance:** Does the assessment inadvertently measure something ELSE? (E.g., a science assessment that requires essay writing also measures literacy; a group project also measures collaboration and social dynamics.)
   - **Construct underrepresentation:** Does the assessment cover enough of the intended construct? (E.g., a test on "understanding photosynthesis" that only asks factual recall questions doesn't assess understanding — it assesses memorisation.)

2. **Content validity:**
   - Does the assessment sample appropriately from the domain of intended learning?
   - Are important aspects of the learning missing from the assessment?
   - Are there aspects of the assessment that go beyond the intended learning?

3. **Reliability (Brookhart, 2003):**
   - Would different markers give the same score? (Inter-rater reliability)
   - Would the same student get a similar score on a different day? (Test-retest)
   - Is the marking scheme clear enough to be applied consistently?

4. **Consequential validity (Stobart, 2008):**
   - What behaviours will this assessment drive? Will students engage in genuine learning or strategic/surface-level preparation?
   - Does the assessment create unfair barriers for specific groups (EAL students, students with learning differences)?
   - Does the assessment format match the learning it claims to measure?

5. **Authenticity:**
   - Does the task require genuine demonstration of the learning, or can a student perform well without actually having learned the intended content?
   - Can the task be completed through memorisation, copying, or procedural compliance without understanding?

Return your output in this exact format:

## Assessment Validity Analysis

**Assessment:** [Brief description]
**Claims to measure:** [Intended learning]
**For:** [Student level]

### Validity Analysis

**Construct validity:** [Analysis of whether the assessment measures what it claims]
**Construct-irrelevant variance:** [What ELSE the assessment measures that isn't intended]
**Construct underrepresentation:** [What aspects of the intended learning are NOT assessed]

### Reliability Analysis

[Analysis of marking consistency and specific reliability concerns]

### Consequential Validity

[What learning behaviours the assessment is likely to drive]

### Threats Identified

[Numbered list of specific validity threats, each with an explanation]

### Recommendations

[Specific, actionable modifications to address each identified threat]

### Overall Verdict

[Summary judgement: is this assessment fit for its stated purpose? What is the single most important modification?]

**Self-check before returning output:** Verify that (a) the analysis addresses construct validity, reliability, and consequential validity, (b) each threat is specific and explained, (c) each recommendation directly addresses an identified threat, (d) the analysis considers the assessment's purpose and stakes, and (e) the verdict is constructive — identifying what to fix, not just what's wrong.
```

## 示例输出

**情景：** *评估描述：“学生制作一张关于气候变化起因的海报并向全班展示。海报必须包含至少 3 个起因、一个视觉元素（图表或示意图），且‘视觉上具有吸引力’。满分 20 分：内容（8 分）、视觉设计（6 分）、展示（6 分）。” / 预期学习：“学生理解气候变化的起因与影响。” / 学生水平：“九年级” / 学科领域：“地理”*

---

## 评估效度分析

**评估任务：** 气候变化起因海报展示
**声称测量：** 对气候变化起因与影响的理解
**适用对象：** 九年级地理

### 效度分析

**构念效度：** **中度担忧**。该评估声称测量对气候变化起因与影响的理解，但任务与评分方案同时评估了三个构念：地理知识（8/20 = 40%）、视觉设计技能（6/20 = 30%）以及公开演讲技能（6/20 = 30%）。一名深刻理解气候变化但不会画画或演讲不够自信的学生，得分会低于一名知识浅薄却制作出精美海报且自信展示的学生。该评估并未主要测量它声称要测量的内容。

**构念无关变异：**
- **视觉设计（6 分）：** 制作“视觉上具有吸引力”的海报的能力与理解气候变化无关。这测量的是美术/设计技能以及获取彩笔、打印机和手工材料的条件——这些资源与社会经济背景相关，而非地理理解。制作出美学上朴素但科学上准确的海报的学生会受到惩罚。这是最显著的效度威胁。
- **展示技能（6 分）：** 公开演讲自信度是独立于地理理解之外的技能。英语作为附加语言（EAL）的学生、有言语障碍的学生和有社交焦虑的学生会在这一部分处于劣势。展示或许能揭示理解，但占 6/20 的分数意味着表达仪态的权重几乎与科学准确性相当。
- **物质条件差异：** 在家能用彩印机、电脑或购买海报材料的学生获得了与学习无关的优势。

**构念代表性不足：**
- 评估仅要求“至少 3 个起因”，但预期学习还包括“影响”——尽管“影响”是既定学习目标的一部分，却未被评估。
- 评估并未要求学生**解释**起因——只要求罗列。一张只列出“燃烧化石燃料、砍伐森林、农业”而不作解释的海报就能拿满内容分。罗列是回忆；解释才是理解。该评估对“理解”成分代表性不足。
- 没有评估起因之间的关系、相对重要性或证据评价——而这些正是目标所隐含的地理思维技能。

### 信度分析

- **“视觉上具有吸引力”** 具有高度主观性且缺乏锚定标准。两位阅卷人对什么算“有吸引力”很可能会有显著分歧。这一标准将产生所有组成部分中最低的评分者间信度。
- **内容评分（8 分）** 如果评分标准明确规定了什么算一个“起因”以及何种解释水平对应多少分，尚可具有信度——但如前所述，“至少 3 个起因”是一个二元门槛，而非质量量表。罗列 3 个基本起因的学生与提供 5 个详实有据解释的学生可能拿到相近分数。
- **展示（6 分）** 未说明具体标准。阅卷人可能对流畅度、自信、眼神交流、音量或内容准确性赋予不同权重。缺少量规时，信度会很低。

### 后果效度

- **该评估激励“装饰”而非“理解”。** 意识到 12/20 分（60%）取决于设计与展示的学生，会理性地把更多时间花在美工和排练上，而非学习内容本身。这助长了表层学习行为。
- **该评估对 EAL 学生和内向学生不利。** 6 分的展示分制造了与地理无关的障碍。深刻理解气候变化但一上台就紧张的学生，其表现会低于真实理解水平。
- **该评估奖励社会经济优势。** 拥有打印机、彩纸、马克笔和设计电脑的学生在 30% 的分数上占尽先机。这有失公平。

### 识别出的威胁

1. **重大威胁：来自视觉设计的构念无关变异。** 30% 的分数评估的是设计技能而非地理。这意味着评估分数并不代表它所声称的内容。
2. **重大威胁：来自展示的构念无关变异。** 30% 的分数评估公开演讲，使 EAL、焦虑及言语障碍学生处于劣势。
3. **中度威胁：构念代表性不足。** 尽管“影响”在预期学习中，却未被评估。不要求解释起因——只要求罗列。
4. **中度威胁：信度偏低。** “视觉上具有吸引力”主观性强。展示分缺少量规。内容分无法区分解释质量。
5. **轻度威胁：后果效度不佳。** 分数权重激励装饰而非学习。

### 修改建议

1. **重构分值分配。** 内容应至少占总分的 70%。将视觉设计降至 0 分（彻底移除该标准）或封顶为 2 分的“视觉传达清晰度”（图表/示意图是否有效传递信息——而非是否好看）。将展示降至最多 4 分，并配以聚焦“解释清晰度”而非“表达自信度”的量规。

2. **要求解释，而非仅仅罗列。** 将“至少 3 个起因”改为“解释气候变化的 3 个起因，包括每个起因**如何**导致温室气体浓度升高”。这测的是理解，而非回忆。

3. **补齐缺失构念。** 增加对“影响”和“起因”的共同要求——或者修改预期学习以匹配评估。对齐必须双向一致。

4. **用“清晰且具传达力”替换“视觉上具有吸引力”。** 如果保留视觉元素，评估图表/示意图是否准确传达地理信息——而非它是否美观。

5. **提供现场展示的替代方案。** 允许学生提交录制好的解释视频、书面段落或向教师一对一口头解释，替代全班展示。这能移除公开演讲障碍，同时依然评估学生能否解释自己的理解。

6. **制定内容量规。** 用描述性量规替代笼统的 8 分内容分，区分罗列起因（较低水平）、解释起因（中等水平）以及分析起因间关系与相对重要性（较高水平）。

### 总体结论

按目前的设计，这项评估**不符合预期目的**。它声称测量对气候变化的理解，实际上测量的却是地理知识（40%）、美术技能（30%）与公开演讲（30%）的混合物。唯一最重要的修改是**重构分值分配**，让内容理解主导评估。如果一名学生深刻理解气候变化的起因与影响，无论其海报画得如何或演讲是否自信，都应当获得高分。

---

## 已知局限

1. **本分析评估的是“书面描述的评估”，可能与实际执行有所差异。** 教师在实践中如果对设计打分宽松、对内容打分严格，可能会部分弥补分值分配问题——但结构性问题依然存在。应当确保评估的**设计**本身就是有效的，而不仅仅依赖实施中的补救。

2. **效度始终相对于特定目的而言。** 本分析评估的是针对**既定**目的（测量对气候变化的理解）的效度。如果评估的实际目的确实包含培养演讲技能，效度分析就会不同——但此时该评估应当明确标注为测量多个构念。

3. **部分效度威胁属于权衡取舍，而非单纯错误。** 纳入展示环节可能有合理的教学理由（培养口语表达技能、建立自信）。本分析指出了这些设计选择的效度代价——教师必须权衡教学收益是否足以证明效度妥协的合理性。关键在于对评估实际测量的内容保持透明。
