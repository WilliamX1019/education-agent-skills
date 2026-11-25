---
# AGENT SKILLS STANDARD FIELDS (v2)
name: ecological-inquiry-anchor-designer
description: "设计锚定在当地生态系统中的探究序列，将科学或地理课程内容融入其中。适用于借助花园、池塘或树篱等当地生命系统开展教学时。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "environmental-experiential-learning/ecological-inquiry-anchor-designer"
skill_name: "生态探究锚点设计师"
domain: "environmental-experiential-learning"
version: "1.0"
evidence_strength: "moderate"
evidence_sources:
  - "Sobel (1996) — Beyond Ecophobia: reclaiming the heart in nature education"
  - "Sobel (2004) — Place-Based Education: connecting classrooms and communities"
  - "Orr (1992) — Ecological Literacy: education and the transition to a postmodern world"
  - "Kimmerer (2013) — Braiding Sweetgrass: Indigenous wisdom, scientific knowledge, and the teachings of plants"
  - "Chawla (1998) — Significant life experiences revisited: a review of research on sources of environmental sensitivity"
input_schema:
  required:
    - field: "local_ecosystem"
      type: "string"
      description: "作为探究锚点的具体当地生态系统或生命系统——花园、池塘、树篱、大树、一片荒地、窗台花箱"
    - field: "curriculum_objective"
      type: "string"
      description: "探究必须达成的科学或地理课程内容目标"
  optional:
    - field: "student_level"
      type: "string"
      description: "年龄/年级"
    - field: "time_frame"
      type: "string"
      description: "探究持续时间——单节课、一周、一学期、一年"
    - field: "school_grounds"
      type: "string"
      description: "学校拥有的户外或种植空间"
    - field: "community_expertise"
      type: "string"
      description: "当地专家——园艺师、生态学家、农场主、公园管理员"
    - field: "student_prior_experience"
      type: "string"
      description: "学生与自然及户外环境的既有关系"
output_schema:
  type: "object"
  fields:
    - field: "ecological_inquiry"
      type: "object"
      description: "完整的探究设计——锚定在具体当地生态系统中，通过直接生态调查达成课程目标"
    - field: "inquiry_question"
      type: "string"
      description: "从生态系统中自然生发并与课程相连的核心驱动问题"
    - field: "investigation_activities"
      type: "array"
      description: "学生做什么——直接观察、数据收集、长期监测、生态干预"
    - field: "ecological_literacy_outcomes"
      type: "object"
      description: "学生对生态系统的理解——超越课程目标的更深层生态素养"
    - field: "stewardship_dimension"
      type: "object"
      description: "探究如何引向对生态系统的照护——知识催生责任"
chains_well_with:
  - "outdoor-learning-sequence-designer"
  - "place-based-inquiry-anchor"
  - "phenomenon-based-unit-anchor"
  - "biophilic-learning-environment-designer"
  - "critical-thinking-task-designer"
teacher_time: "4 分钟"
tags: ["ecological-literacy", "Sobel", "Orr", "place-based", "environmental-education", "inquiry", "stewardship"]
---

# 生态探究锚点设计师

## 本技能的作用

设计一项锚定在具体当地生态系统——池塘、花园、树篱、大树甚至窗台花箱——中的持续性生态探究，将科学课程目标与对生命系统的直接调查联系起来，让学生能够长期观察、监测并照料这些系统。该方法借鉴了 Sobel (1996, 2004) 的地方本位教育（place-based education）及其对“生态恐惧症（ecophobia）”的批判（在儿童对当地自然产生热爱之前，就用全球环境灾难吓唬他们），以及 Orr (1992) 的生态素养概念（理解自然系统如何运作，而不仅仅是知道关于自然的事实）。核心原则在于：生态理解源自与特定生命系统的“关系”——对一个池塘的持续观察比阅读十个生物群系的资料更能教会学生生态学。输出包括探究设计、驱动问题、调查活动、生态素养成果（超越课程本身）以及让学生对所研究的生态系统承担起照护责任的守护维度。AI 在此尤为有价值，因为通过真实的生态调查来达成课程目标，需要将科学概念精准映射到特定当地生态系统所能揭示的现象上——确保生态学探究真实自然，而非生硬拼凑。

## 循证基础

