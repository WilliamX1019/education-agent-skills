---
# AGENT SKILLS STANDARD FIELDS (v2)
name: vocabulary-tiering-tool
description: "将文本或主题中的词汇划分为日常词汇（Tier 1）、学术词汇（Tier 2）和专业词汇（Tier 3），并确定教学优先级。适用于预教词汇或识别文本中的语言障碍时。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "eal-language-development/vocabulary-tiering-tool"
skill_name: "词汇分级工具"
domain: "eal-language-development"
version: "1.0"
evidence_strength: "strong"
evidence_sources:
  - "Beck, McKeown & Kucan (2002, 2013) — Bringing Words to Life: robust vocabulary instruction"
  - "Nation (2001) — Learning Vocabulary in Another Language"
  - "Coxhead (2000) — The Academic Word List: a new look at academic vocabulary"
  - "Stahl & Nagy (2006) — Teaching Word Meanings"
  - "Graves (2006) — The Vocabulary Book: learning and instruction"
input_schema:
  required:
    - field: "text_or_topic"
      type: "string"
      description: "需要分析词汇需求的文本节选或主题"
    - field: "student_level"
      type: "string"
      description: "年龄/年级"
    - field: "subject_area"
      type: "string"
      description: "课程学科"
  optional:
    - field: "language_proficiency"
      type: "string"
      description: "目标学生的 EAL 语言水平"
    - field: "student_profiles"
      type: "array"
      description: "来自上下文引擎：第一语言、先前评估中发现的词汇缺口"
    - field: "lesson_focus"
      type: "string"
      description: "课程重点——有助于确定哪些词汇最为关键"
    - field: "word_count_limit"
      type: "integer"
      description: "最多预教的词汇数量——帮助教师聚焦"
output_schema:
  type: "object"
  fields:
    - field: "tiered_vocabulary"
      type: "object"
      description: "完整的词汇分析，将词汇分为 Tier 1、Tier 2 和 Tier 3"
    - field: "teaching_sequence"
      type: "array"
      description: "按优先级排序的词汇教学顺序及每个词的教学方法"
    - field: "word_teaching_cards"
      type: "array"
      description: "每个重点词的教学卡：定义、语境例句、视觉线索、常见混淆"
    - field: "quick_check"
      type: "string"
      description: "用于检查词汇理解的简短活动"
chains_well_with:
  - "language-demand-analyser"
  - "scaffolded-task-modifier"
  - "text-complexity-analyser"
  - "academic-language-sentence-frame-generator"
teacher_time: "3 分钟"
tags: ["vocabulary", "tiering", "Tier-2", "academic-language", "EAL", "word-teaching"]
---

# 词汇分级工具

## 本技能的作用

接收一段文本节选或一个主题，将所有重要词汇划分为 Tier 1（日常词汇）、Tier 2（跨学科学术词汇）和 Tier 3（特定学科专业词汇），随后生成一份聚焦于 Tier 2 词汇的优先教学序列——这些高实用性的学术词汇跨学科出现，却极少在任何一门课中被明确教授。输出包括分级分析、附带教学方法的教学顺序、包含定义/语境例句/视觉线索/常见混淆的词汇教学卡，以及一项快速词汇检查活动。AI 在此尤为有价值，因为词汇分级既需要词频认知（该词在通用英语与学术英语中的常见程度如何），也需要教学判断（这群特定学生可能已经掌握哪些词，哪些词能解锁课程内容的理解）。

## 循证基础

