---
# AGENT SKILLS STANDARD FIELDS (v2)
name: emergent-project-design-scaffold
description: "运用瑞吉欧（Reggio-inspired）取向，从观察到的儿童兴趣出发搭建生成性项目（emergent project）支架。适用于在学前或小学阶段顺应儿童的好奇心开展深度探究时。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "global-cross-cultural-pedagogies/emergent-project-design-scaffold"
skill_name: "生成性项目设计支架"
domain: "global-cross-cultural-pedagogies"
version: "1.0"
evidence_strength: "moderate"
evidence_sources:
  - "Rinaldi (2006) — In Dialogue with Reggio Emilia: listening, researching and learning"
  - "Malaguzzi (1993) — For an education based on relationships"
  - "Helm & Katz (2016) — Young Investigators: the project approach in the early years (3rd edition)"
  - "Wien (2008) — Emergent Curriculum in the Primary Classroom: interpreting the Reggio Emilia approach in schools"
  - "Edwards, Gandini & Forman (2012) — The Hundred Languages of Children (3rd edition)"
input_schema:
  required:
    - field: "children_interest"
      type: "string"
      description: "在儿童身上观察到的正在萌发的兴趣、问题或迷恋——吸引他们注意力的事物"
    - field: "teacher_observations"
      type: "string"
      description: "教师注意到的情况——儿童与该兴趣相关的问题、理论、实验和表征"
  optional:
    - field: "student_level"
      type: "string"
      description: "年龄组"
    - field: "curriculum_connections"
      type: "string"
      description: "该兴趣自然连接的课程领域"
    - field: "available_resources"
      type: "string"
      description: "可支持调查的材料、空间和社区资源"
    - field: "project_duration"
      type: "string"
      description: "项目可能持续的时间——一周、几周、一学期"
    - field: "team_context"
      type: "string"
      description: "教师是独立工作还是在团队中协作"
output_schema:
  type: "object"
  fields:
    - field: "project_scaffold"
      type: "object"
      description: "生成性项目设计——不是固定计划，而是回应儿童不断深化的探究的弹性支架"
    - field: "provocations"
      type: "array"
      description: "旨在深化和拓展儿童探究的体验、材料与问题（激发物/挑衅物）"
    - field: "curriculum_mapping"
      type: "object"
      description: "生成性项目如何连接到课程目标——自然的联结，而非牵强附会"
    - field: "documentation_plan"
      type: "object"
      description: "如何记录项目的演进——捕捉儿童的学习历程"
    - field: "decision_points"
      type: "array"
      description: "教师观察并做决定的节点：延伸这一方向、引入新的激发物，或让项目自然收尾"
chains_well_with:
  - "reggio-documentation-protocol"
  - "awe-wonder-experience-designer"
  - "agency-scaffold-generator"
  - "place-based-inquiry-anchor"
teacher_time: "4 分钟"
tags: ["Reggio-Emilia", "emergent-curriculum", "project-approach", "Rinaldi", "Malaguzzi", "provocations", "early-years", "primary"]
---

# 生成性项目设计支架

## 本技能的作用

为一个生成性项目（emergent project）设计弹性支架——即遵循瑞吉欧·艾米利亚（Reggio Emilia）课程取向、由儿童自身的兴趣、问题和理论所驱动的持续性调查。不同于预先确定的项目（教师提前规划好主题、活动和成果），生成性项目始于儿童真实的好奇心，并通过“观察 → 激发（provocation）→ 记录（documentation）→ 回应”的循环不断演进。教师的角色不是事先规划好整趟旅程，而是为旅程“搭建支架”——提供材料、激发物和环境，在深化与拓展儿童探究的同时将其自然连接到课程目标。来自 Rinaldi 的核心原则是：教师是与儿童并肩前行的研究者，对调查将走向何方抱有真诚的好奇。输出包括项目支架（不是死板的计划，而是带有决策点的弹性框架）、旨在深化探究的激发物、课程联结、记录计划以及教师观察回应的决策节点。AI 在此尤为有价值，因为设计真正回应儿童当前思维的激发物，需要同时理解儿童想法的发展轨迹，以及能够推动思维前进的丰富材料、体验和问题。

## 循证基础

