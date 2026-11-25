---
# AGENT SKILLS STANDARD FIELDS (v2)
name: sourcing-skill-builder
description: "培养学生在阅读历史史料前先审问出处的能力——追问作者是谁、何时所写、为何而写以及这对可靠性的影响。适用于学生读文献不关注作者身份时。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS
skill_id: "historical-thinking/sourcing-skill-builder"
skill_name: "历史史料溯源技能构建器"
domain: "historical-thinking"
version: "1.0"
contributor: "Sean Hu"
evidence_strength: "strong"
evidence_sources:
  - "Wineburg (1991) — Historical problem solving: cognitive processes in the evaluation of documentary and pictorial evidence"
  - "Wineburg (1998) — Reading Abraham Lincoln: an expert/expert study in historical cognition"
  - "Wineburg (2007) — Unnatural and essential: the nature of historical thinking"
  - "Gottlieb & Wineburg (2012) — Between Veritas and Communitas: epistemic switching in the reading of academic and sacred history"
  - "Reisman (2012) — Reading like a historian: a document-based history curriculum intervention in urban high schools"
  - "Wineburg & Reisman (2015) — Disciplinary literacy in history: a toolkit for digital citizenship"
input_schema:
  required:
    - field: "historical_topic"
      type: "string"
      description: "学生正在调查的历史主题、时期或问题"
    - field: "student_level"
      type: "string"
      description: "年龄/年级以及当前一手史料分析的经验水平"
    - field: "current_challenge"
      type: "string"
      description: "学生目前在遇到历史史料时做了什么或没做到什么——表明溯源尚未成为习惯的可观察行为"
  optional:
    - field: "source_type"
      type: "string"
      description: "学生正在使用的历史史料类型——例如书面证言、政府文件、照片、政治漫画、报纸文章、地图、私人信件"
    - field: "available_documents"
      type: "string"
      description: "学生在本课或本单元将接触的具体文献描述"
    - field: "curriculum_framework"
      type: "string"
      description: "来自上下文引擎：正在使用的相关课程标准或历史思维框架——例如 DIG、Seixas 六大概念、国家课程要求"
    - field: "prior_instruction"
      type: "string"
      description: "学生已经接受过的溯源教学——使建议在既有基础上递进而非重复"
output_schema:
  type: "object"
  fields:
    - field: "sourcing_progression"
      type: "object"
      description: "针对该年龄段学生，溯源在初学、发展中和熟练水平上的表现——附每级可观察指标，区分“提及出处”与“审问出处”"
    - field: "explicit_instruction_sequence"
      type: "object"
      description: "用指定史料类型教授溯源的三段式序列（示范 → 引导练习 → 独立练习），包含展示专家读者在阅读正文前如何处理书目信息的教师出声思维脚本"
    - field: "guiding_questions"
      type: "array"
      description: "学生在阅读前与阅读中应提出的针对史料类型的引导问题——改编自 DIG 溯源规程并按发展水平与史料类型校准"
    - field: "common_failure_patterns"
      type: "array"
      description: "该水平学生未能有效溯源的常见具体模式——附每项的针对性教学应对"
    - field: "assessment_indicators"
      type: "object"
      description: "溯源正在发展为习惯性实践而非被动提示行为的可观察迹象——讨论中听什么、书面作业中看什么"
chains_well_with:
  - "close-reading-skill-builder"
  - "contextualisation-skill-builder"
  - "corroboration-skill-builder"
  - "historical-thinking-strategy-modelling-guide"
  - "document-based-lesson-designer"
  - "historical-source-adapter"
  - "historical-thinking-assessment-designer"
  - "source-credibility-evaluation-protocol"
teacher_time: "3 分钟"
tags: ["sourcing", "historical-thinking", "primary-sources", "disciplinary-literacy", "document-analysis", "Wineburg", "DIG"]
---

# 历史史料溯源技能构建器

## 本技能的作用

