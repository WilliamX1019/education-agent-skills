---
# AGENT SKILLS STANDARD FIELDS (v2)
name: document-based-lesson-designer
description: "运用“像历史学家一样阅读（Reading Like a Historian）”四段式结构设计完整的基于文献的历史课。适用于规划一手史料探究课或将课本课转化为文献调查课时。"
disable-model-invocation: false
user-invocable: true
effort: high

# EXISTING FIELDS
skill_id: "historical-thinking/document-based-lesson-designer"
skill_name: "基于文献的历史课程设计师"
domain: "historical-thinking"
version: "1.0"
contributor: "Sean Hu"
evidence_strength: "strong"
evidence_sources:
  - "Reisman (2012) — Reading like a historian: a document-based history curriculum intervention in urban high schools"
  - "Wineburg, Martin & Monte-Sano (2011) — Reading like a historian: teaching literacy in middle and high school history classrooms"
  - "Wineburg & Martin (2004) — Reading and rewriting history"
  - "Wineburg (2007) — Unnatural and essential: the nature of historical thinking"
  - "Wineburg & Reisman (2015) — Disciplinary literacy in history: a toolkit for digital citizenship"
  - "Wineburg (2016) — Why historical thinking is not about history"
input_schema:
  required:
    - field: "central_question"
      type: "string"
      description: "驱动整节课的核心历史问题——学生将使用一手史料调查的探究问题"
    - field: "document_set"
      type: "string"
      description: "学生将使用的史料——数量、类型、关键内容以及内置于文献集中的张力"
    - field: "student_level"
      type: "string"
      description: "年龄/年级、阅读水平以及基于文献探究的经验"
    - field: "lesson_duration"
      type: "string"
      description: "可用时间——例如 '1 hour'、'2 × 50-minute periods'、'3 hours across a week'"
  optional:
    - field: "target_skills"
      type: "string"
      description: "重点突出的历史思维技能——若未指定，将在文献集支持的情况下整合全部四项"
    - field: "background_knowledge"
      type: "string"
      description: "学生已经掌握的背景知识及还需要补充的内容——决定背景知识阶段的时间分配"
    - field: "learning_objectives"
      type: "string"
      description: "学生在本节课结束时应当知道、理解或能够做到什么"
    - field: "writing_task"
      type: "string"
      description: "课程是否应以书面论证收尾——例如基于证据的短文、简短段落或不设正式写作"
    - field: "curriculum_framework"
      type: "string"
      description: "来自上下文引擎：正在使用的相关课程标准或历史思维框架"
    - field: "prior_instruction"
      type: "string"
      description: "学生已经接受过的历史思维教学——决定策略教学是引入性还是巩固性"
output_schema:
  type: "object"
  fields:
    - field: "lesson_plan"
      type: "object"
      description: "遵循 RLH 四段式活动结构的完整教案——背景知识、核心问题引入、附带策略教学的文献调查轮次以及全班讨论——包含每个阶段的时间、教师行动和学生行动"
    - field: "strategy_instruction_plan"
      type: "object"
      description: "本节课中将在哪些节点、结合哪些文献明确教授或巩固哪些历史思维策略"
    - field: "discussion_plan"
      type: "object"
      description: "如何组织全班讨论——驱动讨论的问题、如何将学生回答连接到证据，以及讨论如何推向课程的论证终点"
    - field: "differentiation_notes"
      type: "object"
      description: "课程如何适应不同阅读水平和先验知识——包括哪些文献需要改编、提供哪些支架，以及如何在不降低分析要求的情况下支持阅读困难学生"
    - field: "assessment_opportunities"
      type: "array"
      description: "课中可观察或评估学生历史思维技能发展的节点——形成性而非终结性"
chains_well_with:
  - "central-historical-question-evaluator"
  - "historical-document-set-curator"
  - "historical-source-adapter"
  - "historical-thinking-strategy-modelling-guide"
  - "sourcing-skill-builder"
  - "close-reading-skill-builder"
  - "contextualisation-skill-builder"
  - "corroboration-skill-builder"
  - "historical-thinking-assessment-designer"
  - "backwards-design-unit-planner"
  - "discussion-protocol-selector"
teacher_time: "5 分钟"
tags: ["lesson-design", "document-based-lessons", "historical-thinking", "primary-sources", "disciplinary-literacy", "activity-structure", "RLH", "DIG"]
---

# 基于文献的历史课程设计师

## 本技能的作用

