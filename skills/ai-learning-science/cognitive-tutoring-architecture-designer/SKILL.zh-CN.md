---
# AGENT SKILLS STANDARD FIELDS (v2)
name: cognitive-tutoring-architecture-designer
description: "为认知辅导系统或自适应学习平台绘制知识组件与技能层级图谱。适用于设计智能辅导软件或基于掌握度的技能系统。"
disable-model-invocation: true
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "ai-learning-science/cognitive-tutoring-architecture-designer"
skill_name: "认知辅导架构设计器"
domain: "ai-learning-science"
version: "1.0"
evidence_strength: "strong"
evidence_sources:
  - "Anderson et al. (1995) — Cognitive tutors: lessons learned (ACT-R theory applied to education)"
  - "Corbett & Anderson (1995) — Knowledge tracing: modeling the acquisition of procedural knowledge"
  - "Koedinger & Aleven (2007) — Exploring the assistance dilemma in experiments with cognitive tutors"
  - "Ritter et al. (2007) — Cognitive Tutor: applied research in mathematics education"
  - "Pane et al. (2014) — Effectiveness of cognitive tutor algebra I at scale (RAND evaluation)"
input_schema:
  required:
    - field: "skill_domain"
      type: "string"
      description: "需要辅导的具体知识或技能领域——学生需要学会做什么"
    - field: "knowledge_components"
      type: "string"
      description: "构成该领域能力的具体知识点或子技能——掌握度的基本构建模块"
  optional:
    - field: "student_level"
      type: "string"
      description: "年龄/年级及能力水平"
    - field: "subject_area"
      type: "string"
      description: "课程学科"
    - field: "common_errors"
      type: "string"
      description: "学生最常犯的错误及其背后的迷思概念"
    - field: "mastery_threshold"
      type: "string"
      description: "什么算作掌握——在被认定为学会之前需要连续正确应用多少次"
    - field: "system_context"
      type: "string"
      description: "用于 AI 辅导系统、教师授课模式还是混合模式"
output_schema:
  type: "object"
  fields:
    - field: "cognitive_model"
      type: "object"
      description: "知识组件图谱——学生需要知道什么以及各组件之间的关系"
    - field: "knowledge_tracing_design"
      type: "object"
      description: "如何追踪学生对每个知识组件的掌握度——追踪算法与掌握标准"
    - field: "problem_selection_logic"
      type: "object"
      description: "如何根据学生当前的知识状态选择下一道题目"
    - field: "feedback_architecture"
      type: "object"
      description: "在每一步提供什么反馈，并与具体知识组件和错误类型关联"
chains_well_with:
  - "adaptive-hint-sequence-designer"
  - "intelligent-tutoring-dialogue-designer"
  - "formative-assessment-loop-designer"
  - "worked-example-to-problem-solving-transition-designer"
  - "technological-pedagogical-content-knowledge-developer"
teacher_time: "6 分钟"
tags: ["cognitive-tutor", "ACT-R", "Anderson", "knowledge-tracing", "Corbett", "mastery", "ITS", "adaptive"]
---

# 认知辅导架构设计器

## 本技能的作用

为辅导系统设计认知架构——包括知识组件模型、知识追踪算法、选题逻辑和反馈架构，共同构成自适应学习体验。本技能基于 Anderson 等人（1995）在卡内基梅隆大学开发的认知辅导系统（Cognitive Tutor）架构，它至今仍是最具实证检验基础的智能辅导方法之一。认知辅导方法建立在 ACT-R 理论之上：即任何领域的专业能力都可以拆解为一组离散的“知识组件”（产生式规则），这些组件可以分别学习、练习和追踪。系统维护每个学生知识状态的模型（知识追踪），选择针对学生尚未掌握的知识组件的题目，并在出现错误时提供步骤级反馈。Pane 等人（2014）进行的一项大规模兰德公司（RAND）评估发现，Cognitive Tutor Algebra I 相较于传统教学提升了学生成绩。AI 在此尤为关键，因为该架构需要跨多个组件实时追踪个体知识状态——这项任务在计算上非常直接，但对于管理 30 名学生的教师而言在人力上几乎不可能实现。