设计针对性教学以培养学生的史料溯源（sourcing）实践——在阅读前与阅读中审问历史文献由谁撰写、何时撰写、为何撰写、面向什么受众，以及这对文献可靠性意味着什么的习惯。输出包括发展进阶序列（指定水平下从初学到熟练的溯源表现）、附带教师出声思维脚本的显性教学序列、针对史料类型的引导问题、常见失败模式及教学应对，以及区分“提及出处”与“审问出处”的评估指标。

溯源是历史思维的基础动作。Wineburg & Reisman (2015) 将其描述为在每一项历史阅读研究中区分专家与新手实践的试金石。但“常规化溯源”（学生因受过训练而习惯性地瞥一眼出处注）与“分析性溯源”（学生在读正文一个字之前，就利用出处信息生成关于文献可靠性、目的及与其他记述关系的假设）之间存在关键区别。Gottlieb & Wineburg (2012) 证明，历史学家与非历史学家提及出处的频率相近——区别不在于他们多久提一次出处，而在于他们用这些信息“做了什么”。一位科学家记下作者姓名便继续往下读；一位历史学家则深挖书名、出版社和日期，单从书目信息就推导出关于文本政治立场的假设。本技能同时瞄准这两个层面——先建立习惯，再深化分析质量——因为有前者无后者只会培养出把溯源当作课堂仪式的学生，而非真正的智识实践者。

AI 在此尤为有价值，因为诊断学生为何未能溯源，需要区分几种需要截然不同教学应对的失败模式。完全跳过出处注的学生，与读了出处注却不加使用的学生，以及使用出处信息但流于表面的学生，各自需要不同的干预。

## 循证基础

Wineburg (1991) 通过一项比较历史学家与高中生如何阅读历史文献的里程碑式研究，确立了溯源作为专家-新手区分指标的地位。历史学家始终在阅读内容之前先检查文献出处——核查谁写的、何时写的以及在什么处境下写的；而学生则直接一头扎进正文。这一发现在多项研究中得到复制与拓展（Wineburg, 1998; Rouet et al., 1997; Leinhardt & Young, 1996; Nokes, Dole & Hacker, 2007），使溯源成为专家历史阅读中实证记录最充分的特征。

Wineburg (2007) 通过激活扩散（spread of activation）与可得性启发法（availability heuristic）解释了为何溯源在认知上是“反自然的”。当文献提及一个熟悉主题时，读者既有的知识与观点会瞬间涌入阅读过程，压倒对文献出处的关注。学科溯源正是通过训练读者“暂停”来对抗这种默认反应——在考虑清楚是谁创作了它以及为什么之前，克制自己不去直接评判内容。Wineburg 将这种暂停所催生的专家思维倾向称为“无知的明确化（specification of ignorance）”：利用文献来清晰界定自己尚不知道什么，而不是用它来证实自己早已相信的观点。

Gottlieb & Wineburg (2012) 进一步完善了这一图景，表明历史学家与理科/工科博士提及出处的“数量”相近——两组人都会注意到并提及出处信息。区别在于质量。面对一本由不知名作者撰写、Free Press 出版的书，历史学家会深挖书目信息中的每一个词，生成关于文本主题、政治倾向以及与当代争论关系的假设；而科学家只记下同样信息便继续往下读。这一发现意味着，教学生提及出处是必要的，但远远不够——教学还必须发展学生对出处信息进行分析加工的深度。

Reisman (2012) 证明溯源在城市高中课堂中可以通过显性教学教授。在一项为期六个月的准实验干预中，实验组学生在溯源上取得了显著提升（F(1,181) = 15.89, p < .001, ηp² = .08）。溯源是仅有的两项显示出显著处理效应的历史思维技能之一（另一项是精读）——语境化和互证均未对同一教学法产生显著反应。Reisman 将此归因于溯源的具体性：它包含一个离散、可观察的动作（阅读前先看出处注），可以示范、在单份文献上练习，并不断强化直至成为习惯。

