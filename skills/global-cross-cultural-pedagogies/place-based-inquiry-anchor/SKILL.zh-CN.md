---
# AGENT SKILLS STANDARD FIELDS (v2)
name: place-based-inquiry-anchor
description: "将课程学习锚定在特定当地场所，并与社区、文化和身份认同建立联结。适用于将学术内容与学生的本地环境及文化遗产相联系时。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "global-cross-cultural-pedagogies/place-based-inquiry-anchor"
skill_name: "地方本位探究锚点设计器"
domain: "global-cross-cultural-pedagogies"
version: "1.0"
evidence_strength: "moderate"
evidence_sources:
  - "Castagno & Brayboy (2008) — Culturally responsive schooling for Indigenous youth: a review of the literature"
  - "Gruenewald (2003) — The best of both worlds: a critical pedagogy of place"
  - "Sobel (2004) — Place-Based Education: connecting classrooms and communities"
  - "Smith (2002) — Place-based education: learning to be where we are"
  - "Bang, Medin & Atran (2007) — Cultural mosaics and mental models of nature"
input_schema:
  required:
    - field: "curriculum_content"
      type: "string"
      description: "需要教授的学术内容或技能"
    - field: "local_place"
      type: "string"
      description: "作为探究锚点的具体场所——当地河流、公园、街区、建筑或地貌特征"
  optional:
    - field: "student_level"
      type: "string"
      description: "年龄/年级"
    - field: "subject_area"
      type: "string"
      description: "课程学科"
    - field: "indigenous_connections"
      type: "string"
      description: "该当地场所是否具有原住民历史或文化意义"
    - field: "community_knowledge_holders"
      type: "string"
      description: "社区中对该场所拥有深厚知识的人——农民、历史学家、长者、环保团体"
    - field: "access_constraints"
      type: "string"
      description: "学生是否可以实地探访该场所，还是必须在教室内开展探究"
output_schema:
  type: "object"
  fields:
    - field: "place_based_inquiry"
      type: "object"
      description: "完整的探究设计——锚定在特定当地场所中，将学术内容与地方本位知识相连"
    - field: "place_knowledge"
      type: "object"
      description: "该场所本身教会了什么——直接接触这一特定地点所能学到的内容"
    - field: "multiple_knowledge_systems"
      type: "object"
      description: "探究如何尊重认识该场所的多种方式——科学的、历史的、文化的、原住民的、体验式的"
    - field: "action_dimension"
      type: "object"
      description: "探究如何引向与该场所相关的负责任行动——守护、倡导或服务"
chains_well_with:
  - "culturally-responsive-teaching-designer"
  - "ubuntu-collective-knowledge-task-designer"
  - "phenomenon-based-unit-anchor"
  - "awe-wonder-experience-designer"
teacher_time: "4 分钟"
tags: ["place-based", "Indigenous-education", "Castagno-Brayboy", "Gruenewald", "local", "land", "stewardship", "decolonising"]
---

# 地方本位探究锚点设计器

## 本技能的作用

设计一项锚定在特定当地场所的探究——将该场所本身作为第一手文本与教学资源，将学术课程与直接接触当地地貌、社区和环境所能学到的知识联系起来。该方法借鉴了地方本位教育（Sobel, 2004; Smith, 2002）、批判性地方教学法（Gruenewald, 2003）以及原住民教育研究（Castagno & Brayboy, 2008; Bang, Medin & Atran, 2007）。核心洞察在于：场所不仅仅是学习发生的地点——它们本身就是知识的源泉。一条当地河流同时教授生态学、化学、地理学、历史学与公民责任；一个街区同时教授经济学、社会学、建筑学与社区意识。地方本位探究尊重认识一个场所的多种方式——科学观察、历史研究、文化记忆、原住民知识以及直接感官体验——将它们视为互补，而非等级高低。输出包括锚定在特定场所的探究设计、对该场所教学价值的识别、尊重多元知识体系的框架，以及让学生对自身与该场所的关系承担责任的行动维度。AI 在此尤为有价值，因为将课程标准连接到特定当地场所，需要把学术内容映射到地方本位的机会上——这项工作受益于横跨课程与地方地理的广博知识。

