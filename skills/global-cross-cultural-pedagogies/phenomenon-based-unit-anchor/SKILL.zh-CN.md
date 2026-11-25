---
# AGENT SKILLS STANDARD FIELDS (v2)
name: phenomenon-based-unit-anchor
description: "将跨学科单元锚定在一个需要多学科视角才能理解的真实世界现象上。适用于跨学科设计整合单元或现象教学单元时。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "global-cross-cultural-pedagogies/phenomenon-based-unit-anchor"
skill_name: "基于现象的单元锚点设计器"
domain: "global-cross-cultural-pedagogies"
version: "1.0"
evidence_strength: "moderate"
evidence_sources:
  - "Finnish National Agency for Education (2016) — National Core Curriculum for Basic Education (POPS 2016)"
  - "Lonka (2018) — Phenomenal Learning from Finland"
  - "Symeonidis & Schwarz (2016) — Phenomenon-based teaching and learning through the pedagogical lenses of phenomenology"
  - "Halinen (2018) — The new educational curriculum in Finland"
  - "Silander (2015) — Phenomenon-based learning in Espoo"
input_schema:
  required:
    - field: "phenomenon"
      type: "string"
      description: "作为单元锚点的真实世界现象——一个需要多个学科视角才能理解的复杂真实情境"
    - field: "subjects_involved"
      type: "string"
      description: "该现象所依托的学科领域或门类"
  optional:
    - field: "student_level"
      type: "string"
      description: "年龄/年级"
    - field: "curriculum_links"
      type: "string"
      description: "单元必须回应的具体课程目标"
    - field: "unit_duration"
      type: "string"
      description: "单元持续时间——1 周、2 周、半学期模块"
    - field: "school_context"
      type: "string"
      description: "学校是否支持跨学科规划、课表弹性、协同授课"
    - field: "local_relevance"
      type: "string"
      description: "该现象如何与学生所在当地社区或生活经验相连"
output_schema:
  type: "object"
  fields:
    - field: "unit_design"
      type: "object"
      description: "完整的现象教学单元——锚点现象、驱动问题、各学科贡献、整合节点"
    - field: "subject_contributions"
      type: "array"
      description: "每个学科为理解该现象贡献什么——具体的知识与技能"
    - field: "integration_points"
      type: "array"
      description: "各学科在何处以及如何连接——真正的整合，而非仅仅相邻"
    - field: "student_inquiry_pathway"
      type: "object"
      description: "学生如何调查该现象——问题、活动、证据收集"
    - field: "assessment_design"
      type: "object"
      description: "如何评估对现象的理解——展示整合性理解，而非分科测试"
chains_well_with:
  - "project-brief-designer"
  - "culturally-responsive-teaching-designer"
  - "place-based-inquiry-anchor"
  - "agency-scaffold-generator"
  - "curriculum-knowledge-architecture-designer"
teacher_time: "5 分钟"
tags: ["phenomenon-based-learning", "Finland", "POPS-2016", "Lonka", "cross-curricular", "interdisciplinary", "transversal-competences"]
---

# 基于现象的单元锚点设计器

## 本技能的作用

设计一个锚定在真实世界现象上的现象教学（phenomenon-based learning）单元，该现象需要多个学科共同参与才能被完整理解——遵循芬兰 2016 年国家核心课程（POPS 2016）的核心取向。来自芬兰模式的关键洞察在于：现象不是“主题”或“话题”——它们是真正“需要”多个学科视角才能理解的复杂真实情境，因为没有任何单一学科能完全解释它们。像“当地河流水质”这样的现象需要科学（污染物化学、水生生物生态）、地理（土地利用、水系）、数学（数据分析、测量）以及公民教育（政策、社区责任）。本技能设计单元时，确保每个学科的贡献都不可或缺，且整合是真实的——各学科之所以连接，是因为现象本身有此需求，而不是教师人为把它们拼凑在一起。输出包括单元设计、各学科贡献、具体整合节点、学生探究路径以及检验整合性理解的评估设计。AI 在此尤为有价值，因为设计真实的基于现象的单元需要同时将多个学科的课程目标映射到同一个现象上，并确保真正的整合——这是一个适合系统性交叉索引的复杂设计挑战。

## 循证基础

