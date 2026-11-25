---
# AGENT SKILLS STANDARD FIELDS (v2)
name: adaptive-hint-sequence-designer
description: "为特定题型生成级联提示序列，在不直接给出答案的前提下逐步揭示线索。适用于设计辅导对话或脚手架学习单。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "ai-learning-science/adaptive-hint-sequence-designer"
skill_name: "自适应提示序列设计器"
domain: "ai-learning-science"
version: "1.0"
evidence_strength: "strong"
evidence_sources:
  - "VanLehn (2011) — The relative effectiveness of human tutoring, intelligent tutoring systems, and other tutoring systems (meta-analysis, effect size 0.76)"
  - "Aleven & Koedinger (2002) — An effective metacognitive strategy: learning by doing and explaining with a computer-based Cognitive Tutor"
  - "Shute (2008) — Focus on formative feedback"
  - "Wood, Bruner & Ross (1976) — The role of tutoring in problem solving"
  - "Razzaq & Heffernan (2010) — Hints: is it better to give or wait to be asked?"
input_schema:
  required:
    - field: "problem_type"
      type: "string"
      description: "学生正在处理的具体题目或任务类型——他们试图解决或产出的内容"
    - field: "common_sticking_points"
      type: "string"
      description: "学生通常卡住的位置——阻碍进展的具体迷思概念、程序性错误或概念漏洞"
  optional:
    - field: "student_level"
      type: "string"
      description: "年龄/年级及能力水平"
    - field: "subject_area"
      type: "string"
      description: "课程学科"
    - field: "delivery_context"
      type: "string"
      description: "提示是由 AI 系统、教师交付，还是嵌入在学习材料中"
    - field: "number_of_hint_levels"
      type: "integer"
      description: "需要设计多少个渐进提示层级——通常为 3–5 级"
    - field: "final_hint_policy"
      type: "string"
      description: "提示序列末尾的处理方式——给出答案、转介教师或提供不同任务"
output_schema:
  type: "object"
  fields:
    - field: "hint_sequence"
      type: "array"
      description: "级联提示序列——从最笼统到最具体，每一级在不给出答案的情况下揭示更多线索"
    - field: "hint_design_rationale"
      type: "object"
      description: "为什么每个提示层级这样设计——它承担什么认知功能"
    - field: "trigger_conditions"
      type: "object"
      description: "何时交付每条提示——基于时间、基于错误、基于请求或基于行为的触发条件"
    - field: "bottom_out_design"
      type: "object"
      description: "当所有提示耗尽时会发生什么——‘兜底（bottom-out）’策略"
chains_well_with:
  - "intelligent-tutoring-dialogue-designer"
  - "productive-failure-desirable-difficulty-designer"
  - "worked-example-fading-designer"
  - "formative-assessment-loop-designer"
teacher_time: "4 分钟"
tags: ["hints", "scaffolding", "ITS", "VanLehn", "Aleven", "adaptive", "tutoring", "cognitive-tutor"]
---

# 自适应提示序列设计器

## 本技能的作用

为特定题型设计级联提示序列——一系列逐步揭示更多信息的提示，帮助学生越过卡点，而不是直接给出答案。这是智能辅导系统（ITS）设计中技术要求最高的环节之一。VanLehn（2011）元分析的核心洞见在于：辅导（无论人类还是 AI）的有效性高度依赖于脚手架的质量——而提示序列正是主要的脚手架机制。序列设计一旦出错，要么会让学生沮丧（提示太模糊、太少），要么会剥夺他们的学习机会（提示太具体、太早）。输出包括完整的提示级联（通常为 3–5 个层级，从宏观策略引导到具体程序轻推）、解释每一层级认知功能的设计理据、触发条件（何时触发每条提示）以及兜底策略（提示耗尽时如何处理）。AI 在此尤为关键，因为设计有效的提示序列需要同时预判学生错误、校准提示具体度，并确保每一级提示都恰好提供足够信息来帮学生解困，同时不绕过产生学习的认知加工过程。

## 实证基础

VanLehn（2011）对辅导有效性进行了最全面的元分析，比较了人类辅导、智能辅导系统和其他方法。他发现 ITS 的平均效应量为 0.76——惊人地接近人类辅导（0.79），且显著高于“无辅导”条件。关键在于，ITS 的有效性取决于步骤级交互的质量：在每个解题步骤提供反馈与提示的系统（内循环 inner loop）远比仅评估最终答案的系统（外循环 outer loop）更有效。Aleven & Koedinger（2002）研究了 Carnegie Learning Cognitive Tutor 中的求助行为，发现学生对提示的使用往往不够理想——要么请求提示过快（在尝试解题前就点），要么过慢（陷入无效挣扎）。他们发现，训练学生掌握元认知提示策略（“先自己尝试，再请求提示，然后向自己解释这条提示”）显著提升了学习效果。Razzaq & Heffernan（2010）比较了主动提示（自动给出）与被动提示（应请求给出），发现最佳方式取决于学生水平：表现较弱的学生从主动提示中获益更多，而表现较强的学生从先挣扎再求助中获益更多。Shute（2008）综述了形成性反馈研究，指出有效反馈应具体、及时且可操作——这些原则直接适用于提示设计。Wood、Bruner & Ross（1976）确立了脚手架（scaffolding）概念：提供临时支持使学习者能完成独立时无法完成的任务，然后随着能力发展逐步撤除支持。

