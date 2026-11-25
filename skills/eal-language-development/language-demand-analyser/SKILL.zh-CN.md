---
# AGENT SKILLS STANDARD FIELDS (v2)
name: language-demand-analyser
description: "分析课堂任务的语言需求，识别 EAL 与多语学习者面临的障碍。适用于调整任务、规划支持或评估语言可及性时。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "eal-language-development/language-demand-analyser"
skill_name: "语言需求分析器"
domain: "eal-language-development"
version: "1.0"
evidence_strength: "strong"
evidence_sources:
  - "Cummins (1981, 2000) — BICS/CALP framework: Basic Interpersonal Communication Skills vs. Cognitive Academic Language Proficiency"
  - "Gibbons (2002, 2015) — Scaffolding Language, Scaffolding Learning: teaching English language learners in the mainstream classroom"
  - "Schleppegrell (2004) — The Language of Schooling: a functional linguistics perspective"
  - "Zwiers (2014) — Building Academic Language: meeting Common Core standards across disciplines"
  - "Bailey & Heritage (2008) — Formative Assessment for Literacy: building reading and academic language skills across the curriculum"
input_schema:
  required:
    - field: "task_description"
      type: "string"
      description: "学生必须完成的具体课堂任务"
    - field: "student_level"
      type: "string"
      description: "年龄/年级"
    - field: "subject_area"
      type: "string"
      description: "课程学科"
  optional:
    - field: "language_proficiency"
      type: "string"
      description: "目标学生的 EAL 语言水平——例如 New to English、Early Acquisition、Developing、Consolidating、Competent"
    - field: "student_profiles"
      type: "array"
      description: "来自上下文引擎：第一语言、接受英语授课学校教育的时间、具体语言需求"
    - field: "task_materials"
      type: "string"
      description: "任务中使用的文本、练习纸或资源的描述"
    - field: "prior_language_instruction"
      type: "string"
      description: "已向这些学生明确教授过的语言特征"
output_schema:
  type: "object"
  fields:
    - field: "language_demand_profile"
      type: "object"
      description: "跨越四个维度的分析：词汇、语法、语篇和体裁"
    - field: "scaffold_recommendations"
      type: "object"
      description: "针对每个语言需求维度的具体支架"
    - field: "priority_actions"
      type: "array"
      description: "如果时间有限，最具影响力的 2–3 个可实施支架"
    - field: "teacher_language_notes"
      type: "string"
      description: "教师在任务期间自身的语言使用如何支持理解与参与"
chains_well_with:
  - "vocabulary-tiering-tool"
  - "scaffolded-task-modifier"
  - "academic-language-sentence-frame-generator"
  - "cognitive-load-analyser"
teacher_time: "3 分钟"
tags: ["EAL", "language-demands", "BICS-CALP", "scaffolding", "academic-language"]
---

# 语言需求分析器

## 本技能的作用

从四个维度识别课堂任务的语言需求——词汇（Tier 1/2/3）、语法（句式复杂度、时态、语态、情态）、语篇（文本结构、衔接、段落组织）和体裁（目的、受众、语域）——并为每个维度推荐具体支架。该分析让任务中“默认假设学生已掌握”却极少被明确教授的语言显现出来，揭示阻碍 EAL 学生展示其学科知识的隐性语言障碍。AI 在此尤为有价值，因为大多数教师是学科内容专家，而非任务所需语言特征的专家——他们知道一份优秀的科学实验结论是什么样的，但未必能清晰阐述它所需要的具体语法结构、语篇模式和词汇层级。

## 循证基础

