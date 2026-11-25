---
# AGENT SKILLS STANDARD FIELDS (v2)
name: outdoor-learning-sequence-designer
description: "设计结构化的户外学习序列，将课程目标嵌入可用的户外空间中。适用于规划在校园场地、公园或当地自然环境中开展的课程时。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "environmental-experiential-learning/outdoor-learning-sequence-designer"
skill_name: "户外学习序列设计师"
domain: "environmental-experiential-learning"
version: "1.0"
evidence_strength: "moderate"
evidence_sources:
  - "Education Endowment Foundation (2019) — Outdoor Adventure Learning systematic review"
  - "Rickinson, Dillon, Teamey, Morris, Choi, Sanders & Benefield (2004) — A Review of Research on Outdoor Learning"
  - "Waite (2011) — Children learning outside the classroom: from birth to eleven"
  - "Beames, Higgins & Nicol (2012) — Learning Outside the Classroom: theory and guidelines for practice"
  - "Mannion, Mattu & Wilson (2015) — Teaching, learning and play in the outdoors"
input_schema:
  required:
    - field: "learning_objective"
      type: "string"
      description: "学生将学习的具体课程内容或技能——户外活动在教育上“为了什么”"
    - field: "outdoor_space"
      type: "string"
      description: "可用的户外空间——校园场地、当地公园、林地、草坪、操场、花园"
  optional:
    - field: "student_level"
      type: "string"
      description: "年龄/年级"
    - field: "subject_area"
      type: "string"
      description: "课程学科"
    - field: "class_size"
      type: "string"
      description: "学生人数及可用的成人支持"
    - field: "time_available"
      type: "string"
      description: "户外课程持续时间"
    - field: "weather_constraints"
      type: "string"
      description: "季节、典型天气及任何限制条件"
    - field: "risk_factors"
      type: "string"
      description: "已知风险——交通、水体、地形、学生需求"
output_schema:
  type: "object"
  fields:
    - field: "outdoor_sequence"
      type: "object"
      description: "完整的户外学习序列——室内准备、户外活动、室内跟进"
    - field: "learning_design"
      type: "object"
      description: "户外元素如何服务于学习目标——在户外能学到哪些在室内学不到的内容"
    - field: "safety_framework"
      type: "object"
      description: "风险-收益评估、安全规程、成人职责"
    - field: "indoor_outdoor_continuity"
      type: "object"
      description: "室内与户外要素如何衔接——户外学习不是孤立活动，而是连贯序列的一部分"
chains_well_with:
  - "ecological-inquiry-anchor-designer"
  - "place-based-inquiry-anchor"
  - "biophilic-learning-environment-designer"
  - "awe-wonder-experience-designer"
teacher_time: "4 分钟"
tags: ["outdoor-learning", "EEF", "Rickinson", "outside-classroom", "fieldwork", "nature", "experiential"]
---

# 户外学习序列设计师

## 本技能的作用

设计一个结构化的户外学习序列，使户外元素服务于具体的课程学习目标——不是作为奖励、换换环境或泛泛的身心健康活动，而是作为一种充分利用户外环境独特优势的学习体验。Rickinson 等 (2004) 综述的核心原则是：当户外学习具备清晰的学习意图、与室内学习相连（课前准备、课后跟进）并让学生将户外环境作为主要资源开展主动探究时，其效果最佳。输出包括完整序列（室内准备、户外活动、室内跟进）、解释为何户外元素比室内替代方案更服务于目标的学习设计、安全框架以及室内外连贯性规划。AI 在此尤为有价值，因为设计有效的户外学习需要同时权衡课程对齐（学生在学什么？）、环境机会（这片特定空间提供什么？）、实际后勤（安全、天气、时间）以及教学法设计（如何组织活动以最大化学习）——这是一个多维度的规划挑战。

## 循证基础

