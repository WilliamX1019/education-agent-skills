---
# AGENT SKILLS STANDARD FIELDS (v2)
name: experiential-learning-cycle-designer
description: "将直接体验构建为包含具体体验、反思与概念迁移的完整学习循环。适用于规划实地考察、模拟活动或实践任务时。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "environmental-experiential-learning/experiential-learning-cycle-designer"
skill_name: "体验式学习循环设计师"
domain: "environmental-experiential-learning"
version: "1.0"
evidence_strength: "moderate"
evidence_sources:
  - "Hattie (2009) — Visible Learning: simulation and gaming effect size d=0.33"
  - "Billig (2000) — Research on K-12 school-based service learning: the evidence builds"
  - "Dewey (1938) — Experience and Education"
  - "Boud, Keogh & Walker (1985) — Reflection: turning experience into learning"
  - "Wurdinger & Carlson (2010) — Teaching for Experiential Learning: five approaches that work"
input_schema:
  required:
    - field: "learning_objective"
      type: "string"
      description: "学生需要发展的具体知识、技能或理解"
    - field: "experience_type"
      type: "string"
      description: "可用的直接体验类型——模拟、角色扮演、实地考察、社区项目、实践任务、实验"
  optional:
    - field: "student_level"
      type: "string"
      description: "年龄/年级"
    - field: "subject_area"
      type: "string"
      description: "课程学科"
    - field: "time_available"
      type: "string"
      description: "完整循环可用时间——单节课、多节课、一周"
    - field: "resources_available"
      type: "string"
      description: "可用于该体验的资源、材料或场地"
    - field: "prior_knowledge"
      type: "string"
      description: "学生已经知道的内容——决定循环中重点落在哪一环节"
output_schema:
  type: "object"
  fields:
    - field: "experiential_cycle"
      type: "object"
      description: "四阶段学习循环：体验 → 反思 → 概念化 → 应用"
    - field: "experience_design"
      type: "object"
      description: "直接体验——学生做什么、看什么、感受什么、遇到什么"
    - field: "reflection_design"
      type: "object"
      description: "学生如何处理体验——提炼学习成果的结构化反思"
    - field: "conceptualisation_design"
      type: "object"
      description: "学生如何将体验与理论、原理或可迁移知识联系起来"
    - field: "application_design"
      type: "object"
      description: "学生如何将所学应用到新情境中——通过行动检验理解"
chains_well_with:
  - "service-learning-project-designer"
  - "outdoor-learning-sequence-designer"
  - "reflective-practice-prompt-generator"
  - "agency-scaffold-generator"
teacher_time: "4 分钟"
tags: ["experiential-learning", "simulation", "service-learning", "Dewey", "reflection", "direct-experience"]
---

# 体验式学习循环设计师

## 本技能的作用

设计一个四阶段体验式学习循环，带领学生从直接体验出发，经过结构化反思，走向概念理解，再进入新情境中的应用。该循环借鉴了 Dewey (1938) 的核心原则：教育是对经验的改造——学习并非来自经验本身，而是来自对经验的“反思”以及将其与更广泛理解的联结。本技能刻意设计每一个阶段：体验必须真正吸引人且与教育相关（而不仅仅是“好玩”），反思必须结构化（而不仅仅是“感觉怎么样？”），概念化必须将体验与可迁移的原理相连，应用则必须在新情境中检验理解。输出包括完整的四阶段循环，附带每个阶段的详细设计以及阶段之间的过渡衔接。AI 在此尤为有价值，因为设计有效的体验式学习需要在参与度（体验必须引人入胜）与严谨性（必须产生真正的学习，而不仅仅是愉快的活动）之间取得平衡。

## 循证基础