Wineburg & Reisman (2015) 将溯源界定为不仅是一种策略，更是一种世界观（weltanschauung）——一种重构读者与文本关系的世界观。当溯源成为习惯时，课本所隐含的无可置疑的事实权威便被打破。阅读变成了主动的探究者与人类作者之间的辩证对话，作者的动机、局限与处境都必须纳入考量。

## 输入模式

教师必须提供：
- **Historical topic（历史主题）：** 学生正在调查的主题、时期或问题。*例如："The causes of the American Revolution" / "Life in the trenches during World War I" / "The impact of the transatlantic slave trade on West African societies" / "Did Pocahontas rescue John Smith?"*
- **Student level（学生水平）：** 年龄/年级及一手史料分析经验。*例如："Year 7, first time working with primary sources" / "Year 10, have done some document analysis but don't source consistently" / "Year 12 IB History, can source when prompted but don't do it independently"*
- **Current challenge（当前挑战）：** 学生目前做了什么或没做到什么。*例如："They dive straight into reading the text without looking at the source information" / "They note the author but don't think about what the author's position means for the document's reliability" / "They dismiss sources as 'biased' without explaining how the bias shapes the content" / "They treat all primary sources as equally trustworthy because they're 'from the time'"*

可选（如上下文引擎可用则自动注入）：
- **Source type（史料类型）：** 历史史料类型——影响哪些溯源问题最具生产力
- **Available documents（可用文献）：** 学生将使用的具体文献
- **Curriculum framework（课程框架）：** DIG、Seixas 六大概念、国家课程、IB 等
- **Prior instruction（先前教学）：** 学生已接受过的溯源教学

## Prompt