Rinaldi (2006) 将生成性课程描述为“协商学习的过程”——课程从儿童兴趣、教师知识与环境的交汇处生长出来。教师并非放弃规划，而是“以不同的方式”规划：教师不提前规划具体活动，而是规划回应儿童当前正在调查之物的激发物（材料、体验、问题）。Malaguzzi (1993) 将环境阐述为“第三位教师”——在成人教师与儿童同伴之外，物理环境激发、支持并记录学习。生成性项目需要用心的环境设计：邀请调查的材料、支持协作的空间以及记录并维系项目演进的展示。Helm & Katz (2016) 为学前和小学阶段的“方案教学法（project approach）”提供了实用指南，描述了三个阶段：第 1 阶段（开启项目——识别兴趣、分享初始知识、提出问题）、第 2 阶段（发展项目——调查、表征、重温）和第 3 阶段（结束项目——分享、反思、庆祝）。Wien (2008) 将瑞吉欧原则调适应用于小学课堂，证明生成性课程并不局限于幼儿阶段，只要教师愿意追随儿童的问题，任何学段都可以实践。Edwards, Gandini & Forman (2012) 记录了瑞吉欧教育者如何规划“设计方案（progettazione）”——不是传统教案，而是对可能催化调查的环境、激发物和相遇进行有意识的设计，并结合细致的教学记录来指引下一步。

## 输入模式

教师必须提供：
- **Children's interest（儿童兴趣）：** 吸引他们注意力的事物。*例如："The children found a bird's nest in the school garden and are fascinated by how it was built — they keep going back to look at it, drawing it, and asking questions about the bird that made it" / "Year 1 children are obsessed with maps after finding an old map of the school grounds — they want to make their own maps of everything" / "Several children are deeply engaged with building — constructing increasingly complex structures and testing whether they stand up"*
- **Teacher observations（教师观察）：** 教师注意到的现象。*例如："Three children spent 20 minutes examining the nest, pointing at the different materials woven into it. One child said 'the bird is like a builder.' Another asked 'how did the bird carry all these sticks?' I've noticed children collecting sticks and leaves and trying to weave them together during outdoor play." / "Children are drawing maps of their bedrooms, the playground, and their journey to school. They argue about whether the map is 'right' — 'No, the swings aren't there, they're THERE!' — which shows they're grappling with representation and perspective."*

可选（如上下文引擎可用则自动注入）：
- **Student level（学生水平）：** 年龄组
- **Curriculum connections（课程联结）：** 相关课程领域
- **Available resources（可用资源）：** 材料、空间、社区资源
- **Project duration（项目时长）：** 预期长度
- **Team context（团队背景）：** 个人或团队

## Prompt

```
You are an expert in emergent curriculum and project-based investigation in the Reggio Emilia tradition, with deep knowledge of Rinaldi's (2006) concept of negotiated learning, Malaguzzi's (1993) hundred languages and environment as third teacher, Helm & Katz's (2016) project approach phases, Wien's (2008) emergent curriculum in primary settings, and Edwards, Gandini & Forman's (2012) account of Reggio progettazione. You understand that emergent projects are NEITHER unplanned ("let the children do whatever they want") NOR predetermined ("I've planned a bird project for this half-term"). They are intentionally scaffolded — the teacher observes, documents, interprets, and then designs provocations that deepen the children's inquiry in directions that are both child-led and educationally rich.

CRITICAL PRINCIPLES:
- **Start from the child's question, not the teacher's topic.** The interest is the children's — not a theme the teacher has chosen. The teacher's role is to recognise the interest, take it seriously, and provide opportunities for it to develop. If the teacher redirects the interest to fit a pre-planned topic, it ceases to be emergent.
- **Provocations, not lessons.** The teacher does not teach about birds — they provide a magnifying glass, books about nest construction, materials for building, and the question: "Could YOU build a nest that's as strong as the bird's?" A provocation invites investigation; a lesson delivers content. Provocations open possibilities; lessons close them.
- **The project is a conversation, not a delivery.** The project develops through a cycle: children investigate → teacher documents → teacher interprets → teacher designs provocation → children investigate further. Each step responds to the previous one. If the teacher plans all the provocations in advance, they are not responding — they are delivering.
- **Curriculum connections are found, not forced.** An emergent project on nest-building naturally connects to science (materials, habitats), technology (construction, engineering), literacy (stories about birds, information texts, children's own writing), mathematics (measurement, shape), and art (observation drawing, sculpture). These connections should be identified and used — but the investigation should not be distorted to "cover" a curriculum objective that doesn't fit.
- **Projects have a natural lifespan.** Not all interests sustain a long project. Some last a week and wind down; others last a term and keep deepening. The teacher should be attentive to the project's energy — extending it when children are engaged and allowing it to conclude gracefully when interest wanes.

Your task is to design an emergent project scaffold for:

**Children's interest:** {{children_interest}}
**Teacher observations:** {{teacher_observations}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Student level:** {{student_level}} — if not provided, design for early years or Key Stage 1.
**Curriculum connections:** {{curriculum_connections}} — if not provided, identify natural connections.
**Available resources:** {{available_resources}} — if not provided, suggest accessible resources.
**Project duration:** {{project_duration}} — if not provided, design with decision points that allow the project to last 1–4 weeks depending on children's engagement.
**Team context:** {{team_context}} — if not provided, design for a solo practitioner.

Return your output in this exact format:

## Emergent Project: [Interest]

**Children's interest:** [What has captured their attention]
**Teacher's guiding question:** [What the teacher is curious about — what they want to understand about children's thinking through this project]
**Potential duration:** [Flexible estimate]

### Phase 1 — Launching the Investigation

[How to begin — sharing what children already know, surfacing their questions, creating the conditions for investigation]

### Phase 2 — Provocations and Investigations

For each provocation (3–5):
**Provocation [N]: [What the teacher offers]**
- **What:** [The material, experience, or question]
- **Why:** [What this provocation might reveal or develop — connected to the teacher's observations]
- **Watch for:** [What to observe — children's responses, theories, new questions]
- **If children respond by...:** [Possible next steps depending on children's response]

### Phase 3 — Deepening and Representing

[How children represent their understanding through multiple "languages" — drawing, building, writing, dramatic play, discussion]

### Phase 4 — Sharing and Concluding

[How the project is shared and celebrated — with the class, with families, with the school]

### Curriculum Connections

[Natural connections to curriculum areas — what children are learning through the project]

### Decision Points

[Specific moments where the teacher pauses, documents, and decides: continue this direction, introduce a new provocation, or allow the project to wind down]

### Documentation Plan

[How to document the project's journey — what to capture and how to use it]

**Self-check before returning output:** Verify that (a) the project begins from children's genuine interest, (b) provocations respond to observed thinking, (c) the scaffold is flexible with decision points, (d) curriculum connections are natural, and (e) the project has a plan for concluding, not just beginning.
```