## 循证基础

Castagno & Brayboy (2008) 综述了针对原住民青少年的文化响应型学校教育文献，发现面向原住民学生的有效教育将“场所（PLACE）”与“土地（LAND）”置于学习的核心。在原住民认识论中，知识不是抽象且可随意抽离的——它植根于与特定场所的关系之中，理解土地与理解自我密不可分。尽管该研究聚焦于原住民语境，但“场所是知识之源”这一原则对所有学生都具有启示。Gruenewald (2003) 提出了“批判性地方教学法（critical pedagogy of place）”，将批判教学法（审视权力、公平与社会结构）与地方本位教育（通过本地参与学习）相结合。他主张教育应当帮助学生既“栖居（INHABIT）”于自己的场所（与当地环境建立深厚、关怀的关系），又“去殖民化（DECOLONISE）”这些场所（批判性审视场所如何被殖民、经济和政治力量所塑造）。Sobel (2004) 记录了美国各地的地方本位教育项目，表明通过当地场所学习的学生比传统教室里的学生展现出更高的学业成就、更强的社区联结以及更强烈的环境守护意识。Smith (2002) 将地方本位学习方法分为五类：文化研究（地方历史、传统、艺术）、自然研究（地方生态、环境科学）、现实问题解决（调查地方议题）、实习与创业（社区参与）以及融入社区进程（公民参与）。Bang, Medin & Atran (2007) 证明，通过文化情境化、地方本位方式学习的原住民儿童，比通过标准西方科学课程学习生态学的儿童发展出了更复杂且更准确的生态理解——表明原住民认识自然的方式在认识论上是丰富的，而非匮乏的。

## 输入模式

教师必须提供：
- **Curriculum content（课程内容）：** 学生需要学什么。*例如："Ecosystems and food chains — Year 7 Science" / "Local history — Year 8 History, how our area has changed" / "Data collection and analysis — Year 6 Mathematics" / "Geographical fieldwork — Year 9 Geography, physical and human geography of a local area"*
- **Local place（当地场所）：** 具体场所。*例如："The canal that runs behind our school — it was built in the 1790s, fell into disuse, and was recently restored by a community trust" / "The park at the end of our road — an old Victorian park with mature trees, used by many different community groups" / "The high street — a mix of independent shops, chain stores, and empty units, reflecting economic change in our town"*

可选（如上下文引擎可用则自动注入）：
- **Student level（学生水平）：** 年级
- **Subject area（学科领域）：** 课程学科
- **Indigenous connections（原住民联结）：** 该场所是否具有原住民文化意义
- **Community knowledge holders（社区知识持有者）：** 深谙该场所的人
- **Access constraints（准入限制）：** 学生能否实地探访

## Prompt

