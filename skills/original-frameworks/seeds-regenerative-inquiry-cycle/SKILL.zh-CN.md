---
# AGENT SKILLS STANDARD FIELDS (v2)
name: seeds-regenerative-inquiry-cycle
description: "设计 SEEDS 再生探究循环，将基于地方的学习与幼小学习者的生态觉察连接起来。适用于围绕生态系统与社区构建幼教或小学探究。"
disable-model-invocation: true
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "original-frameworks/seeds-regenerative-inquiry-cycle"
skill_name: "SEEDS 再生探究循环"
domain: "original-frameworks"
version: "1.0"
evidence_strength: "emerging"
evidence_sources:
  - "Manning (2025) — SEEDS cycle, published in All Thoughts Subject to Change (Substack)"
  - "Manning (2025) — Metabolising Regeneration (regenerative vs restorative vs sustainable spectrum)"
  - "Kimmerer (2013) — Braiding Sweetgrass (bio-empathy, reciprocity)"
  - "Vervaeke (2019) — Relevance realisation (philosophical underpinning for the Sense stage)"
  - "Sobel (2004) — Place-based education (external validation of underlying principles)"
  - "Reggio Emilia documentation pedagogy (aligned assessment approach)"
input_schema:
  required:
    - field: "learning_group"
      type: "string"
      description: "哪个年龄组——幼教阶段（5-8岁）或小学阶段（8-12岁）"
    - field: "place_context"
      type: "string"
      description: "锚定本次探究的具体场所、生态系统或社区——学习发生的地点及所连接的对象"
  optional:
    - field: "existing_problem_or_potential"
      type: "string"
      description: "如已识别的已知问题或机遇——SEEDS 可以从问题出发，也可以从可能性出发"
    - field: "time_available"
      type: "string"
      description: "整学期、全年或更短周期"
    - field: "community_connections"
      type: "string"
      description: "探究可对接的人员、组织或生态系统"
    - field: "documentation_approach"
      type: "string"
      description: "学习将如何变得可见——学习故事、档案袋、观察记录"
output_schema:
  type: "object"
  fields:
    - field: "seeds_overview"
      type: "object"
      description: "循环概览、地方锚点与再生意图"
    - field: "sense_stage"
      type: "object"
      description: "调频活动、生态共情实践、基线数据收集、知识缺口识别"
    - field: "envision_stage"
      type: "object"
      description: "构想序列、专家介入计划、基于标准的现实检验、评估检查点"
    - field: "experiment_stage"
      type: "object"
      description: "原型制作与行动计划、调整机制、形成性评估方法"
    - field: "design_to_last_stage"
      type: "object"
      description: "管家结构、照料常规、交接计划、指定管家或接任者"
    - field: "share_stage"
      type: "object"
      description: "影响评估（诚实面对——正面、负面、预期与非预期）、叙事方式、回连至“感知（Sense）”阶段"
    - field: "documentation_plan"
      type: "object"
      description: "如何在全程让学习变得可见——档案袋、学习故事、观察记录"
    - field: "known_limitations"
      type: "object"
      description: "关于证据基础、时间需求以及与标准学校时间表张力的诚实说明"
chains_well_with:
  - "place-based-inquiry-anchor"
  - "reggio-documentation-protocol"
  - "ecological-inquiry-anchor-designer"
  - "ubuntu-collective-knowledge-task-designer"
  - "critical-thinking-task-designer"
teacher_time: "6 分钟"
tags: ["SEEDS", "regenerative", "inquiry", "place-based", "Manning", "bio-empathy", "stewardship", "cyclical", "documentation"]
---

# SEEDS 再生探究循环

## 本技能的功能

本技能编码了由教育者、课程设计师及学习系统设计师 Gareth Manning 开发的原创实践者框架。与其他领域的技能不同，它并非源自同行评审研究传统，而是植根于对学习科学的深入研习、原创课程设计工作以及一线课堂测试。将其纳入本库，是因为该方法论逻辑连贯、可迁移且真正实用——同时出于学术诚实，需将实践者框架与经研究验证的方法加以区分。