遵循“像历史学家一样阅读（Reading Like a Historian）”课程的四段式活动结构，设计一节完整的基于文献的历史课：（1）背景知识、（2）核心历史问题、（3）附带显性策略教学的一手史料调查，以及（4）全班讨论。输出是一份包含时间分配、教师行动、学生行动、策略教学节点、讨论计划、分层教学说明与形成性评估机会的完整教案。

本技能是历史思维领域的整合器。它接收其他技能的产出——核心问题（由 central-historical-question-evaluator 评估）、文献集（由 historical-document-set-curator 策展）、改编后的史料（来自 historical-source-adapter）以及策略教学计划（来自四个技能构建器与 strategy-modelling-guide）——并将它们组装成一个连贯的课堂架构。当教师直接提供核心问题与文献时，它也可以从零开始设计。

四段式活动结构并非随意设定。Reisman (2012) 在五所城市高中的 236 名学生中开展的六个月干预研究证明了其有效性。经历该课堂模式的实验组学生在历史思维、事实知识、阅读理解以及历史思维向当代议题迁移四项指标上均优于对照组。该结构之所以有效，是因为每个阶段都承担着特定的认知功能：背景知识激活语境化所需的背景；核心问题提供分析焦点；文献轮次为递进的复杂性搭建支架；全班讨论则使推理变得可见且具有社会性。

然而，Reisman 也发现教师对完整结构的实施保真度较低——大多数教师在保真度量表上的得分低于基线，全班讨论更是极为罕见。最常见的失误是省略讨论环节，这或许解释了语境化和互证为何出现零结果（两者都受益于对话式教学）。因此，本技能明确设计了讨论阶段，并提供了教师主持讨论所需的问题与规程，因为讨论既是整节课最重要、又是最容易被跳过的环节。

## 循证基础

Reisman (2012) 将“基于文献的课程（Document-Based Lesson）”开发为一种包含四个阶段的新“活动结构”。实验组教师在 42–72% 的教学时间（M = 58.3%）中使用该结构，六个月内实施了 36–50 节基于文献的课。干预在全部四项结果测量上均产生了显著效应：历史思维（ηp² = .09）、迁移（ηp² = .08）、事实知识（ηp² = .03）和阅读理解（ηp² = .05）。未发现“学校 × 实验处理”交互作用，表明该结构在差异很大的学校语境中均有效。

四段式结构旨在解决特定的教学难题。背景知识阶段确保学生具备语境化所需的背景知识——没有它，学生无法将文献与其历史时刻相连（Wineburg, 2007）。核心问题阶段提供分析焦点——没有驱动问题，史料分析就会沦为技能操练而非探究（Wineburg, Martin & Monte-Sano, 2011）。附带显性策略教学的文献调查阶段使历史思维技能变得可见且可练习——没有示范，学生无法发展溯源、精读、语境化或互证（Wineburg, 1991）。全班讨论阶段使推理变得社会化且可问责——没有讨论，互证与语境化所需的比较与推理思维就会停留在内部而得不到发展（Reisman, 2012）。

Wineburg, Martin & Monte-Sano (2011) 提供了遵循该结构的八个完整课例。分析揭示了一致的设计原则：课程从激活学生已知内容开始（通常从熟悉的流行文化入手——例如迪士尼的《风中奇缘》——然后将其复杂化）；文献按复杂度递增的轮次引入（先一手史料，再历史学家阐释）；每轮之后紧跟回扣核心问题的讨论。

Wineburg & Martin (2004) 证明，基于文献的课程的收官之作是论证写作：学生必须利用文献中的具体证据，对核心问题建构基于证据的回答。读与写是成对的活动——只读史料不写论证是不完整的，因为写作迫使学生选定立场并为此调集证据。

Reisman (2012) 发现，尽管实验组学生在传统内容讲授上花费的时间“更少”，但他们在事实知识上的表现却优于对照组——这一发现对课程设计具有重要意义。基于文献的课程为学生提供了“组织和保持原本零散事实的有意义活动与图式框架”——学生在调查语境中接触事实时，比从课本中死记硬背记得更牢。

## 输入模式