Education Endowment Foundation (2019) 对户外冒险学习进行了系统综述，发现其对学业成绩具有中等但稳定的正向效应（尤其是对处境不利学生），对自信心、自我效能感、学习动机和团队合作等非认知成果具有更强的效应。关键在于，EEF 发现具有清晰学习目标的结构化户外学习比非结构化的户外时间效果更好。Rickinson 等 (2004) 完成了最全面的户外学习研究综述，识别出三大关键情境：实地考察与户外参访（与学校学科相连）、户外冒险教育（住宿制、团队建设）以及校园场地与社区项目。他们发现，设计良好的实地考察能够改善学科内容的长期记忆、发展实践探究技能并提升参与度——但设计糟糕的户外活动（目标不明确、与课程联系薄弱）除了带来愉悦感外，几乎不产生学习收益。Waite (2011) 聚焦于低龄儿童，证明户外环境天然支持主动的、感官的、探索性的学习，而这些学习在室内教室中往往受到限制。Beames, Higgins & Nicol (2012) 提出了户外学习的“地方教学法（pedagogy of place）”，主张物理环境应当成为规划的起点——不是把课程内容生硬套用到户外地点，而是发掘地点本身提供的学习机会。Mannion, Mattu & Wilson (2015) 记录了苏格兰学校的有效户外学习，强调最优质的户外学习序列包含三个阶段：预期（anticipation，准备）、相遇（encounter，户外体验）和回忆（recollection，反思与跟进）。

## 输入模式

教师必须提供：
- **Learning objective（学习目标）：** 学生将学什么。*例如："Measuring angles and distances — Year 7 Mathematics" / "Understanding habitats and adaptation — Year 4 Science" / "Descriptive writing using sensory detail — Year 6 English" / "Map skills and compass use — Year 8 Geography"*
- **Outdoor space（户外空间）：** 可用场地。*例如："School playing field — flat grass area, some trees around the perimeter, a pond in the conservation area" / "Local woodland — 15-minute walk from school, paths, stream, varied terrain" / "School playground — tarmac, benches, some planters, view of the local area"*

可选（如上下文引擎可用则自动注入）：
- **Student level（学生水平）：** 年级
- **Subject area（学科领域）：** 课程学科
- **Class size（班级规模）：** 人数与成人支持
- **Time available（可用时间）：** 户外课时长度
- **Weather constraints（天气限制）：** 季节与天气状况
- **Risk factors（风险因素）：** 已知危险

## Prompt

