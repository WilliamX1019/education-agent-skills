---
# AGENT SKILLS STANDARD FIELDS (v2)
name: prepared-environment-designer
description: "将教室重新设计为“有准备的环境”，优化独立学习、平静过渡与材料取用。适用于教室布局阻碍独立性或自主学习时。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "montessori-alternative-approaches/prepared-environment-designer"
skill_name: "有准备的环境设计器"
domain: "montessori-alternative-approaches"
version: "1.0"
evidence_strength: "moderate"
evidence_sources:
  - "Lillard (2005) — Montessori: The Science Behind the Genius"
  - "Cossentino (2006) — Big work: goodness, volitional action, and the classroom environment in Montessori method"
  - "Barrett et al. (2015) — The impact of classroom design on pupils' learning: final results of a holistic, multi-level analysis (HEAD project)"
  - "Fisher et al. (2014) — Visual environment, attention, and learning in young children: when too much of a good thing may be bad"
  - "Lillard & Else-Quest (2006) — Evaluating Montessori education (Science)"
input_schema:
  required:
    - field: "current_environment"
      type: "string"
      description: "当前教室或学习空间的描述——外观、组织方式、可用材料以及存在的问题"
    - field: "improvement_goals"
      type: "string"
      description: "教师希望通过重新设计环境实现的目标——更平静的过渡、更多独立工作、更顺畅的材料取用或其他具体目标"
  optional:
    - field: "student_level"
      type: "string"
      description: "年龄/年级与发展阶段"
    - field: "budget"
      type: "string"
      description: "可用于改造的预算——从零成本到较大投入"
    - field: "space_constraints"
      type: "string"
      description: "固定限制——房间大小、固定家具、窗户、门、共享空间"
    - field: "curriculum_context"
      type: "string"
      description: "属于蒙台梭利学校、希望采纳部分原则的常规学校，还是家庭学习环境"
    - field: "time_for_implementation"
      type: "string"
      description: "改造需要多快完成——一个周末、一学期内逐步完成，还是假期期间"
output_schema:
  type: "object"
  fields:
    - field: "environment_audit"
      type: "object"
      description: "对照蒙台梭利“有准备的环境”原则对当前空间的分析——哪些有效，哪些无效"
    - field: "redesign_plan"
      type: "object"
      description: "推荐的具体改动——按优先级与成本组织"
    - field: "implementation_sequence"
      type: "array"
      description: "改动顺序——先做什么、什么可以延后"
    - field: "maintenance_protocol"
      type: "object"
      description: "如何长期维护有准备的环境——常规程序、责任分工与更新周期"
chains_well_with:
  - "three-part-lesson-designer"
  - "uninterrupted-work-cycle-designer"
  - "mixed-age-learning-task-designer"
  - "biophilic-learning-environment-designer"
teacher_time: "5 分钟"
tags: ["Montessori", "prepared-environment", "classroom-design", "Lillard", "Cossentino", "accessibility", "order", "beauty", "materials"]
---

# 有准备的环境设计器

## 本技能的功能

对照蒙台梭利“有准备的环境（prepared environment）”原则评估教室或学习空间，并生成切实可行的改造计划。有准备的环境是蒙台梭利最具特色且影响深远的贡献之一：认为物理空间**本身就是**课程——精心设计的环境能邀请学习、支持独立性并减少对教师指令的依赖。Lillard（2005）确立了核心原则：可及性（儿童能独立够到并选择材料）、秩序（每样物品都有固定位置并在使用后归位）、美感（环境具有审美愉悦感，使用自然材料与精心设计）、真实材料（功能性物品而非玩具——真玻璃、真工具、真植物）以及儿童尺度（家具与材料尺寸适合使用它们的儿童）。Cossentino（2006）补充了“大工作（big work）”概念——环境应当邀请持续、有意义的投入，而非快速、零散的活动。本技能之所以尤为有价值，是因为环境设计是拥有最多独立支持证据的蒙台梭利原则之一：Barrett 等人（2015）发现，教室设计因素（光线、温度、空气质量、归属感、灵活性、复杂度与色彩）解释了学生学习进步方差的 16%——对于单一变量而言这是相当可观的效应。Fisher 等人（2014）发现，视觉杂乱的教室显著降低了儿童的注意力与学习成绩，为蒙台梭利强调视觉秩序提供了直接的实证支持。

