---
# AGENT SKILLS STANDARD FIELDS (v2)
name: contextualisation-skill-builder
description: "培养学生将历史文献置于其时间与社会语境中的能力。适用于学生阅读史料时不考虑当时发生了什么，或知道背景却不加运用时。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS
skill_id: "historical-thinking/contextualisation-skill-builder"
skill_name: "历史语境化技能构建器"
domain: "historical-thinking"
version: "1.0"
contributor: "Sean Hu"
evidence_strength: "moderate"
evidence_sources:
  - "Wineburg (2007) — Unnatural and essential: the nature of historical thinking"
  - "Wineburg (1998) — Reading Abraham Lincoln: an expert/expert study in historical cognition"
  - "Gottlieb & Wineburg (2012) — Between Veritas and Communitas: epistemic switching in the reading of academic and sacred history"
  - "Reisman (2012) — Reading like a historian: a document-based history curriculum intervention in urban high schools"
  - "Wineburg & Reisman (2015) — Disciplinary literacy in history: a toolkit for digital citizenship"
  - "Wineburg, Smith & Breakstone (2018) — What is learned in college history classes?"
input_schema:
  required:
    - field: "historical_topic"
      type: "string"
      description: "学生正在调查的历史主题、时期或问题"
    - field: "student_level"
      type: "string"
      description: "年龄/年级以及当前语境化的经验水平"
    - field: "current_challenge"
      type: "string"
      description: "学生目前在语境化时做了什么或没做到什么——表明语境化能力尚未发展起来的可观察行为"
  optional:
    - field: "source_type"
      type: "string"
      description: "学生正在使用的历史史料类型"
    - field: "available_documents"
      type: "string"
      description: "学生将使用的具体文献描述"
    - field: "background_knowledge"
      type: "string"
      description: "学生对该时期已经掌握的背景知识——至关重要，因为语境化需要有知识可供调动，缺口可能在于知识而非技能"
    - field: "curriculum_framework"
      type: "string"
      description: "来自上下文引擎：正在使用的相关课程标准或历史思维框架"
    - field: "prior_instruction"
      type: "string"
      description: "学生已经接受过的语境化教学"
output_schema:
  type: "object"
  fields:
    - field: "contextualisation_progression"
      type: "object"
      description: "语境化在初学、发展中和熟练水平上的表现——附区分“知道背景信息”与“将其用于改变对文献解读”的可观察指标"
    - field: "explicit_instruction_sequence"
      type: "object"
      description: "教授语境化的三段式序列，针对该技能相比溯源与精读更高的复杂性而设计——包含使“将文献与历史时刻相连”这一隐形心理动作显性化并可练习的策略"
    - field: "contextualisation_prompts"
      type: "array"
      description: "引导学生将文献连接到其历史时刻的提示语——按发展水平与史料类型校准"
    - field: "common_failure_patterns"
      type: "array"
      description: "学生未能语境化的具体模式，包括“拥有背景知识”与“在阅读文献时激活它”之间的关键区分"
    - field: "assessment_indicators"
      type: "object"
      description: "学生正在进行语境化的可观察迹象——讨论中听什么、书面作业中看什么"
chains_well_with:
  - "sourcing-skill-builder"
  - "close-reading-skill-builder"
  - "corroboration-skill-builder"
  - "historical-thinking-strategy-modelling-guide"
  - "document-based-lesson-designer"
  - "historical-thinking-assessment-designer"
  - "lesson-opening-designer"
teacher_time: "4 分钟"
tags: ["contextualisation", "historical-thinking", "disciplinary-literacy", "document-analysis", "chronological-reasoning", "DIG"]
---

# 历史语境化技能构建器

## 本技能的作用

设计针对性教学以培养学生的历史语境化（contextualisation）实践——推理文献创作时的时间、空间和社会处境如何塑造其内容、意义与可靠性。输出包括发展进阶序列、针对语境化更高复杂性而调整的显性教学序列、引导学生将文献与其历史时刻相连的提示语、常见失败模式以及评估指标。

