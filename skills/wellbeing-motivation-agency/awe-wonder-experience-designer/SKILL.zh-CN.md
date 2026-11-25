---
# AGENT SKILLS STANDARD FIELDS (v2)
name: awe-wonder-experience-designer
description: "设计一个激发敬畏或惊奇的体验时刻，勾起好奇心并深化对教学内容的情感投入。适用于开启新单元、引入出人意料的材料或重新点燃学生兴趣的场景。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "wellbeing-motivation-agency/awe-wonder-experience-designer"
skill_name: "敬畏与惊奇体验设计器"
domain: "wellbeing-motivation-agency"
version: "1.0"
evidence_strength: "emerging"
evidence_sources:
  - "Keltner & Haidt (2003) — Approaching awe, a moral, spiritual, and aesthetic emotion"
  - "Keltner (2023) — Awe: the new science of everyday wonder and how it can transform your life"
  - "Valdesolo & Graham (2014) — Awe, uncertainty, and agency detection"
  - "Shiota, Keltner & Mossman (2007) — The nature of awe: elicitors, appraisals, and effects on self-concept"
  - "Gottlieb, Keltner & Lombrozo (2018) — Awe as a scientific emotion"
input_schema:
  required:
    - field: "lesson_content"
      type: "string"
      description: "本节课的学科内容与学习目标"
    - field: "student_level"
      type: "string"
      description: "年龄/年级"
  optional:
    - field: "subject_area"
      type: "string"
      description: "课程学科"
    - field: "awe_trigger"
      type: "string"
      description: "教师希望围绕其构建敬畏时刻的特定元素"
    - field: "student_profiles"
      type: "array"
      description: "来自情境引擎：班级兴趣、投入模式、先备知识"
    - field: "available_resources"
      type: "string"
      description: "可用的技术、空间、材料"
    - field: "lesson_duration"
      type: "string"
      description: "课时长度"
output_schema:
  type: "object"
  fields:
    - field: "awe_moment_design"
      type: "object"
      description: "设计好的敬畏体验——学生将遭遇什么、如何呈现、置于课堂何处"
    - field: "vastness_element"
      type: "string"
      description: "是什么营造了宏大感——物理、时间、概念还是社会层面"
    - field: "accommodation_bridge"
      type: "string"
      description: "敬畏时刻如何连接到学习——敬畏所激发的“求知需求”"
    - field: "teaching_sequence"
      type: "object"
      description: "如何编排课堂序列，使敬畏时刻驱动探究而不仅仅是娱乐"
chains_well_with:
  - "perma-based-lesson-designer"
  - "motivation-diagnostic-task-redesign"
  - "lesson-opening-designer"
  - "critical-thinking-task-designer"
teacher_time: "3 分钟"
tags: ["awe", "wonder", "curiosity", "Keltner", "engagement", "positive-emotion"]
---

# 敬畏与惊奇体验设计器（Awe & Wonder Experience Designer）

## 本技能的功能

在课堂中设计一个“敬畏或惊奇时刻”（moment of awe or wonder）——一种让学生停下脚步、感受到“宏大感”（vastness，某种比预期更庞大、更复杂或更壮美的事物）并触发“顺应需求”（need for accommodation，即更新自身心理模型以解释无法纳入现有认知之事物的内在驱动力）的体验。核心原则在于：敬畏不是装饰性的点缀——它是通往好奇心与探究的可能路径，但并非保证必然发生的情绪、思维转变或学习结果。输出包括敬畏时刻设计、宏大感来源分析、连接敬畏时刻与学习目标的桥梁（使惊奇导向探究而非仅仅娱乐），以及利用该时刻驱动内容深度学习的教学序列。AI 在此具有独特价值，因为设计敬畏时刻既需要学科专业知识（知道该内容**真正令人惊叹之处**在哪里），又需要心理学知识（知道如何呈现才能产生最大冲击）——而且教师因为对所教内容过于熟悉，往往已经失去了敏锐捕捉那份惊叹感的能力。

## 循证依据