Cummins (1981, 2000) 区分了基本人际交往技能（BICS）——EAL 学生通常在 1–2 年内发展的日常会话流利度——与认知学术语言能力（CALP）——课程学习所需的学术语言，其发展需要 5–7 年。这一区分至关重要，因为在日常对话中表现流利的学生，可能仍然缺乏完成课程任务所需的学术语言。Gibbons (2002, 2015) 将这一区分转化为课堂实践，证明必须明确识别并搭建语言需求的支架——仅靠“沉浸式学习”不足以发展学术语言。Schleppegrell (2004) 证明，学校语言并不仅仅是比日常语言“更难”——它在结构上就有所不同，以日常对话中不会出现的方式使用名词化、被动语态、复杂名词短语和抽象词汇。Zwiers (2014) 提供了一个跨学科识别和教授学术语言的实用框架，强调语言需求因学科而异。Bailey & Heritage (2008) 指出，语言需求存在于所有任务中，而不仅仅是读写任务——一道数学题也有语言需求（阅读题目、理解数学词汇、解释推理过程），这些需求对教师而言往往是隐形的，但对 EAL 学生却构成障碍。

## 输入模式

教师必须提供：
- **Task description（任务描述）：** 具体任务。*例如："Write a conclusion for a science experiment about friction" / "Read a textbook extract and answer comprehension questions about the causes of WW1" / "Participate in a class debate about whether zoos should be banned"*
- **Student level（学生水平）：** 年级。*例如："Year 8"*
- **Subject area（学科领域）：** 学科。*例如："Science" / "History" / "English" / "Mathematics"*

可选（如上下文引擎可用则自动注入）：
- **Language proficiency（语言水平）：** EAL 语言水平
- **Student profiles（学生档案）：** 第一语言、接受英语授课学校教育的时间、具体需求
- **Task materials（任务材料）：** 所用文本或资源的描述
- **Prior language instruction（先前的语言教学）：** 已经教授过的语言特征

## Prompt

