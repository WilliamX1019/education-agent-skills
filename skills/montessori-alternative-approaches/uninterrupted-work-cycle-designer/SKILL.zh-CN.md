---
# AGENT SKILLS STANDARD FIELDS (v2)
name: uninterrupted-work-cycle-designer
description: "在现实时间段内设计包含自主选择活动结构的无打断工作周期。适用于规划蒙台梭利式独立工作时段或延长自主选择时间。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "montessori-alternative-approaches/uninterrupted-work-cycle-designer"
skill_name: "无打断工作周期设计器"
domain: "montessori-alternative-approaches"
version: "1.0"
evidence_strength: "moderate"
evidence_sources:
  - "Lillard (2005) — Montessori: The Science Behind the Genius"
  - "Lillard & Else-Quest (2006) — Evaluating Montessori education (Science)"
  - "Rosenshine (2012) — Principles of instruction: research-based strategies that all teachers should know (time-on-task)"
  - "Csikszentmihalyi (1990) — Flow: the psychology of optimal experience"
  - "Diamond & Lee (2011) — Interventions shown to aid executive function development in children 4-12 years old"
input_schema:
  required:
    - field: "available_time"
      type: "string"
      description: "实际可用的时间段——课表允许的无打断时间现实长度"
    - field: "learning_activities"
      type: "string"
      description: "学生在工作周期内可选择的活动范围——架子上、学习站或环境中提供的材料"
  optional:
    - field: "student_level"
      type: "string"
      description: "年龄/年级与发展阶段"
    - field: "class_size"
      type: "string"
      description: "教室内的学生人数"
    - field: "current_routines"
      type: "string"
      description: "教室目前的运作方式——过渡发生频率、学生通常工作多久后切换任务"
    - field: "teacher_concerns"
      type: "string"
      description: "教师的顾虑——分心行为、部分学生不选有挑战性的工作、问责顾虑"
    - field: "environment_setup"
      type: "string"
      description: "房间如何组织——材料是否易于取用、工作区是否界定清晰"
output_schema:
  type: "object"
  fields:
    - field: "work_cycle_design"
      type: "object"
      description: "完整的工作周期结构——开场、工作时段与收尾，以及教师在各阶段的角色"
    - field: "materials_rotation"
      type: "object"
      description: "材料如何组织、轮换与更新——提供什么以及学生如何选择"
    - field: "teacher_observation_protocol"
      type: "object"
      description: "教师在工作周期内做什么——如何观察、何时介入以及如何记录观察结果"
    - field: "transition_management"
      type: "object"
      description: "学生如何进入和退出工作周期——支持平稳过渡的常规"
chains_well_with:
  - "prepared-environment-designer"
  - "three-part-lesson-designer"
  - "mixed-age-learning-task-designer"
  - "self-regulated-learning-designer"
teacher_time: "5 分钟"
tags: ["Montessori", "work-cycle", "uninterrupted", "flow", "Csikszentmihalyi", "time-on-task", "Rosenshine", "executive-function", "choice"]
---

# 无打断工作周期设计器

## 本技能的功能

设计一个无打断工作周期——一段持续的自主学习时间，学生从有准备的环境中自主选择活动，并在没有预定打断的情况下工作。在蒙台梭利实践中，工作周期通常为3小时——是所有主流教育模式中单次最长的无打断时间块。Lillard（2005）指出，这段延长的工作时间对于深度投入至关重要：儿童需要时间安定下来、选择有意义的工作、维持专注力，并体验完成后的满足感。Csikszentmihalyi（1990）将这种状态描述为“心流（flow）”——即挑战与技能相匹配、注意力完全沉浸、时间感消失的最优体验状态。工作周期正是为了创造进入心流的条件而设计的。然而，在常规学校环境中，3小时时间块在实践上最具挑战性，因为课表通常被划分为 40–60 分钟的课时，且节与节之间存在过渡。本技能针对教师**实际**可用的时间来设计工作周期——无论是完整的3小时、90分钟的连堂课，还是60分钟的适配版——并包含使工作周期富有成效而非陷入混乱的材料轮换、教师观察规程和过渡管理。

## 循证基础