```
You are an expert in place-based education, with deep knowledge of Castagno & Brayboy's (2008) research on culturally responsive schooling for Indigenous youth, Gruenewald's (2003) critical pedagogy of place, Sobel's (2004) place-based education framework, Smith's (2002) categories of place-based learning, and Bang, Medin & Atran's (2007) research on Indigenous ecological knowledge. You understand that places are not passive backdrops for learning — they are active sources of knowledge. A place teaches through its ecology, its history, its communities, its changes, and its stories. Place-based education reads the place as a primary text.

CRITICAL PRINCIPLES:
- **The place is the text.** The starting point is not the curriculum but the PLACE. What does this specific place teach? What can be learned from direct engagement with it? The curriculum content is then mapped onto what the place offers — not the other way around. The place determines the questions; the curriculum provides the tools for answering them.
- **Multiple ways of knowing.** A scientist knows a river through water chemistry and species counts. A historian knows it through the stories of who built the canal and why. An elder knows it through decades of memory and change. An Indigenous knowledge holder may know it through relationships with the land that predate colonial settlement. Place-based inquiry honours ALL these ways of knowing as legitimate and complementary.
- **Direct experience is primary.** Students should engage with the place directly — visit it, observe it, touch it, listen to it — wherever possible. If physical access is not possible, bring the place into the classroom through photographs, sound recordings, soil samples, water samples, maps, and testimony from people who know it. But no substitute fully replaces direct experience.
- **Critical engagement, not just appreciation.** Following Gruenewald, place-based education is not just "nature appreciation" or "local pride." It includes critical analysis: Who owns this land? How did they come to own it? Whose stories are told about this place, and whose are erased? What economic forces shape it? What environmental damage has been done, and by whom?
- **Responsibility follows knowledge.** If students learn deeply about a place, they develop a relationship with it. The inquiry should include an action dimension — stewardship, advocacy, or service — that grows naturally from the learning.

Your task is to design a place-based inquiry for:

**Curriculum content:** {{curriculum_content}}
**Local place:** {{local_place}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Student level:** {{student_level}} — if not provided, design for lower secondary.
**Subject area:** {{subject_area}} — if not provided, infer from the curriculum content.
**Indigenous connections:** {{indigenous_connections}} — if not provided, include a note about investigating the pre-colonial history of the place.
**Community knowledge holders:** {{community_knowledge_holders}} — if not provided, suggest who might hold knowledge of this place.
**Access constraints:** {{access_constraints}} — if not provided, design for a visit to the place.

Return your output in this exact format:

## Place-Based Inquiry: [Place] × [Curriculum Content]

**Place:** [The specific local place]
**Curriculum content:** [What academic knowledge and skills students develop]
**Driving question:** [A question that emerges from the place itself]

### What This Place Teaches

[What can be learned from direct engagement with this specific place — its ecology, history, community, changes, stories]

### Multiple Ways of Knowing

[How different knowledge systems illuminate the place — scientific, historical, cultural, experiential, and where appropriate, Indigenous]

### Inquiry Design

**Phase 1 — Encounter the place**
[How students first engage with the place — direct experience, observation, sensory engagement]

**Phase 2 — Question the place**
[What questions the place raises — prompted by what students observe, wonder, and notice]

**Phase 3 — Investigate**
[How students use academic tools (from the curriculum content) to answer their questions — fieldwork, research, data collection]

**Phase 4 — Integrate and share**
[How students bring together what they've learned from multiple sources and share it]

### Action Dimension

[How the inquiry leads to responsible action — stewardship, advocacy, or service in relation to the place]

### Community Knowledge Holders

[Who in the community holds knowledge about this place, and how they might contribute to the inquiry]

**Self-check before returning output:** Verify that (a) the place drives the inquiry, not the curriculum alone, (b) multiple ways of knowing are honoured, (c) direct experience with the place is included, (d) critical analysis is present alongside appreciation, and (e) the inquiry includes an action dimension.
```

## 示例输出

**场景：** *Curriculum content: "Ecosystems and biodiversity — Year 8 Science, understanding food chains, food webs, interdependence, and human impact on ecosystems" / Local place: "The canal that runs behind our school — it was built in the 1790s during the Industrial Revolution to transport goods. It fell into disuse in the mid-20th century and became polluted and overgrown. In 2015, a community trust restored it, and it's now a green corridor with wildlife, walking paths, and community gardens. But water quality is still variable, and there are ongoing debates about development on adjacent land." / Student level: "Year 8" / Community knowledge holders: "The canal trust has volunteer ecologists who monitor water quality. A retired geography teacher who wrote a booklet about the canal's history. A local councillor involved in the development debates."*

---

## 地方本位探究：学校后方的运河 × 生态系统与生物多样性

