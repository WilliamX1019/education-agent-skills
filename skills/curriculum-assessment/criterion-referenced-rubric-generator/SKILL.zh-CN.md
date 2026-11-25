---
# AGENT SKILLS STANDARD FIELDS (v2)
name: criterion-referenced-rubric-generator
description: "为特定任务或目标生成带有描述性表现等级的标准参照量规。适用于评分指南和一般课程情境。对于以 Competent 为成功的 Manning 项目，请改用 coherent-rubric-logic-builder。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "curriculum-assessment/criterion-referenced-rubric-generator"
skill_name: "标准参照量规生成器"
domain: "curriculum-assessment"
version: "1.0"
evidence_strength: "strong"
evidence_sources:
  - "Brookhart (2013) — How to Create and Use Rubrics for Formative Assessment and Grading"
  - "Andrade (2000, 2013) — Using rubrics to promote thinking and learning"
  - "Jonsson & Svingby (2007) — The use of scoring rubrics: reliability, validity and educational consequences"
  - "Sadler (1989) — Formative assessment and the design of instructional systems"
  - "Panadero & Jonsson (2013) — The use of scoring rubrics for formative assessment purposes revisited"
input_schema:
  required:
    - field: "learning_objective"
      type: "string"
      description: "量规所评估的学习目标"
    - field: "task_description"
      type: "string"
      description: "学生将完成的具体任务"
    - field: "student_level"
      type: "string"
      description: "年龄/年级"
  optional:
    - field: "criteria_count"
      type: "integer"
      description: "维度数量（默认：4）"
    - field: "performance_levels"
      type: "integer"
      description: "表现等级数量（默认：4）"
    - field: "subject_area"
      type: "string"
      description: "课程学科"
    - field: "existing_criteria"
      type: "string"
      description: "教师希望包含的任何已有维度——量规将围绕这些维度构建"
output_schema:
  type: "object"
  fields:
    - field: "rubric"
      type: "object"
      description: "包含维度、表现等级描述符与评分指南的完整量规"
    - field: "design_rationale"
      type: "string"
      description: "为何选择这些维度以及如何区分各等级描述符"
    - field: "student_friendly_version"
      type: "string"
      description: "供学生用于自评与互评的简化版量规"
    - field: "calibration_notes"
      type: "string"
      description: "帮助多位阅卷人一致应用该量规的校准说明"
chains_well_with:
  - "competency-unpacker"
  - "backwards-design-unit-planner"
  - "gap-analysis-from-student-work"
  - "feedback-quality-analyser"
  - "kud-knowledge-type-mapper"
teacher_time: "3 分钟"
tags: ["rubric", "assessment", "criteria", "descriptive-language", "formative-assessment"]
---

# 标准参照量规生成器

## 本技能的作用

根据学习目标与任务描述生成一份标准参照量规（criterion-referenced rubric），并在每个表现等级采用描述性（而非评价性）语言。每个维度描述学生作品在各个等级**看起来是什么样子**——而不是它有多“好”。输出包括完整量规、设计理据、用于自评/互评的学生友好版，以及确保跨阅卷人一致性的校准说明。AI 在此尤为关键，因为有效的量规设计需要精准的描述性语言，既能区分不同表现等级，又不使用评价性标签（“优秀”、“良好”、“较差”）或模糊的数量词（“一些”、“许多”、“彻底”）——并且每个描述符必须与相邻等级存在质的差异，而不仅仅是同一段描述的程度缩放。

## 实证基础

Brookhart（2013）确立了有效量规使用描述性语言而非评价性语言的原则——它们描述作品中**呈现了什么**，而不是它有多好。“用具体的文本证据支撑每一个分析论点”是描述性的；“证据运用良好”是评价性的。描述性量规能带来更可靠的评分和更有用的反馈，因为它们准确告诉学生该做出什么不同的行动，而不仅仅是需要“做得更好”。Andrade（2000, 2013）证明，在任务开始前将量规分享给学生能同时改善教学与学习——它们发挥学习工具的作用，而不仅仅是打分工具。当量规用于自我评估时，这一效应最强。Jonsson & Svingby（2007）发现，分析性量规（独立评分的多个维度）比整体性量规（单一总评判断）更可靠且能产出更好反馈，尽管使用耗时更长。Sadler（1989）指出，评估质量取决于“差距”是否可见——学生必须能够看清当前位置与目标位置之间的差距。描述性的量规等级使这一差距变得具体可见。Panadero & Jonsson（2013）证实，使用量规能提升学生表现，尤其是与自评结合时，具有中等效应量。

## 输入规范