芬兰国家教育署（2016）规定所有学校每年至少开展一次拓展性的“多学科学习模块”，让学生透过多个学科视角研究同一现象。其依据在于现实世界的问题不会按学科打包出现——气候变化不只是“科学”、“地理”或“经济”，而是所有这些的同时交织。Lonka (2018) 记录了芬兰的实践取向，强调现象教学（PBL——注意不要与基于问题的学习混淆）并不是抛弃学科，而是围绕真实现象对学科进行整合。学科依然存在并被教授——但它们定期聚拢在一起共同应对现实世界的复杂性。Symeonidis & Schwarz (2016) 从现象学哲学为该方法奠基，指出人类在将现象分析性地拆分为各学科之前，首先是以整体方式体验现象的——因此学习有时应当逆转这种分析性拆分，回归整体性参与。Halinen (2018) 描述了芬兰课程如何将学科特定目标与“横贯能力（transversal competences）”（思维与学会学习、文化胜任力与互动、多元读写、ICT 能力、职场能力、参与和投入、自我照护与日常生活管理）配对，并通过现象教学模块加以培养。Silander (2015) 记录了埃斯波（Espoo）的早期实施经验，表明最有效的现象教学单元是那些现象真正复杂（需要多学科）且具有本地相关性（与学生社区相连）的单元，而非生硬拼凑学科联系的虚假“主题”。

## 输入模式

教师必须提供：
- **Phenomenon（现象）：** 真实世界情境。*例如："Water quality in our local river — why does it change through the year and what affects it?" / "Fast fashion — why are clothes so cheap and what does that cost?" / "Our school's carbon footprint — where does it come from and can we reduce it?" / "Migration to our city — why do people come, what changes, and how do communities respond?"*
- **Subjects involved（涉及学科）：** 哪些学科参与。*例如："Science, Geography, Mathematics" / "Geography, Economics, Ethics, Textiles" / "Science, Mathematics, Citizenship" / "Geography, History, English, PSHE"*

可选（如上下文引擎可用则自动注入）：
- **Student level（学生水平）：** 年级
- **Curriculum links（课程关联）：** 需要回应的具体目标
- **Unit duration（单元时长）：** 单元持续时间
- **School context（学校背景）：** 课表弹性、协同授课能力
- **Local relevance（本地相关性）：** 与学生社区的联结

## Prompt

```
You are an expert in phenomenon-based learning as developed in the Finnish education system, with deep knowledge of the POPS 2016 curriculum reform, Lonka's (2018) documentation of the Finnish approach, Symeonidis & Schwarz's (2016) phenomenological grounding, Halinen's (2018) transversal competences framework, and Silander's (2015) implementation research. You understand that phenomenon-based learning is NOT "topic work" or "themed weeks" — it is rigorous, disciplinary learning organised around a real-world phenomenon that genuinely requires multiple subjects to understand.

CRITICAL PRINCIPLES:
- **The phenomenon must be GENUINELY complex.** A good phenomenon cannot be fully understood through one subject alone. If the "integration" requires forcing connections ("Let's do fractions about the rainforest!"), the phenomenon is wrong. Each subject must contribute something NECESSARY that the other subjects cannot provide.
- **Subjects contribute, they don't disappear.** Students still learn science AS science, maths AS maths. The phenomenon provides the context and motivation — but the disciplinary rigour is maintained. Students should learn subject content MORE deeply because the phenomenon gives it meaning, not less deeply because the integration is superficial.
- **Start with a question, not a topic.** "Water" is a topic. "Why does the water quality in our river change through the year, and what can we do about it?" is a driving question that generates genuine inquiry. The question should be real, open, and locally relevant.
- **Integration points must be genuine.** The subjects should connect at specific, identified points where one subject's contribution informs another's. "Science tells us about pollutants; Geography tells us where they come from; Maths helps us analyse the data" — each subject's contribution is genuinely needed at a specific point.
- **Assessment must be integrated.** If you test each subject separately at the end, you have not designed a phenomenon-based unit — you have designed parallel subject units on the same topic. The final assessment should require students to draw on multiple subjects simultaneously.

Your task is to design a phenomenon-based unit for:

**Phenomenon:** {{phenomenon}}
**Subjects involved:** {{subjects_involved}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Student level:** {{student_level}} — if not provided, design for lower secondary (Years 7–9).
**Curriculum links:** {{curriculum_links}} — if not provided, identify appropriate curriculum areas.
**Unit duration:** {{unit_duration}} — if not provided, design for a 2-week module (approximately 10–12 lessons across subjects).
**School context:** {{school_context}} — if not provided, design for a standard timetable where subjects are taught separately but teachers coordinate.
**Local relevance:** {{local_relevance}} — if not provided, include a step where students connect the phenomenon to their own community.

Return your output in this exact format:

## Phenomenon-Based Unit: [Phenomenon]

**Driving question:** [The central question that animates the unit]
**Subjects:** [Which disciplines contribute]
**Duration:** [How long]
**Transversal competences developed:** [Which Finnish-style transversal competences this unit develops]

### Unit Overview

[One paragraph: what students investigate, how subjects contribute, what they produce]

### Subject Contributions

For each subject:
**[Subject]: [What this subject contributes]**
- **Knowledge:** [What students learn in this subject through the phenomenon]
- **Skills:** [What disciplinary skills students develop]
- **Why this subject is necessary:** [What understanding would be MISSING without this subject's contribution]

### Integration Map

[Where and how the subjects genuinely connect — specific points where one subject's output becomes another subject's input]

### Student Inquiry Pathway

**Week 1: [Phase name]**
[What students do — which subjects are active, what questions they investigate, what they produce]

**Week 2: [Phase name]**
[Continuation — how the inquiry deepens, how subjects come together]

### Assessment Design

[How to assess integrated understanding — not subject-by-subject testing but a task that requires drawing on multiple disciplines]

### Practical Considerations

[How to coordinate across subjects when teachers have separate timetables — meeting points, shared resources, communication]

**Self-check before returning output:** Verify that (a) the phenomenon genuinely requires multiple subjects, (b) each subject contributes something necessary that others cannot provide, (c) the integration points are genuine and specific, (d) the assessment requires integrated understanding, and (e) the unit is practically feasible within normal school structures.
```

