---
# AGENT SKILLS STANDARD FIELDS (v2)
name: cross-cultural-task-validity-checker
description: "检查教育实践或任务是否存在文化偏见、WEIRD 假设与跨文化效度问题。适用于为多元文化背景调整资源或审视普适性论断时。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "global-cross-cultural-pedagogies/cross-cultural-task-validity-checker"
skill_name: "跨文化任务效度检查器"
domain: "global-cross-cultural-pedagogies"
version: "1.0"
evidence_strength: "strong"
evidence_sources:
  - "Henrich, Heine & Norenzayan (2010) — The weirdest people in the world? (WEIRD bias in behavioural science)"
  - "Tobin, Wu & Davidson (1989) — Preschool in Three Cultures: Japan, China, and the United States"
  - "Alexander (2001) — Culture and Pedagogy: international comparisons in primary education"
  - "Stigler & Hiebert (1999) — The Teaching Gap: best ideas from the world's teachers for improving education in the classroom"
  - "Nsamenang (2006) — Human ontogenesis: an indigenous African view on development and intelligence"
input_schema:
  required:
    - field: "task_or_practice"
      type: "string"
      description: "需要检查跨文化效度的教育任务、教学实践、策略或研究成果"
    - field: "intended_context"
      type: "string"
      description: "该任务或实践将被用于何处及面向哪些学生——学生的具体文化语境"
  optional:
    - field: "source_context"
      type: "string"
      description: "该任务或实践最初是在何处开发或研究的——其起源文化语境"
    - field: "student_level"
      type: "string"
      description: "年龄/年级"
    - field: "subject_area"
      type: "string"
      description: "课程学科"
    - field: "specific_concerns"
      type: "string"
      description: "教师对文化契合度的任何特定顾虑"
output_schema:
  type: "object"
  fields:
    - field: "validity_analysis"
      type: "object"
      description: "对任务跨文化效度的分析——它隐含了哪些假设，在何处可能无法迁移"
    - field: "cultural_assumptions"
      type: "array"
      description: "嵌入任务中的具体文化假设——关于个人主义、沟通风格、知识、权威或价值观"
    - field: "adaptation_suggestions"
      type: "array"
      description: "如何针对目标语境调整该任务——具体、可操作的修改建议"
    - field: "alternative_approaches"
      type: "array"
      description: "来自其他文化传统、以不同方式达成相同学习目标的替代做法"
chains_well_with:
  - "culturally-responsive-teaching-designer"
  - "ubuntu-collective-knowledge-task-designer"
  - "belonging-classroom-culture-designer"
  - "phenomenon-based-unit-anchor"
teacher_time: "3 分钟"
tags: ["WEIRD-bias", "Henrich", "cross-cultural", "cultural-assumptions", "validity", "decolonising", "global-pedagogy"]
---

# 跨文化任务效度检查器

## 本技能的作用

分析一项教育任务、教学策略或基于研究的实践，揭示其中可能限制其在不同文化背景学生中有效性或适用性的隐性文化假设。来自 Henrich, Heine & Norenzayan (2010) 的核心洞察在于：绝大多数教育研究是在 WEIRD 人群（Western 西方、Educated 受过良好教育、Industrialised 工业化、Rich 富裕、Democratic 民主）中进行的，但研究发现却常被当作“人类普适规律”来呈现，尽管它们实际上具有文化特定性。一项在研究中“有效”的教学策略，之所以有效，可能是因为它契合了被研究人群的文化假设——而不是因为它放之四海而皆准。本技能识别嵌入任务中的具体文化假设（关于个人主义、沟通风格、权威、知识、竞争或价值观），评估这些假设在目标语境中是否成立，并提出调整建议或来自其他文化传统的替代方案。输出包括效度分析、文化假设识别、调整建议以及替代方法。AI 在此尤为有价值，因为识别隐性文化假设需要同时理解来源文化语境与使用文化语境——这需要横跨多个文化体系的广泛交叉比对知识。

## 循证基础

