---
# AGENT SKILLS STANDARD FIELDS (v2)
name: worked-example-fading-designer
description: "设计从完整样例逐步过渡到独立练习的样例渐隐序列。适用于向新手学习者教授操作步骤、算法或多步骤过程。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "memory-learning-science/worked-example-fading-designer"
skill_name: "带补全渐隐的样例设计器"
domain: "memory-learning-science"
version: "1.0"
evidence_strength: "strong"
evidence_sources:
  - "Sweller & Cooper (1985) — The use of worked examples as a substitute for problem solving in learning algebra"
  - "Atkinson et al. (2000) — Learning from examples: instructional principles from the worked examples research"
  - "Renkl (2014) — Toward an instructionally oriented theory of example-based learning"
  - "Kalyuga et al. (2003) — The expertise reversal effect (when worked examples become counterproductive)"
  - "van Merriënboer & Kirschner (2018) — Ten Steps to Complex Learning: fading and scaffolding principles"
input_schema:
  required:
    - field: "skill_to_teach"
      type: "string"
      description: "学生需要学习的具体程序或技能"
    - field: "student_level"
      type: "string"
      description: "年龄/年级与熟练水平（新手/发展中/高阶）"
    - field: "steps_in_procedure"
      type: "integer"
      description: "完整程序的大致步骤数"
  optional:
    - field: "common_errors"
      type: "array"
      description: "学生在该程序上通常犯的已知错误"
    - field: "student_profiles"
      type: "array"
      description: "来自上下文引擎：学生个体准备度数据"
    - field: "prior_knowledge"
      type: "string"
      description: "该技能所依托的学生已有知识"
output_schema:
  type: "object"
  fields:
    - field: "worked_example"
      type: "object"
      description: "带有步骤注释和自我解释提示的完整样例"
    - field: "completion_problems"
      type: "array"
      description: "包含3–4道逐步渐隐的补全问题序列"
    - field: "independent_problems"
      type: "array"
      description: "2–3道完全独立的练习题"
    - field: "fading_rationale"
      type: "string"
      description: "说明每一阶段渐隐的内容及原因"
chains_well_with:
  - "cognitive-load-analyser"
  - "explicit-instruction-sequence-builder"
  - "practice-problem-sequence-designer"
  - "checking-for-understanding-protocol-designer"
teacher_time: "4 分钟"
tags: ["worked-examples", "scaffolding", "fading", "cognitive-load", "novice-learning"]
---

# 带补全渐隐的样例设计器

## 本技能的功能

设计一套完整的支架序列，引导学生从研习完整样例出发，经过逐步撤除步骤的补全问题，最终过渡到独立练习。针对给定程序或技能，生成：（1）每一步均带有推理解释注释的完整样例；（2）依次移除步骤的系列补全问题；（3）独立练习题。AI 在此处具有独特价值，因为有效的样例需要对推理过程进行专家级注释（不仅展示步骤，还要解释**为什么**采取这一步），且渐隐序列需要审慎校准移除哪些步骤以及移除顺序——这需要同时深谙学科内容与认知负荷研究。

## 循证基础

Sweller 与 Cooper（1985）证明，研习样例的新手学习者比直接尝试解题的学习者学得更有效，因为样例降低了外在认知负荷——学生可以专注于理解程序，而不必盲目搜寻解题路径。Atkinson 等人（2000）综合了样例研究并确立了关键设计原则：样例必须包含解释性注释（而不仅仅是步骤），且从样例向独立练习的过渡应当是渐进的。Renkl（2014）完善了该理论，表明嵌入样例中的自我解释提示通过促进相关加工（germane processing）显著提升学习效果。van Merriënboer 与 Kirschner（2018）表明，渐隐法（fading）——即样例逐步省略步骤形成“补全问题”——比从样例骤然跳到独立解题更为有效。尤为关键的是，Kalyuga 等人（2003）揭示了专业逆转效应：帮助新手的样例对于高阶学习者反而会适得其反，后者从直接解题中学得更好。这意味着渐隐速率必须根据学生熟练度进行校准。

## 输入模式

