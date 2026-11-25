---
# AGENT SKILLS STANDARD FIELDS (v2)
name: text-complexity-analyser
description: "从量化、质性以及读者-任务三个维度分析文本复杂度，并提供支架设计建议。适用于文本筛选、可读性评估或阅读支持规划。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "literacy-critical-thinking/text-complexity-analyser"
skill_name: "文本复杂度分析与支架设计器"
domain: "literacy-critical-thinking"
version: "1.0"
evidence_strength: "strong"
evidence_sources:
  - "Shanahan et al. (2012) — An analysis of text complexity progression in CCSS"
  - "Hiebert (2012) — Seven actions that teachers can take right now: text complexity"
  - "Fisher & Frey (2012) — Text complexity: raising rigour in reading"
  - "Beck et al. (2013) — Bringing Words to Life: robust vocabulary instruction"
  - "Graves & Graves (2003) — Scaffolding Reading Experiences: designs for student success"
input_schema:
  required:
    - field: "text_description"
      type: "string"
      description: "文本描述，包括体裁、主题、大致篇幅及来源"
    - field: "student_level"
      type: "string"
      description: "年龄/年级及当前阅读水平"
    - field: "reading_purpose"
      type: "string"
      description: "学生阅读该文本的目的——该阅读所支持的任务"
  optional:
    - field: "text_extract"
      type: "string"
      description: "用于更精确分析的文本节选"
    - field: "student_profiles"
      type: "array"
      description: "来自上下文引擎：阅读水平、EAL 状态、背景知识"
    - field: "subject_area"
      type: "string"
      description: "课程学科背景"
    - field: "known_challenges"
      type: "string"
      description: "教师预期的该文本具体难点"
output_schema:
  type: "object"
  fields:
    - field: "complexity_analysis"
      type: "object"
      description: "涵盖量化、质性与读者-任务维度的分析"
    - field: "scaffold_plan"
      type: "object"
      description: "针对已识别复杂度定制的读前、读中、读后支架"
    - field: "vocabulary_focus"
      type: "array"
      description: "需预先教授的核心词汇，按优先级分层"
    - field: "differentiation"
      type: "object"
      description: "针对不同阅读水平学生的调整方案"
chains_well_with:
  - "reading-comprehension-strategy-selector"
  - "vocabulary-tiering-tool"
  - "scaffolded-task-modifier"
  - "cognitive-load-analyser"
teacher_time: "4 分钟"
tags: ["text-complexity", "reading", "scaffolding", "vocabulary", "differentiation"]
---

# 文本复杂度分析与支架设计器

## 本技能的功能

从三个维度评估文本复杂度——量化维度（句长、词频）、质性维度（结构、意义层次、知识需求）以及读者-任务维度（文本要求与特定读者及阅读目的之间的互动）——并生成一套针对所识别具体复杂度挑战的读前、读中、读后定制支架。与仅依赖可读性公式（只测量量化特征）的做法不同，本分析会考量文本是否存在需要推理的隐含意义、是否预设了学生可能缺乏的背景知识、结构是否熟悉，以及词汇需求主要属于第二层级（学术词汇）还是第三层级（专业术语）。AI 在此处具有独特价值，因为文本复杂度是多维度的——一段文本可能在量化上简单但在质性上复杂（例如句子简短但具有深层比喻意义的诗歌），支架必须针对**真实的**复杂度，而不仅仅是阅读难度数值。

## 循证基础