语境化在性质上不同于溯源和精读，且更难教授。Reisman (2012) 在其为期六个月的干预研究中发现，溯源和精读取得了显著处理效应，但语境化（和互证）没有。她将此归因于语境化的抽象性：溯源涉及一个离散动作（查看出处注），精读涉及关注具体文本特征（用词选择），而语境化需要一次推理飞跃——将文献连接到“文献本身之中并不存在”的处境。读者必须把外部知识带入文本，并用它来转化文本的意义。这意味着语境化依赖两个其他技能所不依赖的条件：拥有相关背景知识“以及”在阅读时激活它的倾向。

Wineburg (2007) 通过哈里森总统宣言的案例展示了这种双重条件。一名学生和小学教师都拥有关于 19 世纪 90 年代移民潮的知识——美国课程中反复教授移民史。但当他们阅读哈里森 1892 年的哥伦布日宣言时，这项知识并未被激活。哥伦布这一认知节点压倒了它。相比之下，历史学博士生在几秒钟内就将该文献与 1892 年的语境联系起来——不是因为他们更了解哥伦布，而是因为他们具备学科思维倾向，会追问：“1892 年发生了什么，使这份文献成为必要？” 这就是 Wineburg 所说的“拥有知识”与“调动知识”之间的区别。

本技能的证据强度评级为“moderate（中等）”而非“strong（强）”，因为尽管研究清楚表明语境化是专家历史阅读的核心组成部分，但关于如何有效教授它的实证证据比溯源更薄弱。Reisman (2012) 提出语境化可能需要更多全班讨论以及对语境与文献间推理联结的更明确示范——但这是对零结果的事后解释，而非经过检验的教学设计。

## 循证基础

Wineburg (2007) 最清晰地展示了实践中的语境化是什么样子。面对哈里森 1892 年关于哥伦布的宣言，博士生 Matt 的反应是："Okay it's 1892... Benjamin Harrison. The 1890s, the beginning of the Progressive Era, end of the century, closing of the frontier, Frederick Jackson Turner, you've got the Columbian Exposition coming up the following year. Biggest wave of immigration in US history. That's it." 不到一分钟，Matt 就将该文献连接到了五个不同的语境参照点，并提出了一个假设：这份宣言关乎移民政治，而非哥伦布。而阅读同一份文献的 17 岁学生则把时间花在评价哥伦布的品格上。两位读者都认真投入了文献；只有一位进行了语境化。

Gottlieb & Wineburg (2012) 发现，历史学家使用语境化的频率显著高于非历史学家（Z = 2.84, p = .005），且其语境化的质性特征也截然不同。非历史学家能隐约觉得文献哪里不对（一位牧师注意到感恩节画作里的每个人“看起来都干净且衣食无忧”），但缺乏具体知识来说明原因。历史学家则调动了事实纠偏与时代错置（anachronism）等学科概念。八位历史学家中有六位将华盛顿的感恩节宣言解读为启蒙运动自然神论（deism）的证据，而全部八位神职人员和科学家都将同样的语言解读为宗教虔诚的证明。这表明语境化不仅仅是增添背景信息——它改变了意义。

Wineburg & Reisman (2015) 主张，语境化是理解的构成部分，而非附加补充："For the novice reader, the available information begins and ends with the text. For historical readers, the text becomes a portal to another time." 他们批评了将历史文献简化为“信息性文本”并指示教师回避语境问题（称其为“非文本依赖”）的共同核心标准（Common Core）实施做法。他们指出，把林肯的《葛底斯堡演说》与美国内战剥离开来，文字就会变得毫无意义。

Wineburg, Smith & Breakstone (2018) 提供了反面证据：94% 的大学一年级学生忽略了 1621 年事件与 1932 年描绘该事件的画作之间长达 300 年的时间跨度；84% 的高年级学生未能识别出一个 1859 年的事实无法解释为什么有人在 1936 年写了一部剧本。学生始终为了内容而非语境阅读——关注文献说了什么，却不关注其创作时的处境。连历史专业学生也表现出这一模式，说明仅仅上过历史课并不会自动培养出语境化能力。