Sobel (1996) 主张，环境教育应当始于对当地自然的“热爱”，而非对全球破坏的“恐惧”。他记录了在儿童尚未与当地自然建立情感纽带之前，过早接触环境灾难（雨林破坏、物种灭绝、气候变化）会如何催生“生态恐惧症”——焦虑、无力感与疏离，而非守护行动。他的建议是：4–7 岁探索家庭周边环境；8–11 岁探索当地社区及其生态系统；12–15 岁及以后再参与更广泛的社会与环境议题。从本地开始，从积极面开始，从建立关系开始。Sobel (2004) 将此延伸至地方本位教育，主张课程应当从当地环境中“生长出来”，而不是生硬地“套用到”环境上。Orr (1992) 将生态素养定义为理解自然系统如何维持生命——能量的流动、物质的循环、物种的相互依存以及生态系统的韧性。他认为生态文盲是最危险的无知形式，因为它使人类在不明白自己所作所为的情况下摧毁维持自身生存的系统。Kimmerer (2013) 从原住民（波塔瓦托米族）视角出发，描述了一种既科学又互惠的与生命世界的关系——向植物和生态系统学习与照料它们是密不可分的。Chawla (1998) 综述了关于“重要生活经历”的研究——即促使成年人关心环境的塑造性经历——发现最常见的因素是童年时期直接、长期的自然体验，而非环境教育课程或宣传活动。

## 输入模式

教师必须提供：
- **Local ecosystem（当地生态系统）：** 具体的生命系统。*例如："The school pond — about 2m × 3m, established 5 years ago, has frogspawn in spring, dragonflies in summer, some algae buildup" / "A large oak tree in the school grounds — estimated 150 years old, visible from our classroom window" / "Three raised beds in the school garden — currently growing herbs and vegetables" / "A patch of 'waste ground' behind the school fence — overgrown, wild, officially neglected but ecologically interesting"*
- **Curriculum objective（课程目标）：** 必须学习的内容。*例如："Year 4 Science: living things and their habitats — identify local habitats and the organisms that live there" / "Year 7 Science: ecosystems — food chains, food webs, interdependence" / "Year 8 Geography: ecosystems — how ecosystems function, human impact"*

可选（如上下文引擎可用则自动注入）：
- **Student level（学生水平）：** 年级
- **Time frame（时间跨度）：** 探究时长
- **School grounds（校园场地）：** 可用的户外空间
- **Community expertise（社区专业支持）：** 当地专家
- **Student prior experience（学生既有经验）：** 现有的自然连接

## Prompt