## 示例输出

**场景：** *Children's interest: "Reception children (ages 4–5) found a bird's nest in the school garden after it fell from a tree during a storm. They are fascinated by how it was built — examining the materials (twigs, moss, feathers, string, a piece of plastic bag), asking questions about the bird that made it, and trying to build their own nests during outdoor play." / Teacher observations: "Three children spent 20 minutes examining the nest with a magnifying glass. One said 'the bird is like a builder — she made a house!' Another asked 'how did the bird carry all these sticks with no hands?' A third pointed to the plastic bag piece and said 'the bird went shopping!' Several children have been collecting sticks, leaves, and string from the garden and trying to weave them into nests. The attempts keep falling apart, which is frustrating some children and motivating others to try differently." / Available resources: "School garden, outdoor area, art materials, clay, magnifying glasses, iPad for photos, access to a local nature reserve with a ranger"*

---

## 生成性项目：筑巢大师

**儿童兴趣：** 鸟类如何筑巢——材料、方法，以及不用手就能筑造的惊人本领
**教师的引导问题：** "What do the children understand about how structures are built, and how will their understanding develop as they try to build structures themselves?"
**潜在时长：** 2–4 周，取决于持续兴趣

### 第 1 阶段——开启调查

**第 1 天——汇总已知：**
小心地将鸟巢带入教室。放在配有放大镜的桌面上，邀请儿童仔细观察。在集体围坐谈话中提问："What do you notice?" 将儿童的观察记录在一张大纸上（教师代写，儿童口述）。

接着问："What questions do you have about this nest?" 记录问题。预期问题（基于目前的观察）：
- 鸟是怎么造出这个窝的？
- 它是用什么材料做的？
- 鸟没有手，怎么搬运这么多树枝？
- 鸟从哪里找来的绳子？
- 为什么里面有塑料？
- 鸟窝掉下来了，小鸟会不会难过？

将观察记录与问题张贴在墙上。这些就是调查的起点——由儿童的问题驱动整个项目。

**第 2 天——我们已经知道什么？我们想弄清什么？**
制作一张简明的记录展板：“关于鸟巢我们知道的事”（儿童当前认知）并列“我们想弄清的事”（儿童的问题）。这让探究过程可见，并创造了一个儿童在整个项目期间可以随时回看的参照点。

### 第 2 阶段——激发物与深入调查

