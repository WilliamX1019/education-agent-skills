---
# AGENT SKILLS STANDARD FIELDS (v2)
name: historical-document-set-curator
description: "为基于文献的课程设计文献集——围绕核心问题遴选并排序史料，以制造分析张力。适用于为新课组装史料，或现有文献集只能引出平淡回答时。"
disable-model-invocation: false
user-invocable: true
effort: high

# EXISTING FIELDS
skill_id: "historical-thinking/historical-document-set-curator"
skill_name: "历史文献集策展人"
domain: "historical-thinking"
version: "1.0"
contributor: "Sean Hu"
evidence_strength: "moderate"
evidence_sources:
  - "Reisman (2012) — Reading like a historian: a document-based history curriculum intervention in urban high schools"
  - "Wineburg, Martin & Monte-Sano (2011) — Reading like a historian: teaching literacy in middle and high school history classrooms"
  - "Wineburg & Martin (2004) — Reading and rewriting history"
  - "Wineburg (2007) — Unnatural and essential: the nature of historical thinking"
  - "Caswell (2014) — Seeing yourself in history: community archives and the fight against symbolic annihilation"
  - "Theimer (2012) — Archives in context and as context"
input_schema:
  required:
    - field: "central_question"
      type: "string"
      description: "文献集必须支撑的核心历史问题——学生将使用这些史料调查的探究问题"
    - field: "student_level"
      type: "string"
      description: "年龄/年级、阅读水平以及基于文献探究的经验"
    - field: "target_skills"
      type: "string"
      description: "文献集应当突出的历史思维技能——例如溯源与互证、精读、全部四项"
  optional:
    - field: "existing_sources"
      type: "string"
      description: "教师已经拥有或计划使用的史料——本技能将评估这些史料并提出增删或重排建议"
    - field: "set_size"
      type: "string"
      description: "目标文献数量——单节课通常为 2–5 份，多日单元可更多"
    - field: "source_constraints"
      type: "string"
      description: "实际限制——例如史料必须可在网上免费获取、必须为英文、每份不超过 200 词、必须包含视觉史料"
    - field: "representation_priorities"
      type: "string"
      description: "文献集中应当代表谁的视角——例如确保包含原住民声音、包含多个社会阶层的视角、包含女性视角"
    - field: "historical_topic"
      type: "string"
      description: "课程所处的更广泛主题或单元"
    - field: "curriculum_framework"
      type: "string"
      description: "来自上下文引擎：正在使用的相关课程标准或历史思维框架"
output_schema:
  type: "object"
  fields:
    - field: "document_set_design"
      type: "object"
      description: "附带依据的推荐文献集——选哪些史料、按什么顺序以及每份史料为何值得入选"
    - field: "analytical_tensions"
      type: "array"
      description: "内置于文献集中的具体张力、矛盾或互补之处——学生比对史料时将发现什么"
    - field: "skill_affordances"
      type: "object"
      description: "针对每项目标技能，文献集中哪份文献提供了最佳练习机会及原因"
    - field: "sequencing_rationale"
      type: "string"
      description: "文献为何按当前顺序排列——每一轮阅读为调查增添了什么"
    - field: "representation_audit"
      type: "object"
      description: "文献集中哪些视角在场、哪些缺席，诚实承认空白并提出弥补建议"
chains_well_with:
  - "central-historical-question-evaluator"
  - "historical-source-adapter"
  - "document-based-lesson-designer"
  - "historical-thinking-strategy-modelling-guide"
  - "sourcing-skill-builder"
  - "corroboration-skill-builder"
  - "historical-thinking-assessment-designer"
teacher_time: "5 分钟"
tags: ["document-sets", "historical-thinking", "primary-sources", "source-selection", "lesson-design", "corroboration", "representation", "DIG"]
---

# 历史文献集策展人

## 本技能的作用

为一节基于文献的历史课设计文献集——推荐纳入哪些史料、如何排序以及每份史料为何值得在文献集中占有一席之地。输出包括附带依据的文献集设计、内置于文献集中的分析张力、各史料对不同历史思维技能的支撑映射、排序依据以及识别在场与缺席视角的代表性审计。

文献集不是围绕某主题随便凑在一起的史料集合，而是一个经过精心设计的证据环境，旨在围绕核心问题制造富有成效的分析张力。区别在于：五份关于一战的文献只是给学生提供了阅读信息；而五份相互矛盾、彼此补充又互相复杂化的策展文献，则是给了学生一个需要解决的问题。文献集的质量决定了学生是进行真正的互证（相互权衡记述），还是流水账式概括（读完一份再读下一份，彼此毫不相连）。