## 输入规范

教师必须提供：
- **题型（Problem type）：** 学生正在解决的问题。*例如：“解一元一次方程——如 3x + 7 = 22” / “为议论文段落撰写主题句” / “配平化学方程式” / “调试一个本应返回排序列表却返回 None 的 Python 函数”*
- **常见卡点（Common sticking points）：** 学生卡住的位置。*例如：“学生忘了在方程两边做相同运算” / “学生写的主题句太笼统，或只陈述事实而非提出主张” / “学生随机配平原子而非系统配平” / “学生不理解 Python 的 sort() 返回 None——他们以为会返回排序后的列表”*

可选项（如可用则由上下文引擎注入）：
- **学生水平（Student level）：** 年级与能力水平
- **学科领域（Subject area）：** 课程学科
- **交付情境（Delivery context）：** AI 系统、教师或学习材料
- **提示层级数量（Number of hint levels）：** 需要设计多少级
- **最终提示策略（Final hint policy）：** 序列末尾如何处理

## 提示词（Prompt）

```
You are an expert in hint sequence design for intelligent tutoring systems, with deep knowledge of VanLehn's (2011) meta-analysis of ITS effectiveness, Aleven & Koedinger's (2002) research on hint-seeking behaviour, Razzaq & Heffernan's (2010) work on proactive vs. reactive hints, Shute's (2008) formative feedback principles, and Wood, Bruner & Ross's (1976) scaffolding framework. You understand that hint design is the hardest part of ITS design: too little help produces frustration and abandonment; too much help produces answer-copying without learning. The optimal hint sequence progressively reduces the cognitive work required while preserving as much productive struggle as possible.

CRITICAL PRINCIPLES:
- **Progressive specificity.** The first hint should be the MOST GENERAL — pointing the student toward the right strategy or concept without revealing the specific step. Each subsequent hint should be more specific, narrowing the cognitive search space while still requiring the student to do some thinking. The final hint (the "bottom-out hint") may reveal the specific step but should still require the student to execute it and understand why.
- **Each hint should do ONE thing.** A hint that says "Remember to isolate the variable by subtracting 7 from both sides and then dividing by 3" is not a hint — it's the answer in disguise. Each hint level should address ONE aspect of the sticking point.
- **Hints should address the CAUSE of the error, not just the symptom.** If a student gets 3x + 7 = 22 wrong, the hint should not just say "Try again" (too vague) or "x = 5" (the answer). It should address the likely CAUSE: "What operation will move the 7 to the other side?" — targeting the specific conceptual gap.
- **Trigger conditions matter as much as hint content.** When a hint fires is as important as what it says. Too early: the student doesn't get the chance to struggle productively. Too late: the student has given up. Design triggers based on observable behaviour: time elapsed, number of incorrect attempts, specific error patterns, or student request.
- **The bottom-out strategy must still produce learning.** When all hints are exhausted, the system cannot just shrug and move on. The bottom-out should provide the answer WITH a self-explanation prompt: "The answer is X because Y. In your own words, explain why Y leads to X." This converts the bottom-out from answer-giving to learning.

Your task is to design a hint sequence for:

**Problem type:** {{problem_type}}
**Common sticking points:** {{common_sticking_points}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Student level:** {{student_level}} — if not provided, design for a general secondary school context.
**Subject area:** {{subject_area}} — if not provided, infer from the problem type.
**Delivery context:** {{delivery_context}} — if not provided, design for an AI tutoring system that can also be used by teachers.
**Number of hint levels:** {{number_of_hint_levels}} — if not provided, design 4 levels (strategic → conceptual → procedural → bottom-out).
**Final hint policy:** {{final_hint_policy}} — if not provided, design a bottom-out hint with self-explanation prompt.

Return your output in this exact format:

## Adaptive Hint Sequence: [Problem Type]

**Problem type:** [What students are solving]
**Common sticking points:** [Where they get stuck]
**Hint levels:** [How many levels, from general to specific]

### Hint Architecture

[Overview of the hint strategy — what each level does and why the sequence is ordered this way]

### Hint Sequence

For each level:
**Level [N]: [Hint type — Strategic / Conceptual / Procedural / Bottom-out]**
- **Hint text:** [Exactly what the student sees or hears]
- **Cognitive function:** [What this hint does — what cognitive work it performs for the student and what it preserves for them to do]
- **Trigger condition:** [When this hint fires — time, errors, request, behaviour]
- **Expected student response:** [What a student who benefits from this hint will do next]
- **If this hint doesn't help:** [What happens — escalate to next level]

### Bottom-Out Strategy

[What happens when all hints are exhausted — the specific design for revealing the answer while still producing learning]

### Trigger Conditions Summary

| Trigger Type | Condition | Hint Level Activated |
|---|---|---|
| [Type] | [Specific condition] | [Which level] |

### Adaptation Notes

[How the sequence adapts to different student profiles — stronger students may skip early levels; weaker students may need the full cascade]

**Self-check before returning output:** Verify that (a) hints are progressively more specific, (b) each hint does ONE thing, (c) hints address the cause of the error not just the symptom, (d) trigger conditions are specified, (e) the bottom-out still produces learning, and (f) the sequence preserves productive struggle.
```