Reisman (2012) 发现，尽管溯源和精读显示出显著处理效应，语境化却未显示出显著处理效应。她的解释是：溯源和精读是可在单份文献上练习的“离散、具体的动作”，而语境化要求在文献与文献自身之外的知识之间建立联系。实验班课堂中全班讨论的普遍缺失，可能限制了学生练习这一更复杂、更具对话性技能的机会。

## 输入模式

教师必须提供：
- **Historical topic（历史主题）：** *例如："The Gettysburg Address" / "Columbus Day proclamation of 1892" / "Propaganda posters from World War I" / "The Declaration of the Rights of Man (1789)"*
- **Student level（学生水平）：** *例如："Year 8, have studied the period but don't connect background knowledge to document analysis" / "Year 11, can source and close-read but don't spontaneously ask what was happening at the time a document was created"*
- **Current challenge（当前挑战）：** *例如："They know the background but don't use it when reading documents" / "They treat documents as timeless — they don't consider that the same words meant different things in different periods" / "They can answer 'when was this written?' but can't answer 'why does it matter that it was written THEN?'"*

可选：
- **Background knowledge（背景知识）：** 学生对该时期已经知道的内容——对于诊断缺口是“知识”还是“调动”至关重要
- **Source type, available documents, curriculum framework, prior instruction** —— 同溯源技能构建器

## Prompt

```
You are an expert in historical thinking pedagogy, with deep knowledge of Wineburg's (2007) demonstration that contextualisation requires both possession of background knowledge AND the disposition to activate it during reading, Gottlieb and Wineburg's (2012) finding that contextualisation transforms meaning rather than merely adding background information, and Reisman's (2012) finding that contextualisation did NOT show significant treatment effects in a six-month intervention — suggesting it requires different instructional strategies than sourcing or close reading.

Your task is to design targeted contextualisation instruction for:

**Historical topic:** {{historical_topic}}
**Student level:** {{student_level}}
**Current challenge:** {{current_challenge}}

The following optional context may or may not be provided. Use whatever is available.

**Source type:** {{source_type}}
**Available documents:** {{available_documents}}
**Background knowledge:** {{background_knowledge}} — if provided, this is critical. If students already know the relevant context, the problem is DEPLOYMENT, not knowledge — and instruction should focus on activating existing knowledge during reading. If students lack the background, the problem is partly a knowledge gap and instruction must address both knowledge and deployment.
**Curriculum framework:** {{curriculum_framework}}
**Prior instruction:** {{prior_instruction}}

Design the following:

1. **Contextualisation progression:** What contextualisation looks like at three levels:
   - **Novice:** The student reads the document as if it could have been written at any time. They engage with the content in isolation from historical circumstances. Describe what this looks like with observable indicators.
   - **Developing:** The student can state relevant background information when prompted ("What was happening in 1892?") but does not spontaneously connect it to the document. Context and document remain in separate compartments. Describe what this disconnection looks like.
   - **Proficient:** The student spontaneously connects the document to its historical moment, using context to transform their interpretation of the document's meaning, purpose, or reliability. Describe what this integration looks like — the specific reasoning moves a proficient student makes.

   IMPORTANT: The critical distinction here is between POSSESSING context and DEPLOYING it (Wineburg, 2007). A student who can recite facts about the 1890s but reads Harrison's proclamation as a statement about Columbus possesses knowledge but does not deploy it. Make this distinction concrete and observable.

2. **Explicit instruction sequence:** This must differ from the sourcing and close reading sequences because contextualisation involves an inferential leap that is harder to model with concrete actions. Design a sequence that makes the invisible mental move of "connecting document to context" visible:
   - **I DO:** A think-aloud script (150–200 words) showing the teacher modelling the contextualisation move — reading the document's date and immediately reaching for what they know about that moment, connecting specific features of the document to specific historical circumstances, and showing how context changes the interpretation. The think-aloud should make the INFERENCE explicit: "Because I know X was happening in [year], this document probably means Y rather than Z."
   - **WE DO:** A guided practice activity that scaffolds the inferential leap. Consider using a structured bridge — e.g., students first list what they know about the period (activating knowledge), then read the document, then explicitly connect items from their list to specific features of the document. The bridge makes the connection step deliberate rather than implicit.
   - **YOU DO:** Independent practice with monitoring criteria.

3. **Contextualisation prompts:** Prompts that guide students toward the contextualisation move, calibrated to the source type. For each prompt, include the prompt itself, why it matters, and a sentence starter. Prompts should push students beyond "when was this written?" toward "why does it matter that it was written THEN?"

4. **Common failure patterns:** 3–4 patterns, including the knowledge-possession-without-deployment pattern that is distinctive to contextualisation.

5. **Assessment indicators:** What to listen for, what to look for, and the key test.

Return your output in this exact format:

## Contextualisation Instruction Plan

**Topic:** [Historical topic]
**Students:** [Level and current challenge]
**Source type:** [Type of source]

### Contextualisation Progression

**Novice — reading without context:**
[Observable indicators]

**Developing — knowing context but not deploying it:**
[Observable indicators]

**Proficient — deploying context to transform interpretation:**
[Observable indicators]

### Explicit Instruction Sequence

**I DO — Teacher Think-Aloud**
[Script, 150–200 words]

**WE DO — Guided Practice**
[Activity with scaffolded bridge between context knowledge and document interpretation]

**YOU DO — Independent Practice**
[What to monitor for]

### Contextualisation Prompts

[Prompts with rationale and sentence starters]

### Common Failure Patterns

[3–4 patterns]

### Assessment Indicators

**In discussion:** [What to listen for]
**In written work:** [What to look for]
**The key test:** [Single most reliable indicator]

**Self-check before returning output:** Verify that (a) the progression distinguishes between possessing background knowledge and deploying it during reading, (b) the think-aloud makes the inferential leap from context to interpretation EXPLICIT, (c) the guided practice includes a structured bridge that scaffolds the connection step, (d) the failure patterns address the knowledge-vs-deployment distinction, and (e) the instruction design accounts for the finding that contextualisation requires different strategies than sourcing and close reading.
```

