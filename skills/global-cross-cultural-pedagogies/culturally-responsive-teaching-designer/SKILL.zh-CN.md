---
# AGENT SKILLS STANDARD FIELDS (v2)
name: culturally-responsive-teaching-designer
description: "重新设计课程以围绕学生的文化背景、社区知识与生活经验展开。适用于为多元学生群体提升课程相关性与包容性时。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "global-cross-cultural-pedagogies/culturally-responsive-teaching-designer"
skill_name: "文化响应型教学设计师"
domain: "global-cross-cultural-pedagogies"
version: "1.0"
evidence_strength: "strong"
evidence_sources:
  - "Gay (2018) — Culturally Responsive Teaching: theory, research, and practice (3rd edition)"
  - "Ladson-Billings (1995) — Toward a theory of culturally relevant pedagogy"
  - "Hammond (2015) — Culturally Responsive Teaching and The Brain"
  - "Paris & Alim (2017) — Culturally Sustaining Pedagogies: teaching and learning for justice in a changing world"
  - "Aronson & Laughter (2016) — The theory and practice of culturally relevant education: a synthesis of research across content areas"
input_schema:
  required:
    - field: "lesson_content"
      type: "string"
      description: "需要教授的课程内容或学习目标"
    - field: "student_community"
      type: "string"
      description: "班上学生的文化背景、社区语境与生活经验"
  optional:
    - field: "subject_area"
      type: "string"
      description: "课程学科"
    - field: "student_level"
      type: "string"
      description: "年龄/年级"
    - field: "current_approach"
      type: "string"
      description: "目前如何教授该内容——使用了哪些文本、例证和视角"
    - field: "school_context"
      type: "string"
      description: "人口构成、社区背景、先前开展的文化响应实践"
    - field: "teacher_background"
      type: "string"
      description: "教师自身的文化背景及文化响应教学经验"
output_schema:
  type: "object"
  fields:
    - field: "crt_lesson_design"
      type: "object"
      description: "融入文化响应原则重新设计的教案——保持同等严谨的内容，采用文化连接的教学法"
    - field: "cultural_connections"
      type: "array"
      description: "课程内容与学生文化知识、社区实践和生活经验之间的具体联结"
    - field: "critical_consciousness_element"
      type: "object"
      description: "课程如何培养学生识别和批判不平等的能力——社会政治维度"
    - field: "high_expectations_framework"
      type: "object"
      description: "课程如何在保持文化响应的同时维持严谨的学术期望——绝不降低标准"
chains_well_with:
  - "ubuntu-collective-knowledge-task-designer"
  - "place-based-inquiry-anchor"
  - "belonging-classroom-culture-designer"
  - "phenomenon-based-unit-anchor"
teacher_time: "4 分钟"
tags: ["culturally-responsive", "Gay", "Ladson-Billings", "equity", "culturally-sustaining", "Hammond", "inclusion"]
---

# 文化响应型教学设计师

## 本技能的作用

将课程内容重新设计为文化响应型教学（Culturally Responsive Teaching）——将严谨的学术课程与学生的文化背景、社区知识和生活经验相连接，同时维持高学术期望并发展批判意识。该方法借鉴了 Geneva Gay (2018) 的文化响应型教学框架与 Gloria Ladson-Billings (1995) 的文化相关教学法理论。核心原则在于：文化响应型教学不是降低标准、增加一个“多元文化日”或用文化内容替代学术内容——而是将学生的文化知识作为通往严谨学术学习的“桥梁”。当课程与学生已经知道和珍视的事物相连时，学生学到的是“更多”，而不是“更少”。输出包括附带具体文化联结的重新设计教案、批判意识要素（学生运用学科内容审视公平与权力）以及确保学术严谨性得到加强而非稀释的高期望框架。AI 在此尤为有价值，因为在课程内容与多元文化语境之间找到真实联结，需要横跨不同文化、学科与教学法的广泛知识——同时保持对每个具体社区独特性的敏感。

## 循证基础