```
You are an expert in ecological education and place-based inquiry, with deep knowledge of Sobel's (1996, 2004) place-based education and ecophobia framework, Orr's (1992) ecological literacy, Kimmerer's (2013) reciprocal relationship with living systems, and Chawla's (1998) research on significant life experiences. You understand that ecological understanding is not a set of facts but a WAY OF SEEING — an ability to perceive the connections, dependencies, and cycles in living systems. This understanding comes from sustained relationship with specific ecosystems, not from textbook descriptions of generic biomes.

CRITICAL PRINCIPLES:
- **Start with love, not fear (Sobel, 1996).** Children need to fall in love with a specific pond, tree, or garden BEFORE they can meaningfully engage with abstract environmental issues. Don't begin with "ecosystems are under threat" — begin with "look at what lives in our pond."
- **The ecosystem is the teacher.** The curriculum objective is met THROUGH the ecosystem, not mapped onto it. If the objective is "food chains," the students don't learn about food chains and then look at the pond — they investigate the pond and discover the food chain that's actually there.
- **Long-term observation reveals what short visits cannot.** An ecosystem changes through seasons, through weather, through years. A single visit shows a snapshot; a term of weekly observations shows a living system. Design the inquiry for sustained engagement, not a one-off trip.
- **Reciprocity, not extraction (Kimmerer, 2013).** Students don't just TAKE knowledge from the ecosystem (observe, collect data, leave). They give back — through care, stewardship, and respect. The inquiry includes a stewardship dimension: what can we do FOR this ecosystem?
- **Every ecosystem is complex enough.** A school pond is not a "simple" ecosystem. It contains hundreds of species, multiple trophic levels, seasonal cycles, water chemistry, decomposition processes, and inter-species relationships. A single tree supports an entire community. Don't dismiss small or familiar ecosystems as educationally insufficient.

Your task is to design an ecological inquiry for:

**Local ecosystem:** {{local_ecosystem}}
**Curriculum objective:** {{curriculum_objective}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Student level:** {{student_level}} — if not provided, infer from the curriculum objective.
**Time frame:** {{time_frame}} — if not provided, design for a term-long inquiry with weekly observations.
**School grounds:** {{school_grounds}} — if not provided, use the described ecosystem.
**Community expertise:** {{community_expertise}} — if not provided, suggest who might help.
**Student prior experience:** {{student_prior_experience}} — if not provided, assume limited but not absent nature experience.

Return your output in this exact format:

## Ecological Inquiry: [Ecosystem] × [Curriculum Objective]

**Ecosystem:** [The specific local living system]
**Curriculum objective:** [What students must learn]
**Driving question:** [The question that emerges from the ecosystem and connects to the curriculum]

### Why This Ecosystem

[What makes this specific ecosystem educationally rich — what it can teach that a textbook cannot]

### Inquiry Design

**Phase 1 — Meeting the ecosystem**
[How students first encounter the ecosystem — observation, wonder, questions]

**Phase 2 — Investigating**
[What students investigate — specific activities, data collection, long-term monitoring]

**Phase 3 — Understanding**
[How students make sense of what they've found — connecting observations to ecological concepts]

**Phase 4 — Stewardship**
[How students give back — caring for the ecosystem based on what they've learned]

### Investigation Activities

[Detailed activities — what students do, what data they collect, what tools they use]

### Curriculum Connections

[How the inquiry addresses the specific curriculum objective — with evidence from the ecosystem itself]

### Ecological Literacy Outcomes

[What students understand about HOW ecosystems work — beyond the specific curriculum objective]

### Stewardship Plan

[Specific actions students take to care for the ecosystem — informed by their investigation]

**Self-check before returning output:** Verify that (a) the inquiry starts with love and wonder, not fear, (b) the ecosystem drives the inquiry rather than the curriculum being mapped onto it, (c) sustained observation is built in, (d) stewardship follows naturally from investigation, and (e) the curriculum objective is genuinely addressed through the ecological inquiry.
```

## 示例输出

**场景：** *Local ecosystem: "The school pond — about 2m × 3m, dug 5 years ago by a previous Year 6 class. It has pond plants (water lilies, iris, water mint), frogspawn appears in spring, dragonflies are seen in summer, there's a growing algae problem (green water), and we've noticed fewer frogs this year than last. It's in the school conservation area, which also has a log pile, a wildflower strip, and a bird feeder." / Curriculum objective: "Year 7 Science: ecosystems — food chains, food webs, interdependence, and the impact of changes to the ecosystem" / Time frame: "One term — approximately 12 weeks, with one session per week (plus the regular Science lessons where concepts are taught)"*

---

## 生态探究：学校池塘 × 生态系统与相互依存

**生态系统：** 学校池塘——2m × 3m，建成 5 年，已有水生植物、青蛙种群、藻类问题及生物多样性指标下降现象
**课程目标：** 七年级科学——食物链、食物网、相互依存以及生态系统变化的影响
**驱动问题：** "Our pond is going green and we're seeing fewer frogs. What's happening, and can we help?"

### 为什么选择这个生态系统

这个池塘就是一个微缩的完整生态系统。它包含：
- **生产者：** 藻类、水生植物（睡莲、鸢尾、水薄荷）
- **初级消费者：** 水蚤（Daphnia）、池塘蜗牛、蜉蝣幼虫、蚊子幼虫
- **次级消费者：** 蜻蜓幼虫、仰泳蝽、龙虱、蝾螈（如有）
- **三级消费者：** 青蛙（成体）、苍鹭（如有造访）
- **分解者：** 沉积物中的细菌、真菌

它存在一个真实的问题——藻类过度繁殖与青蛙数量减少——这是一个真正的生态谜题。藻类暴发可能源于营养物质富集（富营养化），例如落叶、土壤径流或此前投放饲料过量。青蛙数量减少可能与此相关（藻类降低溶氧量，使池塘不再宜居），也可能另有原因（周边栖息地丧失、捕食、疾病）。这不是一道课本练习题——这是一项学生能够找到真实答案的真实调查。

