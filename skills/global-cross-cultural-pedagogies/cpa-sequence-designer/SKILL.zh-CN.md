---
# AGENT SKILLS STANDARD FIELDS (v2)
name: cpa-sequence-designer
description: "使用教具为数学概念设计“具象-表象-抽象（CPA）”学习序列。适用于采用新加坡数学方法教学或学生在理解抽象概念遇到困难时。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "global-cross-cultural-pedagogies/cpa-sequence-designer"
skill_name: "具象-表象-抽象学习序列设计师"
domain: "global-cross-cultural-pedagogies"
version: "1.0"
evidence_strength: "strong"
evidence_sources:
  - "Bruner (1966) — Toward a Theory of Instruction (enactive, iconic, symbolic)"
  - "Ministry of Education Singapore (2012) — Mathematics Syllabus: Primary and Secondary"
  - "Leong, Ho & Cheng (2015) — Concrete-Pictorial-Abstract: surveying its origins and charting its future"
  - "Fyfe, McNeil, Son & Goldstone (2014) — Concreteness fading in mathematics and science instruction"
  - "Kaur (2019) — The what, why and how of the 'Model' method in Singapore mathematics"
input_schema:
  required:
    - field: "mathematical_concept"
      type: "string"
      description: "学生需要理解的数学概念——最终在抽象层面应当掌握的内容"
    - field: "student_level"
      type: "string"
      description: "年龄/年级及当前的数学理解水平"
  optional:
    - field: "current_approach"
      type: "string"
      description: "教师目前如何教授这一概念——现在的做法"
    - field: "common_errors"
      type: "string"
      description: "学生在该概念上常犯的典型错误"
    - field: "available_manipulatives"
      type: "string"
      description: "可用的实物教具——方块、计数片、十进制积木、分数条"
    - field: "lesson_time"
      type: "string"
      description: "可用于 CPA 序列的课时时间"
output_schema:
  type: "object"
  fields:
    - field: "cpa_sequence"
      type: "object"
      description: "完整的 C→P→A 序列——学生在每个阶段做什么，以及阶段之间的明确架桥"
    - field: "concrete_stage"
      type: "object"
      description: "基于教具的活动——学生亲手操作什么，以及这能建构什么理解"
    - field: "pictorial_stage"
      type: "object"
      description: "视觉表征活动——条形图模型（bar models）、示意图、数轴——连接具象与抽象"
    - field: "abstract_stage"
      type: "object"
      description: "符号/数字运算——连接到正式的数学符号表达"
    - field: "bridging_questions"
      type: "array"
      description: "帮助学生将一个阶段连接到下一阶段的问题"
chains_well_with:
  - "variation-theory-task-designer"
  - "worked-example-fading-designer"
  - "explicit-instruction-sequence-builder"
  - "diagnostic-question-generator"
  - "pedagogical-content-knowledge-developer"
teacher_time: "4 分钟"
tags: ["CPA", "Singapore-maths", "Bruner", "manipulatives", "bar-model", "concreteness-fading", "mathematics"]
---

# 具象-表象-抽象学习序列设计师

## 本技能的作用

设计一个学习序列，带领学生从具象操作（实物对象），经过表象表征（示意图、条形图模型、数轴），走向抽象符号（符号与数字）——遵循新加坡数学课程框架核心的 CPA（Concrete-Pictorial-Abstract）教学法。该方法植根于 Bruner (1966) 的表征理论：学习者依次经历动作表征（enactive，基于动作）、图像表征（iconic，基于图像）和符号表征（symbolic，基于语言/符号）。核心洞察在于：这三个阶段不是彼此割裂的活动，而是一个连贯的递进过程——每个阶段建构的理解都会让下一阶段变得有意义。输出包括每个阶段的活动设计以及明确的架桥问题，帮助学生看清自己用实物做的操作、在图上画的模型与数字和符号之间的联系。AI 在此尤为有价值，因为设计有效的 CPA 序列需要确保具象阶段和表象阶段真正体现了数学“结构”（而不仅仅是表面演示），并且阶段之间的过渡是明确搭建的，而非想当然的。

