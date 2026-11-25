---
# AGENT SKILLS STANDARD FIELDS (v2)
name: three-part-lesson-designer
description: "设计蒙台梭利三段式教学课，通过具体教具与命名引入概念。适用于借助实物操作教授词汇、分类或概念。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "montessori-alternative-approaches/three-part-lesson-designer"
skill_name: "三段式教学设计器（蒙台梭利）"
domain: "montessori-alternative-approaches"
version: "1.0"
evidence_strength: "moderate"
evidence_sources:
  - "Lillard & Else-Quest (2006) — Evaluating Montessori education (Science, 313, 1893-1894)"
  - "Lillard (2012) — Preschool children's development in classic Montessori, supplemented Montessori, and conventional programs"
  - "Lillard (2005) — Montessori: The Science Behind the Genius"
  - "Séguin (1866) — Idiocy: and its treatment by the physiological method (origin of the three-period lesson)"
  - "Standing (1957) — Maria Montessori: Her Life and Work (detailed description of three-period lesson)"
input_schema:
  required:
    - field: "concept_to_teach"
      type: "string"
      description: "本节课将引入的具体概念、词汇或分类——学生需要学会命名、辨认与回忆的内容"
    - field: "concrete_materials"
      type: "string"
      description: "将使用的实物材料或教具——学生在课上看到并触摸操作的对象"
  optional:
    - field: "student_level"
      type: "string"
      description: "年龄/年级与发展阶段"
    - field: "subject_area"
      type: "string"
      description: "课程学科"
    - field: "group_size"
      type: "string"
      description: "学生人数——蒙台梭利实践中通常为 1–3 人"
    - field: "prior_knowledge"
      type: "string"
      description: "学生关于该概念或相关概念已有的知识"
    - field: "language_considerations"
      type: "string"
      description: "任何语言需求——EAL 学生、专业词汇或教室内的多语种情况"
output_schema:
  type: "object"
  fields:
    - field: "three_period_lesson"
      type: "object"
      description: "涵盖全部三个阶段的完整课程——命名、再认与回忆"
    - field: "materials_preparation"
      type: "object"
      description: "如何准备与呈现材料——包括概念孤立化"
    - field: "assessment_indicators"
      type: "object"
      description: "如何判断学生已掌握每个阶段——理解的可观察证据"
    - field: "extension_activities"
      type: "array"
      description: "针对快速掌握学生的拓展活动以及针对需要额外练习学生的活动"
chains_well_with:
  - "prepared-environment-designer"
  - "mixed-age-learning-task-designer"
  - "uninterrupted-work-cycle-designer"
  - "retrieval-practice-designer"
teacher_time: "3 分钟"
tags: ["Montessori", "three-part-lesson", "Lillard", "naming", "recognition", "recall", "vocabulary", "classification", "concrete"]
---

# 三段式教学设计器（蒙台梭利）

## 本技能的功能

设计蒙台梭利三段式教学（亦称三阶段课或三部曲课）——这是最易编码化且研究最充分的蒙台梭利教学实践。三段式教学最初由 Édouard Séguin（1866）开发，并由玛丽亚·蒙台梭利改造用于具体教具教学。它包含三个清晰阶段：第一段（引入/命名）——教师在学生操作材料的同时命名概念：“这是一个等腰三角形”；第二段（再认）——教师请学生从选项中指认概念：“请给我看哪个是等腰三角形”；第三段（回忆）——教师请学生凭记忆说出概念名称：“这个叫什么？”这一序列经过刻意排序，因为命名（第一段）仅需被动接收，再认（第二段）需要将名称与实物匹配，而回忆（第三段）需要从记忆中主动提取——每一段都比前一段要求更高的认知加工。Lillard 等人（2006）发表在《Science》上的研究证明，蒙台梭利项目中的儿童在学业与社交成果上均展现出显著优势，而三段式教学正是高保真蒙台梭利实施的标志性具体教学实践之一。本技能设计完整课程，包括材料准备、各阶段具体话术、评估指标与拓展活动。

## 循证基础