Keltner 与 Haidt（2003）将“敬畏”（awe）界定为具有两个核心特征的情绪：感知到的宏大感（刺激物比观察者当前的参照系更庞大、更复杂或更有力量）以及顺应需求（观察者现有的心理模型无法解释所经历的事物，从而产生更新模型的驱动力）。Keltner（2023）将其拓展并归纳出八类敬畏诱发源：道德之美、集体沸腾、自然、音乐、视觉设计、灵性、生与死以及顿悟（突然的理解）。Shiota、Keltner 与 Mossman（2007）表明，敬畏会缩小自我——产生“微小自我”（small self）体验，从而减少自我中心关注并提高对新信息的开放度。将这些发现应用于课堂投入度属于一种设计推论；所生成的活动尚未被证明能直接改变学习者信念或学业成绩。Gottlieb、Keltner 与 Lombrozo（2018）证明，敬畏发挥着“科学情绪”的作用——它激发寻求解释的动机、提升好奇心并促进更深层加工。Valdesolo 与 Graham（2014）发现敬畏能提升对不确定性的容忍度——这是学习的关键品质，因为学习要求人能够安然面对“尚未知晓”。

## 输入规范

教师必须提供：
- **课堂内容：** 本节课的主题。*例如：“7 年级科学：宇宙的尺度——理解太阳系中天体的相对大小与距离” / “10 年级历史：一战战壕——理解士兵的处境与经历” / “8 年级数学：概率——理解看似随机的事件在大尺度下遵循可预测的规律”*
- **学生水平：** 年级。*例如：“7 年级”*

可选（如情境引擎可用，将自动注入）：
- **学科领域：** 课程学科
- **敬畏触发点：** 围绕其构建体验的特定元素
- **学生档案：** 班级兴趣、投入模式
- **可用资源：** 技术、空间、材料
- **课时长度：** 课程时长

## Prompt

```
Use Keltner & Haidt's (2003) vastness/accommodation model, Keltner's (2023) elicitors and Gottlieb, Keltner & Lombrozo's (2018) scientific-emotion research as design rationale. Classroom transfer remains emerging; do not promise cognitive or academic effects from this activity.

IMPORTANT: Awe is not the same as "cool" or "interesting." Awe requires VASTNESS — something that exceeds the student's current frame of reference — and a NEED FOR ACCOMMODATION — the student's existing understanding cannot account for what they're experiencing. A flashy video might be interesting; a carefully verified model of astronomical distances may challenge a learner's existing sense of scale. No stimulus guarantees awe.

IMPORTANT: Awe must serve learning, not replace it. A lesson that starts with an amazing video and then reverts to a worksheet has used awe as entertainment, not as a learning driver. The awe moment should create a NEED TO KNOW that the rest of the lesson satisfies. Keep inquiry tied to the stated objective; learning can also be worthwhile without an emotional response.

Your task is to design an awe moment for:

**Lesson content:** {{lesson_content}}
**Student level:** {{student_level}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Subject area:** {{subject_area}} — if not provided, infer from the content.
**Awe trigger:** {{awe_trigger}} — if not provided, identify the most awe-inducing element of the content.
**Student profiles:** {{student_profiles}} — if not provided, design for a typical class.
**Available resources:** {{available_resources}} — if not provided, assume a standard classroom with a projector and internet access.
**Lesson duration:** {{lesson_duration}} — if not provided, assume 50–60 minutes.

Verify stimulus facts, quantities and scale calculations against suitable primary sources before classroom use; label illustrative models and uncertainty. Check prior knowledge, sensory/physical access, supervision and emotional intensity. Offer a preview or accessible classroom alternative without loss of the learning goal. Do not use suffering, graphic material or traumatic experiences as spectacle. Awe, quietness and surprise are optional responses; inspect questions and work for learning instead of requiring an emotion.

Apply these principles:

1. **Identify the genuine source of awe in the content (Keltner & Haidt, 2003):**
   - Every subject contains something genuinely vast, complex, or beautiful — but familiarity can blind us to it.
   - Science: the scale of the universe, the complexity of a cell, the age of the Earth.
   - History: collective achievement, individuals' decisions and the chain of consequences from an event. Treat suffering with historical care, never as an emotional spectacle.
   - Mathematics: the emergence of patterns from chaos, the infinite, the unreasonable effectiveness of mathematics.
   - English: the power of a single sentence to change how you see the world.
   - Art: the capacity of humans to create beauty from nothing.

2. **Design for vastness (Shiota et al., 2007):**
   - Physical vastness: scale, size, distance, number.
   - Temporal vastness: deep time, long chains of cause and effect.
   - Conceptual vastness: the realisation that something is far more complex or interconnected than imagined.
   - Social vastness: collective human achievement, sacrifice, or creativity.

3. **Create the need for accommodation (Keltner & Haidt, 2003):**
   - The awe moment should leave students thinking: "I didn't know that was possible" or "I can't quite fit this into what I already knew."
   - This dissonance IS the learning opportunity — the rest of the lesson should help students build a new, more accurate mental model.

4. **Bridge awe to inquiry (Gottlieb et al., 2018):**
   - After the awe moment, channel the wonder into specific questions: "How is that possible?" / "Why does that happen?" / "What would we need to understand to explain this?"
   - The lesson content becomes the ANSWER to the questions that awe provokes.

5. **Protect the moment:**
   - Avoid unnecessary explanation before a reveal while providing any needed access information, preview or content warning. Don't tell students what they're about to see is "amazing" — let them feel it themselves.
   - Use silence after the moment. Let the vastness land. Don't rush to the next activity.
   - Allow varied responses, including no particular emotion; do not infer a shared emotional state.

Return your output in this exact format:

## Awe Moment Design: [Lesson Topic]

**Content:** [What students learn]
**For:** [Student level]

### The Awe Moment

[Detailed description of the moment — what students experience, how it's presented, what makes it awe-inducing]

### Vastness Element

[What creates the sense of vastness and which category of awe it uses]

### Accommodation Bridge

[How the awe moment creates a "need to know" that the lesson content satisfies]

### Teaching Sequence

[How the awe moment fits into the lesson — what comes before, the moment itself, and what comes after]

### Protecting the Moment

[How to present the awe moment without diluting it — timing, silence, teacher language]

**Self-check before returning output:** Verify that (a) the awe moment involves genuine vastness, not just "something interesting," (b) the moment connects directly to the learning objective, (c) the bridge from awe to inquiry is explicit, (d) the moment is protected with appropriate pacing and silence, and (e) the lesson links wonder to learning, and (f) facts/scale, access/supervision and preview/alternative choices have been checked without requiring awe.
```

