---
# AGENT SKILLS STANDARD FIELDS (v2)
name: discipline-specific-critical-thinking-task-designer
description: "设计植根于知识依赖型推理而非通用技能的学科特定批判性思维任务。适用于将高阶思维嵌入学科内容。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "curriculum-assessment/discipline-specific-critical-thinking-task-designer"
skill_name: "学科特定批判性思维任务设计器"
domain: "curriculum-assessment"
version: "1.0"
evidence_strength: "strong"
evidence_sources:
  - "Bailin, Case, Coombs & Daniels (1999) — Common misconceptions of critical thinking: the intellectual resources framework"
  - "Bailin & Siegel (2003) — Critical thinking in philosophy of education"
  - "Willingham (2007) — Critical thinking: why is it so hard to teach?"
  - "McPeck (1981) — Critical Thinking and Education: domain-specificity of critical thinking"
  - "Ennis (1989) — Critical thinking and subject specificity"
  - "Paul & Elder (2006) — The Art of Socratic Questioning: disciplinary thinking standards"
  - "Perkins & Salomon (1989) — Are cognitive skills context-bound? Transfer and domain-contingency"
  - "Hattie (2009) — Visible Learning: effect sizes for thinking skills instruction"
  - "Maton (2013) — Making semantic waves: semantic gravity and cumulative knowledge-building"
  - "Bernstein (1999) — Vertical and horizontal discourse: disciplinary knowledge structures"
input_schema:
  required:
    - field: "curriculum_topic"
      type: "string"
      description: "学生当前正在学习的学科主题、单元或概念"
    - field: "learner_stage"
      type: "string"
      description: "年龄范围或年级"
    - field: "discipline_or_subject"
      type: "string"
      description: "学科领域，因为思维标准具有学科特定性"
  optional:
    - field: "knowledge_baseline"
      type: "string"
      description: "学生对该主题已经知道的内容；用于核查知识充足性"
    - field: "existing_learning_targets"
      type: "string"
      description: "本任务应当关联的任何既有学习目标（LT）"
    - field: "thinking_focus"
      type: "string"
      description: "若教师心中已有特定思维动作（例如评估证据、识别假设、考量视角）"
output_schema:
  type: "object"
  fields:
    - field: "knowledge_prerequisite_check"
      type: "object"
      description: "评估学生是否具备足够领域知识使批判性思维变得有意义；若知识基础不足则标出并建议先建立什么"
    - field: "disciplinary_thinking_standards"
      type: "object"
      description: "针对该主题，在该学科中优秀的思维具体是什么样子；不是泛泛而谈（‘仔细思考’），而是实质性的（‘在历史学中，优秀思维要求评估史料出处并在多份来源间互证主张’）"
    - field: "critical_thinking_task"
      type: "object"
      description: "结构化任务本身：情境/案例、思维要求以及学生作答的具体问题或提示"
    - field: "intellectual_resources"
      type: "object"
      description: "学生完成思考所需的脚手架支持：需激活或提供的背景知识、需澄清的关键概念、需提供的思维启发法，以及需培养的心智习惯"
    - field: "assessment_guidance"
      type: "object"
      description: "学生作答中高质量思维的评判标准；这属于横向知识（推理有优劣之分，而非唯一对错答案）；量规应评估推理过程的质量，而非结论是否正确"
    - field: "teacher_development_notes"
      type: "object"
      description: "设计与实施该任务揭示了该学科思维的什么本质；作为专业学习洞见呈现，而不仅仅是课堂交付提示"
chains_well_with:
  - "curriculum-knowledge-architecture-designer"
  - "kud-knowledge-type-mapper"
  - "coherent-rubric-logic-builder"
  - "learning-target-authoring-guide"
  - "ai-output-critical-audit-designer"
teacher_time: "10 分钟"
tags: ["critical-thinking", "disciplinary-thinking", "horizontal-knowledge", "knowledge-contingent", "task-design", "intellectual-resources", "Bailin", "Willingham", "domain-specific"]
---

# 批判性思维任务设计器

## 本技能的作用