Shanahan 等人（2012）分析了文本复杂度进阶规律，确立了有效的文本选择与支架搭建需要三维模型：量化指标（词频、句长、文本长度）、质性维度（意义层次、文本结构、语言常规性、知识需求）以及读者-任务考量（特定读者的背景知识、动机及阅读目的）。仅依赖量化指标（如 Flesch-Kincaid）会产生误导结果——海明威的散文尽管在质性上很复杂，但在可读性公式中却得分“容易”。Hiebert（2012）明确了教师可采取的应对文本复杂度的具体行动，强调支架应针对构成最大挑战的具体复杂度维度——对于复杂度在于结构的文本提供词汇支架属于支持错位。Fisher 与 Frey（2012）开发了一个通过适当支架提升阅读严谨性的实用框架：不是简化文本，而是提供学生接触复杂文本所需的支持。Beck 等人（2013）证明，词汇教学在聚焦于第二层级词汇（跨学科出现的高效用学术词汇）而非第三层级词汇（特定学科的技术词汇），并在语境中通过多次接触进行教学时最为有效。Graves 与 Graves（2003）确立了支架式阅读体验（Scaffolded Reading Experience）模型：读前活动（激活先前知识、建构背景、预教词汇）、读中活动（引导性问题、出声思考、文本批注）和读后活动（讨论、写作、应用）。

## 输入模式

教师必须提供：
- **文本描述：** 学生将阅读的内容。*例如：“Louis Sachar《Holes》第3章——约1,200词，双时间线叙事小说” / “一篇关于光合作用的 BBC Bitesize 文章——500词，带图表的说明文” / “十年级历史史料手册节选——一战士兵的一封原始书信，约300词”*
- **学生水平：** 年级与阅读水平。*例如：“七年级，混合能力——阅读年龄跨度为9至14岁”*
- **阅读目的：** 学生阅读的原因。*例如：“识别 Sachar 如何利用双时间线制造悬念” / “提取光合作用的关键阶段以绘制总结图” / “从一手史料中推断战壕中的真实生活”*

可选（如有，由上下文引擎注入）：
- **文本节选：** 用于更精确分析的一小段节选
- **学生档案：** 阅读水平、EAL 状态、背景知识
- **学科领域：** 课程学科
- **已知挑战：** 预期的困难

## 提示词