## 示例输出

**场景：** *课堂内容：“7 年级科学：太阳系的尺度——理解行星的相对大小与彼此间距” / 学生水平：“7 年级” / 可用资源：“学校操场可用、标准教室、投影仪”*

---

## 敬畏时刻设计：太阳系的尺度

**内容：** 太阳系中的相对大小与距离
**适用对象：** 7 年级科学

### 敬畏时刻

首先检查路线、安全监护、可见度以及行动/感官无障碍条件。在不损失学习目标的前提下，同步提供教室内的图表/触觉或数字模型、提前预览或坐姿观察替代方案。对于操场版本，将班级带到约定且有监护的区域。在一端放一个足球（直径 22 厘米）。告诉学生：“这个足球是太阳。我想请你们猜一猜——如果太阳是这个足球，地球有多大？它离太阳有多远？”

收集猜测。学生通常会猜地球像一颗玻璃弹珠，而且“就在那儿”（指着 5–10 米外的地方）。

对于这一演示模型，教师应在使用前核对标称直径与距离：太阳 139 万公里，地球 1.27 万公里且距太阳 1.5 亿公里，木星 14.3 万公里且距太阳 7.78 亿公里。按 22 厘米太阳的比例换算，地球直径约 2 毫米、距离约 24 米；木星直径约 23 毫米、距离约 123 米。这些是四舍五入的模型数值，而非当前实时轨道距离预测。随后亮出地球——一颗约 2 毫米大小的胡椒粒。举起来，让他们看清它与足球相比有多么渺小。（保持沉默。先不要解释。让他们感受尺度的悬殊。）

接着问：“那它有多远呢？”开始走。一直走。按这个比例，地球距离太阳 24 米。学生看着你走啊、走啊、走啊。当你走到终点举起那颗胡椒粒时，回头看那个太阳足球已经变得很远，地球微乎其微，而其间的空间无比辽阔。

现在问：“木星呢？”按此比例，木星直径约 23 毫米；请使用测量过的物体或图示，而非规格不明的七叶树果。它距离太阳 123 米。继续走。站在木星的位置回头望，那个足球太阳几乎快看不见了。

作为可选的恒星拓展，可使用经过核实的恒星直径与距离数据按同一比例计算，并核对地图定位；切勿将比邻星简单画成另一个足球大小，也不要在未核实距离的情况下随便点名某座城市。若缺乏可靠数据，则将本次现场体验保持在上述太阳系模型之内。

保持沉默。让那份宏大感沉淀下来。

### 宏大感要素

