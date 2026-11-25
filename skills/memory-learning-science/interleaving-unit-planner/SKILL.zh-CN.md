---
# AGENT SKILLS STANDARD FIELDS (v2)
name: interleaving-unit-planner
description: "将分块主题序列重新设计为穿插计划，实现相关主题间的混合练习。适用于规划单元、家庭作业进度表或复习方案。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "memory-learning-science/interleaving-unit-planner"
skill_name: "穿插式单元规划器"
domain: "memory-learning-science"
version: "1.0"
evidence_strength: "strong"
evidence_sources:
  - "Kornell & Bjork (2008) — Learning concepts and categories: is spacing the enemy of induction?"
  - "Rohrer et al. (2015) — Interleaved practice improves mathematics learning in a classroom setting"
  - "Taylor & Rohrer (2010) — The effects of interleaved practice on learning"
  - "Bjork & Bjork (2011) — Making things hard on yourself, but in a good way: creating desirable difficulties"
  - "Pan (2015) — The interleaving effect: mixing it up boosts learning"
input_schema:
  required:
    - field: "topics"
      type: "array"
      description: "当前按分块顺序规划的主题序列"
    - field: "subject"
      type: "string"
      description: "学科领域与年级"
    - field: "unit_length"
      type: "string"
      description: "该单元涵盖的课时数或周数"
  optional:
    - field: "prerequisite_dependencies"
      type: "array"
      description: "必须在其他主题之前教授的主题（硬性约束）"
    - field: "curriculum_sequence"
      type: "string"
      description: "来自上下文引擎：规定的课程顺序"
    - field: "student_profiles"
      type: "array"
      description: "来自上下文引擎：班级能力画像、先验知识水平"
output_schema:
  type: "object"
  fields:
    - field: "interleaved_sequence"
      type: "array"
      description: "应用了穿插策略的重构课时序列"
    - field: "interleaving_rationale"
      type: "string"
      description: "为什么这些特定主题能从穿插中获益"
    - field: "teacher_briefing"
      type: "string"
      description: "如何向觉得练习更难的学生解释这一方法"
    - field: "blocked_vs_interleaved"
      type: "string"
      description: "原始序列与穿插序列的并排对比"
chains_well_with:
  - "spaced-practice-scheduler"
  - "retrieval-practice-generator"
  - "practice-problem-sequence-designer"
  - "cognitive-load-analyser"
teacher_time: "5 分钟"
tags: ["interleaving", "desirable-difficulty", "planning", "memory", "practice"]
---

# 穿插式单元规划器

## 本技能的功能

接收一个分块主题序列（主题 A, A, A，然后主题 B, B, B），并将其重构为穿插相关但不同概念的序列（A, B, A, C, B, A...），从而生成能够利用“穿插效应”提升长期保持率与相似概念辨别力的教学计划。输出包括重构后的计划、穿插这些特定主题的学理依据，以及向学生解释该方法的指导话术。AI 在此处具有独特价值，因为实施穿插需要识别哪些主题能从穿插中获益（相关但不同的概念）、哪些必须保持分块（真正的前置知识）以及如何编排穿插模式——这项任务需要同时理解认知科学与具体学科内容。

## 循证基础

Kornell 与 Bjork（2008）证明，穿插学习不同类别（相对于分块学习每一类别）使随后的分类准确率提高了 30–40%，尽管学生主观认为分块学习更有效。Rohrer 等人（2015）在真实数学课堂中证实了这些发现：进行穿插习题练习的学生在延迟测试中的得分比进行分块练习的学生高出 25%。Taylor 与 Rohrer（2010）表明，穿插的益处对于需要**辨别**的任务尤为显著——即知道该应用哪种策略或概念，而不仅仅是知道如何应用它。Bjork 与 Bjork（2011）将穿插解释为一种“合意困难”（desirable difficulty）——它使初始学习感觉更困难、更缓慢，但能带来显著更好的长期保持与迁移。关键在于，穿插之所以有效，是因为它迫使学习者在每次练习尝试时都必须辨别相似概念，而不是因为身处某主题的“专块”中就提前知道了答案类型。

## 输入模式

教师必须提供：
- **主题：** 当前按计划顺序排列的主题序列。*例如：["分数——加法", "分数——减法", "分数——乘法", "分数——除法"]*
- **学科：** 学科领域与年级。*例如：“八年级数学”*
- **单元时长：** 单元持续时间。*例如：“4周共12节课”*

可选（如有，由上下文引擎注入）：
- **前置依赖关系：** 必须排在其他主题之前的主题。*例如：“加法必须先于减法”*
- **课程顺序：** 学校教学大纲规定的任何顺序
- **学生档案：** 班级能力画像与先验知识数据

## 提示词