Lillard（2005）对蒙台梭利工作周期的科学基础进行了最详尽的分析。她指出了多重机制：（a）延长的时间允许儿童经历蒙台梭利所观察到的典型“工作曲线”——最初的安定阶段（5–15分钟的轻度活动），随后投入具挑战性的工作，接着进入深度专注期，最后在挑选新工作前体验满足与休息；（b）无打断时间消除了过渡的认知代价——每次打断都要求儿童停下、脱离、身体移动、重新定向并重新投入，每次都会丢失工作记忆内容；（c）工作周期内的选择权支持内在动机——自主选择工作的儿童比被指派工作的儿童投入度更高（Deci & Ryan, 2000）；（d）长时段支持执行功能的发展——儿童必须规划、启动、维持并完成自己的工作，在受支持的环境中练习自我调节。Lillard 与 Else-Quest（2006）发现，蒙台梭利项目中的儿童相比匹配对照组展现出更优越的执行功能——Diamond 与 Lee（2011）指出这一发现与蒙台梭利对自主活动和持续专注的强调高度一致。尽管无打断工作周期的独立贡献无法从其他蒙台梭利实践中剥离，但执行功能发展是理论上与工作周期结构关联最紧密的成果。Rosenshine（2012）将“任务专注时间（time-on-task）”列为其十项有效教学原则之一。教学时间与学习之间的关系已充分确立：更多的专注投入时间带来更多学习（前提是活动具有恰当挑战性）。蒙台梭利工作周期通过消除过渡以及允许儿童按自身节奏开展自选活动，最大化了专注时间——减少了常规课表中因排队、等待指令和换教室而累积的“无效时间”。Csikszentmihalyi（1990）描述了心流这一心理状态——全神贯注于具挑战性的活动、忘却时间流逝并体验深层满足感。心流需要多项条件：明确目标、即时反馈、挑战与技能的平衡，以及——至关重要的——无打断时间。Csikszentmihalyi 发现心流通常需要 15–20 分钟才能进入，且极易被外部打断破坏。在40分钟的课上，学生可能刚进入心流就被下课铃拉了出来。3小时的时间块则为多个心流周期提供了时间空间。

## 输入模式

教师必须提供：
- **可用时间：** 实际可用的时间段。*例如：“完整的3小时蒙台梭利上午工作周期，8:30–11:30” / “连堂课：90分钟（五年级，周三上午）” / “60分钟课（我的课表允许的最长无打断时间块）” / “2.5小时，但10:00有20分钟的强制全校集会打断”*
- **学习活动：** 学生可选择的内容。*例如：“完整蒙台梭利环境：开放架上的日常生活、感官、语言、数学与文化材料” / “数学与读写活动：6个数学站与4个读写站，外加独立阅读” / “主题式：与‘热带雨林’主题相关的8项活动，涵盖研究任务、创意表达与数据分析”*

可选（如有，由上下文引擎注入）：
- **学生水平：** 年龄/年级
- **班级规模：** 学生人数
- **当前常规：** 教室目前的运作方式
- **教师顾虑：** 对实施无打断工作时间的担忧
- **环境布置：** 房间是如何组织的

## 提示词

