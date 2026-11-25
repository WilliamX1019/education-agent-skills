---
# AGENT SKILLS STANDARD FIELDS (v2)
name: historical-thinking-assessment-designer
description: "设计让学生的历史思维可见的形成性评估——揭示他们是否会溯源、精读、语境化与互证。适用于评估历史思维技能或规划诊断性测评时。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS
skill_id: "historical-thinking/historical-thinking-assessment-designer"
skill_name: "历史思维评估设计师"
domain: "historical-thinking"
version: "1.0"
contributor: "Sean Hu"
evidence_strength: "strong"
evidence_sources:
  - "Wineburg, Smith & Breakstone (2018) — What is learned in college history classes?"
  - "Reisman (2012) — Reading like a historian: a document-based history curriculum intervention in urban high schools"
  - "Wineburg (2007) — Unnatural and essential: the nature of historical thinking"
  - "Wineburg (1991) — Historical problem solving: cognitive processes in the evaluation of documentary and pictorial evidence"
  - "Wiliam (2011) — Embedded Formative Assessment"
  - "Gottlieb & Wineburg (2012) — Between Veritas and Communitas: epistemic switching in the reading of academic and sacred history"
input_schema:
  required:
    - field: "target_skills"
      type: "string"
      description: "评估应瞄准哪些历史思维技能——溯源、精读、语境化、互证中的一项或多项，或“全部四项”"
    - field: "student_level"
      type: "string"
      description: "年龄/年级以及当前历史思维发展水平"
    - field: "assessment_purpose"
      type: "string"
      description: "教师希望从评估中了解什么——例如‘学生在无提示下是否会在阅读前溯源’、‘学生能否语境化一份未见过的文献’、‘单元开始的基线诊断’、‘单元末对全部四项技能的检查’"
  optional:
    - field: "historical_topic"
      type: "string"
      description: "评估应取材的主题或时期——若未提供，本技能将选用无需专门先验知识即可作答的主题"
    - field: "assessment_format"
      type: "string"
      description: "偏好的形式——例如‘建构性反应（简短书面回答）’、‘选择题’、‘混合’、‘基于讨论’、‘文献分析任务’"
    - field: "time_available"
      type: "string"
      description: "可用于评估的时间——影响任务数量与复杂度"
    - field: "prior_instruction"
      type: "string"
      description: "学生已经接受过的历史思维教学——使评估瞄准已教授的内容"
    - field: "curriculum_framework"
      type: "string"
      description: "来自上下文引擎：正在使用的相关课程标准或历史思维框架"
output_schema:
  type: "object"
  fields:
    - field: "assessment_tasks"
      type: "array"
      description: "评估任务——每项包含文献或刺激材料、问题或提示语、任务旨在揭示的内容以及评分指南"
    - field: "scoring_guide"
      type: "object"
      description: "每项任务的量规或评分指南——包含初学、发展中和熟练回答的描述语，并与所评估的具体历史思维技能挂钩"
    - field: "diagnostic_value"
      type: "object"
      description: "评估结果告诉教师什么——如何解读不同的作答模式以及它们指向何种教学调整"
    - field: "validity_notes"
      type: "object"
      description: "评估测量了什么、没有测量什么——包括构念无关变异以及对结果有效解读的任何威胁"
chains_well_with:
  - "document-based-lesson-designer"
  - "sourcing-skill-builder"
  - "close-reading-skill-builder"
  - "contextualisation-skill-builder"
  - "corroboration-skill-builder"
  - "assessment-validity-checker"
  - "formative-assessment-technique-selector"
  - "criterion-referenced-rubric-generator"
  - "gap-analysis-from-student-work"
  - "historical-source-adapter"
teacher_time: "4 分钟"
tags: ["assessment", "historical-thinking", "formative-assessment", "HATs", "diagnostic", "sourcing", "close-reading", "contextualisation", "corroboration", "DIG"]
---

# 历史思维评估设计师