Henrich, Heine & Norenzayan (2010) 证明，心理学、认知科学和行为经济学中的绝大多数研究都是在 WEIRD 人群中开展的——然而研究成果却习惯性地被泛化为“人类”规律，仿佛 WEIRD 人群具有普遍代表性。他们指出，WEIRD 人群在许多维度上都是统计学上的离群值：相比世界上大多数人口，他们更具个人主义倾向、更偏向分析性思维、更倾向于抽象推理，也更看重个人选择与自主性。这对教育具有直接启示：源自 WEIRD 研究的教学策略可能携带隐性文化假设，而这些假设对来自其他文化传统的学生并不成立。Tobin, Wu & Davidson (1989) 比较了日本、中国和美国的学前教育，揭示了关于教育目的、教师角色、个人成就与集体成就价值以及何为“良好”学习行为的根本不同假设。Alexander (2001) 对英格兰、法国、印度、俄罗斯和美国的小学教育开展了最全面的国际比较研究，发现教学实践反映着深层文化价值观——何为“好教学”在不同文化间差异巨大，在一种文化中有效的实践在另一种文化中可能无效甚至适得其反。Stigler & Hiebert (1999) 比较了日本、德国和美国的数学教学，表明日本教师和美国教师对学生如何学习持有根本不同的理论——日本教师运用建设性挣扎与全班讨论，而美国教师优先考虑个人练习与即时成功。两者并无绝对“对错”，但若不加调整就将其中一种直接移植到另一种文化语境中，很难取得成功。Nsamenang (2006) 阐述了非洲人类发展观，以社会责任、参与式学习和社区嵌入为核心——挑战了将个人自主与抽象认知成就置于首位的西方发展模型。

## 输入模式

教师必须提供：
- **Task or practice（任务或实践）：** 要检查的内容。*例如："Growth mindset praise — telling students 'You worked really hard on that' instead of 'You're so smart'" / "Think-pair-share as a discussion strategy" / "Individual goal-setting where each student writes their own personal learning target" / "Using Bloom's Taxonomy to design higher-order thinking questions" / "Exit tickets where students individually write what they learned at the end of the lesson"*
- **Intended context（目标语境）：** 将在何处使用。*例如："A multicultural school in London with students from diverse backgrounds including recent arrivals" / "A school in rural Kenya" / "A school in Japan" / "A classroom with a significant proportion of First Nations students in Australia" / "An international school in Singapore with students from 40+ nationalities"*

可选（如上下文引擎可用则自动注入）：
- **Source context（来源语境）：** 该实践在何处开发
- **Student level（学生水平）：** 年级
- **Subject area（学科领域）：** 课程学科
- **Specific concerns（具体顾虑）：** 教师对文化契合度的特定担忧

## Prompt

```
You are an expert in cross-cultural education research, with deep knowledge of Henrich, Heine & Norenzayan's (2010) WEIRD bias research, Tobin, Wu & Davidson's (1989) cross-cultural comparison of early childhood education, Alexander's (2001) comparative pedagogy, Stigler & Hiebert's (1999) research on mathematics teaching across cultures, and Nsamenang's (2006) African developmental psychology. You understand that educational practices are cultural products — they emerge from specific cultural contexts and carry assumptions about learning, personhood, knowledge, authority, and community that may not transfer across cultures.

CRITICAL PRINCIPLES:
- **All educational practices carry cultural assumptions.** There is no "culture-free" pedagogy. Every teaching strategy, assessment method, and classroom routine embodies assumptions about what learning is, how people relate to each other, and what matters. The task is to make these assumptions VISIBLE, not to eliminate them (which is impossible).
- **"Evidence-based" does not mean "universally valid."** A practice that has strong research evidence may have been tested only with WEIRD populations. The evidence tells us it works in THAT context — it does not tell us it works everywhere. Be precise about what the evidence actually shows and where it was generated.
- **Identify the SPECIFIC assumption, not a vague concern.** "This might not work in other cultures" is too vague. "This practice assumes that individual public performance is motivating — but in cultures that value group harmony, being singled out may cause discomfort rather than motivation" is specific and actionable.
- **Offer adaptations, not just critiques.** Identifying cultural assumptions is useful only if it leads to practical adaptation. For each assumption identified, suggest how the practice could be modified to work in the intended context — or suggest an alternative approach from a different cultural tradition that achieves the same learning objective.
- **Avoid both cultural essentialism and cultural relativism.** Don't assume all members of a cultural group share the same values (essentialism). Don't conclude that nothing can transfer across cultures (relativism). Instead, identify specific assumptions, assess their fit with the specific context, and adapt thoughtfully.

Your task is to check the cross-cultural validity of:

**Task or practice:** {{task_or_practice}}
**Intended context:** {{intended_context}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Source context:** {{source_context}} — if not provided, identify the likely cultural origin of the practice.
**Student level:** {{student_level}} — if not provided, design for general school-age students.
**Subject area:** {{subject_area}} — if not provided, address the practice in general terms.
**Specific concerns:** {{specific_concerns}} — if not provided, conduct a general cross-cultural validity analysis.

Return your output in this exact format:

## Cross-Cultural Validity Check: [Practice Name]

**Practice:** [What is being checked]
**Source context:** [Where the practice was developed/researched]
**Intended context:** [Where it will be used]
**Overall assessment:** [Brief summary — e.g., "Partially transferable with significant adaptations needed" / "Core principle transfers well; specific implementation needs adjustment" / "Fundamental assumptions may not hold in this context"]

### Cultural Assumptions Identified

For each assumption (3–5):
**Assumption [N]: [The assumption]**
- **What the practice assumes:** [The specific cultural value or norm embedded in the practice]
- **Where this assumption holds:** [Cultures/contexts where this assumption is valid]
- **Where it may not hold:** [Cultures/contexts where this assumption may not apply]
- **Evidence:** [Research or cross-cultural comparison that supports this analysis]

### Adaptation Suggestions

For each adaptation (2–4):
**Adaptation [N]: [What to change]**
- **Original:** [How the practice currently works]
- **Adapted:** [How to modify it for the intended context]
- **Why this works:** [How the adaptation addresses the cultural assumption while maintaining the learning objective]

### Alternative Approaches From Other Traditions

[2–3 alternative approaches from non-WEIRD educational traditions that achieve the same learning objective through different cultural logic]

### What Transfers Well

[Elements of the practice that DO transfer across cultures — the universal or widely applicable principles underneath the cultural packaging]

### Honest Caveats

[Limitations of this analysis — what can and cannot be determined without direct knowledge of the specific students and community]

**Self-check before returning output:** Verify that (a) specific cultural assumptions are identified, not vague concerns, (b) the analysis avoids cultural essentialism, (c) practical adaptations are suggested, (d) alternative approaches are offered from non-WEIRD traditions, (e) the analysis identifies what DOES transfer, not just what doesn't, and (f) honest caveats acknowledge the limits of the analysis.
```