Lillard 与 Else-Quest（2006）在《Science》上发表了一项里程碑式研究，对比了蒙台梭利学校儿童与其他类型学校匹配对照组的发展结果。蒙台梭利儿童在标准化阅读和数学测试中表现显著更优，且展现出更强的执行功能、社交问题解决能力与社群归属感。虽然该研究评估的是整个蒙台梭利项目（而非孤立的单项实践），但三段式教学在蒙台梭利文献（Lillard, 2005; Standing, 1957）中被认定为区分高保真蒙台梭利与常规教学的基础性教学实践之一。Lillard（2012）随后开展了一项后续研究，对比“经典”蒙台梭利（高保真，包括持续使用带具体教具的三段式教学）、“补充型”蒙台梭利（蒙台梭利教具加常规活动）以及常规项目。经典蒙台梭利儿童在多项指标上优于其他两组，表明特定的蒙台梭利实践——包括三段式教学——促成了整体项目效应，而非单纯归因于生源选择偏差或学校整体质量。Lillard（2005）在《Montessori: The Science Behind the Genius》中从认知科学视角剖析了三段式教学，指出它契合多项循证原则：始于具体感官经验（具身认知）、孤立待学概念（降低认知负荷）、在第三段使用主动提取（测试效应），以及要求掌握当前阶段后再推进（掌握学习）。三段式结构还直接对应认知科学中再认记忆（较容易，第二段）与回忆记忆（较困难，第三段）的区分——这一区分至少自 Anderson 与 Bower（1972）以来在记忆研究中已充分确立。Séguin（1866）最初设计三段式方法是为了向智力障碍儿童教授分类与词汇，证明了从命名经由再认到回忆的结构化序列即便对存在显著认知挑战的学习者依然有效——印证了该方法的稳健性。

## 输入模式

教师必须提供：
- **待教概念：** 学生将学会命名、辨认与回忆的内容。*例如：“三种三角形：等边、等腰和不等边三角形” / “花的构造：花瓣、雄蕊、雌蕊、萼片” / “物质三态：固态、液态、气态” / “几何立体：正方体、球体、圆柱体、圆锥体” / “音符时值：四分音符、二分音符、全音符”*
- **具体材料：** 学生将触摸操作的实物。*例如：“来自几何橱的三个木制三角形——每种一个，一面涂成蓝色” / “解剖并固定在绿色毛毡垫上的真花” / “三个容器：一块木头、一杯水、一个充满空气的气球” / “来自蒙台梭利数学架的木制几何立体”*

可选（如有，由上下文引擎注入）：
- **学生水平：** 年龄/年级与发展阶段
- **学科领域：** 课程学科
- **小组规模：** 学生人数
- **先验知识：** 学生已经知道的内容
- **语言考量：** 任何语言需求

## 提示词

