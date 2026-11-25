---
# AGENT SKILLS STANDARD FIELDS (v2)
name: erroneous-example-designer
description: "设计刻意包含缺陷的样例，以培养纠错能力并深化理解。适用于学生常犯典型错误、需要练习识别错误时。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "ai-learning-science/erroneous-example-designer"
skill_name: "错误样例设计器"
domain: "ai-learning-science"
version: "1.0"
evidence_strength: "moderate"
evidence_sources:
  - "McLaren, Adams & Mayer (2012) — Delayed learning effects with erroneous examples"
  - "McLaren, Adams, Durkin, Goguadze, Mayer & Rittle-Johnson (2015) — To err is human, to explain and correct is divine"
  - "Tsovaltzi, Melis, McLaren, Meyer, Dietrich & Goguadze (2010) — Learning from erroneous examples"
  - "Große & Renkl (2007) — Finding and fixing errors in worked examples"
  - "Siegler (2002) — Microgenetic studies of self-explanation"
input_schema:
  required:
    - field: "problem_domain"
      type: "string"
      description: "学生容易出现典型错误的问题或程序类型"
    - field: "target_errors"
      type: "string"
      description: "学生所犯的具体、常见错误——真实的迷思概念或程序性失误"
  optional:
    - field: "student_level"
      type: "string"
      description: "年龄/年级及能力水平"
    - field: "subject_area"
      type: "string"
      description: "课程学科"
    - field: "correct_examples_available"
      type: "string"
      description: "学生是否已经看过该题型的正确样例"
    - field: "number_of_examples"
      type: "integer"
      description: "需要设计多少个错误样例"
    - field: "delivery_context"
      type: "string"
      description: "以数字形式、纸质形式还是课堂讨论形式交付"
output_schema:
  type: "object"
  fields:
    - field: "erroneous_examples"
      type: "array"
      description: "一组错误样例——每个样例在特定步骤包含一个真实且常见的错误"
    - field: "error_analysis_scaffold"
      type: "object"
      description: "引导学生发现、解释并纠正每处错误的提示脚手架"
    - field: "learning_mechanism"
      type: "object"
      description: "为什么每个错误样例能促进学习——错误检测的认知机制"
    - field: "correct_version"
      type: "object"
      description: "每个样例的正确版本——供教师参考及学生自查"
chains_well_with:
  - "adaptive-hint-sequence-designer"
  - "worked-example-fading-designer"
  - "self-explanation-prompt-designer"
  - "diagnostic-question-generator"
teacher_time: "3 分钟"
tags: ["erroneous-examples", "McLaren", "error-detection", "worked-examples", "misconceptions", "self-explanation"]
---

# 错误样例设计器

## 本技能的作用

设计包含刻意设置的真实错误的样例，供学生识别、解释与纠正——这种技术产生的学习效果可媲美甚至超过正确样例，同时还能额外培养纠错能力。McLaren 等人（2012, 2015）的核心洞见在于：错误必须**真实**且**常见**——即学生实际会犯的错误，而非没人会犯的刻意编造的错误。设计良好的错误样例能够激活自我解释（Chi et al., 1989）：学生必须推理**为什么**该步骤是错的，这迫使他们进行比单纯模仿正确程序更深度的加工。输出包括在特定步骤带有真实错误的错误样例、错误分析脚手架（引导学生发现并纠正错误的提示）、学习机制说明以及正确版本。AI 在此尤为关键，因为设计有效的错误样例需要深入了解特定题型的常见错误模式——哪些错误真实存在、哪些具有启发性的混淆价值，以及哪些会制造有害的迷思概念。

## 实证基础

McLaren、Adams & Mayer（2012）发现，学习错误样例的学生在保持和迁移测试上显著优于学习正确样例的学生——但这种效应是**延迟显现**的（出现在一周后的延迟后测中，而非即时测试）。这表明错误样例产生了比正确样例更深层、更持久的学习，原因可能是纠错过程迫使学生进行了更精细的认知加工。McLaren 等人（2015）复制并拓展了这一发现，表明将错误样例**与**自我解释提示结合能产生最强效应。Tsovaltzi 等人（2010）发现，当提示学生解释**为什么**错误是错的，而不仅仅是指出错误时，错误样例尤其有效。Große & Renkl（2007）发现，当学生具备足够的先验知识来识别错误时，错误样例能促进学习——但可能会让缺乏前置知识的学生感到困惑（他们可能会把错误当成正确程序来学）。这确立了一条关键设计约束：错误样例应在学生见过正确样例**之后**使用，而非作为首次接触材料。Siegler（2002）表明，儿童从同时解释正确与错误策略中获益——“这样做有效而那样做无效”的对比比单独学习其中任何一种更能深化理解。