Beck, McKeown & Kucan (2002, 2013) 确立了已成为词汇教学基石的三级词汇框架：Tier 1 词汇是大多数母语者都知道的基础高频词（house、happy、run）；Tier 2 词汇是跨学术语境出现、对理解至关重要但常未被明确教授的高实用性词汇（analyse、significant、contrast、demonstrate、furthermore）；Tier 3 词汇是低频的特定领域术语（photosynthesis、onomatopoeia、denominator）。他们的核心发现是：Tier 2 词汇是词汇教学杠杆率最高的目标，因为它们在所有学科中出现得足够频繁以至于举足轻重，却极少通过日常对话习得。Nation (2001) 证实，学术词汇（大致相当于 Tier 2）是学业成功的关键门槛——缺乏学术词汇的学生在所有学科中都会受阻，而不仅仅是英语课。Coxhead (2000) 编制了学术词汇表（AWL）——包含 570 个词族，约占学术文本的 10%——为识别 Tier 2 词汇提供了实证基础。Stahl & Nagy (2006) 证明，有效的词汇教学需要在多种语境中多次接触——单一的定义是不够的。Graves (2006) 确立了全面词汇教学的四个组成部分：广泛阅读、教授单个词汇、教授词义学习策略以及培养词意识。

## 输入模式

教师必须提供：
- **Text or topic（文本或主题）：** 学生将要阅读的文本节选，或主题描述。*例如："Year 8 History textbook extract on the Industrial Revolution" / "The topic of photosynthesis for Year 7 Science" / [直接粘贴实际文本节选]*
- **Student level（学生水平）：** 年级。*例如："Year 9"*
- **Subject area（学科领域）：** 学科。*例如："History" / "Science" / "English" / "Geography"*

可选（如上下文引擎可用则自动注入）：
- **Language proficiency（语言水平）：** EAL 语言水平
- **Student profiles（学生档案）：** 第一语言、已知词汇缺口
- **Lesson focus（课堂重点）：** 本节课的核心内容
- **Word count limit（词汇数量上限）：** 最多预教的词汇数（默认：5–8 个）

## Prompt