## 示例输出

**场景：** *Task or practice: "Think-pair-share — a discussion strategy where the teacher asks a question, gives students individual thinking time, then pairs discuss, then selected pairs share with the whole class. Widely used as a 'best practice' for increasing student participation." / Intended context: "An international school in the UAE with students from diverse backgrounds — Emirati, South Asian (Indian, Pakistani, Bangladeshi), Filipino, Egyptian, Jordanian, British, American. Significant cultural diversity in the same classroom. Some students are very comfortable with public discussion; others rarely speak in class despite being capable and engaged." / Specific concerns: "I notice that think-pair-share seems to work well for some students but not others. The students who don't participate aren't disengaged — they seem uncomfortable with the format itself. I want to understand whether the strategy has cultural assumptions that might explain this."*

---

## 跨文化效度检查：思考-结对-分享（Think-Pair-Share）

**实践：** Think-pair-share —— 个人思考时间 → 同伴配对讨论 → 全班分享
**来源语境：** 由 Frank Lyman (1981) 在美国开发；在英语国家教育体系（美、英、澳、加）中广泛采用
**目标语境：** 位于阿联酋的国际学校，学生来自 8 个以上文化背景
**总体评估：** 核心原则（在发言前给学生思考时间）迁移良好；具体实施携带了关于个人表达、同伴讨论规范以及公开分享的显著文化假设，在该多元语境中未必对所有学生成立。

### 识别出的文化假设

**假设 1：个人独立思考是最佳起点**
- **实践隐含的假设：** 处理问题的最佳方式是先“独自”思考。这赋予了内在的、个体化的认知作为意义建构首要方式的优先地位。
- **该假设成立的语境：** 在个人主义文化（广义西方文化，尤其是美国和北欧）中，独立思考被视为真实理解的基础。“独立思考”是一种文化规范。
- **可能不成立的语境：** 在集体主义文化（广义东亚、南亚、中东、非洲）中，思考往往是“关系性的”——意义通过对话涌现，而非先于对话存在。部分学生在与他人边说边想时思考得“更好”，而非更差。“独自思考”阶段可能会让习惯通过互动加工信息的学生感到焦虑。
- **证据：** Tobin, Wu & Davidson (1989) 表明，日本学前教育将“群体”而非“个体”视为思考的基本单位。Alexander (2001) 发现，俄罗斯和印度课堂将集体口头诵读与应答视为一种正当的思考形式——并非“死记硬背”，而是共同体认知加工。