Dewey (1938) 确立了基本原则：经验本身并不具有教育意义。“反教育（mis-educative）”的经验——即那些不产生学习、强化错误观念或阻碍进一步成长的经验——与有教育意义的经验同样常见。区别在于经验是否与反思、概念化和未来应用相连。Hattie (2009) 报告称，模拟与游戏作为教学策略的效应量为 d=0.33——这是一个中等正向效应，表明模拟在设计良好时有效，但并非灵丹妙药。当模拟包含结构化复盘（反思）以及与学习目标的明确联结（概念化）时，效应最强。Billig (2000) 综述了服务性学习研究，发现其对学业成就、公民责任和个人发展具有中等正向效应——但“仅当”服务体验通过结构化反思与课程内容相连时才成立。没有反思的服务能带来社区收益，但不能带来学习。Boud, Keogh & Walker (1985) 开发了一个从经验中进行反思性学习的详细模型，提出反思包括：回到经验（发生了什么？）、关注感受（我有什么感受？）以及重新评估经验（这意味着什么？）。没有这一结构化过程，经验只会停留在轶事层面，而无法转化为学习。Wurdinger & Carlson (2010) 记录了五种能产生学习的体验式方法：主动学习、基于问题的学习、基于项目的学习、服务性学习和地方本位学习——它们都共享“体验 → 反思 → 概念化 → 应用”的共同结构。

## 输入模式

教师必须提供：
- **Learning objective（学习目标）：** 学生需要学习的内容。*例如："Understanding supply and demand — Year 10 Economics" / "Empathy and perspective-taking — Year 8 PSHE" / "The water cycle — Year 5 Science" / "How Parliament works — Year 9 Citizenship"*
- **Experience type（体验类型）：** 可用的体验形式。*例如："Simulation — we can run a classroom marketplace where students buy and sell" / "Role play — students can take on roles in a mock Parliament" / "Field trip — we're visiting a water treatment plant next week" / "Community project — students are planning a fundraising event for a local charity"*

可选（如上下文引擎可用则自动注入）：
- **Student level（学生水平）：** 年级
- **Subject area（学科领域）：** 课程学科
- **Time available（可用时间）：** 完整循环的时长
- **Resources available（可用资源）：** 现有的材料或场地
- **Prior knowledge（先验知识）：** 学生已经知道的内容

## Prompt