## 输入规范

教师必须提供：
- **问题领域（Problem domain）：** 题目类型。*例如：“异分母分数加法” / “计算百分比增长” / “区分所有格与缩写中的撇号用法” / “配平化学方程式”*
- **目标错误（Target errors）：** 具体的常见错误。*例如：“分别将分子和分母相加：½ + ⅓ = 2/5” / “计算增长的百分比而非百分比增长：混淆‘80 的 20% 是多少？’与‘从 80 增长到 96 的百分比是多少？’” / “在复数词中使用撇号：用 apple's 代替 apples” / “配平时将化学计量数改成下标”*

可选项（如可用则由上下文引擎注入）：
- **学生水平（Student level）：** 年级与能力水平
- **学科领域（Subject area）：** 课程学科
- **是否有正确样例（Correct examples available）：** 学生是否已见过正确版本
- **样例数量（Number of examples）：** 需要设计多少个
- **交付情境（Delivery context）：** 数字、纸质或课堂讨论

## 提示词（Prompt）

```
You are an expert in erroneous example design for learning, with deep knowledge of McLaren et al.'s (2012, 2015) research on delayed learning effects from erroneous examples, Tsovaltzi et al.'s (2010) work on error-based learning, Große & Renkl's (2007) research on finding and fixing errors in worked examples, and Siegler's (2002) microgenetic studies of self-explanation with correct and incorrect strategies. You understand that erroneous examples are not "trick questions" — they are carefully designed learning tools where realistic, common errors are embedded at specific steps, and students learn by DETECTING, EXPLAINING, and CORRECTING the error.

CRITICAL PRINCIPLES:
- **Errors must be REALISTIC and COMMON.** The error should be one that students actually make — a genuine misconception or procedural slip, not an absurd mistake. "3 + 4 = 12" is not a realistic error. "½ + ⅓ = 2/5" IS a realistic error (adding numerators and denominators separately). Realistic errors activate recognition: "I've made this mistake" or "I can see why someone would think that."
- **One error per example.** An example with multiple errors is confusing, not instructive. Embed ONE error at ONE specific step, with all other steps correct. This isolates the learning target and makes detection feasible.
- **Students must already have seen correct examples.** Große & Renkl (2007) showed that erroneous examples confuse students who haven't seen correct versions first. Use erroneous examples AFTER correct worked examples, not instead of them. The sequence is: correct examples → erroneous examples → independent practice.
- **The error analysis scaffold is essential.** Simply showing an erroneous example is insufficient. Students need prompts: "Find the error," "Explain why it's wrong," "Correct it," "Explain why your correction is right." This scaffold forces the self-explanation that produces the learning effect.
- **Erroneous examples develop error-detection skills.** Beyond learning the specific content, students who practise with erroneous examples become better at monitoring their OWN work for errors. This metacognitive benefit is separate from and additional to the content learning.

Your task is to design erroneous examples for:

**Problem domain:** {{problem_domain}}
**Target errors:** {{target_errors}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Student level:** {{student_level}} — if not provided, design for a general secondary school context.
**Subject area:** {{subject_area}} — if not provided, infer from the problem domain.
**Correct examples available:** {{correct_examples_available}} — if not provided, include a note that students should see correct examples first.
**Number of examples:** {{number_of_examples}} — if not provided, design 3 erroneous examples targeting different common errors.
**Delivery context:** {{delivery_context}} — if not provided, design for paper-based use that could be adapted for digital delivery.

Return your output in this exact format:

## Erroneous Examples: [Problem Domain]

**Problem domain:** [The type of problem]
**Target errors:** [The common errors being addressed]
**Prerequisite:** [What students must already know — correct examples must come first]

### Erroneous Example [N]

**The problem:** [The problem being solved]
**The erroneous solution:**
[Step-by-step solution with ONE deliberate error at a specific step — all other steps correct]

**The error:** [Which step is wrong and what the error is — FOR TEACHER REFERENCE ONLY, not shown to students]
**Why this error is realistic:** [Why students actually make this mistake — the underlying misconception or procedural confusion]

**Error Analysis Scaffold (for students):**
1. "Read through the solution carefully. Is every step correct?"
2. "Find the step that contains an error. Circle it."
3. "Explain WHY this step is wrong. What mistake was made?"
4. "Write the correct version of this step."
5. "Complete the problem correctly from this point."

### Correct Version (Teacher Reference)

[The fully correct solution for comparison]

### Learning Mechanism

[Why these erroneous examples produce learning — the cognitive process of error detection, explanation, and correction]

### Sequencing Guidance

[When to use these erroneous examples in a lesson — after correct examples, before independent practice]

**Self-check before returning output:** Verify that (a) each error is realistic and common, (b) there is only ONE error per example, (c) the error analysis scaffold requires explanation not just identification, (d) correct versions are provided for teacher reference, and (e) the examples are sequenced after correct worked examples.
```