SEEDS 为幼教与小学情境设计了一个五阶段再生探究循环——一个将学生探究扎根于真实场所、真实系统与真实关爱的学习过程。SEEDS 代表**感知（Sense）→ 愿景（Envision）→ 实验（Experiment）→ 持久设计（Design to Last）→ 分享（Share）**。与线性项目框架不同，SEEDS 是循环的——分享回连至感知，且各阶段彼此重叠、螺旋递进。与大多数项目式学习（PBL）框架不同，SEEDS 始于调频与生态共情（bio-empathy）而非问题陈述，终于管家结构（stewardship structures）而非一场展示。起点处的注意力品质决定了终点处的行动品质。**宁可留在“愿景”阶段增长见识，也不要在无知中贸然行动而造成伤害。**

该框架汲取了 Kimmerer（2013）的互惠伦理（“这就是我们的工作：去发现我们能给予什么”）、Vervaeke 作为“感知”阶段哲学锚点的相关性实现（relevance realisation）、作为评估方法的瑞吉欧·艾米利亚（Reggio Emilia）记录教学法，以及用于扎根真实场所的基于地方的教育原则（Sobel, 2004）。它受巴厘岛绿色学校（Green School Bali）4S 模型（Freud）的启发但与之截然不同——在致敬这一催化剂的同时，明确指出 SEEDS 是具有显著不同评估哲学的原创开发。再生光谱（regenerative spectrum）至关重要：修复性（restorative，修补损伤）只是底线；再生性（regenerative，增强系统蓬勃生长的能力）才是目标。

## 循证基础

Manning（2025）开发了 SEEDS 循环作为传统 PBL 框架的再生型替代方案，发表于 *All Thoughts Subject to Change*（Substack）。该框架回应了标准项目式学习的三大局限：（1）大多数 PBL 始于问题陈述，将世界框定为“坏掉的”而把学生框定为“修理工”——SEEDS 始于调频，将世界框定为复杂的而把学生框定为参与者；（2）大多数 PBL 终于一场汇报展示，将项目简化为一次表演——SEEDS 终于管家精神，将项目嵌入持续的照料；（3）大多数 PBL 评估聚焦于最终产品——SEEDS 评估全程基于记录，在每个阶段让学习变得可见。Manning（2025）还在 *Metabolising Regeneration* 中阐述了再生光谱：可持续（sustainable）维持现状，修复性（restorative）恢复至先前状态，而再生性（regenerative）提升系统蓬勃发展的能力。SEEDS 瞄准的是再生性。Kimmerer（2013）为“感知”阶段提供了哲学基石。她的“生态共情（bio-empathy）”概念——以我们对待人际关系同等的关切去关注非人类世界——锚定了 SEEDS 的第一阶段。生态共情包含非人类的声音：河流需要什么？土壤需要什么？这不是隐喻，而是一项将生态利益相关方纳入探究的方法论承诺。Vervaeke 关于相关性实现的研究支撑了“感知”阶段：在复杂环境中觉察重要之事——区分信号与噪音——的能力是一项可训练的技能，而非固定特质。“感知”阶段正是通过结构化调频实践来训练这一能力。Sobel（2004）以及 Castagno & Brayboy 为 SEEDS 背后的基于地方原则提供了外部验证。基于地方的教育研究一贯表明，扎根于本地场所的学习比抽象、去情境化的学习更能产生深度投入、更强的社区联结以及更好的记忆保持。瑞吉欧·艾米利亚记录教学法与 SEEDS 评估方法高度契合：学习通过贯穿全程的记录（照片、学习故事、档案袋、观察笔记）变得可见，而非仅凭最终产品评价。这种契合是独立产生的——Manning 在深入接触瑞吉欧之前便已开发出该记录方法——但两者的趋同强化了学理基础。

## 输入模式

教育者必须提供：
- **学习群体：** 哪个年龄组。*例如：“幼教阶段，5–8岁——18名儿童的混龄小组” / “小学阶段，8–12岁——26名学生的五年级班”*
- **地方情境：** 锚定探究的具体场所。*例如：“学校被荒废的庭院——一个200平方米的水泥地，有两棵枯树和一座开裂的喷泉” / “学校后面的本地河流——社区请求清理的一段500米河道” / “学校厨房及其废弃物系统——学生注意到厨余垃圾被混入了普通垃圾”*

可选（如有，由上下文引擎注入）：
- **现有问题或潜力：** 如存在已知起点
- **可用时间：** 循环将持续多久
- **社区联结：** 可对接的人员、组织或生态系统
- **记录方式：** 学习将如何变得可见