教师必须提供：
- **待教技能：** 具体的程序或技能。*例如：“用消元法解二元一次方程组” / “撰写分析性段落的主题句” / “配平化学方程式”*
- **学生水平：** 年级与熟练度。*例如：“九年级，首次接触（新手）” / “十一年级复习（发展中）”*
- **程序步骤数：** 大致步骤数。*例如：5*

可选（如有，由上下文引擎注入）：
- **常见错误：** 学生通常犯的已知错误。*例如：["忘记方程两边同乘", "两式相减时符号出错"]*
- **学生档案：** 用于差异化渐隐速率的个体准备度数据
- **先验知识：** 学生已具备的前置知识

## 提示词

```
You are an expert in instructional design specialising in worked examples and cognitive load management. You have deep knowledge of Sweller & Cooper (1985) on the worked example effect, Renkl (2014) on self-explanation in worked examples, Atkinson et al. (2000) on design principles for example-based learning, and the fading approach from van Merriënboer & Kirschner (2018).

Your task is to design a complete worked example with completion fading for:

**Skill:** {{skill_to_teach}}
**Student level:** {{student_level}}
**Steps in procedure:** approximately {{steps_in_procedure}} steps

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Known common errors:** {{common_errors}} — if provided, build awareness of these specific errors into the worked example annotations. If not provided, include the most common errors for this procedure based on your subject knowledge.
**Prior knowledge:** {{prior_knowledge}} — if provided, connect new steps to this existing knowledge explicitly. If not provided, assume standard prerequisite knowledge for the stated year group.
**Student profiles:** {{student_profiles}} — if provided, consider differentiated fading rates for different readiness levels. If not provided, design a single fading sequence for a typical mixed-ability class.

Apply these evidence-based design principles:

1. **Complete worked example first (Sweller & Cooper, 1985):** The first example must show EVERY step, fully worked, with no gaps. The student's only task is to study and understand — not to solve anything.

2. **Annotate reasoning, not just steps (Renkl, 2014):** Each step must include a brief annotation explaining WHY this step is taken, not just WHAT is done. The annotation reveals expert thinking. Format: "Step → Reasoning annotation."

3. **Self-explanation prompts (Renkl, 2014):** After the worked example, include 2–3 self-explanation questions that prompt students to explain the reasoning behind key steps. These promote active processing rather than passive reading.

4. **Fading sequence (van Merriënboer & Kirschner, 2018):** Create 3–4 completion problems that progressively remove steps:
   - Completion 1: Remove the final step only. Student completes it.
   - Completion 2: Remove the final 2 steps.
   - Completion 3: Remove middle and final steps (student must do ~50% of the procedure).
   - Completion 4 (if needed): Only the first step is provided.
   Fade from the END of the procedure backward — the final steps are typically the most routine and least conceptually demanding.

5. **Error awareness (where applicable):** If common errors are provided, include a "common error" annotation at the step where the error typically occurs, showing what the error looks like and why it's wrong.

6. **Expertise reversal guard:** Note at what point the fading should accelerate for students who are demonstrating mastery, and when to move directly to independent practice.

Return your output in this exact format:

## Worked Example Sequence: [Skill Name]

**For:** [Student level]
**Fading strategy:** [Brief description of what is faded and why]

### Stage 1: Complete Worked Example

**Problem:** [A specific, realistic problem]

| Step | Action | Reasoning |
|------|--------|-----------|
| 1 | [What is done] | [Why this step — expert thinking made visible] |
| 2 | ... | ... |
| ... | ... | ... |

**Answer:** [Final answer]

**Self-explanation prompts:**
1. [Question prompting student to explain a key reasoning step]
2. [Question prompting comparison or connection]

### Stage 2: Completion Problems (Fading Sequence)

**Completion Problem 1:** [Final step removed]
**Completion Problem 2:** [More steps removed]
**Completion Problem 3:** [~50% removed]

For each, show the provided steps and clearly mark where the student takes over.

### Stage 3: Independent Practice

2–3 problems with no support. Different surface features from the worked example to promote transfer.

### Fading Rationale

[3–4 sentences explaining what is faded at each stage and why, connected to CLT principles]

### Expertise Reversal Note

[When to skip or accelerate stages for advanced learners]

**Self-check before returning output:** Verify that (a) every step in the worked example includes reasoning, not just procedure, (b) fading moves from end to beginning, (c) self-explanation prompts target reasoning not recall, (d) completion problems change surface features to prevent pattern matching, and (e) independent practice problems require the same procedure but look different from the worked example.
```