```
You are an expert in outdoor learning design, with deep knowledge of the Education Endowment Foundation's (2019) systematic review of outdoor adventure learning, Rickinson et al.'s (2004) comprehensive review of outdoor learning research, Waite's (2011) research on children learning outside the classroom, Beames, Higgins & Nicol's (2012) pedagogy of place, and Mannion, Mattu & Wilson's (2015) three-phase outdoor learning model. You understand that outdoor learning is most effective when it is STRUCTURED (clear learning objectives, not just "go outside"), CONNECTED (linked to indoor learning before and after), and EXPLOITS THE UNIQUE FEATURES OF THE OUTDOOR ENVIRONMENT (teaches something that cannot be taught as well indoors).

CRITICAL PRINCIPLES:
- **The outdoor element must serve the learning objective.** If the lesson could be taught just as effectively indoors, there is no educational reason to go outside. The outdoor environment must offer something the classroom cannot: real specimens, authentic contexts, spatial scale, sensory experience, or direct observation of phenomena.
- **Three-phase design: preparation → encounter → reflection.** Following Mannion et al. (2015), the outdoor session is the middle of a sequence, not a standalone activity. Indoor preparation builds the knowledge and skills students need to learn effectively outdoors. The outdoor encounter is the core learning experience. Indoor follow-up consolidates, analyses, and extends what was learned outside.
- **Active inquiry, not passive observation.** Students should DO something outdoors, not just look at things. Collect data. Measure. Sketch. Sample. Record. Compare. The outdoor environment is a laboratory, not a museum.
- **Safety through risk-benefit analysis, not risk elimination.** Outdoor learning involves risks (weather, terrain, traffic, water). The approach is not to eliminate all risk (which would also eliminate the learning) but to assess the BENEFITS against the risks and manage the risks to an acceptable level. A child who never encounters managed risk never develops risk assessment skills.
- **Weather is a feature, not a bug.** Rain, wind, cold, and heat are learning conditions, not cancellation conditions. "There's no such thing as bad weather, only bad clothing" (Norwegian proverb). Design the session to work in the weather that's likely, not just in ideal conditions.

Your task is to design an outdoor learning sequence for:

**Learning objective:** {{learning_objective}}
**Outdoor space:** {{outdoor_space}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Student level:** {{student_level}} — if not provided, design for a general school-age context.
**Subject area:** {{subject_area}} — if not provided, infer from the learning objective.
**Class size:** {{class_size}} — if not provided, design for 30 students with one teacher and one teaching assistant.
**Time available:** {{time_available}} — if not provided, design for a 60-minute session (including transition time).
**Weather constraints:** {{weather_constraints}} — if not provided, design for a temperate climate with a rain contingency.
**Risk factors:** {{risk_factors}} — if not provided, include standard outdoor risk assessment guidance.

Return your output in this exact format:

## Outdoor Learning Sequence: [Learning Objective]

**Learning objective:** [What students will learn]
**Outdoor space:** [Where]
**Why outdoors?** [Specifically what the outdoor environment offers that the classroom cannot]

### Phase 1 — Preparation (Indoor)

[What students need to know, practise, or prepare before going outside — builds the knowledge needed for the outdoor activity to be effective]

### Phase 2 — Encounter (Outdoor)

**Setup:** [How to organise students, distribute equipment, establish boundaries]
**Activity:** [Step-by-step outdoor learning activity — what students do, in what order]
**Teacher role:** [What the teacher does during the outdoor activity — circulating, questioning, managing]
**Key questions to ask outdoors:** [Specific questions that direct students' attention to the learning objective]

### Phase 3 — Reflection (Indoor)

[How to consolidate the outdoor learning — what students do with the data/observations/experiences they collected outside]

### Safety Framework

**Risk-benefit assessment:**
| Risk | Likelihood | Severity | Benefit | Management |
|---|---|---|---|---|
| [Risk 1] | [L/M/H] | [L/M/H] | [What learning benefit justifies this risk] | [How to manage it] |

**Weather contingency:** [What to do if weather changes — adapt, not cancel]
**Adult roles:** [Who does what — teacher, TA, parent helpers]

### Indoor-Outdoor Continuity

[How the three phases connect — the outdoor session is not a separate event but the middle of a coherent learning sequence]

### Equipment and Resources

[What's needed — kept practical and minimal]

**Self-check before returning output:** Verify that (a) the outdoor element serves the learning objective specifically, (b) the three-phase design is complete, (c) students are actively inquiring outdoors, not passively observing, (d) the safety framework uses risk-benefit analysis, and (e) the indoor and outdoor phases are connected.
```

## 示例输出

**场景：** *Learning objective: "Descriptive writing using sensory detail — Year 6 English. Students need to write descriptions that use all five senses, specific vocabulary, and figurative language (similes, metaphors, personification). Current work is weak — descriptions are generic and rely on sight alone." / Outdoor space: "School grounds — a conservation area with a small pond, trees (including a large oak), a meadow area, and a sensory garden planted by Year 3 last year. Also the main playground (tarmac) and the school building itself." / Time available: "60 minutes for the outdoor session; preparation and follow-up in normal English lessons either side." / Weather constraints: "March — could be sunny, cold, rainy, or any combination. Unpredictable."*

---

## 户外学习序列：感官描写写作——六年级

**学习目标：** 运用五种感官、具体词汇与修辞手法（明喻、暗喻、拟人）撰写描写文
**户外空间：** 校园生态保护区——池塘、树木、草甸、感官花园
**为什么去户外？** 教室是一片感官荒漠——永远是同样的声音（椅子摩擦声、时钟滴答声）、同样的气味（白板笔、食堂午饭味）、同样的触感（课桌、铅笔、纸张）。如果学生没有任何可感知的丰富对象，就无法写出丰富的感官描写。户外环境提供了真实而复杂的感官输入：潮湿泥土的气息、风穿过树枝的声音、树皮的质感、水面上的光影、野蒜的味道（如安全且有生长）。亲身“体验”感官丰富性的学生，比被要求“想象感官细节”的学生写得更加具体生动。

### 第 1 阶段——准备（室内，30 分钟，上一节课）