```
You are an expert in the Montessori uninterrupted work cycle and the cognitive science of sustained engagement, with deep knowledge of Lillard's (2005) analysis of the work cycle, Csikszentmihalyi's (1990) flow theory, Rosenshine's (2012) time-on-task research, and Diamond & Lee's (2011) executive function research. You understand that the uninterrupted work cycle is one of the most powerful — and most challenging — aspects of Montessori practice. You also understand that many teachers want to adopt this principle but face real constraints: fixed timetables, mandatory interruptions, accountability pressures, and anxiety about student behaviour during extended self-directed time.

CRITICAL PRINCIPLES:
- **Design for the ACTUAL time available.** The Montessori ideal is 3 hours. Most conventional schools cannot provide this. Design the best possible work cycle for the time the teacher actually has — even 60 minutes of uninterrupted, self-directed work is dramatically better than 60 minutes chopped into four 15-minute segments.
- **The opening routine matters enormously.** How students enter the work cycle determines whether they settle quickly into purposeful work or drift aimlessly for 20 minutes. A clear, calm opening routine (gather briefly, review choices, set personal goals, begin) sets the tone. Montessori children learn this routine over weeks; conventional students need explicit teaching.
- **The teacher's role is OBSERVER, not INSTRUCTOR.** During the work cycle, the teacher does not teach whole-class lessons (those happen at other times). The teacher circulates, observes, takes notes on what children are doing, and provides brief, individual support when needed. Lillard (2005): the teacher's observations during the work cycle are the primary assessment tool in Montessori — they reveal what children choose, how long they sustain concentration, where they struggle, and what they avoid.
- **Students need training in choosing.** "Choose your own work" sounds simple but is cognitively demanding, especially for children who have always been told what to do. Some will repeatedly choose easy, comfortable work. Some will flit between activities without sustaining any. Some will choose nothing and wait to be told. The work cycle must include mechanisms for developing choice skills: goal-setting, work plans, and periodic teacher conferences about work selection.
- **Protect the block.** The single most important design principle is: DO NOT INTERRUPT. No announcements. No "quick" whole-class reminders. No transitioning to another activity halfway through. Every interruption resets the flow clock and erodes the culture of sustained work. If there is a mandatory interruption (assembly, break), design the work cycle around it rather than pretending it doesn't exist.

Your task is to design an uninterrupted work cycle for:

**Available time:** {{available_time}}
**Learning activities:** {{learning_activities}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Student level:** {{student_level}} — if not provided, design for a primary school context (ages 5-11).
**Class size:** {{class_size}} — if not provided, assume 25-30 students.
**Current routines:** {{current_routines}} — if not provided, assume students are used to teacher-directed, segmented lessons and this is their first experience with an extended work cycle.
**Teacher concerns:** {{teacher_concerns}} — if not provided, address the three most common concerns: off-task behaviour, accountability, and students who don't choose challenging work.
**Environment setup:** {{environment_setup}} — if not provided, assume materials are accessible and work areas are defined (see Skill 93: Prepared Environment Designer).

Return your output in this exact format:

## Uninterrupted Work Cycle: [Time Block]

**Available time:** [The actual time]
**Activities available:** [What students can choose from]
**Student level:** [Who this is designed for]

### Work Cycle Structure

[The complete cycle: opening routine, work period, and closing routine, with timing]

### Opening Routine

[Exactly what happens in the first 5-10 minutes — how students transition from arrival/previous activity into self-directed work. This is the most critical routine in the cycle.]

### Work Period

[What happens during the main block — what students do, what the teacher does, and how the environment supports sustained engagement]

### Teacher Observation Protocol

[What the teacher observes, how they record it, when they intervene, and when they stay back. Include a practical observation tool.]

### Materials Rotation and Choice Management

[How activities are organised, how students choose, and how the selection is managed to ensure appropriate challenge]

### Closing Routine

[How the work cycle ends — tidying, reflection, and transition to the next activity]

### Transition Management

[How to handle the start, end, and any unavoidable interruptions within the cycle]

### Building the Routine Over Time

[How to introduce the work cycle gradually — week by week — for students who are new to self-directed work]

### Addressing Common Concerns

[Practical responses to: off-task behaviour, accountability, students choosing easy work, students who can't settle, and external interruptions]

**Self-check before returning output:** Verify that (a) the design fits the ACTUAL time available, (b) the opening routine is explicit and calm, (c) the teacher's role is observer not instructor, (d) choice mechanisms are included, (e) the block is protected from interruptions, and (f) a gradual introduction plan is provided.
```

## 示例输出

**场景：** *可用时间：“连堂课：90分钟（9:00–10:30）。这是我课表里最长的无打断时间块。期间没有强制打断。课间休息在10:30” / 学习活动：“三年级班（7-8岁）。我在数学、读写和‘古埃及’主题下设置了10项活动：(1) 乘法表闪卡练习，(2) 分数条探索，(3) 应用题挑战卡（3个级别），(4) 书写练习册，(5) 自由写作日记，(6) 带理解问题的引导阅读（5套书），(7) 古埃及研究任务（书籍与打印资料），(8) 金字塔展开图制作（数学/设计技术跨学科），(9) 象形文字破译活动，(10) 尼罗河绘图与标注” / 班级规模：“28名学生” / 当前常规：“目前我的课是45–50分钟加10分钟过渡。我先全班讲授，然后学生做活动，然后我们总结。我以前从未做过90分钟的自主时段” / 教师顾虑：“我担心：(a) 有些学生会胡闹90分钟，(b) 我不知道他们到底学到了什么，(c) 总是同一批学生每次都选简单的活动，(d) 课堂会一片混乱”*

---

## 无打断工作周期：90分钟连堂课

**可用时间：** 90分钟（9:00–10:30），无打断
**可选活动：** 横跨数学、读写与古埃及主题的10项活动
**学生水平：** 三年级（7-8岁），28名学生，首次接触延长版自主工作

### 工作周期结构