接收一个课程主题，产出一份将学科思维嵌入学科内容的结构化批判性思维任务——并显性搭建学生开展思考所需的智力资源脚手架。批判性思维具有领域依赖性：你无法对了解甚少的事物进行批判性思考，且历史学中什么算“好思维”，不同于科学或伦理学中什么算“好思维”。本技能将这一洞见操作化。它不生产泛泛的“高阶思维”任务，而是产出思维需求特定于该学科的任务：在设计任务前先核查知识前置条件，并显性陈述优秀思维的标准，使学生清楚自己瞄准的目标是什么。本技能借鉴了 Bailin 等人的智力资源框架：一位批判性思考者需要背景知识、该领域优秀思维的操作性知识、关键概念知识、有效启发法以及心智习惯。这五者必须全部到位或得到脚手架支持，任务才能真正**培养**批判性思维，而不仅仅是**索要**批判性思维。AI 在此尤为关键，因为设计优质的批判性思维任务需要同时掌握内容领域、学科思维标准、知识前置条件与评估逻辑——这种组合在单个教育者身上十分罕见，且大多数备课流程都会完全跳过。本技能还承担教师专业发展功能：明确界定“在你的学科中什么是好思维”这一行为本身就是一项重大的教学法洞见，而大多数教师从未被要求将其清晰表述出来。

## 实证基础

奠基性洞见来自 Willingham（2007）：批判性思维技能并不像通用技能那样可以自由迁移。在历史课上能批判性思考的学生，在生物学上可能思考得十分天真，因为优秀思维的标准具有学科特定性。脱离具体学科内容去教授通用批判性思维技能——推断、分析、评价——只会教出能背出思维动作名称却无法有意义地执行的学生。启示很明确：批判性思维必须**通过**学科来培养，而不是**平行于**学科去教。

Bailin 等人（1999）提供了最实用的操作框架。他们通过必须具备的五项**智力资源**来界定批判性思考者：**背景知识**（对不了解的事物无法批判性思考）、该领域优秀思维的**操作性知识**、**关键概念知识**（证据、论证、假设、视角）、**有效启发法**（在该领域行之有效的思维动作），以及**心智习惯**（智力谦逊、容忍模糊性、追求严谨推理的承诺）。通用批判性思维教学通常只提供第三类——概念——并假设其余四项会自动跟上。事实并非如此。

McPeck（1981）主张批判性思维完全具有领域特定性——不存在通用思维技能，只有学科思维技能。Ennis（1989）则反驳称部分思维技能可以跨领域迁移。这场领域特定性之争对课程设计者有一个务实结论：某些思维技能比另一些更具迁移性（识别假设、考量替代视角），但所有思维技能都需要领域知识才能有意义地执行。设计启示在于：批判性思维任务应当嵌入具体内容之中，显性核查或提供领域知识，并用学科特定术语陈述思维标准。

Bailin & Siegel（2003）在教育哲学框架内拓展了这一思路，指出批判性思维根本不是一种“技能”，而是由思考者所调动的智力资源构成的推理**质量**。这一重构对任务设计至关重要：目标不是把“批判性思维”当作一项技能去教，而是确保学生拥有针对特定主题进行良好思考所需的智力资源，然后创造需要调动这些资源的任务。

Paul & Elder（2006）贡献了学科思维标准概念——即学科内部评判推理优劣的具体标准。在科学中，好思维要求可检验的假设、受控变量和基于证据的结论。在历史学中，好思维要求史料评估、互证与语境化。在伦理学中，好思维要求识别利益相关方、清晰阐述原则与权衡后果。这些标准不可互换，未能显性阐明相关标准的任务会让学生只能猜测“好思维”究竟是什么意思。

Hattie（2009）发现教授思维技能具有中等效应量（d = 0.62），但随实施方式差异巨大。证据表明，当思维技能教学嵌入内容之中、思维标准显性化、且学生练习将其应用于具体问题时，教学最为有效——这正是本技能旨在创造的条件。脱离内容的通用思维技能教学产出的效应要弱得多。

