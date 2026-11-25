---
# AGENT SKILLS STANDARD FIELDS (v2)
name: practice-problem-sequence-designer
description: "生成具有阶梯难度与策略性变式的支架化练习题序列。适用于编制练习纸、家庭作业题集或独立练习材料时。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "explicit-instruction/practice-problem-sequence-designer"
skill_name: "练习题序列设计师"
domain: "explicit-instruction"
version: "1.0"
evidence_strength: "strong"
evidence_sources:
  - "Rosenshine (2012) — Principles of Instruction, Principles 5 & 8: guide student practice, provide scaffolds"
  - "Rohrer (2009) — The effects of spacing and mixing practice problems"
  - "Sweller et al. (2019) — Cognitive load theory: variability and worked example effects"
  - "Atkinson et al. (2000) — Learning from examples: varied practice promotes transfer"
  - "Bjork & Bjork (2011) — Making things hard on yourself, but in a good way: desirable difficulties"
input_schema:
  required:
    - field: "skill_to_practise"
      type: "string"
      description: "学生正在练习的具体技能"
    - field: "student_level"
      type: "string"
      description: "年龄/年级及当前能力水平"
    - field: "problem_count"
      type: "integer"
      description: "要生成的练习题数量"
  optional:
    - field: "common_errors"
      type: "array"
      description: "需要围绕其设计题目的已知常见错误"
    - field: "prior_examples"
      type: "string"
      description: "学生已经看过的样例或范例"
    - field: "student_profiles"
      type: "array"
      description: "来自上下文引擎：能力范围、具体需求"
    - field: "assessment_format"
      type: "string"
      description: "学生将如何被评估——用于指导题型变化"
output_schema:
  type: "object"
  fields:
    - field: "problem_sequence"
      type: "array"
      description: "带有难度递进与设计意图的有序题目序列"
    - field: "scaffold_reduction_plan"
      type: "string"
      description: "支架如何随着序列推进而逐步减少"
    - field: "differentiation_options"
      type: "object"
      description: "支持与拓展调整方案"
    - field: "monitoring_guide"
      type: "string"
      description: "学生练习时应观察什么以及何时介入"
chains_well_with:
  - "explicit-instruction-sequence-builder"
  - "worked-example-fading-designer"
  - "interleaving-unit-planner"
  - "cognitive-load-analyser"
teacher_time: "4 分钟"
tags: ["practice", "problem-design", "scaffolding", "variability", "desirable-difficulty"]
---

# 练习题序列设计师

## 本技能的作用

设计一组遵循分布难度、渐进撤除支架以及表面特征变式原则的有序练习题——带领学生从近迁移（与所教例题高度相似的题目）走向远迁移（表面看起来不同但需要相同底层技能的题目）。输出包括题目本身、每道题的设计意图、支架撤除说明以及教师监控指南。AI 在此尤为有价值，因为高效的练习序列需要对难度、表面特征和支架水平进行刻意调控——大多数教师自编的练习题集要么顺序随机（缺乏递进），要么难度单一（缺乏变化），这两种情况都会削弱学习效果。

## 循证基础

Rosenshine (2012) 将引导练习和独立练习列为原则 5 与原则 8，强调练习必须搭建支架（从教师支持开始并逐步减少），且学生在撤除支架前应达到较高成功率（80% 以上）。Rohrer (2009) 证明，将不同题型混合练习（穿插练习 interleaving）以及跨时段分散练习（间隔练习 spacing）比集中块状练习能带来显著更好的记忆保持。Sweller 等 (2019) 确立了变式效应（variability effect）——使用多样化题型练习能促进图式抽象与迁移，而练习一模一样的题目则会导致僵化、绑定于特定情境的知识。Atkinson 等 (2000) 表明，表面特征变式（在保持底层结构不变的同时改变情境、数字或呈现形式）对迁移至关重要——只练习与所教例题外观相同题目的学生，在题目外观变化时就会失败。Bjork & Bjork (2011) 将此界定为“合意困难（desirable difficulty）”——让人感觉更费力的练习（因为题目在变化）比让人感觉轻松的练习（因为题目千篇一律）能产出更好的长期学习。

## 输入模式