| 阶段 | 时间 | 时长 | 发生内容 |
|---|---|---|---|
| 开场 | 9:00–9:10 | 10分钟 | 集合、设定目标、开始 |
| 工作时段 | 9:10–10:15 | 65分钟 | 自主定向工作，教师观察 |
| 收尾 | 10:15–10:30 | 15分钟 | 整理、反思、分享 |

### 开场常规

**9:00 — 地毯集合（3分钟）。**
学生围坐成一圈。不讲新课——这纯粹是过渡环节。教师说：

*“早上好。今天的工作周期是90分钟。你们有10项活动可以挑选。你们的目标是深度完成**至少**两项活动——意思是认真做完，而不是匆匆敷衍。让我们快速回顾一下有哪些可选活动。”*

简要报出10项活动名称（30秒——学生昨天引入时应该已经认识它们了），指向每个站点。

**9:03 — 个人工作计划（5分钟）。**
每位学生在一张简易工作计划卡上填写：

| 我的工作计划 | 活动名称 | 完成？ |
|---|---|---|
| 第一选择： | _________ | ☐ |
| 第二选择： | _________ | ☐ |
| 如果两项都完成了： | _________ | ☐ |

工作计划服务于三个目的：（a）将学生的意图外显化，让他们在开始前做出承诺；（b）为教师提供每位学生计划做什么的记录；（c）培养规划技能——一项核心执行功能。

**9:08 — 开始。**
*“准备好了，就去你的第一项活动。轻步走。选一个工作区。开始。”*

学生移向自己选择的活动。教师**不要**指挥交通。部分学生会立刻开始；部分学生需要一分钟安定下来。这很正常。除非有学生站着超过2分钟仍未做出选择，否则不要介入——此时再低声私下提示：*“你的第一选择是什么？我们一起去找找看。”*

### 工作时段

**9:10–10:15（65分钟持续工作）**

**学生做什么：**
- 在自选的工作区（课桌、地板、安静角）开展自选活动
- 完成一项活动后，将材料放回架子，在工作计划上打勾，然后前往第二选择
- 如果遇到卡壳，先尝试自己解决，再问邻座同学，**只有在那之后**才来找教师。（第1周明确教授这个“找我之前先试三招”的常规。）
- 完成第二项活动后，从工作计划中选择第三项或挑选新内容
- 学生可以独立工作或结伴工作，前提是双方都在认真工作（而不仅仅是闲聊）

**教师做什么：**
见下方教师观察规程。简言之：巡视、观察、记录，并在必要时提供简短的个别支持。**不要**在工作时段内讲授全班课。**不要**发布全班通知。**不要**打断一个正在深度专注的学生去问他问题——远距离观察并记录下来留待后续。

**“虚假启动”模式（提前预料）：**
在最初的 10–15 分钟里，部分学生会在活动间跳来跳去、没必要地削铅笔、上厕所或聊天。蒙台梭利观察到这种安定适应期是**正常的**——儿童需要时间找到自己的工作。15–20 分钟后，大多数儿童会安定下来进入持续投入。安定阶段切勿惊慌。那不是混乱——那是选择与投入的认知过程。

**深度工作阶段（核心目标）：**
安定阶段过后，寻找心流的迹象：学生全神贯注、安静、聚焦、注意力持续集中。教室给人的感觉会与常规课截然不同——更平静，带有一种富有成效的轻微嗡嗡声，而非教师主导活动下的那种被管束出来的安静。拼尽全力保护这一阶段。如果有学生在深度工作阶段带着非紧急问题走近你，轻声说：*“我看大家都在非常专心地工作。这件事能等到收尾圆圈时间再说吗？”*

### 教师观察规程

**在工作周期内，教师的首要角色是“观察者”。** 这是你整周能做的最有价值的评估，因为它揭示了：
- 学生**选择**什么（他们倾向于哪些活动、回避哪些活动）
- 他们能**维持**多久（谁能连续工作30分钟，谁每5分钟换一次）
- 他们在哪里**受挫**（什么引发了困惑、沮丧或半途而废）
- 他们如何**自我调节**（他们会规划吗？遇到挫折能恢复吗？能管理时间吗？）

**观察工具——使用简易网格表：**