```
You are an expert in experiential learning design, with deep knowledge of Dewey's (1938) philosophy of experience and education, Hattie's (2009) evidence on simulation and gaming, Billig's (2000) research on service learning, Boud, Keogh & Walker's (1985) model of reflective learning, and Wurdinger & Carlson's (2010) five experiential approaches. You understand that experiential learning is NOT "learning by doing" in the vague sense — it is a rigorous four-phase cycle where each phase serves a specific pedagogical function, and the learning happens in the REFLECTION and CONCEPTUALISATION, not in the experience itself.

CRITICAL PRINCIPLES:
- **Experience without reflection is just activity.** Dewey was explicit: not all experience is educative. A simulation that students enjoy but don't reflect on produces entertainment, not learning. A field trip without structured follow-up produces memories, not understanding. The REFLECTION PHASE is where learning happens — design it with as much care as the experience itself.
- **Reflection must be structured, not generic.** "How did that go?" is not reflection. "What happened when you raised the price? How did the buyers respond? Why do you think that happened? What principle does this illustrate?" is structured reflection that extracts learning from experience.
- **Conceptualisation connects the specific to the general.** The experience is specific (THIS simulation, THIS field trip). The learning must be general (the principle of supply and demand, the process of water purification). Conceptualisation explicitly bridges: "In our simulation, X happened. In the real economy, the same principle applies — here's how."
- **Application tests transfer.** If students can only explain what happened in the simulation but cannot apply the principle to a new situation, they learned the simulation, not the concept. The application phase provides a new context where students must use their learning.
- **Design the experience for learning, not just engagement.** A marketplace simulation where students have fun but the supply-demand dynamics are invisible has failed. The experience must be designed so that the target concept is EMBEDDED in the experience — students encounter it through doing, even if they don't yet have the language for it.

Your task is to design an experiential learning cycle for:

**Learning objective:** {{learning_objective}}
**Experience type:** {{experience_type}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Student level:** {{student_level}} — if not provided, infer from the learning objective.
**Subject area:** {{subject_area}} — if not provided, infer from the learning objective.
**Time available:** {{time_available}} — if not provided, design for a 2-lesson sequence (one for experience, one for reflection and conceptualisation, with application as homework or a third lesson).
**Resources available:** {{resources_available}} — if not provided, design with minimal resources.
**Prior knowledge:** {{prior_knowledge}} — if not provided, design the experience to introduce the concept rather than reinforce it.

Return your output in this exact format:

## Experiential Learning Cycle: [Learning Objective]

**Learning objective:** [What students will understand]
**Experience:** [The type of direct experience]
**Key concept embedded in experience:** [The specific principle or understanding that the experience makes tangible]

### Phase 1 — Experience (Concrete Experience)

**The experience:** [What students do — detailed, step-by-step]
**What makes this experience educative:** [How the learning objective is embedded in the activity — what students encounter through doing]
**Teacher role during experience:** [What the teacher does — facilitates, observes, takes notes for the reflection phase]

### Phase 2 — Reflection (Reflective Observation)

**Structured reflection questions:** [Specific questions that extract learning from the experience — not "how did it go?" but targeted questions about what happened and why]
**Reflection format:** [How reflection is structured — whole-class discussion, written journal, paired dialogue, recorded observations]
**Key moments to revisit:** [Specific moments from the experience that the teacher draws attention to — "Remember when X happened? Why do you think that occurred?"]

### Phase 3 — Conceptualisation (Abstract Conceptualisation)

**From experience to principle:** [How the teacher helps students move from "what happened in our activity" to "what this tells us about [the concept]"]
**Theory/principle introduced:** [The formal knowledge that explains what students experienced]
**Connection made explicit:** [How the teacher links the experience directly to the theory — "In our simulation, you experienced X. The economic term for this is Y. It happens in real life when Z."]

### Phase 4 — Application (Active Experimentation)

**New context:** [A different situation where students apply the principle they've learned]
**Application task:** [What students do to test their understanding in this new context]
**How to know it worked:** [Evidence that students can transfer the learning beyond the original experience]

### Transitions Between Phases

[How to move smoothly from each phase to the next — the "glue" that makes the cycle coherent]

**Self-check before returning output:** Verify that (a) the experience genuinely embeds the learning objective, (b) the reflection is structured with specific questions, (c) the conceptualisation explicitly connects experience to transferable principle, (d) the application tests transfer to a new context, and (e) each phase serves a distinct pedagogical function.
```

## 示例输出

**场景：** *Learning objective: "Understanding supply and demand — Year 10 Economics. Students need to understand: when supply is limited and demand is high, prices rise; when supply exceeds demand, prices fall; and that this mechanism operates through the independent decisions of buyers and sellers, not through central planning." / Experience type: "Simulation — classroom marketplace where students buy and sell goods" / Time available: "2 lessons (50 minutes each)" / Prior knowledge: "Students have not yet studied supply and demand formally — this is their introduction to the concept"*

---

## 体验式学习循环：供给与需求

**学习目标：** 理解供求价格机制——价格如何从买卖双方的独立决策中自发形成
**体验：** 课堂市场模拟
**嵌入体验的核心概念：** 当许多买方想要一种稀缺商品时，价格上涨；当商品充裕而买方稀少时，价格下跌。这一过程无需任何人决定“价格应该是 X”，而是从互动中自发涌现。

### 第 1 阶段——体验（具体体验，第 1 课时：40 分钟）

**体验过程：**

*准备（10 分钟）：*
将全班分为买方（15 人）和卖方（15 人）。每位卖方获得 5 张代表“商品”的卡片（彩色卡片——无需复杂道具）。每位买方获得一笔课堂货币“预算”（纸质代币——每人 10 枚）。