## 本技能的作用

设计让学生的历史思维变得可见的形成性评估任务——揭示学生是否在进行溯源、精读、语境化和互证，以及处于何种精细程度。输出包括附带文献与提示语的评估任务、区分初学/发展中/熟练回答的评分指南、关于如何解读结果的诊断指导，以及指出评估测量了什么与未测量什么的效度说明。

本技能解决的根本问题是：绝大多数历史测试考查的是事实回忆，而非历史思维。一道问 "When was the Battle of Gettysburg?" 的题目测量的是学生是否背下了日期；而一道提供创作于 1932 年的画作并问 "Does this painting help us understand what happened at the first Thanksgiving in 1621? Explain your reasoning" 的题目，测量的则是学生是否会考虑史料与其所描绘事件之间的时间关系。前者告诉你学生记住了什么；后者告诉你学生如何思考。

Wineburg, Smith & Breakstone (2018) 令人震撼地揭示了这一落差。使用历史思维评估（History Assessments of Thinking, HATs）——针对溯源、语境化和主张-证据推理的简短建构反应任务——他们发现 94% 的大学一年级学生忽略了 1621 年事件与 1932 年画作之间 300 年的时间差。高年级历史专业学生表现也仅略好一点：在一项要求把参议院听证会的“存在本身”（而非其内容）作为反战公众反对声音证据的任务上，78% 的人得了零分。学生始终为了内容而非语境阅读——关注文献说了什么，却不关注其创作时的处境。

这些发现证实，历史思维技能必须被明确评估，而不能想当然。而 HATs 模型展示了如何做到这一点：围绕单份文献设计简短任务，提出只有调动特定历史思维技能才能答好的问题。本技能正是遵循该模型生成评估。

## 循证基础

Wineburg, Smith & Breakstone (2018) 在美国国会图书馆支持下开发了历史思维评估（HATs）。三套 HATs 施测于 78 名低年级和 49 名高年级大学生。每道 HAT 呈现一份附带完整书目信息的文献（画作、证词笔录、戏单），并提出需要溯源、语境化或主张-证据推理才能答好的问题。评分量规采用三级：基础（Basic, 0 分）——无目标技能证据；萌芽（Emergent, 1 分）——有部分证据但不完整或流于表面；熟练（Proficient, 2 分）——清晰展示该技能。结果发人深省：低年级学生 12 分满分平均不到 0.5 分，最高分仅为 3 分。HATs 模型证明，历史思维可以被简短、真实且具诊断性地评估——每项任务都能揭示特定技能的存在与否。

Reisman (2012) 使用一份 30 题的历史思维测试（22 道选择题 + 8 道建构反应题，α = .79）和一份 20 题的迁移测试作为结果测量。历史思维测试评估溯源、精读、语境化和互证策略的应用。实验组学生在该测量上显示出显著提升，证明历史思维技能既可教又可评。Reisman 发现效应集中在溯源和精读（而非语境化或互证），这提供了诊断指导：如果评估显示学生溯源表现良好但语境化较差，这与研究完全一致——不同技能发展速度不同，需要不同的教学方法。

Wiliam (2011) 确立了形成性评估的价值在于让学生的思维可见，从而使教师能够调整教学。最有用的形成性评估任务是那些能够区分“已发展该技能的学生”与“尚未发展该技能的学生”的任务——在这些任务中，错误答案与正确答案同样富有信息量，因为它揭示了具体的误区或技能缺口。对历史思维而言，这意味着评估任务应当让会溯源的学生与不会溯源的学生给出截然不同的回答，且学生未能溯源的具体方式会揭示他们下一步需要学什么。

Wineburg (2007) 指出，若没有恰当的评估，“态度批判（being critical）”与“批判性思考（thinking critically）”之间的区别是看不见的。他的学生 Jacob 对哥伦布充满激情地批判——但他的批判受激活扩散（他早已相信的关于哥伦布的一切）驱动，而非对文献的学科分析。一道关于哥伦布事实的选择题永远无法揭示这一点；只有要求 Jacob 将文献作为“文献”来对待——关注其出处、语境与语言——的任务，才能让这一区别显现出来。