```
You are an expert in historical thinking pedagogy, with deep knowledge of Wineburg's (1991, 1998, 2007) research on sourcing as a disciplinary reading practice, Gottlieb and Wineburg's (2012) finding that the quality of sourcing — not the quantity — distinguishes expert from novice readers, and Reisman's (2012) evidence that sourcing is teachable through explicit instruction. You understand that sourcing is the foundational move in historical thinking: interrogating who authored a document, when, why, for what audience, and what this means for its reliability — before engaging with the document's content.

Your task is to design targeted sourcing instruction for:

**Historical topic:** {{historical_topic}}
**Student level:** {{student_level}}
**Current challenge:** {{current_challenge}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Source type:** {{source_type}} — if not provided, design for written primary sources as the default, noting how the approach would differ for visual or non-textual sources.
**Available documents:** {{available_documents}} — if provided, tailor the instruction to these specific documents. If not, design generalisable instruction with placeholder examples.
**Curriculum framework:** {{curriculum_framework}} — if provided, align the sourcing questions and progression descriptors to this framework. If not, use the DIG framework (who wrote this, what is their perspective, why was it written, when, where, is it reliable) as the default.
**Prior instruction:** {{prior_instruction}} — if provided, build on what students have already learned rather than repeating it. If not, assume this is early-stage sourcing instruction.

Design the following:

1. **Sourcing progression:** What sourcing looks like at three levels for this age group:
   - **Novice:** The student engages with the document's content without attending to its source. Describe what this typically looks like with this age group and topic — the specific things students say, write, or do that reveal they are not sourcing.
   - **Developing:** The student notes source information but uses it superficially. Describe what "superficial sourcing" looks like — e.g. mentioning the author but not considering their position, noting the date but not reasoning about what was happening at that time, labelling a source as "biased" without explaining how the bias shapes the content.
   - **Proficient:** The student uses source information to generate hypotheses about the document's reliability, purpose, and perspective before and during reading. Describe what this looks like with this topic — the specific questions a proficient student would ask, the inferences they would draw from the bibliographic information, the way source awareness shapes their reading of the content.

   IMPORTANT: The distinction between developing and proficient is the distinction Gottlieb and Wineburg (2012) identified — the difference between mentioning a source and interrogating it. Make this distinction concrete and observable for this specific context.

2. **Explicit instruction sequence:** A three-part sequence for moving students from their current challenge toward proficient sourcing:
   - **I DO (teacher models):** A think-aloud script (approximately 150–200 words) showing the teacher encountering the document's source information and modelling what an expert reader does with it. The think-aloud should make visible the internal reasoning that is normally invisible — pausing at the source note, generating questions from the author's name and position, forming hypotheses from the date and publication context, noting what is NOT in the source information and why that matters. The think-aloud must be specific to the source type and topic, not generic.
   - **WE DO (guided practice):** A structured activity where students practise sourcing a second document with teacher support. Specify what the teacher does (circulates, prompts, redirects), what questions the teacher asks when students skip the source or use it superficially, and how the teacher gradually withdraws support.
   - **YOU DO (independent practice):** What independent sourcing looks like — students source a third document without prompting. Specify what the teacher monitors for and how to assess whether students are sourcing habitually or only when reminded.

3. **Guiding questions:** Source-type-specific questions for students, calibrated to the developmental level. These should be adapted from the DIG sourcing protocol but made specific to the source type. For each question, include:
   - The question itself
   - Why this question matters for this source type (brief, one sentence)
   - A sentence starter students can use when responding

   Do NOT simply list the generic DIG questions (who, what, when, where, why, reliable?). Adapt them to the source type so they guide students toward the specific analytical moves that source type demands.

4. **Common failure patterns:** The 3–4 most common ways students at this level fail to source effectively, based on the current challenge described. For each pattern:
   - Name the pattern
   - Describe what it looks like (what the student says or writes)
   - Explain why the student does this (the cognitive habit or misconception driving it)
   - Provide a specific instructional response (what the teacher says or does to redirect)

5. **Assessment indicators:** Observable signs that sourcing is developing as a habitual practice:
   - **In discussion:** What to listen for — specific things students say spontaneously (not when prompted) that indicate sourcing is becoming automatic
   - **In written work:** What to look for — specific features of student writing that indicate source awareness is shaping their analysis, not just appearing as a formulaic opening sentence
   - **The key test:** One specific observable behaviour that most reliably distinguishes a student who sources habitually from one who sources only when reminded

Return your output in this exact format:

## Sourcing Instruction Plan

**Topic:** [Historical topic]
**Students:** [Level and current challenge]
**Source type:** [Type of source or "written primary sources (default)"]

### Sourcing Progression

**Novice — not yet sourcing:**
[Description with observable indicators specific to this context]

**Developing — sourcing superficially:**
[Description with observable indicators — what "mentioning but not interrogating" looks like here]

**Proficient — sourcing analytically:**
[Description with observable indicators — what genuine interrogation looks like here]

### Explicit Instruction Sequence

**I DO — Teacher Think-Aloud**
[Full think-aloud script, 150–200 words, modelling expert sourcing with a specific document]

**WE DO — Guided Practice**
[Structured activity with teacher prompts and gradual release]

**YOU DO — Independent Practice**
[What independent sourcing looks like and how to monitor it]

### Guiding Questions

[Source-type-specific questions with rationale and sentence starters]

### Common Failure Patterns

[3–4 patterns with descriptions, explanations, and instructional responses]

### Assessment Indicators

**In discussion:** [What to listen for]
**In written work:** [What to look for]
**The key test:** [The single most reliable indicator]

**Self-check before returning output:** Verify that (a) the progression clearly distinguishes between mentioning a source and interrogating it, (b) the think-aloud script models the INTERNAL reasoning of an expert reader, not just the external behaviour, (c) the guiding questions are adapted to the source type, not generic, (d) each failure pattern includes a specific instructional response, and (e) the assessment indicators describe what students do SPONTANEOUSLY, not what they do when prompted.
```

## 示例输出

**场景：** *Historical topic: "Did Pocahontas rescue John Smith?" / Student level: "Year 8, second term of working with primary sources, have been introduced to sourcing but don't do it consistently" / Current challenge: "They note the author's name but don't think about what the author's position or circumstances mean for the document's reliability — they treat all eyewitness accounts as equally trustworthy because they're 'from the time'" / Source type: "Written first-person accounts" / Available documents: "John Smith's 1608 True Relation and his 1624 General History"*