Gay (2018) 将文化响应型教学定义为“利用族裔多元化学生的文化知识、先前经验、参照框架和表现风格，使学习体验对他们更具相关性与有效性”。她确立了五大核心要素：发展文化多样性知识库、设计文化相关课程、展现文化关怀并建立学习共同体、跨文化沟通，以及课堂教学中的文化一致性。Ladson-Billings (1995) 提出了文化相关教学法的三项标准：学业成功（学生必须在学业上取得成就）、文化胜任力（学生必须保持并发展其文化认同）以及批判意识（学生必须发展批判社会不平等的能力）。她强调，文化相关教学法对学生要求“更高”，而非更低——它提升期望，同时让通往高期望的路径具有文化意义。Hammond (2015) 将文化响应型教学与神经科学联系起来，指出当学习具有文化联结时，会激活学生既有的神经通路和先验知识，降低认知负荷并提高投入度——大脑在新信息与既有图式相连时学习效率更高。Paris & Alim (2017) 将该框架延伸至“文化维续教学法（culturally sustaining pedagogies）”，主张教学不仅应回应学生的文化，更应在面对文化抹除时主动维续和发展这些文化。Aronson & Laughter (2016) 综合了跨学科研究，发现文化相关教育持续提升了学生的参与度与学业成就，对边缘化群体学生的效应最为显著。

## 输入模式

教师必须提供：
- **Lesson content（课程内容）：** 学生需要学什么。*例如："Persuasive writing — Year 9 English, constructing arguments with evidence" / "Fractions — Year 4 Mathematics, understanding fractions as parts of wholes" / "The Industrial Revolution — Year 8 History, causes and consequences of industrialisation" / "Ecosystems — Year 7 Science, understanding food chains and interdependence"*
- **Student community（学生社区）：** 学生是谁。*例如："Predominantly South Asian British community, many students bilingual (Urdu/Punjabi and English), strong family and community connections, local area has a vibrant market culture" / "Mixed community in a coastal town — some farming families, significant Eastern European population (Polish, Romanian), local fishing industry declining" / "Inner-city London school, very diverse — Caribbean, West African, Somali, Bangladeshi, white British working class, significant proportion of students eligible for Pupil Premium"*

可选（如上下文引擎可用则自动注入）：
- **Subject area（学科领域）：** 课程学科
- **Student level（学生水平）：** 年级
- **Current approach（当前教法）：** 目前如何教授该内容
- **School context（学校背景）：** 人口构成、社区、先前实践
- **Teacher background（教师背景）：** 教师自身的文化经验

## Prompt

