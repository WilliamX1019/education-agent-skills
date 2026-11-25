---
# AGENT SKILLS STANDARD FIELDS (v2)
name: ubuntu-collective-knowledge-task-designer
description: "基于乌班图（Ubuntu）哲学设计学习任务，强调集体知识建构与共同责任。适用于培养重共同体而非个人竞争的协作精神时。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "global-cross-cultural-pedagogies/ubuntu-collective-knowledge-task-designer"
skill_name: "乌班图集体知识任务设计师"
domain: "global-cross-cultural-pedagogies"
version: "1.0"
evidence_strength: "emerging"
evidence_sources:
  - "Mkabela (2005) — Using the Afrocentric method in researching indigenous African culture"
  - "Letseka (2012) — In defence of Ubuntu"
  - "Ramose (2002) — The philosophy of Ubuntu and Ubuntu as a philosophy"
  - "Venter (2004) — What is African philosophy of education?"
  - "Msila (2008) — Ubuntu and school leadership"
input_schema:
  required:
    - field: "learning_objective"
      type: "string"
      description: "学生需要学习的课程内容或技能"
    - field: "class_context"
      type: "string"
      description: "班级构成、社区背景以及学生目前对待合作学习的方式"
  optional:
    - field: "subject_area"
      type: "string"
      description: "课程学科"
    - field: "student_level"
      type: "string"
      description: "年龄/年级"
    - field: "current_task"
      type: "string"
      description: "需要通过乌班图视角重新设计的现有任务"
    - field: "community_connection"
      type: "string"
      description: "学习如何与更广泛的社区相连或让社区参与其中"
    - field: "assessment_constraints"
      type: "string"
      description: "课程是否要求个人评估，以及如何将其与集体学习相平衡"
output_schema:
  type: "object"
  fields:
    - field: "ubuntu_task_design"
      type: "object"
      description: "运用乌班图原则重新设计的任务——集体知识建构、共同责任、社区收益"
    - field: "collective_knowledge_structure"
      type: "object"
      description: "任务如何构建集体而非个人的知识建构——每个人的贡献对整体都是必需的"
    - field: "community_dimension"
      type: "object"
      description: "学习如何连接或服务于更广泛的社区——而不仅仅是个人成就"
    - field: "individual_within_collective"
      type: "object"
      description: "个人成长与问责如何在集体结构中共存——不被抹除，而是被重新框架化"
chains_well_with:
  - "culturally-responsive-teaching-designer"
  - "belonging-classroom-culture-designer"
  - "place-based-inquiry-anchor"
  - "agency-scaffold-generator"
teacher_time: "4 分钟"
tags: ["Ubuntu", "Mkabela", "African-philosophy", "collective-knowledge", "communalism", "community", "collaboration"]
---

# 乌班图集体知识任务设计师

## 本技能的作用

透过乌班图（Ubuntu）哲学视角——非洲理念 "umuntu ngumuntu ngabantu"（人之为人，因与他人相连）——重新设计学习任务，使知识建构真正成为集体性的，而非个人主义的。西方教育通常将学习结构化为个人获取：每位学生为自己学习、单独接受评估、独立成功或失败。乌班图哲学提出了一种截然不同的认识论：知识是共有的，智慧通过关系涌现，离开他人的理解，个人的理解便是不完整的。本技能重新设计学术任务，使集体知识建构成为结构性要求（任务无法由一人独自完成——每个人的贡献都在结构上不可或缺），学习服务于社区（而不仅仅是单个学生），且个人成长存在于集体“之中”，而非集体之外。输出包括带有集体知识结构的重新设计任务、社区维度以及集体学习中的个人问责框架。AI 在此尤为有价值，因为设计真正的集体任务（而不是给普通小组作业贴个新标签）需要在根本层面上重构任务结构——确保相互依存是真实的，而非装饰性的。

## 循证基础

Mkabela (2005) 阐述了一种扎根于集体知识生产的非洲中心主义研究方法论，指出在非洲哲学传统中，知识不是私人商品，而是属于社区的共享资源。个体学习者的角色不是为了个人优势而占有知识，而是为社区的集体理解做出贡献。Letseka (2012) 将乌班图辩护为一个具有教育意涵的连贯哲学框架：教育的目的是培养将自己视为与他人根本相连的人——“我们在，故我在（I am because we are）”。这并非抹杀个体的集体主义，而是一种关系本体论，其中个体身份通过社区得以构成。Ramose (2002) 探讨了乌班图作为“存在（be-ing）”的哲学，认为人类存在本质上是共同体式的，教育应当培养这种共同体取向，而非竞争性个人主义。Venter (2004) 专门考察了非洲教育哲学，提炼出核心原则：共同体主义（社区福祉优先于个人私利）、尊重长者与知识持有者、通过参与社区生活来学习，以及教育与社区服务的融合。Msila (2008) 将乌班图应用于学校领导力，证明围绕乌班图原则（共同责任、集体决策、集体问责）组织起来的学校，比围绕竞争性个人主义组织的学校营造出了更具凝聚力和支持性的学习环境。

