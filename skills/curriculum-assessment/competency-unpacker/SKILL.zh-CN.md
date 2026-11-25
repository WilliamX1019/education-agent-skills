---
# AGENT SKILLS STANDARD FIELDS (v2)
name: competency-unpacker
description: "将宽泛的标准或能力描述符拆解为具体、可评估的成功标准与子技能。适用于解读课程标准或撰写学习目标。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "curriculum-assessment/competency-unpacker"
skill_name: "能力拆解器（Competency Unpacker）"
domain: "curriculum-assessment"
version: "1.0"
evidence_strength: "strong"
evidence_sources:
  - "Wiggins & McTighe (1998, 2005) — Understanding by Design: backward design from desired results"
  - "Marzano & Kendall (2007) — The New Taxonomy of Educational Objectives"
  - "Heritage (2008) — Learning progressions: supporting instruction and formative assessment"
  - "Popham (2007) — The lowdown on learning progressions"
  - "Hattie (2009) — Visible Learning: success criteria and learning intentions"
input_schema:
  required:
    - field: "competency_descriptor"
      type: "string"
      description: "需要拆解的标准、学习目标或能力描述符"
    - field: "student_level"
      type: "string"
      description: "年龄/年级"
  optional:
    - field: "subject_area"
      type: "string"
      description: "课程学科"
    - field: "curriculum_framework"
      type: "string"
      description: "来自上下文引擎：具体的课程或标准框架"
    - field: "student_profiles"
      type: "array"
      description: "来自上下文引擎：先前学业水平数据、常见漏洞"
    - field: "assessment_purpose"
      type: "string"
      description: "拆解该能力的目的——用于教学规划、评估设计还是学业汇报"
output_schema:
  type: "object"
  fields:
    - field: "observable_indicators"
      type: "array"
      description: "证明该能力的具体、可观察行为"
    - field: "prerequisite_knowledge"
      type: "array"
      description: "学生在尝试该能力前必须已经知道或能够做到的内容"
    - field: "common_misconceptions"
      type: "array"
      description: "妨碍展示该能力的典型误解"
    - field: "success_criteria"
      type: "object"
      description: "多层级成功标准——初现（beginning）、发展（developing）、稳固（secure）、拓展（extending）"
chains_well_with:
  - "backwards-design-unit-planner"
  - "criterion-referenced-rubric-generator"
  - "learning-progression-builder"
  - "formative-assessment-technique-selector"
  - "curriculum-knowledge-architecture-designer"
  - "kud-knowledge-type-mapper"
  - "scope-and-sequence-designer"
teacher_time: "3 分钟"
tags: ["competency", "standards", "success-criteria", "unpacking", "curriculum"]
---

# 能力拆解器（Competency Unpacker）

## 本技能的作用

接收一项标准、学习目标或能力描述符——通常以抽象、高度浓缩的语言写成——并将其拆解为四个可操作组件：可观察指标（达成该能力的学生实际上**做什么**）、前置知识（必须先具备什么）、常见迷思概念（通常哪里会出错）以及多层级成功标准（从初现到拓展）。输出将晦涩的课程语言转化为具体、可评估、可教学的组成要素。AI 在此尤为关键，因为能力描述符往往被刻意压缩——像“分析作者如何运用语言和结构来达到效果并影响读者”这样短短一句话，内部包含了多种技能、知识领域和熟练度层级，必须先拆解才能施教或评估。

## 实证基础

Wiggins & McTighe（1998, 2005）确立了有效课程设计始于对预期结果的清晰界定——而大多数课程标准在转化为教学与评估之前都需要进行大量“拆解”。一条写着“学生将理解第一次世界大战的起因”的标准，在用可观察术语界定“理解”之前是无法评估的。Marzano & Kendall（2007）提供了一套对标准认知需求进行分类的体系——区分提取、领会、分析与知识运用——使教师能够识别标准究竟要求哪种思维。Heritage（2008）和 Popham（2007）证明，将标准拆解为学习进阶——从前置能力到目标能力的子技能序列——对教学与形成性评估都至关重要，因为它揭示了学生当前所处位置以及下一步需要什么。Hattie（2009）发现，清晰的成功标准（效应量 0.77）是最高杠杆的教学策略之一，但前提是它们用具体、可观察的术语描述成功是什么样子——而不是换个说法复述学习目标。

## 输入规范

教师必须提供：
- **能力描述符（Competency descriptor）：** 要拆解的标准或目标。*例如：“分析作者如何运用语言和结构来达到效果并影响读者” / “运用比和比例（包括比率）解决问题” / “解释环境变化如何影响生物体”*
- **学生水平（Student level）：** 年级。*例如：“九年级”*

可选项（如可用则由上下文引擎注入）：
- **学科领域（Subject area）：** 课程学科
- **课程框架（Curriculum framework）：** 具体标准框架（如国家课程、IB、ACARA）
- **学生画像（Student profiles）：** 先前学业水平数据、常见漏洞
- **评估目的（Assessment purpose）：** 拆解该能力的目的

## 提示词（Prompt）

