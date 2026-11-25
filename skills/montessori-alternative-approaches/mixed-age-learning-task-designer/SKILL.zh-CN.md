---
# AGENT SKILLS STANDARD FIELDS (v2)
name: mixed-age-learning-task-designer
description: "设计混龄学习任务，使不同年龄段学生共同合作并让所有年龄组均能互惠获益。适用于规划跨龄辅导、纵向分组或多学年联合活动。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "montessori-alternative-approaches/mixed-age-learning-task-designer"
skill_name: "混龄学习任务设计器"
domain: "montessori-alternative-approaches"
version: "1.0"
evidence_strength: "moderate"
evidence_sources:
  - "Lillard & Else-Quest (2006) — Evaluating Montessori education (Science)"
  - "Hattie (2009) — Visible learning: peer tutoring effect size 0.55"
  - "Topping (2005) — Trends in peer learning (meta-analysis of peer tutoring effects)"
  - "Vygotsky (1978) — Mind in society: the development of higher psychological processes (ZPD)"
  - "Lillard (2005) — Montessori: The Science Behind the Genius (chapter on mixed-age grouping)"
input_schema:
  required:
    - field: "learning_objective"
      type: "string"
      description: "混龄任务应达成的具体学习目标——高龄与低龄学生各自应学到什么"
    - field: "age_range"
      type: "string"
      description: "共同合作的年龄段或年级——最长者与最幼者之间的具体跨度"
  optional:
    - field: "subject_area"
      type: "string"
      description: "课程学科"
    - field: "group_composition"
      type: "string"
      description: "各年龄段学生人数及任何已知的群体动态"
    - field: "time_available"
      type: "string"
      description: "混龄活动持续时长"
    - field: "space_and_materials"
      type: "string"
      description: "可用的空间与教具材料"
    - field: "frequency"
      type: "string"
      description: "是一次性活动还是常规混龄课程"
output_schema:
  type: "object"
  fields:
    - field: "task_design"
      type: "object"
      description: "完整的混龄任务——学生做什么、角色如何建构以及如何创造真正的相互依赖"
    - field: "older_student_learning"
      type: "object"
      description: "高龄学生从体验中学到什么——不仅是“帮忙”，而是真正的认知收益"
    - field: "younger_student_learning"
      type: "object"
      description: "低龄学生学到什么——高龄学生的参与如何创造最近发展区（ZPD）支架"
    - field: "role_structure"
      type: "object"
      description: "高龄与低龄学生的具体角色——旨在创造真正的相互依赖，而非单向帮助"
chains_well_with:
  - "three-part-lesson-designer"
  - "prepared-environment-designer"
  - "uninterrupted-work-cycle-designer"
  - "peer-tutoring-protocol-designer"
teacher_time: "5 分钟"
tags: ["mixed-age", "Montessori", "peer-tutoring", "Vygotsky", "ZPD", "Hattie", "Lillard", "cross-age", "interdependence"]
---

# 混龄学习任务设计器

## 本技能的功能

设计能够高效利用混龄分组的学习任务——在高龄与低龄学生之间创造真正的相互依赖，使**两个**年龄组都能学习。这是蒙台梭利教育最具代表性的特征之一，也是最常被误解的方面之一：混龄分组不是让大孩子去“照顾/帮扶”小孩子（这会让小孩子受益，却可能浪费大孩子的时间），而是要设计出这样的任务：大孩子的角色需要真正的认知投入以深化自身理解，同时小孩子从其最近发展区（ZPD，Vygotsky, 1978）内的支架中获益。Hattie（2009）报告同伴辅导（peer tutoring）的效应量高达 0.55——是其综合研究中最具影响力的策略之一——但这一效应关键取决于辅导互动的**设计**。Topping（2005）发现，只要任务要求小老师组织、解释并调适自己的知识（这是一项高要求的认知任务），辅导者（高龄儿童）学到的往往与被辅导者一样多甚至更多。输出包括完整的任务设计、**两个**年龄组的学习目标（不仅限于低龄学生）、角色结构（为相互依赖而设计，而非单向帮助）以及实用的实施指南。

## 循证基础