```
You are an expert in language development and EAL pedagogy, with deep knowledge of Cummins' (1981, 2000) BICS/CALP framework, Gibbons' (2002, 2015) scaffolding approach, Schleppegrell's (2004) functional linguistics analysis of school language, and Zwiers' (2014) academic language framework. You understand that every curriculum task has language demands that are often invisible to subject teachers but create significant barriers for EAL students and students with limited academic language proficiency.

Your task is to analyse the language demands of:

**Task:** {{task_description}}
**Student level:** {{student_level}}
**Subject area:** {{subject_area}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Language proficiency:** {{language_proficiency}} — if not provided, analyse demands that would affect students across a range of EAL proficiency levels, from Early Acquisition to Consolidating.
**Student profiles:** {{student_profiles}} — if not provided, assume a class where several students are developing English language learners with conversational fluency but limited academic language proficiency.
**Task materials:** {{task_materials}} — if not provided, infer typical materials for this type of task.
**Prior language instruction:** {{prior_language_instruction}} — if not provided, assume no explicit language instruction has been given for this task.

Analyse language demands across these four dimensions:

1. **Vocabulary demands (Beck et al., 2002; Zwiers, 2014):**
   - **Tier 1 (everyday words):** Common words that may still be unfamiliar to EAL students — particularly idioms, phrasal verbs, and culturally specific terms.
   - **Tier 2 (academic vocabulary):** High-utility words used across subjects — "analyse," "significant," "evidence," "contrast," "evaluate." These are the highest priority for explicit teaching because they appear in every subject but are rarely taught in any.
   - **Tier 3 (technical vocabulary):** Subject-specific terms — "photosynthesis," "alliteration," "hypotenuse." Usually taught explicitly within the subject.
   - Identify specific vocabulary demands, not just categories.

2. **Grammar demands (Schleppegrell, 2004; Gibbons, 2015):**
   - Sentence complexity: simple, compound, or complex sentences required?
   - Tense requirements: which tenses must students use? (Science conclusions use past tense for method, present tense for conclusions; history uses past tense throughout.)
   - Voice: active or passive? (Science often requires passive voice: "the solution was heated" rather than "we heated the solution.")
   - Modality: hedging language, conditional statements? ("The results suggest..." "If the temperature increased, then...")
   - Nominalisation: turning processes into nouns? ("evaporate" → "evaporation"; "the water moved" → "the movement of water")
   - Identify SPECIFIC grammar demands, with examples from the task.

3. **Discourse demands (Schleppegrell, 2004; Zwiers, 2014):**
   - Text structure: what organisational pattern does the task require? (Chronological, cause-effect, compare-contrast, claim-evidence-reasoning)
   - Cohesion: what connectives and linking devices are needed? (Causal: "because," "therefore"; Comparative: "however," "in contrast"; Sequential: "firstly," "subsequently")
   - Paragraph structure: does the task require multi-paragraph organisation?
   - Reference: does the task require referring back to previous points or sources?

4. **Genre demands (Gibbons, 2002; Schleppegrell, 2004):**
   - What genre must students produce or comprehend? (Report, explanation, argument, narrative, recount, discussion)
   - What register is required? (Formal/informal, academic/conversational, impersonal/personal)
   - What is the purpose and audience? (To explain, to persuade, to describe, to evaluate)
   - Are there discipline-specific genre conventions? (Science reports differ from historical arguments)

For each dimension, provide:
- The specific language demands identified
- Why these demands may be invisible to the subject teacher
- Specific, practical scaffolds to address each demand

Return your output in this exact format:

## Language Demand Analysis: [Task Description]

**For:** [Student level] [Subject area]
**Task:** [Brief task description]

### Language Demand Profile

**Vocabulary Demands**
[Tier 1, 2, and 3 vocabulary identified, with specific words listed]

**Grammar Demands**
[Specific grammatical structures required, with examples]

**Discourse Demands**
[Text structure, cohesion, and organisational requirements]

**Genre Demands**
[Genre, register, purpose, and discipline-specific conventions]

### Scaffold Recommendations

**For vocabulary:** [Specific scaffolds]
**For grammar:** [Specific scaffolds]
**For discourse:** [Specific scaffolds]
**For genre:** [Specific scaffolds]

### Priority Actions (if time is limited)

[The 2–3 highest-impact scaffolds — the ones that will make the biggest difference for EAL students accessing this task]

### Teacher Language Notes

[How the teacher's own language use during the task — instructions, explanations, questioning — can support or hinder access]

**Self-check before returning output:** Verify that (a) all four language dimensions are analysed with specific examples, (b) scaffolds are practical and specific to the task, (c) the analysis identifies language demands that a subject teacher might not notice, (d) priority actions focus on the highest-impact scaffolds, and (e) the analysis distinguishes between language that should be pre-taught and language that can be supported during the task.
```

## 示例输出

**场景：** *Task: "Write a conclusion for a science experiment investigating the effect of surface area on the rate of dissolving" / Student level: "Year 8" / Subject area: "Science (Chemistry)" / Language proficiency: "Several students at Early Acquisition and Developing levels"*

---

## 语言需求分析：撰写科学实验结论

**适用对象：** 八年级科学（化学）
**任务：** 为一项探究表面积对溶解速率影响的实验撰写结论

### 语言需求档案

**词汇需求**

| 层级 | 词汇 | 说明 |
|------|------|------|
| Tier 1（日常词汇——但 EAL 学生可能仍不熟悉） | "rate"（同时具有日常含义与科学含义）、"surface"（抽象空间概念）、"dissolve"（日常对话中不常使用）、"crushed" | "Rate" 尤其容易造成困扰——EAL 学生可能知道它的“工资率”含义，但不知道“反应速率”。从日常含义到学术含义的转变常让学生措手不及。 |
| Tier 2（学术词汇——跨学科通用） | "investigate"、"effect"、"conclude"、"significant"、"therefore"、"demonstrate"、"evidence"、"support"（意为“支持假设”） | 这些词是撰写结论所必需的，但在科学课上却极少被教授。"Support" 尤其令人困惑——EAL 学生知道它表示“帮助/支撑”，但不知道它表示“为……提供证据”。 |
| Tier 3（专业词汇——特定学科） | "surface area"、"rate of dissolving"、"solute"、"solvent"、"particle"、"collision"、"hypothesis"、"variable"、"controlled variable" | 这些词在实验过程中理应已经教过，但可能尚未巩固。"Surface area" 是一个复合名词，需要两个词合在一起才能理解其意义。 |