教师必须提供：
- **Central question（核心问题）：** *例如："Did Pocahontas rescue John Smith?" / "Who was most to blame for World War I?" / "Was Rosa Parks's arrest spontaneous or planned?"*
- **Document set（文献集）：** *例如："4 documents: Smith's 1608 and 1624 accounts (adapted), Adams's critique, Lemay's defence" / "3 documents: Treaty of Versailles excerpt, political cartoon, soldier's letter" / "5 documents: Parks's autobiography excerpt, newspaper account from 1955, NAACP internal memo, bus boycott flyer, interview with Jo Ann Robinson"*
- **Student level（学生水平）：** *例如："Year 8, third document-based lesson this term" / "Year 11 IB History, experienced" / "Year 7, first-ever document-based lesson"*
- **Lesson duration（课时长度）：** *例如："1 hour" / "2 × 50 minutes" / "3 hours across the week"*

可选：
- **Target skills（目标技能）：** 重点突出哪些技能
- **Background knowledge（背景知识）：** 学生已知什么以及需要了解什么
- **Learning objectives（学习目标）：** 学生应当达成什么
- **Writing task（写作任务）：** 课程是否以写作收尾
- **Curriculum framework, prior instruction** —— 用于对齐与进阶

## Prompt

```
You are an expert in designing document-based history lessons, with deep knowledge of the Reading Like a Historian four-part activity structure (Reisman, 2012; Wineburg, Martin & Monte-Sano, 2011), the role of explicit strategy instruction in developing historical thinking skills (Wineburg, 1991, 2007), and the finding that whole-class discussion is both the most important and the most frequently omitted component of the lesson structure (Reisman, 2012).

Your task is to design a complete document-based lesson:

**Central question:** {{central_question}}
**Document set:** {{document_set}}
**Student level:** {{student_level}}
**Lesson duration:** {{lesson_duration}}

The following optional context may or may not be provided. Use whatever is available.

**Target skills:** {{target_skills}} — if not provided, integrate all four skills where the document set supports them, but foreground the 1–2 skills most naturally demanded by the document set.
**Background knowledge:** {{background_knowledge}} — if provided, design the background phase accordingly. If students already have the knowledge, the phase can be brief (5 minutes). If they lack critical context, the phase must be more substantial.
**Learning objectives:** {{learning_objectives}} — if provided, align the lesson to these objectives and ensure assessment opportunities target them.
**Writing task:** {{writing_task}} — if not provided, include a short written response (1 paragraph minimum) as the default culminating activity, following Wineburg and Martin's (2004) argument that reading and writing are paired activities.
**Curriculum framework:** {{curriculum_framework}}
**Prior instruction:** {{prior_instruction}} — if students are new to document-based inquiry, include more explicit strategy instruction. If experienced, reduce scaffolding and increase independence.

Design the following:

1. **Lesson plan:** A complete plan following the four-part structure, with timing, teacher actions, and student actions for each phase:

   **Phase 1 — Background knowledge** (typically 5–15 minutes):
   How the teacher activates or provides the contextual knowledge students need. This might include a brief lecture, a timeline, a short video clip, or a review of prior learning. The background phase should be efficient — its purpose is to equip students for the investigation, not to deliver all the content.

   **Phase 2 — Central question introduction** (typically 3–5 minutes):
   How the teacher introduces the question, why it matters, and what students will do to investigate it. The question should be posted visibly and returned to throughout the lesson.

   **Phase 3 — Document investigation rounds** (the bulk of the lesson):
   The document rounds with explicit strategy instruction. For each round:
   - Which documents students read
   - Which historical thinking strategy is modelled or practised
   - What guiding questions or tools students use
   - How long each round takes
   - What whole-class check-in happens between rounds (brief discussion connecting findings back to the central question)

   Design the rounds to build progressively: Round 1 introduces the core evidence and models the primary strategy; Round 2 introduces complication or contradiction; Round 3 (if time allows) adds further complexity. Each round should include a brief whole-class discussion connecting findings to the central question.

   **Phase 4 — Whole-class discussion and/or writing** (typically 10–20 minutes):
   How the teacher structures the culminating discussion. Include:
   - 2–3 discussion questions that build from factual to interpretive
   - How the teacher connects student responses to evidence from the documents
   - How the discussion addresses the central question without imposing a single correct answer
   - If a writing task is included: the prompt, the evidence requirement, and how long students have

2. **Strategy instruction plan:** Which historical thinking strategies are explicitly taught or reinforced at which points in the lesson:
   - Which strategy is foregrounded in each round
   - Whether the instruction is introductory (modelling from scratch) or reinforcing (prompting students to apply a strategy they've practised before)
   - Where the teacher think-aloud occurs (if applicable)

3. **Discussion plan:** The specific questions and protocols for the whole-class discussion phase. Reisman (2012) found that discussion was extremely rare in treatment classrooms — this section exists to make discussion concrete and facilitatable rather than abstract and skippable. Include:
   - Opening question (connected to the central question)
   - Follow-up question (pushing toward evidence and reasoning)
   - Closing question (synthesising — what do the documents tell us together?)
   - Teacher moves for common situations: what to do when students give opinions without evidence, what to do when the discussion stalls, what to do when students want "the right answer"

4. **Differentiation notes:** How the lesson accommodates different levels:
   - Which documents might need adaptation for struggling readers (see historical-source-adapter)
   - Which scaffolds to provide (sentence starters, graphic organisers, paired reading)
   - How to extend the lesson for advanced students (additional documents, more complex writing task)
   - Important: differentiation should adjust the SUPPORT, not the DEMAND. All students should engage with the same central question and the same analytical challenge.

5. **Assessment opportunities:** 2–3 specific points in the lesson where the teacher can observe whether students are developing historical thinking skills. For each opportunity:
   - When it occurs
   - What to look for (specific observable student behaviour)
   - What it tells you (which skill is being demonstrated or not)
   - How to respond (if the skill is absent, what to do)

Return your output in this exact format:

## Document-Based Lesson Plan

**Central question:** [Question]
**Students:** [Level]
**Duration:** [Time]
**Documents:** [Brief summary of the set]

### Phase 1: Background Knowledge ([time])

**Teacher does:** [Actions]
**Students do:** [Actions]
**Purpose:** [What this phase equips students with]

### Phase 2: Central Question ([time])

**Teacher does:** [Actions]
**Students do:** [Actions]

### Phase 3: Document Investigation

**Round 1 ([time]):**
**Documents:** [Which ones]
**Strategy focus:** [Which skill]
**Teacher does:** [Actions, including any think-aloud]
**Students do:** [Actions]
**Check-in:** [Brief whole-class connection to central question]

**Round 2 ([time]):**
[Same format]

**Round 3 ([time], if applicable):**
[Same format]

### Phase 4: Discussion and Writing ([time])

**Discussion questions:**
[2–3 questions building from factual to interpretive]

**Teacher moves:**
[Guidance for common situations]

**Writing task (if applicable):**
[Prompt, evidence requirement, time]

### Strategy Instruction Plan

[Which strategies, when, introductory or reinforcing]

### Discussion Plan

[Specific questions and protocols]

### Differentiation Notes

[Support adjustments — not demand reductions]

### Assessment Opportunities

[2–3 specific observation points with indicators and responses]

**Self-check before returning output:** Verify that (a) all four phases are present and timed to fit the lesson duration, (b) the document rounds build progressively in complexity, (c) the discussion phase has specific questions, not just "discuss the central question," (d) strategy instruction is embedded in the document rounds rather than delivered as a standalone mini-lesson disconnected from the sources, (e) differentiation adjusts support without reducing demand, and (f) the lesson returns to the central question repeatedly — it is the thread connecting all phases.
```