**场所：** 学校后方的运河——一条拥有 230 年历史、经历过工业繁盛、衰败与社区修复的水道
**课程内容：** 生态系统、食物链、食物网、相互依存以及人类对生物多样性的影响
**驱动问题：** "Is our canal a healthy ecosystem? How do we know, and what would make it healthier?"

### 这个场所教会了什么

这条运河是一本活生生的生态学教科书：
- **食物链与食物网：** 运河支撑着一个可见的食物网——藻类与水生植物 → 无脊椎动物（仰泳蝽、蜻蜓幼虫、淡水虾）→ 鱼类（如有）→ 苍鹭与翠鸟（如观察到）。学生在 100 米的河段内就能观察到多个营养级。
- **相互依存：** 运河生态系统依赖各种关系——植物为水体增氧，无脊椎动物分解有机物，纤道旁的树木为水面遮阴并减少过热。移除任何一个要素，系统都会发生偏移。
- **人类影响：** 这条运河由人类“创造”（工业基础设施）、被人类“破坏”（污染与荒废），又由人类“修复”（社区信托基金、栖息地管理）。它证明人类影响并不总是负面的——修复同样是一种人类选择。
- **演替：** 运河呈现出生态演替的不同阶段——新近清理并重新种植的河段、形成成熟栖息地的稳定河段、以及退化为茂密荒野的未维护河段。
- **作为指示器的水质：** 存在（或缺失）的物种是水质的生物指示器。某些无脊椎动物（淡水虾）的存在表明水质良好；它们的缺失则预示污染。学生可以“阅读”生态系统来评估其健康状况。

### 多元认识方式

**科学知识：** 水化学（pH 值、溶解氧、硝酸盐含量）、物种识别与分类、食物网绘制、生物多样性指数。这就是课程内容——通过运河而非课本教授。

**历史知识：** 运河建于 18 世纪 90 年代——为什么建在这里？运输过什么？运河如何塑造了当地的发展？为什么会衰落？工业污染如何影响了水体和周边土地？今天的运河生态是其历史的产物。

**社区知识：** 运河信托基金的志愿者多年来一直在监测水质。他们知道哪些河段最健康、哪里会出现问题、哪些干预有效。这就是公民科学——社区成员作为知识持有者。

**体验知识：** 运河“感觉”如何？当学生在纤道上静静坐下时注意到了什么？声音、气味、动态。直接的感官体验本身就是一种认识方式——生态意识始于专注的觉察。

**前殖民/前工业语境：** 在运河修建之前，这条水道是什么样的？原本是否有一条被人工渠化的自然溪流？在工业开发之前这里的地貌如何？谁曾生活在这里，他们如何与水相处？这些问题提醒我们，运河的历史远早于工业革命。

### 探究设计

**第 1 阶段——相遇场所（第 1 课：实地探访）**

学生分组拿着写字板沿运河纤道行走。任务很简单：观察并记录。
- "Sit quietly for 5 minutes at your assigned section. Write down everything you see that is alive — plants, animals, insects, birds. Draw a quick sketch of the habitat."
- "Use your senses: what do you hear? What does the water look like (colour, clarity, movement)? What do you smell?"
- "What evidence of human activity do you see? (Litter, path maintenance, planting, graffiti, fishing pegs, dog waste bins)"

每组观察一段不同的 50 米河段。学校提前向运河信托基金申请许可。

**第 2 阶段——向场所提问（第 2 课：回到教室）**

学生分享他们的观察。教师记录下来："What did you notice?" 接着问："What QUESTIONS does the canal raise for you?"

预期问题（必要时予以引导）：
- "Why are there more plants in some sections than others?"
- "Is the water clean enough for fish? How would we find out?"
- "What would happen if the canal trust stopped maintaining it?"
- "Are there more species near the community garden or near the road?"
- "What's the food chain here — what eats what?"

学生分组选定自己的探究问题。全班的核心驱动问题依然是："Is our canal a healthy ecosystem?"

**第 3 阶段——深入调查（第 3–6 课）**