## 循证基础

Lillard（2005）从认知科学视角对“有准备的环境”进行了最全面的分析。她指出，蒙台梭利的环境设计原则与以下研究高度契合：（a）具身认知——儿童通过与材料的身体互动来学习，因此材料必须易于取用且具有吸引力；（b）执行功能——具有清晰常规的有序环境支持自我调节能力的发展；（c）注意力——视觉平静、展示有目的性的环境能减少分心并支持持续专注；（d）内在动机——儿童自主选择工作的环境支持自主性与投入度。Cossentino（2006）对蒙台梭利教室进行了民族志研究，将“大工作”确定为有准备的环境的标志性特征。环境的设计使得最具吸引力、挑战性与意义的活动处于最显眼、最易触及的位置——儿童是被空间设计而非教师指令吸引向深度工作的。Cossentino 发现，环境的审美品质传递了对儿童工作的尊重，并营造出一种关爱与匠心的文化。Barrett 等人（2015）开展了 HEAD（整体证据与设计）研究——迄今为止规模最大的教室设计与学习成果研究。他们评估了27所英国学校的153间教室，发现教室设计解释了一学年内学生学习进步方差的 16%。最具影响力的因素包括自然性（光线、温度、空气质量）、个性化（归属感、灵活性）以及刺激度（复杂度、色彩）。最优教室拥有良好的自然采光、适度的视觉复杂度（既不空洞也不杂乱）以及学生归属感的体现。这些发现独立印证了多项蒙台梭利原则：自然光、视觉秩序（适度复杂度）以及学生对空间的归属感。Fisher 等人（2014）通过实验测试了教室视觉环境对幼儿园儿童学习的影响。他们发现，在重度装饰的教室（墙面贴满海报、地图、手工作品）中，儿童分心的时间显著多于简洁教室，且学习评估得分更低。效应十分显著：重度装饰教室的分心时间占比为 38.6%，而简洁教室为 28.4%。这为蒙台梭利“环境应视觉有序且有目的性，而非视觉过载”的原则提供了直接实证支持。

## 输入模式

教师必须提供：
- **当前环境：** 空间现在的样子。*例如：“一年级教室，约60平方米。桌子排成6组，每组4人。讲台在前方，配有交互式白板。墙上贴满商业海报、奖励榜和上学期学生作品（边缘卷曲）。材料装在带标签的塑料盒里放在高架子上——儿童取用大多数资源都需请成人帮忙。一角有地毯区用于全班授课。衣帽钩和书包把狭窄的走廊入口堵得杂乱不堪” / “供3个孩子（4岁、7岁、10岁）使用的家庭学习室。由小卧室改造。有宜家书架、一张桌子和三把椅子。目前沦为杂物堆放处”*
- **改进目标：** 教师希望实现什么。*例如：“孩子们总是向我索要材料——我希望他们能独立取用资源。活动之间的过渡要花10分钟。房间感觉很混乱，我觉得这影响了行为” / “我希望有一个空间，让三个孩子能同时各自做不同的事，不吵架也不需要时刻监督”*

可选（如有，由上下文引擎注入）：
- **学生水平：** 年龄/年级
- **预算：** 可用于改造的资源
- **空间限制：** 房间的固定特征
- **课程背景：** 蒙台梭利、常规学校或家庭
- **实施时间：** 改动需要多快落地

## 提示词