**激发物 1：筑巢材料大拆解**
- **提供内容：** 小心地拆解鸟巢的一小部分（或如果有第二个鸟巢则使用第二个），将各种材料一一摊开：细树枝、苔藓、羽毛、细绳、塑料片。提供放大镜与绘画工具。提问："What is the nest made of? Why do you think the bird chose THESE materials?"
- **设计意图：** 教师观察到儿童对材料很感兴趣，但尚未思考鸟“为什么”选择这些材料。这一激发物将注意力聚焦于材料特性——坚固性、柔韧性、保暖性、防水性。
- **观察要点：** 儿童是按特性描述材料（"this one is bendy," "this one is soft"），还是只叫出名称（"it's a stick"）？基于特性的描述标志着材料科学理解的萌芽。
- **如果儿童开始研究材料特性：** 用分类挑战延伸——"Can you sort these into groups? What's your rule for sorting?"
- **如果儿童关注材料从哪里来：** 用花园搜寻延伸——"Can you find these materials in OUR garden?"

**激发物 2：筑巢建造挑战**
- **提供内容：** 在户外设立“筑巢工坊”。提供天然材料（树枝、干草、树叶、泥巴、羽毛）以及一个挑战："Can you build a nest that holds an egg?" 使用一颗小木蛋或小球作为测试物。两人或小组合作。
- **设计意图：** 儿童早先尝试筑巢时总是散架。这一激发物给予他们专注的时间、特定的材料以及明确的检验标准（能托住蛋吗？）。结构失败带来的挫败感具有建设性——它驱动问题解决与理论修正。
- **观察要点：** 儿童如何应对问题——是随机堆砌还是先有计划？他们会模仿真鸟巢的结构吗？当鸟巢散架时，他们是重复同样的方法还是改变策略？倾听工程语言："We need to make it tighter," "It needs to go round and round."
- **如果儿童成功：** 追问："What made YOUR nest work? What did the bird do that you did too?" 这将他们的经验重新连接到真鸟巢上。
- **如果儿童遇到困难：** 引入新的激发物——播放一段鸟类筑巢的视频片段（BBC 自然纪录片）。慢速观看。"What is the bird doing? How does she use her beak? What pattern is she following?"

**激发物 3：精细观察写生**
- **提供内容：** 提供细铅笔，将鸟巢放在小组中央。提问："Can you draw the nest EXACTLY as you see it — every stick, every piece of moss?" 这是观察性写生，而非自由创意绘画。
- **设计意图：** 绘画迫使人进行精细观察。画鸟巢的儿童会注意到单纯看时忽略的结构特征——树枝互相咬合的方式、不同材料的分层、圆形的轮廓。绘画本身就是一种调查方式。
- **观察要点：** 画中出现了哪些结构特征？儿童是画出一根根具体的树枝，还是只画一个笼统形状？他们注意到编织/交错的模式了吗？画作揭示了儿童“看到了什么”，从而反映出他们对结构的理解。
- **如果儿童注意到交错模式：** 这是一个关键的结构洞察。延伸：提供编织材料（布条、扭扭棒）和编织框。"Can you make materials interlock like the bird did?"

**激发物 4：与专家相遇**
- **提供内容：** 安排自然保护区护林员来访（或前往保护区参访）。儿童提前准备好问题。护林员展示不同类型的鸟巢，讲解鸟类如何筑巢，如条件允许则在花园或保护区观察真鸟。
- **设计意图：** 儿童已经亲自调查过鸟巢并形成了自己的理论。与专家相遇提供了新的信息，他们可以将其与自己的理论对比。专家应当“回答”儿童的问题，而不是发表讲座——由儿童的探究主导这次相遇。
- **观察要点：** 儿童如何协调专家的信息与自己的理论。他们会更新想法吗？他们会质疑专家吗？（"But we tried that and it didn't work!"）两种反应都很宝贵——它们表明儿童正投入真正的探究。
- **如果相遇引发了新问题：** 这些问题就成为下一阶段的调查方向。"The ranger said birds use mud as glue — can WE use mud as glue?"

### 第 3 阶段——深化与多元表征

儿童通过“一百种语言”表征他们的理解：

**绘画与涂鸦：** 鸟巢的观察性写生、小鸟筑巢的画作、带插图的筑巢“说明书”（程序性写作的萌芽）

**建构：** 使用日益丰富的材料筑巢。部分儿童可能会从天然材料转向试验其他材料——"What if we used playdough instead of mud?" 这就是工程探究。

**戏剧游戏：** 在角色扮演区创设“小鸟建筑工地”——安全帽、写字板、“建筑图纸”（儿童的画作）以及筑巢材料。儿童在扮演中演绎建造过程，这揭示了他们对顺序与方法的理解。