**第 1 轮——稀缺：** 每位卖方只有 2 件商品可售。每位买方想买 3 件商品。（需求大于供给。）卖方自行定价。买方与卖方单独议价。开放交易——所有人在教室内自由走动，同时议价。限时 5 分钟。结束时，将所有成交价格记录在黑板上。

**第 2 轮——过剩：** 现在每位卖方有 8 件商品可售。每位买方仍然只想买 3 件商品。（供给大于需求。）规则相同——卖方定价、自由交易。5 分钟。记录所有成交价格。

**第 3 轮——市场冲击：** 本轮进行到一半时，教师宣布：“突发新闻——政府宣布这些商品现在是即将到来的考试的必备品。每人至少需要 5 件。”（需求激增。）观察价格发生什么变化。5 分钟。记录价格。

*使这一体验具有教育意义的设计：*
- 在第 1 轮，学生亲身“体验”价格上涨——卖方发现自己可以开高价，因为买方正在争夺稀缺商品。价格机制不是靠讲解，而是靠亲身遭遇。
- 在第 2 轮，学生亲身“体验”价格下跌——卖方发现自己必须降价，因为买方有很多选择。拒绝降价的卖方卖不出去。
- 在第 3 轮，学生亲身“体验”需求冲击——原本低迷的价格在需求骤增时突然飙升。市场动态变得可见、可感。

**体验期间教师的角色：** 不要解释正在发生什么。巡视、观察并记笔记：哪些卖方提高了价格？哪些买方转身离开？当供给增加时价格发生了什么变化？这些观察记录将为反思阶段提供素材。如果学生抱怨价格“不公平”，记下这一点——它在教学上非常有价值。

### 第 2 阶段——反思（反思性观察，第 1 课时：10 分钟 + 第 2 课时：15 分钟）

**第 1 课时结束——快速捕捉（10 分钟）：**
在体验记忆消退前，捕捉即时反思：
- "What happened to prices in Round 1? Were they high or low? Why?"
- "What happened in Round 2? Why did prices change?"
- "When I announced the demand shock in Round 3, what did Sellers do? Why?"
- "Did anyone decide what the 'correct' price should be, or did it just... happen?"

将关键观察记录在黑板上。暂时不要解释——只做收集。

**第 2 课时开始——结构化反思（15 分钟）：**
将三轮的成交价格数据绘制在图表上（纵轴为价格，横轴为轮次）。学生看到规律：第 1 轮价格高、第 2 轮价格低、第 3 轮价格飙升。

结构化反思问题：
1. "In Round 1, why were Sellers able to charge high prices? What was their power?"（他们拥有买方想要且别处买不到的东西——稀缺性。）
2. "In Round 2, why did prices fall even though no one TOLD Sellers to lower their prices?"（买方有选择权。要价过高的卖方没有顾客。竞争迫使价格下降。）
3. "Did any Buyers feel frustrated in Round 1? Did any Sellers feel frustrated in Round 2? Why?"（这引出了情感维度——对市场支配力与市场脆弱性的体验。）
4. "Who decided the prices? Was there a central authority?"（没有人决定。价格从成百上千次个人谈判中自发形成。这是核心洞察。）
5. "In Round 3, the same goods suddenly became more valuable. Did the goods themselves change? What changed?"（商品本身没有变——“需求”变了。价值并非商品固有属性，而是取决于人们有多想要它。）

### 第 3 阶段——概念化（抽象概念化，第 2 课时：20 分钟）

**从体验到原理：**
"What you just experienced has a name in economics. Let me introduce the language for what you already KNOW."

教师引入：
- **供给（Supply）：** 卖方在给定价格下愿意出售的商品数量。第 1 轮中，供给低（每位卖方 2 件）。第 2 轮中，供给高（每位卖方 8 件）。
- **需求（Demand）：** 买方在给定价格下想要购买的商品数量。第 1 轮和第 2 轮中，需求适中。第 3 轮中，需求激增。
- **价格机制（Price mechanism）：** 价格通过调整来平衡供给与需求。没有人人为决定——它从买卖双方的互动中自发涌现。
- **供给曲线与需求曲线：** 教师画出经典示意图。"Remember Round 1? That's here on the graph — low supply, high demand, price is here. Round 2? Here — high supply, same demand, price drops. Round 3? Here — demand curve shifts right, price jumps."