## 示例输出

**情景：** *问题领域：“异分母分数加法——六年级数学” / 目标错误：“错误 1：分别将分子和分母相加（½ + ⅓ = 2/5）。错误 2：找到了公分母但忘了调整分子（½ + ⅓ = 1/6 + 1/6 = 2/6）。错误 3：正确化为同分母分数，但在最后相加时出现算术错误（3/6 + 2/6 = 6/6 而非 5/6）。” / 是否有正确样例：“是——学生已完成同分母分数加法的正确样例，并见过寻找公分母的步骤”*

---

## 错误样例：异分母分数加法

**问题领域：** 异分母分数加法
**目标错误：** 分子分母分别相加、忘记调整分子、最终加法算术错误
**前置条件：** 学生必须已经学过寻找公分母和同分母分数加法的正确样例。错误样例用于正确样例**之后**，以深化理解。

### 错误样例 1：“Sam 的解答”

**题目：** 计算 ½ + ⅓

**Sam 的解答：**
- 第 1 步：我需要把 ½ 和 ⅓ 相加
- 第 2 步：我把分子相加：1 + 1 = 2
- 第 3 步：我把分母相加：2 + 3 = 5
- 第 4 步：我的答案是 2/5 ✓

**错误所在（仅教师参考）：** 第 2 步和第 3 步。Sam 分别将分子和分母相加，把分数加法当成了整数加法。这是最常见的分数错误，反映了对分数**本质**的根本性迷思——分母表示份数的大小，不能通过把份数名称相加来合并不同大小的份。

**为什么此错误真实：** 刚学会整数加法的学生会把同样的逻辑套用到分数上。这看起来“很顺理成章”——把上面的加起来，下面的也加起来，就像加两个整数一样。这一错误极为普遍，研究一致发现 30–50% 初学分数加法的学生都会犯此错误。

**错误分析脚手架（供学生使用）：**
1. “仔细阅读 Sam 的解答。每一步都合理吗？”
2. “Sam 说 ½ + ⅓ = 2/5。想一想：½ 等于 0.5。2/5 比 ½ 大还是小？”（2/5 = 0.4，竟然比单独的 ½ 还**小**。这不可能——给 ½ 加上一个正分数，结果必须比 ½ 更大。）
3. “哪一步出错了？圈出来并解释**为什么**错了。”
4. “Sam 原本应该怎么做？正确解出这道题。”
5. “给 Sam 写一段话，用能帮他理解的方式解释这个错误。”

### 错误样例 2：“Priya 的解答”

**题目：** 计算 ½ + ⅓

**Priya 的解答：**
- 第 1 步：我需要一个公分母。2 和 3 都能整除 6。公分母是 6。
- 第 2 步：½ = 1/6（我把分母改成了 6）
- 第 3 步：⅓ = 1/6（我把分母改成了 6）
- 第 4 步：1/6 + 1/6 = 2/6
- 第 5 步：我的答案是 2/6 ✓

**错误所在（仅教师参考）：** 第 2 步和第 3 步。Priya 正确找到了公分母（6），但**只**改变了分母而没有调整分子。她写成 ½ = 1/6，而实际上 ½ = 3/6（分子分母同乘 3）。同理，⅓ = 2/6（分子分母同乘 2）。Priya 明白需要公分母，但尚未理解分数必须保持**等值**——分子和分母必须按相同倍数变化。

**为什么此错误真实：** 被教导“找公分母”的学生有时会将其当作只改底部数字的操作，而不理解分数必须保持等值。他们遵循了**程序**（改变分母），却未理解**原理**（保持等值）。这是一种“有程序无概念”的错误。