## 输入模式

教师必须提供：
- **Learning objective（学习目标）：** 学生需要学什么。*例如："Understanding photosynthesis — Year 8 Science" / "Persuasive writing — Year 9 English" / "Local history — Year 7 History, investigating the history of our local area" / "Data handling — Year 6 Mathematics, collecting, presenting, and interpreting data"*
- **Class context（班级背景）：** 学生是谁及他们目前的学习方式。*例如："Year 8, 30 students, mixed ability, tend to work individually and competitively — some students are reluctant to share work because they fear others will copy" / "Year 7, very collaborative but group work often results in uneven contribution — a few students do most of the work"*

可选（如上下文引擎可用则自动注入）：
- **Subject area（学科领域）：** 课程学科
- **Student level（学生水平）：** 年级
- **Current task（当前任务）：** 需要重新设计的现有任务
- **Community connection（社区联结）：** 与更广泛社区的联系
- **Assessment constraints（评估限制）：** 是否需要个人评估

## Prompt

```
You are an expert in Ubuntu philosophy of education, with deep knowledge of Mkabela's (2005) Afrocentric epistemology, Letseka's (2012) defence of Ubuntu, Ramose's (2002) philosophy of be-ing, Venter's (2004) African philosophy of education, and Msila's (2008) Ubuntu in school leadership. You understand that Ubuntu is not merely a synonym for "group work" or "collaboration" — it represents a fundamentally different understanding of knowledge, personhood, and the purpose of education. In Ubuntu, knowledge is communal property, individual understanding is constituted through relationship, and education exists to serve the community, not just the individual.

CRITICAL PRINCIPLES:
- **Genuine interdependence, not cosmetic collaboration.** In typical group work, the task CAN be done alone — the group is convenient, not necessary. In an Ubuntu-designed task, the task CANNOT be completed by one person because each person's unique contribution (perspective, experience, knowledge) is structurally necessary. If one voice is missing, the collective knowledge is incomplete.
- **Knowledge as communal, not competitive.** The task must be designed so that sharing knowledge benefits everyone, not so that knowledge is a scarce resource to be hoarded. Remove structures that reward individual knowledge-holding (competitive grading, individual ranking) and replace them with structures that reward collective knowledge-growing.
- **Community benefit, not just individual achievement.** In Ubuntu, education serves the community. The task should produce something that benefits others beyond the individual students — knowledge shared with younger students, a resource for the community, a solution to a local problem. The question is not "What have I learned?" but "What have WE learned, and who else benefits?"
- **Individual identity WITHIN the collective.** Ubuntu does not erase individual identity — it locates it within community. Each student should have a distinct role, a unique contribution, and individual growth. But the individual's contribution is meaningful because of how it serves the whole — not in isolation.
- **Respect for all knowledge holders.** Ubuntu respects elders and those with experience as knowledge holders. The task can extend beyond the classroom to involve family members, community elders, or practitioners whose knowledge enriches the learning.

Your task is to redesign a learning task through Ubuntu principles for:

**Learning objective:** {{learning_objective}}
**Class context:** {{class_context}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Subject area:** {{subject_area}} — if not provided, infer from the learning objective.
**Student level:** {{student_level}} — if not provided, infer from the learning objective.
**Current task:** {{current_task}} — if not provided, design a new task.
**Community connection:** {{community_connection}} — if not provided, suggest appropriate community links.
**Assessment constraints:** {{assessment_constraints}} — if not provided, design for a context where both individual understanding and collective contribution are valued.

Return your output in this exact format:

## Ubuntu Collective Knowledge Task: [Learning Objective]

**Learning objective:** [What students learn]
**Ubuntu principle:** [The specific Ubuntu principle most central to this task]
**Community benefit:** [How the learning serves others beyond the students themselves]

### Why Collective Knowledge Matters Here

[Brief explanation of why THIS learning objective benefits from collective rather than individual knowledge building — what is gained that individual learning cannot achieve]

### Task Design

**The collective task:** [What the class or group does together — structured so that each person's contribution is genuinely necessary]
**Individual contributions:** [What each student uniquely brings — their specific role, knowledge, or perspective]
**Knowledge integration:** [How individual contributions are woven together into collective understanding]

### Collective Knowledge Structure

[How the task ensures genuine interdependence — what mechanisms prevent the task from being completed by one person alone]

### Community Dimension

[How the learning connects to or serves the wider community — a practical, authentic community element]

### Individual Within Collective

[How individual learning and accountability exist within the collective structure — assessment approach that values both]

### Teacher's Role

[How the teacher facilitates collective knowledge building — different from facilitating group work]

**Self-check before returning output:** Verify that (a) the task requires genuine interdependence, not cosmetic collaboration, (b) knowledge sharing is structurally rewarded, (c) the learning serves someone beyond the individual students, (d) individual identity and contribution are maintained within the collective, and (e) the design is respectful and authentic, not a superficial application of Ubuntu terminology to standard group work.
```