Lillard 与 Else-Quest（2006）发现，蒙台梭利教室（标准采用3岁年龄跨度）中的儿童相比匹配对照组展现出更优越的社交技能与更强的社群意识。Lillard（2005）指出，混龄分组通过多重机制促成蒙台梭利成效：年幼儿童通过观察年长儿童更进阶的工作获得启发；年长儿童通过向年幼儿童讲解来巩固自身理解；混龄群体的社交动态与同龄群体有着根本不同（更少竞争、更多指导、更丰富的榜样）。Hattie（2009）综合了同伴辅导研究，发现整体效应量为 0.55——远高于他所界定的有效干预阈值“0.40拐点”。关键在于，这一效应不仅限于被辅导者：辅导者也表现出显著的学习增益，尤其是当辅导要求他们解释概念、监控被辅导者的理解并调适解释方式时。Topping（2005）对同伴学习研究进行了全面综述，确定了跨龄辅导最有效的条件：（a）必须对辅导者进行“如何辅导”的培训（不能只说“去帮忙”）；（b）任务必须要求辅导者付出真正的认知劳动（解释，而非直接给答案）；（c）年龄/能力差距必须恰当（太大则辅导者难以共情；太小则没有最近发展区收益）；（d）辅导者与被辅导者都应有明确的角色与责任。Vygotsky（1978）通过最近发展区（ZPD）为混龄学习提供了理论基础：儿童独立能做的与在更有能力的同伴或成人支持下能做的之间的差距。混龄分组创造了自然的 ZPD 支架——高龄儿童能够提供恰好落在低龄儿童 ZPD 内的支持，因为他们不久前才刚走过同一片概念领地。成人的解释往往过于抽象或远离儿童经验；1–2年前刚学过该概念的同伴往往是更有效的支架。

## 输入模式

教师必须提供：
- **学习目标：** 学生应学到什么。*例如：“两组都发展对分数的理解——四年级学生通过使用具体教具向二年级学生教授分数来巩固分数概念；二年级学生在四年级导师的引导下通过动手活动建立对二分之一和四分之一的初步理解” / “六年级与三年级学生发展科学探究技能——六年级设计并带领实验，三年级进行观察并记录数据” / “学前班与二年级学生发展阅读流利度——二年级儿童为学前班儿童朗读并提出理解问题”*
- **年龄范围：** 谁将一起合作。*例如：“二年级（6-7岁）与四年级（8-9岁）——2岁差距” / “三年级与六年级——3岁差距” / “学前班（4-5岁）与二年级（6-7岁）——2岁差距”*

可选（如有，由上下文引擎注入）：
- **学科领域：** 课程学科
- **群体构成：** 人数与动态
- **可用时间：** 活动时长
- **空间与材料：** 可用资源
- **频率：** 一次性或定期

## 提示词