```
You are an expert in vocabulary instruction and academic language development, with deep knowledge of Beck, McKeown & Kucan's (2002, 2013) three-tier vocabulary framework, Nation's (2001) work on vocabulary learning, Coxhead's (2000) Academic Word List, and Stahl & Nagy's (2006) principles of effective vocabulary teaching. You understand that Tier 2 vocabulary is the highest-leverage target for explicit instruction — these words appear across all academic subjects, are essential for comprehension, but are rarely taught directly.

Your task is to analyse and tier the vocabulary in:

**Text or topic:** {{text_or_topic}}
**Student level:** {{student_level}}
**Subject area:** {{subject_area}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Language proficiency:** {{language_proficiency}} — if not provided, tier vocabulary assuming a class that includes EAL students at Developing level alongside native speakers with varying vocabulary breadth.
**Student profiles:** {{student_profiles}} — if not provided, assume mixed language backgrounds with conversational fluency but limited academic vocabulary.
**Lesson focus:** {{lesson_focus}} — if not provided, use the text/topic to infer what vocabulary is most important for comprehension.
**Word count limit:** {{word_count_limit}} — if not provided, select 5–8 priority words for explicit teaching.

Apply these evidence-based principles:

1. **Three-tier classification (Beck, McKeown & Kucan, 2002):**
   - **Tier 1:** Basic, high-frequency words most students know. BUT — for EAL students, some Tier 1 words are NOT known, especially: idioms ("break a leg"), phrasal verbs ("look up," "turn down"), words with multiple meanings ("table" as noun/verb, "run" in dozens of senses), and culturally embedded terms. Flag these.
   - **Tier 2:** Academic, cross-subject words. These are the PRIORITY. They appear in Coxhead's Academic Word List or equivalent and are essential for academic success across subjects. Examples: analyse, significant, evidence, contrast, furthermore, demonstrate, evaluate, indicate, consequently, whereas.
   - **Tier 3:** Subject-specific technical vocabulary. Usually taught within the subject. Important but narrow — a student needs "photosynthesis" for Biology but not for History.
   - Classify each significant word and explain the classification.

2. **Prioritise Tier 2 for explicit teaching (Beck et al., 2002; Nation, 2001):**
   - Tier 3 words are usually taught by the subject teacher as part of the topic.
   - Tier 1 words are usually known (except for EAL-specific gaps noted above).
   - Tier 2 words fall in the gap — assumed by all subjects, taught by none. These are the highest-impact targets.
   - Within Tier 2, prioritise words that are: (a) essential for understanding this text/topic, (b) useful across multiple subjects, and (c) likely unknown to the target students.

3. **Effective word teaching requires depth, not just definitions (Stahl & Nagy, 2006; Graves, 2006):**
   - For each priority word, provide:
     a. A student-friendly definition (not a dictionary definition)
     b. The word used in context (from the text or topic)
     c. A visual cue or memorable association
     d. Common confusions or false friends (especially relevant for EAL students whose first language may have a cognate with a different meaning)
   - One exposure is not enough — recommend how to revisit the word across the lesson.

4. **Quick check activity (Stahl & Nagy, 2006):**
   - Provide a brief activity (2–3 minutes) to check whether students have grasped the key vocabulary before they encounter it in the task.

Return your output in this exact format:

## Vocabulary Analysis: [Text/Topic]

**For:** [Student level] [Subject area]
**Total significant words identified:** [Count]
**Priority words for explicit teaching:** [Count]

### Tiered Vocabulary

**Tier 1 — Everyday (with EAL notes)**
[Words with any notes about potential EAL challenges — multiple meanings, idioms, false friends]

**Tier 2 — Academic (PRIORITY)**
[Words listed with brief definition and why they matter for this text/topic]

**Tier 3 — Technical**
[Subject-specific words, noting which are likely already taught]

### Teaching Sequence

[Ordered list of priority words to teach, starting with the most essential for comprehension]

### Word Teaching Cards

For each priority word:
**[Word]**
- **Student-friendly definition:** [Plain language definition]
- **In context:** [The word used in a sentence from or related to the text/topic]
- **Visual/memory cue:** [An image, association, or mnemonic]
- **Watch out for:** [Common confusions, false friends, or multiple meanings]

### Quick Check Activity

[A 2–3 minute activity to check vocabulary understanding before students tackle the main task]

**Self-check before returning output:** Verify that (a) words are correctly tiered, (b) Tier 2 words are prioritised for teaching, (c) word teaching cards include definition, context, visual cue, and confusions, (d) the teaching sequence is ordered by importance for this specific text/topic, (e) EAL-specific challenges are flagged for Tier 1 words, and (f) the quick check tests understanding, not just recall of definitions.
```

## 示例输出

**场景：** *Text or topic: "Year 9 Geography textbook extract on urbanisation in LICs (Low Income Countries) — covers push and pull factors, rural-to-urban migration, informal settlements, and challenges of rapid urbanisation" / Student level: "Year 9" / Subject area: "Geography" / Language proficiency: "Several students at Developing level"*

---

## 词汇分析：低收入国家（LICs）的城市化

**适用对象：** 九年级地理
**识别出的重要词汇总数：** 28
**优先明确教授的词汇数：** 6

### 分级词汇表

**Tier 1 — 日常词汇（附 EAL 说明）**

| 词汇 | EAL 说明 |
|------|----------|
| "push" / "pull" | 此处为隐喻用法——不是物理上的推/拉。EAL 学生可能只知道字面意思。"Push factors push people AWAY; pull factors pull people TOWARDS." |
| "settle" / "settlement" | 一词多义："settle down"（安静下来）、"settle"（决定）、"settlement"（人类居住地）。地理学含义是特定的。 |
| "challenge" | 此处用作名词（"challenges of urbanisation"），而非动词（"I challenge you"）。学术名词用法可能不熟悉。 |
| "opportunity" | 可能在日常会话中认识，但不熟悉 "economic opportunity" 这一学术用法。 |
| "lack" | 常见学术词汇，但在日常口语中不常见——处于 Developing 水平的 EAL 学生可能不认识。 |

**Tier 2 — 学术词汇（优先）**