## 示例输出

**场景：** *Phenomenon: "Fast fashion — why are clothes so cheap, what does that cost environmentally and socially, and what could we do about it?" / Subjects involved: "Geography, Science, Mathematics, Ethics/PSHE" / Student level: "Year 8" / Unit duration: "2 weeks — approximately 10 lessons across the four subjects" / Local relevance: "The school is near a high street with several fast-fashion retailers — students shop there regularly"*

---

## 基于现象的单元：快时尚（Fast Fashion）

**驱动问题：** 为什么我们的衣服这么便宜？这种便宜的真正代价是什么？我们又有什么选择？
**学科：** 地理、科学、数学、伦理/社会健康教育（Ethics/PSHE）
**时长：** 2 周（4 个学科共约 10 节课）
**培养的横贯能力：** 思维与学会学习、文化胜任力与互动、多元读写、参与与投入

### 单元概览

学生透过四个学科视角调查快时尚现象：地理学审视全球供应链（衣服在哪里生产、为什么生产转移到特定国家、服装工人的人文地理）；科学调查环境影响（纺织化学、染料造成的水污染、合成纤维脱落的微塑料、运输碳足迹）；数学分析数据（成本构成、产量规模、废弃物统计以及不同来源数据的对比与解读）；伦理/PSHE 探讨道德维度（消费者选择、工人权利、可负担性与剥削之间的张力）。单元最终产出学生制作的“真实成本标签（True Cost Label）”——一种重新设计的服装吊牌，利用全部四个学科的证据传达一件衣服完整的环境与人文成本。

### 各学科贡献

**地理：我们的衣服从哪里来，以及为什么？**
- **知识：** 全球供应链、制造业经济地理（为什么是孟加拉国、越南、埃塞俄比亚）、工厂选址的推拉因素、制造区的城市化与工作条件
- **技能：** 地图技能（追踪供应链）、数据解读（对比不同国家的工资与工作条件）、地理探究
- **为何该学科不可或缺：** 没有地理，学生就无法理解衣服“为什么”便宜——全球制造的空间逻辑、劳动力成本的逐底竞争、服装工人的人文地理处境。科学能解释环境破坏，但无法解释造成这种破坏的经济空间结构。