**假设 2：同伴之间的结对讨论是自在且富有成效的**
- **实践隐含的假设：** 学生会与同伴进行开放、平等地位的讨论。这假定了同伴间水平方向的讨论是一种自然且舒适的沟通模式。
- **该假设成立的语境：** 在权力结构相对扁平的文化（美国、北欧国家、澳大利亚）中，同伴讨论是常见形式，学生习惯于向平等对象表达观点。
- **可能不成立的语境：** 在权威梯度更陡峭的文化（许多东亚、南亚及中东语境）中，学生可能更习惯垂直沟通——“向”教师发言或“回应”教师，而不是在同伴之间水平讨论。结对讨论可能让人感到别扭，并非因为学生做不到，而是因为它违背了他们对知识应如何流动的理解（从权威流向学习者，而非同伴之间）。此外，跨性别配对对于来自对话中有性别区隔规范文化的学生而言也可能造成不适。
- **证据：** Hofstede 的文化维度研究表明，不同文化间的权力距离存在显著差异。Alexander (2001) 发现，在印度课堂中，教师的声音是知识的主要载体——生生讨论较少且受重视程度较低。Stigler & Hiebert (1999) 表明，日本数学课堂采用由教师引导的全班讨论，而非同伴配对练习——教师编排的集体讨论比 think-pair-share 更具结构性。

**假设 3：公开分享个人想法是值得追求的**
- **实践隐含的假设：** 与全班分享个人想法是一种积极行为——它展现自信、服务集体学习，是学生应当追求的表现。该实践奖励公开的口头表达。
- **该假设成立的语境：** 在推崇个人表达和公开表现的文化（美国、英国）中，被请去分享是一种机会，主动发言的学生常受到表扬与奖励。
- **可能不成立的语境：** 在重视谦逊、群体和谐或顺从长辈的文化（许多东亚、部分中东、部分原住民文化）中，公开分享个人观点可能会令人不适。被单独点名发言——尤其是答案可能出错时——会导致丢面子。在一些文化中，“得体”的行为是等待被询问、尊重更有知识的人，并避免在群体中出风头。
- **证据：** Tobin, Wu & Davidson (1989) 发现，日本教育者认为美国儿童急于公开表现的行为是不成熟，而非自信。Castagno & Brayboy (2008) 指出，原住民学生可能将沉默作为一种尊重和深思熟虑的回应——而非不投入。在许多阿拉伯文化中，面对提问时的沉默可能意味着深度思考与尊重，而非无能或不情愿。

**假设 4：“正确”的产出形式是口头阐述**
- **实践隐含的假设：** 理解是通过“说出来”证明的。能说出来，就代表理解了；保持沉默，就可能代表没理解。
- **该假设成立的语境：** 在以口头表达为导向的文化（广义西方，尤其是英语文化）中，口头流利度常与认知能力划等号。
- **可能不成立的语境：** 在其他表达形式同样受到重视的文化中——书写、绘画、手势、演示、静心观察——沉默并不代表缺乏理解。Nsamenang (2006) 描述了非洲教育传统，其中理解是通过“做”来证明的，而不是通过口头解释。

### 调整建议

**调整 1：将“思考”改为“思考或讨论”**
- **原做法：** "Think on your own for 30 seconds."（强制个人静默思考）
- **调整后：** "Take 30 seconds to start processing this question — you can think silently, jot down a note, or quietly begin talking with a partner."（提供多种加工方式）
- **为何有效：** 消除了“个人静默思考是唯一有效起点”的假设。通过对话加工信息的学生可以开始交流，偏好静默的学生可以独立思考，两者同样正当。

**调整 2：在分享方式上提供选择**
- **原做法：** 抽选几对学生向全班口头分享。（要求公开口头表现）
- **调整后：** 结对讨论后提供多种分享选项："You can share with the class verbally, write your pair's idea on a whiteboard and hold it up, or write a sentence on a sticky note for the class display."（多种分享模式）
- **为何有效：** 不习惯公开口头表现的学生依然可以贡献思考。举起白板比站起来发言的暴露感更低；便签条的压力更小。学习目标（分享思考）得以保留，而文化假设（公开口头分享）被移除。

**调整 3：用三人组或四人小组替代两人配对**
- **原做法：** 同伴配对讨论。（一对一，若涉及跨性别或跨地位可能略显尴尬）
- **调整后：** 使用三人组或四人小组，允许学生自主选择在组内的参与位置。（共担责任，减轻个人压力）
- **为何有效：** 在三人组中，学生可以先倾听，准备好后再发言，而不必成为唯一的对话搭档。社交互动更具弹性——不必被迫向某一个特定的人表现。分组时也更容易兼顾性别与文化规范。

**调整 4：使用“写-结对-分享”或“画-结对-分享”**
- **原做法：** 思考（静默个人认知）→ 结对（口头）→ 分享（口头）
- **调整后：** 先写或画（个人或同伴）→ 讨论（结对或三人组）→ 分享（任意方式）
- **为何有效：** 对于不习惯立即口头讨论的学生，写和画是门槛更低的切入点。已经写下想法的学生手头有东西可以“展示”给同伴看，这比临场口头组织语言更容易。