```
You are an expert in Montessori pedagogy with specific knowledge of the three-period lesson structure, grounded in Lillard's (2005, 2006, 2012) research, Séguin's (1866) original method, and Standing's (1957) detailed descriptions of Montessori practice. You understand that the three-period lesson is not merely a vocabulary exercise — it is a carefully structured sequence that builds from passive reception (naming) through active recognition to active recall, using concrete materials to anchor abstract concepts in sensory experience. You also understand the cognitive science behind the sequence: Period 1 creates an association between word and object; Period 2 strengthens that association through recognition (lower cognitive demand); Period 3 tests retrieval (higher cognitive demand). The lesson should only progress from one period to the next when the student demonstrates mastery of the current period.

CRITICAL PRINCIPLES:
- **Isolate the concept.** The materials should differ ONLY in the feature being taught. If you're teaching types of triangle, all triangles should be the same colour, same material, same size (as much as possible) — so the ONLY difference is the shape. This is Montessori's "isolation of the difficulty" principle, which aligns with cognitive load theory: reduce extraneous variation so the student's attention is directed to the relevant feature.
- **Use precise language.** In Period 1, the teacher uses the EXACT term, clearly and simply: "This is an isosceles triangle." Not "This one is called isosceles — it's the one with two equal sides." The name comes first; the explanation comes later, after the student can name and recognise it. Overloading Period 1 with explanation defeats the purpose.
- **Period 2 should be playful and active.** "Show me the isosceles triangle" can be varied: "Put the isosceles triangle on the blue mat." "Give me the isosceles triangle." "Put the isosceles triangle under the table." The recognition task is embedded in movement and game-like interaction. This sustains engagement and provides multiple retrieval opportunities.
- **Period 3 is the test — don't rush to it.** Only move to Period 3 when Period 2 is fluent. If the student hesitates in Period 3 (cannot recall the name), return to Period 2 (recognition) rather than telling them the answer. The sequence is: if Period 3 fails → return to Period 2 → try Period 3 again later.
- **Three items maximum per lesson.** The three-period lesson works best when introducing 2-3 items at a time. More than 3 overloads working memory. If there are more concepts to teach, split them across multiple lessons.

Your task is to design a three-period lesson for:

**Concept to teach:** {{concept_to_teach}}
**Concrete materials:** {{concrete_materials}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Student level:** {{student_level}} — if not provided, design for an early years/primary context (ages 3-9), as this is where the three-period lesson is most commonly used.
**Subject area:** {{subject_area}} — if not provided, infer from the concept.
**Group size:** {{group_size}} — if not provided, design for 1-3 students (the Montessori norm for this lesson type).
**Prior knowledge:** {{prior_knowledge}} — if not provided, assume this is the student's first encounter with these terms.
**Language considerations:** {{language_considerations}} — if not provided, assume the lesson is conducted in the students' primary language.

Return your output in this exact format:

## Three-Period Lesson: [Concept]

**Concept:** [What students will learn to name, recognise, and recall]
**Materials:** [What is used]
**Group size:** [How many students]
**Estimated duration:** [Typically 5-15 minutes for the three periods]

### Materials Preparation

[How to set up the materials before the lesson — including isolation of the concept, arrangement, and any preparation the teacher needs to do]

### Period 1: Introduction (Naming)

[The exact sequence for introducing and naming each item. Include the precise teacher language — word for word. Describe the sensory engagement: how the student handles the material while hearing the name.]

### Period 2: Recognition ("Show Me")

[The recognition activities — varied requests that ask the student to identify named items. Include at least 5-6 varied prompts that embed recognition in movement, game, and interaction. Describe how to cycle through all items and how to gauge readiness for Period 3.]

### Period 3: Recall (Naming by Student)

[The recall phase — how to prompt the student to produce the name from memory. Include the specific questions, what to do if the student succeeds, and what to do if the student cannot recall (return to Period 2, do NOT give the answer).]

### Assessment Indicators

[How to know the student has mastered each period — observable evidence]

| Period | Mastery Indicator | Not Yet Ready |
|---|---|---|
| 1 | [What success looks like] | [What indicates more work is needed] |
| 2 | [What success looks like] | [What indicates more work is needed] |
| 3 | [What success looks like] | [What indicates more work is needed] |

### Extensions

[What comes after mastery — follow-up activities that deepen understanding, connect to other work, or extend to new concepts]

### Adaptation Notes

[How to adapt the lesson for different ages, group sizes, or contexts — including use outside traditional Montessori settings]

**Self-check before returning output:** Verify that (a) the concept is isolated in the materials, (b) language in Period 1 is precise and minimal, (c) Period 2 is varied and active, (d) Period 3 is not rushed, (e) the return-to-Period-2 protocol is included, and (f) no more than 3 items are introduced per lesson.
```

## 示例输出

**场景：** *待教概念：“三种三角形：等边（三边相等）、等腰（两边相等）和不等边（三边均不等）” / 具体材料：“来自几何橱的三个大型木制三角形——等边、等腰、不等边各一个。均涂有相同色调的蓝色。最长边约15厘米。每个三角形上都有一个便于抓握的小圆钮” / 学生水平：“二年级（6-7岁）” / 学科领域：“数学——几何” / 小组规模：“2名学生”*

---

## 三段式教学：三角形的类型

**概念：** 三种三角形——等边三角形、等腰三角形、不等边三角形
**材料：** 来自几何橱的三个蓝色木制三角形（等边、等腰、不等边）
**小组规模：** 2名学生
**预计时长：** 10–15分钟

### 材料准备

将三个三角形放在一块素色工作毯（中性色——米白或浅灰）上。将它们排成一排，彼此留出间隔，朝向一致（一个顶点朝上）。工作毯提供了界定清晰的工作空间和视觉焦点。移走紧邻区域内的其他任何材料——学生的注意力应完全集中在这三个形状上。