**语言与读写：** 口述故事（《建筑师小鸟》）、鸟巢展品标签、班级合集《关于鸟巢我们学到的事》、写给小鸟的信（"Dear Bird, we found your nest and we are looking after it"）

**数学：** 测量鸟巢中使用的树枝（"the longest stick is ___ cm"）、统计材料数量、比较鸟巢大小（如有多个鸟巢）、编织中的规律模式

### 第 4 阶段——分享与收尾

**鸟巢展览：** 在学校入口或教室展示项目记录——儿童调查的照片、他们的原话、他们的写生作品、他们建造的鸟巢与真鸟巢并列展示。呈现历程："First we thought... then we discovered... now we understand..."

**邀请家长：** 邀请家庭参观展览。儿童向家人讲解自己的项目——这是最有力的评估：孩子能否向不在场的人解释自己学到了什么？

**归还鸟巢：** 如条件合适，将鸟巢归还花园——或制作永久展示。与儿童讨论："The bird might build a new nest. Should we help? How?"

**自然收尾：** 当儿童的兴趣转向新焦点时，项目自然结束。这可能在 2 周后，也可能在 4 周后。教师敏锐察觉能量的退潮（选择鸟巢活动的人数减少、注意力转向别处），并帮助团队以展览的形式体面地画上句号。

### 课程联结

| 课程领域 | 儿童通过项目学到什么 |
|---|---|
| 科学（生物与栖息地） | 鸟类栖息地、筑巢方式、材料特性、观察技能 |
| 设计与技术 | 搭建结构、测试、迭代改进、按用途选择材料 |
| 数学 | 测量、计数、规律、形状（圆形鸟巢、交错模式） |
| 读写能力 | 词汇发展、程序性写作（如何筑巢）、讲故事、写标签、信息文本 |
| 艺术 | 观察性写生、立体造型（把筑巢当作雕塑艺术）、关注细节 |
| 社会情感与公民（PSHE） | 尊重自然、团队合作、建造失败时的坚持、关爱生命 |

### 决策节点

| 时机 | 观察什么 | 决策 |
|---|---|---|
| 第 1 周末 | 儿童是否仍在自主选择鸟巢相关活动？是否有新问题涌现？ | 如果是：引入激发物 3 或 4。如果兴趣减退：开始准备收尾。 |
| 建造挑战后 | 挑战是激发了新问题还是带来了纯挫败感？ | 若产生新问题：顺势跟进。若只有挫败没有好奇：提供更多支持或换个切入点。 |
| 专家相遇后 | 新信息是否点燃了新的探究？ | 如果是：延伸项目。如果相遇“解答了一切”：项目可能已准备好收尾。 |
| 当新兴趣出现时 | 儿童的问题是否正在转向新主题？ | 允许过渡。当新兴趣接棒时，让鸟巢项目自然结束。 |

### 记录计划

全程使用“瑞吉欧记录规程”进行记录：
- **每日：** 2–3 张照片 + 2–3 句原话摘录（记在随身笔记本中，当天结束时整理扩充）
- **每周：** 挑选最具揭示性的证据，制作一块迷你展板："This week we discovered..." 张贴在儿童视线高度以便重温
- **全程：** 收集儿童的画作与建构作品（立体作品拍照留存），并附注儿童自己的解释
- **项目结束：** 汇编成项目画册或电子档案袋。这将成为班级“集体记忆”的一部分，也是教师专业反思的宝贵资源

---

## 已知局限性

1. **生成性课程需要教师能够坦然面对不确定性。** 它没有预设的终点、没有保证覆盖的固定清单，也无法提前预知项目会走向何方。习惯于精细教案的教师可能会感到不适。上述支架提供了结构——但在这个结构之内，教师必须愿意追随儿童的引领。

2. **问责制体系可能与生成性取向产生冲突。** 要求提前提交详细中期计划的学校，很难轻松容纳生成性课程。上文列出的课程联结表明生成性项目“确实”回应了课程目标——但并非以可预测、可提前排程的顺序实现。教师可能需要在学校的规划要求中争取弹性空间。

3. **并非所有兴趣都能支撑一个项目。** 儿童的某些迷恋只是昙花一现——热烈一天便消退了。教师的专业功力在于区分“短暂的迷恋”与“能够支撑深入调查的持续兴趣”。上述决策节点正为此提供帮助——如果第 1 周后兴趣消退，就顺势收尾，而不是人为强行拉长。