Maton（2013）的语义波概念在此同样适用：有效的知识建构需要在抽象原则与具体案例之间往返移动。始终停留在抽象层面（“分析论证”）而不锚定具体内容的批判性思维任务，只会产出浅薄思考；始终停留在具体层面（“描述发生了什么”）而不要求应用分析框架的任务，产出的只是描述而非思考。设计良好的任务能带领学生穿越语义波：从具体案例走向抽象原则，再落回具体应用。

Perkins & Salomon（1989）证明，认知技能的迁移不会自动发生——它需要刻意搭建桥梁。学生不会自发把在一门课学到的思维技能应用到另一门课。这强化了如下设计原则：批判性思维必须在每门学科内部单独培养，并显性关注哪些思维动作是学科特定的，哪些可以在刻意教学下实现迁移。

## 输入规范

教育者必须提供：
- **课程主题（Curriculum topic）：** 学生当前学习的主题、单元或概念。*例如：“九年级历史——第一次世界大战的起因” / “十年级生物——自然选择与进化” / “八年级伦理——电车难题与道德推理”*
- **学习者阶段（Learner stage）：** 年龄范围或年级。*例如：“14–15 岁” / “九年级” / “D 学段”*
- **学科或科目（Discipline or subject）：** 学科领域。*例如：“历史” / “生物” / “伦理” / “地理”*

可选项（如可用则由上下文引擎注入）：
- **知识基线（Knowledge baseline）：** 学生对该主题已经知道什么
- **既有学习目标（Existing learning targets）：** 本任务应关联的任何 LT
- **思维焦点（Thinking focus）：** 教师希望强调的特定思维动作

## 提示词（Prompt）