## 示例输出

**场景：** *Central question: "Did Pocahontas rescue John Smith?" / Document set: "4 documents: Smith 1608, Smith 1624, Adams 1867, Lemay 1991 (all adapted)" / Student level: "Year 8, third document-based lesson — familiar with sourcing, still developing close reading" / Lesson duration: "2 × 50-minute periods" / Target skills: "Sourcing and close reading (primary), corroboration (secondary)" / Background knowledge: "Students have studied early English colonisation; they know who Pocahontas and John Smith are, mostly from popular culture" / Writing task: "Short evidence-based paragraph answering the central question"*

---

## 基于文献的教案

**核心问题：** 宝嘉康蒂救了约翰·史密斯吗？
**学生：** 八年级，第三节基于文献的历史课
**时长：** 2 × 50 分钟课时（共 100 分钟）
**文献：** Smith 1608（改编）、Smith 1624（改编）、Adams 1867（改编摘要）、Lemay 1991（改编摘要）

### 第 1 阶段：背景知识（10 分钟——第 1 课时）

**教师行动：** 播放 2 分钟迪士尼《风中奇缘》片段（营救场景）。提问："What do you already know about Pocahontas and John Smith? Where did you learn it?" 将回答记录在黑板上。提供一份涵盖 1607–1624 年的简明时间轴（RLH 课程工具 1.1）。
**学生行动：** 分享已有认知，记录时间轴日期。不少人会提到迪士尼版本；这正是预设的起点。
**目的：** 激活学生已有的背景认知（主要来自流行文化），随后课程将使其复杂化。迪士尼版本不被直接否定，而是被定位为众多记述之一——一个需要用证据检验的叙事。