**孤立化检查：** 三个三角形颜色相同（蓝色）、材质相同（木头）、大小相近。**唯一**的系统性差异在于它们各边之间的关系。这种孤立化确保当你说出“等腰”时，学生的注意力被引导至定义它的特征——而非颜色或大小差异。

课前，用手指沿每个三角形的边缘描摹一遍，确认能触觉感知边长的差异。你将引导学生做同样的动作。

### 第一段：引入（命名）

坐在学生身旁（而非对面——以便与他们共享观察材料的视角）。

**教具 1——等边三角形：**
捏住小圆钮拿起等边三角形。用食指缓慢描摹三条边，在每个角略作停顿。清晰而简洁地说：

*“这是一个等边三角形。”*

将其放在学生面前。邀请每位学生拿起它，描摹各边，并说出名称：*“等边三角形。”* 此时不要解释为什么叫等边。名称本身就足够了。

**教具 2——等腰三角形：**
拿起等腰三角形。描摹各边——在两条相等的边上略作停顿，再摸不同长度的边。说：

*“这是一个等腰三角形。”*

放在学生面前。每位学生拿起、描摹并说：*“等腰三角形。”*

**教具 3——不等边三角形：**
拿起不等边三角形。描摹三条边——每一条在视觉上长度都明显不同。说：

*“这是一个不等边三角形。”*

放下。每位学生拿起、描摹并说：*“不等边三角形。”*

**第一段总耗时：** 2–3分钟。目的**仅在于建立联结**——通过感官体验（看、触、听、说）将词语与实物联系起来。

### 第二段：再认（“请给我看”）

现在三个三角形摆放在工作毯上。学生已经知道了三个名称（至少是被动接收）。第二段测试他们能否将名称与实物匹配。

变换指令以保持活动趣味性，并将再认嵌入身体动作中：

1. *“请给我看看等边三角形。”*（学生指向或拿起正确的三角形。）
2. *“你能把等腰三角形放到蓝椅子上吗？”*（移动——学生必须识别它**并**带到房间另一头。）
3. *“请把不等边三角形递给我。”*（社交互动——递给教师。）
4. *“把等边三角形放到等腰三角形上面。”*（需要同时正确识别**两个**。）
5. *“用你的手肘碰一下不等边三角形。”*（趣味性——保持投入，测试同样的再认能力。）
6. *“把它们排成一排：等边在最前，然后是不等边，最后是等腰。”*（排序——需要全部识别。）
7. *“我藏起了哪一个？”*（将其中一个三角形藏到身后，展示剩下的两个。学生必须凭名称说出缺少的那一个——这是通往第三段的桥梁。）

**多次循环所有三个名称。** 打乱顺序。观察是否有犹豫——如果学生在拿起等腰三角形前停顿思考，说明他们在进入第三段前还需要在第二段多加练习。

**进入第三段的准备信号：** 学生在至少3种不同指令下都能正确、迅速、毫不犹豫地识别出全部三种三角形。

**第二段总耗时：** 4–6分钟。

### 第三段：回忆（由学生命名）

一次指向或拿起一个三角形，问：

*“这个三角形叫什么名字？”*

从学生在第二段中显得最自信的那一个开始——给他们一次早期成功体验。

**如果学生命名正确：** 点头或微笑。换下一个三角形。无需过度夸奖——成功本身就是最好的奖励。

**如果学生犹豫或命名错误：** **不要**纠正他们或直接说出答案。相反，退回到第二段：

*“请给我看看等腰三角形。”*（退回到难度更低的再认阶段。）

再进行 2–3 次再认指令后，再次尝试第三段。如果学生仍然无法回忆，以积极肯定结束本课（“你们今天在这些形状上做得非常棒”），明天再来继续。名称会在一夜之间得到巩固。

**回忆提问顺序：**
1. 拿起学生掌握最稳的三角形。*“这个叫什么？”*
2. 拿起第二稳的。*“那这个呢？”*
3. 拿起最具挑战性的。*“这个又叫什么呢？”*

**第三段总耗时：** 2–3分钟。

### 评估指标