## 示例输出

**场景：** *Learning objective: "Local history — Year 7 History, investigating the history of our local area over the last 100 years" / Class context: "Year 7, 28 students, diverse community — families have been in the area for varying lengths of time, from multiple generations to recently arrived. Students tend to work individually. The school is in an area undergoing rapid change (new housing developments, changing demographics) and there's a mix of long-established and newer communities." / Community connection: "The school has good relationships with a local community centre, a care home, and several places of worship. There are community members who have lived in the area for 50+ years."*

---

## 乌班图集体知识任务：我们社区的故事——一部集体历史

**学习目标：** 调查地方历史——运用一手与二手史料、分析随时间推移的变化、理解历史事件的多重视角
**乌班图原则：** "Umuntu ngumuntu ngabantu" —— 人之为人，因与他人相连。我们社区的历史不是任何个人的故事——它是曾在这里生活过的每一个人的集体故事。没有任何一个人掌握全部历史。只有当许多声音共同贡献时，完整的故事才会浮现。
**社区收益：** 全班共同制作一座“社区记忆档案馆（Community Memory Archive）”——一份包含口述史、照片、地图与分析的馆藏，捐赠给当地社区中心和学校图书馆，作为未来学生与居民的永久资源。

### 为什么集体知识在这里至关重要

地方历史本质上是集体的。没有任何一位学生——也没有任何一本课本——掌握这个社区的历史。历史存在于“人”之中：在老居民的记忆里、在新来者的经历里、在议会保存的档案里、在家庭相册的老照片里、在餐桌上代代相传的故事里。标准的个人历史任务（"Research the history of our area using library resources"）只能产出基于二手资料的个人报告。乌班图取向认识到“社区”本身就是一手史料——而建构这段历史要求每位学生贡献只有他们自己才能获取的知识（他们家庭的故事、他们社区的视角、他们的文化透镜）。

### 任务设计

**集体任务：** 全班共同建立一座“社区记忆档案馆”——通过居住在这里的人们的声音讲述当地百年历史的多层次档案。档案馆包含：
- 口述史访谈（学生采访家庭成员、邻居与社区长者）
- 批注地图（展示该地区如何变化，附带居民的个人批注）
- 本地重要事件时间轴，从“多元”视角建构（同一事件在不同社区视角下可能呈现截然不同的面貌）
- 反思性分析："What has this community gained and lost over the last 100 years, and who decides?"

**个体贡献：** 每位学生至少对一位家庭成员或社区联系人进行一次口述史访谈，贡献一个“没有其他学生能够提供”的独特视角。家族在此居住三代的学生带来长期记忆；新近迁入的家庭带来新来者的视角——是什么吸引他们来到这里、他们发现了什么、他们如何被接纳；来自特定信仰社区的学生带来该社区的故事。每一个故事都不可或缺，因为缺少任何一个声音，档案馆都是残缺的。

**知识整合：** 学生将各自的访谈与发现带入“知识圆圈”（5–6 人小组）。每个圆圈综合组内贡献：浮现了哪些共同主题？故事在哪些地方一致？在哪些地方存在分歧？随后各圆圈向全班分享，全班共同构建一条集体时间轴，其中“同一个”事件旁会标注多个视角。例如，新建住宅区的落成可能被一个家庭记为“进步”，却被另一个家庭记为“我们玩耍的那片绿地的终结”。

### 集体知识结构

**为什么一个人无法独自完成：**
1. **每位学生的家庭/社区联结都是独一无二的。** 只有 Amara 能采访她在商业街开了 40 年杂货店的祖母；只有 Jakub 能采访他父母 2008 年从波兰迁来时的经历；只有 Priya 能接触到寺庙社区建造第一座永久礼拜场所的记忆。知识分散在社区之中，通过关系而非单纯检索来获取。

2. **综合分析需要多元视角。** 集体时间轴只有包含多种甚至相互矛盾的观点时，才能揭示地方历史的复杂性。由单一视角建构的历史是片面的。乌班图原则在此具有结构性意义：集体理解大于任何个体贡献之和。

3. **档案馆的体量超越个人能力。** 实体成果——访谈、地图、照片、分析——需要许多双手共同完成，但更重要的是，它需要许多“关系”。档案馆的价值正存在于它所容纳的声音之广度。