## 示例输出

**场景：** *Historical topic: "Columbus Day proclamation of 1892" / Student level: "Year 10, have studied 1890s immigration and the Progressive Era but don't connect this knowledge to document analysis" / Current challenge: "When they read Harrison's proclamation, they focus entirely on Columbus — whether he was a hero or a villain — and don't consider why a president in 1892 would create this holiday" / Background knowledge: "Students have studied the closing of the frontier, mass immigration from Southern and Eastern Europe, nativism, and the Columbian Exposition"*

---

## 语境化教学计划

**主题：** 1892 年哥伦布日宣言
**学生：** 十年级，了解 19 世纪 90 年代背景，但将其用于评论哥伦布而非进行语境分析
**史料类型：** 政府公告

### 语境化发展进阶

**初学——脱离语境阅读：**
学生阅读哈里森的宣言，并对哥伦布做出回应："He says Columbus was noble but Columbus actually killed people" 或 "I agree that Columbus was brave." 文献触发了关于哥伦布的观点，学生对照自己已有的知识去评判这些观点。1892 年这个年份对他们的阅读毫无影响——这份文献就算写于 1792 年或 1992 年，他们的反应也会一模一样。如果被问到 "Why was this written in 1892?"，他们会感到困惑——这个问题对他们来说毫无意义，因为他们从未考虑过文献是特定历史时刻的产物。

**发展中——知道语境但不调动它：**
在提示下，学生能回忆起 19 世纪 90 年代发生了什么：移民潮、排外主义、边疆结束、哥伦布世博会。但这些知识与文献处于彼此隔离的心理隔间里。阅读宣言时，他们只与哥伦布互动；被问及 19 世纪 90 年代时，他们能背出关于移民的事实。两者并未相连。如果直接问 "Could the 1890s immigration wave have anything to do with this proclamation?"，他们可能会开始看到联系——但他们不会主动建立这种联系。

**熟练——调动语境以转化解读：**
学生读到 "1892" 时立即将其与已知联系起来：美国历史上最大规模的移民潮，主要来自南欧和东欧——被新教主流群体视为威胁的天主教徒和犹太裔移民。他们提出假设：将哥伦布（一位意大利天主教徒）宣布为国家英雄，可能是为了扩大“美国人”的定义以接纳这些新移民的策略性举措。这份文献不再是关于 1492 年的陈述，而成为了 1892 年的一次政治行动。语境彻底转化了解读。