| 学生 | 所选活动 | 持续时间 | 观察笔记 |
|---|---|---|---|
| Aisha | 金字塔展开图 | 25分钟 | 高度专注，仔细测量，仅求助过一次（恰当） |
| Ben | 乘法表 → 自由写作 | 5分钟 → 20分钟 | 很快放弃了乘法表（太简单？太难？回避？）。安定下来投入了自由写作。 |
| Cara | 研究任务 | 35分钟 | 专注力极强。做了笔记。高度自主。 |

你不可能每次课都深入观察全部28名学生。每次周期锁定 8–10 名学生，一周内轮转，确保每周至少观察到每位学生一次。

**何时介入：**
- 安定阶段过后，某学生无所事事超过3分钟 → 轻声私下提示
- 某学生干扰他人 → 低声重定向，而非公开批评
- 某学生卡壳且已尝试过“找我之前先试三招” → 简短、聚焦的帮助（2分钟以内），然后离开
- 某学生连续3次课选择同一个简单活动 → 安排一次工作面谈（见下方选择管理）

**何时不要介入：**
- 学生在工作但速度较慢 → 那是他的节奏，不是问题
- 学生盯着空处发呆一分钟 → 他可能正在思考，而非走神。静观其变。
- 学生完成一项活动后在开始下一项前停顿片刻 → 过渡缓冲时间是正常的

### 材料轮换与选择管理

**活动组织：**
10项活动各有明确位置（一个架子、一个托盘、一个站点）。每项活动都是自足的：所有必需材料都在一处，且指令内嵌其中（任务卡、视觉指引）。学生不需要问“我该做什么？”——材料本身就应传达这一点。

**管理选择以确保恰当挑战：**

工作计划卡是核心工具。开场时，悄悄浏览 5–6 份工作计划。如果你看到某学生连续第三次选择同一个简单活动，进行一次简短的私下对话：

*“我注意到你已经选了三次乘法表闪卡了。你现在那块已经非常棒了！这周，我想请你试试应用题挑战卡——从第1级开始。把它写进你工作计划的第一选择里。”*

这不是剥夺选择权——而是在**指导**选择。随着时间推移，学生会发展出恰当选择的自我觉察。在最初几周，部分学生需要这种引导。

**轮换周期：**
每 2–3 周更新一次活动。当学生接触完当前所有活动后，引入 2–3 项新活动并撤下 2–3 项旧活动。这既能保持环境的新鲜感，又不会因一次提供过多选项而让学生不知所措。

### 收尾常规

**10:15 — 整理（5分钟）。**
发出清晰信号（一声风铃、摇铃或视觉计时器归零）：*“工作周期即将结束。请完成你手头这一步，归还材料，然后带着你的工作计划回到地毯上。”*

学生将材料放回架子上的**精确**原位。这不是可选项——正是这一习惯维持了有准备的环境。如果材料未正确归位，下一个选择该活动的学生就会面对一团糟，从而瓦解整个系统。

**10:20 — 反思圆圈（7分钟）。**
学生带着工作计划围坐成一圈。

三个快速反思提示（每次课选一到两个，不要全用）：
1. *“你今天做了什么？向大家展示一件你感到自豪的成果。”*（2–3名学生分享——不是全部28人）
2. *“今天有人遇到困难了吗？卡壳时你是怎么做的？”*（将挣扎正常化，赞赏自我调节）
3. *“今天有人尝试了新东西——以前没做过的活动吗？”*（赞赏敢于冒险尝试）

收齐工作计划卡。这些是你的问责记录——显示每位学生计划了什么、实际做了什么以及是否完成。

**10:27 — 过渡。**
*“谢谢大家度过了一个非常棒的工作周期。排队准备课间休息。”*

### 过渡管理

**进入工作周期：** 开场常规（地毯 → 工作计划 → 开始）不应超过10分钟。如果耗时更长，说明常规需要收紧——多加练习。

**退出工作周期：** 响铃-整理-反思-过渡序列应耗时15分钟。最初几次在学生熟悉常规期间可能会更久。

**若发生不可避免的打断**（消防演习、突发集会）：平静应对。学生回来后，给他们2分钟重新安定：*“回到你刚才的地方。看看你的工作计划。继续。”* 不要重启开场常规——直接让他们恢复工作。

### 随时间建立常规

**第1周：30分钟。** 在90分钟时间块中仅用30分钟进行自主工作。前20分钟明确教授常规：如何选择、如何开始、如何归还材料、如何使用“找我之前先试三招”。接着30分钟自主工作，然后15分钟复盘。其余时间用于常规授课。

**第2周：45分钟。** 延长至45分钟。此时开场与收尾常规应当更顺畅了。本周聚焦观察规程——开始记录你所看到的。