## 实证基础

Anderson 等人（1995）基于 ACT-R（Adaptive Control of Thought—Rational，思维自适应控制——理性版）开发了认知辅导系统，该认知架构将人类学习建模为产生式规则——即 IF-THEN 知识组件——的习得。例如，在代数中，一个知识组件可能是“IF 方程形式为 ax + b = c，THEN 第一步从两边减去 b”。核心洞见在于：复杂技能可以拆解为有限数量的这类组件，每个组件都可以独立追踪与辅导。认知辅导系统维护一个学生模型，估算每位学生已学会每个知识组件的概率，并选择针对最薄弱组件的题目。Corbett & Anderson（1995）开发了知识追踪（KT）算法来追踪学生掌握度。KT 使用隐马尔可夫模型：每个知识组件要么处于“已学会”状态，要么处于“未学会”状态（隐状态）。每当学生尝试涉及某个知识组件的解题步骤时，系统观察该步骤是否正确（可观察量），并更新对该组件已学会概率的估计。四个参数控制该模型：P(L₀)——学生在教学前已知该组件的概率；P(T)——每次练习机会学会该组件的概率；P(G)——不知道却猜对的概率；以及 P(S)——虽然知道却粗心失误的概率。当 P(Lₙ) 超过阈值（通常为 0.95）时，该组件被视为已掌握。Koedinger & Aleven（2007）在认知辅导系统语境下提出了“辅助两难（assistance dilemma）”：提供过多辅助（即时提示、步骤级指导）可能导致学生学会的是辅导系统的界面操作而非领域知识。他们发现最佳辅助水平取决于学生当前的知识状态——学习困难的学生受益于更多辅助，而高水平学生受益于更少辅助。Ritter 等人（2007）报告了 Cognitive Tutor Algebra 在超过 2,600 所学校中的部署情况，证明了该方法的可扩展性。Pane 等人（2014）对 Cognitive Tutor Algebra I 进行了一项兰德公司资助的随机对照试验，发现其对代数成绩产生了适度但显著的正向影响，尤其是对按设计规范使用该系统（忠实于预期模型）的学生而言。

## 输入规范

教师必须提供：
- **技能领域（Skill domain）：** 学生需要学习的内容。*例如：“解一元一次方程——从一步方程（x + 5 = 12）到两步方程（3x + 5 = 20），再到两边都含未知数的多步方程（4x + 3 = 2x + 11）” / “配平化学方程式” / “根据原始数据构建并解读直方图”*
- **知识组件（Knowledge components）：** 构成模块。*例如：“对于线性方程：（1）识别未知数，（2）加减法互逆运算（加 ↔ 减），（3）乘除法互逆运算（乘 ↔ 除），（4）运算顺序（先撤销加减再撤销乘除），（5）两边同时施加运算，（6）合并同类项，（7）将未知数移到一侧” / “对于直方图：（1）识别连续数据，（2）选择合适的组距，（3）计算每组频数，（4）设定坐标轴刻度，（5）绘制无间隙柱条，（6）从直方图中读取数值，（7）比较分布”*

可选项（如可用则由上下文引擎注入）：
- **学生水平（Student level）：** 年级与能力水平
- **学科领域（Subject area）：** 课程学科
- **常见错误（Common errors）：** 高频错误及其原因
- **掌握阈值（Mastery threshold）：** 什么算作已掌握
- **系统背景（System context）：** AI 系统、教师授课还是混合模式

## 提示词（Prompt）