| 词汇 | 重要性说明 |
|------|------------|
| **significant** | 贯穿全文："significant increase"、"significant challenges"。地理写作必备。在所有学科中都会出现。 |
| **consequently** | 关键因果连接词："Consequently, cities grew rapidly." 学生在写作中需要用它来解释因果关系。 |
| **factor** | 主题核心："push factors"、"pull factors"。用于地理、历史、科学。常被误解为 "fact"。 |
| **migration** | 处于 Tier 2/3 交界——在地理中是专业词，但也越来越多地用于一般学术和媒体语境。词根 "migrate" 连接多个相关词。 |
| **infrastructure** | 讨论城市化挑战的关键词："lack of infrastructure"。用于地理、经济、公民教育。 |
| **inadequate** | 用于描述非正规住区的服务："inadequate sanitation"。极具表现力的评价性词汇，跨学科通用。 |

**Tier 3 — 专业词汇**

| 词汇 | 说明 |
|------|------|
| urbanisation | 核心主题词——应在单元开始时定义 |
| rural-to-urban migration | 复合术语——需要明确拆解 |
| informal settlement | 地理专业术语——学生可能知道 "slum"，但 "informal settlement" 是学术术语 |
| LIC / HIC | 缩写（Low Income Country / High Income Country）——需要明确教授 |
| megacity | 专业术语——人口超过 1,000 万的城市 |
| push factor / pull factor | 日常词汇的专业化应用——需要明确定义 |

### 教学顺序

按以下顺序教授（对理解最关键的词优先）：

1. **factor** —— 没有这个词，整个主题框架（推拉因素）就无法理解
2. **significant** —— 贯穿全文，且学生写作中需要用到
3. **infrastructure** —— 理解城市化挑战所必需
4. **consequently** —— 写作中进行因果解释所必需
5. **inadequate** —— 描述城市挑战的关键评价性词汇
6. **migration** —— 连接 Tier 2 与 Tier 3 的核心概念词

### 词汇教学卡

**factor**
- **学生友好型定义：** 影响某件事的原因或因素——促使某件事发生的条件之一。
- **语境例句：** "One push factor is the lack of jobs in rural areas, which drives people to move to cities."
- **视觉/记忆线索：** 把 factors 想象成食谱里的配料——每一种配料都促成了最终的结果。画一张图：多个箭头（factors）共同指向同一个结果（urbanisation）。
- **注意混淆：** 学生常把 "factor" 和 "fact" 混淆。fact 是真实的事实；factor 是“导致”或“影响”某事的原因。此外，"factory" 拼写相似但意思完全不同——不过在这个主题里，城市里的工厂本身可以是一个 pull factor！

**significant**
- **学生友好型定义：** 重要到值得注意或提及的；大到足以产生影响的。
- **语境例句：** "There has been a significant increase in the population of Lagos over the last 30 years."
- **视觉/记忆线索：** 联想到交通标志（sign）——一个 sign-ificant 的变化，就是大到需要竖起警示牌的变化。它不是微小或琐碎的。
- **注意混淆：** 在日常英语中，"significant" 有时指“意味深长的”（a significant look）。在学术英语中，它几乎总是指“大且重要的”。西班牙语同源词："significativo"——含义相近，是有益的关联。

**infrastructure**
- **学生友好型定义：** 一座城市正常运转所需的基础系统和设施——道路、水管、电力、下水道、医院、学校。
- **语境例句：** "Rapid urbanisation often outpaces infrastructure development, leaving new residents without clean water or reliable electricity."
- **视觉/记忆线索：** "Infra" 意为“在下方/底层”。Infrastructure 就是运转中的城市“底下”的东西——基础支撑。展示一张城市剖面图，呈现建筑物下方的管道、电缆和道路。
- **注意混淆：** 这是一个看起来很吓人的长词，但结构清晰：infra（下方）+ structure（建筑/结构）。将其拆开记忆。学生可能在新闻语境中遇到过它（关于“基础设施支出”的政治讨论）。