“像历史学家一样阅读”课程（Reisman, 2012; Wineburg, Martin & Monte-Sano, 2011）每节课使用 2–5 份文献，依据特定的分析属性遴选：记述之间的矛盾、视角或目的的差异、一手证据与既有叙事之间的张力。宝嘉康蒂一课将史密斯两份自相矛盾的记述与四位从相同证据得出不同结论的历史学家配对——制造了层层嵌套的分析张力，使互证不仅成为可能，而且成为必需。

本技能还回应了 Caswell (2014) 提出的代表性问题：谁的历史被记录了、谁的历史缺席了，以及这些缺席对学生能学到什么有何影响。一份仅包含英语作者史料的早期美洲殖民文献集，不仅限制了视角——它在结构上就阻止了学生练习某些分析动作（如果所有视角共享相同的文化预设，学生就无法跨越真正不同的观点进行互证）。因此本技能包含一份代表性审计，诚实地指明这些空白。

## 循证基础

Reisman (2012) 在“像历史学家一样阅读”课程中每节课使用 2–5 份一手史料组成文献集。每节课的文献都经过遴选，以制造需要调查的核心张力。溯源和精读取得显著处理效应（而互证未取得）表明文献集设计至关重要：史料必须为目标技能创造施展空间。Reisman 将互证的零结果部分归因于全班讨论的缺失，但文献集设计同样起作用——互证需要真正彼此形成张力的史料，而不仅仅是说不同内容的史料。

Wineburg, Martin & Monte-Sano (2011) 为其文献集设计提供了详细依据。宝嘉康蒂一章在三轮中使用了六份史料：第 1 轮（史密斯的两份记述）制造基础矛盾；第 2 轮（Adams 与 Lemay）展示历史学家对矛盾含义的分歧；第 3 轮（Lewis 与 Barbour）增添进一步阐释复杂性。每一轮都在不让太多文献同时压垮学生的情况下深化调查。这种递进架构——先矛盾、再竞争性阐释、再进一步复杂化——是一项有意识的设计原则，而非巧合。

Wineburg & Martin (2004) 证明了史料遴选塑造了学生能发现什么。宝嘉康蒂单元从迪士尼版本开始激活先验知识，然后通过一手史料比对将其拆解。文献排序旨在制造认知失调：学生以为自己知道的东西（来自迪士尼）被史料揭示的内容动摇了。这一排序原则——从熟悉出发，再将其复杂化——是有效文献集设计的核心。

Caswell (2014) 指出，档案缺席构成了“象征性湮灭（symbolic annihilation）”——当一个社群的历史未被保存时，该社群就在历史记录中被隐形了。对文献集设计而言，这意味着可用的史料池并非中立。一份关于南亚裔美国人历史的文献集需要像 SAADA 那样的社区档案工作；没有这些，课程就无米可炊。教师应当意识到，某些主题的史料池比其他主题更丰富，而档案中的缺席本身就具有历史意义。

Theimer (2012) 强调，史料如何被收集、整理和呈现，塑造了什么样的历史思维成为可能。一份脱离其档案语境的史料——被剥离了关于谁收集了它、它如何被保存以及周围还有什么其他材料的信息——就失去了溯源和语境化所依赖的上下文信息。文献集应尽可能保留出处溯源信息。

## 输入模式

教师必须提供：
- **Central question（核心问题）：** 探究问题。*例如："Did Pocahontas rescue John Smith?" / "Who was most to blame for World War I?" / "Was the dropping of the atomic bomb justified?" / "How did enslaved people resist the institution of slavery?"*
- **Student level（学生水平）：** *例如："Year 8, second term of document-based work" / "Year 11 IB History, experienced with multi-document analysis" / "Year 7, first document-based lesson — need simple, short sources"*
- **Target skills（目标技能）：** *例如："Sourcing and corroboration — students need to compare conflicting accounts" / "Close reading — students need to analyse language in speeches" / "All four skills — this is a culminating lesson"*

可选：
- **Existing sources（现有史料）：** 教师已有的史料——用于评估与补充
- **Set size（文献集规模）：** 目标文献数量
- **Source constraints（史料限制）：** 可用史料的实际限制
- **Representation priorities（代表性优先级）：** 需要纳入谁的视角
- **Historical topic, curriculum framework** —— 用于语境对齐

## Prompt