**科学：快时尚对地球做了什么？**
- **知识：** 纺织纤维特性（天然纤维 vs. 合成纤维）、印染与后整理化学过程、水污染（工厂化学废水）、微塑料污染（洗涤合成纤维释放微塑料）、全球运输的碳排放
- **技能：** 科学探究（测试不同面料的微塑料释放量）、数据收集、理解化学过程
- **为何该学科不可或缺：** 没有科学，学生就无法理解“环境”代价。“污染”只会停留在模糊字眼，除非学生理解具体的化学机制——纺织染料里有哪些化学物质、合成纤维进入水道后会发生什么、为什么涤纶需要 200 年才能分解。

**数学：问题有多大，我们能相信这些数字吗？**
- **知识：** 百分比（成本拆分——一件 5 英镑 T 恤中有百分之多少流向工人？）、大数感知（每年生产 27 亿件服装——如何直观理解这一数量级？）、数据解读（阅读和批判性审视来自公益倡议组织与行业报告的图表）
- **技能：** 计算百分比、解读并比较不同来源的数据、理解统计宣称、制作数据可视化
- **为何该学科不可或缺：** 没有数学，学生就无法把握问题的“规模”。“很多衣服被浪费了”是模糊的；“在英国，每年有 35 万吨衣物进入垃圾填埋场——相当于 35,000 辆双层巴士的重量”则是具体且可理解的。数学还提供了评估行业报告与环保组织相互冲突宣称的批判性工具。

**伦理/PSHE：我们应该对此做些什么？**
- **知识：** 伦理框架（权利、后果、公平）、消费者责任、“道德消费”概念、个人选择与系统变革之间的张力、工人权利（《世界人权宣言》、国际劳工组织公约）
- **技能：** 伦理推理、构建论证、换位思考、权衡相互冲突的价值（可负担性 vs. 可持续性 vs. 工人权利）
- **为何该学科不可或缺：** 没有伦理/PSHE，单元只会产出没有能动性的知识。学生知道了快时尚造成伤害，却没有框架来判断该“做什么”。这是消费者的责任、企业的责任还是政府的责任？抵制购买是有效，还是会伤害它本想帮助的工人？这些都是需要伦理推理的伦理问题。

### 整合图谱

| 整合节点 | 学科 A 贡献…… | 学科 B 利用它来…… |
|---|---|---|
| **供应链映射** | 地理绘制一件 T 恤的生产旅程（棉田 → 纺纱厂 → 制衣厂 → 货轮 → 仓库 → 商店） | 数学计算每个阶段的成本（零售价的百分之多少流向了哪里？） |
| **环境证据** | 科学识别纺织生产中的具体污染物 | 地理标注污染发生的位置（生产国工厂附近的河流水系，而非消费国） |
| **问题规模** | 数学分析产量与废弃物统计数据 | 伦理利用数据评估道德责任（"If 87% of clothing fibre ends up in landfill or incineration, is this a design problem or a consumer problem?"） |
| **工人处境** | 地理描述服装厂的工作条件与工资 | 伦理通过权利框架审视这些处境（"Does this violate Article 23 of the UDHR?"） |
| **真实成本标签** | 所有学科共同贡献数据与分析 | 学生将四个视角综合为单一产品 |

### 学生探究路径

**第 1 周：理解现象**

*地理（2 课时）：* 追踪一件特定衣物的供应链。发给学生一张服装标签（"Made in Bangladesh"）并调查其旅程：棉花在哪里种植？在哪里纺纱？衣服在哪里缝制？如何运抵英国？学生绘制供应链地图，并调研每个阶段的工作条件。家庭作业：查看你衣柜里 5 件衣服的标签——它们是在哪里制造的？

*科学（2 课时）：* 调查纺织材料。第 1 课：在显微镜下观察面料样本（棉 vs. 涤纶 vs. 尼龙）——它们由什么构成？有什么特性？第 2 课：设计并开展简易实验测试微塑料释放——在水中清洗合成面料样本、过滤并在显微镜下观察。你发现了什么？

*数学（1 课时）：* 5 英镑 T 恤的成本拆解。学生获得一件快时尚 T 恤的成本结构数据并计算：棉农、工厂工人、航运公司、零售商和品牌各自获得百分之多少？将数据绘制成饼图。讨论："Does this distribution seem fair? What would have to change for the worker to earn a living wage?"

**第 2 周：分析与回应**