Gottlieb & Wineburg (2012) 证明，专家与新手提及史料出处的“数量”相近——区别在于“质量”。因此，评估任务必须区分“提及出处”与“审问出处”。写下 "This was written by John Smith in 1624" 只是提及出处；写下 "Smith wrote this 17 years after the event, at a time when Pocahontas had become famous, which may explain why he added the rescue story" 才是审问出处。评分指南必须捕捉这一区别。

## 输入模式

教师必须提供：
- **Target skills（目标技能）：** *例如："Sourcing only" / "Sourcing and contextualisation" / "All four skills" / "Corroboration — I want to know if students can compare two accounts"*
- **Student level（学生水平）：** *例如："Year 8, midway through first term of document-based lessons" / "Year 11 IB History, experienced with source analysis" / "Year 7, baseline diagnostic before any instruction"*
- **Assessment purpose（评估目的）：** *例如："Baseline diagnostic — I want to know where students are before I start teaching sourcing" / "Mid-unit check — are students sourcing without prompting?" / "End-of-unit — can students deploy all four skills on unfamiliar documents?"*

可选：
- **Historical topic（历史主题）：** 取材主题——若省略，将使用普遍易懂的主题
- **Assessment format（评估形式）：** 偏好形式
- **Time available（可用时间）：** 限制任务数量与复杂度
- **Prior instruction（先前教学）：** 已教授的内容
- **Curriculum framework（课程框架）：** 用于对齐

## Prompt