```
You are an expert in cognitive tutoring architecture, with deep knowledge of Anderson et al.'s (1995) ACT-R-based Cognitive Tutor framework, Corbett & Anderson's (1995) knowledge tracing algorithm, Koedinger & Aleven's (2007) assistance dilemma research, Ritter et al.'s (2007) large-scale deployment data, and Pane et al.'s (2014) RAND evaluation. You understand that effective tutoring systems are built on a precise cognitive model — a decomposition of the target skill into knowledge components that can be individually tracked, practised, and mastered. You know that the quality of the cognitive model determines the quality of the tutoring: a poorly decomposed skill set leads to misdiagnosis, inappropriate problem selection, and ineffective feedback.

CRITICAL PRINCIPLES:
- **Decompose into TESTABLE knowledge components.** Each component must be independently observable — there must be a problem step where the component is required and where success or failure reveals whether the student has learned it. If you can't design a problem step that isolates a component, the decomposition is too coarse.
- **Knowledge components should be at the GRAIN SIZE of learning.** Too coarse (e.g., "can solve equations") and you can't diagnose specific weaknesses. Too fine (e.g., "can subtract 7 from 22") and you're tracking arithmetic, not algebra. The right grain size is the level at which students make conceptually meaningful errors.
- **Map the dependency structure.** Some components depend on others — you can't apply an operation to both sides if you don't know the inverse operation. The problem selection logic should respect these dependencies: don't present problems requiring Component 5 if the student hasn't mastered Components 1-4.
- **Link errors to components.** Each common error should be traceable to a specific knowledge component that has not been mastered. If a student subtracts from only one side, that's a failure of the "apply to both sides" component, not a general "equation" failure. The feedback should target the specific component.
- **Mastery is probabilistic, not binary.** Knowledge tracing gives a PROBABILITY of mastery, not a certainty. A student who gets 3 in a row right might still be guessing (P(G) > 0). A student who gets one wrong might have slipped (P(S) > 0). The system should require consistent performance before declaring mastery.

Your task is to design a cognitive tutoring architecture for:

**Skill domain:** {{skill_domain}}
**Knowledge components:** {{knowledge_components}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Student level:** {{student_level}} — if not provided, design for a general secondary school context.
**Subject area:** {{subject_area}} — if not provided, infer from the domain.
**Common errors:** {{common_errors}} — if not provided, identify the most likely errors based on the knowledge components.
**Mastery threshold:** {{mastery_threshold}} — if not provided, use P(Lₙ) ≥ 0.95 (approximately 3-4 consecutive correct applications).
**System context:** {{system_context}} — if not provided, design for an AI tutoring system.

Return your output in this exact format:

## Cognitive Tutoring Architecture: [Skill Domain]

**Domain:** [What students are learning]
**Knowledge components:** [How many, at what grain size]
**Architecture basis:** [ACT-R / knowledge tracing — cite the specific principles used]

### Knowledge Component Map

[Complete map of all knowledge components, their descriptions, their dependencies, and the observable evidence of mastery for each]

| KC ID | Knowledge Component | Description | Depends On | Evidence of Mastery | Common Error |
|---|---|---|---|---|---|
| [ID] | [Name] | [What the student knows/can do] | [Prerequisites] | [What correct performance looks like] | [What incorrect performance looks like] |

### Dependency Graph

[Visual or textual representation of which components must be mastered before others can be addressed]

### Knowledge Tracing Design

[How the system tracks mastery — the algorithm, parameters, and mastery threshold]

### Problem Selection Logic

[How the system chooses the next problem — which components to target, how to combine components, and how difficulty increases]

### Feedback Architecture

[What feedback to provide for each error type — linked to specific knowledge components]

### Example Tutoring Sequence

[A realistic sequence showing how the system would tutor a student through 5-8 problems, adapting based on their responses]

**Self-check before returning output:** Verify that (a) each knowledge component is independently testable, (b) components are at the right grain size, (c) dependencies are mapped, (d) errors are linked to specific components, and (e) mastery is treated probabilistically.
```

## 示例输出