**微课：感官词汇审计。**
发给学生一张包含五列的表格：看（See）、听（Hear）、触（Touch）、嗅（Smell）、尝（Taste）。挑战："Describe this classroom using ALL five senses. Write at least three specific details per sense." 学生会发现：视觉很容易，听觉尚可，触觉有限，嗅觉有限，味觉几乎不可能。这揭示了问题所在：平庸单一的环境产出平庸单一的描写。

**范文分析。** 阅读一段精彩的自然描写节选（例如 Robert Macfarlane 的自然散文或 Ted Hughes 的诗歌）。学生识别：使用了哪些感官？哪些细节是“具体的”（不只是 "green"，而是 "the sharp green of new nettles"）？哪些使用了修辞手法？

**户外环节准备：** 发放“感官田野笔记本”——对折的 A4 纸，标好五种感官分区。说明任务："Tomorrow you will be a writer in the field. Your job is to COLLECT sensory details like a scientist collects specimens. You will take them back to the classroom and use them to write."

### 第 2 阶段——相遇（户外，60 分钟）

**集合与引入（5 分钟）：**
步行前往生态保护区。在入口处停下。"Before you write ANYTHING, stand still for 60 seconds. Close your eyes. Listen. What can you hear?" 这种从室内到户外的过渡是有意设计的——它让学生放慢节奏，将注意力从同伴闲聊转向环境感知。

**活动 1——感官站点（30 分钟）：**
学生轮流经过五个站点，每站停留 5–6 分钟，在“感官田野笔记本”中记录。

| 站点 | 位置 | 感官聚焦 | 任务 |
|---|---|---|---|
| 1：倾听哨所 | 老橡树下 | 听觉 | 闭眼 2 分钟。写下听到的每一种声音——近处与远处、响亮与轻柔。要“具体”：不要写 "bird"，而要写 "two sharp, rising notes, then a pause, then three more." |
| 2：触感小径 | 树篱/林线旁 | 触觉 | 触摸 5 种不同的天然表面（树皮、树叶、泥土、石头、苔藓）。每一种都准确写出它的触感。使用一个明喻："the bark felt like..." |
| 3：气味地图 | 感官花园 | 嗅觉 | 轻轻揉碎一片叶子。闻一闻泥土。闻一闻空气。写下：这里闻起来像什么？能否不用另一种气味来形容一种气味？（这很难——而这正是重点。） |
| 4：视觉定格 | 池塘边 | 视觉（但必须具体） | 选定一小块区域（不超过手掌大小）。准确描写你看到的一切——色彩、形状、动态、光线。规则：禁止使用笼统词汇。不要写 "green"，而是“哪一种”绿？不要写 "water"，而是此刻的水看起来是什么样？ |
| 5：全景之地 | 草甸区 | 五感综合 | 站在草甸中。写一段“全景描写”——视线从左扫到右，调动“所有”感官描述你的体验。这是综合训练：视觉 + 听觉 + 嗅觉 + 触觉 + （如适用）味觉。 |

**活动 2——修辞语言寻宝（15 分钟）：**
完成站点轮转后集中全班："Now find ONE thing in this environment that reminds you of something completely different. The pond that looks like a mirror. The branches that reach like fingers. The wind that whispers. Find YOUR comparison and write it down with the REASON — why does it remind you of that?"

**教师角色：** 在各站点间巡视。提出核心问题（见下文）。从肩后查看学生记录。识别仍然写得笼统的学生（"the tree was brown"）并引导纠正："Closer. WHICH brown? Touch it. Close your eyes. Now describe." 同时留意写出精彩细节的学生，记下来以便第 3 阶段分享。

**户外提问核心问题：**
- "Close your eyes. What do you hear NOW that you didn't notice before?"
- "You wrote 'the bark was rough.' Rough like sandpaper? Rough like a cheese grater? Rough like your dad's chin? WHICH rough?"
- "What does this smell remind you of? Can you capture that in words?"
- "If you had to describe this place to someone who has never been here, what ONE detail would you choose?"

**收尾（10 分钟）：** 返回教室。"Don't lose your notebooks. Everything you collected outside is the raw material for tomorrow's writing."

### 第 3 阶段——反思与成文（室内，45 分钟，下一节课）

**第 1 步——挖掘田野笔记（10 分钟）：** 学生回顾自己的“感官田野笔记本”。标出三个“最佳”细节——最具体、最生动、最出人意料的细节。与同伴分享："Which of my details is strongest?"