```
You are an expert in learning environment design, with deep knowledge of Montessori prepared environment principles (Lillard, 2005; Cossentino, 2006), Barrett et al.'s (2015) HEAD study on classroom design and learning outcomes, and Fisher et al.'s (2014) research on visual environment and attention. You understand that the physical environment is not neutral — it actively shapes behaviour, attention, and learning. A well-designed space invites independence, sustains focus, and communicates respect. A poorly designed space creates dependence, fragmentation, and low-level disruption.

CRITICAL PRINCIPLES:
- **Accessibility.** Children must be able to reach, choose, and return materials independently. If a child needs an adult to access a resource, that resource is not truly available to them. Shelves at child height, open (not closed) storage, and a clear organisational system are essential.
- **Order.** Everything has a defined place. Every material has a specific location on a specific shelf, and children know where it belongs. Order is not rigidity — it is freedom. When children know where things are, they don't need to ask. When they know where things go back, they develop responsibility. Barrett et al. (2015) found that visual order (moderate complexity, not bare or cluttered) was associated with better learning outcomes.
- **Beauty.** The environment should be aesthetically pleasing — not decorated, but DESIGNED. Natural materials (wood, wicker, cotton, glass) over plastic. Plants. Clean lines. Purposeful displays (current student work, reference materials) rather than commercial decoration. Cossentino (2006) found that aesthetic care communicated respect for children's work.
- **Real materials.** Montessori environments use functional objects: real glass (children learn to carry carefully), real tools (child-sized brooms, real cooking utensils), real plants (children care for them). This develops practical life skills AND communicates trust. Fisher et al. (2014) found that reducing visual clutter improved attention — real, purposeful materials contribute to visual clarity; plastic decorative items contribute to clutter.
- **Child scale.** Furniture and materials should be sized for the children. Tables they can sit at without dangling feet. Shelves they can reach without stretching. Sinks they can use independently. This is not just ergonomic — it communicates that the space belongs to THEM.
- **Defined work areas.** Different areas for different types of work: a quiet reading corner, a practical life area, a maths materials shelf, an art space. The physical layout communicates what happens where, reducing the need for verbal instruction.

Your task is to evaluate and redesign this learning environment:

**Current environment:** {{current_environment}}
**Improvement goals:** {{improvement_goals}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Student level:** {{student_level}} — if not provided, infer from the description.
**Budget:** {{budget}} — if not provided, begin with zero-cost changes and indicate which improvements require investment.
**Space constraints:** {{space_constraints}} — if not provided, assume standard constraints (fixed walls, one door, windows on one side).
**Curriculum context:** {{curriculum_context}} — if not provided, design for a conventional school wanting to adopt prepared environment principles (not a full Montessori conversion).
**Time for implementation:** {{time_for_implementation}} — if not provided, design a phased implementation starting with quick wins.

Return your output in this exact format:

## Prepared Environment Redesign: [Space Description]

**Current space:** [Summary of what exists]
**Goals:** [What the redesign should achieve]
**Approach:** [Full Montessori conversion or selective adoption of principles]

### Environment Audit

[Evaluate the current space against each Montessori principle. Be specific — what works and what doesn't, with reference to the evidence.]

| Principle | Current State | Rating | Key Issue |
|---|---|---|---|
| Accessibility | [Description] | [Strong/Adequate/Weak] | [Main problem] |
| Order | [Description] | [Strong/Adequate/Weak] | [Main problem] |
| Beauty | [Description] | [Strong/Adequate/Weak] | [Main problem] |
| Real Materials | [Description] | [Strong/Adequate/Weak] | [Main problem] |
| Child Scale | [Description] | [Strong/Adequate/Weak] | [Main problem] |
| Defined Areas | [Description] | [Strong/Adequate/Weak] | [Main problem] |

### Redesign Plan

**Phase 1: Zero-Cost Quick Wins (this weekend)**
[Changes that cost nothing — rearranging, removing, reorganising]

**Phase 2: Low-Cost Improvements (under £50)**
[Small purchases that make a significant difference]

**Phase 3: Investment Changes (if budget allows)**
[Larger changes that require more resources]

### Implementation Sequence

[The specific order of changes — what to do first and why]

### Maintenance Protocol

[How to maintain the prepared environment — daily routines, weekly checks, and how to involve students in environment care]

### Before and After

[A clear description of the key differences the teacher will see — the specific changes to daily life in the classroom]

**Self-check before returning output:** Verify that (a) all six principles are addressed, (b) changes are phased by cost and effort, (c) the redesign is practical for the given constraints, (d) maintenance is addressed, and (e) the changes serve the stated improvement goals.
```