教师必须提供：
- **Skill to practise（要练习的技能）：** 具体技能。*例如："Solving linear equations with the unknown on both sides" / "Writing a paragraph using the PEEL structure" / "Drawing and interpreting box plots"*
- **Student level（学生水平）：** 年级与当前水平。*例如："Year 9, have just seen two worked examples — novice with this specific skill"*
- **Problem count（题目数量）：** 需要多少道题。*例如：10*

可选（如上下文引擎可用则自动注入）：
- **Common errors（常见错误）：** 需要针对性设计的已知错误
- **Prior examples（先前例题）：** 已经展示过的样例或范例
- **Student profiles（学生档案）：** 能力范围、具体需求
- **Assessment format（评估形式）：** 学生将如何被评估

## Prompt

```
You are an expert in practice design and instructional sequencing, with deep knowledge of Rosenshine's (2012) practice principles, Rohrer's (2009) research on practice spacing and mixing, Sweller et al.'s (2019) variability effect, and Bjork & Bjork's (2011) concept of desirable difficulties. You understand that the sequence and structure of practice problems affects learning as much as the number of problems.

Your task is to design a practice problem sequence for:

**Skill:** {{skill_to_practise}}
**Student level:** {{student_level}}
**Number of problems:** {{problem_count}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Common errors:** {{common_errors}} — if not provided, identify the 2–3 most common errors for this skill and include problems specifically designed to surface them.
**Prior examples:** {{prior_examples}} — if not provided, assume students have seen a standard worked example and design the first 2 problems to closely match it.
**Student profiles:** {{student_profiles}} — if not provided, design for a mixed-ability class and include differentiation notes.
**Assessment format:** {{assessment_format}} — if not provided, include at least one problem in the format students are likely to encounter in assessments.

Apply these evidence-based principles:

1. **Near-to-far transfer progression (Atkinson et al., 2000):**
   - Problems 1–2: Nearly identical to the worked example (same structure, similar numbers, same context). Success rate should be 90%+. These build confidence and confirm basic understanding.
   - Problems 3–5: Same underlying skill, different surface features (different context, different numbers, different presentation). The student must recognise the same skill in a new wrapper.
   - Problems 6–8: Increased difficulty — additional steps, missing information to infer, or combining this skill with a previously learned skill.
   - Problems 9+: Far transfer — the problem looks substantially different from the worked example but requires the same underlying skill, possibly embedded in a larger problem or applied to a novel context.

2. **Surface feature variation (Sweller et al., 2019):**
   - Vary the context, numbers, format, and presentation while keeping the underlying structure constant.
   - If the worked example used a word problem about buying apples, practice problems should include different contexts (temperature, distance, money) — students who only practise apple problems can't solve temperature problems because they've learned "the apple procedure," not the underlying mathematics.

3. **Scaffold reduction (Rosenshine, 2012):**
   - Early problems may include partial scaffolds: a hint, a first step, or a reminder of the formula.
   - Middle problems remove these scaffolds.
   - Later problems require students to determine the method independently.

4. **Error-targeting problems:**
   - Include at least 2 problems specifically designed to surface common errors.
   - If students commonly confuse operation X with operation Y, include a problem where the wrong operation gives a plausible-looking answer — forcing students to think carefully about which approach is correct.

5. **One "twist" problem:**
   - Include at least one problem that looks like it requires this skill but actually doesn't — or that requires the student to explain why the skill doesn't apply. This tests whether students are thinking or just applying a procedure mechanically.

Return your output in this exact format:

## Practice Problem Sequence: [Skill]

**For:** [Student level]
**Total problems:** [Count]
**Scaffold reduction:** [Brief overview of how scaffolding reduces across the sequence]

### Problem Sequence

For each problem:
- **Problem [N]:** [The problem text]
- **Design intent:** [Why this problem is at this position — what it tests that previous problems didn't]
- **Difficulty level:** [Near transfer / Developing / Far transfer]
- **Common error to watch for:** [If applicable]

### Scaffold Reduction Plan

[How scaffolding decreases across the sequence — what support is provided early and removed later]

### Differentiation

**Support:** [How to modify for students who struggle — which problems to prioritise, what scaffolds to add back]
**Extension:** [How to challenge students who finish quickly — which problems to add]

### Monitoring Guide

[What the teacher should look for while students work: which problems are diagnostic, what errors signal which misunderstanding, when to intervene vs. let students struggle]

**Self-check before returning output:** Verify that (a) problems progress from near to far transfer, (b) surface features vary across the sequence, (c) at least 2 problems target common errors, (d) scaffolding decreases progressively, (e) one problem tests whether students can discriminate when the skill does/doesn't apply, and (f) the first 2 problems are accessible enough for 90%+ success rate.
```