```
You are an expert in critical thinking pedagogy, with deep knowledge of Bailin et al.'s (1999) intellectual resources framework, Willingham's (2007) research on domain-specificity, McPeck's (1981) and Ennis's (1989) work on critical thinking and subject specificity, Paul & Elder's (2006) disciplinary thinking standards, Hattie's (2009) evidence on thinking skills instruction, and Maton's (2013) semantic wave concept. You understand that critical thinking is domain-contingent: it requires sufficient domain knowledge, discipline-specific thinking standards, and all five intellectual resources (background knowledge, operational knowledge, critical concepts, heuristics, habits of mind) to be present or scaffolded.

Your task is to design a structured critical thinking task for the following curriculum input.

**Curriculum topic:** {{curriculum_topic}}
**Learner stage:** {{learner_stage}}
**Discipline or subject:** {{discipline_or_subject}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Knowledge baseline:** {{knowledge_baseline}} — if not provided, state what the minimum knowledge base would need to be and flag this as an assumption.
**Existing learning targets:** {{existing_learning_targets}} — if provided, connect the task to these LTs.
**Thinking focus:** {{thinking_focus}} — if provided, use this as the primary thinking demand. If not provided, select the most productive thinking demand for this topic and discipline.

## Process

Follow these seven steps precisely. Each step produces a named section in the output.

**Step 1 — Knowledge Prerequisite Check.**
Before designing the task, assess whether students have sufficient domain knowledge for critical thinking to be meaningful. If a student cannot accurately describe the phenomenon they are asked to analyse, they cannot analyse it critically — they will produce opinion dressed as reasoning. State explicitly: what is the minimum knowledge base required for this task? If the knowledge baseline provided suggests students are not there yet, flag this and recommend what to establish first. Do not proceed to task design until this question is answered. If no knowledge baseline is provided, state the assumed prerequisites and flag this as an assumption the teacher must verify.

**Step 2 — Identify the Disciplinary Thinking Standard.**
What does good thinking look like specifically in this discipline and for this topic? Avoid generic standards. "Evaluates evidence" is generic. "In history: identifies the provenance of a source, explains how provenance affects reliability, and corroborates the claim across at least two independent sources" is disciplinary. State the standard in terms that a student could understand and a teacher could use to assess. Reference the discipline's conventions for valid reasoning — what counts as evidence, what counts as a strong argument, what distinguishes expert thinking from novice thinking in this field.

**Step 3 — Select the Thinking Demand.**
Choose one primary thinking move for this task. Options include but are not limited to: evaluating competing claims or interpretations, identifying assumptions underlying a position, analysing a case through multiple lenses, constructing and defending a reasoned argument, identifying the limits of a given explanation, or considering how context or perspective changes interpretation. One thinking demand, done well, produces more genuine critical thinking than five thinking demands done superficially. State the selected thinking demand and explain why it is the most productive choice for this topic and learner stage.

**Step 4 — Design the Task.**
Write the context or scenario students will think about. It should be concrete, discipline-specific, and genuinely open — there should be better and worse answers but not a single correct answer. Write the specific question or prompt. It should require the selected thinking move to answer well. It should not be answerable by recall alone. The task should move students across Maton's (2013) semantic wave: from concrete case to abstract principle and back to concrete application.

**Step 5 — Scaffold the Intellectual Resources.**
For each of Bailin et al.'s (1999) five intellectual resources, state what students need and how it will be provided or activated:

1. **Background knowledge:** What do students need to know, and is it already established or does it need to be provided in the task materials? If it needs to be provided, specify exactly what to include.
2. **Operational knowledge:** What does good thinking look like here, and has the teacher modelled it? If not, how should the standard be shared with students before they begin?
3. **Critical concepts:** Which concepts (evidence, assumption, perspective, causation — discipline-specific) are required, and do students have working definitions? If not, provide the definitions.
4. **Heuristics:** What thinking moves or protocols will help students approach this task? Provide 1-2 specific, actionable heuristics — not generic advice ("think carefully") but concrete moves ("ask: what would change my mind about this?").
5. **Habits of mind:** Which dispositions (intellectual humility, tolerance for ambiguity, willingness to revise) does this task cultivate, and how will the classroom environment support them? Note: these are dispositional — they cannot be assessed through this task but can be cultivated by it.

**Step 6 — Write the Assessment Guidance.**
State 3-4 criteria for quality thinking in student responses. These criteria assess the reasoning process, not the conclusion. A student who reaches an unconventional conclusion through rigorous reasoning should score higher than a student who reaches a conventional conclusion through poor reasoning. Make the criteria specific to this task and this thinking demand. Use the rubric scale Emerging / Developing / Competent / Extending if level descriptors are provided. These criteria become the input for the Coherent Rubric Logic Builder if a formal rubric is needed.

**Step 7 — Write the Teacher Development Notes.**
What does designing and running this task reveal about disciplinary thinking in this subject? What would a teacher who ran this task learn about what good thinking looks like in their discipline? Frame this as professional insight, not classroom management advice. This section is the reason the skill has value beyond individual lesson planning — it builds the teacher's own critical thinking about their subject.

Return your output in this exact format:

## Critical Thinking Task: [Topic]

**Discipline:** [Subject]
**Learner stage:** [Age/year]
**Thinking demand:** [Selected thinking move]
**Connected LTs:** [If provided; otherwise "None specified"]

### 1. Knowledge Prerequisite Check

**Minimum knowledge required:**
[List the specific knowledge elements students must have before this task is meaningful]

**Status:** [Sufficient / Insufficient / Assumed — based on knowledge baseline provided]

[If insufficient: what must be established first, and how]

### 2. Disciplinary Thinking Standard

**In [discipline], good thinking about [topic] requires:**
[State the standard in discipline-specific terms — what counts as evidence, what counts as a strong argument, what distinguishes expert from novice reasoning]

### 3. Thinking Demand

**Primary thinking move:** [Selected demand]
**Why this demand:** [Why it is the most productive choice for this topic and learner stage]

### 4. The Task

**Context:**
[The scenario or case students will think about — concrete, discipline-specific, genuinely open]

**Task materials provided to students:**
[Any documents, data, sources, or information students need — specify exactly what is given]

**The question:**
[The specific prompt — requiring the selected thinking move, not answerable by recall alone]

### 5. Intellectual Resources

| Resource | What students need | How it is provided or activated |
|---|---|---|
| Background knowledge | [Specific knowledge] | [Already established / provided in task materials / needs pre-teaching] |
| Operational knowledge | [What good thinking looks like here] | [How the standard is shared — teacher modelling, exemplar, explicit statement] |
| Critical concepts | [Discipline-specific concepts required] | [Working definitions provided / already established / needs explicit teaching] |
| Heuristics | [Specific thinking moves] | [Stated to students as protocol / modelled by teacher] |
| Habits of mind | [Dispositions cultivated] | [How the classroom environment supports them] |

### 6. Assessment Guidance

**Criteria for quality thinking** (assess reasoning process, not conclusion):

1. [Criterion 1 — specific to this task]
2. [Criterion 2]
3. [Criterion 3]
4. [Criterion 4 — if needed]

**What distinguishes Competent from Extending:**
[The specific quality of reasoning that separates meeting the standard from genuinely exceeding it]

### 7. Teacher Development Notes

[What this task reveals about disciplinary thinking in this subject — framed as professional insight]

**Self-check before returning output:** Verify that (a) the knowledge prerequisite check is specific and honest — not assumed to be sufficient without evidence, (b) the disciplinary thinking standard is genuinely discipline-specific, not generic, (c) the task is not answerable by recall alone, (d) all five intellectual resources are addressed with specific content, not generic placeholders, (e) the assessment criteria assess reasoning quality, not conclusion correctness, (f) the teacher development notes contain genuine disciplinary insight, and (g) the rubric scale uses Emerging / Developing / Competent / Extending wherever level descriptors appear.
```