```
You are an expert in curriculum design and standards-based instruction, with deep knowledge of Wiggins & McTighe's (1998, 2005) Understanding by Design framework, Marzano & Kendall's (2007) taxonomy of educational objectives, and Heritage's (2008) work on learning progressions. You understand that competency descriptors are compressed summaries of complex learning — they must be unpacked into observable, teachable, assessable components before they can guide instruction.

Your task is to unpack:

**Competency descriptor:** {{competency_descriptor}}
**Student level:** {{student_level}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Subject area:** {{subject_area}} — if not provided, infer from the competency descriptor.
**Curriculum framework:** {{curriculum_framework}} — if not provided, unpack in general terms applicable across frameworks.
**Student profiles:** {{student_profiles}} — if not provided, assume a typical mixed-ability class at the stated year level.
**Assessment purpose:** {{assessment_purpose}} — if not provided, unpack for general instructional planning.

Apply these evidence-based principles:

1. **Observable indicators (Wiggins & McTighe, 2005; Hattie, 2009):**
   - Define what a student who has achieved the competency actually DOES — observable actions, not internal states.
   - "Understands" is not observable. "Identifies," "explains," "compares," "evaluates," "constructs" are observable.
   - Be specific to the competency: "identifies the effect of a writer's word choice on the reader" is more useful than "analyses language."
   - Include 4–6 specific indicators that collectively cover the competency.

2. **Prerequisite knowledge and skills (Heritage, 2008; Popham, 2007):**
   - What must a student already know or be able to do BEFORE they can work toward this competency?
   - Distinguish between content prerequisites (knowledge needed) and skill prerequisites (abilities needed).
   - These prerequisites become diagnostic checks — if a student can't demonstrate the competency, the prerequisite list helps identify WHERE the gap is.

3. **Common misconceptions (Marzano & Kendall, 2007):**
   - What typically goes wrong when students attempt this competency?
   - Include both conceptual misconceptions (misunderstandings of the content) and procedural errors (mistakes in the process).
   - These become assessment design priorities — good assessments surface these misconceptions.

4. **Multi-level success criteria (Hattie, 2009):**
   - Provide success criteria at four levels: Emerging, Developing, Competent, Extending.
   - Each level should describe what the student CAN do (not what they can't).
   - Levels should be qualitatively different, not just quantitatively different (Competent is not "more of" Developing — it's a different quality of response).
   - Use descriptive language, not evaluative labels.

Return your output in this exact format:

## Competency Unpacked: [Brief descriptor]

**Standard:** [Full competency descriptor]
**For:** [Student level]
**Subject:** [Subject area]

### Observable Indicators

[4–6 specific, observable behaviours that demonstrate this competency]

### Prerequisite Knowledge and Skills

**Content prerequisites (what students must know):**
[Specific knowledge required]

**Skill prerequisites (what students must be able to do):**
[Specific skills required]

### Common Misconceptions

[3–4 typical misconceptions or errors, with explanation of why they occur]

### Success Criteria

| Level | What the student does |
|-------|----------------------|
| **Emerging** | [Description of early, partial demonstration] |
| **Developing** | [Description of growing but inconsistent demonstration] |
| **Competent** | [Description of consistent, accurate demonstration] |
| **Extending** | [Description of sophisticated, independent application] |

### Implications for Teaching

[2–3 key teaching implications — what the unpacking reveals about how this competency should be taught]

**Self-check before returning output:** Verify that (a) all indicators are observable, not internal ("explains" not "understands"), (b) prerequisites are specific enough to be diagnostic, (c) misconceptions are based on common patterns, not hypothetical, (d) success criteria describe what students CAN do at each level, and (e) the four levels are qualitatively distinct.
```

## 示例输出

**情景：** *能力描述符：“分析作者如何运用语言和结构来达到效果并影响读者” / 学生水平：“九年级” / 学科领域：“英语语言”*

---

## 能力拆解：分析作者的语言与结构

**标准：** 分析作者如何运用语言和结构来达到效果并影响读者
**适用对象：** 九年级
**学科：** 英语语言

### 可观察指标

达成该能力的学生能够：

1. **识别具体语言选择**（单个词语、短语、修辞手法、句式类型）并在适用时准确命名技巧（隐喻、嘘音、制造冲击的短句）。
2. **解释每处语言选择对读者产生的效果**——它让读者想到什么、感受到什么或脑海中浮现什么画面——而不仅仅是识别出技巧名称。
3. **识别结构选择**（段落长度、开头、结尾、语气转折、顺叙 vs. 非线性、句子位置）并解释它们如何在整篇文本中塑造读者体验。
4. **将语言与结构选择联系到作者意图**——解释作者**为什么**做出这些选择，将技巧与意图（说服、制造紧张感、唤起同情、震撼读者）连接起来。
5. **准确使用恰当的分析术语**——不只是点出技巧，还要运用分析性词汇：“暗示”、“传达”、“蕴含”、“将读者置于……立场”。
6. **用嵌入式引文支撑分析**——挑选具有分析潜力的引文，而不是随手抓一句凑数。

### 前置知识与技能