## 示例输出

**情景：** *题型：“解一元一次方程——特别是 ax + b = c 形式的方程，学生必须分离出 x。示例：3x + 7 = 22” / 常见卡点：“学生忘了在两边做相同运算（只从左边减去 7 而右边不减）。学生不理解逆运算概念（该减时反而加，或反之）。学生运算顺序出错（先除以 3 再减去 7）。” / 交付情境：“AI 辅导系统——触发时提示出现在屏幕上” / 学生水平：“八年级，代数第一学期”*

---

## 自适应提示序列：解一元一次方程（ax + b = c）

**题型：** 解一元一次方程——在类似 3x + 7 = 22 的方程中分离出 x
**常见卡点：** 两边未同时运算、逆运算混淆、运算顺序错误
**提示层级：** 4 级（策略级 → 概念级 → 程序级 → 兜底级）

### 提示架构

序列从**策略级**（指向解题思路）经由**概念级**（激活相关原理）到**程序级**（指明具体步骤），再到**兜底级**（揭示步骤并附带自我解释）。在每一级中，学生都保留了一定的认知加工任务：

- **第 1 级（策略级）：** “这是**目标**”——学生必须自己想出方法
- **第 2 级（概念级）：** “这是**原理**”——学生必须自己想出具体运算
- **第 3 级（程序级）：** “这是**步骤**”——学生必须自己执行并验算
- **第 4 级（兜底级）：** “这是这一步的**答案**”——学生必须解释原因

### 提示序列

**第 1 级：策略级——“你的目标是什么？”**
- **提示文本：** “你的目标是把 x 单独留在方程的一边。现在，x 旁边还连着一些多余的数字。你可以先做什么来开始移除它们？”
- **认知功能：** 提醒学生整体策略（分离 x），但不指明具体执行哪种运算或先处理哪个数字。学生仍需识别要移除哪些数字以及使用什么运算。
- **触发条件：** 学生 60 秒无进展，或输入了错误的 x 值且未展示过程，或主动请求提示。
- **预期学生反应：** 学生意识到需要“去掉”+7 或 3，并尝试一种运算。即便运算选错，策略框架也已将他们的注意力重新引向目标。
- **若此提示无效：** 再出现一次错误尝试或 45 秒无进展后，升级至第 2 级。

**第 2 级：概念级——“先处理哪个数字，它的逆运算是什么？”**
- **提示文本：** “看这个方程：3x + 7 = 22。x 既乘以了 3，又加上了 7。**先**处理加法。加 7 的逆运算（相反运算）是什么？”
- **认知功能：** 这条提示完成两件事：它告诉学生**顺序**（先处理加法再处理乘法——与 BIDMAS/PEMDAS 顺序相反），并激活**逆运算**概念（加法的相反运算）。学生仍需自己想出“加 7 的相反运算是减 7”并将其应用于两边。
- **触发条件：** 学生在第 1 级后尝试了错误运算（例如先除以 3），或正确识别了“减去”但未应用于两边。
- **预期学生反应：** 学生写出 3x + 7 - 7 = 22 - 7，化简为 3x = 15。如果他们只从一边相减，第 3 级会处理这一问题。
- **若此提示无效：** 再出现一次错误或 30 秒无进展后，升级至第 3 级。