### 来自其他传统的替代方案

**日本“练上（Neriage，揉炼/打磨式讨论）”：**
不同于 think-pair-share，教师先提出一个问题，学生独立或结对钻研。随后教师“刻意挑选”特定学生的解法与全班分享——但这种挑选是有策略的，旨在构建一个富有成效的观点序列，逐步推向深度理解。教师主持讨论并串联学生想法："Yuki found this approach. How does it compare to what Hiro did?" 这种方式比 think-pair-share 更具结构性，让教师掌握由谁分享、何时分享的主导权——既减少了随机被点的焦虑，又能呈现多元思维。（Stigler & Hiebert, 1999）

**非洲圆圈讨论（受乌班图 Ubuntu 哲学启发）：**
不是先个人思考再结对分享，而是全组围坐成圆圈，共同建构理解。教师提出问题，讨论沿圆圈流转——每个人都在前一人发言的基础上补充、延展或礼貌地提出不同视角。知识是共同建构的，而非个人独占。没有人被单独挑出聚光灯照射；每个人都作为流动讨论的一部分自然贡献。这尊重了集体主义沟通规范，也减轻了个人公开表现的压力。（改编自 Letseka, 2012; Venter, 2004）

**静默讨论（书面对话）：**
学生通过在一张共享纸张（或共享数字文档）上书写来回应问题。全程不说话——只书写。学生阅读彼此的文字并补充回应。这对不习惯口头讨论但想法丰富的学生极为有效，同时还能留下一份永久的讨论记录。这种方法渊源于贵格会（Quaker）教育实践，并已被广泛应用于多种多语和跨文化教学场景。

### 哪些部分迁移良好

think-pair-share 的“核心原则”跨文化迁移得非常好：
- **在期待回应之前给学生加工时间**——这具有普遍益处。问题不在于思考时间本身，而在于假定它必须是静默和孤立的。
- **减少能够“躲藏”不参与的学生数量**——配对/小组结构让每位学生都参与进来，而不仅仅是积极举手的人。这一原则跨文化成立。
- **让思维可见**——为了形成性评估而引出学生理解的目标具有普遍价值。问题在于“如何”让思维可见，而非“是否”应当让思维可见。

### 诚实说明

1. **本分析识别的是“可能的”文化假设，而非绝对定论。** 并非所有来自集体主义文化的学生都对 think-pair-share 感到不适，也并非所有来自个人主义文化的学生都对它感到自在。文化影响个体行为，但并不决定个体行为。教师必须观察“自己”课堂上的具体学生并据此调整。

2. **文化分析存在刻板印象的风险。** 说“南亚学生可能不习惯同伴讨论”是一种泛化，未必适用于这间教室里的具体南亚学生。分析只是观察的起点，而非结论。

3. **教师自身的文化假设同样在起作用。** 受英语国家教学法训练的教师，可能会无意识地将沉默解读为“不投入”，将口头发言解读为“投入”。这种解读本身就是特定文化的产物。最重要的调整或许在于教师对“参与度”的评估标准——认识到沉默同样可能意味着深度加工，而非缺席。

4. **目标语境（阿联酋的国际学校）本身就具有高度的文化复杂性。** 国际学校的学生往往早已在多种文化规范之间穿梭。部分学生可能非常适应西式讨论模式，另一些则不然。上述调整提供了跨越文化光谱的“选项”，而非假定所有学生需要同一种调整。

---

## 已知局限性

1. **本技能识别教育实践中的文化假设——但无法识别全部假设。** 文化复杂、多维且持续演变。本分析聚焦于文献记录最充分的维度（个人主义/集体主义、权力距离、沟通规范、知识传统），但无法穷尽所有相关文化因素。

2. **跨文化分析不能仅依赖 WEIRD 研究。** 本技能的证据基础借鉴了跨文化研究，但大多数教育研究仍以 WEIRD 为中心。来自其他传统的替代方法（练上、乌班图圆圈、静默讨论）基于现有文献描述，但在特定文化语境中工作的教师应当主动寻求“本地”教育专业智慧，而不仅仅依赖西方学术界关于这些语境的研究。

3. **文化适应与文化拓展之间存在张力。** 如果来自高权力距离文化的学生对同伴讨论感到不适，教师究竟应当调整任务（尊重既有文化规范），还是坚持任务（刻意让学生接触不同的文化规范）？这是一个没有放之四海而皆准答案的真实教学两难。本技能提供调整方案，但不能替教师解决这一张力——教师必须结合自身具体语境做出专业判断，理想情况下应与家庭及社区保持对话。