```
You are an expert in text complexity analysis and reading scaffolding, with deep knowledge of Shanahan et al.'s (2012) three-dimensional text complexity model, Hiebert's (2012) practical approaches to text complexity, Fisher & Frey's (2012) scaffolding framework, and Graves & Graves' (2003) Scaffolded Reading Experience model. You understand that text complexity is NOT a single number — it's a multi-dimensional interaction between the text's features, the reader's capabilities, and the task's demands.

Your task is to analyse text complexity and design reading scaffolds for:

**Text description:** {{text_description}}
**Student level:** {{student_level}}
**Reading purpose:** {{reading_purpose}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Text extract:** {{text_extract}} — if provided, use it for specific, grounded analysis. If not, base your analysis on the text description and your knowledge of the genre and topic.
**Student profiles:** {{student_profiles}} — if not provided, design for a mixed-ability class with reading ages spanning approximately 2 years below to 2 years above chronological age.
**Subject area:** {{subject_area}} — if not provided, infer from the text description.
**Known challenges:** {{known_challenges}} — if not provided, identify the most likely challenges based on the text description and student level.

Apply these evidence-based principles:

1. **Three-dimensional complexity analysis (Shanahan et al., 2012):**

   **Quantitative dimensions:**
   - Sentence length and complexity (simple, compound, complex)
   - Vocabulary frequency (common words vs. uncommon/academic/technical)
   - Text length relative to the reading task
   - Estimate difficulty relative to the stated student level.

   **Qualitative dimensions:**
   - Levels of meaning: Is meaning explicit or implicit? Are there figurative, ironic, or symbolic layers?
   - Text structure: Is the structure familiar (chronological, cause-effect) or unfamiliar (non-linear, fragmented, multiple embedded structures)?
   - Language conventionality: Is the language modern and standard, or archaic, dialectal, or highly figurative?
   - Knowledge demands: What background knowledge (cultural, historical, scientific, literary) does the text assume?

   **Reader-task dimensions:**
   - What is the gap between what these specific readers know and what the text requires?
   - Does the reading purpose require surface comprehension or deep analysis?
   - What reader motivation or engagement factors are relevant?

2. **Match scaffolds to the specific complexity dimension (Hiebert, 2012):**
   - If the main complexity is VOCABULARY: pre-teach key words, provide a glossary, use context clue instruction.
   - If the main complexity is STRUCTURE: provide a text map or graphic organiser, teach the text structure explicitly.
   - If the main complexity is KNOWLEDGE DEMANDS: build background knowledge before reading, provide context-setting information.
   - If the main complexity is IMPLICIT MEANING: teach inference strategies, model think-alouds at key inference points.
   - Do NOT apply all scaffold types regardless of the complexity profile — target the scaffolds.

3. **Scaffold the reader, not the text (Fisher & Frey, 2012):**
   - The goal is NOT to simplify the text but to give students the support needed to access complex text.
   - Scaffolds should be temporary — they support initial engagement and are progressively removed.
   - Maintaining text complexity is essential for growth; oversimplification reduces learning.

4. **Before-during-after structure (Graves & Graves, 2003):**
   - Before reading: address the most significant barrier to comprehension BEFORE students encounter it.
   - During reading: provide guided support at the specific points where complexity peaks.
   - After reading: extend comprehension through discussion, writing, or application.

5. **Vocabulary focus (Beck et al., 2013):**
   - Identify key vocabulary, prioritising Tier 2 words (high-utility academic vocabulary) over Tier 3 (technical terms that can be defined quickly).
   - Recommend which words to pre-teach (essential for comprehension) and which to address during reading (can be inferred from context with support).

Return your output in this exact format:

## Text Complexity Analysis: [Text title/description]

**For:** [Student level]
**Text:** [Brief description]
**Reading purpose:** [Purpose]

### Complexity Profile

**Quantitative:** [Analysis of sentence length, vocabulary frequency, text length — with estimated difficulty rating for these students]
**Qualitative — Levels of meaning:** [Explicit vs. implicit, figurative language, irony, symbolism]
**Qualitative — Text structure:** [Familiar vs. unfamiliar structure, navigational demands]
**Qualitative — Language conventionality:** [Standard vs. archaic, dialectal, figurative]
**Qualitative — Knowledge demands:** [Background knowledge assumed by the text]
**Reader-task:** [Gap between what these readers know and what the text requires, given the reading purpose]

**Primary complexity challenge:** [The single most significant barrier to comprehension for these students — this determines the scaffold focus]

### Vocabulary Focus

**Pre-teach (essential for comprehension):** [Words to teach BEFORE reading, with brief definitions]
**Address during reading (can be supported in context):** [Words that can be clarified as students encounter them]

### Scaffold Plan

**Before Reading (X minutes)**
[Scaffolds targeting the primary complexity challenge — building background, pre-teaching vocabulary, setting purpose, introducing text structure]

**During Reading (X minutes)**
[Scaffolds for specific complexity peaks — guiding questions, annotation prompts, think-aloud points, glossary use]

**After Reading (X minutes)**
[Scaffolds extending comprehension — discussion, writing, application tasks]

### Differentiation

**Support (for below-level readers):** [Additional scaffolds — paired reading, audio support, reduced section, sentence frames for responses]
**Extension (for above-level readers):** [Reduced scaffolds, additional analytical questions, independent reading of related text]

**Self-check before returning output:** Verify that (a) the complexity analysis covers all three dimensions, (b) the primary complexity challenge is clearly identified, (c) scaffolds are targeted to the specific complexity rather than generic, (d) scaffolds support access to the complex text rather than simplifying it, (e) vocabulary is prioritised by Tier and necessity, and (f) the before-during-after structure addresses complexity at the right points in the reading process.
```

## 示例输出