```
You are an expert in assessing historical thinking skills, with deep knowledge of the History Assessments of Thinking (HATs) model developed by Wineburg, Smith, and Breakstone (2018), Reisman's (2012) assessment of sourcing, close reading, contextualisation, and corroboration, and Wiliam's (2011) principles of formative assessment. You understand that the purpose of formative assessment is to make student thinking visible so that teachers can adjust instruction — and that most history assessments fail at this because they test factual recall rather than historical thinking.

Your task is to design a formative assessment:

**Target skills:** {{target_skills}}
**Student level:** {{student_level}}
**Assessment purpose:** {{assessment_purpose}}

The following optional context may or may not be provided. Use whatever is available.

**Historical topic:** {{historical_topic}} — if not provided, select a topic and document that are accessible without specialised prior knowledge (the assessment should test historical thinking, not content knowledge).
**Assessment format:** {{assessment_format}} — if not provided, default to constructed response (short written answers), as these reveal more about student thinking than multiple choice.
**Time available:** {{time_available}} — if not provided, design for 15–20 minutes (a single task or brief set of tasks, not a full exam).
**Prior instruction:** {{prior_instruction}} — if provided, align the assessment to what has been taught. If not, design tasks that can function as baseline diagnostics.
**Curriculum framework:** {{curriculum_framework}}

Design the following:

1. **Assessment tasks:** For each task:
   - **Document/stimulus:** A brief historical document or source (with full attribution) that students will work with. The document should be short enough to read in 2–3 minutes and should contain features that reward the target skills — e.g., source information that is analytically productive for sourcing tasks, language choices that reward close reading, a date that matters for contextualisation.
   - **Question/prompt:** The question students must answer. Design the question so that a student who deploys the target skill will answer DIFFERENTLY from a student who does not. The question should not cue the skill by name (don't say "Source this document") — it should require the skill without naming it.
   - **What this task reveals:** Which specific skill the task targets and what a successful vs. unsuccessful response looks like.

2. **Scoring guide:** For each task, a three-level rubric:
   - **Basic (0):** The student does not demonstrate the target skill. Describe what a Basic response looks like — what the student does instead of the target skill (e.g., evaluates the painting by whether it matches their beliefs about Thanksgiving rather than noting the 300-year temporal gap).
   - **Emergent (1):** The student demonstrates the skill partially or superficially. Describe what partial demonstration looks like (e.g., notes the date of the painting but doesn't reason about what the temporal gap means for its reliability as evidence).
   - **Proficient (2):** The student demonstrates the skill fully. Describe what a proficient response includes (e.g., identifies the temporal gap, reasons that a 1932 painter could not have witnessed 1621 events, and concludes that the painting reflects 1930s ideas about Thanksgiving rather than historical reality).

   The scoring guide must distinguish between mentioning a skill and deploying it (Gottlieb & Wineburg, 2012). "This was written by Smith in 1624" is mentioning. "Smith wrote this 17 years after the event, which raises questions about..." is deploying.

3. **Diagnostic value:** What the results tell the teacher:
   - **If most students score Basic:** What this suggests about the class's skill development and what instruction to prioritise
   - **If most students score Emergent:** What the gap between Emergent and Proficient typically looks like and how to close it
   - **If scores vary across skills:** What it means if students source well but don't contextualise (consistent with Reisman, 2012) and what instructional adjustment to make
   - **Specific response patterns to watch for:** Common wrong answers that reveal specific misconceptions (not just "the student didn't get it" but "the student evaluated the source by its content rather than its provenance, which suggests...")

4. **Validity notes:** What the assessment does and does not measure:
   - What construct the assessment targets
   - Potential construct-irrelevant variance (e.g., does the assessment inadvertently test reading comprehension, content knowledge, or writing ability rather than historical thinking?)
   - Whether the assessment can distinguish between students who lack the skill and students who possess the skill but lack the content knowledge needed to deploy it in this specific context

Return your output in this exact format:

## Historical Thinking Assessment

**Target skills:** [Skills]
**Students:** [Level]
**Purpose:** [What the teacher wants to learn]
**Time:** [Duration]

### Task 1: [Brief title]

**Document:**
[Brief source with full attribution]

**Question:**
[The prompt — designed to require the target skill without naming it]

**What this reveals:** [Target skill and what success vs. failure looks like]

**Scoring guide:**
- **Basic (0):** [Description of a response that does not demonstrate the skill]
- **Emergent (1):** [Description of a partial or superficial demonstration]
- **Proficient (2):** [Description of a full demonstration]

[Repeat for additional tasks]

### Diagnostic Value

**If most students score Basic:** [What it means and what to do]
**If most students score Emergent:** [The gap and how to close it]
**If scores vary across skills:** [What the pattern reveals]
**Response patterns to watch for:** [Specific wrong answers and what they diagnose]

### Validity Notes

**What this assesses:** [The construct]
**Potential threats:** [Construct-irrelevant variance]
**Important caveat:** [Skill vs. knowledge distinction]

**Self-check before returning output:** Verify that (a) the questions require the target skill without naming it, (b) the scoring guide distinguishes between mentioning and deploying the skill, (c) a student who sources/close-reads/contextualises/corroborates will answer DIFFERENTLY from one who doesn't — the task discriminates, (d) the diagnostic value provides specific instructional guidance, not just "teach more sourcing," and (e) the validity notes honestly identify what the assessment does not measure.
```

## 示例输出

**场景：** *Target skills: "Sourcing and contextualisation" / Student level: "Year 9, have received six weeks of sourcing instruction, contextualisation introduced but not yet practised independently" / Assessment purpose: "Mid-unit check — can students source without prompting, and are they beginning to contextualise?" / Time available: "15 minutes" / Historical topic: "not specified — use an accessible topic"*

---

## 历史思维评估

**目标技能：** 溯源与语境化
**学生：** 九年级，接受过六周溯源教学，语境化已引入但尚未独立练习
**目的：** 单元中期检查——溯源习惯与萌芽中的语境化
**时间：** 15 分钟（两项任务，每项约 7 分钟）