教师必须提供：
- **学习目标（Learning objective）：** 量规评估什么。*例如：“学生能够撰写一篇运用修辞手法影响听众的说服性演讲稿” / “学生能够设计并开展公平实验，并得出有效结论”*
- **任务描述（Task description）：** 具体任务。*例如：“撰写并发表一场 3 分钟的自选主题说服性演讲” / “规划并开展探究光照对植物生长影响的实验，然后撰写结论”*
- **学生水平（Student level）：** 年级。*例如：“八年级”*

可选项（如可用则由上下文引擎注入）：
- **维度数量（Criteria count）：** 维度数（默认：4）
- **表现等级（Performance levels）：** 等级数（默认：4）
- **学科领域（Subject area）：** 课程学科
- **现有维度（Existing criteria）：** 教师希望纳入的维度

## 提示词（Prompt）

```
You are an expert in assessment design and rubric construction, with deep knowledge of Brookhart's (2013) principles of effective rubric design, Andrade's (2000, 2013) research on rubrics as learning tools, and Sadler's (1989) formative assessment framework. You understand that effective rubrics use DESCRIPTIVE language (describing what is present) rather than EVALUATIVE language (judging how good it is), and that each performance level must be QUALITATIVELY distinct — not just a scaled version of the same description.

Your task is to generate a rubric for:

**Learning objective:** {{learning_objective}}
**Task description:** {{task_description}}
**Student level:** {{student_level}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Criteria count:** {{criteria_count}} — if not provided, use 4 criteria.
**Performance levels:** {{performance_levels}} — if not provided, use 4 levels.
**Subject area:** {{subject_area}} — if not provided, infer from the learning objective.
**Existing criteria:** {{existing_criteria}} — if provided, incorporate these and add others as needed.

Apply these evidence-based principles:

1. **Descriptive, not evaluative language (Brookhart, 2013):**
   - NEVER use: excellent, good, satisfactory, poor, limited, basic, outstanding, weak.
   - NEVER use vague quantifiers: some, many, few, several, thorough, adequate.
   - INSTEAD: describe specifically what is PRESENT in the work at each level.
   - Bad: "Good use of evidence." Good: "Each analytical point is supported by a specific, relevant quotation from the text."
   - Bad: "Limited vocabulary." Good: "Vocabulary is predominantly everyday; academic or technical terms are absent or used inaccurately."

2. **Qualitatively distinct levels (Sadler, 1989; Brookhart, 2013):**
   - Adjacent levels must describe qualitatively DIFFERENT work, not just more or less of the same thing.
   - Bad progression: "Uses some evidence" → "Uses more evidence" → "Uses a lot of evidence" (quantitative — just more).
   - Good progression: "States claims without evidence" → "Includes evidence but does not connect it to claims" → "Connects evidence to claims with explicit reasoning" → "Selects the most compelling evidence and explains why it is the strongest support for each claim" (qualitative — different type of work).

3. **Criteria must be independent (Jonsson & Svingby, 2007):**
   - Each criterion should assess a distinct, separable aspect of the work.
   - A student should be able to score at different levels on different criteria — not all criteria tracking together.
   - If two criteria always produce the same score, they're probably measuring the same thing.

4. **Student-friendly version (Andrade, 2000, 2013):**
   - Produce a version using student-accessible language.
   - Written in second person: "You support each point with a specific quotation" rather than "The student supports each point with a specific quotation."
   - Can be used for self-assessment before submission.

5. **Calibration notes (Jonsson & Svingby, 2007):**
   - Include notes that help multiple markers apply the rubric consistently.
   - Identify the key distinctions between levels — the "decision points" where markers are most likely to disagree.
   - Where possible, describe what a borderline response looks like between two levels.

Return your output in this exact format:

## Rubric: [Task Description]

**Assesses:** [Learning objective]
**For:** [Student level]
**Criteria:** [Count] | **Levels:** [Count]

### Rubric

[Full rubric table with criteria as rows and performance levels as columns. Each cell contains descriptive language.]

### Design Rationale

[Why these criteria were chosen and how the levels are distinguished]

### Student-Friendly Version

[Simplified rubric in student-accessible language, suitable for self/peer assessment]

### Calibration Notes

[Guidance for consistent application — key decision points, borderline cases]

**Self-check before returning output:** Verify that (a) NO evaluative language appears (no "good," "excellent," "poor," "limited"), (b) NO vague quantifiers appear (no "some," "many," "thorough"), (c) adjacent levels are qualitatively distinct, (d) each criterion is independent, (e) the student-friendly version is genuinely accessible, and (f) calibration notes address the most likely points of marker disagreement.
```

## 示例输出