**场景：** *文本描述：“一战士兵家书节选（一手史料）——约300词，写于1916年，描述战壕状况。语言相对简单，但包含时代词汇和委婉语。信件语气乐观，这与学生所知的战壕状况相矛盾。” / 学生水平：“九年级，混合能力——大多数学生能流畅阅读，但接触一手史料的经验有限” / 阅读目的：“通过字里行间推断战壕生活的真实面貌——理解为什么信件的语气可能无法反映真实经历，因为信件受到审查且士兵不想让家人担心”*

---

## 文本复杂度分析：一战士兵书信（一手史料）

**适用对象：** 九年级历史
**文本：** 约1916年一战士兵的一手书信史料，约300词
**阅读目的：** 通过字里行间推断战壕状况的真实面貌——理解为什么信件的语气可能并不反映士兵的真实经历

### 复杂度画像

**量化维度：** 中低难度。句子相对较短且语法结构简单——这是一封私人书信，而非正式文本。词汇多为常用词，仅含少量时代特定术语。文本长度（300词）易于掌控。仅靠量化指标会将该文本评定为“容易”。

**质性维度——意义层次：** **高复杂度。** 这正是真正的难点所在。文本具有两层意义：表层意义（士兵写了什么）与隐含意义（实际状况如何）。士兵写道“我们一直保持愉快”（"We are keeping cheerful"）——但读者必须推断这可能是一种委婉表达，或是为了特定受众（家乡的亲人）而进行的“表演”。表层意义与隐含意义之间的落差**就是**文本的核心——只读字面意思的学生将完全误解这份史料。

**质性维度——文本结构：** 低复杂度。书信遵循熟悉的结构（问候、近况、安抚、落款），没有阅读导航障碍。

**质性维度——语言常规性：** 中等复杂度。语言总体易懂，但包含时代表达（"in good spirits"、"doing our bit"、"Fritz"）以及需要结合语境理解的委婉语。语域非正式且偏向口语化——比许多历史文献更接近现代英语。

**质性维度——知识需求：** 中高复杂度。学生需要了解：（1）前线寄出的信件会受到军官审查；（2）士兵常常淡化恶劣状况以避免家人担忧；（3）战壕的实际状况是怎样的（从而识别信件与现实之间的落差）。若缺乏这些背景知识，学生会按字面意思理解信件，并得出战壕生活“还不错”的结论。

**读者-任务维度：** **高难度。** 该阅读目的要求对史料可靠性进行推理与批判性评估——而不仅仅是理解字面内容。九年级学生能读懂字词，但未必会自发质疑信件的语气。关键落差在于他们默认的阅读方式（全盘接受文本所说）与任务要求（质疑文本为何如此表述）之间的差距。

**主要复杂度挑战：** 意义层次——表层语气与隐含现实之间的落差。除非明确教导学生读出言外之意，否则学生会按字面意思理解士兵乐观的措辞。知识需求（理解战时书信审查及写信的社会语境）进一步加剧了这一挑战。

### 词汇重点

**读前预教（理解文本所必需）：**
- *censorship（审查制度）*——军事当局会阅读士兵的信件，并涂黑任何暴露位置、恶劣状况或士气问题的内容。这是理解**为什么**信件听起来很乐观的关键背景。
- *euphemism（委婉语）*——当现实严酷时，用温和或正面的说法来表达。“我们遇上了点坏天气”可能意味着“我们在齐膝深的泥泞里站了三天”。

**读中处理（可在语境中提供支持）：**
- *Fritz*——对德国士兵的俚语称呼（可在页边加注）
- *doing our bit*——时代常用语，意为“为战争尽自己的一份力”
- *Blighty*——指代英国/家乡的俚语
- *in good spirits*——在讨论中作为可能的委婉语加以探讨

### 支架计划

**读前（8分钟）**

1. *建构关键背景知识（5分钟）：*
“在我们读这封信之前，你们需要知道两件事，它们会彻底改变你们理解这封信的方式。”

事实一：“士兵寄回家的每一封信都会被审查官阅读。如果你写了任何关于生活条件、士气或战事的负面内容，就会被墨水涂黑。所以士兵即使想说真话也**不能**写。”