**第 2 步——起草成文（25 分钟）：** 学生以田野笔记为主要素材，撰写一段关于生态保护区的描写文。要求：至少调动三种感官、至少使用两种修辞手法、不使用笼统词汇（教师提供“禁用词清单”：nice、good、big、small、pretty、green——改用更具体的替代词）。

**第 3 步——同伴互评（10 分钟）：** 交换作品。同伴阅读并回答："Which ONE detail made you feel like you were THERE? Where could the description be more specific?"

### 安全框架

**风险-收益评估：**

| 风险 | 可能性 | 严重程度 | 收益 | 管理措施 |
|---|---|---|---|---|
| 湿滑地面滑倒 | 中（三月） | 低 | 接触真实感官环境；雨水本身“增添”感官细节 | 提醒学生穿合适鞋履。步行勿跑。标出湿滑区域。 |
| 池塘落水 | 低 | 中 | 池塘站点提供丰富的视觉与听觉细节（水面、倒影、声音） | 距池岸 1 米设置清晰边界标记。安排成人驻守池塘边。学生仅在岸上观察。 |
| 过敏反应（植物、花粉） | 低 | 中 | 与植物进行直接感官接触 | 课前核查医疗记录。有花粉热或植物过敏的学生调整嗅觉站任务（只观察，不揉碎叶片）。如学生配有抗组胺药则随身携带。 |
| 寒冷/降雨 | 高（三月） | 低 | 天气本身就是感官素材——雨声、湿润的气味、寒冷的触感都是写作材料 | 要求穿外套。如非常寒冷可缩短至 45 分钟。雨天预案：照常外出——雨天产出的感官描写往往优于晴天。仅在暴风雨或雷电时取消。 |

**天气应急预案：** 小雨——照常进行，携带带防雨罩的写字板。大雨——缩短至 30 分钟，聚焦较有遮蔽的站点。雷电——推迟。

**成人职责：** 教师巡视并提问引导。助教管理站点轮换并看护池塘区域。如有家长志愿者：每站一人提示不善动笔的学生。

### 室内外连贯性

三个阶段构成“一个”完整的学习序列：
- **准备阶段**构建学生户外采集有效素材所需的分析词汇（感官类别、修辞类型）
- **相遇阶段**提供室内无法生成的原始感官素材——真实的气味、真实的质感、真实的声音
- **反思阶段**将原始感官数据转化为精心打磨的文字——户外笔记是“证据”，室内课堂是“写作建构”

户外环节不是附带写作任务的“郊游放松”。写作直接依赖户外体验；没有田野笔记，学生就无从下笔。

### 器材与资源

- 感官田野笔记本（预先准备：对折 A4 纸，标好五个感官区）
- 写字板与铅笔（不用钢笔/水笔——雨天写不出字）
- 放大镜（可选，但对视觉站点很有帮助）
- 站点轮换计时器
- 急救包
- 备用外套（供忘记带外套的学生使用）

---

## 已知局限性

1. **户外学习需要校园场地或可达的户外空间。** 位于高密度城区、只有小型硬化操场且缺乏绿地的学校需要作出调整——感官站点在任何户外环境中都可以开展，但体验的丰富程度取决于环境本身的丰富程度。铺满沥青和围栏的校园操场提供的感官多样性不如生态保护区。

2. **天气确实会限制某些活动。** 虽然本技能主张将雨水视为特色而非缺陷（对于感官描写确实如此），但有些户外学习目标高度依赖天气。需要干燥条件的科学野外调查、需要稳固手部操作的户外美术，或积水草地上的体育活动都会面临真实的天气限制。本技能对雨天的积极定位适用于“本示例”，而非放之四海而皆准。

3. **EEF 综述发现户外学习对学业成绩的效应量为中等，而非巨大。** 户外学习持续提升参与度、学习动机和身心健康——但直接提升考试成绩的证据强度仅为中等。户外学习最强的理由在于它能提供室内无法复制的学习体验（真实感官输入、真实样本、空间尺度），而非它能普遍提高考试分数。教师应当在户外环境能增添教室无法提供的独特价值时使用户外学习，而不是将其作为提升分数的通用策略。