## 示例输出

**场景：** *当前环境：“一年级教室（5-6岁），约60平方米。六张长方形桌子排成4人一组（共24名学生）。讲台在前方，紧邻交互式白板。墙上贴满商业识字与算术海报、行为奖励榜、生日展示墙，以及上学期的学生作品（边缘卷曲，有的正在掉落）。材料装在带标签的塑料盒里，沿着两面墙放在高架子上——儿童需要请成人帮忙才能取用大多数资源，包括铅笔，因为‘他们老是弄丢’，所以铅笔锁在柜子里。一角铺有大地毯作为全班教学区。衣帽钩在狭窄的走廊入口处——地上的书包造成绊倒隐患。一面有窗（朝西）。荧光吸顶灯。塑料椅子，有些摇晃。” / 改进目标：“孩子们总是向我要材料——我希望他们能独立取用资源。活动间的过渡要花10分钟，因为孩子们要排队领放材料。房间让人感觉视觉上不堪重负，我认为这影响了行为——我有4个孩子很难集中注意力。我希望房间感觉更平静，孩子们更独立” / 预算：“本学期100英镑，下学期可能更多” / 课程背景：“公立小学，非蒙台梭利——但我想采纳在我情境中行之有效的原则”*

---

## 有准备的环境改造：一年级教室

**当前空间：** 60平方米一年级教室，24名儿童，分组桌椅，高架子，上锁的铅笔，重度墙面装饰，杂乱的入口
**目标：** 独立取用材料、更快的过渡、更平静的视觉环境、提升专注力
**路径：** 在公立小学情境下选择性采纳蒙台梭利“有准备的环境”原则——非全面转型，但对可及性、秩序与视觉环境进行显著改造

### 环境审计

| 原则 | 当前状态 | 评级 | 核心问题 |
|---|---|---|---|
| 可及性 | 材料放在高架子上，铅笔上锁，儿童必须询问成人 | 弱 | 儿童完全依赖成人获取资源——造成排队、延误以及习得性无助 |
| 秩序 | 材料贴有标签但够不到；没有明确的归还系统 | 弱 | 当儿童无法接触架子时标签形同虚设。缺乏将材料放回原位的常规 |
| 美感 | 商业海报、卷曲的学生作品、奖励榜、生日墙 | 弱 | 每个表面都在制造视觉杂乱。Fisher 等人（2014）：重度装饰房间使分心行为增加约10%。没有任何元素邀请持续凝视或传递关爱 |
| 真实材料 | 塑料储物盒、塑料椅子、化纤地毯 | 尚可 | 标准学校配置。缺少自然材料，但功能完备。更大的问题在于可及性，而非材料质感 |
| 儿童尺度 | 桌子高度合适，但架子太高。椅子摇晃但尺寸适合儿童 | 尚可 | 主要问题是架子高度。家具虽不够美观但具备功能性 |
| 功能分区 | 教学地毯区、作业桌——但没有其他明确区域 | 弱 | 只有两种模式：“在地毯上”和“在桌子旁”。没有阅读角、没有安静区、没有操作区。房间支持全班和小组作业，但不支持自主选择 |

### 改造计划

**第一阶段：零成本快速见效（本周末完成）**

1. **解锁铅笔。** 将铅笔、蜡笔、尺子和剪刀放在每组桌子上的敞口容器里（每桌一个笔筒或托盘）。如果孩子“弄丢”铅笔，这是一个可解决的管理问题——在每次活动结束时训练“铅笔检查”常规。把资源锁起来传递的是不信任并制造依赖。*效果：消除最大单一瓶颈。*

2. **将材料移至儿童高度。** 把塑料盒从高架子上拿下来，放到低层架子、地面层或桌面上。如果低层架子空间有限，优先把最常用的材料放在儿童高度，极少使用的材料留在高处。儿童在常规课上需要的每一种材料都应无需询问即可触及。*效果：消除取用材料的排队现象。*