### 社区维度

**服务社区，而不仅仅是完成作业：**

1. **作为馈赠与服务的口述史。** 访谈不只是数据采集——它们是“认可”的行动。社区长者的记忆得到珍视、保存与致敬。对于当地养老院的老年居民而言，被一位真诚想听自己故事的年轻人采访，本身就极具意义。

2. **作为社区资源的档案馆。** 完工的档案馆被印制/数字化并捐赠给社区中心和学校图书馆。举办“社区记忆之夜”，邀请受访者与社区成员前来观看他们的故事呈现。这不是一场校内集会——这是一场将知识归还给产出它的社区的社区活动。

3. **持续生长的资源。** 未来的七年级班级可以继续向档案馆添砖加瓦，使其成为一份不断生长的活态集体记忆文献。第一届开启传统，后续班级延续传统。

### 集体中的个体

**个体学习：**
- 每位学生发展历史学科技能：开展口述史访谈（一手史料创作）、分析口述证言（可靠性、视角、偏见）、从证据中构建叙事
- 每位学生撰写个人反思："What did I learn from my interview that I couldn't have learned from a textbook? What did I learn from my classmates' interviews that I couldn't have learned from my own?"

**集体中的个人问责：**
- 每位学生对自己的访谈负责（是否准备了问题、是否尊重地进行了采访、是否转录了关键段落、是否将发现带回小组？）
- 每位学生向档案馆提交一份对自身访谈的书面分析
- 采用双重评估：个人访谈的质量“以及”个人对集体综合的贡献质量。两者缺一不可。

**评估方案：**
| 评估要素 | 个人还是集体 | 它展示了什么 |
|---|---|---|
| 口述史访谈（准备、实施、转录） | 个人 | 历史探究技能、对史料的尊重 |
| 访谈书面分析 | 个人 | 分析技能、得出历史结论的能力 |
| 对知识圆圈综合的贡献 | 教师观察 | 倾听、整合、贡献于集体理解的能力 |
| 集体档案馆板块质量 | 集体（小组评估） | 将多重视角综合为连贯历史的能力 |
| 个人反思 | 个人 | 对集体学习与个体学习差异的元认知觉察 |

### 教师的角色

乌班图任务中的教师不是“小组作业协调员”——而是“社区连接者”与“知识编织者”：

1. **任务前：** 联系社区中心与养老院安排采访渠道。致信家庭解释项目并邀请参与。物色乐意接受采访的社区成员。

2. **任务中：** 示范尊重他人的访谈方式。帮助学生准备符合文化礼仪的访谈做法（部分社区对与长者交谈可能有特定礼仪）。走访知识圆圈倾听并提出深化综合的问题："I notice Amara's story and Jakub's story describe the same street but with completely different feelings about it. Why might that be?"

3. **整合阶段：** 帮助学生驾驭相互矛盾的视角所带来的复杂性。在乌班图中，分歧不是需要消除的问题，而是值得珍视的丰富性："Both stories are true. The history of this place contains both experiences."

4. **社区之夜：** 帮助学生怀着尊重与感恩展示他们的档案馆。确保受访者得到致敬——他们的名字、他们的故事、他们对集体知识的贡献。

---

## 已知局限性

1. **乌班图是一种哲学，而不是一种教学技巧。** 将乌班图原则应用于课堂任务设计是一种阐释——它借鉴了哲学传统，但不可避免地为特定教育语境作了调适。教师应当将乌班图理解为一种丰富的哲学框架，而不要将其简化为“花哨的小组作业”。阅读 Letseka、Ramose 和 Mkabela 的著作能提供任务模板所无法提供的深度。

2. **乌班图存在于特定文化语境之中。** 尽管共同体知识、关系身份和集体责任等原则具有广泛适用性，但乌班图植根于特定的南部非洲哲学传统。在英国或其他西方课堂中应用它需要文化敏感度——应当在“理解”该哲学传统的基础上实施，而非文化挪用。承认其渊源并怀着敬意对待这一哲学至关重要。

3. **集体知识建构比个人学习耗时更多。** 上述档案馆任务比常规地方史单元耗时显著更长。它所产出的深度与社区参与值得这份时间投入，但面临紧凑课程进度的教师可能需要作出调整。并非每项任务都必须集体化——乌班图原则可以指导“部分”任务，同时保留另一些个人任务。

4. **个人评估体系可能与集体学习产生冲突。** 如果学校要求每一份作业都给出个人分数，集体维度就可能被削弱。上述评估框架试图同时兼顾个人与集体贡献，但在最终将一切还原为个人分数的体系中，集体维度仍可能被贬低。这是制度局限，而非设计局限。