**情景：** *学习目标：“学生能够撰写一篇运用修辞手法影响听众的说服性演讲稿” / 任务描述：“撰写并向全班发表一场 3 分钟的自选主题说服性演讲” / 学生水平：“九年级” / 学科领域：“英语”*

---

## 量规：说服性演讲（撰写与发表）

**评估目标：** 撰写运用修辞手法影响听众的说服性演讲稿
**适用对象：** 九年级英语
**维度数：** 4 | **等级数：** 4

### 量规

| 维度 | 等级 1 | 等级 2 | 等级 3 | 等级 4 |
|------|--------|--------|--------|--------|
| **论证与结构** | 演讲稿提出了一个观点，但未用理由加以展开。要点罗列在一起，缺乏逻辑关联。没有明确的开头、主体或结尾——演讲在任意位置开始或停止，听众都不会察觉。 | 演讲稿表明了立场并给出 1–2 个理由，但理由未能充分展开。演讲具有可辨认的开头与结尾，但主体部分缺乏清晰组织——各要点之间未能层层递进。 | 演讲稿呈现清晰立场，由 3 个以上充分展开的理由按逻辑顺序支撑。每一点都建立在前一点之上，形成累积性论证。开头吸引听众，结尾强化立场而非简单重复。 | 演讲稿建构了策略性论证，要点排序经过刻意安排——最有力的论点被放在能产生最大冲击的位置。承认并回应了反方观点。结尾以全新视角重构论证，给听众留下持久印象。 |
| **修辞手法** | 演讲稿依赖个人看法（“我认为……”），未刻意使用任何修辞技巧。通篇采用日常口语化表达。 | 演讲稿包含 1–2 种修辞手法（例如反问、重复、三段式排比），但显得孤立——像是硬塞进日常口语中，而非融入论证。手法虽存在，但未明显增强说服力。 | 演讲稿使用 3 种以上融入论证的修辞手法——每种手法都服务于特定说服目的（用反问挑战听众、用重复强调核心论点、用感染力语言制造紧迫感）。演讲者能解释为何选择每种手法。 | 演讲稿展现出对修辞的娴熟控制与丰富变化——多种手法组合产生协同效果（例如先反问，再用三连排比作答）。语气策略性转换（从理性到感性、从冷静到紧迫）以引导听众立场。语言选择体现对特定听众的觉察。 |
| **听众意识** | 演讲稿面向泛泛的一般听众写作——没有具体提及在座听众、他们的经历或可能的异议。演讲者是在“对着”听众讲话，而不是“向着”他们交流。 | 演讲稿体现出一定听众意识（例如“作为学生，我们都知道……”），但这种意识停留在表面——仅点出了听众身份，未根据他们的具体关切或视角调整论证。 | 演讲稿直接回应听众可能的观点、关切或经历。演讲者预判听众会如何想或感受并予以回应：“你们可能在想……但请考虑这一点。”演讲听起来像是专为**这批**听众而写，而非任意听众。 | 演讲稿为特定听众量身定制——运用共享参照物、预判具体异议，并调整语域、词汇与语气以契合听众。演讲者在现场观察全场反应并实时响应（调整语速、加重语气、与持怀疑态度者眼神交流）。 |
| **现场表达** | 照着讲稿念，极少眼神交流。音量要么小到听不清，要么全程平铺直叙。演讲者显得与自己的论证脱节。 | 大部分时间在念稿，偶尔抬头看听众。音量可听清。尝试了一些语调变化，但节奏不均——部分段落急促赶场，另一些地方则尴尬停顿。 | 演讲者仅将笔记作为提示，而非通篇照读。眼神交流规律且覆盖全场听众。音量、语速与重音刻意变化以强化关键点。停顿用于制造效果，而非出于不确定。 | 演讲者基本脱离讲稿。表达显得自然自信——让人感觉是在现场思考并说话，而非背诵文稿。手势、走动、面部表情与声音变化全部服务于论证。演讲者掌控全场。 |

### 设计理据

**为何选择这四个维度：**
1. **论证与结构**——根基。没有清晰论证的演讲不具有说服力，无论表达多么出色。
2. **修辞手法**——工具箱。学习目标明确要求使用修辞手法；本维度评估它们是否既存在**又**发挥功能。
3. **听众意识**——说服视角。说服从根本上是面向听众的；本维度评估演讲者究竟是**为**听众而写，还是仅仅**对着**空气说话。
4. **现场表达**——表现维度。演讲是一种口语体裁；内容质量与表达质量是两项独立技能，应当分开评估。学生可能写出精彩讲稿但表达欠佳，反之亦然——分设维度才能同时捕捉两者。