**情景：** *技能领域：“解一元一次方程——从一步方程（x + 5 = 12）到两步方程（3x + 5 = 20），再到两边都含未知数的方程（4x + 3 = 2x + 11）” / 知识组件：“（1）识别未知数，（2）加减互逆，（3）乘除互逆，（4）撤销运算顺序，（5）两边同时运算，（6）合并同类项，（7）将未知数移至一侧” / 学生水平：“八年级，正式代数第一学期” / 学科领域：“数学” / 常见错误：“仅从一侧相减、运算顺序错误（先除后减）、不理解 3x 表示 3 × x、合并非同类项（将 3x + 5 相加得 8x）”*

---

## 认知辅导架构：解一元一次方程

**领域：** 从一步方程到两边都含未知数的一元一次方程
**知识组件：** 7 个，位于概念-程序粒度
**架构基础：** 基于 ACT-R 的产生式规则模型（Anderson et al., 1995）与贝叶斯知识追踪（Corbett & Anderson, 1995）

### 知识组件图谱

| KC ID | 知识组件 | 描述 | 依赖前置 | 掌握证据 | 常见错误 |
|---|---|---|---|---|---|
| KC1 | 识别未知数 | 认识到 x（或任意字母）代表方程将要揭示的未知数 | 无 | 学生能说出“我们需要求出 x 的值” | 学生将 x 视为标签而非未知数；试图直接目测“猜出”答案而不写任何代数步骤 |
| KC2 | 加减互逆 | 知道 +b 的逆运算是 −b，反之亦然 | KC1 | 面对 x + 5 = 12，学生能识别“减去 5”为正确运算 | 学生该减时反而相加（或反之）；把 5 加到 12 上而非减去 |
| KC3 | 乘除互逆 | 知道 ×a 的逆运算是 ÷a，反之亦然；理解 3x 表示 3 × x | KC1 | 面对 3x = 15，学生能识别“除以 3”为正确运算 | 学生减去 3 而非除以 3；不理解 3x = 3 × x |
| KC4 | 运算顺序 | 撤销运算时，按运算优先级（BIDMAS）的反序进行——**先**撤销加减，**再**撤销乘除 | KC2, KC3 | 面对 3x + 5 = 20，学生先减去 5，再除以 3 | 学生先除以 3，得到 (3x + 5)/3 = 20/3——代数上正确但更难化简，或者只把 3x 除以 3 而出错 |
| KC5 | 两边同时运算 | 对方程一边进行的任何运算，都必须对另一边进行 | KC2, KC3 | 学生写出“3x + 5 − 5 = 20 − 5”（在**两边**都体现减法） | 学生写出“3x = 20 − 5”而未体现左边相减，或只从左边减去 5 而右边未减 |
| KC6 | 合并同类项 | 能通过合并含相同未知数的项（3x + 2x = 5x）和常数项（7 + 3 = 10）来化简表达式，且知道**不能**合并非同类项 | KC1 | 面对 3x + 2x + 5 = 20，学生正确化简为 5x + 5 = 20 | 学生合并非同类项：3x + 5 = 8x；或该合并同类项时未能合并 |
| KC7 | 移项合并未知数 | 能通过对含未知数的项施加逆运算，将未知数项移至方程一侧 | KC2, KC5 | 面对 4x + 3 = 2x + 11，学生从两边减去 2x 得到 2x + 3 = 11 | 该减去未知数项时却减去数字；或试图从同一侧同时减去 4x 和 2x |

### 依赖关系图

```
KC1（识别未知数）
├── KC2（加减互逆）
│   ├── KC4（运算顺序）← 同时也需要 KC3
│   └── KC5（两边同时运算）← 同时也需要 KC3
├── KC3（乘除互逆）
│   ├── KC4（运算顺序）← 同时也需要 KC2
│   └── KC5（两边同时运算）← 同时也需要 KC2
└── KC6（合并同类项）

KC5（两边同时运算）+ KC2 → KC7（移项合并未知数）
KC4 + KC5 + KC6 → 多步方程能力
KC4 + KC5 + KC6 + KC7 → 两边均含未知数方程能力
```

### 知识追踪设计