**语法需求**

- **时态转换：** 结论部分需要用过去时描述发生了什么（"The crushed sugar dissolved faster"），并用现在时进行科学解释（"This is because smaller particles have a larger surface area"）。处于 Early Acquisition 阶段的 EAL 学生往往通篇只使用单一时态，或完全回避使用时态标记。
- **被动语态：** 科学写作规范要求使用被动结构："The experiment was repeated" 而非 "We repeated the experiment"；"The results were recorded" 而非 "I recorded the results"。被动语态是 EAL 学习者最晚掌握的语法结构之一——它在日常英语对话中很少出现，且结构复杂。
- **因果连接词：** 结论需要使用因果语言："because"、"therefore"、"as a result"、"this is due to"、"which means that"。处于 Developing 阶段的学生可能只掌握了 "because"。
- **模糊限制语/情态（Hedging/modality）：** 科学结论需要谨慎、非绝对的表达："The results suggest..." "This may indicate..." "It is likely that..." EAL 学生倾向于写得更绝对："This proves..."——这在科学上反而不够准确。
- **名词化（Nominalisation）：** "The sugar dissolved"（过程）→ "the rate of dissolving"（名词化）。"The particles collide" → "the rate of collision"。名词化是学术写作的典型特征，尤其具有挑战性，因为它将熟悉的动词变成了不熟悉的名词。

**语篇需求**

- **文本结构：** 结论需要遵循特定模式：陈述发现 → 用科学原理解释 → 联系假设 → 承认局限性。这一结构并不直观，也很少被明确说明。
- **衔接：** 结论必须合乎逻辑地连接各个观点："The results show that... This is because... Therefore... This supports the hypothesis that..." 每一句都必须与上一句相连。语言水平较低的 EAL 学生往往会写出彼此孤立的句子。
- **指代：** 结论必须回指假设、方法和结果——这需要使用代词和指代链："This pattern... These results... The data suggests..."

**体裁需求**

- **体裁：** 科学结论——一种具有自身规范的特定学校科学体裁（不同于英语课或历史课上的“结论”）。
- **语域：** 正式、非个人化、学术化。不使用 "I" 或 "we"（在许多学校科学写作规范中如此）。需要使用专业词汇。
- **目的：** 从科学概念的角度解释结果的意义——而不是叙述发生了什么。
- **学科特定规范：** 结论必须展现科学推理，而不是个人观点。"I think the sugar dissolved faster" 是不够的——必须写成 "The data demonstrates that increased surface area increases the rate of dissolving because..."。

### 支架建议

**针对词汇：**
- 明确预教 Tier 2 词汇："demonstrate"、"significant"、"support"（学术义项）、"evidence"。使用快速配对活动：学术词汇 → 学生友好型定义 → 科学句子中的例句。
- 如果已知学生的第一语言，为 Tier 3 术语提供双语词汇表——这能让学生将新的英语术语与他们可能已经理解的概念联系起来。
- 为本次实验创建专属词墙：图文并茂地展示关键术语。

**针对语法：**
- 提供时态指南："When you describe what HAPPENED → use past tense (dissolved, increased). When you explain WHY → use present tense (particles have, surface area increases)."
- 提供被动语态句式框架："The experiment was carried out to..." "The results were recorded by..." "It was found that..."
- 明确教授 3 个因果连接词："because"（学生已知）、"therefore"（新学——意为“所以，因此”）、"this is due to"（"because of" 的正式替代表达）。在写作期间将其展示在黑板上。
- 在卡片上提供模糊限制语短语："The results suggest..." "This may be because..." "It is likely that..."——向学生解释科学家使用这些表达是因为科学基于证据，而非绝对确定性。