**第3周：60分钟。** 整整一小时。大多数学生此时已理解常规。聚焦选择指导——谁的选择恰当，谁需要支持？

**第4周：75分钟。** 接近完整时间块。此时深度工作阶段应当已清晰可见——安静、高效的教室，25名以上学生在独立工作，而你可以自由观察与支持。

**第5周及以后：完整90分钟。** 工作周期已经建立。你现在的角色是维护：更新活动、指导选择、观察以及提供个别支持。

### 应对常见顾虑

**“有些学生会胡闹90分钟。”**
如果是循序渐进建立常规，就不会如此。分阶段引入（30 → 45 → 60 → 75 → 90分钟）意味着学生随着时间块的延长同步发展了自我调节技能。极少数在5周后确实仍无法自我调节的学生，可能需要一份调整版工作计划：“你的前20分钟做[指定具体活动]。之后再自主选择。”随着其自我调节能力提升，逐步增加他们的自主选择时间。

**“我怎么知道他们到底学到了什么？”**
工作计划卡 + 你的观察笔记 + 他们工作的实体产出（完成的活动、书面作业、制作物）所提供的评估数据，远**多于**一节常规讲授课。在讲授课上，你知道你**教**了什么；在工作周期里，你知道学生**做**了什么、持续了多久以及在哪里卡壳。观察规程就是你的评估工具。

**“总是同一批学生每次都选简单的活动。”**
这是一个真实风险，可通过选择指导（见上文）来解决。部分学生需要被明确引导向难度恰当的工作。随着时间推移，大多数学生会发展出更好的选择能力——但这需要教师主动指导，而非被动祈祷。

**“课堂会一片混乱。”**
第1周会感觉有点乱。第2周会感觉很忙碌。第3周会感觉很高效。第5周会感觉令人惊叹。循序渐进至关重要——切勿在未经分阶段引入的情况下直接尝试90分钟自主工作。常规**本身就是**管理策略。

---

## 已知局限

1. **在常规学校课表中，3小时的蒙台梭利工作周期极少能实现。** 大多数小学将一天划分为 45–60 分钟的时间块，中间穿插强制性过渡（集会、课间休息、午餐、专科课）。上例中使用的90分钟连堂课是一个现实的适配方案，但仍只有蒙台梭利理想的**一半**。研究证据（Lillard, 2005; Csikszentmihalyi, 1990）表明更长的时间块能带来更深层的投入，但从90分钟延长到180分钟的边际收益尚未在常规学校环境中经过实证检验。90分钟时间块是一种有原则的折中方案，而非经验证的等价替代。

2. **专门针对工作周期的证据嵌入在整体蒙台梭利项目评估中。** Lillard 与 Else-Quest（2006）评估的是作为一个完整系统的蒙台梭利——混龄分组、有准备的环境、特定教具**以及**工作周期。无打断时间的独立贡献无法被剥离。Rosenshine（2012）的任务专注时间研究与 Csikszentmihalyi（1990）的心流研究提供了独立的理论支持，但两者均非专门针对蒙台梭利工作周期开展。

3. **自主定向选择需要一个有准备的环境。** 工作周期预设了高质量、自足且具恰当挑战性的活动是可用且可及的（见技能93：有准备的环境设计器）。若缺乏这一点，“自主选择工作”就会变成“从手边随便抓点什么”——两者截然不同。工作周期与有准备的环境相互依存；只实施其中之一会削弱效果。

4. **执行功能的发展因年龄和个体而异。** 工作周期的自我调节要求（选择、启动、维持、完成）需要贯穿整个童年期不断发展的执行功能技能。年幼儿童（3–5岁）可能需要更短的工作时段和更结构化的选择。存在执行功能困难的儿童（包括许多 ADHD 儿童）可能需要调整版工作计划与额外支架。分阶段引入计划（第1–5周）在一定程度上解决了这一问题，但部分学生在导入期结束后仍需持续支持。

5. **教师焦虑是一个真实障碍。** 习惯于全班授课的教师在工作周期内可能会体验到真实的焦虑——安静（或富有成效的轻声讨论）令人感到陌生，缺乏直接控制感令人不适。Cossentino（2006）发现，蒙台梭利教师描述了一个需要练习与信任的有意识的“退后一步”过程。这并非微不足道的心态转变，不应被轻视。分阶段引入同样有助于教师与学生同步建立信心。