```
You are an expert in mixed-age learning design, with deep knowledge of Montessori mixed-age grouping principles (Lillard, 2005; Lillard & Else-Quest, 2006), peer tutoring research (Hattie, 2009, effect size 0.55; Topping, 2005), and Vygotsky's (1978) zone of proximal development. You understand that the critical design challenge in mixed-age learning is creating GENUINE INTERDEPENDENCE — where both age groups learn, not just the younger students. Poorly designed mixed-age activities waste older students' time and reduce to babysitting. Well-designed mixed-age activities are among the most powerful learning strategies available.

CRITICAL PRINCIPLES:
- **Both age groups must learn.** The most common mistake is designing for the younger students and treating the older students as helpers. The older student's role must require genuine cognitive work: explaining concepts (which deepens understanding — "the protégé effect"), monitoring a younger student's understanding (which develops metacognition), and adapting explanations when the first attempt doesn't work (which develops flexible thinking). If the older student could do their role on autopilot, the task is poorly designed.
- **Design for interdependence, not one-directional help.** The task should require contributions from BOTH age groups that neither could provide alone. The older student contributes knowledge and organisational skill; the younger student contributes fresh perspective, curiosity, and the need for clear explanations. Both roles should feel necessary and valued.
- **The age gap must be appropriate.** Topping (2005): a gap of 2-3 years is typically optimal. Less than 1 year and there may not be sufficient knowledge difference. More than 4 years and the older student may struggle to relate to the younger student's level, or the younger student may be intimidated. Within the gap, the older student should be confident (not struggling) with the content, so that their cognitive resources are available for the teaching role.
- **Train the tutors.** Don't just say "help the younger children." Teach the older students HOW to be effective peer tutors: ask questions before giving answers, break instructions into small steps, praise effort not just correctness, and check understanding by asking the younger student to explain back. This training is an investment that pays off across multiple sessions.
- **Structure the interaction.** Open-ended "work together" instructions produce unstructured interaction where the older student does the work and the younger student watches. Provide a specific protocol: what to do first, what each person's role is at each stage, and what the shared outcome looks like.

Your task is to design a mixed-age learning task for:

**Learning objective:** {{learning_objective}}
**Age range:** {{age_range}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Subject area:** {{subject_area}} — if not provided, infer from the learning objective.
**Group composition:** {{group_composition}} — if not provided, design for pairs (one older, one younger student).
**Time available:** {{time_available}} — if not provided, design for 30-40 minutes.
**Space and materials:** {{space_and_materials}} — if not provided, assume a standard classroom with basic materials.
**Frequency:** {{frequency}} — if not provided, design for a regular weekly session.

Return your output in this exact format:

## Mixed-Age Learning Task: [Task Name]

**Learning objective:** [What both groups learn]
**Age groups:** [Who works together]
**Interdependence design:** [One sentence — why both groups need each other]

### Task Overview

[The complete task — what students do together, the shared outcome, and the timeline]

### Role Structure

**Older Student Role:**
[What the older student does at each stage — and what they LEARN by doing it]

**Younger Student Role:**
[What the younger student does at each stage — and how the older student's involvement creates ZPD scaffolding]

### Tutor Preparation

[How to prepare the older students for their role — the specific tutoring skills they need and how to teach them. This is NOT optional — it is essential for the task to work.]

### Task Sequence

[Step-by-step: what happens when, who does what, and how the interaction is structured]

**Step 1:** [Time] — [What happens]
**Step 2:** [Time] — [What happens]
...

### Learning Outcomes

**Older students learn:**
[Specific cognitive benefits — not just "leadership skills" but genuine subject-matter deepening]

**Younger students learn:**
[Specific learning gains — how the ZPD scaffolding produces understanding they couldn't reach alone]

### Quality Indicators

[How to know the task is working — observable signs of genuine interdependence vs. signs that one group is doing all the work]

### Adaptation Notes

[How to adapt for different group sizes, age gaps, or contexts]

**Self-check before returning output:** Verify that (a) both age groups have genuine learning objectives, (b) the task creates interdependence not one-directional help, (c) the age gap is appropriate, (d) tutor preparation is included, and (e) the interaction is structured with specific roles.
```

## 示例输出

**场景：** *学习目标：“两组都发展对分数的理解——四年级学生（8-9岁）通过为二年级学生（6-7岁）设计和带领分数活动来巩固和深化其分数理解；二年级学生在四年级导师引导下通过动手活动建立对二分之一和四分之一的初步理解” / 年龄范围：“二年级（6-7岁）与四年级（8-9岁）——2岁差距” / 学科领域：“数学——分数” / 群体构成：“12名四年级学生与12名二年级学生一对一配对” / 可用时间：“40分钟” / 频率：“每周一次，连续4周”*

---

## 混龄学习任务：分数工作坊

**学习目标：** 四年级通过教学巩固分数；二年级通过有指导的动手活动建立对二分之一和四分之一的初步理解
**年龄组：** 四年级（8-9岁）与二年级（6-7岁）结对
**相互依赖设计：** 四年级学生必须将分数解释得足够清晰以让6岁孩子听懂（深化自身概念知识），而二年级学生通过一对一支架学习分数——这是班级教师面对30名孩子时无法同时提供的支持

### 任务概述

在为期4周的每周课程中，每位四年级学生为他们的二年级同伴设计并带领一项分数活动。四年级学生不是在“辅导作业”——他们是在**设计**一节微课，这要求他们思考同伴已经知道什么、选择合适的材料、将概念拆分为步骤，并在行不通时进行调整。共同成果是一本由每对搭档合著的《分数书》：二年级学生绘制并标注分数图画，四年级学生撰写解释并核对准确性。

### 角色结构

**四年级学生角色（导师/设计师）：**
- **第1周：** 设计一项使用具体材料（折纸、分橡皮泥、分糖果）引入“二分之一”的动手活动。四年级学生必须提前**规划**该活动——决定使用什么材料、说什么以及问什么问题。
- **第2周：** 基于二年级同伴在第1周所学内容，设计引入“四分之一”的活动。
- **第3周：** 设计一项对比活动——½ 和 ¼ 哪个更大？——使用实物证明答案。
- **第4周：** 引导同伴制作《分数书》，核对准确性并解释纠错。