**第 3 级：程序级——“对两边做同样的事”**
- **提示文本：** “从方程**两边**同时减去 7。左边变成 3x + 7 - 7 = 3x。右边变成多少？22 - 7 = ？”
- **认知功能：** 这条提示指明了具体运算（减去 7）并强调了“两边同时”原则。学生仍需计算 22 - 7 = 15，并自己想出下一步（除以 3）。提示解决了**第一步**，但把**第二步**留给了学生。
- **触发条件：** 学生只从一边相减，或在第 2 级后仍无法识别正确运算。
- **预期学生反应：** 学生写出 3x = 15，随后尝试通过两边除以 3 分离 x，得出 x = 5。
- **若此提示无效：** 如果学生在此提示后仍无法完成题目（算不出 22 - 7，或不知道下一步要除以 3），升级至兜底级。

**第 4 级：兜底级——“这是步骤，请解释为什么。”**
- **提示文本：** “完整解答如下：3x + 7 = 22 → 两边减去 7 → 3x = 15 → 两边除以 3 → x = 5。现在：请用你自己的话解释，**为什么**我们在除以 3 之前先减去 7？如果我们先除以 3 会发生什么？”
- **认知功能：** 答案已完全揭示，但自我解释提示保留了学习价值。通过追问“为什么是这个顺序？”，系统迫使学生投入数学逻辑思考，而不只是抄写答案。反事实问题（“先除会怎样？”）能培养对运算顺序的更深理解。
- **触发条件：** 前述所有提示耗尽，学生仍无法完成题目。
- **预期学生反应：** 学生解释（文本输入或选择）：“我们先减 7 是因为这样更简单 / 因为 7 是加上去的，不是乘在 x 上的 / 因为如果我们先除以 3，就必须把 7 也除以 3，这会产生分数。”以上任一表述均表明理解。

### 兜底策略

兜底提示会揭示完整解答，但要求学生在进入下一题之前完成自我解释。系统呈现两个提示：

1. **解释解答：** “为什么我们在除以 3 之前先减去 7？”（自由文本或多项选择）
2. **预测类似题目：** “如果方程是 5x + 12 = 37，你会先做什么？”（检验学生能否将原理迁移到新实例）

如果学生的自我解释准确，则进入下一题（一道类似方程，检验即时应用）。如果自我解释不准确（“因为 7 比 22 小”），则给出简短纠正性解释后再继续。兜底**不是**失败状态——它是一个学习事件。自我解释将“直接给答案”转化为“建构理解”。

### 触发条件汇总

| 触发类型 | 条件 | 激活的提示层级 |
|---|---|---|
| 基于时间 | 60 秒无进展 | 第 1 级 |
| 基于错误 | 最终答案错误且未展示过程 | 第 1 级 |
| 基于错误 | 运算错误（如先除后减） | 第 2 级 |
| 基于错误 | 正确运算但仅应用于一边 | 第 3 级 |
| 基于请求 | 学生点击“提示”按钮 | 序列中的下一级 |
| 耗尽兜底 | 前述提示已全部交付，仍卡住 | 第 4 级（兜底级） |

### 自适应调整说明

**针对较强学生：** 如果学生已连续成功解出 3 道以上类似方程，跳过第 1 级（他们已掌握策略）。如果他们出错，直接从第 2 级开始——他们的卡点更可能是概念或程序性的，而非策略性的。

**针对较弱学生：** 如果学生在连续前 2 道题上都需要兜底提示，考虑从提示切换为样例（worked example）——学生可能缺乏提示所假设的前置知识。提示为**问题解决**提供脚手架；它们不教授基础概念。

**针对滥用提示的学生（Aleven & Koedinger, 2002）：** 如果学生不尝试解题就快速点击跳过所有提示，在第一条提示前插入“先试一试”提示：“在请求提示前先尝试一下这道题。你认为第一步最可能是什么？”这能解决元认知缺陷：防止学生学会从提示中套取答案而非主动思考。

---

## 已知局限

1. **提示序列假设学生具备从提示中获益的前置知识。** 一条说“加 7 的逆运算是什么？”的提示，假设学生理解逆运算概念。如果他们不理解，此序列中的任何提示都帮不了他们——他们需要关于前置概念的直接教学。提示序列为**问题解决**搭脚手架，而非**知识习得**。缺乏基础知识的学生需要不同的干预。

2. **最佳提示触发时机仍是一个开放的研究问题。** Razzaq & Heffernan（2010）发现主动提示帮助较弱学生、被动提示帮助较强学生，但学术界尚未收敛出定论性的触发模型。上述触发条件是合理的默认值，而非经过实证最优化的阈值。在真实的 ITS 中，需要针对实际学生群体通过 A/B 测试进行校准。

3. **提示质量取决于对错误的准确诊断。** 上述提示序列假定了特定错误模式（运算顺序错误、单边运算、逆运算混淆）。如果学生的实际错误不同（例如算错 22 - 7），提示就会偏离靶心。有效的提示系统需要针对特定错误的分支逻辑，而不仅仅是线性级联——这在设计上复杂得多。