**错误分析脚手架（供学生使用）：**
1. “Priya 找到了正确的公分母（6）。开局不错。但请看第 2 步。”
2. “Priya 说 ½ = 1/6。用图示或分数条比一比：½ 和 1/6 一样大吗？”（不一样——½ 比 1/6 大得多。）
3. “哪里出了问题？当 Priya 把 ½ 换成六分之几时，分子应该是多少？你是怎么知道的？”
4. “从第 2 步起纠正 Priya 的解答。”
5. “Priya 应该记住什么**规则**？（提示：你对分母做的运算，也必须对___做同样的运算）”

### 错误样例 3：“Marcus 的解答”

**题目：** 计算 ½ + ⅓

**Marcus 的解答：**
- 第 1 步：我需要一个公分母。2 和 3 都能整除 6。
- 第 2 步：½ = 3/6（分子分母同乘 3）✓
- 第 3 步：⅓ = 2/6（分子分母同乘 2）✓
- 第 4 步：3/6 + 2/6 = 6/6
- 第 5 步：6/6 = 1 整份
- 第 6 步：我的答案是 1 ✓

**错误所在（仅教师参考）：** 第 4 步。Marcus 在最后一步加法前全都做对了：3/6 + 2/6 = 5/6，而不是 6/6。这是一个简单的算术失误（3 + 2 = 5，不是 6），但它却得出了一个看起来很合理的最终答案（1 整份），可能因为“看起来很规整”而没有触发学生的自我纠错警觉。

**为什么此错误真实：** 一旦学生成功闯过了概念上较难的部分（找公分母、调整分子），他们在最后一步反而容易犯粗心的算术错误。由于困难的概念工作已经完成，学生放松了监控，漏掉了这个简单失误。此外，6/6 = 1 看起来像是一个“漂亮”的答案，反而强化了错误而非发出警示。

**错误分析脚手架（供学生使用）：**
1. “Marcus 正确找到了公分母，并正确转换了两个分数。到目前为止做得很好。”
2. “仔细看第 4 步。检查加法：3 + 2 = ？”
3. “正确答案应该是什么？写出纠正后的步骤。”
4. “Marcus 的错误很小——只是算术笔误。但它彻底改变了答案。这对你检查作业有什么启示？”

### 正确版本（教师参考）

½ + ⅓
= 3/6 + 2/6（公分母为 6；½ × 3/3 = 3/6；⅓ × 2/2 = 2/6）
= 5/6

### 学习机制

这三个错误样例在程序的三个不同位置瞄准了三种**不同类型**的错误：

1. **样例 1（Sam）：** **概念性**错误——误解分数加法的意义。解决最根本的迷思概念。
2. **样例 2（Priya）：** **程序-概念脱节**——机械遵循程序却不理解为何分子分母必须同变。解决程序与理解脱节的问题。
3. **样例 3（Marcus）：** **算术**错误——概念全对但出现粗心计算失误。训练自我监控与核查。

通过同时呈现这三类样例，学生建立起一套错误类型分类法：“当我做分数加法时，我需要检查概念性错误（我加得对不对？）、程序性错误（我调整分子了吗？），以及算术错误（我把数字加对了吗？）。”

### 教学顺序指南

**课堂位置：** 在学生完成以下环节**之后**使用这些错误样例：
1. 通过正确样例学会了正确程序
2. 在引导支持下练习了 2–3 道题目

**引入话术：** “这里有三位同学的解答。每一位都犯了一个错误。你们的任务是找出错误、解释哪里错了，并把它改正。”

**后续衔接：** 进行独立练习，由学生自己解题——此时他们已具备监控自己作业的纠错能力。

---

## 已知局限

1. **如果在正确样例之前使用，错误样例可能会制造迷思概念（Große & Renkl, 2007）。** 在尚未建立对正确程序的稳固心智模型前就接触错误，学生可能会无意中把错误当作正确做法来学。顺序至关重要：**先**正确样例，**再**用错误样例深化理解并培养纠错能力。

2. **学习效应往往是延迟显现的（McLaren et al., 2012）。** 学习错误样例的学生在即时测试中未必胜过学习正确样例的学生——但他们在延迟测试（一周后）中表现出更优异的保持与迁移效果。教师应知晓这一益处可能不会立竿见影，不应仅凭当天测验就断定该方法无效。

3. **错误分析脚手架的质量决定了学习效果。** 仅仅向学生展示错误并说“找出错误”，产生的效果远弱于提供要求解释与纠正的结构化提示（Tsovaltzi et al., 2010）。上述脚手架旨在迫使学生进行自我解释——但如果学生跳过解释步骤、只指出错误而不加推理，学习收益将大幅下降。