**四年级学到什么：** 设计一节课比**做**分数题需要更深层的理解。四年级学生必须思考：“½ 到底**意味着**什么？在不用分数符号的情况下我该如何解释它？如果他们以为 8 颗糖的 ½ 是 3，我该如何向他们展示为什么是 4？”这就是“门徒效应（protégé effect）”——教学迫使知识重组与巩固。此外，当二年级学生出现误解时，四年级学生必须诊断错误并尝试不同的解释，从而发展灵活的数学推理能力。

**二年级学生角色（学习者/创作者）：**
- 参与四年级同伴设计的活动
- 感到困惑时提出问题（明确鼓励——“如果你没听懂，那就是你搭档的工作没讲清楚”）
- 在共创的《分数书》中绘制并标注分数图画
- 到第4周时，用自己的例子向四年级同伴解释二分之一和四分之一

**二年级学到什么：** 通过具体、动手的活动以及来自刚学过相同概念的同伴的一对一支架引入分数概念。四年级学生的解释往往比成人更易懂，因为他们使用儿童友好的语言，且不久前刚克服过相同的概念障碍。最近发展区（ZPD）得到优化：在适当支架下，二分之一和四分之一正处于二年级学生的能力所及范围内，而四年级同伴恰好提供了这种支架。

### 导师准备

**第1周前（仅面向四年级学生的30分钟准备课）：**

向四年级学生教授四项辅导原则：

1. **先问再讲。** “在你解释之前，先问问你的搭档已经知道了什么。‘你觉得一半是什么意思？’你可能会惊讶——他们也许已经知道一部分了。”

2. **使用教具。** “不要只**说**‘8的一半是4’。要**演示**出来。把8个计数器分成相等的两组。让你的搭档亲手去分。”

3. **检查理解。** “解释完之后，请你的搭档反过来**讲给你听**。‘你能演示给我看这些糖果的一半是多少吗？’如果他们能演示出来，说明懂了；如果不能，你需要换一种方式解释。”

4. **保持耐心。** “你的搭档才6岁。有些话他们可能需要听三遍。这很正常。如果你的第一种解释行不通，换一种方式——换用不同的材料或不同的例子。”

**演练：** 让四年级学生在见到二年级搭档之前，先**互相**练习用这些原则讲解“二分之一”。复盘：“讲解时什么最难？什么方法有效？”

### 任务流程

**第1周：认识二分之一（40分钟）**

**第1–5分钟：** 四年级学生领取准备好的材料，在共享工作区与二年级搭档会合。

**第5–10分钟：** 四年级学生问搭档：“你知道‘一半’是什么意思吗？你能做给我看吗？”这个诊断性问题揭示了二年级学生的起点——有的知道，有的不知道，有的部分理解。

**第10–25分钟：** 四年级学生带领自己规划的活动。示例：将一张纸对折（“你看两块大小一模一样？这就是一半的意思——两份**相等**的部分”），接着将10个计数器分成相等的两组（“每半边有多少个？”），再将8颗糖果平分到两个盘子里。四年级学生全程引导、提问并检查理解。

**第25–35分钟：** 二年级学生在《分数书》中绘制“二分之一”——被平分物体的图画，并在四年级学生帮助下标上“½”。

**第35–40分钟：** 快速反思。四年级学生告诉老师：“我的搭档能/不能解释一半的意思。他们觉得[X]很容易，[Y]很难。”这种对**被辅导者**的评估培养了四年级学生的元认知监控能力。

**第2–4周：** 遵循相同结构，内容难度逐步递进（四分之一、大小比较、制作《分数书》）。

### 学习成果

**四年级学生学到：**
- **更深层的分数理解。** 必须解释**为什么** 8 的 ½ 是 4（而不仅仅是算出来），迫使学生进行概念性投入。“因为一半意味着分成相等的两组，而8分成相等的两组每组是4”是一种概念性解释，而非机械程序。
- **灵活的数学推理。** 当二年级学生误解时，四年级学生必须尝试不同的解释方式——培养从多角度切入同一概念的能力。
- **元认知技能。** 评估他人的理解（“他们懂了吗？我怎么知道？”）能培养他们自身学习所需的同样监控技能。
- **沟通技能。** 将数学理解转化为清晰、适龄的语言是一项高要求的认知与语言任务。