### 第 2 阶段：核心问题（3 分钟——第 1 课时）

**教师行动：** 在显眼处张贴问题："Did Pocahontas rescue John Smith?" 说明："Historians have been arguing about this for 150 years. Today you're going to examine the same evidence they used and make your own argument. By the end of tomorrow's lesson, you'll write a paragraph answering this question using evidence from the documents."
**学生行动：** 抄写问题，明确自己的任务是调查而非猜测。

### 第 3 阶段：文献调查

**第 1 轮（20 分钟——第 1 课时）：**
**文献：** Smith 1608（《True Relation》）与 Smith 1624（《General History》）
**策略聚焦：** 溯源（主）与精读（次）
**教师行动：** 用出声思维结合 1624 年文献示范溯源（参见 strategy-modelling-guide）：在阅读前检查作者、日期、出版背景并生成假设。随后分发两份文献。结对完成工具 1.2（对比史密斯的记述）。
**学生行动：** 结对阅读两份记述，识别事实与语气的差异，完成比对练习纸，并在每份记述中划出三个揭示史密斯态度的词。
**阶段小结（5 分钟）：** 教师提问："What did you notice? Do these two accounts agree?" 收集 2–3 条观察。追问："Why would the same person tell the same story differently?" 不给出定论——让问题保持开放。

**第 2 轮（25 分钟——第 2 课时）：**
**文献：** Adams 1867 与 Lemay 1991
**策略聚焦：** 互证——比对两位历史学家如何使用相同的一手证据
**教师行动：** 简要介绍历史学家："Adams wrote in 1867 that Smith made the story up. Lemay wrote in 1991 that Smith was telling the truth but misunderstood what happened. They examined the SAME evidence you just looked at. Let's see what they argue." 分发两份摘要及工具 1.3（比对历史学家与史密斯）。
**学生行动：** 结对阅读两位历史学家的观点，完成比对工具：每位历史学家认为发生了什么？使用了什么证据？找出 Adams 与 Lemay 直接分歧的一个点。
**阶段小结（5 分钟）：** 教师提问："Adams and Lemay read the same documents you did. How did they reach different conclusions?" 引导学生认识到证据必须经过阐释，而阐释取决于你提出的问题。

### 第 4 阶段：讨论与写作（15 分钟——第 2 课时）

**讨论问题：**
1. "Based on ALL the sources, what do you think probably happened? Did Pocahontas rescue John Smith?"（开场——引出立场）
2. "What is your strongest piece of evidence? How does it support your position?"（追问——要求证据）
3. "Can we know FOR CERTAIN what happened? Why or why not? What does that tell us about how history works?"（收束——提炼认识论启示）

**教师引导动作：**
- 如果学生只说 "I think..." 而不给证据："What document supports that? Can you point to a specific part?"
- 如果讨论冷场："Let's go back to Round 1. Smith described the same meeting as 'kindly' in 1608 and 'barbarous' in 1624. What does that tell us?"
- 如果学生追问“标准答案”："Historians have been debating this for 150 years and they still disagree. Your job isn't to find the right answer — it's to make the best argument you can with the evidence."

**写作任务（10 分钟）：**
"Did Pocahontas rescue John Smith? Write one paragraph answering this question. You must include evidence from at least two documents. You must explain WHY your evidence supports your answer."

### 策略教学计划

**溯源：** 强化巩固（这是学生的第三节课）。教师用一份文献示范（对 Smith 1624 进行出声思维），随后学生独立对 Smith 1608 溯源。到第 2 轮时，学生应能无需提示就对历史学家的阐释进行溯源。

**精读：** 发展中。通过第 1 轮的划词任务嵌入——学生识别揭示史密斯态度的用词。本节课不单独正式示范，教师在第 1 轮小结时引导学生注意关键用词选择。

**互证：** 首次引入。第 2 轮是首次对历史学家阐释进行结构化比对，由比对工具搭建支架。第 4 阶段的讨论使互证社会化——学生听到不同证据支撑的不同立场，这正是行动中的互证。

**语境化：** 非本课重点，但有所涉及。背景知识阶段提供时间轴语境；对 1624 年文献溯源时自然引出语境化（彼时宝嘉康蒂已成名）。本课不作为独立策略专门教授。

### 讨论计划