## 示例输出

**场景：** *待教技能：“根据频数分布表计算平均数” / 学生水平：“八年级数学，首次接触（新手）” / 步骤数：5 / 常见错误：["将频数相加而不是用数值乘以频数", "除以行数而不是总频数"]*

---

## 样例序列：根据频数分布表计算平均数

**适用对象：** 八年级数学，新手
**渐隐策略：** 从程序末尾向开头逐步移除步骤，因为一旦理解了概念设置，末尾步骤（除法与解释）在程序上是最直接的。中间步骤（fx 列、总计）最后才渐隐，因为它们包含概念要求最高的要素。

### 第一阶段：完整样例

**题目：** 老师记录了每位学生本学期阅读的书籍数量。计算阅读书籍的平均数。

| 阅读书目 (x) | 频数 (f) |
|:-:|:-:|
| 0 | 3 |
| 1 | 7 |
| 2 | 12 |
| 3 | 5 |
| 4 | 3 |

| 步骤 | 操作 | 推理依据 |
|------|--------|-----------|
| 1 | 在表中增加一列 fx。将每个数值乘以其频数：0x3=0, 1x7=7, 2x12=24, 3x5=15, 4x3=12 | 我们需要求出**所有**数值的总和，而不仅仅是表格里列出的数字。“2本书”出现了12次，因此它对总数的贡献是 2x12=24 本书，而不仅仅是“2”。这里最容易出错——把 0+1+2+3+4 相加只有在每个数值只出现一次时才对。 |
| 2 | 求 fx 列的总和：0+7+24+15+12 = 58 | 这给出了**所有**学生阅读书籍的总数。这就是平均数公式中的“所有数值之和”。 |
| 3 | 求总频数：3+7+12+5+3 = 30 | 这是学生总人数。我们除以**这个数**，而不是除以表格的行数（5）。常见错误：因为有5行就除以5——但这里有30名学生，不是5名。 |
| 4 | 计算平均数：fx 总和 / f 总和 = 58 / 30 = 1.93（保留2位小数） | 平均数 = 所有数值之和 / 数值个数。我们使用表格的总计是因为我们没必要把每个单独的数值相加（否则得把“2”写十二遍）。频数表是一种快捷方式。 |
| 5 | 解释：每名学生平均阅读书籍数为 1.93 本，即约 2 本。 | 务必结合情境说明平均数代表什么。光写“1.93”没有意义——“每名学生 1.93 本书”把计算与真实情境联系了起来。 |

**答案：** 平均数 = 每名学生 1.93 本书

**常见错误警示：**
- 在第1步：把 x 列相加（0+1+2+3+4 = 10）而非用 x 乘以 f 的学生，是把表格当成了每个数值只出现一次。提问：“难道只有一名学生读了2本书吗？”
- 在第3步：除以5（行数）而非30（总频数）的学生混淆了类别数与数据点总数。提问：“一共有多少名学生——5名还是30名？”

**自我解释提示：**
1. 为什么在第1步中我们要用每个数值乘以它的频数，而不是只把第一列的数值相加？如果我们只算 0+1+2+3+4 会出什么错？
2. 在第3步中，我们除以30，而不是5。用你自己的话解释为什么除以5会得出错误答案。这两个数字分别代表什么？

### 第二阶段：补全问题（渐隐序列）

**补全问题 1** *（移除第5步——由学生解释）*

一家商店记录了一天内售出的鞋码：

| 鞋码 (x) | 频数 (f) | fx |
|:-:|:-:|:-:|
| 5 | 4 | 20 |
| 6 | 8 | 48 |
| 7 | 11 | 77 |
| 8 | 6 | 48 |
| 9 | 1 | 9 |
| **总计** | **30** | **202** |

平均数 = 202 / 30 = 6.73

**轮到你了：** 写一句话结合情境解释这个平均数。6.73 代表什么？

---

**补全问题 2** *（移除第4–5步——由学生计算并解释）*

调查询问了学生有多少个兄弟姐妹：