### 探究设计

**第 1 阶段——初遇池塘（第 1–2 周）**

*第 1 周：初次相遇。*
学生来到池塘边。不带写字板，不带练习纸。只是看。安静地坐在池塘边 10 分钟。然后提问："What did you notice? What did you see moving? What questions do you have?" 教师将问题记录在一张大纸上。

预期问题："Why is the water green?" "Where are the frogs?" "What's that bug on the surface?" "Is the pond dying?"

发绿的池水和消失的青蛙是天然的切入点——学生会立刻注意到它们。探究问题从观察中生发，而不是由教师强加。

*第 2 周：基线调查。*
学生开展生物多样性调查。使用捞网和物种识别图鉴采集无脊椎动物样本，识别物种（或物种类别），并记录发现。他们还记录：水色、水体清澈度（能否看到池底？）、植物覆盖率以及任何可见动物。这是后续衡量变化的基线。

**第 2 阶段——深入调查（第 3–8 周）**

*第 3 周：构建食物网。*
利用第 2 周发现的物种，学生构建“这个池塘”真实的食物网——不是课本上的食物网，而是基于他们亲眼观察结果的食物网。"We found Daphnia. What do Daphnia eat? (Algae.) What eats Daphnia? (Dragonfly larvae, fish if present.) What eats dragonfly larvae? (Frogs, birds.)" 食物网绘制在一块大型展板上，整个学期持续展示——它是一份动态更新的工作文档，随新物种的发现不断补充。

*第 4–5 周：藻类调查。*
驱动问题进一步聚焦："Why is our pond going green?" 学生设计并开展调查：
- 检测水质：pH 值、硝酸盐含量（使用简易试纸，水族店约 5 英镑）、水体清澈度（塞氏盘——学生可用系着绳子的配重白色圆盘自制）
- 对比：取一份池塘水样和一份学校自来水样。有什么不同？硝酸盐检测很可能会显示池塘中硝酸盐偏高（这是藻类生长的原因）
- 假设："If nitrates are high, what's producing them?" 学生调查：池塘中腐烂的落叶、邻近花坛的土壤径流、附近喂鸟器带来的鸟粪。每一项都是可检验的假设。

*第 6–7 周：青蛙问题。*
"Why are there fewer frogs?" 学生研究青蛙的生命周期和栖息地需求：青蛙繁殖需要洁净的水体（藻类会降低溶解氧）、长有植被的池岸用于隐蔽，以及周边栖息地用于觅食。学生评估：我们的池塘是否还能提供这些条件？原木堆提供了觅食栖息地。但藻类是否让水体变得不再适合蝌蚪生存？

*第 8 周：相互依存关系映射。*
学生回到他们的食物网。教师引入“相互依存（INTERDEPENDENCE）”的概念："If the algae takes over and covers the surface, what happens to the plants underneath? (They can't photosynthesise — they die.) If the plants die, what happens to the invertebrates that live in them? (They lose habitat.) If the invertebrates decline, what eats them? (The frogs.) So the algae problem might be CONNECTED to the frog problem." 学生沿着食物网追踪这种级联效应——通过“他们的”池塘，相互依存变得清晰可见。

**第 3 阶段——理解内化（第 9–10 周）**

学生综合他们的发现：
- 食物网展示了能量如何在池塘生态系统中流动
- 藻类调查展示了单一因素（营养水平）的变化如何级联影响整个系统
- 青蛙问题展示了行动中的相互依存——单一物种的健康取决于整个系统的健康
- “生态系统平衡”的概念变得具体可感：这个池塘刚挖好时是平衡的，而某种因素使其发生了偏移

学生为学校撰写一份《生态系统健康报告》——总结发现、解释科学原理并提出行动建议。

**第 4 阶段——生态守护（第 11–12 周）**

基于他们的调查，学生设计并实施一项干预措施：
- 如果问题是落叶：秋季安装池塘防护网，防止树叶落入
- 如果问题是径流：在花坛和池塘之间建立一条植物缓冲带
- 如果问题是营养积累：部分换水（抽走部分富含藻类的水并补充洁净水），并投放麦秸（barley straw，一种传统且有证据支持的抑藻方法）
- 长期机制：成立“池塘监测小组”，每月检测水质和物种——探究不会随着单元结束而终止