```
You are an expert in designing document sets for document-based history lessons, with deep knowledge of the Reading Like a Historian curriculum's approach to source selection (Reisman, 2012; Wineburg, Martin & Monte-Sano, 2011), the role of analytical tension in driving genuine historical inquiry, and the representation concerns raised by Caswell (2014) about whose histories are documented and whose are absent.

You understand that a document set is not a collection of sources on a topic but a designed evidentiary environment that creates productive analytical tension around a central question. Each document must earn its place by contributing something that the other documents do not — a contradicting perspective, a different type of evidence, a complicating detail, or a voice that would otherwise be absent.

Your task is to design a document set for:

**Central question:** {{central_question}}
**Student level:** {{student_level}}
**Target skills:** {{target_skills}}

The following optional context may or may not be provided. Use whatever is available.

**Existing sources:** {{existing_sources}} — if provided, evaluate these sources first. Do they create analytical tension? Do they support the target skills? Should any be removed, replaced, or supplemented?
**Set size:** {{set_size}} — if not provided, recommend 3–4 documents for a single lesson, noting that 2 is the minimum for corroboration and 5+ risks overwhelming students.
**Source constraints:** {{source_constraints}}
**Representation priorities:** {{representation_priorities}} — if provided, design the set to include these perspectives. If not, audit the set for representation and flag gaps.
**Historical topic:** {{historical_topic}}
**Curriculum framework:** {{curriculum_framework}}

Source-supply boundary: this skill designs a set; it cannot supply or certify documents merely by recommending them. Label each source within its existing description as supplied text, teacher-reported source (not inspected), or proposed/unverified recommendation. Mark unknown authors, dates, titles or availability as unverified; do not invent provenance, quotations, excerpts or working links. For proposed documents, describe the intended analytical contribution conditionally until the teacher locates and checks the actual passage. Before classroom use or handoff to Historical Source Adapter, obtain the actual text and verify attribution, content, reading level and access constraints. A design recommendation alone does not satisfy that adapter's original_source input.

Design the following:

1. **Document set design:** For each recommended document, provide:
   - A description (author, date, type, key content)
   - Why it earns its place in the set — what it contributes that no other document in the set provides
   - Which historical thinking skills it most directly supports
   - Its role in the sequence (what it adds to the investigation at this point)

   If existing sources were provided, evaluate them first and indicate which to keep, modify, or replace before recommending additions.

2. **Analytical tensions:** The specific contradictions, complementarities, or complications built into the set. For each tension, identify:
   - Which documents create the tension
   - What students should discover when they compare them
   - What historical thinking skill the tension demands

   A set with no analytical tension is a reading list, not an investigation. Every set must have at least one clear tension.

3. **Skill affordances:** For each target skill, identify which documents in the set provide the best opportunity to practise it:
   - **Sourcing:** Which document has source information that is most analytically productive?
   - **Close reading:** Which document has language most worth attending to closely?
   - **Contextualisation:** Which document is most illuminated by knowledge of its historical context?
   - **Corroboration:** Which document pairing creates the most productive comparison?

4. **Sequencing rationale:** Why the documents are ordered as they are. The default structure from the RLH curriculum is:
   - Round 1: The foundational source(s) that establish the problem
   - Round 2: Source(s) that complicate, contradict, or reinterpret
   - Round 3 (if applicable): Source(s) that add further complexity or introduce new perspectives

   Explain what each round adds to the investigation and why the order matters.

5. **Representation audit:** Whose perspectives are present in the set and whose are absent. Be honest about gaps. If the central question concerns an event involving multiple groups (colonisers and Indigenous peoples, employers and workers, men and women), note which groups have voice in the set and which do not. Where possible, suggest sources that would address gaps. Where sources from absent perspectives do not exist (because those voices were not documented), name this as a historically significant silence — itself a teaching opportunity.

Return your output in this exact format:

## Document Set Design

**Central question:** [Question]
**Students:** [Level]
**Set size:** [Number of documents]

### Document 1: [Brief title]
**Source:** [Author, date, type; supplied/teacher-reported/proposed status and what remains to verify]
**Why it's here:** [What it contributes]
**Supports:** [Which skills]
**Role in sequence:** [What it adds at this point]

### Document 2: [Brief title]
[Same format]

[Continue for each document]

### Analytical Tensions

[Numbered list of tensions with documents involved, what students should discover, and skill demanded]

### Skill Affordances

**Sourcing:** [Best document and why]
**Close reading:** [Best document and why]
**Contextualisation:** [Best document and why]
**Corroboration:** [Best pairing and why]

### Sequencing Rationale

[Why this order, what each round adds]

### Representation Audit

**Perspectives present:** [Who has voice]
**Perspectives absent:** [Who doesn't, and why]
**Suggestions:** [How to address gaps, or acknowledgement that the gap is itself historically significant]

**Self-check before returning output:** Verify that (a) every document earns its place — remove any source that doesn't contribute something unique, (b) at least one clear analytical tension exists in the set, (c) the skill affordances are specific to the documents, not generic, (d) the sequencing has a rationale beyond chronological order, and (e) the representation audit is honest about whose voices are missing, and (f) recommendations are labelled, unknown provenance is explicit, and no proposed text is presented as a document obtained or checked.
```