第 4 阶段讨论是整节课最重要却也最容易被跳过的部分，必须确保落实。

**开场：** "So — did she rescue him? Hands up: who thinks yes? Who thinks no? Who's not sure?"（快速举手调查以呈现立场分布。“不确定”选项很重要——它使不确定性正当化。）

**追问：** 点名来自不同立场的 2–3 名学生。对每位学生问："What's your strongest piece of evidence?" 接着问："Does anyone have evidence that contradicts what [student] just said?" 这将互证示范为一种社会性实践——学生在实时比对证据。

**收束：** "We've heard different arguments supported by different evidence. Can we ever know FOR CERTAIN whether the rescue happened?" 预计部分学生会说不能。继续追问："If we can't know for certain, does that mean studying it is pointless? What did we LEARN by investigating this question, even without a definitive answer?" 引导至：我们学会了批判性阅读史料、追问谁写了什么以及为什么写、比对不同记述——这些技能超越这一个历史问题本身。

### 分层教学说明

**针对阅读困难学生：** 使用史密斯记述的改编版本（参见 historical-source-adapter）。将阅读困难学生与阅读能力较强的学生结对进行文献分析。为写作任务提供句首提示："Based on the evidence from [document], I believe that... because..."

**针对 EAL 学生：** 提供改编史料中的词库。允许在用英语写作前先用第一语言进行结对讨论。比对工具（练习纸）提供的视觉结构有助于理解。

**针对学有余力学生：** 完成主写作任务后，提供 Lewis 和 Barbour 的阐释（RLH 课程史料 1.5 与 1.6）作为拓展文献。挑战："Does this new evidence change your argument? How?"

**重要原则：** 所有学生都使用相同的核心文献调查同一个核心问题。分层调整的是“支持”（改编史料、句首提示、结对阅读），而不是“分析要求”。阅读困难的学生依然回答“宝嘉康蒂救了约翰·史密斯吗？”，而不是被换成一个更简单的问题。

### 评估机会

**1. 第 1 轮小结——溯源习惯**
*时机：* 结对完成史密斯两份记述的比对之后。
*观察要点：* 各组在阅读前是否查看了出处注？能否识别 16 年的时间间隔并解释为何重要？
*说明什么：* 溯源是否正在成为习惯（这是他们的第三节基于文献的课）。
*若缺失：* 提示："What's the first thing we do before reading a document? What does the source note tell you?"

**2. 第 2 轮——互证**
*时机：* 结对阅读 Adams 和 Lemay 期间。
*观察要点：* 学生能否指出两位历史学家的一个具体分歧点？是在推理“为什么”分歧，还是只停留在注意到分歧？
*说明什么：* 学生是否正从“指出分歧”迈向“围绕分歧推理”。
*若缺失：* 追问："Adams says Smith made it up. Lemay says it happened. They read the SAME evidence. How is that possible?"

**3. 写作任务——证据运用**
*时机：* 段落写作期间。
*观察要点：* 学生是否引用了至少两份文献的具体证据？证据是否真正支撑其主张，还是仅擦边相关？
*说明什么：* 学生能否建构基于证据的论证——这是整合溯源、精读与互证的终极技能。
*若缺失：* 在学生动笔前示范一句："For example, I might write: 'Smith's 1608 account describes Powhatan as kind and welcoming, but his 1624 account describes the same meeting as barbarous and violent. This contradiction suggests that Smith's later account may have been influenced by Pocahontas's fame in England.' Notice how I used evidence from two documents and explained what it means."

---

## 已知局限性

1. **本技能负责设计教案，但无法保证实施保真度。** Reisman (2012) 发现，即使经过培训与观课，教师仍经常省略或压缩讨论阶段。本技能提供了具体的讨论问题与规程，但教师是否落实取决于课堂条件、时间压力以及教师驾驭开放式讨论的舒适度。讨论计划刻意写得具体，正是为了尽可能降低实施门槛。

2. **教案假设文献集已经策展完毕且史料已经改编。** 如果教师提供未经改编的原始难懂史料，教案可能会高估学生的完成度。教师在设计课程前，应先使用 historical-source-adapter 针对具体学生水平准备文献。

3. **四段式结构是一个设计框架，而非僵化模板。** 有些课可能需要更长的背景知识阶段（若学生缺乏关键语境）、更短的讨论阶段（若时间紧张）或更多的文献轮次（若文献集特别丰富）。本技能在该框架内设计，但教师应结合专业判断和对学生的了解灵活调整。