## 循证基础

Bruner (1966) 提出学习者以三种模式表征知识：动作表征（通过操作实物）、图像表征（通过图像与示意图）和符号表征（通过文字与数字）。他主张新概念应当先通过动作经验引入，再进行图像表征，最后进入符号表征。新加坡教育部（2012）将其采纳为数学课程核心的 CPA 教学法，打造了一个在国际测评（TIMSS、PISA）中长期名列前茅的教育体系。Leong, Ho & Cheng (2015) 梳理了新加坡的实施经验，指出 CPA 绝非简单的“用用教具”，而是一个经过精心设计的递进序列，其中每一阶段都刻意与下一阶段相连。表象阶段——尤其是条形图模型（bar model，一种用矩形直观表示数学关系的视觉工具）——是新加坡极具特色的贡献，它架起了具象操作与抽象代数之间的桥梁。Fyfe 等 (2014) 为“具象渐隐（concreteness fading）”提供了实验证据——从具象表征出发，逐步剥离具象特征，直到只剩下抽象结构。他们证明，从具象出发并渐隐至抽象，比直接从抽象开始、只停留在具象不渐隐或同时混用两者，能产生更好的迁移效果。Kaur (2019) 记录了新加坡数学中的“模型法（bar modelling）”，展示了这一表象工具如何让学生表征并解决原本需要代数方程才能解决的复杂应用题。

## 输入模式

教师必须提供：
- **Mathematical concept（数学概念）：** 学生需要理解的概念。*例如："Adding fractions with different denominators" / "Solving word problems involving ratio" / "Understanding place value in 3-digit numbers" / "Multiplying a 2-digit number by a 1-digit number"*
- **Student level（学生水平）：** 年级及当前理解水平。*例如："Year 4, can add fractions with same denominators but struggle when denominators are different" / "Year 2, understand tens and ones but get confused with hundreds"*

可选（如上下文引擎可用则自动注入）：
- **Current approach（当前教法）：** 教师目前如何教授这一内容
- **Common errors（常见错误）：** 学生常犯的典型错误
- **Available manipulatives（可用教具）：** 手头可用的实物资源
- **Lesson time（课时时间）：** 可用教学时间

## Prompt

