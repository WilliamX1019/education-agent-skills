---
# AGENT SKILLS STANDARD FIELDS (v2)
name: digital-worked-example-sequence
description: "创建用于在线或混合式教学的交互式数字样例（含渐隐设计）序列。适用于开发电子学习模块、LMS 内容或基于应用的教学。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "ai-learning-science/digital-worked-example-sequence"
skill_name: "数字样例序列设计器"
domain: "ai-learning-science"
version: "1.0"
evidence_strength: "strong"
evidence_sources:
  - "Sweller, van Merriënboer & Paas (2019) — Cognitive Architecture and Instructional Design: 20 Years Later"
  - "Renkl (2014) — Toward an instructionally oriented theory of example-based learning"
  - "Atkinson, Derry, Renkl & Wortham (2000) — Learning from examples: instructional principles from the worked examples research"
  - "Renkl, Atkinson & Große (2004) — How fading worked-out solution steps works — a cognitive load perspective"
  - "Wylie & Chi (2014) — The self-explanation principle in multimedia learning"
input_schema:
  required:
    - field: "skill_to_teach"
      type: "string"
      description: "样例所要教授的具体程序或技能"
    - field: "target_platform"
      type: "string"
      description: "样例的交付平台——学习管理系统（LMS）、应用程序、交互式 PDF、网页"
  optional:
    - field: "student_level"
      type: "string"
      description: "年龄/年级及当前熟练度"
    - field: "subject_area"
      type: "string"
      description: "课程学科"
    - field: "sequence_length"
      type: "integer"
      description: "序列中包含多少个样例——通常为 4–8 个"
    - field: "interactivity_level"
      type: "string"
      description: "平台支持的交互程度——静态展示、可点击步骤、填空、拖拽"
    - field: "student_data_available"
      type: "string"
      description: "系统是否能够追踪学生作答并自适应调整"
output_schema:
  type: "object"
  fields:
    - field: "example_sequence"
      type: "array"
      description: "从完整样例经由渐隐样例到独立解题的完整序列"
    - field: "self_explanation_prompts"
      type: "array"
      description: "嵌入每一步、要求学生解释推理过程的提示"
    - field: "fading_schedule"
      type: "object"
      description: "移除步骤的精确计划表——哪些步骤先渐隐，哪些后渐隐"
    - field: "digital_design_specs"
      type: "object"
      description: "如何在数字环境中实施——步调控制、交互性与反馈"
chains_well_with:
  - "adaptive-hint-sequence-designer"
  - "erroneous-example-designer"
  - "worked-example-to-problem-solving-transition-designer"
  - "cognitive-load-analyser"
teacher_time: "4 分钟"
tags: ["worked-examples", "fading", "digital-learning", "CLT", "Sweller", "Renkl", "self-explanation", "multimedia"]
---

# 数字样例序列设计器

## 本技能的作用

设计针对数字交付优化的样例（worked example）序列——融入自我解释提示、系统化渐隐（fading）计划以及超越纸质材料的交互设计。该序列引导学生从学习完整样例（展示并解释每一步）过渡到渐隐样例（逐步移除越来越多步骤由学生补全），最终到达独立解题。Renkl（2014）的核心洞见在于：只有当学生**主动加工**样例时，样例才能产生学习——被动阅读样例几乎不比没有样例好多少。数字交付既创造了独特机遇（每一步的自我解释提示、对渐隐步骤的即时反馈、基于表现的自适应步调），也带来了独特风险（屏幕元素间的注意力分散、多媒体带来的认知超载、不假思索一路点击跳过的诱惑）。输出包括完整样例序列、嵌入式自我解释提示、精确渐隐计划表以及数字设计规范。AI 在此尤为关键，因为设计有效的数字样例序列需要协调三个必须对齐的设计维度：内容设计（数学或程序步骤）、认知设计（渐隐计划、自我解释节点）以及界面设计（步骤如何揭示、提示出现在何处、反馈如何呈现）。