**算法：** 贝叶斯知识追踪（Corbett & Anderson, 1995）

**参数（初始值，按领域校准）：**

| 参数 | 数值 | 含义 |
|---|---|---|
| P(L₀) | 0.10 | 学生在任何教学前已知该组件的概率（对于新代数概念较低） |
| P(T) | 0.20 | 每次练习机会学会该组件的概率 |
| P(G) | 0.15 | 不知道却猜对的概率（多步代数中较低） |
| P(S) | 0.10 | 虽已学会但失误（滑误）的概率 |
| 掌握阈值 | 0.95 | 判定该组件已掌握的 P(Lₙ) 阈值 |

**更新规则：** 在学生每次作答涉及 KC_i 的解题步骤后：
- 若正确：P(Lₙ) = P(Lₙ₋₁)(1 - P(S)) / [P(Lₙ₋₁)(1 - P(S)) + (1 - P(Lₙ₋₁))P(G)] — 然后应用学习概率：P(Lₙ) = P(Lₙ) + (1 - P(Lₙ))P(T)
- 若错误：P(Lₙ) = P(Lₙ₋₁)P(S) / [P(Lₙ₋₁)P(S) + (1 - P(Lₙ₋₁))(1 - P(G))] — 然后应用学习概率：P(Lₙ) = P(Lₙ) + (1 - P(Lₙ))P(T)

**通俗解释：** 每次学生尝试一个步骤，系统都会更新对其是否掌握相关知识组件的信念。答对会提高掌握度估计；答错会降低估计。但系统会考虑运气猜对（P(G)）和粗心失误（P(S)），因此答对一次不足以证明掌握，答错一次也不代表完全不会。大约需要连续 3–4 次正确应用才能达到 0.95 的掌握阈值。

### 选题逻辑

**规则 1：遵守依赖关系。** 如果学生尚未掌握所有前置 KC，绝不呈现需要 KC_n 的题目。

**规则 2：瞄准最薄弱的未掌握组件。** 在满足前置条件的组件中，选择涉及当前 P(Lₙ) 最低的知识组件的题目。

**规则 3：逐步组合组件。** 从仅需 1–2 个 KC 的题目开始。随着组件被掌握，逐步引入需要同时运用 3–4 个 KC 的题目。这能控制认知负荷。

**规则 4：穿插已掌握组件。** 偶尔包含需要先前已掌握 KC 的步骤，以防遗忘并验证掌握的保持度。

**题目难度递进：**

| 等级 | 所需 KC | 示例题目 | 呈现时机 |
|---|---|---|---|
| 1 | KC1, KC2 | x + 5 = 12 | 起始 |
| 2 | KC1, KC3 | 3x = 15 | KC2 已掌握 |
| 3 | KC1, KC2, KC3, KC4, KC5 | 3x + 5 = 20 | KC2, KC3 已掌握 |
| 4 | KC1-KC6 | 3x + 2x + 5 = 20 | KC4, KC5 已掌握 |
| 5 | KC1-KC7 | 4x + 3 = 2x + 11 | KC4, KC5, KC6 已掌握 |

### 反馈架构

| 错误模式 | 可能的 KC 失效 | 反馈内容 |
|---|---|---|
| 学生试图靠猜直接得出 x | KC1 | “这个方程需要代数步骤，而不是猜测。你的目标是把 x 单独留在方程的一边。什么运算能帮到你？” |
| 学生该减时却加（或反之） | KC2 | “你在两边都加上了 5。但 x 原本就已经**加上**了 5。加 5 的**逆运算**是什么？” |
| 学生对 3x 减去 3 而不是除以 3 | KC3 | “记住：3x 表示 3 **乘以** x。要撤销乘法，你需要……？” |
| 学生在 3x + 5 = 20 中先除后减 | KC4 | “你直接先除以 3 了。但 +5 还挡在前面。试着先撤销加法——这与表达式构建时的顺序相反。” |
| 学生只对一边进行运算 | KC5 | “你从左边减去了 5。右边呢？方程就像天平——对一边做什么，就必须对另一边做同样的事。” |
| 学生写出 3x + 5 = 8x | KC6 | “你把 3x 和 5 加在一起得到 8x。但 3x 和 5 是不同类型的项——一个带 x 而另一个不带。你只能合并**同类型**的项。” |
| 学生在移项未知数时感到困惑 | KC7 | “方程**两边**都有 x：4x + 3 = 2x + 11。要解方程，先把所有含 x 的项集中到**同一边**。你怎样才能把右边的 2x 消掉？” |