| 阶段 | 掌握指标 | 尚未就绪 |
|---|---|---|
| 第一段（命名） | 学生能在手持材料时复述每个名称——“等边”、“等腰”、“不等边”——发音基本准确 | 学生无法复述名称，或持续混淆两个名称 |
| 第二段（再认） | 学生在3次及以上连续变换指令中均能毫不犹豫地正确识别所有三种三角形 | 学生犹豫、伸手拿错后才自我纠正，或持续混淆其中两种 |
| 第三段（回忆） | 当被指认时，学生无需提示即可在连续2次及以上尝试中正确说出所有三种三角形的名称 | 学生无法说出名称，或经过长时间停顿且明显不确定后才说出 |

### 拓展活动

**即时拓展（同一时段或次日）：**
- **分类：** 给学生一组混合的9个三角形（每种3个，大小与朝向各异），请他们用学过的名称将其分成三组。
- **描摹与标注：** 学生在纸上描出每个三角形，并在下方写下（或口述）名称。
- **发现提问：** “你们已经知道它们的名字了。现在，你们能找出它们**为什么**叫这些名字吗？仔细观察每个三角形的边。”引导学生得出：等边 = 边相等，等腰 = 两条边相等，不等边 = 没有相等的边。这种**解释**放在命名之后，而非之前。

**后续拓展（接下来几周）：**
- 用新的一组教具进行三段式教学：四边形的类型，或三角形的组成部分（顶点、边、角）。
- 测量：用尺子测量每个三角形的边长，验证相等/不等的边。
- 艺术：使用三种三角形创作拼贴画，并标注每一种。
- 环境寻宝：在教室或校园建筑中寻找等边、等腰和不等边三角形的实例。

### 调整说明

**针对高龄学生（三至六年级）：** 当引入新的专业词汇时，三段式教学适用于任何年龄。对于高龄学生，若概念较简单可一次引入超过3项，或将三段式教学与分类活动配对。第二段的趣味动作也可调整——高龄学生可能喜欢竞赛元素（“谁能最快找到等腰三角形？”）或同伴互测（“用第三段的问题互相提问”）。

**针对非蒙台梭利环境：** 三段式教学并不依赖蒙台梭利教具。任何具体、概念孤立化良好的实物组都适用：地理中的岩石类型、音乐中的乐器家族、科学中的叶片类型。核心原则——概念孤立化、精确命名、先再认后回忆、第三段失败退回第二段——可迁移至任何教室。

**针对 EAL 学生：** 三段式教学对 EAL 学习者尤其有效，因为它通过具体、感官联结而非口头定义来建构词汇。可考虑在第一段中结合学生的母语与英语：“This is an equilateral triangle — 等边三角形。”具体教具将意义锚定在两种语言中。

**针对更大群组：** 蒙台梭利三段式教学专为 1–3 名学生设计。在30人的班级中，无法用传统格式全班开展此课。替代方案：（a）在其他学生独立工作时对小组开展；（b）使用大型展示教具与全班齐答改写为全班活动；（c）训练学生结对互相开展第二段和第三段活动。

---

## 已知局限

1. **专门针对三段式教学的证据嵌入在更广泛的蒙台梭利项目评估中。** Lillard 等人（2006）和 Lillard（2012）评估的是蒙台梭利项目整体，而非孤立的单项实践。三段式教学是构成高保真蒙台梭利的众多实践之一，其对整体效应的独立贡献无法从研究设计中剥离。该课型与已确立的认知科学原则（提取练习、具体表征、掌握学习）高度一致，这提供了独立的理论支持，但针对这一特定课型的直接实证证据仅限于项目层面评估。

2. **三段式教学专为具体、可分类的概念设计。** 它在词汇、分类和命名任务上表现卓越——即存在明确无歧义的名称对应明确可感知的实物。它不太适用于抽象或关系性概念（“正义”、“反讽”、“供需关系”），因为这些概念无法握在手中并在材料中孤立出来。

3. **“每课最多三项”的规则限制了单次容量。** 每次只引入 2–3 项意味着一个包含10个类别的分类系统需要 3–4 节独立课程。这在教学法上是合理的（防止过载），但较为耗时。在面临时间压力的常规教室中，教师可能会忍不住每节课引入更多项目，从而削弱该方法的效果。

4. **该课型预设了一个平静、专注的环境。** 三段式教学要求小组在 10–15 分钟内保持持续专注。在嘈杂、频繁被打断或过度刺激的环境中，这种安静精准的教学节奏可能难以维持。有准备的环境（见技能93）是蒙台梭利对此的解决方案，但在常规学校环境中未必总是具备。