**物理宏大感——尺度。** 敬畏感源于用身体步行丈量距离的直观体验。在书上读到“地球距离太阳 1.5 亿公里”只是一个干巴巴的事实；而手里捏着一颗胡椒粒走出 24 米、回头望向远处的足球，则是一场**切身体验**。这种尺度超出了人脑直觉所能把握的范围——这正是 Keltner 对“宏大感”的定义。经过核实的遥远恒星拓展或许能深化尺度问题，但它属于可选项；学习者无需报告自己感到了“敬畏”，也能展示理解。

### 顺应桥梁

这个敬畏时刻会催生出具体的问题：
- “如果地球这么小、离得这么远，我们到底是怎么知道外面有什么的？”
- “行星隔得这么远，为什么还会绕着太阳转？”
- “在它们之间航行需要多长时间？”
- “如果最近的恒星都那么远，宇宙里只有我们吗？”

本节课的其余部分正是利用这些问题来教授课程内容：相对大小（定量数据）以及太阳系结构。如果轨道力学或地外生命问题超出了本节课目标，则将其留作后续探究。敬畏时刻让教学内容变得“不可或缺”——学生迫切想弄懂他们刚刚亲历的现象。

### 教学序列

**第一阶段——敬畏时刻（15 分钟）：**
在操场进行。足球 → 胡椒粒 → 步行丈量距离。提供必要的无障碍信息与模型假设说明，留出观察与提问时间。在适宜时使用教室替代方案。

**第二阶段——将惊奇转化为探究（5 分钟）：**
回到教室。“刚才的体验之后，你们有什么问题？”把问题收集在黑板上并归类。对照既定教学目标梳理学生提问，并显性补充学生未提但课程要求的核心问题；兴趣与问题覆盖面不能仅靠自发保证。

**第三阶段——建构理解（25 分钟）：**
利用这些问题组织学习：相对大小（配合数据表——将操场模型换算为真实测量值）、距离（引入天文单位与光年）以及太阳系结构。每一组数据都与操场体验相连接：“还记得你们走到木星走了多远吗？那就是 7.78 亿公里。”

**第四阶段——反思（5 分钟）：**
“写下一句话，捕捉今天最让你惊讶的发现。然后再写下一个你仍然想知道答案的问题。”收齐，用来规划下一节课。

### 保护这一时刻

1. **提供预览选择。** 提前说明户外活动与无障碍安排。学习者可以选择提前预览尺度模型；“惊喜感”是可选的，而非学习目标本身。

2. **在每次揭示后保持沉默。** 当你举起胡椒粒时：沉默。当你走到 24 米标记处时：沉默。在任何经过核实的拓展之后：留出消化时间。让宏大感先在身体里落定，再启动理性分析。教师的本能是立刻开口讲解——请克制住这个冲动，保持 10 秒沉默。

3. **不要用幽默冲淡它。** 敬畏是一种严肃的情绪。学生可能会紧张地发笑（这是面对震撼事物时的正常反应）。接纳幽默或平静的反应，不要强行赋予某种隐藏情绪；给他们留出消化时间，然后把注意力拉回尺度问题。

4. **允许学生以各自的方式表达反应。** 有人会说“哇”，有人会说“太夸张了”，有人会保持安静。所有这些——包括没有感到敬畏或早已知道这个例子——都是正常的反应。不要规训学生的情绪反应，而是把它们引导向探究问题。

---

## 已知局限性

1. **敬畏是高度主观的。** 让一名学生产生敬畏感的事物，对另一名学生可能只是“有点意思”。尺度模型对大多数学生有效，因为它调动了身体的宏大感体验——但已经见过这一演示的学生可能不会产生同样的敬畏感。教师必须了解自己的学生，选择匹配群体既有经验的触发点。

2. **敬畏时刻天生是稀缺的。** 如果每节课都以一个“敬畏时刻”开场，效果会迅速衰减。敬畏应当策略性地使用——或许每个单元或主题使用一次——放在内容真正值得的节点上。滥用会把敬畏变成廉价奇观。

3. **教育领域中关于敬畏的循证基础尚处于新兴阶段，而非成熟定论。** Keltner 的研究在心理学中非常扎实，但其在课堂学习中的应用缺乏充分的对照实验。心理学发现提供了理论依据，但向课堂好奇心、不确定性容忍度与学业成绩的迁移效果在本设计中尚未实证确立。本技能基于成熟的积极情绪科学在教育情境中的应用，而非直接的教育随机对照试验（RCT）。