## 提示词

```
You are designing a SEEDS regenerative inquiry cycle — a five-stage framework developed by Gareth Manning. You must encode the framework PRECISELY as specified. Do not approximate, improvise, or substitute generic PBL language. SEEDS is specific and its distinctions from standard PBL matter.

THE FIVE STAGES:
1. **Sense** — Attunement. Students develop quality of attention toward the place. They observe, listen, sit with, draw, measure, and ask questions. Bio-empathy practices include asking: what does this place need? What is alive here? What is struggling? What is thriving? This stage also includes baseline data gathering (what is the current state of the place?) and knowledge gap identification (what do we need to learn before we can act wisely?). The Sense stage is NOT a quick warm-up — it may last days or weeks. Rushing past Sense produces uninformed action.

2. **Envision** — Ideation grounded in knowledge. Students generate ideas for what could be — how the place could be healthier, more vibrant, more regenerative. Ideas are tested against criteria: Is it genuinely regenerative (not just less harmful)? Is it feasible with our resources and time? Does it respect the needs we identified in Sense? Expert engagement: bring in people who know this place or this system — a gardener, a community elder, a biologist, a council member. Assessment checkpoints: students should be able to explain the place, its needs, and their reasoning BEFORE moving to Experiment. It is better to stay in Envision and become knowledgeable than to act unknowingly and cause harm.

3. **Experiment** — Prototyping and action. Students test their ideas at small scale before full implementation. Adaptation mechanisms: what will you change if it doesn't work? Formative assessment throughout — documentation captures what students try, what works, what doesn't, and how they adapt. This is where learning science happens: hypotheses, tests, observations, revisions.

4. **Design to Last** — Stewardship, not presentation. The question is not "How will we present this?" but "How will this continue after we're done?" Stewardship structures: who will care for this next term? Next year? Care routines: what needs to happen daily, weekly, seasonally? Handoff plan: how is knowledge transferred to the next group? Named steward or successor: a specific person, group, or structure that takes responsibility. "Design to Last" is the stage that distinguishes SEEDS from conventional PBL — it embeds learning in ongoing responsibility rather than ending it with a product.

5. **Share** — Honest impact assessment and storytelling. Impact assessment must be honest: positive, negative, intended, AND unintended effects. Not a celebration — a reckoning with what actually happened. Storytelling approach: how do we communicate what we learned and what we did, so others can build on it? Connection back to Sense: Share feeds into the next cycle. What do we notice NOW about this place? What has changed? What needs attention next? The cycle is regenerative because it doesn't end — it spirals.

CRITICAL DISTINCTIONS (encode these in the output):
- SEEDS is CYCLICAL, not linear — Share feeds back into Sense
- Begins with QUALITY OF ATTENTION, not identification of a problem
- Bio-empathy includes NON-HUMAN voices — not just human stakeholder empathy
- Assessment is DOCUMENTATION-BASED throughout, not product-focused at the end
- "Design to Last" is NOT the same as "present" — stewardship is the point
- The REGENERATIVE SPECTRUM matters: restorative is minimum, regenerative is the aim
- It is BETTER TO STAY IN ENVISION and become knowledgeable than to act unknowingly and cause harm

Your task is to design a SEEDS cycle for:

**Learning group:** {{learning_group}}
**Place context:** {{place_context}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Existing problem or potential:** {{existing_problem_or_potential}} — if not provided, the Sense stage will surface the inquiry direction.
**Time available:** {{time_available}} — if not provided, design for a full term (10-12 weeks).
**Community connections:** {{community_connections}} — if not provided, identify the connections that would strengthen the inquiry and suggest how to find them.
**Documentation approach:** {{documentation_approach}} — if not provided, recommend a documentation approach appropriate for the age group.

Return your output in this exact format:

## SEEDS Regenerative Inquiry Cycle: [Place Context]

**Place anchor:** [The place, ecosystem, or community]
**Learning group:** [Age range and context]
**Regenerative intent:** [One sentence — what regenerative outcome this cycle aims for]
**Cycle duration:** [How long]

### SEEDS Overview

[Summary of the cycle — what will happen across the five stages, how they connect, and why this place is the right anchor for regenerative inquiry with this group]

### Stage 1: Sense — Attunement

**Duration:** [How long this stage should last — do not rush it]
**Core question:** "What is alive here? What does this place need?"

**Attunement activities:**
[Specific activities that develop quality of attention — observation, sensory engagement, sitting with the place]

**Bio-empathy practices:**
[Activities that extend empathy to non-human elements — what does the soil need? What is the water telling us?]

**Baseline data gathering:**
[What to measure, observe, and document about the current state]

**Knowledge gap identification:**
[What do students need to learn before they can act wisely? What expertise is needed?]

**Documentation during Sense:**
[How learning is made visible at this stage — photographs, drawings, observations, questions recorded]

### Stage 2: Envision — Grounded Ideation

**Duration:** [How long]
**Core question:** "What could this place become? What would genuinely regenerative look like?"

**Ideation sequence:**
[How students generate and develop ideas — grounded in what they learned in Sense]

**Expert engagement plan:**
[Who to bring in and why — people who know this place or this system]

**Reality testing criteria:**
[How to test whether ideas are genuinely regenerative, feasible, and respectful of the place's needs]

**Assessment checkpoint:**
[What students should be able to explain before moving to Experiment — if they can't, stay in Envision]

### Stage 3: Experiment — Prototyping and Action

**Duration:** [How long]
**Core question:** "Does this work? What needs to change?"

**Prototyping plan:**
[Small-scale tests before full implementation]

**Adaptation mechanisms:**
[What to do when things don't work — how to revise, pivot, or return to Envision]

**Formative assessment approach:**
[How learning is documented and assessed throughout — not just at the end]

### Stage 4: Design to Last — Stewardship

**Duration:** [How long]
**Core question:** "How will this continue after we're done?"

**Stewardship structure:**
[Who will care for this? What does ongoing maintenance look like?]

**Care routines:**
[Daily, weekly, and seasonal care tasks]

**Handoff plan:**
[How knowledge and responsibility transfer to the next group]

**Named steward or successor:**
[A specific person, group, or structure that takes ongoing responsibility]

### Stage 5: Share — Honest Impact Assessment

**Duration:** [How long]
**Core question:** "What actually happened — intended AND unintended?"

**Impact assessment:**
[Honest reckoning — positive effects, negative effects, intended outcomes, unintended outcomes]

**Storytelling approach:**
[How students communicate what they learned and did — for others to build on]

**Connection back to Sense:**
[How Share feeds into the next cycle — what do we notice NOW? What needs attention next?]

### Documentation Plan

[How learning is made visible across ALL five stages — the specific documentation tools, routines, and products]

### Known Limitations

[Honest framing — this is a practitioner framework, not a peer-reviewed methodology. Include: evidence base limitations, time requirements, tension with standard school timelines, and where teacher judgment is essential]

**Self-check before returning output:** Verify that (a) all five SEEDS stages are present and distinct, (b) the cycle is framed as cyclical not linear, (c) bio-empathy includes non-human voices, (d) Design to Last specifies stewardship not presentation, (e) Share includes honest impact assessment, (f) documentation is embedded throughout not just at the end, and (g) the regenerative spectrum is referenced.
```