```
You are an expert in the Concrete-Pictorial-Abstract (CPA) approach as implemented in the Singapore Mathematics Curriculum Framework, with deep knowledge of Bruner's (1966) representational theory, the Singapore MOE's (2012) mathematics syllabus design, Leong et al.'s (2015) analysis of CPA implementation, Fyfe et al.'s (2014) research on concreteness fading, and Kaur's (2019) documentation of the Singapore bar model method. You understand that CPA is not "use blocks, then draw, then do sums" — it is a carefully designed progression where each stage builds a specific aspect of understanding that is EXPLICITLY connected to the next stage.

CRITICAL PRINCIPLES:
- **The concrete stage must represent the mathematical structure.** Giving students cubes to count is not CPA — it's just counting with props. The concrete manipulation must embody the mathematical relationship. For fractions: physically breaking a whole into parts and comparing. For multiplication: arranging objects into arrays where the structure of rows × columns IS multiplication.
- **The pictorial stage is not illustration — it is a thinking tool.** Bar models, number lines, and diagrams are not pictures of the answer — they are tools for THINKING about the mathematical structure. Students should learn to draw the representation as a problem-solving strategy, not just as a way to show their working.
- **Bridging between stages must be EXPLICIT.** The most common CPA failure is assuming students will automatically see the connection between the concrete, the pictorial, and the abstract. They won't. The teacher must explicitly connect: "Remember when you broke the fraction strip into quarters? This bar model shows the same thing. And this fraction symbol ¼ means the same thing again." Each stage must be named and linked.
- **Concreteness fading, not replacement.** The concrete stage is not abandoned when students move to pictorial — it remains available as a reference. Students should be able to move BACK to a previous stage if they get confused at a higher level. The stages are cumulative, not sequential.

Your task is to design a CPA sequence for:

**Mathematical concept:** {{mathematical_concept}}
**Student level:** {{student_level}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Current approach:** {{current_approach}} — if not provided, design the full CPA sequence from scratch.
**Common errors:** {{common_errors}} — if not provided, identify likely errors from the concept.
**Available manipulatives:** {{available_manipulatives}} — if not provided, suggest accessible, low-cost manipulatives.
**Lesson time:** {{lesson_time}} — if not provided, design for a 60-minute lesson.

Return your output in this exact format:

## CPA Sequence: [Mathematical Concept]

**Concept:** [What students will understand]
**Students:** [Year group and starting point]
**Mathematical structure:** [The underlying mathematical relationship the CPA sequence must represent]

### Stage 1 — Concrete (Enactive)

**Manipulative:** [What physical objects students use]
**Activity:** [What students do with the objects — step by step]
**What this builds:** [What understanding the concrete manipulation develops]
**Key teacher language:** [What the teacher says to name the mathematical structure while students manipulate]

### Bridging: Concrete → Pictorial

[How the teacher explicitly connects the physical objects to the visual representation — "This block you're holding is the same as this bar I'm drawing"]

### Stage 2 — Pictorial (Iconic)

**Representation:** [Bar model / number line / array diagram / other visual tool]
**Activity:** [What students draw and how they use the representation to solve problems]
**What this builds:** [What understanding the pictorial representation develops beyond the concrete stage]
**Key teacher language:** [What the teacher says to connect the diagram to the physical experience]

### Bridging: Pictorial → Abstract

[How the teacher explicitly connects the visual representation to the symbolic notation — "This section of the bar model represents the same thing as this number in the equation"]

### Stage 3 — Abstract (Symbolic)

**Notation:** [The formal mathematical symbols and procedures]
**Activity:** [What students do with numbers and symbols]
**What this builds:** [Fluent, flexible use of the abstract notation, grounded in concrete and pictorial understanding]
**Connection back:** [How students can return to pictorial or concrete representations if they get stuck at the abstract level]

### Common Errors and CPA Responses

[For each common error, explain which CPA stage addresses it — "Students who make this error need to return to the concrete/pictorial stage because..."]

### Assessment Check

[How to verify that students understand the concept at all three levels — not just procedurally at the abstract level]

**Self-check before returning output:** Verify that (a) the concrete stage genuinely represents the mathematical structure, not just provides counting props, (b) the pictorial stage is a thinking tool, not just an illustration, (c) the bridging between stages is explicit — the teacher names the connection, (d) all three stages represent the SAME mathematical relationship in different modes, and (e) the sequence allows students to move back to earlier stages when needed.
```

## 示例输出

**场景：** *Mathematical concept: "Adding fractions with different denominators — for example, ½ + ⅓" / Student level: "Year 5, comfortable adding fractions with the same denominator (⅓ + ⅓ = ⅔), but confused when denominators are different — many students add numerators and denominators separately (½ + ⅓ = ⅖)" / Common errors: "Adding numerators and denominators: ½ + ⅓ = 2/5. Not understanding why you need a common denominator. Finding a common denominator procedurally but not understanding what it means." / Available manipulatives: "Fraction strips, fraction circles, Cuisenaire rods"*

---

## CPA 序列：异分母分数相加

**概念：** 通过寻找公分母的等值分数实现异分母分数相加
**学生：** 五年级，能进行同分母分数相加，对异分母分数感到困惑
**数学结构：** 分数相加时，各部分必须是“相同大小”（相同分母）。如果各部分大小不同，在合并之前必须将它们细分成分量大小相等的部分。这就是通分（寻找公分母）的真正含义——让各部分变得一样大，从而可以放在一起计数。

### 第 1 阶段——具象（动作表征）

**教具：** 分数条——等长的纸条，分别均分为二分之一、三分之一、四分之一、六分之一、十二分之一。

**活动：**
1. 发给每位学生一条“½”纸条和一条“⅓”纸条。提问："How much pizza do you have altogether if you eat half of one pizza and a third of another?" 学生将 ½ 纸条和 ⅓ 纸条首尾相接。他们能看到总长度，但无法“命名”它，因为两块的大小不同。