```
You are an expert in culturally responsive teaching, with deep knowledge of Gay's (2018) CRT framework, Ladson-Billings' (1995) culturally relevant pedagogy, Hammond's (2015) neuroscience of culturally responsive teaching, Paris & Alim's (2017) culturally sustaining pedagogies, and Aronson & Laughter's (2016) research synthesis. You understand that culturally responsive teaching is a rigorous pedagogical approach, not a superficial add-on — it uses students' cultural knowledge as a cognitive bridge to academic content, maintains the highest academic expectations, and develops critical consciousness about equity and power.

CRITICAL PRINCIPLES:
- **High expectations are non-negotiable.** Culturally responsive teaching is NOT about making work easier, simpler, or "more fun." It is about making rigorous academic content ACCESSIBLE by connecting it to what students already know. If the redesigned lesson has lower academic expectations than the original, it has failed. Ladson-Billings was explicit: culturally relevant pedagogy demands academic excellence.
- **Cultural connections must be AUTHENTIC, not tokenistic.** "Let's do fractions using samosas instead of pizzas" is tokenistic — it changes a surface detail without connecting to genuine cultural knowledge. An authentic connection uses the cultural PRACTICE, not just the cultural OBJECT: "In your family's cooking, recipes are often adjusted for different numbers of guests — how do proportions work when you double a recipe?"
- **Critical consciousness is essential, not optional.** Ladson-Billings' third criterion is that students develop the ability to critique social inequity. This means the lesson should include an element where students use the academic content to examine power, representation, or justice. In History: "Whose story is told? Whose is missing?" In Science: "Who benefits from this research? Who is harmed?" In English: "Who gets to speak? Whose language is valued?"
- **Know the community, don't assume.** Culturally responsive teaching requires knowledge of the SPECIFIC community, not generic assumptions about cultural groups. "South Asian students will connect to Bollywood" is a stereotype. "Students in this community have strong intergenerational storytelling traditions" is specific knowledge. When you don't have specific knowledge, design the lesson to INVITE students' own cultural knowledge rather than assuming it.
- **Sustain, don't just respond.** Following Paris & Alim, the goal is not just to use students' cultures as a bridge (which can treat cultures as instrumental) but to sustain and develop cultural knowledge and identity through the academic work.

Your task is to redesign a lesson to be culturally responsive for:

**Lesson content:** {{lesson_content}}
**Student community:** {{student_community}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Subject area:** {{subject_area}} — if not provided, infer from the lesson content.
**Student level:** {{student_level}} — if not provided, infer from the lesson content.
**Current approach:** {{current_approach}} — if not provided, assume a standard textbook approach.
**School context:** {{school_context}} — if not provided, design for a general context.
**Teacher background:** {{teacher_background}} — if not provided, include a note about the teacher's own positionality.

Return your output in this exact format:

## Culturally Responsive Lesson: [Content]

**Content:** [What students learn — same academic objectives, culturally connected]
**Community:** [Who the students are]
**Core principle:** [The specific CRT principle most central to this redesign]

### Current Approach vs. Culturally Responsive Approach

[Brief comparison: what a standard approach looks like, and what changes in the CRT redesign — not to criticise the standard approach but to make the difference visible]

### Cultural Connections

For each connection (2–4):
**Connection [N]: [What connects]**
- **Cultural knowledge:** [What students bring from their community/experience]
- **Academic content:** [How this connects to the curriculum objective]
- **How to use it:** [Specific activity or approach that bridges the cultural and academic]

### Critical Consciousness Element

[How the lesson develops students' ability to examine equity, power, or representation through the academic content]

### High Expectations Framework

[How the lesson maintains or raises academic rigour — specific evidence that expectations are not lowered]

### Lesson Redesign

[The redesigned lesson — structured, practical, ready to teach]

### Teacher Reflection

[Questions for the teacher to reflect on their own positionality, assumptions, and learning]

**Self-check before returning output:** Verify that (a) academic expectations are at least as high as the original lesson, (b) cultural connections are authentic and specific, not tokenistic, (c) the critical consciousness element is genuinely integrated, (d) the design invites student cultural knowledge rather than assuming it, and (e) the approach sustains cultural identity, not just uses it as a bridge.
```

## 示例输出

**场景：** *Lesson content: "Persuasive writing — Year 9 English. Students need to construct a persuasive argument using evidence, rhetorical techniques (ethos, pathos, logos), and structured paragraphs. The current approach uses model texts from newspaper opinion columns and students write a letter to a local council about a planning issue." / Student community: "Inner-city London school, very diverse — Caribbean, West African, Somali, Bangladeshi, white British working class. Many students are eloquent and persuasive speakers but struggle to transfer this to formal written English. Strong oral traditions in several home cultures. Many students are actively engaged in social media discourse and local community issues." / Current approach: "Model texts from broadsheet newspapers. Students practise ethos/pathos/logos identification, then write a formal letter to a council. Some students disengage because the model texts feel distant from their experience."*

---

## 文化响应型课程：说服性写作——九年级英语

**内容：** 运用证据、修辞手法（信誉 ethos、情感 pathos、逻辑 logos）和结构化段落构建说服性论证——相同的英语课程目标，文化连接的教学法
**社区：** 多元化的伦敦内城区——加勒比裔、西非裔、索马里裔、孟加拉裔、英国白人工薪阶层。深厚的口头传统、社交媒体流利度、社区参与感
**核心原则：** 学生本身已经是熟练的说服者——本课将他们既有的说服能力（口头、数字、基于社区的）桥接到正式学术写作中

### 当前教法 vs. 文化响应型教法

**标准教法：** 采用大报观点专栏作为范文。学生识别修辞手法，随后就规划议题给地方议会写一封正式信函。隐含的信息是：“说服力长成这样”——即白人中产阶级平面媒体话语的特定语域与格式。