### 显性教学序列

**我做（I DO）——教师出声思维**

*教师投影展示日期清晰可见的宣言：*

"Before I engage with what this says about Columbus, I'm going to look at the date. 1892. What do I know about 1892? Immediately I'm thinking: this is the height of mass immigration. Millions of people arriving from Italy, Poland, Russia — Catholic and Jewish immigrants that many Americans saw as a threat. There's a huge nativist backlash.

Now — Columbus was Italian. And Catholic. So a president declaring Columbus a national hero in 1892 is not just making a statement about the past. He's making a statement about the present. He's saying: Italians — Catholics — are part of the American story. They've been part of it from the very beginning.

That changes EVERYTHING about how I read this document. When Harrison calls Columbus's journey 'one of the most notable achievements of human will and effort,' I'm not hearing a history lesson about 1492. I'm hearing a political argument about 1892: these new immigrants are heirs to a noble tradition, not foreign invaders. The document is about NOW, not then."

**我们做（WE DO）——引导练习**

两步架桥活动：

*第 1 步——激活知识：* 在看到文献之前，学生结对花三分钟在图形组织器上列出他们所知道的关于 19 世纪 90 年代的一切（移民、排外主义、边疆结束、哥伦布世博会、进步主义时代）。这激活了知识。

*第 2 步——建立联结：* 学生拿到宣言。他们的任务不是完整分析它，而是完成一个具体句子："This document was written in 1892, and knowing what I know about the 1890s, I think the real purpose of this proclamation was ___ because ___." 他们必须在 19 世纪 90 年代清单中的至少一项与文献中的至少一处具体特征之间画出明确的箭头连线。

教师巡视。核心纠偏：
- 如果学生写哥伦布的品格："Your sentence should start with 1892, not with Columbus. What was happening in 1892 that makes this document make sense?"
- 如果学生做出模糊联结（"It was written during a time of change"）："WHICH change? Be specific. Pick one thing from your 1890s list and connect it to one specific thing in the document."

**你做（YOU DO）——独立练习**

学生拿到一份来自不同时期的新文献（例如一张第一次世界大战征兵海报）。在没有两步架桥支架的情况下，他们撰写一段语境化段落："This document was created in [year]. At this time, [relevant context]. This context helps explain why the document [specific feature], because [connection]."

教师监控学生是自发调动语境，还是仍需提示。

### 语境化提示语

1. **这份文献创作时正在发生什么，这可能如何塑造了作者所写的内容？**
   *为何重要：* 这是核心的语境化动作——将文献与其历史时刻相连。
   *句首提示：* "At the time this was written, ___ was happening, which helps explain why the author..."

2. **如果这份文献早写 20 年或晚写 20 年，会有何不同？如何不同、为什么？**
   *为何重要：* 促使学生将文献视为受时间制约的产物，而非超越时代的文本。如果回答是“没有区别，都一样”，说明学生没有进行语境化。
   *句首提示：* "If this had been written in [different year], it would probably be different because..."

3. **作者是在回应什么问题或局势？**
   *为何重要：* 文献不是在真空中产生的，而是对处境的回应。该提示推动学生识别使文献成为必要的具体处境。
   *句首提示：* "The author was probably responding to ___, which is why they..."

4. **这份文献中的词语在当时是什么意思——这与我们今天对它们的理解有何不同？**
   *为何重要：* Gottlieb & Wineburg (2012) 表明，历史学家能识别历史语言（华盛顿的自然神论措辞），而非历史学家则会强加当代含义。词义随时间演变，语境化也包含语言意识。
   *句首提示：* "When the author wrote '___,' they probably meant ___, which is different from how we'd understand it today because..."

### 常见失败模式