## 示例输出

**场景：** *学习群体：“小学阶段，8–12岁——22名学生的混龄小组” / 地方情境：“学校被荒废的庭院——一个200平方米的水泥空间，有两个枯死的花箱、一条开裂的长椅和一个大雨时会积水的排水口。除作为过道外，该空间目前无人使用。校长已同意学生可以改造它” / 可用时间：“整学期，10周，每周专门投入3小时用于本循环” / 社区联结：“一位身为景观设计师的家长、500米外的一座本地社区花园、了解排水历史的学校管理员”*

---

## SEEDS 再生探究循环：学校庭院

**地方锚点：** 学校被荒废的 200 平方米庭院
**学习群体：** 混龄小学，8–12岁，22名学生
**再生意图：** 将一片毫无生机的水泥空间转化为学生、土壤生物与学校社群共同主动维系的生命系统——不仅仅是一座花园，而是一个拥有管家文化的运转中的微生态系统
**循环时长：** 10周（共30小时）

### SEEDS 概览

本循环选取了一片被荒废的庭院——目前满是水泥、裂缝且无人问津——要求学生在改变它之前先与它建立关系。直接跳去种花种草的诱惑会很大，但 SEEDS 抵制这种诱惑。学生将在前两到三周沉浸于“感知”与“愿景”阶段：观察空间、调查其系统（排水、日照、水泥下的土壤、现有生命）、识别空间需要什么，并基于知识形成再生型愿景。只有在此之后他们才进入“实验”阶段——小规模测试构想。“持久设计”确保庭院不会在学期结束后沦为又一个被遗忘的烂尾项目。“分享”阶段诚实评估实现了什么以及没有实现什么，并回流至下一轮循环。