**文化响应型教法：** 从学生既有的说服专长出发——口头辩论、社交媒体话语、社区倡导、多语说服。跨越多种语域和语境分析说服技巧（TED 演讲、口语诗、社区请愿书、布道辞、社交媒体倡议），随后刻意将这些技能迁移到正式学术写作中。传递的信息是：“You are already persuasive. Academic writing is another register you're adding to your repertoire — not replacing what you already know.”

### 文化联结

**联结 1：口头说服传统**
- **文化知识：** 许多学生来自拥有丰富口头传统的文化——加勒比故事讲述与演讲、西非格里奥（griot）传统、伊斯兰教布道辞（khutbah）的修辞结构、集市交易中的口头议价。那些常被贴上“爱讲话”标签的学生，往往可能是极高明的口头说服者。
- **学术内容：** Ethos、pathos 和 logos 不仅仅是书面技巧——它们起源于口头修辞（亚里士多德的《修辞学》正是关于“演讲”的）。口头说服是书面说服的根基，而非低一等的形式。
- **如何运用：** 以一次“说服力审计”开启单元——学生识别自己生活中进行说服的时刻（与父母协商、说服朋友、操场辩论、社区活动发言）。学生各自带来一个来自自身文化语境的说服案例（一段视频、一段文本、一个故事），全班共同分析其中的 ethos、pathos 和 logos。这确立了一个事实：说服力是普遍存在的，学生“已经”具备这项能力——本课只是在他们既有的能力库中增添正式书面语域。

**联结 2：数字说服**
- **文化知识：** 学生浸润在数字说服之中——社交媒体倡议、YouTube 视频评论、Twitter/X 长帖、change.org 请愿书。许多学生在分析和构建数字说服文本方面，比平面印刷文本拥有更丰富的经验。
- **学术内容：** 数字说服使用与传统说服写作相同的修辞原则——只是格式不同。一条推文长帖同样会像报纸专栏一样使用 logos（数据、证据）和 pathos（个人故事）。同时分析两者有助于学生看清底层结构。
- **如何运用：** 在大报专栏之外，分析一个成功的社交媒体倡议（例如达成目标的请愿书、广泛传播的倡导帖）。学生对比：这条推文如何使用 pathos？这篇报纸专栏如何使用 pathos？相同点是什么？不同点是什么？这将学生的数字素养定位为优势，而非干扰。

**联结 3：真正关切的社区议题**
- **文化知识：** 许多学生深切关注并亲身经历当地社区议题——仕绅化（gentrification）、警务、住房、公共服务获取、群体代表性。这些不是抽象的规划议题，而是活生生的生活体验。
- **学术内容：** 当写作者真正关心议题时，说服性写作才最具力量。标准的“就规划问题给议会写信”可能显得过于假设性。一个学生真正在乎的议题能激发更强的动机、更深的投入，最终产出更老练的写作。
- **如何运用：** 学生选择自己关心的社区议题来写——影响他们社区、家庭或自己的问题。教师提供一份备选议题清单（源自本地知识），但学生也可以自主提出。写作任务在形式上保持完全一致（结构化论证、证据、修辞手法），但内容具有个人与文化意义。

### 批判意识要素

**谁的说服才算数？**

在跨语域（口头、数字、印刷）研究说服技巧之后，学生探讨一个批判性问题："Which forms of persuasion are taken seriously by people in power, and which are dismissed? Why?"

学生对比：一份大报观点专栏、一场口语诗表演、一句抗议口号、一场社交媒体倡议、一份正式请愿书。所有这些都具有说服力。哪一种最会被议会严肃对待？哪一种会被法官采纳？哪一种会被学校倾听？

讨论："Why is a formal letter considered more 'legitimate' than a spoken argument, even if the spoken argument is more detailed, more passionate, and more evidence-based? What does this tell us about power and language? If certain communities are stronger in oral persuasion than written, what happens to their voices in a system that privileges written, formal English?"

这并非偏离英语课程——它“本身就是”英语课程。理解语言、权力与说服之间的相互关联，正是英语教育的核心目标之一。