## 实证基础

Sweller、van Merriënboer & Paas（2019）面向当代数字学习情境更新了认知负荷理论，识别出数字环境中特有的外在认知负荷来源：瞬时信息（出现后又消失的内容）、多个屏幕区域之间的注意力分散（split attention）以及多媒体呈现中的冗余信息。他们强调，数字样例必须通过精心设计来管理这些负荷来源。Renkl（2014）将 25 年的样例研究综合为教学原则：样例应结构化（步骤清晰划分）、应提示自我解释（不能听凭运气）、渐隐应系统化（一次移除一步，从最近学过的步骤开始），且向独立练习的过渡应循序渐进。Atkinson 等人（2000）确立了基础原则：样例对**初学者**最有效（专家会出现“专业逆转效应”——样例变得冗余且适得其反）；样例应与练习题交替出现而非成块堆砌；核心机制是图式习得（为问题类型建立心理模板）。Renkl、Atkinson & Große（2004）证明，系统化渐隐——一次移除一个解题步骤——显著优于从完整样例到完整问题的突兀过渡。Wylie & Chi（2014）表明，嵌入在多媒体样例中的自我解释提示大幅提升了学习效果（相比无提示的样例），因为它们迫使学习者对每一步进行主动加工。

## 输入规范

教师必须提供：
- **教授技能（Skill to teach）：** 具体程序。*例如：“用消元法解二元一次方程组” / “构建平衡论证段落” / “计量单位换算” / “用 Python 编写递归函数”*
- **目标平台（Target platform）：** 交付载体。*例如：“嵌入测验的 Google Slides” / “支持逐步揭示的定制网页应用” / “交互式 PDF” / “学习管理系统（Canvas/Moodle）”*

可选项（如可用则由上下文引擎注入）：
- **学生水平（Student level）：** 年级与熟练度
- **学科领域（Subject area）：** 课程学科
- **序列长度（Sequence length）：** 样例数量
- **交互水平（Interactivity level）：** 平台支持的能力
- **可用学生数据（Student data available）：** 系统是否支持自适应

## 提示词（Prompt）