### 辅导序列示例

一名学生所有组件的初始概率为 P(L₀) = 0.10。

**题目 1：** x + 8 = 15（测试 KC1, KC2, KC5）
- 学生作答：x = 15 - 8 = 7 ✓
- KC1: P(L) → 0.28, KC2: P(L) → 0.28, KC5: P(L) → 0.28

**题目 2：** x - 3 = 10（测试 KC1, KC2, KC5 — 反向运算）
- 学生作答：x = 10 + 3 = 13 ✓
- KC1: P(L) → 0.51, KC2: P(L) → 0.51, KC5: P(L) → 0.51

**题目 3：** x + 12 = 5（测试 KC1, KC2, KC5 — 负数结果）
- 学生作答：x = 5 + 12 = 17 ✗（KC2 失效——该减却加）
- 系统反馈：“你把 12 加到了 5 上。但方程写的是 x **加上** 12 等于 5。要撤销 +12，你需要做减法，而不是加法。”
- KC2: P(L) → 0.33（下降），KC5: 不更新（错误在 KC2，不在 KC5）

**题目 4：** x + 12 = 5（同一道题，重试）
- 学生作答：x = 5 - 12 = -7 ✓
- KC2: P(L) → 0.53

**题目 5：** 4x = 20（测试 KC1, KC3 — 乘除法，新 KC）
- 学生作答：x = 20 ÷ 4 = 5 ✓
- KC3: P(L) → 0.28

**题目 6：** 7x = 21（测试 KC1, KC3）
- 学生作答：x = 21 - 7 = 14 ✗（KC3 失效——该除却减）
- 系统反馈：“7x 表示 7 **乘以** x。要撤销乘以 7，你需要做除法，而不是减法。”
- KC3: P(L) → 0.17

[序列继续：当 KC2 和 KC3 达到掌握阈值（约 0.95）后，系统引入需要 KC4 和 KC5 的两步方程……]

---

## 已知局限

1. **知识组件的拆解是一门艺术，而非纯科学。** 不同研究者对同一领域的拆解方式各异。Anderson 等人的 ACT-R 框架提供了理论指导，但关于粒度大小、组件边界和依赖结构的具体决策需要领域专业知识与迭代测试。上述拆解是一个合乎原则的起点，而非经过验证的认知模型。

2. **标准知识追踪假设知识状态是二元的。** Corbett & Anderson（1995）的模型假定每个 KC 要么“已学会”要么“未学会”。在现实中，知识存在于连续谱上：学生可能部分理解逆运算，能在简单情境中正确应用，却在复杂情境中失败。更先进的模型（例如使用神经网络的深度知识追踪 Deep Knowledge Tracing）解决了这一问题，但牺牲了可解释性。

3. **兰德公司（RAND）评估显示的效应量较为温和。** Pane 等人（2014）发现 Cognitive Tutor Algebra I 提升了成绩，但效应量相对较小（实施第二年为 0.22）。实际意义取决于具体情境：较小的平均效应可能掩盖了对特定学生亚群的更大效应。实施保真度（implementation fidelity）是一个重要调节变量。

4. **认知辅导系统最适用于结构良好的领域。** 线性方程、化学方程式配平等程序性领域可以清晰地拆解为知识组件。结构不良的领域（如议论文写作、历史分析、创意任务）则难以做此类拆解。认知辅导架构功能强大，但存在领域局限。