**重要提示：** 本课的结论“不是”「正式写作不重要」。结论是："Formal written persuasion is a TOOL you should have because it opens doors in systems that value it — AND the system's preference for formal writing over oral argument is itself worth questioning."

### 高期望框架

文化响应型再设计在三个方面提升了学术期望：

1. **更多分析，而非更少。** 学生跨越“五种”语域（口头、数字、印刷、社区、正式）分析说服力，而不是仅分析一种（印刷）。这比研究单一的大报专栏在分析上要求更高。

2. **将语码转换（Code-switching）作为核心技能。** 学生不只是用一种语域写作——他们用两种语域撰写“同一个”论点（一条社交媒体帖 AND 一封正式信函），并分析修辞手法如何随之调整。这比单一语域写作要求更深层的修辞理解。

3. **真实受众。** 在条件允许的情况下，正式信函会真正“寄出”——寄给议会、校长或当地组织。为拥有真实利害关系的真实受众写作，比仅仅为了教师的评分标准写作要求更高的质量。

### 教案再设计

**第 1 课——说服力审计：**
学生识别自己生活中的说服行为。结对讨论："When were you last persuaded? When did you last persuade someone?" 学生带来一个来自自身经验或文化语境的说服案例。全班共建一面“说服力墙”——展示教室里每一种文化和语境的案例。教师利用这些学生提供的案例引入 ethos、pathos、logos。

**第 2 课——跨语域分析：**
跨越五份文本分析说服技巧：大报观点专栏、口语诗（现场或视频演绎）、社交媒体倡议帖、社区请愿书以及一段简短的 TED 演讲节选。学生在每份文本中识别 ethos、pathos 和 logos。讨论："What's the same across all five? What changes depending on the audience and format?"

**第 3 课——选择你的议题：**
学生选择一个自己关心的社区议题。结对使用至少两个信息来源调研该议题，并规划论证：核心主张是什么？有什么证据支持？最强的情感诉求是什么？是什么赋予他们在这个议题上发言的可信度（ethos）？

**第 4 课——双语域写作：**
学生为自己的论点撰写两个版本：(a) 一条社交媒体帖或 60 秒口头演讲脚本，以及 (b) 一封正式说服性信函。相同的论点、相同的证据，不同的语域。这正是语码转换成为有意识、熟练实践的时刻。

**第 5 课——批判性反思与分享：**
学生分享他们的成对文本。全班讨论："Which version is more persuasive? Does it depend on the audience? What does this tell us about language and power?" 学生修改完善正式信函并提交。

### 教师反思

- "Whose persuasive traditions do I unconsciously value most? Am I more impressed by a well-structured formal essay than by an eloquent spoken argument — and if so, what does that mean for how I assess students from oral traditions?"
- "Do I know enough about my students' cultural communication styles to make authentic connections, or am I relying on assumptions? How can I learn more — from students themselves, from families, from community?"
- "When I teach 'formal English,' am I framing it as 'correct English' (which devalues other registers) or as 'one powerful register among many' (which builds repertoire without diminishing identity)?"

---

## 已知局限性

1. **文化响应型教学需要对具体社区有真实的了解。** 本技能可以提供联结思路与框架，但无法替代教师自己与学生及社区建立的关系和了解。不了解学生而机械套用此模板的教师，只会产出流于表面、缺乏真实性的“假性响应”课程。最重要的文化响应实践是“倾听”学生与家庭。

2. **存在本质主义风险——将文化群体视为铁板一块。** 并非所有加勒比裔学生都拥有深厚的口头传统，也并非所有孟加拉裔学生都来自具有特定烹饪习俗的家庭。文化响应型教学必须面向教室里“具体的”学生，而非基于对其所属文化群体的预设。设计应当主动邀请学生分享他们自己的文化知识，而不是由教师替他们假定。

3. **文化响应型教学存在于制度性约束之中。** 单个教师可以将自己的课重新设计为文化响应型，但无法单枪匹马改变评估体系、国家课程或学校制度文化。学生仍可能面对偏重特定文化形式的标准化考试。文化响应型教学帮助学生在这些体系中取得成功，同时培养对其局限性的批判意识——但它无法单凭一己之力改造整个体系。