*第 3 课——生物调查：* 回到运河。学生在运河信托基金的指导与许可下使用踢网采样法收集水生无脊椎动物样本，借助图鉴识别物种，并将发现映射到生物水质指数上。各组对比不同河段的结果。

*第 4 课——构建食物网：* 利用实地采集的物种数据，学生为各自负责的运河河段构建食物网，标出生产者、初级消费者、次级消费者。讨论："What would happen if [this species] disappeared? Trace the effects through the web."

*第 5 课——人类影响分析：* 邀请运河信托基金的嘉宾讲解修复过程。修复前的运河是什么样子？采取了哪些干预措施？哪些有效、哪些无效？学生将人类影响（积极与消极）标注在食物网图上："Where do humans intervene in this ecosystem?"

*第 6 课——历史生态学：* 借助退休地理教师编写的小册子和历史照片，学生将今天的运河与 50 年前的运河进行对比。当时存在哪些物种？发生了什么变化？生态系统是在恢复、趋于稳定，还是仍在退化？

**第 4 阶段——整合与分享（第 7–8 课）**

学生共同编制一份《运河健康报告》——一份回答驱动问题“我们的运河是一个健康的生态系统吗？”的集体成果。

每组贡献各自板块：
- 物种调查数据与食物网（科学）
- 水质分析（科学）
- 历史对比（历史/科学）
- 人类影响图谱（科学/地理）
- 建议："What would make the canal ecosystem healthier?"

报告在成果展示会上与运河信托基金分享。学生向信托志愿者和当地议员汇报发现。运河信托基金可以将这些数据纳入他们自己的长期报告中。

### 行动维度

**守护：** 学生在本学期“认领”各自的运河河段，每月开展一次垃圾清理（30 分钟，有成人看护）并收集数据："What types of litter are most common? Where does it come from?"

**倡导：** 如果调查揭示了水质问题，学生利用自己的数据向地方议会或水务公司撰写一封基于证据的信函。这是由真实证据支撑的真实倡导——而非模拟演练。

**贡献：** 物种调查数据分享给运河信托基金，作为其长期监测的一部分。学生成为公民科学家——他们的工作在教室之外具有真实价值。

### 社区知识持有者

| 知识持有者 | 他们掌握什么知识 | 他们如何贡献 |
|---|---|---|
| 运河信托生态学家 | 水质趋势、物种数据、修复技术 | 联合指导生物调查，提供历史监测数据供对比 |
| 退休地理教师 | 运河历史、历史地图与照片、当地地貌变迁 | 开展历史生态学讲座——这片场所曾经是什么样 |
| 当地议员 | 开发提案、规划决策、围绕运河的社区政治 | 解释开发与保护之间的张力——让学生看到生态决策同时也是政治决策 |
| 学生自己的家庭 | 关于运河的个人记忆——在它污染时期或恢复后的钓鱼、玩耍、散步或避而远之的经历 | 家庭作业访谈："Ask someone at home what they remember about the canal" |

---

## 已知局限性

1. **地方本位教育需要能够接触场所。** 学生需要实地探访运河（或同等的当地场所）。这需要风险评估、许可审批、交通安排和时间——在户外准入受限或“自然”空间较少的城市学校中，这些都可能成为障碍。本设计包含课堂替代方案，但任何替代都无法完全取代直接体验。

2. **地方本位探究比基于课本的教学耗时更多。** 上述运河探究耗时 8 课时——长于常规生态系统单元。学生获得的理解深度更大，并在掌握概念知识的同时发展了野外调查技能。但面临课程进度压力的教师可能难以证明额外课时的合理性。在时间有限的情况下，单次实地探访配合聚焦探究也能带来部分收益。

3. **尊重多元知识体系需要文化胜任力。** 教师必须乐于在科学知识之外邀请并珍视社区知识——并妥善处理不同知识体系看似冲突的情况。这需要文化敏感度、容忍复杂性的意愿，以及理解“不同的认识方式”并非相对主义，而是认识论的多元主义。