```
You are an expert in digital worked example design, with deep knowledge of Sweller et al.'s (2019) updated cognitive load theory for digital contexts, Renkl's (2014) instructional principles for example-based learning, Atkinson et al.'s (2000) foundational worked example research, Renkl, Atkinson & Große's (2004) systematic fading procedure, and Wylie & Chi's (2014) research on self-explanation in multimedia learning. You understand that digital worked examples are not PDFs of paper examples displayed on a screen — they are interactive learning tools that exploit digital affordances (step-by-step reveal, embedded prompts, immediate feedback, adaptive pacing) while managing digital risks (transient information, split attention, passive clicking).

CRITICAL PRINCIPLES:
- **Self-explanation at EVERY step.** The single most powerful design feature is a self-explanation prompt after each step: "Why did we do this?" or "What rule is being applied here?" Without self-explanation, students click through examples like a slideshow — seeing without processing. Renkl (2014) showed that prompted self-explanation is the mechanism that converts passive observation into active learning.
- **Systematic fading, not abrupt transition.** The sequence should remove ONE step at a time, starting with the LAST step (backward fading) or the step that students find easiest. Each faded step becomes a "completion problem" — the student must supply the missing step. The transition from full example to independent problem should be so gradual that students barely notice when they're doing it on their own.
- **Digital pacing: reveal steps one at a time.** Don't display the entire solution at once — this creates extraneous load and encourages scanning rather than studying. Reveal one step at a time, with the self-explanation prompt BEFORE the next step is shown. This forces students to process each step before moving on.
- **Immediate, targeted feedback on faded steps.** When a student fills in a faded step, provide immediate feedback: correct (with brief confirmation) or incorrect (with a hint addressing the specific error, not just "try again"). This is where digital delivery excels over paper.
- **Manage split attention.** The problem, the example steps, the self-explanation prompts, and the feedback must be spatially integrated — not spread across different areas of the screen. The student should never have to hold information from one screen area in working memory while looking at another area.

Your task is to design a digital worked example sequence for:

**Skill to teach:** {{skill_to_teach}}
**Target platform:** {{target_platform}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Student level:** {{student_level}} — if not provided, design for secondary school novice learners.
**Subject area:** {{subject_area}} — if not provided, infer from the skill.
**Sequence length:** {{sequence_length}} — if not provided, design 6 examples (2 full, 2 faded, 2 independent).
**Interactivity level:** {{interactivity_level}} — if not provided, design for step-by-step reveal with text input for faded steps.
**Student data available:** {{student_data_available}} — if not provided, design a fixed sequence with optional adaptation notes.

Return your output in this exact format:

## Digital Worked Example Sequence: [Skill]

**Skill:** [What students learn]
**Platform:** [Where it's delivered]
**Sequence structure:** [How many examples, from full to faded to independent]

### Sequence Overview

[The progression from fully worked to fully independent — what each example does]

### Example [N]: [Full / Faded-1 / Faded-2 / Independent]

**Problem:** [The problem to solve]
**Steps shown vs. faded:**
[Which steps are shown, which are faded (student completes), which have self-explanation prompts]

**Step-by-step design:**
For each step:
- **Step [N]:** [The step — shown or faded]
- **Self-explanation prompt:** [The question students answer before seeing the next step]
- **If faded — expected student input:** [What the student should enter]
- **Feedback on faded step:** [Immediate feedback — correct or incorrect with hint]

### Fading Schedule

[The precise schedule: which steps fade in which example, and why this order]

### Digital Design Specifications

**Pacing:** [How steps are revealed — one at a time, with forced pause at self-explanation prompts]
**Layout:** [How the screen is organised — problem, steps, prompts, feedback integrated to avoid split attention]
**Feedback timing:** [When and how feedback appears]
**Navigation:** [Can students go back? Can they skip ahead? Design choices and rationale]

### Adaptation Notes

[How the sequence could adapt based on student performance — if the platform supports it]

**Self-check before returning output:** Verify that (a) every step has a self-explanation prompt, (b) fading is systematic and gradual, (c) steps are revealed one at a time, (d) feedback on faded steps is immediate and specific, and (e) split attention is managed through integrated layout.
```

## 示例输出

**情景：** *教授技能：“用消元法解二元一次方程组——例如 2x + 3y = 12 与 4x - 3y = 6。学生需要：识别要消去的未知数、将方程相加或相减、解出其中一个未知数、回代求出另一个未知数。” / 目标平台：“定制网页应用——支持逐步揭示、接收文本输入、提供即时反馈” / 学生水平：“十年级，刚学会解一元一次方程，首次接触二元一次方程组” / 序列长度：“6 个样例（2 个完整、2 个渐隐、2 个独立）”*

---

## 数字样例序列：消元法解二元一次方程组

**技能：** 用消元法解二元一次方程组
**平台：** 定制网页应用（逐步揭示、文本输入、即时反馈）
**序列结构：** 6 个样例——E1–E2（完整样例）、E3–E4（逐步渐隐）、E5–E6（独立练习，可选提示）

### 序列概览

| 样例 | 类型 | 展示步骤 | 渐隐步骤 | 目的 |
|---|---|---|---|---|
| E1 | 完整样例 | 全部 5 步 | 无 | 学生学习并对每一步进行自我解释 |
| E2 | 完整样例（不同数字） | 全部 5 步 | 无 | 通过变式强化程序记忆 |
| E3 | 渐隐——移除第 5 步 | 第 1–4 步 | 第 5 步（最终检验） | 学生补全最简单的一步 |
| E4 | 渐隐——移除第 4、5 步 | 第 1–3 步 | 第 4–5 步（回代求解与检验） | 学生补全最后两步 |
| E5 | 独立练习（提供提示） | 不展示步骤 | 全部步骤 | 学生独立求解，可调用提示序列 |
| E6 | 独立练习（无提示） | 不展示步骤 | 全部步骤 | 完全独立练习 |