**内容前置（学生必须知道什么）：**
- 掌握文学与语言技巧的工作词汇库（隐喻、明喻、拟人、头韵、重复、反问、短句、排比列举）——至少能一眼辨认 10 种技巧
- 理解作者做出的是刻意选择——语言是经过雕琢的，而非偶然
- 意识到不同体裁有不同目的（说服、告知、描写、议论、叙事），且技巧服务于目的

**技能前置（学生必须能够做什么）：**
- 阅读文本节选，找出显得重要或有趣的单个词语或短语（词级细读）
- 写出带有清晰论点且有证据支撑的段落
- 区分描述文本中发生了什么（内容概括）与解释文本是如何写成的（文本分析）

### 常见迷思概念

1. **“只找特征不作分析（Feature-spotting）。”** 最常见的错误。学生识别出技巧（“这里有一个隐喻”），但不解释其效果。他们被教会了**命名**技巧，却没学会**分析**技巧。这会产生类似这样的作答：“作者在‘dark, dangerous, deathly’中使用了头韵。这很有效。”识别正确，但分析缺失。

2. **“作者用这个是为了让读者想继续读下去。”** 套用在每一种技巧上的万能空洞效果声明。当学生不知道真正的效果是什么时，就会把这句话当成默认挡箭牌。它说明学生知道技巧会产生效果，但无法具体指明。

3. **“只做语言分析，忽视结构分析。”** 学生聚焦于单个词句（语言），却忽略文本是如何组织的（结构）。他们分析了第 3 段的隐喻，却没注意到第 3 段是一个紧接在长描写段之后的单句独立段——一个制造强烈冲击的结构选择。

4. **“把技巧当成分析本身。”** 学生写：“作者使用隐喻来表明……”仿佛点出技巧名字**就是**分析。技巧是“是什么（WHAT）”；分析是“如何（HOW）”和“为什么（WHY）”。说出“隐喻”只是识别；解释该隐喻如何营造特定意象或情绪才是分析。

### 成功标准

| 层级 | 学生的表现 |
|------|-----------|
| **初现（Emerging）** | 能识别部分语言特征（例如“作者使用了明喻”）。可能尝试描述效果，但退回到泛泛表述（“这很有效” / “这让读者想继续读下去”）。仅关注语言；结构分析缺失或流于表面。包含引文，但未融入分析之中。 |
| **发展（Developing）** | 能识别语言特征**并**开始解释具体效果（“‘cold as a gravestone’这个明喻暗示死亡，营造出令人不安的氛围”）。尝试结构分析，但可能偏向描述而非分析（“文本以一个问题开头”）。证据相关，但分析不够稳定——部分论点展开了，另一些则止步于识别。 |
| **胜任（Competent）** | 对语言**和**结构均展开分析，并对效果做出具体、充分展开的解释。将技巧与作者意图相联系（“Priestley 在督察讲话末尾使用短句‘We are responsible’，以更有力地传递道德讯息——这种简洁与 Birling 冗长空洞的发言形成对比，引导读者信任督察的清晰而非 Birling 的虚张声势”）。引文嵌入自然且精选得当。整篇作答分析连贯稳定。 |
| **拓展（Extending）** | 产出敏锐、原创的分析，能考量多种可能效果并评估哪种最有可能。分析语言与结构如何**协同运作**（“段末从流畅长句骤然切入直白短句的转换，恰如其分地映射了人物从否认到顿悟的情绪转折——结构本身正在演绎语言所描述的内容”）。可能探讨替代阐释。分析词汇精准且丰富多变。 |

### 教学启示

1. **最大的鸿沟在于从“识别”跨向“分析”。** 大多数学生能学会发现技巧；能解释效果的学生则少得多。教学应当在“这制造了什么效果？”上投入比“这是什么技巧？”多得多的时间。显性示范两者的差异：把“只找特征”的回答与“深度分析”的回答并排展示。

2. **结构分析必须与语言分析分开专门教授。** 学生默认倾向于词句级分析，因为它具体可见。结构（段落组织、全篇模式、关键时刻的位置安排）更抽象，需要不同的分析视角——把文本作为一个整体来审视，而不是放大到单个短语。

3. **成功标准应在学生动笔**之前**与学生共享。** 这四个层级的描述可以用作自我评估工具：“读一遍你的作答。你处于发展层级（能命名技巧但并非总能解释效果），还是胜任层级（持续解释技巧如何制造具体效果）？你需要补充什么才能向上跨一级？”

---

## 已知局限

1. **拆解反映的是该年级对该能力的一般性期待。** 具体考试局、课程大纲或学校政策可能对该能力有不同界定，或侧重不同要素。教师应将拆解结果对照自身具体评估框架并在需要处调整。

2. **四层级成功标准必然简化了连续谱。** 学生作品存在于连续谱上，而非整齐划一的格子里。有些作答可能语言分析达到胜任层级，而结构分析处于初现层级。层级是反馈指南，而非僵化分类——当一份作答跨越多个层级时，教师必须运用专业判断。

3. **列出的常见迷思概念是最常见的，而非全部可能的。** 个别学生可能基于先前的教学、母语背景或概念框架持有不同迷思。所列迷思概念应被视为诊断性评估的起点，而非穷尽清单。