```
You are an expert in the cognitive psychology of learning, specialising in the interleaving effect and desirable difficulties. You have deep knowledge of Kornell & Bjork (2008), Rohrer et al. (2015), and Taylor & Rohrer (2010) on how interleaved practice improves discrimination and long-term retention compared to blocked practice.

Your task is to restructure the following blocked topic sequence into an interleaved plan:

**Subject:** {{subject}}
**Current blocked sequence:** {{topics}}
**Unit length:** {{unit_length}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Prerequisite constraints:** {{prerequisite_dependencies}} — if provided, these are hard constraints: do not interleave a topic before its prerequisite has been taught. If not provided, infer likely prerequisites from the topic content and flag your assumptions.
**Mandated sequence:** {{curriculum_sequence}} — if provided, respect this where possible and explain any deviations. If not provided, treat the listed topic order as the teacher's preferred sequence.
**Student profiles:** {{student_profiles}} — if provided, adjust the density of interleaving based on ability (lower-ability students may need more initial blocked practice before interleaving begins). If not provided, design for a typical mixed-ability class.

Apply these evidence-based principles:

1. **Interleave related but distinct concepts.** Interleaving works best when topics are related enough to require discrimination but distinct enough to have different solution strategies. Topics that are entirely unrelated (e.g., fractions and Shakespeare) don't benefit — there's no discrimination challenge. Topics that are almost identical (e.g., two lessons on the same sub-skill) should stay blocked during initial instruction.

2. **Teach before interleaving.** Each topic needs initial instruction in a focused block (typically 1–2 lessons) before it enters the interleaved rotation. Interleaving is a practice strategy, not an instruction strategy. Students need to understand each concept individually before being asked to discriminate between them.

3. **Introduce interleaving progressively.** Start with 2-topic interleaving, then add topics as students become comfortable. Don't interleave all topics simultaneously from lesson 1.

4. **Expect it to feel harder.** Kornell & Bjork (2008) found that students rated blocked practice as more effective even when interleaved practice produced better outcomes. Build in a brief explanation for students about why this approach feels harder but works better.

5. **Respect prerequisite dependencies.** Some topics genuinely require prior knowledge of another topic. These must stay in sequence. Interleave around constraints, not through them.

6. **Include discrimination practice.** The key benefit of interleaving is forcing students to decide WHICH strategy or concept applies, not just HOW to apply it. Include mixed-practice tasks where students must first identify the problem type.

Return your output in this exact format:

## Interleaved Unit Plan: [Subject/Unit Title]

### Original Blocked Sequence vs. Interleaved Sequence

A side-by-side comparison showing the original plan and the restructured plan.

### Interleaved Lesson Sequence

For each lesson, show:
- **Lesson [N]:** [Primary teaching focus] + [Interleaved practice from previous topic(s)]
- Note which topics are being interleaved in practice tasks

### Interleaving Rationale

3–4 sentences explaining why these specific topics benefit from interleaving, what discrimination challenge it creates, and what the expected benefit is.

### Student Briefing Script

A 4–5 sentence script the teacher can use to explain to students why the practice feels harder and why that's productive.

### Practice Task Examples

For 2–3 lessons, provide specific interleaved practice tasks that force discrimination between topics.

**Self-check before returning output:** Verify that (a) prerequisite dependencies are respected, (b) each topic receives initial blocked instruction before entering interleaved practice, (c) the interleaving is between related concepts that require discrimination, (d) mixed practice tasks require students to identify the problem type, not just solve it, and (e) the plan is realistic for the given number of lessons.
```

## 示例输出

**场景：** *主题：["三角形面积", "平行四边形面积", "梯形面积", "组合图形面积"] / 学科：“八年级数学” / 单元时长：“2.5周共10节课” / 前置依赖：“组合图形需要先掌握全部三种单一图形”*

---

## 穿插式单元计划：八年级数学——平面图形的面积

### 原始分块序列 vs. 穿插序列

| 课时 | 分块（原始） | 穿插（重构后） |
|--------|-------------------|---------------------------|
| 1 | 三角形面积 | 三角形面积——初始教学 |
| 2 | 三角形面积 | 三角形面积——练习 + 引入平行四边形 |
| 3 | 三角形面积 | 平行四边形面积——初始教学 |
| 4 | 平行四边形面积 | 混合练习：三角形与平行四边形 |
| 5 | 平行四边形面积 | 梯形面积——初始教学 |
| 6 | 平行四边形面积 | 混合练习：三角形、平行四边形、梯形 |
| 7 | 梯形面积 | 辨别挑战：“哪个公式？哪种图形？” |
| 8 | 梯形面积 | 组合图形面积——初始教学 |
| 9 | 组合图形面积 | 混合练习：四种图形全穿插 |
| 10 | 组合图形面积 | 评估：穿插习题集 |

### 穿插课时序列

**第 1 课：** 教授三角形面积（底 x 高 / 2）。聚焦分块练习——10道样例和10道独立练习题。在开始穿插之前，学生需要对公式达到熟练程度。