*科学（1 课时）：* 碳足迹计算。学生计算所调查衣物旅程的近似碳足迹（使用来自地理供应链地图的简化运输排放数据）。对比：本地制造的衣物与从亚洲海运来的衣物碳足迹有何不同？

*伦理/PSHE（2 课时）：* 第 1 课：伦理辩论。呈现三种立场：“买得更少、买得更好”（消费者责任）、“企业应支付生活工资”（企业责任）、“政府应立法监管”（系统变革）。学生用伦理框架评估每种立场。第 2 课："Is boycotting ethical?"——如果消费者停止购买孟加拉国制造的衣服，工厂工人就会失业。学生直面善意行动可能带来的非预期后果。

*数学（1 课时）：* 评估相互冲突的宣称。给学生两份数据来源：一份行业报告声称“快时尚降低了服装成本，惠及低收入家庭”；一份倡议报告声称“快时尚产生全球 10% 的碳排放”。评估两者：使用了什么数据？是否可靠？宣称是否准确？学生学会批判性地阅读数据。

*全学科（1 课时——合并或协调）：* 制作“真实成本标签”。每位学生为一件自选衣物（来自自己衣柜或假设衣物）设计一张标签，传达：它在哪里制造及由谁制造（地理）、它的环境影响（科学）、成本拆解（数学）以及伦理评级（伦理）。标签必须基于证据——每一项宣称都必须有本单元的数据支撑。

### 评估设计

**真实成本标签（整合性评估）：**

学生为一件自选衣物制作“真实成本标签”。标签必须包含：

1. **供应链摘要**（地理）：衣物产地、流转旅程、各阶段工人处境
2. **环境影响声明**（科学）：环境代价——材料、化学品、碳排放、微塑料——附具体数据
3. **成本拆解**（数学）：零售价流向的可视化图表，附清晰的百分比计算与呈现
4. **伦理评估**（伦理）：运用至少一种伦理框架对衣物伦理状况进行评估，包括承认其中的张力与权衡

**评估标准：** 标签采用整体性评估——而非分科打分。标准包括：准确性（证据是否正确？）、整合度（四个视角是否连接成连贯图景？）、批判性（学生是否承认复杂性与权衡取舍？）以及沟通力（标签是否清晰有效？）。

各参与学科教师评估本学科贡献的准确性，但“整合度”由教师共同评估。

### 实践考量

**协调（最难的部分）：** 四位教师需要在单元前召开一次 30 分钟的备课会，并在单元中途碰头一次（分享学生产出并调整进度）。建立一个共享文件夹（电子或纸质），供学生存放各学科产出的证据——每节课的产出都直接汇入最终标签。

**课表：** 该单元在常规课表内即可运行。每个学科在自己的固定课时授课。唯一的要求是大致同步（地理的供应链课应在数学的成本拆解课之前，因为供应链为成本分析提供数据）。一份简单的共享时间表即可避免各学科进度脱节。

**资源：** 面料样本（供科学显微镜观察）、服装标签（学生从家带来）、数据集（成本拆解、产量统计——由教师精选整理）、简易制图工具（供地理绘制供应链地图）。

---

## 已知局限性

1. **现象教学需要跨学科协调，这在大多数学校存在结构性困难。** 芬兰课程在设计之初就考虑了这一点——芬兰学校通常拥有更大的课表弹性和教师协作传统。在课表刚性、备课时间有限的学校中，学科间的协调是主要障碍。上述单元设计已将所需协调降至最低（一次备课会、一个共享文件夹、大致同步），但仍比单科独立教学需要更多协作。

2. **并非所有学科都与所有现象天然契合。** 上述快时尚案例令人信服地整合了地理、科学、数学与伦理——每个学科都贡献了真正必要的内容。但如果强行整合（“让美术课也加入，学生设计可持续时尚系列”），反而会削弱单元。让三个学科真正深度整合，远胜于把五个学科生硬拼凑在一起。

3. **现象教学是对分科教学的补充，而非替代。** 芬兰模式是在分科教学“之外”并行设置现象教学模块——而不是取而代之。学生仍然需要专门的学科课程来建立他们带入现象探究中的学科知识与技能。如果一所学校用现象教学取代所有分科教学，很可能会培养出涉猎广泛但学科理解浅薄的学生。