## 示例输出

**情景：** *课程主题：“九年级历史——第一次世界大战的起因” / 学习者阶段：“14–15 岁” / 学科或科目：“历史” / 知识基线：“学生已学习过同盟体系（三国同盟与三国协约）、斐迪南大公遇刺与七月危机、欧洲列强间的帝国主义竞争，以及 19 世纪末民族主义的兴起” / 思维焦点：“评估相互竞争的历史阐释”*

---

## 批判性思维任务：第一次世界大战的起因

**学科：** 历史
**学习者阶段：** 14–15 岁（九年级）
**思维要求：** 评估相互竞争的历史阐释
**关联 LT：** 未指定

### 1. 知识前置核查

**所需最低知识基础：**
- 同盟体系：三国同盟与三国协约各包含哪些国家，同盟条约使它们承担了什么义务
- 斐迪南大公遇刺：发生了什么、何时、何人所为，以及直接政治后果（奥匈帝国向塞尔维亚发出最后通牒）
- 七月危机：遇刺（1914 年 6 月 28 日）与全面战争爆发（1914 年 8 月初）之间的事件顺序——具体而言，哪个国家在何时、为何动员
- 帝国主义竞争：欧洲列强在争夺什么（殖民地、贸易路线、国家威望），以及至少两个具体帝国竞争案例
- 民族主义：民族主义情绪如何加剧紧张局势——至少理解统一型民族主义（如泛斯拉夫主义）与国家型民族主义（如法国复仇主义）的区别
- 至少具备基本意识：历史学家对于**谁**或**什么**应对战争负主要责任存在分歧——即史学辩论的概念，即使学生尚不知晓具体立场

**状态：** 充足——所提供的知识基线覆盖了全部必需要素。唯一需要核实的是学生是否理解历史学家就起因积极争论，还是仅仅把“一战起因”当成一套定论清单来背诵。若是后者，在任务前需简短引入史学辩论概念。

### 2. 学科思维标准

**在历史学中，关于一战起因的优秀思维要求：**

- **史料评估：** 评估谁写了或说了某段话、在何时、何种语境、出于何种目的——并解释这些因素如何影响该史料在支撑特定主张时的可靠性与有用性。引用 1914 年 7 月德国政府备忘录的历史学家，必须考虑到该备忘录写于外交危机期间，可能反映的是策略站位而非真实意图。
- **互证（Corroboration）：** 不依赖单一史料或单一历史学家的阐释。关于因果关系的主张必须对照多份史料核验。如果 Fischer 主张德国蓄意策划战争，就必须审视他使用的证据——同时必须考量其他历史学家的竞争性证据。
- **区分因果类型：** 近因（遇刺事件、七月危机）不同于结构性原因（同盟体系、帝国主义竞争、民族主义）。优秀的历史思维会点明当前讨论的是哪种原因，并解释这一区分为何重要。
- **恰当限定（Qualification）：** 关于历史因果的主张应当保持克制限定——用“证据表明”而非“这证明了”。优秀的历史思维承认证据能支撑什么，以及它不能支撑什么。