---

## 溯源教学计划

**主题：** 宝嘉康蒂救了约翰·史密斯吗？
**学生：** 八年级，熟悉基础溯源，但把所有目击者记述都视为同等可信
**史料类型：** 书面第一人称记述

### 溯源发展进阶

**初学——尚未溯源：**
学生阅读史密斯的记述，仅凭内容是否看似合理或是否符合他们对宝嘉康蒂的既有认知（往往来自迪士尼）来评判。他们可能会说 "This proves the rescue happened because Smith was there" 或 "I don't believe it because it seems too dramatic." 在这两种情况下，学生都是在用已有信念评判“内容”，而未考虑史密斯是谁、为何写、何时写或什么处境塑造了他的记述。文献顶部的出处注被完全忽略——如果被问起，学生可能连作者、日期或出版物都说不出来。

**发展中——浅层溯源：**
学生注意到约翰·史密斯写了这份文献，写于 1608 年或 1624 年。他们可能会说 "This was written by John Smith, who was a colonist" 或 "This is a primary source from 1624." 但他们没有用这些信息来推理文献的可靠性。他们把出处当作事实标签——就像一个标题——而不是当作分析杠杆。如果被追问（"Does it matter that Smith wrote this?"），他们可能会说 "He might be biased"，却无法解释他作为殖民者、冒险家或自我宣传者的立场会如何塑造他提出的具体主张。“有偏见（biased）”一词成了笼统的打发，而非分析工具。

**熟练——分析性溯源：**
阅读前，学生审视出处注并推理其含义。对于 1608 年记述，他们可能会问："This was written in the same year — who was Smith writing for? Was he reporting to his sponsors? Would he want to make things sound dangerous or peaceful?" 对于 1624 年记述，他们可能会指出："This was written 16 years later. Pocahontas had already gone to England and died. Was Smith trying to connect himself to her fame?" 学生在阅读内容“之前”就利用日期与作者身份生成假设，然后带着这些假设去读正文。关键在于，他们认识到“同一作者”在“不同时间”写作可能会产出不同记述——他们追问为什么，而不仅仅是指出差异。

### 显性教学序列

**我做（I DO）——教师出声思维**

*教师投影展示出处注清晰可见的史密斯 1624 年《General History》，并在触碰正文前出声朗读：*

"OK, before I read a single word of this account, I'm going to look at who wrote it and when. It says 'John Smith, 1624, General History of Virginia.' So this is John Smith himself — he's the person at the centre of the story. That immediately makes me cautious, because he has a stake in how this story is told. It's HIS reputation on the line.

Now, 1624. When was the event supposed to have happened? 1607. So he's writing about something that happened 17 years ago. That's a long time — I'd struggle to remember details from 17 years ago. But there's something else. I happen to know that Pocahontas went to England in 1616 and became very famous there before she died in 1617. So by 1624, she was a well-known figure. Is Smith connecting himself to a celebrity? I don't know yet, but I'm going to read this with that question in mind.

One more thing — it says 'General History.' That means this was published as a book. He's writing for a public audience, not a private diary. He wants people to read this. WHY? What's he promoting?"

**我们做（WE DO）——引导练习**

学生拿到出处注可见的史密斯 1608 年《True Relation》。结对用三分钟“只”审视出处信息（不读正文），写下他们注意到的内容以及由此引发的问题。

教师巡视倾听。常见纠偏：
- 如果一组直接跳去读正文："Wait — what's the first thing we do? What can you learn from the source note BEFORE you read?"
- 如果一组记下作者和日期后就停下："You said it's from 1608. The event happened in 1607. What does that timing tell you? Is that a long gap or a short gap? How does that compare to the 1624 account?"
- 如果一组说 "He's biased"："Biased HOW? What specific thing might Smith want to emphasise or hide in 1608 that's different from what he might want to emphasise in 1624?"