## 示例输出

**场景：** *Central question: "Did Pocahontas rescue John Smith?" / Student level: "Year 8, second term of document-based lessons" / Target skills: "All four — sourcing, close reading, contextualisation, corroboration" / Set size: "4 documents for a 2-hour lesson"*

---

## 文献集设计

**核心问题：** 宝嘉康蒂救了约翰·史密斯吗？
**学生：** 八年级，熟悉基于文献的探究
**文献集规模：** 分 2 轮呈现的 4 份拟议文献
**状态：** 示例性推荐，非已提供或已核验节选。使用本设计前请先定位每份文献并核查其元数据与拟议对比点；下述引用短语亦需对照所选原文核验。

### 文献 1：史密斯 1608 年《True Relation》（改编节选）
**出处：** 拟议/未核验——John Smith，1608 年，*A True Relation*，寄往英格兰的报告
**入选原因：** 建立基线记述——写作时间距事件最近，完全没有提及威胁或营救，使用了友好与慷慨的语言。其重要性恰恰在于它“没有”说什么。
**支持技能：** 溯源（日期、目的、受众）；精读（语气："kindly"、"friendship"、"kindness"）
**在序列中的角色：** 第 1 轮——学生首先接触的史料，建立起随后第二份史料将要打破的预期。

### 文献 2：史密斯 1624 年《General History》（改编节选）
**出处：** 拟议/未核验——John Smith，1624 年，*General History of Virginia*，正式出版书籍
**入选原因：** 制造核心矛盾。同一作者、同一事件，却是截然不同的记述——此刻出现了戏剧性营救、充满威胁的语言以及作为女英雄的宝嘉康蒂。与文献 1 的反差本身就是历史谜题。
**支持技能：** 溯源（17 年时间差、不同的出版语境）；精读（语气转变："barbarous"、"beat out his brains"、"dearest daughter"）；互证（与文献 1 直接矛盾）
**在序列中的角色：** 第 1 轮——与文献 1 配对以制造核心谜题。学生应在接触任何阐释框架之前先遇到这两份文献。

### 文献 3：Adams 1867 年的批判（改编摘要）
**出处：** 拟议/未核验——Henry Adams，1867 年，*The North American Review*，学术评论
**入选原因：** 引入历史阐释——一位受过训练的历史学家通过引用两份记述间的矛盾，论证史密斯的营救故事系编造。向学生展示历史学家正是用他们刚刚审视过的“同一批”证据来构建论证。
**支持技能：** 溯源（Adams 作为约翰·亚当斯曾孙的身份、其写于重建时期的政治语境）；互证（他的论证依赖于比对两份史密斯记述，示范了学生刚刚练习过的技能）
**在序列中的角色：** 第 2 轮——在学生基于一手史料形成自己的假设之后，遇到一位做了同样分析的历史学家。这既验证又拓展了学生的思考。

### 文献 4：Lemay 1991 年的辩护（改编摘要）
**出处：** 拟议/未核验——J. A. Leo Lemay，1991 年，*The American Dream of Captain John Smith*，学术阐释
**入选原因：** 与 Adams 制造张力。Lemay 主张史密斯是诚实的，两份记述不同是因为目的不同，且该事件很可能是仪式性的收养典礼而非真正的营救。这防止学生将 Adams 的怀疑态度直接当成最终答案。
**支持技能：** 互证（使用相同证据与 Adams 直接意见相左）；语境化（Lemay 的阐释依托于学生可能不了解的波瓦坦收养仪式背景知识）
**在序列中的角色：** 第 2 轮——与 Adams 配对。学生现在必须权衡两位从同一批一手史料得出相反结论的历史学家。问题无法通过挑出“对的一份”解决，而需要真正权衡证据与论证。

### 分析张力

1. **史密斯 vs. 史密斯（文献 1 与文献 2）。** 同一作者在相隔 16 年后自相矛盾。学生应发现目击者证词并非天生可靠，同一个人会因写作时间与目的不同而以不同方式讲述同一件事。*所需技能：* 溯源（为何记述不同）与精读（语言如何不同）。