**二年级学生学到：**
- 通过具体、动手的活动和一对一支架获得**初步分数概念（二分之一与四分之一）**——这正是研究推荐的引入方式。
- **数学语言。** 在自然对话情境中听到大孩子使用分数词汇，比正式讲授更有效地支持语言习得。
- **自信心。** 与同伴导师一起学习通常比全班授课压力更小，尤其是对数学感到焦虑的孩子。

### 质量指标

**任务奏效的迹象（真正的相互依赖）：**
- 四年级学生在提问，而不仅仅是报答案
- 二年级学生在操作材料和做活动，而不仅仅是旁观
- 双方都在交谈——对话是双向流动的
- 当搭档出错时，四年级学生在明显地思考（“我怎么换种方式解释？”）
- 《分数书》既有二年级的画作也有四年级的解释——共同产出的证据

**任务失效的迹象（单向或脱离）：**
- 四年级学生包办活动，二年级学生被动观看
- 四年级学生不提问也不用教具，直接给出答案
- 二年级学生走神、东张西望或不触碰材料
- 四年级学生感到无聊或匆匆走过场——任务对他们而言认知要求不够
- 《分数书》全是四年级的作品——二年级没有实质贡献

**教师对预警信号的回应：** 如果某组搭档出现失调迹象，介入并强化角色：“四年级，记住——你们的任务是**提问题**和**用教具演示**。二年级，你们的任务是**亲手尝试**并在不懂时**发问**。让我看到你们都在履行自己的职责。”

### 调整说明

**针对更大年龄跨度（3岁以上）：** 辅导规程变得更加重要——若无明确培训，六年级学生可能难以把解释校准到学前班孩子的水平。可考虑在第一节课使用“教学脚本”：一套高龄学生遵循的结构化活动序列，同时为**导师**和被辅导者提供支架。

**针对小组而非结对：** 使用三人组（一名高龄配两名低龄）而非更大群组。在4人及以上小组中，辅导会变得分散，部分低龄学生会游离。配对两名低龄学生时，高龄学生可以交替关注，且低龄学生之间也能互相学习。

**针对一次性活动：** 降低预期目标。单次活动可以引入一个概念（二分之一），但无法建立起使定期混龄活动产生强大效果的关系与常规。如果是一次性活动，请聚焦于一个简单、自足且有可见共同成果的活动（一张海报、一个模型、一次简短展示）。

**针对非蒙台梭利学校：** 混龄学习并不需要蒙台梭利体制。只要能组织跨班活动，任何学校都适用。主要障碍在于排课（把两个年级凑到一起）与教师协同（就学习目标和结构达成共识）。在全面推广前，先从一个学科和可控数量的结对开始。

---

## 已知局限

1. **同伴辅导的证据比专门针对蒙台梭利混龄分组的证据更充分。** Hattie（2009）0.55的效应量与 Topping（2005）的元分析为同伴辅导作为通用策略提供了强有力的证据。Lillard 等人（2006）和 Lillard（2005）提供了专门针对蒙台梭利混龄分组的证据，但这些证据嵌入在整体项目评估中——混龄本身的独立贡献无法剥离。上述任务设计同时汲取了这两方面的证据。

2. **高龄学生必须真正自信掌握该内容。** 如果一名四年级学生自己还在分数上吃力，让他们教二年级学生分数只会让双方都陷入混乱。本任务假设高龄学生已经**掌握**了内容——辅导是巩固和深化现有知识，而不是从零创造知识。教师必须在指派导师前核实高龄学生是否准备就绪。

3. **社交动态可能会削弱学习效果。** 部分高龄学生可能居高临下（“这么简单，你早该会了”）；部分低龄学生可能焦虑或胆怯；有些搭档可能单纯合不来。导师准备课应明确强调尊重与耐心，且教师应密切关注搭档动态，必要时重新配对。

4. **混龄分组需要课表协调。** 在课表刚性、分年级独立编班的学校中，安排跨龄课程是一项后勤挑战。最常见的实施形式是每周一次的“伙伴（buddy）”课，但这需要至少两位教师达成一致并对齐课程进度。后勤障碍往往比教学设计挑战更为显著。