### 任务 1：感恩节画作（溯源）

**文献：**
*J.L.G. Ferris 的画作《第一个感恩节 1621》（The First Thanksgiving 1621）彩色复制品*
出处注："J.L.G. Ferris, *The First Thanksgiving 1621*, oil on canvas, painted c. 1912–1915, published 1932."

**问题：**
"Does this painting help historians understand the relationship between the Pilgrims and the Wampanoag people in 1621? Explain your reasoning."

**揭示内容：** 学生在评估文献作为历史证据的有用性时，是否关注出处信息（画作创作日期 vs. 事件发生日期）。会溯源的学生会注意到 300 年的时间差；不会溯源的学生则会根据画作内容是否符合自己对感恩节的既有认知来评判。

**评分指南：**
- **基础（0 分）：** 学生仅凭内容评判画作。"Yes, it shows them eating together peacefully, so they had a good relationship" 或 "No, it makes it look too friendly when actually the Pilgrims were mean to the Native Americans." 在这两种情况下，学生都在依据画作是否符合自己的先入之见做判断，画作日期被完全忽略。
- **萌芽（1 分）：** 学生注意到了日期，但未充分推理其含义。"This was painted in 1912, which is a long time after 1621" 或 "The painter wasn't there, so it might not be accurate." 识别出了时间差，但推理止步于“可能不准确”，未解释“为什么”这一差距重要，也未说明画作反而能反映什么。
- **熟练（2 分）：** 学生识别时间差并推理其后果。"This was painted nearly 300 years after 1621, so Ferris couldn't have seen this event. The painting probably shows what people in the early 1900s imagined Thanksgiving looked like, not what actually happened. It might be more useful as evidence of how Americans in 1912 wanted to remember Thanksgiving than as evidence of the actual event."

### 任务 2：征兵海报（语境化）

**文献：**
*一张第一次世界大战英国征兵海报：一名男子坐在扶手椅上，他的孩子问道：“爸爸，你在大战中做了什么？（Daddy, what did YOU do in the Great War?）”*
出处注："Parliamentary Recruiting Committee, printed by Johnson, Riddle & Co., London, 1915."

**问题：**
"Why was this poster created in 1915? What was happening at that time that made it necessary?"

**揭示内容：** 学生能否将文献与其历史语境相连。会语境化的学生会将海报与 1915 年的处境联系起来（英国在 1916 年实行义务兵役制之前依赖志愿入伍；最初的热情正在消退；伤亡不断攀升）。不会语境化的学生则只描述海报展示了什么，而不将其与海报为何存在相连。

**评分指南：**
- **基础（0 分）：** 学生描述海报内容或陈述其显而易见的目的，却未将其与 1915 年具体联系起来。"It was created to make men feel guilty so they would join the army" 或 "It's showing a dad who didn't fight in the war." 这些回答识别了海报的说服意图，但没有解释为什么 1915 年需要这种说服——即使海报来自 1914 年或 1917 年，回答也一样。
- **萌芽（1 分）：** 学生与战争建立了笼统联系，但未具体说明 1915 年有什么特点使这张海报成为必要。"It was created because World War I was happening and they needed soldiers" 或 "Britain needed more men to fight." 语境存在但模糊——学生尚未指出 1915 年引发此类征兵宣传的具体因素。
- **熟练（2 分）：** 学生将海报连接到 1915 年的具体处境。"By 1915, the war had been going on for over a year and the initial rush of volunteers was slowing down. Britain hadn't introduced conscription yet, so they relied on posters like this to pressure men into enlisting. The emotional manipulation — using children to guilt fathers — suggests that straightforward patriotic appeals weren't working anymore." 学生运用语境知识，不仅解释了海报“为什么”被创作，还解释了“为什么”它在这一特定时刻采取了这种特定形式。

### 诊断价值