**consequently**
- **学生友好型定义：** 作为结果；因此，接下来发生了某事。
- **语境例句：** "Rural areas lacked employment opportunities. Consequently, thousands of people migrated to urban centres."
- **视觉/记忆线索：** Consequence → consequently。如果你知道 "consequence"（接下来发生的结果），"consequently" 就是它的副词形式："as a consequence of this..."
- **注意混淆：** 学生通常知道 "because"，但不知道 "consequently"。区别在于："because" 向后看（这件事发生是因为……），"consequently" 向前看（这件事发生了，因此……）。两者都表达因果关系，但方向相反。

**inadequate**
- **学生友好型定义：** 不够好的；不足以满足所需的。
- **语境例句：** "The inadequate sanitation in informal settlements leads to the spread of waterborne diseases."
- **视觉/记忆线索：** in-（不）+ adequate（足够）。如果某物是 adequate，它就是“够用的”；如果它是 INadequate，它就是“不够用的”。就像 "incomplete" = 不完整。
- **注意混淆：** 表示“不”的前缀 "in-" 是一项强大的词汇学习策略。联系其他 "in-" 词汇：insufficient、inappropriate、inaccessible。这一规律能解锁许多学术词汇。

**migration**
- **学生友好型定义：** 人们为了生活或工作从一个地方移动到另一个地方——通常是大规模或永久性的迁移，而不是度假。
- **语境例句：** "Rural-to-urban migration has transformed cities in LICs, with millions moving from the countryside to urban areas."
- **视觉/记忆线索：** 想到鸟类迁徙（bird migration）——鸟类在特定时间从一个地方飞往另一个地方。人类迁移与之相似：人们移动是因为条件把他们推走，或把他们吸引到更好的地方。
- **注意混淆：** "Migration"（迁移行为）、"migrant"（迁移者）、"migrate"（动词）、"immigration"（迁入某个国家）、"emigration"（迁出某个国家）。这些词彼此相关但有区别。在本主题中，我们关注的是国内迁移（同一国家内部）。

### 快速检查活动

**"Use it or lose it"（学以致用）——3 分钟**

在黑板上展示六个带有空缺的句子。学生从旁边展示的词库中选择正确的词汇。

1. "The lack of jobs in rural areas is a push ___ that drives migration." [factor]
2. "Lagos has experienced a ___ increase in population since 1970." [significant]
3. "The city's ___ cannot keep up with the rapid growth — there aren't enough roads, pipes, or power lines." [infrastructure]
4. "Young people left their villages. ___, the rural population declined." [consequently]
5. "Housing in informal settlements is often ___ — overcrowded and lacking basic facilities." [inadequate]
6. "Rural-to-urban ___ is one of the biggest demographic changes in LICs." [migration]

**检查：** 学生举起迷你白板展示答案。如果 80% 以上正确，则继续往下推进。如果某个词错误率较高，先用另一个例句重新讲解该词再继续。

---

## 已知局限性

1. **词汇分级不是绝对的——语境至关重要。** 对九年级学生来说属于 Tier 2 的词，对十二年级学生来说可能属于 Tier 1。在一所学校属于 Tier 2 的词，在另一所学校可能属于 Tier 3，这取决于学生先前的词汇教学情况。这里提供的分级是基于词频数据和典型学生知识水平的指导，教师应根据对具体学生的了解进行调整。

2. **预教词汇是必要的，但还不够。** 学生需要在不同语境中多次接触（Stahl & Nagy 建议 10–12 次）才能真正掌握一个词。单次预教只是引入该词；必须在整节课、整周和整个单元中反复重现。教学卡提供的是初次接触；教师必须规划重复巩固。

3. **该工具在单词层面分析词汇，但学术语言也涉及短语和结构。** "On the other hand"、"as a result of"、"in contrast to" 是作为单个词汇项目发挥作用的多词表达。该工具识别单个词汇，但可能无法捕捉学生所需的全部重要多词短语。