3. **清理墙面。** 移除**所有**商业海报、奖励榜、生日展示墙以及任何卷曲、褪色或上学期的学生作品。让墙面几乎保持空白。这起初会让人觉得激进，房间会显得“空荡荡”——这正是正确的。Barrett 等人（2015）：适度的视觉复杂度是最优的。Fisher 等人（2014）：减少墙面装饰改善了注意力与学习。你可以**有选择地**重新张贴——见第二阶段。*效果：立即减轻视觉过载。接下来一周观察那4名专注困难的儿童。*

4. **划分明确的安静角。** 把地毯移到一个角落。把书架（从房间别处挪过来）作为部分隔断。在架子上封面朝外摆放 10–15 本精心挑选的绘本。这里成为阅读/安静区。物理边界传达出：“这是一种不同性质的空间。”*效果：儿童现在有了一个可以去进行安静、专注工作的地方。*

5. **清理入口。** 把书包移到衣帽钩下方（挂钩或简易置物架）。如果书包放不下，发信请家长改用扁平书包袋而非大双肩包。入口定下全天基调——绊倒隐患从一天第一刻起就在传递混乱。*效果：更平静的入班常规。*

**第二阶段：低成本改进（100英镑以内）**

6. **开放式置物托盘（20–30英镑）。** 用低架上的敞口托盘或篮子替换几个高处塑料盒。每个托盘只盛放**一套**完整活动或资源。每个托盘贴上实物照片和文字标签。儿童无需打开任何盖子就能看见里面是什么。*效果：儿童可以视觉化地选择材料，而不用去读封闭盒子上的文字标签。*

7. **桌面绿植（10–15英镑）。** 每组桌子放一盆小植物——绿萝、吊兰或多肉植物。指派每桌负责给自己的植物浇水。这服务于多重目的：自然元素（Barrett 等人 2015 发现自然元素提升幸福感）、美感、责任感以及爱护环境的温和启蒙。*效果：视觉改善、儿童归属感、生活实践技能。*

8. **精选墙面展示（10–15英镑用于相框或边框）。** **仅**重新张贴：（a）儿童实际使用的当前参考资料（数轴、字母书写示范卡、当前主题的工作墙），以及（b）4–5件装裱工整的学生作品，每两周轮换一次。展示的每样东西都应有明确目的且保持时效性。不做纯粹为了装饰的张贴。*效果：墙面成为学习工具，而非壁纸。*

9. **材料归位常规。** 教授明确常规：用完一项材料后，将其放回架子上的**精确**原位。用三段式教学法练习一周：向儿童展示物品放哪里（第一段），请他们归还特定物品（第二段），检查他们能否独立找到并归还物品（第三段）。这是对独立性的投资。*效果：常规建立后，10分钟的过渡会缩短至2–3分钟。*

**第三阶段：投资性改动（如下学期预算允许）**

10. **用暖色 LED 替换荧光灯或添置台灯/落地灯（50–150英镑）。** 荧光灯产生刺眼均匀的照明和轻微频闪，部分儿童会感到烦躁。如果无法更换吸顶灯，添置 2–3 盏落地灯或台灯营造温暖光区，并关掉部分顶灯管。*效果：更平静的氛围，尤其有利于感官敏感的儿童。*

11. **低矮开放式书架单元（50–100英镑）。** 将一个专门的矮架单元（如宜家 Kallax）垂直于墙面摆放，既能储物又能充当空间隔断——在不阻挡视线的前提下界定出工作区。*效果：创造出带有可及储物空间的明确功能区。*

12. **用圆凳或地板坐垫替换 2–3 把摇晃的椅子（30–50英镑）。** 提供座位**选择**：标准椅子、圆凳或地板坐垫。部分儿童在能轻微晃动（圆凳）或坐得更低（坐垫）时专注力更好。这是儿童尺度思维在座位上的应用。*效果：满足难以在标准椅子上久坐不动儿童的需求。*

### 实施顺序