## 示例输出

**场景：** *Skill: "Calculating percentage increase and decrease" / Student level: "Year 9, have just seen a worked example of 'find 15% of £240 and add it to the original'" / Problem count: 10 / Common errors: ["Finding the percentage but forgetting to add/subtract it", "Calculating percentage of the new amount instead of the original"]*

---

## 练习题序列：百分比增减计算

**适用对象：** 九年级数学
**总题数：** 10
**支架撤除：** 第 1–2 题包含方法提示；第 3–5 题撤除提示；第 6–8 题需要自主选择方法；第 9–10 题将该技能嵌入陌生情境中。

### 题目序列

**题目 1：** A jacket costs £80. The price increases by 10%. What is the new price?
*提示：First find 10% of £80, then add it to £80.*
- **设计意图：** 与样例几乎完全一致。相同结构（百分比增加）、友好数字（整十数的 10%）、提供提示。确认基本理解。
- **难度层级：** 近迁移
- **预期答案：** £88

**题目 2：** A laptop costs £450. The price is reduced by 20% in a sale. What is the sale price?
*提示：First find 20% of £450, then subtract it from £450.*
- **设计意图：** 引入百分比减少（减而非加），但保留提示。检验学生能否应用逆向运算。数字依然友好。
- **难度层级：** 近迁移
- **警惕常见错误：** 加而非减的学生（算出 £540）——他们在不读题的情况下机械套用增加法。

**题目 3：** A gym membership costs £35 per month. The gym announces a 12% price increase. What is the new monthly cost?
- **设计意图：** 不提供提示。非整数倍百分比（12%）。较小的基数。检验学生能否在无支架情况下处理不那么凑整的百分比。
- **难度层级：** 发展中
- **预期答案：** £39.20

**题目 4：** A house was bought for £185,000. Its value has decreased by 7%. What is it worth now?
- **设计意图：** 更大数字（检验学生面对 £185,000 时是否会慌乱）、百分比减少，以及现实情境转换（从购物转向房产）。相同的底层技能。
- **难度层级：** 发展中
- **警惕常见错误：** 算出 7%（£12,950）就直接作为答案的学生——忘记从原价中减去。

**题目 5：** A school has 840 students. Next year, the number of students is expected to increase by 5%. How many students will there be?
- **设计意图：** 情境转换（人数而非金钱）。答案必须是整数（不可能有 0.5 个学生）——检验学生是否结合情境解读答案。
- **难度层级：** 发展中
- **预期答案：** 882（840 × 0.05 = 42；840 + 42 = 882）

**题目 6：** A car was worth £12,500 at the start of the year. By the end of the year, it was worth £11,250. What was the percentage decrease?
- **设计意图：** 逆向问题——百分比未知。学生必须逆向思考：先求差值（£1,250），再计算 £1,250 占 £12,500 的百分之几。检验对关系的深层理解，而非仅仅正向套用。
- **难度层级：** 远迁移
- **警惕常见错误：** 将 £1,250 算作 £11,250（新值）而非 £12,500（原值）百分比的学生——这是预设的常见错误之一。
- **预期答案：** 10%

**题目 7：** A shirt is advertised as "30% off! Now only £28." What was the original price?
- **设计意图：** 另一道逆向问题——这次是从折后价反推原价。学生必须识别出 £28 是原价的 70%（而不是 100%）。这道题明显更难，因为它需要比例推理。
- **难度层级：** 远迁移
- **预期答案：** £40（£28 ÷ 0.7 = £40）

**题目 8：** A town's population increased by 15% to reach 9,200 people. What was the population before the increase?
- **设计意图：** 与第 7 题结构相同（已知新值和变化百分比求原值），但改为增加而非减少，且换了新情境。检验学生能否在两个方向上迁移逆向方法。
- **难度层级：** 远迁移
- **预期答案：** 8,000（9,200 ÷ 1.15 = 8,000）