三分钟后，教师收集 2–3 组的观察，并示范如何将观察转化为假设："So you noticed it was written in 1608, just a year after the event, and it was sent back to England as a report. What hypothesis does that give us about WHY Smith wrote it?"

**你做（YOU DO）——独立练习**

学生拿到第三份文献——一位历史学家的阐释（例如 Henry Adams 1867 年对史密斯的批判）。在无提示的情况下，他们撰写一段溯源段落：在阅读正文“之前”，他们从出处中注意到了什么、引发了什么问题以及对文献有什么假设。

教师监控要点：
- 学生是从出处注开始，还是直接一头扎进正文？
- 学生是在提出问题，还是仅仅陈述关于出处的事实？
- 学生是否将出处信息与文献可靠性的潜在影响联系起来？

无需提示即能分析性溯源的学生准备好继续推进；仍需提醒（"What's the first thing we do?"）的学生尚在养成习惯，需要更多引导练习。

### 引导问题

1. **谁写了这份文献，他们与事件是什么关系？**
   *对第一人称记述为何重要：* 同时也是参与者的目击者对事件如何被呈现拥有切身利益——他们的记述绝非中立观察。
   *句首提示：* "The author was... which means they might want to..."

2. **这是何时写的，距离事件发生有多久？**
   *对第一人称记述为何重要：* 事后立即写下的记述（汇报、辩解）服务于不同于多年后写下的记述（纪念、塑造声誉）的目的。记忆随时间改变，写作者的动机亦然。
   *句首提示：* "This was written [X years] after the event, which means..."

3. **预期受众是谁，作者希望他们怎么想或怎么做？**
   *对第一人称记述为何重要：* 给资助人的报告、公开出版的书籍和私人信件服务于不同目的，塑造了作者纳入、省略或润色什么。
   *句首提示：* "The author was writing for... so they probably wanted to..."

4. **作者可能有什么理由去夸大、省略或以特定方式呈现某些内容？**
   *对第一人称记述为何重要：* 每位作者都有自身利益。识别这些利益并不意味着记述是假的——而是带着对作者得失的觉察去阅读。
   *句首提示：* "The author might have a reason to... because..."

5. **这份史料“不能”告诉我们什么，我们还需要哪些其他史料？**
   *对第一人称记述为何重要：* 单一目击者只提供一种视角。认识到任何单一史料的局限，正是通往互证的桥梁。
   *句首提示：* "This source can tell us about... but it can't tell us about... because..."

### 常见失败模式

**1. “内容优先”——不看出处直接扎进正文**
*表现：* 学生从正文第一行开始读，完全跳过出处注。他们的回答只涉及文献说了“什么”，而不涉及“谁”说的或“为什么”。
*原因：* 其他场景（小说、课本、网页）的阅读习惯训练学生从正文开头读起。出处注看起来像个页眉——是可以跳过的元数据，而不是需要分析的信息。
*教学应对：* 物理遮住文献正文，只留出处注可见。要求学生在揭开正文前先用 60 秒单从出处注生成问题。重复这一常规，直到先看出处注成为自动反应。

**2. “把出处当标签”——提及出处却不加运用**
*表现：* 学生写下 "This was written by John Smith in 1624"，然后就按出处信息毫不相干的方式继续分析内容。出处只是一句与后续分析脱节的套话开场白。
*原因：* 他们学到了溯源是“要做的一件事”（提一下作者和日期），但没学到它是“改变你阅读方式的东西”。溯源成了仪式，而非推理工具。
*教学应对：* 在学生点出出处后，追问："So what? How does knowing Smith wrote this in 1624 change how you read what he says?" 推动他们补全句子："Because Smith wrote this in 1624, I expect to find... / I'm suspicious that... / I want to check whether..."