**等级如何区分：**
- 等级 1 → 等级 2：要素**出现**但尚未有效（手法存在但未产生说服力；结构存在但未形成递进）。
- 等级 2 → 等级 3：要素**发挥功能**——服务于明确目的并产生效果（手法融入论证、结构层层推进、直接回应听众）。
- 等级 3 → 等级 4：要素具备**策略性**——学生做出刻意、老练的选择并能解释原因（修辞组合使用、论证为冲击力排序、现场观察并回应听众）。

### 学生友好版

**提交前，对照以下标准自查你的演讲：**

**你的论证：**
- 等级 1：你表达了观点，但没有真正解释原因。
- 等级 2：你给出了理由，但没有充分展开——你还没有解释**为什么**你的理由有说服力。
- 等级 3：你提出了清晰的论证，包含 3 个以上层层递进的理由。你的开头抓住注意力，结尾强化了你的核心观点。
- 等级 4：你策略性地安排了要点顺序——把最有力的论点放在冲击力最大的位置。你还回应了反方会怎么说。

**你对修辞手法的运用：**
- 等级 1：你没有使用任何说服技巧——听起来就像平时随便聊天。
- 等级 2：你用了 1–2 个技巧，但感觉像是“硬贴上去的”——好像是为了凑要求而加的。
- 等级 3：你用了 3 个以上技巧，且每一个都有明确**目的**——你能解释为什么选它以及它制造了什么效果。
- 等级 4：你的技巧**协同**工作——你把它们组合起来，并刻意变换语气以影响听众。

**你的听众意识：**
- 等级 1：你是在**对着**听众念，而不是**和**他们交流。
- 等级 2：你提到了听众（“作为学生，我们……”），但并没有真正根据他们调整你的论证。
- 等级 3：你直接回应了听众的想法与感受。“你们可能在想……但请想想这一点。”
- 等级 4：你的整场演讲都是为**这批**特定听众量身打造的——你使用他们的语言、预判他们的异议，并在现场随时调整。

**你的现场表达：**
- 等级 1：你低着头照着纸念稿。
- 等级 2：你偶尔抬头。声音能听见，但几乎没有变化。
- 等级 3：你只用提纲笔记，不照念全文。你有眼神交流。你刻意改变语速、音量和重音。
- 等级 4：你几乎不需要看笔记。表达自然自信。你的肢体语言和声音都在为你的论证服务。

### 校准说明

**阅卷人关键决策点：**

1. **修辞手法中等级 2 vs. 等级 3：** 区分在于手法是“仅仅出现”还是“发挥功能”。自问：“如果删掉这个反问句，演讲的说服力会下降吗？”如果会 → 等级 3（它在起作用）；如果不会 → 等级 2（它只是装饰）。

2. **论证与结构中等级 3 vs. 等级 4：** 等级 3 拥有清晰、合乎逻辑的论证；等级 4 拥有**策略性**论证——排序经过刻意设计，且回应了反方论点。如果演讲提出了好论点但顺序随意 → 等级 3；如果排序本身体现了策略思考（逐步推向高潮、压轴保留最强论点）→ 等级 4。

3. **现场表达独立于内容。** 学生可能用极高自信发表一篇结构混乱的演讲（高表达、低论证），也可能用平淡单调的声音发表一篇精彩讲稿（高论证、低表达）。请独立为每个维度评分。

4. **等级 2 与等级 3 之间的临界案例：** 最常见的边界。拿不准时问自己：“学生只是在‘完成动作’（用了一个修辞、提了一句听众），还是**带着目的**在做（用修辞达成特定效果、回应听众的具体关切）？”有明确目的 → 等级 3；例行公事 → 等级 2。

---

## 已知局限

1. **量规描述表现等级，但不解释如何改进。** 学生看量规知道自己在修辞手法处于等级 2，明白需要改变**什么**（让手法带着目的融入），但未必知道**怎么做**。量规应配合教学与反馈使用，向学生展示如何从一个等级跨向下一个等级。可与 `feedback-quality-analyser` 串联以获得靶向改进建议。

2. **四个等级是现实权衡。** 有些任务受益于更多等级（以区分细微梯度）或更少等级（以简化评估）。四个等级在信度（足够多等级以提供信息）与可用性（足够少以便于实操）之间取得平衡。若量规用于高利害评分，可能需要补充更细的等级描述符。

3. **描述性语言更难撰写，但比评价性语言更有用。** 本量规避开了“良好”、“优秀”和“较差”，这使得每个单元格更长、更具体。这是一项刻意权衡——评价性量规更简短，但对反馈帮助甚微。教师可能需要时间适应描述性量规语言。