2. 提问："Can you tell me EXACTLY how much that is? Not 'a bit more than a half' — an exact fraction?" 学生会犯难。这就是关键时刻：你“不能”直接数块数，因为它们“大小不同”。½ 和 ⅓ 不一样大。你不能说“1 + 1 = 2 块”，因为两块的大小不一样。

3. 现在发给学生六分之一纸条。提问："Can you find pieces from the sixths strip that are exactly the same length as your half? How many sixths make a half?" 学生亲手把六分之一纸条叠放在 ½ 纸条上：3 个六分之一 = 1 个二分之一。接着问："How many sixths make a third?" 2 个六分之一 = 1 个三分之一。

4. 用 3/6 替换 ½ 纸条，用 2/6 替换 ⅓ 纸条。现在每一块都“一样大”了。提问："Now can you tell me the total?" 3 个六分之一 + 2 个六分之一 = 5 个六分之一。各部分大小相同，因此可以合起来计数。

**这建构了什么：** 让学生亲身体验“为什么”需要公分母——大小不同的部分无法直接合并。学生在学习解法（找匹配的等值小块）之前，先切身感受到了问题（小块对不上）。

**核心教师语言：** "The pieces are different sizes. We can't count them together until they're the same size. We need to find smaller pieces that match both." 反复使用 "same size"（相同大小）——这正是“公分母”的本质含义。

### 架桥：具象 → 表象

当学生面前还摆着实物分数条时，教师直接在黑板上画出这些分数条：

"Look at your fraction strips. I'm going to draw exactly what you have." 画一条均分为 2 份的长条（涂阴影 1 份）。"This is your half." 画一条均分为 3 份的长条（涂阴影 1 份）。"This is your third." 画一条均分为 6 份的长条（涂阴影 3 份）。"This is your 3 sixths — the same as your half." 画一条均分为 6 份的长条（涂阴影 2 份）。"This is your 2 sixths — the same as your third."

"Can you see that my drawing shows the same thing as your strips? Put your strips next to my drawing and check."

### 第 2 阶段——表象（图像表征）

**表征工具：** 条形图模型（Bar models）——等长的矩形长条，按需分割为若干等份。

**活动：**
1. 学生自己动手画条形图模型（而不仅仅是看教师画）。题目："What is ½ + ¼?" 学生画出：
   - 一条均分为 2 份的条，涂 1 份（½）
   - 一条均分为 4 份的条，涂 1 份（¼）
   - 提问："Can you see a way to make the pieces the same size?" 学生发现每个二分之一可以再分成 2 个四分之一。重画：一条均分为 4 份的条，涂 2 份（2/4 = ½）。现在：2/4 + 1/4 = 3/4。

2. 用 ⅓ + ¼ 重复练习：
   - 画一条均分 3 份涂 1 份；画一条均分 4 份涂 1 份。
   - "What size pieces would work for both thirds AND quarters?" 学生在图上尝试细分：十二分之一可行。重画两条均分 12 份的条：4/12 + 3/12 = 7/12。

3. 在掌握正式计算方法之前，学生开始能从条形图模型中“预测”公分母："I need a number that both 3 and 4 divide into evenly."

**这建构了什么：** 条形图模型无需实物即可让数学结构清晰可见。学生能“看见”为什么 ⅓ = 4/12（图形直接展示了它），并能把画图当作解题工具——不断尝试不同的细分方式，直到找到同时适用于两个分数的份数。

**核心教师语言：** "Your bar model shows the same thing as the fraction strips. The bars must be the SAME LENGTH — because we're talking about parts of the same whole. What size pieces would match both fractions?"

### 架桥：表象 → 抽象

在学生用条形图模型解决几道题后，教师在图旁写出符号算式：

"Let's write what you just drew in maths notation. You drew ⅓ as 4/12 — we write: ⅓ = 4/12. You drew ¼ as 3/12 — we write: ¼ = 3/12. Then you added: 4/12 + 3/12 = 7/12. The numbers say EXACTLY what your bar model shows."