**第 2 课：** 简要回顾三角形（5分钟提取），随后引入平行四边形面积（底 x 垂直高）。最后10分钟：6道练习题——3道三角形、3道平行四边形，打乱顺序。学生必须识别图形类型并选择正确公式。

**第 3 课：** 深入教授平行四边形面积。进行平行四边形的分块练习，包括必须从图形中识别垂直高的题目（常见错误来源）。

**第 4 课——首次全面穿插课：** 不讲新内容。混合练习集：12道随机排序的三角形与平行四边形题目。关键在于，部分题目以非常规方向呈现图形，或带有必须忽略的额外测量数据。学生必须（1）识别图形，（2）选择公式，（3）找出正确测量值，（4）计算。

**第 5 课：** 教授梯形面积（(a + b) / 2 x h）。聚焦分块练习。强调梯形公式与三角形/平行四边形公式之间的关系。

**第 6 课——三主题穿插：** 混合练习：15道穿插全部三种图形的题目。包含外观相似的图形（例如朝向看起来像梯形的平行四边形）。最后5分钟：学生在计算前先将10个图形分类。

**第 7 课——辨别挑战：** “哪个公式？哪种图形？”学生拿到20道题。前10题**不计算**——只识别图形类型并写出正确公式。后10题进行识别并计算。这单独强化了穿插所培养的辨别技能。

**第 8 课：** 教授组合图形面积。演示如何将组合图形分解为三角形、平行四边形和梯形。针对分解策略进行分块练习。

**第 9 课——全面穿插：** 15道混合题：单一图形（需要选择公式）和组合图形（需要分解 + 选择公式）。随机排序。

**第 10 课——评估：** 包含所有四种图形类型且随机排序的穿插评估，包括组合图形。这同时测试计算技能与穿插所建立的辨别能力。

### 穿插学理依据

这四个主题非常适合穿插，因为它们具有相似的表层结构（平面图形、底、高、面积公式），但需要不同的解题策略。核心辨别挑战在于：给定一个图形，适用哪个公式？在分块练习中，学生从不面临这一决策——他们知道每道题都用同一个公式，因为他们正处于“平行四边形这一章”。穿插迫使学生在每一道题上都做出决策，而这正是他们在任何考试或现实应用中都会面临的挑战。Rohrer 等人（2015）发现，这种特定类型的数学穿插在延迟测试中带来了 25% 的成绩提升。

### 学生动员话术

“接下来的几节课，我们要把练习打乱混合，而不是先做完所有三角形题目，再做所有平行四边形题目。这会让人感觉更难——你们可能会觉得自己错得更多、学得更少。但实际上，这正是大脑在更努力工作的信号，因为你们必须思考**使用哪种方法**，而不仅仅是如何套用。Doug Rohrer 教授团队的研究表明，用这种方式练习的学生在几周后的测试中得分高出 25%，尽管他们在练习时感觉没那么自信。相信这个过程——这种困难正是意义所在。”

### 练习任务示例

**第 4 课——混合练习集（样例）：**
1. 求底为 8 cm、高为 5 cm 的三角形面积。
2. 求底为 12 cm、垂直高为 4 cm 的平行四边形面积。
3. 一个三角形底为 6.5 cm、高为 9 cm，计算其面积。
4. 求该平行四边形的面积。[图示一个底 10 cm、斜边 7 cm、垂直高 6 cm 的平行四边形——学生必须忽略斜边]
5. 画有一个三角形，标有尺寸 4 cm、7 cm 及高 3.5 cm。哪个测量值是不需要的？计算面积。
6. 求底为 15 cm、高为 8 cm 的平行四边形面积。

**第 7 课——纯辨别任务（样例）：**
“针对下方每个图形，**不要**计算。请写出：（a）图形类型，（b）正确公式，（c）你会使用图中的哪些测量值。”
[10个不同朝向的图形，标有多个测量值，包含无关数据]

---

## 已知局限

1. **穿插是一种练习策略，而非初始教学策略。** 本技能重构练习序列，但不能提升初始教学的质量。如果学生在初始分块教学后仍未理解某个概念，将该概念与其他概念穿插只会增加混淆，而非促进学习。穿插前务必先检查理解情况。

2. **实证基础在数学与类别学习任务中最为坚实。** Rohrer 等人（2015）和 Taylor 与 Rohrer（2010）使用的是数学和知觉分类任务。向人文学科（如穿插不同体裁写作、历史时期）的迁移虽有理论支持，但直接实验证据较少。在数学与科学之外使用时需保持审慎。

3. **学生有时甚至同事可能会产生抵触。** Kornell 与 Bjork（2008）一致发现，学习者主观认为分块练习更有效。教师可能会遇到来自学生的抱怨（“太乱了”）、家长的质疑（“怎么跳来跳去的”）以及同事的反对（“他们得先精通一个主题才能学下一个”）。学生动员话术是必需的，而非可选项。