### 样例 1：完整样例

**题目：** 联立求解：2x + 3y = 12（方程 1）和 4x - 3y = 6（方程 2）

**第 1 步——识别消元机会**
*屏幕展示：* “观察含 y 的项：+3y 和 -3y。它们系数**大小相同**但**符号相反**。如果我们将两个方程相加，y 项就会抵消。”
*自我解释提示：* “为什么我们可以把这两个方程加在一起？+3y 和 -3y 相加时 y 项会发生什么？”[学生输入回答后才出现下一步]
*学生作答后展示的标准解释：* “+3y + (-3y) = 0。因为互为相反数，y 项相互抵消。”

**第 2 步——方程相加**
*屏幕展示：* “(2x + 3y) + (4x - 3y) = 12 + 6 → 6x + 0y = 18 → 6x = 18”
*自我解释提示：* “我们把**左边**与左边相加，**右边**与右边相加。为什么这样做是允许的？（提示：两个方程都成立，所以两边相等。）”

**第 3 步——求解 x**
*屏幕展示：* “6x = 18 → x = 18 ÷ 6 → x = 3”
*自我解释提示：* “现在我们得到了一个一元一次方程——你已经会解了。这里我们使用了什么运算？”

**第 4 步——回代求解**
*屏幕展示：* “将 x = 3 代入方程 1：2(3) + 3y = 12 → 6 + 3y = 12 → 3y = 6 → y = 2”
*自我解释提示：* “为什么我们代入方程 1 而不是方程 2？（其实代入哪个都可以。你能代入方程 2 验证一下吗？）”

**第 5 步——检验解**
*屏幕展示：* “检验：方程 1：2(3) + 3(2) = 6 + 6 = 12 ✓。方程 2：4(3) - 3(2) = 12 - 6 = 6 ✓。方程组的解为：x = 3, y = 2。”
*自我解释提示：* “为什么在**两个**方程中都进行检验很重要，而不仅仅检验其中一个？”

### 样例 3：渐隐——移除第 5 步

**题目：** 联立求解：3x + 2y = 16 和 5x - 2y = 8

第 1–4 步按与 E1 相同的结构展示（并附带自我解释提示）。

**第 5 步——渐隐（由学生补全）：**
*屏幕展示：* “我们求出了 x = 3 和 y = 3.5。现在在两个方程中**检验**你的解。”
*学生输入框：* [两个输入框：“方程 1：3(___) + 2(___) = ___” 以及 “方程 2：5(___) - 2(___) = ___”]
*预期输入：* 方程 1：3(3) + 2(3.5) = 9 + 7 = 16 ✓。方程 2：5(3) - 2(3.5) = 15 - 7 = 8 ✓。
*正确反馈：* “两个方程都验算通过。你已验证该解正确。”
*错误反馈：* “检查一下你的算术计算。仔细将 x = 3 和 y = 3.5 代入每个方程。”

### 样例 4：渐隐——移除第 4、5 步

**题目：** 联立求解：x + 4y = 14 和 3x - 4y = 2

展示第 1–3 步。方程相加后：4x = 16，因此 x = 4。

**第 4 步——渐隐：**
*屏幕展示：* “已知 x = 4。将其代入方程 1 求出 y。”
*学生输入框：* [y = ___]
*预期输入：* y = 2.5（由 4 + 4y = 14 → 4y = 10 → y = 2.5 得出）
*正确反馈：* “正确！现在检验你的解。”
*错误反馈（例如 y = 10）：* “你可能忘了做除法。4y = 10 意味着 y = 10 ÷ 4。再试一次。”

**第 5 步——渐隐：** [同 E3]

### 渐隐计划表