### 3. 思维要求

**核心思维动作：** 评估相互竞争的历史阐释
**为何选择此要求：** 在 14–15 岁，学生已准备好超越“罗列起因”（回忆），进入“理解历史学家对哪些起因最重要以及为何重要存在分歧”的阶段。这是从将历史视为固定叙事向将历史视为持续论证的过渡——是最根本的学科思维转向。评估竞争性阐释要求学生评判推理质量而不仅仅是记忆主张内容，这正是历史批判性思维的核心。同时它要求学生把两种立场同时装在脑海中并在两者间做出有理有据的判断——在恰当脚手架支持下，这是该年龄段能够胜任的认知挑战。

### 4. 任务设计

**情境背景：**
1961 年，德国历史学家 Fritz Fischer 出版著作，主张德国应对第一次世界大战承担主要责任——德国领导层蓄意推行侵略政策，利用斐迪南大公遇刺作为借口，发动了一场他们早已策划的战争。这一论点引发轩然大波。数十年来，公认观点一直是各大国通过同盟、误判与局势升级的叠加“梦游般”卷入战争——没有任何单一国家应负主要责任。Fischer 的论证使历史学家阵营分裂，至今仍在争论之中。

**提供给学生的任务材料：**

**史料 A——Fischer 论题（摘要）：**
Fischer 主张，德国领导层（尤其是首相 Bethmann-Hollweg）推行了扩张主义战争目标的“九月纲领”。他指出德国向奥匈帝国开出无条件支持的“空白支票”，明知这很可能导致更大规模战争。Fischer 利用 1914 年德国政府档案论证：开战决定是蓄意的，而非意外。

**史料 B——修正主义立场（摘要）：**
包括 Christopher Clark（《梦游者》，2012）在内的历史学家主张所有大国共同承担责任。Clark 将战争爆发描述为一场集体失败：奥匈帝国鲁莽的最后通牒、俄国过早动员、法国对俄国的鼓动、英国模糊的信号——每一个大国都做出了使危机升级的决定。Clark 认为，聚焦德国罪责扭曲了一幅多方行为体均做出灾难性选择的图景。

**史料 C——一手证据：**
1914 年 7 月 29 日德国皇帝威廉二世致俄国沙皇尼古拉二世电报：“我正在尽最大努力劝说奥匈政府坦诚行事，以期与你方达成令人满意的谅解。我深信你会协助我努力化解可能仍会出现的困难。你最真诚、忠实的朋友与表兄，威利。”

**史料 D——一手证据：**
1912 年 12 月 8 日德国帝国战争委员会会议纪要节选（由 Fischer 发现）：“皇帝陛下表示……若俄国动员，则别无选择唯有开战。他进一步表示海军必须为对英作战做好准备……总参谋长表示，在他看来战争不可避免——越早越好。”

**任务问题：**
基于你学过的知识以及所提供的史料，哪一种阐释——Fischer 的德国主责论，还是修正派的共同责任论——得到了现有证据更有力的支撑？在你的回答中：
- 说明你认为哪一种阐释更有说服力，并解释原因
- 结合所提供史料中的具体证据**以及**你自己的历史知识来支撑你的立场
- 解释**另一方**所使用的、你觉得最难反驳的证据是什么
- 指出至少一件这些证据**无法**告诉我们的事——即关于一战起因我们所能认知的边界

### 5. 智力资源脚手架