事实二：“即使没有审查制度，大多数士兵也不想让家人惊恐万分。你会给妈妈写信说‘我周围都是死亡，我吓坏了’吗？还是会说‘我很好，别担心’？”

“因此，当我们读这封信时，我们要问：士兵是在告诉我们**真实**发生的事情——还是在告诉我们他**被允许**说的话以及他**希望**家人听到的话？”

2. *设定阅读目的（2分钟）：*
“你们的任务**不是**找出士兵说了什么。你们的任务是找出他**没说**什么——乐观话语背后藏着什么。每次他说正面内容时，我都要你们问：现实到底可能是怎样的？”

3. *布置批注任务（1分钟）：*
给学生两支不同颜色的笔：一种用于“他写了什么”，另一种用于“现实可能是什么”。他们将用双色批注整封信。

**读中（10分钟）**

*第一遍阅读（5分钟）：* 学生独立阅读信件。暂不做批注，只管通读。

*第二遍结合批注阅读（5分钟）：* 学生重读并用双色笔批注：
- 颜色1：划出士兵所写的听起来积极或令人安心的语句。
- 颜色2：在页边空白处写下现实可能是什么。

特定节点引导提示：
- 当士兵写到 "keeping cheerful" 时 → 页边提示：“他为什么可能这样写？‘cheerful’ 掩盖了什么？”
- 当士兵随意提及食物或天气时 → 页边提示：“这是全貌吗？你对战壕状况了解多少？”
- 当士兵说 "don't worry" 时 → 页边提示：“如果一切都好，他还需要特意说这句话吗？”

**读后（7分钟）**

1. *同伴讨论（3分钟）：* “与同伴比较批注。士兵**真正**想表达什么？找出他所写内容与你们认为的现实之间落差最大的一处。”

2. *全班讨论（4分钟）：* “这封信能告诉我们关于战壕状况的什么信息——又**不能**告诉我们什么？为什么即使士兵没有说出全部真相，这份史料依然很有价值？”

引导学生得出核心历史洞察：这封信告诉了我们作为一名士兵的**体验**（保持乐观的压力、保护家人的愿望、审查制度的限制），即便它并没有准确描述物质条件。

### 差异化教学

**支持（针对阅读水平低于年级标准的学生或 EAL 学生）：**
- 在信件旁提供时代词汇表。
- 预先批注 2–3 个示例：展示一句乐观陈述及页边提示的可能现实，由学生独立完成其余批注。
- 与阅读自信的同伴结对完成批注任务。
- 为页边批注提供句式框架：“他说 ___，但现实可能是 ___，因为 ___。”

**拓展（针对阅读水平高于年级标准的学生）：**
- 撤除批注支架——挑战学生独立识别表层与现实之间的落差。
- 提供另一名士兵的第二封信（或未经审查的日记条目）进行对比：“这则私人日记与寄回家的信有何不同？这种差异说明了家信作为史料的什么特点？”
- 提问：“如果你是一名历史学家，你会如何使用这封信作为证据？它能可靠地告诉你什么，又不能告诉你什么？”

---

## 已知局限

1. **在没有文本节选的情况下，分析基于文本描述与体裁知识。** 当提供实际文本节选时，复杂度画像会更加准确。教师应将分析与具体文本进行对照，并在分析与实际不符处调整支架。

2. **该分析识别的是文本复杂度，但无法测量单个学生的阅读水平。** 支架建议是针对所陈述的学生水平设计的，但班内单个学生在阅读能力、背景知识和参与度上各有不同。教师必须基于对具体学生的了解，在支架计划内部进行差异化调整。

3. **文本复杂度具有情境依赖性。** 同一文本在一种阅读目的下可能很简单，在另一种目的下却可能很复杂——出于消遣阅读一首诗与分析其比喻语言，所需的理解要求截然不同。本分析针对所陈述的阅读目的；若改变阅读目的，复杂度画像与支架建议也随之改变。