| 兄弟姐妹数 (x) | 频数 (f) | fx |
|:-:|:-:|:-:|
| 0 | 5 | 0 |
| 1 | 9 | 9 |
| 2 | 8 | 16 |
| 3 | 6 | 18 |
| 4 | 2 | 8 |
| **总计** | **30** | **51** |

**轮到你了：** 计算平均数并写一句话解释其含义。

---

**补全问题 3** *（移除第2–5步——由学生计算总计、平均数并解释）*

体育老师记录了学生跑完的圈数：

| 圈数 (x) | 频数 (f) | fx |
|:-:|:-:|:-:|
| 3 | 2 | 6 |
| 4 | 7 | 28 |
| 5 | 10 | 50 |
| 6 | 8 | _____ |
| 7 | 3 | _____ |
| **总计** | **_____** | **_____** |

**轮到你了：** 补全剩余行的 fx 列，求出两个总计，计算平均数并解释你的答案。

---

**补全问题 4** *（仅提供表格——由学生完成全部步骤）*

一项调查询问了学生昨晚做作业的时间（小时）：

| 小时数 (x) | 频数 (f) |
|:-:|:-:|
| 0 | 6 |
| 1 | 11 |
| 2 | 9 |
| 3 | 4 |

**轮到你了：** 添加 fx 列，计算所有数值，求出平均数并解释你的答案。

### 第三阶段：独立练习

**问题 1：** 掷骰子40次，结果记录如下。计算每次投掷的平均点数。

| 点数 | 1 | 2 | 3 | 4 | 5 | 6 |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| 频数 | 5 | 8 | 7 | 9 | 6 | 5 |

*（不同形式：横向表格，不同情境，相同程序）*

**问题 2：** 在一项调查中，25个家庭报告了饲养宠物的数量：0只宠物（8户），1只宠物（9户），2只宠物（5户），3只宠物（2户），4只宠物（1户）。计算每户平均饲养宠物数量。

*（不同形式：数据以文本而非表格给出——学生必须先构建频数表）*

**问题 3：** 一个20人班级的测验平均分为 14.5 分。下面的频数表不完整。求缺失的频数。

| 分数 (x) | 频数 (f) |
|:-:|:-:|
| 12 | 4 |
| 13 | ? |
| 14 | 6 |
| 15 | 3 |
| 16 | 2 |
| 17 | 1 |

*（逆向问题：已知平均数，求缺失值——将同一程序向新方向延伸）*

### 渐隐学理依据

该渐隐序列从程序末尾向开头逐步移除步骤，因为最后几步（除法与解释）在程序上更简单，可以在不使工作记忆超载的情况下最先交由学生完成。中间步骤（构建 fx 列与求总计）概念要求最高——核心洞察（每个数值按频数次数计入总和）正存在于此——因此这些步骤保留支持的时间最长。到补全问题 4 时，仅提供原始表格，由学生执行全部程序。随后独立练习变换了表层特征（横向表格、纯文本数据、逆向问题），以促进超越样例特定格式的迁移。

### 专业逆转效应提示

如果学生能够准确且自信地完成补全问题 2，直接跳至补全问题 4 或独立练习。强迫高阶学生走完每一个渐隐阶段会浪费时间并产生冗余负荷（Kalyuga et al., 2003）。对于正在复习此主题的十一年级学生，完全跳过样例——直接从独立练习开始，仅当错误表明程序尚未掌握稳固时才提供样例。

---

## 已知局限

1. **样例对于步骤清晰的程序性技能最为有效。** 对于主要属于概念性、创意性或需要判断力的任务（如撰写论文、设计实验），分步样例格式的适用性较低。本技能仍能产出有用的范例，但渐隐序列向开放式任务的迁移可能没那么顺畅。

2. **渐隐序列假设学生准备度相对均质。** 在混合能力班级中，部分学生需要更多渐隐阶段，部分需要更少。教师应将补全问题 2 作为检查点——如果学生准确无误，加快推进；如果遇到困难，在继续渐隐前再提供一个不同数字的样例。

3. **独立练习中的表层特征变化至关重要但难以完全预判。** 如果所有练习题看起来都与样例过于相似，学生可能形成僵化知识，只对长得像样例的题有效。本技能尝试变换表层特征，但教师应结合评估中出现的题型进一步补充变式。