**针对语篇：**
- 提供带有小标题的结论结构模板：Finding → Explanation → Hypothesis link → Limitations。学生在每个小标题下撰写，而不是写一个没有结构的段落。
- 提供用于衔接的句首提示："The results show that..." → "This can be explained by..." → "This supports/contradicts the hypothesis because..." → "However, a limitation was..."
- 明确示范如何衔接："Watch how each sentence connects to the one before it. This word — 'therefore' — tells the reader that what follows is a CONSEQUENCE of what came before."

**针对体裁：**
- 并排展示两个例子：一个是对实验的叙事性复述（"First we crushed the sugar, then we put it in water..."），另一个是科学结论（"The results demonstrate that crushing the sugar increased the rate of dissolving because..."）。提问："What's the difference? Why is the second one better for science?"
- 明确教授体裁规则："A conclusion explains what the results MEAN, not what you DID."

### 优先行动（如果时间有限）

1. **提供带有句首提示的结论结构模板。** 这一项支架即可同时解决语篇需求（文本结构、衔接）和语法需求（时态、因果连接词）。它让 EAL 学生能够把认知精力集中在科学内容上，而不必在如何组织写作上苦苦挣扎。

2. **预教 3 个核心 Tier 2 词汇："demonstrate"、"therefore"、"suggest"。** 这三个词会在科学结论中反复出现，并且可以迁移到其他学科。用五分钟结合例句进行明确教学，将在未来的许多任务中持续发挥作用。

3. **在黑板上展示时态规则。** 描述发生了什么用过去时，解释为什么用现在时。这一简单的视觉提示可以预防科学结论中最常见的语法错误，而且不占用课堂教学时间——只需写在黑板上即可。

### 教师语言说明

- **放慢指令语速，但不要简化内容。** 下达任务指令时，保持适中语速，使用较短的句子，并重复关键术语。不要简化科学内容——降低语言障碍并不等于降低思维要求。
- **在任务指令中避免使用习语。** "Right, let's wrap this up"（容易令人困惑），对比 "Now write your conclusion"（清晰明了）。"This is a piece of cake"（令人困惑），对比 "This part is straightforward"（虽然仍带习惯用法，但更透明）。
- **既要口头说出关键词汇，也要写下来。** EAL 学生处理书面英语比处理口头英语更可靠（因为他们可以重读，但无法重听）。说出关键术语的同时将其写在黑板上。
- **保持术语使用一致。** 不要在 "conclusion"、"summary"、"write-up" 和 "final paragraph" 之间来回切换——选定一个术语并坚持使用。母语者自然使用的同义替换，会给 EAL 学习者带来不必要的处理负荷。
- **检查学生对“任务”的理解，而不仅仅是对“科学”的理解。** 一名 EAL 学生可能完全理解科学原理，却不明白 "write a conclusion" 要求他做什么。可以这样检查："What are the four parts of your conclusion? What goes first?"

---

## 已知局限性

1. **该分析在总体层面上识别语言需求——无法预测个别学生的具体语言挑战。** 一名第一语言为西班牙语的学生所面临的英语挑战，与一名第一语言为普通话的学生所面临的挑战不同（例如冠词使用、时态标记、词序）。教师对单个学生第一语言和语言水平的了解，对于调整支架至关重要。

2. **语言需求与认知需求相互作用，而本分析为了清晰起见将其分开处理。** 在实践中，一名既在理解科学概念上遇到困难、又在用语言表达这些概念上遇到困难的学生，面临的是叠加挑战。支架有助于解决语言问题，但如果学生根本不理解科学内容，单靠语言支架是不够的。在聚焦语言产出之前，请确保概念理解已经稳固。

3. **该分析假设教师会临时性地使用支架。** 随着学生语言水平的提高，支架应当逐步撤除。如果永久提供句式框架，学生可能会对其产生依赖，而不是发展出独立的学术语言能力。目标是培养能力，而不是制造永久性的拐杖。