### 第一阶段：感知（Sense）——调频

**时长：** 2.5周（第1–2周，及第3周前半）
**核心问题：** “这里有什么活着的东西？这个地方需要什么？”

**调频活动：**
- **静坐观察（第1周第1次课）。** 学生在庭院里静坐15分钟。起初不带手机、不带笔记本，只是静坐。15分钟后：“你注意到了什么？有什么让你惊讶？”记录观察。在三天内的不同时段——清晨、正午、下午——重复进行，以觉察光线、声音与活动如何变化。
- **感官地图（第1周第2次课）。** 学生两两结对绘制庭院感官地图：他们**看到**什么（水泥、裂缝、裂缝里的杂草、排水口、围墙）、**听到**什么（马路车流、屋顶鸟鸣、风声）、**感受到**什么（水泥地 vs. 阴凉处的温度、长椅的粗糙感）、**闻到**什么（排水口附近的潮味、花箱里毫无气息）。这训练了注意力的品质。
- **生命审计（第2周）。** 学生系统地搜寻庭院中的每一个生命体：裂缝里的杂草、墙上的青苔、昆虫、蜘蛛、来访的鸟类。用照片与绘图记录每一种。庭院并没有死——它只是被忽视了。这里已经有什么在顽强生存？

**生态共情实践：**
- **“雨水怎么看这个地方？”**（第2周）。下雨时，学生观察水流向哪里。是积水还是排走？它滋养了任何东西吗？提问：如果你是雨水，你会想落在这里吗？你会流去哪里？这不是幻想——而是一种怀着共情关注水系统的方式。
- **“土壤会说什么？”** 学生调查水泥下方是否有土壤（向管理员询问庭院历史）。如果在一个区域敲掉水泥，可能长出什么？土壤里生活着什么生物？它们需要什么？

**基线数据收集：**
- 测量庭院：面积、日照时长（在上午9点、中午12点、下午3点追踪阴影）、排水模式、温度（水泥地面 vs. 背阴墙面）
- 从四个固定点位拍照——这些将成为影响评估的“改造前”影像
- 访谈管理员：排水系统的历史是什么？庭院上次使用是什么时候？水泥下面有什么？
- 土壤测试：如果任何地方有裸露土壤（裂缝、花箱边缘），测试其 pH 值与结构

**知识缺口识别：**
学生生成一份“我们需要学习什么”清单：
- 排水系统如何运作？
- 哪些植物能在半阴且贫瘠的土壤中存活？
- 如何安全地移除水泥？
- 是什么让微生态系统能够自我维持？
- “再生型（regenerative）”是什么意思（相对于仅仅“没那么糟”）？

**感知阶段的记录：**
- 学习日志：每位学生维护一本庭院日志，记录观察、绘图、问题与数据
- 照片：每周从四个固定点位拍摄照片
- 班级“好奇墙”：将问题贴在共享展板上，分类为“我们能自己回答”和“我们需要帮助”

### 第二阶段：愿景（Envision）——基于知识的构想

**时长：** 1.5周（第3周后半，第4周）
**核心问题：** “这个地方能成为什么？真正具有再生性的样子是什么？”

**构想序列：**
- **个人愿景绘图（第3周）。** 每位学生画出自己对庭院的愿景。暂不设限——大胆梦想。随后小组分享：有哪些相似之处？有哪些不同之处？
- **再生光谱课（第3周）。** 教授三者区别：可持续（SUSTAINABLE）意味着维持原样；修复性（RESTORATIVE）意味着回到过去的样子；再生型（REGENERATIVE）意味着变得比以前**更有生命力**——系统蓬勃发展的能力提升了。提问：我们的庭院项目瞄准的是哪一种？（再生型。）
- **小组综合（第4周）。** 将个人愿景整合为 3–4 个小组提案。每个提案必须回答：这里将有什么现在还没有的生命？它将如何自我维持？谁来照料它？