**3. “以偏见为由全盘否定”——用“有偏见”作为拒绝史料的理由**
*表现：* 学生说 "This source is biased because Smith was involved, so we can't trust it." “有偏见（biased）”成了终结分析而非开启分析的判决词。
*原因：* 他们学到一手史料可能不可靠，却将其解读为二元对立（可信 vs. 有偏见），而非光谱。他们尚未理解“所有”史料都有视角，分析任务是识别视角“如何”塑造记述，而不是判断它“是否”存在。
*教学应对：* 暂时禁用 "biased" 一词，替换为："This author's perspective might lead them to emphasise... and downplay..." 这迫使学生指明偏见的“方向”，而非一刀切否定。同时指出，即使是“有偏见”的史料也告诉了我们一些东西——它揭示了作者“希望”人们相信什么，这本身就具有历史意义。

**4. “目击者 = 真相”——将一手史料视为天然可靠**
*表现：* 学生说 "This is a primary source, so it's more reliable" 或 "Smith was there, so he would know." 他们仅仅因为时间上更接近事件，就赋予第一手记述高于后来阐释的特权。
*原因：* 常作为基础概念教授的一手/二手史料区分，可能在无意中制造了一种“一手 = 更好”的可靠性等级。学生尚未遇到“目击者可能有理由歪曲、夸大或省略”的想法。
*教学应对：* 直接使用史密斯案例：1608 年和 1624 年记述都是同一位目击者的一手史料，且彼此矛盾。问："If primary sources are always reliable, how do we explain this?" 这打破了预设，打开了真正溯源的大门。

### 评估指标

**讨论中：** 倾听学生在讨论内容前是否自发询问出处——尤其是引入新文献时。关键信号是无提示的发问："Wait, who wrote this?" 或 "When was this written? Was that before or after...?" 如果学生只在教师问 "What do we do first?" 时才溯源，习惯仍处于教师依赖阶段。

**书面作业中：** 寻找“融入”分析之中、而非作为孤立开场白的出处信息。发展中的学生会写："This was written by Smith in 1624. The passage describes..."（出处与内容脱节）。熟练的学生会写："Smith wrote this account 17 years after the event, at a time when Pocahontas had become famous in England, which may explain why he now included the dramatic rescue story he had not mentioned in his earlier report." 在这里，出处信息塑造了解读——它不是标签，而是透镜。

**核心检验：** 给学生一份他们从未见过的新文献，不给出任何溯源指令。观察他们在前 30 秒内做什么。已经内化溯源的学生会先看出处注再读正文；只把溯源当课堂程序来学的学生则会直接开始读正文。这 30 秒窗口是判断溯源究竟已内化为思维倾向还是仍停留在受提示行为的最可靠指标。

---

## 已知局限性

1. **溯源是四项历史思维技能中最具体、最易教的一项（Reisman, 2012），但“常规化溯源行为”与“深层分析性溯源”之间存在重要区别。** 本技能同时兼顾两个层面，但从习惯（看一眼出处注）到思维倾向（利用出处信息重塑阅读）的跃迁需要数月的持续练习，而非一节课就能完成。本技能提供教学设计，教师提供持续强化。

2. **将溯源作为专家-新手区分指标的证据基础主要来自使用英语历史文献的美国研究。** 溯源实践如何迁移到非西方史学传统、口述史语境或多语史料环境中，尚缺乏充分研究。在这些语境中工作的教师应调整引导问题，以尊重所教历史的证据传统。

3. **Gottlieb & Wineburg (2012) 证明，身份认同与社群归属会塑造读者如何应用溯源标准——人们在阅读与自身身份无关的主题时可能严格溯源，但在阅读关乎自身认同的过去时却会降低批判防线。** 本技能未涵盖历史思维的这一“水平轴”。教师应意识到，当主题连接到学生自己的社群、传统或信仰时，学生溯源可能没那么仔细——不是因为缺乏技能，而是因为身份卷入改变了他们所应用的认识论标准。

4. **为了教学清晰起见，本技能孤立地聚焦于溯源，但在真实的历史探究中，溯源是与语境化、互证和精读协同运作的。** 一旦学生能稳定溯源，教学应通过基于文献的课程（参见 document-based-lesson-designer）将溯源与其他三项技能整合起来。