### 调查活动

| 周次 | 活动 | 学生做什么 | 收集的数据 |
|---|---|---|---|
| 1 | 静默观察 | 静坐、观察、记录问题 | 问题清单、初步素描 |
| 2 | 生物多样性调查 | 捞网采样、识别物种 | 物种清单、数量估算 |
| 3 | 构建食物网 | 研究摄食关系、绘制网络 | 实体食物网展板 |
| 4 | 水质检测 | 检测 pH、硝酸盐、清澈度 | 水质数据（定量） |
| 5 | 藻类来源调查 | 检验关于营养来源的假设 | 对比数据、观察记录 |
| 6 | 青蛙栖息地评估 | 评估繁殖与觅食栖息地 | 栖息地核查表、状况评级 |
| 7 | 与健康池塘对比 | 研究或探访对比地点 | 物种/水质对比数据 |
| 8 | 相互依存映射 | 在食物网中追踪级联效应 | 带影响箭头的标注食物网 |
| 9–10 | 生态系统健康报告 | 综合整理并撰写 | 附带证据的书面报告 |
| 11–12 | 守护干预 | 规划并实施改善行动 | 行动计划、前后对比数据方案 |

### 课程关联

| 课程目标 | 池塘探究如何落实 |
|---|---|
| 食物链 | 学生利用在“自己”池塘中发现的物种构建真实食物链 |
| 食物网 | 完整食物网基于观察到的生物体构建，而非课本示例 |
| 相互依存 | 藻类与青蛙之间的关联展示了生命系统中的级联效应 |
| 变化的影响 | 藻类暴发本身就是对生态系统的改变——学生调查其成因与后果 |
| 人类影响 | 学生发现人类活动（花坛径流、喂鸟器位置）可能造成了问题——而人类守护也能加以改善 |

### 生态素养成果

超越具体课程目标之外，学生还将发展：
1. **系统思维。** 池塘不是单个生物的集合——它是一个万事万物相互连接的“系统”。改变一个要素会以并不总是显而易见的方式影响其他要素。
2. **季节意识。** 通过每周探访，学生注意到池塘在整个学期中不断变化——物种出现又消失，植物生长又枯萎，水位升降。生态系统是动态的，而非静止的。
3. **生态互惠。** 学生“向”池塘学习，并“回馈”池塘。这就是 Kimmerer 的原则：知识催生责任。理解池塘生态的学生更有动力去照料它。
4. **长期观察的价值。** 单次探访只是一张快照；十二周则是一个故事。学生体会到生态理解需要耐心与持续观察。

### 守护计划

学生基于证据设计干预措施：
1. **确定原因。** 调查结果决定藻类是由营养径流、落叶还是其他因素引起的。
2. **研究解决方案。** 针对每种成因，研究生态适宜的干预方式（非化学手段——而是生物与结构手段）。
3. **实施。** 在教师和校园管理员的支持下开展干预。
4. **监测。** 建立持续监测机制：每月水质检测、每学期物种调查。下一届七年级将继续监测，并将他们的数据与今年的基线进行对比。池塘成为一个长期的生态研究基地。

---

## 已知局限性

1. **生态探究需要接触真实生态系统。** 没有池塘、花园或可达自然区域的学校面临实际限制。然而，Sobel 的原则是：任何生命系统——哪怕是一个窗台花箱、一个堆肥箱，或是操场裂缝里长出的一小片草——在生态复杂性上都足以支持调查。探究规模可以根据手头可用的生态系统灵活调整。

2. **生态教育的证据基础主要为质性研究。** Chawla (1998) 和 Sobel (1996, 2004) 依托质性研究传统——重要生活经历叙事、案例研究和实践者记录。证明生态探究能够提升科学测试成绩的随机对照试验（RCT）或大规模定量研究相对较少。关于参与度、环境意识和守护行为的证据，强于关于科学考试成绩的证据。

3. **长期探究需要制度支持。** 为期一学期的每周调查需要课表时间保障、全天候的户外准入以及学校领导层的支持。如果一遇到下雨或场地泥泞就取消探究，持续观察的原则就会受到破坏。教师需要积极争取使生态探究成为可能的时间与条件。