**专家介入计划：**
- **景观设计师家长（第3或第4周）：** 邀请其审阅小组提案。向他提问：这可行吗？我们忽略了什么？专业人士会做哪些不同选择？
- **参访社区花园（第4周）：** 带学生前往本地社区花园。向园丁请教：你们是怎么起步的？什么失败了？你们希望当初早点知道什么？你们是如何长期维持的？
- **学校管理员（贯穿全程）：** 管理员是关键利益相关方——无论学生创造出什么，日常都将由他共同面对。他对这片空间的实用知识无可替代。

**现实检验标准：**
对照以下四点检验每个小组提案：
1. 它是否真正具有再生性？（它是提升了空间支持生命的能力，还是仅仅让它看起来更好看？）
2. 在我们的时间、预算与技能下是否可行？（22名学生真的能在6周内完成吗？）
3. 它是否尊重我们在“感知”阶段学到的东西？（它回应了排水、日照与现有生命吗？）
4. 它能持久吗？（没有我们的时候，它能熬过暑假吗？）

**评估检查点：**
在进入“实验”阶段之前，每位学生必须能够解释：（a）庭院现在是什么样以及为什么；（b）他们小组的提案是什么以及为什么它是再生型的（而不仅仅是好看）；（c）他们还需要学习什么。如果答不上来，小组就留在“愿景”阶段直到能够回答为止。

### 第三阶段：实验（Experiment）——原型与行动

**时长：** 3周（第5–7周）
**核心问题：** “这行得通吗？需要改变什么？”

**原型计划：**
- **第5周：小规模测试。** 在改造整个庭院前，先在小尺度上测试关键要素。如果计划包含种植：先种一小块测试区观察一周。如果计划包含移除水泥：先测试敲开一小块看看下面有什么。如果计划包含水景：先用水桶实验测试排水。
- **第6–7周：实施。** 基于测试结果实施商定方案。分成工作小组：种植组、建造组（高架床、座椅）、记录组（拍照、测量、记录）。轮换小组，让所有学生都能体验各个环节。

**调整机制：**
- **每周复盘（每次课结束时）：** 什么有效？什么无效？我们需要改什么？记录决策及其理由。
- **转向规程：** 如果某件事失败了（植物枯死、排水不畅、水泥撬不动），带着新信息退回“愿景”阶段。失败是数据，不是败北。

**形成性评估方法：**
- 记录持续进行：每次课都有照片、日志条目与数据收集
- 技能评估：学生能安全使用工具吗？能遵循种植计划吗？能准确测量和记录吗？
- 协作评估：学生是在相互依赖地工作吗？谁贡献了什么？

### 第四阶段：持久设计（Design to Last）——管家精神

**时长：** 1.5周（第8周，第9周前半）
**核心问题：** “我们离开后，这件事将如何延续下去？”

**管家结构：**
- **庭院委员会：** 由4名学生组成的轮值小组（每半学期换届），负责每周检查。高年级学生（10–12岁）率先任职并培训低年级学生接班。
- **教师赞助人：** 一名教师同意督导该委员会——不是替学生干活，而是确保委员会机制正常运转。

**照料常规：**
- **每日：** 检查任何种植区域的湿度/水位（纳入班级每日值日轮班表，而不仅靠委员会）
- **每周：** 委员会拿着核对清单巡视庭院——植物健康吗？座椅干净吗？排水畅通吗？有任何损坏吗？向全班汇报。
- **每季：** 春季播种、秋季清理、冬季对脆弱植物的防护。这些任务**现在**就写进下学期的校历，而不是听天由命。

**交接计划：**
- **《庭院指南》：** 学生制作一份实体指南（过塑，存放在庭院中），说明：哪里种了什么、它需要什么、每个季节做什么，以及出问题时联系谁。
- **下一批接任者入职引导：** 当前小组向**下一批**将接手庭院的学生展示庭院——解释历史、设计选择以及照料常规。这才是真正的“汇报展示”——不是为了炫耀，而是为了移交责任。

**指定管家或接任者：**
首届庭院委员会（4名具名学生）+ 教师赞助人。委员会结构在设计上旨在超越任何个人——每半学期吸纳新成员入职。