| 资源 | 学生需要什么 | 如何提供或激活 |
|---|---|---|
| 背景知识 | 同盟体系、七月危机顺序、帝国主义竞争、民族主义——足以评估史料证据是否与更广泛模式一致 | 通过先前教学已建立。教师应在课初开展一次简短提取活动（5 分钟）：“凭记忆列出同盟义务和七月危机时间线。”这能激活知识并在任务开始前暴露漏洞。 |
| 操作性知识 | 优秀历史论证是什么样子——基于证据、审慎限定、回应反证、区分因果类型 | 教师在任务前用另一个例子示范：选一个更简单的历史辩论（例如“罗马帝国衰落是由蛮族入侵还是内部腐败导致的？”），演示对两种立场的强有力评估是什么样子。10 分钟。学生在被要求达标前先看见标准。 |
| 关键概念 | **历史因果：** 近因（触发战争的事件）vs. 结构性原因（使战争成为可能的条件）。**史料出处（Provenance）：** 谁在何时为何制作了史料——以及这如何影响我们能用它来支撑什么。**互证：** 用多份史料核验同一主张。 | 教师在黑板或学习单上提供工作定义。核心提问：“当我们在历史中说‘原因’时，是指‘触发事件的导火索’，还是‘使事件成为可能的条件’？Fischer 在这两方面都有论证。每一条证据分别支撑哪一种原因？” |
| 启发法（Heuristics） | **“什么会改变我的想法？”**——形成初步立场后，学生追问：我需要看到什么证据才会倒向另一种阐释？这迫使学生真正回应反方论点而非轻率打发。**“这份证据不能告诉我们什么？”**——针对每份史料识别其局限。德皇电报显示了他对沙皇说了什么，而非他真实意图；战争委员会纪要显示讨论了什么，而非最终决定了什么。 | 作为两条思维协议明确写在黑板上。学生在动笔前教师先带练一个例子：“史料 C——德皇电报——听起来很温和。但它**不能**告诉我们什么？它不能告诉我们威廉究竟是真诚的，还是在为了外交记录做表面文章。这直接影响我们给它多大权重。” |
| 心智习惯 | **智力谦逊：** 愿意说出“我不确定”或“证据尚无定论”。**容忍模糊性：** 能够同时把两种合理阐释放在脑海中，不急于强行消解张力。**修正意愿：** 若证据充分，愿意改变想法。 | 教师明确设定课堂基调：“在历史课上，说‘我不确定哪种阐释更有力’不是软弱——只要你能解释**为什么**不确定，这就是成熟思维的标志。比起虚假的笃定，我更看重诚实的不确定性。”确立规则：任务奖励推理质量，而非立场有多强硬。 |

### 6. 评估指南

**高质量思维标准**（评估推理过程，而非结论立场）：

1. **具体历史证据的运用。** 学生是否引用了所给史料中**以及**自己知识库中的具体证据？笼统提及（“有证据表明德国想打仗”）得分低于具体引用（“1912 年 12 月战争委员会纪要显示德皇与总参谋长讨论战争不可避免——Fischer 用此论证开战是预谋的”）。仅复述 Fischer 的观点不算证据——Fischer 所使用的史料才是证据。

2. **对反方论点回应的质量。** 学生是否真正回应了对方阐释的最强版本，还是流于表面地否定？写“修正派错了，因为是德国挑起的”不算有效回应。写“Clark 认为各方共担责任的论点得到了俄国过早动员的支撑——这是 Fischer 论题最难解释的证据，因为它表明局势升级并非德国单方面所致”才是有意义的回应。

3. **主张的恰当限定。** 学生是否区分了证据支撑什么与不支撑什么？像“这证明德国负全责”这样的主张过于绝对——证据并无定论。像“战争委员会纪要表明至少部分德国领导层早在 1912 年就认为战争可取，尽管纪要本身不能证明这种偏好最终变成了国家政策”则限定得当。

4. **历史推理的学科准确性。** 学生是否区分近因与结构性原因？是否区分史料字面说了什么与实际意味着什么？是否区分证据能支撑与不能支撑的内容？将所有证据等量齐观或完全忽略史料出处的学生，其推理低于学科标准。