同时指向算式的每一部分与条形图模型的对应部分："This 4 [指向分子] is these 4 shaded sections [指向长条]. This 12 [指向分母] is these 12 equal sections the bar is divided into [指向长条]."

### 第 3 阶段——抽象（符号表征）

**符号表达：** ⅓ + ¼ = 4/12 + 3/12 = 7/12

**活动：**
1. 学生仅用数字练习通分与分数相加：⅕ + ⅓, ⅔ + ¼, ¾ + ⅙。
2. 每道题都要写出等值分数、相加，并在需要时约分。
3. 学生通过画一个快速的条形图模型来检验前几道题的答案："Does 7/12 LOOK right? Draw the bar and check."

**这建构了什么：** 流畅、灵活地使用标准运算程序——但“植根于理解之中”。当学生写下 ⅓ = 4/12 时，他们知道这“意味着”什么（长条被分为 12 份，其中 4 份涂色）。运算步骤不再是任意死记的规则，而是具象与表象经验的浓缩表达。

**回溯连接：** 如果学生在抽象层面卡住（"I don't know what common denominator to use for ⅗ + ¼"），教师引导："Draw a bar model. What size pieces would work for both fifths and quarters?" 表象阶段始终作为思维工具保留在手边，而非被抛弃。

### 常见错误与 CPA 应对

| 错误 | 学生做法 | CPA 应对 |
|---|---|---|
| 分子分母分别相加 | ½ + ⅓ = 2/5 | 回到具象阶段："Show me 2/5 with a fraction strip. Now show me ½ + ⅓ end-to-end. Are they the same length?" 它们并不等长——2/5 甚至比 ½ 还要短。物理证据直接证伪了错误。 |
| 会通分但不理解为什么 | 能正确写出 ⅓ = 4/12 但无法解释 | 回到表象阶段："Draw a bar divided into 3. Now divide each third into 4 pieces. How many pieces do you have? How many are shaded?" 条形图模型直观展示了为什么 ⅓ = 4/12。 |
| 忘记约分 | 算出 4/12 + 2/12 = 6/12 但不约分为 ½ | 回到表象阶段："Draw 6/12. Now look — can you see a simpler way to describe this? How many halves is it?" 条形图模型显示 12 份中的 6 份正好是整条的一半。 |

### 评估检查

给学生三项任务，检验他们在全部三个 CPA 层面上的理解：

1. **具象/表象检查：** "Draw a bar model to show ⅔ + ¼. Use your diagram to find the answer."（检验学生能否独立使用表象工具。）

2. **抽象检查：** "Calculate ⅗ + ¼. Show your working."（检验学生能否使用标准符号程序。）

3. **概念理解检查：** "Ali says ½ + ⅓ = 2/5. Explain why Ali is wrong. You can use a diagram to help your explanation."（检验学生是否理解“为什么”通分有效——能否解释错误，而不仅仅是避开错误？）

如果学生能答对全部三题，他们就在全部三个 CPA 层面上真正理解了分数加法——不仅是程序上的熟练，更是概念上的通透。

---

## 已知局限性

1. **CPA 在数学教育中得到的研究验证最为充分。** 新加坡框架正是为数学教育而设计的，其证据基础在数学领域最为坚实。“先具象后抽象、明确架桥不同表征”的原则跨学科通用，但具体工具——条形图模型、分数条、十进制积木——属于数学领域。教师将 CPA 应用于其他学科时应迁移其原则，而非机械照搬工具。

2. **具象阶段需要高质量教具与教师专业技能。** 设计不当的教具（例如用散装计数片来教分数）非但不能预防误区，反而会制造误区。教具必须体现数学结构。教师需要接受培训，了解哪种教具表征哪种概念——使用错误的具象材料比不用具象材料更糟。

3. **CPA 并不意味着每节课都必须从具象阶段重新开始。** 一旦学生对某个概念建立了稳固的具象与表象理解，他们就可以直接在抽象层面工作，而不必每次都走完三个阶段。CPA 是学习“新概念”的递进路径，而不是每节课的固定仪式。当学生遇到新应用或产生困惑时再回溯早期阶段，而在学生已熟练掌握时无需重复。