**明确建立联结：** "In our simulation, you charged high prices when your goods were scarce. In the real economy, the same principle explains why concert tickets cost more when the band is popular, why house prices rise when many people want to live in an area, and why petrol prices spike when oil supply is disrupted. The mechanism is the same — you've already experienced it."

### 第 4 阶段——应用（主动实验，第 2 课时：15 分钟）

**新情境：** 学生将供求分析应用到一个他们“没有”亲身体验过的现实情境中：

"Read this news article: 'House prices in [local area] rise by 15% as new tech company opens headquarters.' Using what you learned from the marketplace simulation, explain: Why did house prices rise? Draw a supply-demand diagram. What would happen to house prices if the tech company then built 500 new homes for its workers?"

**应用任务：** 学生使用经济学术语（supply、demand、price mechanism、scarcity、surplus）写一段解释，并绘制一幅标注清晰的供求曲线图。他们必须将现实情境与自己在模拟中体验到的原理联系起来。

**如何判断有效：** 能够用供求分析解释房价情境的学生，已经将所学从模拟迁移到了新情境中。只能描述模拟中发生了什么、却无法将该原理应用于房价情境的学生，只学会了“活动本身”，而未掌握“概念”——他们需要在概念化和应用阶段获得更多练习。

### 阶段之间的过渡衔接

**体验 → 反思：** 过渡桥梁是价格数据。把成交价格记录在黑板上，创造了一个所有人都能看到的“共享数据集”。这份数据就是反思的原材料："Look at the data. What pattern do you see?"

**反思 → 概念化：** 过渡桥梁是这句话："What you noticed has a name in economics." 学生已经用自己的话阐述了核心洞察（"prices went up because everyone wanted them"）。教师此时引入正式词汇，为他们已经理解的内容命名。

**概念化 → 应用：** 过渡桥梁是挑战："Can you use this principle to explain something you HAVEN'T experienced?" 这检验学习是否已从特定情境（我们的模拟）走向一般规律（供求原理）。

---

## 已知局限性

1. **Kolb (1984) 的体验式学习循环虽然被广泛引用，但存在显著的理论与实证局限性。** 本技能采用四阶段循环结构（体验 → 反思 → 概念化 → 应用），但并不将其标榜为 Kolb 的专属模型。Kolb 的理论曾受到以下批评：(a) 实证验证薄弱——该循环在直觉上很吸引人，但尚未经过严格检验；(b) 文化偏见——该循环假定了一种以个人经验为起点的西方个人主义学习模式；(c) 其中的“学习风格”部分（Kolb 学习风格量表）已被反复证伪（Coffield et al., 2004）；(d) 该循环暗示了固定顺序，而实践中学习者可能从任何一点切入。本技能将四阶段结构用作一种实用的规划框架，立足于 Dewey (1938) 与 Boud 等 (1985)，而非专门依托 Kolb。

2. **模拟会简化现实。** 课堂市场只是对供求关系的模拟，并非真实市场。真实市场涉及信息不对称、外部性、政府管制、垄断势力、行为偏差以及课堂模拟无法复制的历史背景。模拟教授的是基础机制——但应明确告诉学生："The real economy is more complex than our simulation. What we've learned is the foundation — the principle that supply and demand affect prices. In the coming weeks, we'll add the complications."

3. **基于模拟的学习效应量为中等（Hattie, d=0.33）。** 这是一个正向但并不算大的效应，且高度依赖于复盘质量。没有结构化反思的模拟，其学习效果始终弱于包含结构化反思的模拟。反思阶段不是可选项——它正是学习发生的地方。一场精彩有趣的模拟之后如果只说一句“好了，刚才挺好玩的，现在打开课本”，就白白浪费了体验式学习的契机。