**胜任（Competent）与拓展（Extending）的区别：**
胜任级作答能运用具体证据评估两种阐释、回应反方论点并恰当限定主张。拓展级作答在此基础上，还能指出**证据基础本身的真实局限**——即在现有史料下**两种**阐释都无法完全解释的空白——并阐明还需要什么进一步证据才能解决这一争论。这标志着从“在给定框架内评估”跃迁到“评估框架本身”。

### 7. 教师发展说明

**本任务揭示了历史学科思维的什么本质：**

设计这项任务迫使教师直面一个大多数历史教师从未被明确追问过的问题：知道一战的起因，与针对一战起因进行**历史性思考**，区别究竟在哪里？答案并不显而易见。能背出全部四个 MAIN 起因（同盟、帝国主义、军国主义、民族主义）并详述七月危机的学生拥有大量知识——但他们可能完全不知道如何评估哪个原因更重要，也不知道如何评判历史学家的论证质量。知识是思考的必要条件，但并非充分条件。

历史学科的思维标准——史料评估、互证、区分因果类型、恰当限定——并不是大多数历史课程会显性写明的内容。学生常被要求“评估史料”，却极少被教导在历史学中“评估”到底意味着什么：出处之所以重要，是因为它决定了史料能用来支撑什么主张；互证之所以重要，是因为没有任何单一史料足以支撑因果主张；限定之所以重要，是因为历史证据永远是不完整的。将这些标准显性化本身就是一次专业发展训练：教师必须把自己在历史推理时隐性运用的动作清晰表达出来，这要求他们审视自己的学科思维。

Fischer 争论尤其富有启发性，因为它展示了历史知识并非尘埃落定。一直把“一战起因”当作标准清单来学的学生，可能会对历史学家围绕同一批事件产生根本分歧感到迷茫。这种迷茫是富有成效的——正是从这一刻起，学生开始理解历史是一场论证，而非单一叙事。但这要求教师自己对模糊性感到自在，而这又要求教师足够熟悉史学争论，从而能引导学生在真正的不确定性中穿行，而不是退回到虚假的确定性中。

“什么会改变我的想法？”这一启发法作为可迁移动作尤为值得关注。虽然学科思维标准是历史特定的，但追问“什么证据会让我修正立场？”这一习惯却是跨学科迁移的元认知动作。一位在历史课运行了此任务的教师，如果再去询问科学或伦理学同事在他们学科中对应的启发法是什么，他正在做的正是那种能够一次一门学科、在显性化各自标准中建立全校批判性思维文化的跨学科专业学习。

---

## 已知局限

1. **批判性思维任务的好坏完全取决于其前置知识基础的扎实度。** 本技能包含前置核查，但它无法验证学生实际知道什么——只能依据教师的汇报。为“熟悉同盟体系”的学生设计的任务，如果他们其实一知半解，就会失败。教师必须诚实评估知识充足性。

2. **思维标准的领域特定性意味着本技能需要教师具备足够学科理解来把关输出。** 本技能会生成学科思维标准——但如果该标准未能准确反映专家在该领域实际如何推理，任务培养的就会是伪批判性思维，而非真正的学科推理。教师是最终质量守门人。

3. **单次任务培养不出批判性思维。** 批判性思维是在持续课程中反复练习学科思维而发展起来的。单个精心设计的任务只是课程应持续实践的范例，而非孤立的灵丹妙药。如果一整个单元只用一次本技能，其余教学全靠死记硬背，批判性思维就无法发展。

4. **心智习惯成分（智力谦逊、容忍模糊性）属于倾向性素养，无法通过单次任务培养或通过量规评估。** 如果课堂文化支持，任务可以滋养这些习惯——但课堂文化超出本技能范围。如果评估环境充满控制感或高利害压力，学生就会为了迎合量规而“表演”推理，而非投入真正思考。

5. **不应想当然假设跨领域迁移。** 在历史课运行本技能并不意味着学生在科学课就会批判性思考。每门学科都需要将自己的思维标准显性化。恰当的做法是在多门学科中持续使用本技能，而不是假设在一个领域培养的批判性思维会自动迁移。