| 周末/周次 | 行动 | 投入精力 | 预期效果 |
|---|---|---|---|
| 本周末 | 解锁铅笔、将材料移至儿童高度、清理墙面、设立安静角、清理入口 | 3–4小时 | 立竿见影：更平静的视觉环境、更快的材料取用 |
| 第1周 | 教授材料归位常规（每天5分钟练习） | 每天5分钟，共5天 | 周末前过渡时间显著缩短 |
| 第2周 | 观察与调整——记录哪些材料需调位置、哪些儿童需额外常规练习 | 仅观察 | 基于数据的微调 |
| 第3–4周 | 添置桌面植物、精选墙面展示、敞口托盘 | 40–50英镑，2小时布置 | 视觉温暖感回归（有目的，而非杂乱） |
| 下半学期 | 灯光调整、矮架单元、座位选择 | 100–150英镑 | 更深层次的环境质量提升 |

### 维护规程

**每日（由儿童完成）：**
- 时段结束整理：每个孩子把材料放回正确位置。一旦形成常规，只需2–3分钟。由一名“架子管理员”检查每个架子是否整洁正确。
- 植物检查：桌面植物是否已浇水且健康？

**每周（由教师完成）：**
- 快速架子审计：材料是否在正确位置？是否有破损、缺失或不再需要的物品？
- 展示检查：工作墙是否保持最新？是否有学生作品需要轮换？

**每半学期（教师 + 儿童）：**
- 空间复盘：“我们教室里哪些地方好用？哪些不好用？我们应该改什么？”让儿童参与环境决策——蒙台梭利的儿童归属感原则同样延伸到空间本身。
- 材料轮换：撤下不再使用的材料（已结束主题的资源）并引入新材料。精挑细选的小规模陈列远胜于令人眼花缭乱的堆砌。

### 改造前后对比

**改造前：** 孩子们在讲台前排队要铅笔。墙面从每个角落都在高声尖叫着色彩。24个孩子同时试图从高架子上拿材料，过渡耗时长达10分钟。房间显得拥挤而混乱。四个孩子难以集中注意力。

**改造后：** 每张桌子上都有铅笔——孩子们拿起来就开始工作。墙面平静：一条数轴、一面工作墙和五件装裱妥当的学生作品。材料放在矮架上——孩子们自己挑选并在用完后放回。过渡只需2–3分钟，因为孩子们知道每样东西去哪里。这里有一个安静的阅读角供孩子自主选择。每桌的绿植增添了生机。房间让人感到有目的性且平静。

最大的改变不是视觉上的——而是行为上的。以前事事请示的孩子现在开始独立行动。以前忙于管理物资后勤的教师现在可以专心教学。

---

## 已知局限

1. **“有准备的环境”的证据在通用教室设计原则方面比专门针对蒙台梭利设计的更为坚实。** Barrett 等人（2015）和 Fisher 等人（2014）支持视觉秩序、自然光和适度复杂度原则——但他们的研究是在常规教室而非蒙台梭利环境中进行的。Lillard（2005）和 Cossentino（2006）提供了专门针对蒙台梭利的证据，但主要属于质性与观察性研究而非实验研究。通用教室设计研究与蒙台梭利专项分析的结合提供了强有力的学理支撑，但作为一个完整系统的“有准备的环境”尚未经过随机对照试验的检验。

2. **环境设计效应难以与教学效应完全剥离。** Lillard 等人（2006）的研究发现蒙台梭利项目具有积极成效，但这些项目将有准备的环境与特定教学实践（三段式教学、混龄分组、无打断工作周期）结合在了一起。从研究设计中无法将环境的独立贡献与教学的独立贡献完全分离开来。

3. **学校政策可能限制环境改动。** 许多学校对墙面展示有硬性规定（识字工作墙、数学展示、行为榜），对安全有规定（可能禁止真玻璃），对家具有规定（由统一采购系统配发的标准化桌椅）。上述改造计划应在不与学校政策冲突的前提下灵活适配，而非硬碰硬。

4. **初期过渡可能会暂时加剧混乱。** 当习惯于事事请示许可的孩子突然获得对材料的自由取用权时，可能会出现一段时期的过度使用、凌乱或试探边界。这是正常且暂时的。材料归位常规（第二阶段第9步）正是为此而设，但教师应预留1–2周的适应期。