2. **Adams vs. Lemay（文献 3 与文献 4）。** 两位历史学家审视同一批一手证据却得出相反结论。学生应发现历史知识是通过阐释建构出来的，而不是现成躺在文献里的。*所需技能：* 互证（比对历史学家的论证）与语境化（理解每位历史学家带入阅读的背景视角）。

3. **一手史料 vs. 二手史料（文献 1–2 vs. 3–4）。** 学生先接触原始证据，再接触对这些证据的专业阐释。他们应发现自己对一手史料的分析是进入真实史学争论的有效入口。*所需技能：* 全部四项——这一张力架构了整节课。

### 技能支撑映射

**溯源：** 文献 2（1624 年《General History》）——17 年的时间差、从报告到出版书籍的转变以及史密斯的自利动机，使其成为最丰富的溯源机会。但文献 3（Adams）在溯源上同样富有成效：他写作于 1867 年重建时期，这为其批判弗吉尼亚建基神话增添了政治维度。

**精读：** 文献 1 与文献 2 结合——从 "kindly welcomed me" 到 "their best barbarous manner" 的转变，是本文献集中最具分析价值的语言对比，个别词语承载着巨大分量。

**语境化：** 文献 2——理解史密斯为何在 1624 年写出不同版本，需要知道此时宝嘉康蒂已造访英国并成名。文献 3 同样奖励语境化：Adams 在重建时期写作，有政治动机去削弱弗吉尼亚的建基神话。

**互证：** 文献 3 与文献 4 结合——Adams 与 Lemay 构成了最清晰的对比，因为他们审视相同的证据却得出相反的结论。这一配对教会学生，互证不是寻找一致，而是通过分歧进行推理。

### 排序依据

**第 1 轮（文献 1 与文献 2——史密斯的两份记述）：** 学生在接触任何阐释之前先接触一手证据。这确保他们在被告知历史学家怎么想之前，先自己形成关于“为什么两份记述不同”的假设。1608 年记述排在前面，因为它对营救的“缺席”只有在对比中才显出意义——学生需要先读友好的记述，然后被戏剧性的记述惊到。

**第 2 轮（文献 3 与文献 4——Adams 与 Lemay）：** 在学生钻研过一手证据之后，他们遇到做了同样工作的两位历史学家。这肯定了学生的分析努力（历史学家提出了与他们相同的问题），同时拓展了探究（历史学家带入了更多知识并构建了更成熟的论证）。Adams 排在 Lemay 之前，让学生先体验对史密斯的怀疑，再被 Lemay 的辩护复杂化。

### 代表性审计

**在场视角：** 英国殖民者（Smith）、19 世纪美国历史学家（Adams）、20 世纪美国文学学者（Lemay）。全部为白人男性，且均从制度权威的位置写作。

**缺席视角：** 宝嘉康蒂本人未留下任何书面记录；没有直接呈现波瓦坦视角；没有女性声音；未纳入原住民学者的阐释。

**建议：** 这一缺席具有历史意义，应在课中明确点出：我们之所以没有波瓦坦方面关于这一事件的记述，不是一个可以随手填补的空白，而是权力的结果——谁能书写历史、谁的话语得以留存。如果拓展文献集，可考虑加入 Helen Rountree 的民族史研究（从考古学和人类学证据中重建波瓦坦视角），或 Camilla Townsend 的《Pocahontas and the Powhatan Dilemma》（突出原住民语境）。教师也可以将这种缺席本身作为溯源教学契机："Why do we only have Smith's account? What does that tell us about whose stories get preserved?"

---

## 已知局限性

1. **本技能负责设计文献集，但无法直接提供文献本身。** 它按作者、日期和类型推荐具体史料，但教师必须自行定位、获取并在必要时改编它们。对于免费可用的史料，sheg.stanford.edu 上的 SHEG/DIG 课程为许多美国史主题提供了改编好的一手史料；对于其他主题，教师需从档案馆、课本或数字馆藏中获取文献。

2. **代表性审计识别了空白，但未必总能填补。** 对某些历史主题而言，边缘化群体的声音从未被记录——不是因为他们不存在，而是因为决定何种记录得以保存的权力结构排斥了他们（Caswell, 2014; Theimer, 2012）。本技能诚实地指出这些沉默，而不是假装它们可以轻易解决。在某些情况下，缺席本身就是最值得教授的内容。

3. **文献集设计与核心问题密不可分。** 为 "Did Pocahontas rescue John Smith?" 设计的文献集，并不适用于 "What was the nature of Powhatan-English relations?"。本技能是对照所提供的具体问题来评估文献集的。如果核心问题改变，文献集应重新评估。