### 第五阶段：分享（Share）——诚实的影响评估

**时长：** 1周（第9周后半，第10周）
**核心问题：** “实际发生了什么——预期的以及非预期的？”

**影响评估：**
学生开展一次诚实的审计：
- **正面的预期效果：** 我们计划达成且实际达成了什么？（更多生命、更好的排水、可用的空间）
- **正面的非预期效果：** 发生了哪些我们未曾计划的好事？（低年级学生开始来这里阅读；有鸟儿在新植物里筑巢）
- **负面的预期效果：** 我们刻意采取的行动是否造成了任何伤害？（敲除水泥是否暴露了树根？新种植是否挤占了原本支持昆虫的杂草？）
- **负面的非预期效果：** 出了哪些我们未曾预料的问题？（高架床挡住了管理员的通行路线；某一种植物实际上是入侵物种）

这**不是**一场庆功会，而是一次诚实的清算。诚实的影响评估是再生实践的基石——你无法改进你拒绝看见的东西。

**叙事方式：**
学生利用他们的照片、日志摘录与数据，制作一条从第一次静坐到管家交接的循环视觉时间线。时间线讲述**真实的**故事，包括失败与转向，而非经过粉饰的成功叙事。这条时间线就展示在庭院内部——让未来的学生看到过程，而不仅仅是结果。

**回连至“感知”：**
在最后一节课，学生回到庭院静坐15分钟——正如第1周那样。然后：“你**现在**注意到了什么第1周时没注意到的东西？什么改变了？什么仍然需要关注？”这些新观察将汇入下一轮循环。SEEDS 循环不会终结——它螺旋上升。

### 记录计划

**贯穿全部五个阶段：**
- **学生日志：** 每位学生维护一本庭院日志——观察、绘图、数据、问题与反思。这是他们的个人记录与核心评估材料。
- **定点摄影：** 每周从庭院四个固定点位拍照——创建跨越10周的变化视觉档案。
- **班级记录墙：** 每周更新的实体或数字展板，展示：当前阶段、关键观察、所做决策以及正在调查的问题。
- **学习故事（教师撰写）：** 教师每周撰写 2–3 篇学习故事——对重要学习瞬间的叙事性记录，附带照片。这些是与瑞吉欧记录教学法对齐的主要评估文档。

---

## 已知局限

1. **SEEDS 是一个原创实践者框架，而非同行评审方法论。** 它已在特定教育情境（Manning 在布达佩斯 REAL School 及相关项目中的工作）中开发并测试，但尚未接受过对照实验评估。其底层原则与同行评审研究（基于地方的教育、记录教学法、形成性评估）一致，但具体的 SEEDS 框架及其五阶段结构是 Manning 的原创设计。

2. **SEEDS 需要大量时间——超出大多数学校课表所允许的范围。** 上述深度的完整 SEEDS 循环需要 10–12 周且每周有专门时段。课表刚性、分科教学且面临考试压力的学校可能难以分配这段时间。可以进行缩短版适配（压缩“感知”与“愿景”阶段的6周循环），但会牺牲使 SEEDS 独树一帜的调频深度。

3. **“感知”阶段感觉很慢——可能会遭遇阻力。** 习惯于行动导向 PBL 的教师可能想跳过“感知”或将其压缩成一节课。学生可能会感到沮丧：“我们什么时候才真正**做**点什么？”“感知”阶段刻意放慢，是因为起点处的注意力品质决定了终点处的行动品质。这需要教师与学生双方都信任这种“慢”是富有成效的。

4. **生态共情在哲学上基础扎实，但在方法论上不够精确。** 问“土壤需要什么？”是一个极具生成性的探究提示，但并非科学方法。它既可能产出真正的生态洞察（土壤需要有机质、水分、微生物生命），也可能沦为模糊的拟人化（土壤“很难过”）。教师的角色是引导学生从共情提示走向科学调查——将共情用作入口，而非终点。

5. **管家精神依赖于机构的延续性。** “持久设计”阶段要求学校在原始学生群体离开之后继续维持管家结构——庭院委员会、照料常规、季节性日程。如果学校不承诺这种延续性，庭院就会退化回荒废状态，而学生将学到“我们的工作并不重要”。教师在许下管家承诺前必须获得机构支持。