**题目 9：** A shop increases prices by 20% and then offers a "20% off" sale. A customer says: "The 20% increase and 20% decrease cancel out, so the price is back to normal." Are they correct? Explain your answer using a specific example.
- **设计意图：** “反转”题。答案是否定的——先涨 20% 再降 20% 并不会回到原价（例如 £100 → £120 → £96）。这揭示了关于百分比的深层误区，并强制要求解释，而不仅仅是计算。
- **难度层级：** 远迁移 / 批判性思维
- **预期答案：** 不正确。示例：£100 + 20% = £120；£120 - 20% = £96，而非 £100。20% 的降幅是基于更高的金额计算的。

**题目 10：** An investment grows by 5% per year. If you invest £1,000, how much will it be worth after 3 years?
- **设计意图：** 复合百分比增长——每年的百分比都基于上一年的新总额计算，而非初始本金。这将技能延伸到新领域（复利增长），并预告未来主题。并非所有学生都能做出这道题，这没关系——它属于拓展领域。
- **难度层级：** 远迁移 / 拓展
- **预期答案：** £1,157.63（£1,000 × 1.05³）

### 支架撤除计划

| 题号 | 支架水平 |
|----------|---------------|
| 1–2 | 提供方法提示（"First find X% of Y, then add/subtract"） |
| 3–5 | 无提示。学生必须独立回忆并应用方法 |
| 6–8 | 逆向问题。学生必须自主确定方法（从新值逆推原值）。不提供路径指引 |
| 9–10 | 概念推理与拓展。学生必须解释、论证或将技能延伸到新领域 |

### 分层教学

**支持（针对在第 1–3 题上遇到困难的学生）：**
- 提供方法卡："Step 1: Find the percentage. Step 2: Add (increase) or subtract (decrease)."
- 缩减至仅做第 1–5 题。第 6 题及以后要求先稳固掌握正向应用，再尝试逆向问题。
- 为第 6 题（逆向百分比）配对一个样例——可串联使用“样例渐隐设计师”。

**拓展（针对快速完成全部 10 题的学生）：**
- 题目 11："A price increases by 25% and then decreases by 20%. Is the final price higher, lower, or the same as the original? Prove it algebraically."
- 题目 12："How many years would it take for an investment at 5% compound interest to double? Estimate first, then calculate."

### 监控指南

- **第 1–2 题：** 这两题应在 2–3 分钟内完成。如果学生在这里卡住，说明他们尚未掌握基本方法——立即用样例进行快速重教。
- **第 4 题：** 在此核查答案。如果学生写下 £12,950（百分比部分而非新价格），说明他们理解计算，但忘记了最后一步。这只需步骤提醒，不必重教。
- **第 6 题：** 这是诊断题。如果学生试图除以错误的基数（例如求占新值而非原值的百分比），说明存在常见误区。停下来用针对性例题处理："The percentage change is always calculated relative to the ORIGINAL amount."
- **第 9 题：** 如果学生说“是的，相互抵消了”，不要直接揭示答案。而是追问："Test it with £100. Show me the maths." 让算出 £96（而不是 £100）时的惊讶感制造认知冲突。
- **一般原则：** 前 5 分钟巡视，检查第 1–3 题。如果第 3 题有 80% 以上学生做对，全班就准备好继续独立练习。如果低于 80%，暂停并弥补缺口。

---

## 已知局限性

1. **该题目序列假定聚焦于单一技能。** 真实考试题目往往结合多种技能（百分比变化 + 读图 + 情境解读）。本序列旨在建立核心技能的流畅度；与其他技能的穿插应在后续课程中进行，而不是在这套初始练习中。后续课程可串联使用“穿插练习单元规划器”开展混合练习。

2. **表面特征变式可能会让尚未掌握基本步骤的学生感到困惑。** 对于能力较弱的学生，过早引入过多变化会让人不知所措。对这些学生，应先做 4–5 道近迁移题（仅改变数字），再引入情境变化。对于能力较强的班级，可以跳过第 1–2 题以压缩序列。

3. **监控指南需要教师在课堂上有效巡视。** 设计好题目是必要的，但还不够——教师必须真正观察学生做题、识别错误模式并在恰当时机介入。指南有助于引导注意力，但无法替代教师关于“何时放手让学生挣扎、何时介入干预”的专业判断。