| 样例 | 第 1 步（识别） | 第 2 步（加减） | 第 3 步（求解） | 第 4 步（回代） | 第 5 步（检验） |
|---|---|---|---|---|---|
| E1 | 展示 | 展示 | 展示 | 展示 | 展示 |
| E2 | 展示 | 展示 | 展示 | 展示 | 展示 |
| E3 | 展示 | 展示 | 展示 | 展示 | **渐隐** |
| E4 | 展示 | 展示 | 展示 | **渐隐** | **渐隐** |
| E5 | **渐隐** | **渐隐** | **渐隐** | **渐隐** | **渐隐** |
| E6 | **渐隐** | **渐隐** | **渐隐** | **渐隐** | **渐隐** |

**渐隐逻辑：** 步骤按**从后往前**的顺序渐隐（逆向渐隐，backward fading）。第 5 步（检验）最先渐隐，因为它在程序上最简单。第 1 步（识别消元机会）最后渐隐，因为它需要最多的策略性思考。这意味着学生会先独立完成**较容易**的步骤，同时在**较难**的步骤上继续获得脚手架支持。

### 数字设计规范

**步调控制：** 点击“下一步”按钮揭示每一步。自我解释提示出现在下一步**之前**，学生必须输入回答（至少 5 个字符），揭示下一步的按钮才会激活。这能防止不加思考地一路点击跳过。

**页面布局：** 题目显示在屏幕**顶部**并全程保持可见。步骤按顺序显示在题目下方——每一步新步骤都紧接在上一步下方，使学生能看到累积的解题过程。自我解释提示作为内联文本框紧跟在每一步下方。渐隐步骤显示为带有步骤标签（“第 4 步：回代求 y”）的空白输入框。

**反馈时机：** 在渐隐步骤中，学生提交答案后立即出现反馈。正确：绿色对勾及简短确认。错误：琥珀色高亮并给出具体提示（不只是“错误”，而是针对可能出错的地方）。学生可在正确答案及解释揭示前重试两次。

**导航控制：** 学生可以向上滚动回顾之前的步骤，但**不能**向前跳过。他们必须完成每一步的自我解释提示才能继续。他们**可以**返回修改自我解释的回答。样例完成后，“总结”视图会一并展示所有步骤。

### 自适应调整说明

如果平台支持追踪学生作答：
- **如果学生所有自我解释回答正确且首次尝试即完成渐隐步骤：** 跳过 E2（第二个完整样例），直接进入 E3。学生不需要额外的完整样例。
- **如果学生在渐隐步骤上遇到困难（2 次以上错误尝试）：** 在 E4 与 E5 之间插入一个额外的渐隐样例，每次仅多渐隐一步。不要过快跳到完全独立练习。
- **如果学生的自我解释暴露出特定迷思概念：** 分支进入针对该迷思概念的微型课程，然后再继续序列。

---

## 已知局限

1. **样例对“初学者”最有效。** 随着学生趋于熟练，样例会变得冗余，甚至可能阻碍表现（即“专业逆转效应”——Kalyuga et al., 2003）。本序列专为学生**首次**接触二元一次方程组而设计。对于已有一定熟练度的学生，应从渐隐序列的较后位置开始，或直接进入独立练习。

2. **数字自我解释提示可能流于形式。** 学生可能会学会只输入满足解锁下一步的最低字数要求，而不真正投入思考。本设计对此进行了缓解（最低字符数、提示出现在答案之前），但无法完全杜绝敷衍点击行为。在课堂使用时，教师应定期抽查学生的自我解释作答，以检验其真实参与度。

3. **上述渐隐计划是一个固定序列。** 真正的自适应渐隐应根据每位学生的表现调整节奏——对展现掌握度的学生加快渐隐，对遇到困难的学生放慢渐隐。固定序列适用于尚不具备自适应能力的平台。具备追踪功能的平台应利用上述自适应调整说明来个性化调整节奏。