**1. “拥有知识但未调动”——知道语境却不加连接**
*表现：* 学生在测验中能答对“19 世纪 90 年代发生了什么？”，但阅读 1892 年文献时却只字不提 19 世纪 90 年代。语境知识与文献分析存储在彼此隔离的隔间里。
*原因：* 阅读习惯把文献当作自足的文本。学生尚未学会把“当时发生了什么？”当作阅读前的反射动作，就像他们可能学会了先看文献出处一样。语境化需要一次溯源所不需要的推理飞跃。
*应对：* 使用两步架桥：在发文献“之前”先激活语境知识，然后要求在语境条目与文献特征之间写下明确联结。久而久之，学生内化了这座桥梁，便不再需要支架。

**2. “当下主义（Presentism）”——用当代价值观阅读历史文献**
*表现：* 学生用当代标准评判哈里森对哥伦布的赞美："He shouldn't have celebrated Columbus because Columbus committed genocide." 学生将 2024 年的道德标准套用于 1892 年的文献，而未考虑这些话对当时原始受众意味着什么。
*原因：* 这就是激活扩散效应（Wineburg, 2007）。“哥伦布”节点触发了学生关于哥伦布历史重估的全部已知信息，压倒了对 1892 年处境的关注。
*应对：* 肯定学生的道德立场，但随后引导："You're right that we see Columbus differently today. But the question isn't whether WE think Columbus was a hero — it's why HARRISON, in 1892, thought celebrating Columbus was politically useful. What was happening in 1892 that made this make sense to people at the time?"

**3. “把语境当作装饰”——堆砌背景信息却不加运用**
*表现：* 学生先写一段关于时代背景的介绍，再另写一段分析文献。两段话互不相连。语境只是铺垫背景，而非分析工具。
*原因：* 学生以为“语境”的意思就是“写写历史背景”，尚未学会语境应当“改变”他们解读文献的方式。
*应对：* 要求在连接处必须使用 "because" 或 "which explains why"。学生必须写出一句明确将语境事实与文献具体特征相连的话："Because mass immigration was creating anti-Catholic sentiment in the 1890s, Harrison's celebration of Columbus — an Italian Catholic — was a political act, not just a historical commemoration."

### 评估指标

**讨论中：** 倾听学生在讨论文献前或讨论中是否自发询问时代背景："When was this written? What was going on then?" 更进阶的表现：倾听学生是否无需提示就将文献与同时代事件相连——"This reminds me of what was happening with immigration at the time."

**书面作业中：** 寻找利用语境“改变”解读（而不仅仅是铺垫场景）的句子。检验标准：如果删掉语境段，分析段是否毫无变化？如果答案是肯定的，说明学生在装饰，而非语境化；如果删掉语境段会导致分析坍塌，说明学生真正调动了语境。

**核心检验：** 给学生一份来自他们已学时期、日期可见但没有提示“请进行语境化”的文献。他们会自发将文献与对该时期的了解联系起来，还是孤立地阅读内容？学生在有提示（"What was happening in 1892?"）与无提示时的表现差距，正是衡量语境化在多大程度上已从课堂练习内化为思维倾向的尺度。

---

## 已知局限性

1. **在“像历史学家一样阅读”课程的基础有效性研究（Reisman, 2012）中，语境化未显示出显著处理效应。** 本技能中的教学策略借鉴了 Reisman 的事后解释以及 Wineburg (2007) 与 Gottlieb & Wineburg (2012) 记录的专家阅读行为，但尚未作为独立干预措施经过实验检验。因此证据强度评级为“moderate（中等）”。

2. **语境化对背景知识的依赖程度远高于溯源和精读。** 如果学生对 19 世纪 90 年代一无所知，就不可能语境化一份 1890 年代的文献。这意味着语境化教学必须以内容教学为先导或与之配对。本技能在解决“调动问题”（学生知道语境但不用）方面比解决“知识缺口问题”（学生完全缺乏语境）更有效。教师在选择教学策略前，应先诊断学生面临的是哪类问题。

3. **语境化与当下主义之间的界限在教学上非常敏感。** 教导学生“在其时代背景下”理解一份文献，可能被误解为要求他们搁置道德判断——接受奴隶制在当时是可以接受的，因为“那时的人想法不同”。这并非语境化的含义。语境化意味着理解过去的人们“为什么”那样行动和思考，而不是赞同它。教师应明确点出这一区分，避免让学生误以为历史理解要求道德相对主义。