**如果大多数学生在任务 1（溯源）得基础分：** 经过六周溯源教学后，学生理应关注出处注。如果大多数仍得基础分，说明溯源尚未成为习惯——学生仍在未检查出处的情况下直接阅读内容。应退回基础溯源常规：遮住文献正文，要求在阅读前先花 60 秒研究出处注。该技能已引入但尚未内化。

**如果大多数学生在任务 1 得萌芽分：** 习惯正在形成——学生注意到了日期——但缺乏分析深度。他们识别出差距却未推理其影响。这正是 Gottlieb & Wineburg (2012) 指出的区别：提及 vs. 审问。教学应聚焦于“那又怎样？（So what?）”这一步：在学生指出日期后，追问这对其作为证据的可靠性意味着什么。

**如果大多数学生在任务 2（语境化）得基础分，但在任务 1（溯源）得萌芽/熟练分：** 这与研究完全一致。Reisman (2012) 发现溯源有处理效应而语境化没有。溯源更具体、发展更快；语境化既需要知识又需要调动它的倾向。检查缺口在于知识（学生不知道 1915 年的征兵状况）还是在于调动（知道但不会连接到文献）。若缺知识，补充更多背景；若缺调动，使用 contextualisation-skill-builder 中的两步架桥支架。

**需要警惕的作答模式：**
- *按内容契合度评判：* "Yes, the painting is helpful because it shows a peaceful meal" —— 学生把画作内容当作透明真相。他们需要明白所有史料都有带着立场的作者。
- *二元可靠性判断：* "We can't trust this because it was painted 300 years later" —— 观察正确，结论错误。这幅画“很有用”——作为后代如何想象该事件的证据。学生需要明白“作为 1621 年事件的记录不可靠”不等于“毫无用处”。
- *只描述不联结：* "The poster shows a father with his children" —— 纯粹描述。学生没有思考海报“为什么”存在，只停留在它展示了“什么”。这是为了内容而阅读，而非语境。

### 效度说明

**本评估测量什么：** 学生在解读历史文献时是否会自发调动溯源（任务 1）与语境化（任务 2）。任务经过专门设计，使调动目标技能产生的回答与未调动时“在质上截然不同”——不是同一个回答的更好版本，而是根本不同的回答。

**潜在威胁：** 任务 2（语境化）测量的可能是关于一战征兵的内容知识，而非语境化技能本身。不了解 1915 年英国情况的学生，无论技能水平如何都无法语境化这张海报。如果对尚未学过一战的学生施测，任务 2 测的就是知识而非技能——低分不应被解读为学生不会语境化。如果内容知识不确定，可考虑将海报替换为学生已学时期的文献。

**重要提示：** 在熟悉主题上得熟练分的学生，未必能将技能迁移到陌生主题上。教学期间溯源和语境化是用特定文献类型练习的；学生能否将这些技能泛化到新类型史料仍是一个开放问题。单元末评估应当至少包含一份课堂未涉及主题的文献，以检验迁移（参见 Reisman, 2012，她使用陌生当代议题发现了显著迁移效应）。

---

## 已知局限性

1. **建构反应任务比选择题更能揭示学生思维，但同时也测量了写作能力。** 一名具备历史思维但写作表达薄弱的学生，得分可能低于其实际历史思维水平。教师应结合课堂讨论观察（参见各技能构建器中的评估指标）进行三角互证。在条件允许时，允许学生同时用口头和书面方式解释推理。

2. **HATs 模型（Wineburg, Smith & Breakstone, 2018）是在美国大学生阅读美国史文献的背景下开发并检验的。** 任务结构（文献 + 需要特定技能的问题）可以迁移到其他语境，但具体文献与评分描述语必须针对不同年龄段、国家课程和历史主题进行调适。

3. **形成性评估只有在能改变教学时才有用。** 诊断价值部分为每种得分模式提供了具体教学指导，但教师必须采取行动。如果评估揭示了学生不会语境化，却未引发任何教学调整，那就是浪费机会。评估的全部价值在于接下来发生什么。
