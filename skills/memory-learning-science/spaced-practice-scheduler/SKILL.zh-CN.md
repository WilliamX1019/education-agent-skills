---
# AGENT SKILLS STANDARD FIELDS (v2)
name: spaced-practice-scheduler
description: "为任意主题列表与时间表设计间隔提取进度表。适用于规划单元教学、学期序列或复习方案。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "memory-learning-science/spaced-practice-scheduler"
skill_name: "间隔练习进度表生成器"
domain: "memory-learning-science"
version: "1.0"
evidence_strength: "strong"
evidence_sources:
  - "Ebbinghaus (1885/1913) — The forgetting curve: exponential decay of memory without review"
  - "Cepeda et al. (2006) — Quantitative synthesis of 317 experiments in 184 articles on distributed practice in verbal recall: effective spacing depends on the retention interval"
  - "Kornell & Bjork (2008) — Spacing and interleaving effects on learning"
  - "Carpenter et al. (2012) — Using spacing to enhance diverse forms of learning"
  - "Dunlosky et al. (2013) — Distributed practice rated high-utility learning strategy"
input_schema:
  required:
    - field: "topics"
      type: "array"
      description: "需要在进度表中进行间隔安排的主题或概念列表"
    - field: "timeline"
      type: "string"
      description: "可用教学周期（如“6周半学期”或“第2学期：1月15日–3月28日”）"
    - field: "lessons_per_week"
      type: "integer"
      description: "该学科每周的课时数"
  optional:
    - field: "assessment_date"
      type: "string"
      description: "如已知，终结性评估的日期——影响最终间隔周期"
    - field: "topic_difficulty"
      type: "array"
      description: "教师对各主题相对难度的估计（高/中/低）"
    - field: "curriculum_sequence"
      type: "array"
      description: "来自上下文引擎：规定的教学顺序或前置依赖"
    - field: "student_profiles"
      type: "array"
      description: "来自上下文引擎：来自先前评估的班级层面记忆保持数据"
output_schema:
  type: "object"
  fields:
    - field: "schedule"
      type: "array"
      description: "展示新课教学与间隔复习时段的分周进度表"
    - field: "spacing_rationale"
      type: "string"
      description: "解释为什么将主题间隔安排在这些时间点"
    - field: "review_activity_suggestions"
      type: "array"
      description: "每个复习时段的简短提取活动建议"
    - field: "teacher_guidance"
      type: "string"
      description: "如何实施该进度表并根据学生反馈进行调整"
chains_well_with:
  - "retrieval-practice-generator"
  - "interleaving-unit-planner"
  - "formative-assessment-technique-selector"
  - "lesson-opening-designer"
teacher_time: "5 分钟"
tags: ["spacing", "memory", "planning", "forgetting-curve", "distributed-practice"]
---

# 间隔练习进度表生成器

## 本技能的功能

接收一份主题列表与教学时间线，生成一份实用的复习进度表，将提取机会分散在时间轴上，并以可调整的递增间隔作为起始模式。输出是一份分周计划，明确何时引入新内容、何时重温先前主题，并为每个复习时段提供具体的活动建议。AI 在此处具有独特价值，因为在遵守前置依赖与课表约束的同时协调多个主题的复习间隔确实相当复杂——大多数教师默认采用集中分块练习（讲完主题 A，进入主题 B，永不回头），正是因为手动规划间隔进度表的认知负荷过高。

## 循证基础

Ebbinghaus（1885/1913）记录了特定实验条件下的遗忘规律；这并未确立课堂学习在24小时内必然流失的通用百分比，也未确立适用于所有材料的单一衰减函数。Cepeda 等人（2006）综合了184篇文章中的317项言语回忆分布式练习实验。最有效的学习间隔随保持时间目标而变化，更长的保持目标通常需要更长的间隔。该结果并未确立通用的 10–20% 规则或下文使用的精确递增课堂时间表。Carpenter 等人（2012）将这些发现拓展到多样化的课堂学习情境，表明间隔练习有益于陈述性知识、程序性技能和问题解决。Kornell 与 Bjork（2008）证明，间隔练习在学习者主观上感觉效果更差——即便间隔练习带来了更好的记忆保持，学生仍认为集中练习更有效。这意味着教师应预料到学生起初会更偏爱（并要求）效果较差的方法。Dunlosky 等人（2013）在其全面综述中将分布式练习评为仅有的两项“高效用”策略之一。

## 输入模式

教师必须提供：
- **主题：** 需要进行间隔安排的主题列表。*例如：["细胞结构", "细胞运输", "细胞分裂", "酶", "生物分子"]*
- **时间线：** 可用教学周期。*例如：“8周学期，自2月3日起”*
- **每周课时数：** 每周几节课。*例如：3*

可选（如有，由上下文引擎注入）：
- **评估日期：** 终结性评估的时间——用于锚定最终复习周期
- **主题难度：** 教师对各主题相对难度的估计，以便高难度主题获得更多复习时段
- **课程顺序：** 规定顺序或前置约束
- **学生档案：** 来自先前评估的班级层面保持率数据

## 提示词

```
You are an expert in the cognitive psychology of memory, specialising in the spacing effect and distributed practice. You have deep knowledge of Cepeda et al.'s (2006) meta-analysis on optimal inter-study intervals, Ebbinghaus's forgetting curve, and Carpenter et al.'s (2012) work on spacing in educational contexts.

Your task is to generate a spaced practice schedule for the following:

**Topics:** {{topics}}
**Timeline:** {{timeline}}
**Lessons per week:** {{lessons_per_week}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Assessment date:** {{assessment_date}} — if provided, ensure all topics have at least one retrieval opportunity in the final week before the assessment. If not provided, design the schedule for long-term retention without a specific deadline.
**Topic difficulty ratings:** {{topic_difficulty}} — if provided, allocate more review slots to high-difficulty topics. If not provided, treat all topics as roughly equal difficulty unless your subject knowledge suggests otherwise.
**Required teaching order:** {{curriculum_sequence}} — if provided, respect prerequisite dependencies. If not provided, assume topics can be taught in the order listed.
**Class retention data:** {{student_profiles}} — if provided, weight additional review toward topics where prior data shows weak retention. If not provided, use the provisional expanding pattern below and invite adjustment after the first review.

Apply these research-informed principles and labelled scheduling heuristics. Spacing is supported; the exact intervals, minute allocations, maximum gaps and re-teaching thresholds below are practitioner starting points, not validated optima. Do not infer a universal daily forgetting percentage from Ebbinghaus.

1. **Adaptable intervals:** As a practical starting pattern, try a first review at 1–3 days after initial teaching, a second at 1–2 weeks, and a third at 3–4 weeks if the timeline permits. Cepeda et al. (2006) relates effective gaps to the intended retention interval; it does not establish this precise sequence or require successively expanding gaps for every learner. Adjust using actual recall, topic demands, timetable and retention goals, explaining departures.

2. **Review through retrieval, not re-teaching:** Each review slot should involve a retrieval activity (quiz, brain dump, diagram from memory), NOT re-teaching or re-reading. The learning happens through the retrieval attempt (Roediger & Butler, 2011).

3. **New teaching to review ratio:** In any given lesson, approximately 10–15 minutes should be available for retrieval of previously taught material (typically the lesson opening). New content occupies the main teaching portion.

4. **Interleaving where appropriate:** When topics share a domain, mix review questions from different topics in the same retrieval session. This produces an interleaving effect (Rohrer et al., 2015) that improves discrimination between similar concepts.

5. **Difficulty-weighted spacing:** Topics rated as more difficult should receive more frequent review slots. Topics with strong initial encoding may need fewer.

6. **Pre-assessment consolidation:** If an assessment date is provided, ensure every topic has at least one retrieval opportunity in the 5 days before the assessment — but do NOT cram all review into the final week. That defeats the purpose of spacing.

Return your output in this exact format:

## Spaced Practice Schedule: [Subject/Context]

**Timeline:** [Start to end]
**Topics:** [List]
**Total lessons:** [Number]

### Week-by-Week Schedule

For each week, provide:
| Lesson | New Content | Spaced Review (10–15 min starter) |
|--------|------------|-----------------------------------|
| [Day]  | [Topic]    | [Which previous topic(s) to retrieve + brief activity type] |

### Spacing Rationale

Explain in 3–4 sentences why the topics are spaced at these specific intervals, referencing the evidence base.

### Review Activity Suggestions

For each review slot, suggest a specific brief retrieval activity (not "review Topic X" but "5 free-recall questions on cell transport mechanisms" or "label a blank diagram of cell structure from memory").

### Teacher Guidance

- How long each review starter should take
- What to do when review reveals gaps (re-teach briefly vs. schedule additional retrieval)
- How to explain the purpose to students (they will feel like spaced practice is less effective — this is normal)

**Self-check before returning output:** Verify that (a) gaps beyond the suggested 3-week planning target are explained, (b) intervals fit the retention goal and available lessons, with any expanding pattern identified as a heuristic, (c) harder topics get more review slots, (d) the schedule is realistic given the lessons-per-week constraint, and (e) review activities involve retrieval, not re-reading or re-teaching.
```

## 示例输出

**场景：** *主题：["构造板块", "地震", "火山", "风化与侵蚀", "河流地貌"] / 时间线：“6周半学期，每周5节课” / 每周课时数：5 / 评估日期：“第6周周末”*

---

## 间隔练习进度表：八年级地理——自然地貌

**时间线：** 第1–6周（共30节课）
**主题：** 构造板块、地震、火山、风化与侵蚀、河流地貌
**总课时数：** 30

### 分周进度表

| 周次 | 课时 | 新授课内容 | 间隔复习导入（10–15分钟） |
|------|--------|-------------|-----------------------------------|
| 1 | 1 | 构造板块——地球内部圈层结构 | —（基线评估：学生已经知道什么？） |
| 1 | 2 | 构造板块——板块边界 | 提取：凭记忆绘制地球圈层简图，标注并注释 |
| 1 | 3 | 构造板块——对流作用 | 提取：说出3种板块边界类型及每种类型的一个特征 |
| 1 | 4 | 地震——成因及震源/震中 | 提取：用3句话解释对流作用如何驱动板块运动 |
| 1 | 5 | 地震——测量与影响 | 提取：绘制并标注展示震源、震中与地震波的示意图 |
| 2 | 1 | 地震——案例研究 | 提取：**构造板块**——关于板块边界的5道自由回忆题（主题复习，距首次引入约7天；此前导入课也已提取过该主题） |
| 2 | 2 | 火山——形成与类型 | 提取：凭记忆对比两个地震案例——成因、影响、应对措施 |
| 2 | 3 | 火山——喷发过程 | 混合提取：3题**构造板块** + 2题**地震测量** |
| 2 | 4 | 火山——案例研究 | 提取：凭记忆绘制复式火山剖面图，标注5个特征 |
| 2 | 5 | 火山——与火山风险共存 | 提取：**地震**全主题——“5分钟内写下你关于地震所知道的一切”（头脑倾倒） |
| 3 | 1 | 风化与侵蚀——风化类型 | 混合提取：4题穿插**构造板块**与**火山**（距首次引入约2周；第2周也曾复习） |
| 3 | 2 | 风化与侵蚀——侵蚀过程 | 提取：凭记忆说出并解释3种风化类型 |
| 3 | 3 | 风化与侵蚀——侵蚀 vs 风化 | 提取：**火山**——空白图：标注火山特征并解释形成过程 |
| 3 | 4 | 河流地貌——纵剖面与河流作用 | 混合提取：区分风化与侵蚀 + 2题**地震影响** |
| 3 | 5 | 河流地貌——上游地貌特征 | 提取：**风化与侵蚀**——凭记忆解释4种河流侵蚀类型 |
| 4 | 1 | 河流地貌——中游地貌特征 | 混合提取：2题**构造板块** + 2题**火山** + 1题**风化**（穿插，距引入约3周） |
| 4 | 2 | 河流地貌——下游地貌特征 | 提取：凭记忆绘制并注释河流纵剖面图 |
| 4 | 3 | 河流地貌——洪水 | 提取：**地震**——对比两个案例 + 解释一种测量标度 |
| 4 | 4 | 河流地貌——防洪治理 | 混合提取：3题**河流作用** + 2题**侵蚀类型** |
| 4 | 5 | 巩固/深化课 | 全面穿插小测：横跨全部5个主题的10道题（每主题2题，打乱顺序） |
| 5 | 1 | 拓展写作：比较自然地理过程 | 提取：**河流地貌**——凭记忆速写上/中/下游地貌特征 |
| 5 | 2 | 案例深化：自选主题 | 混合提取：5题穿插**火山**、**风化**、**河流** |
| 5 | 3 | 主题间的联系 | 提取：**构造板块**——完整自由回忆（距引入约4周；属于计划性重温，而非已确立的临界间隔） |
| 5 | 4 | 应试技巧：运用案例研究 | 混合提取：横跨全部5个主题的6道题，聚焦常混淆概念 |
| 5 | 5 | 模拟评估 | 提取：模拟评估前针对全部5个主题进行每题1分钟快问快答 |
| 6 | 1 | 基于模拟评估缺口的复习 | 针对模拟评估数据中最薄弱的2个主题进行定向提取 |
| 6 | 2 | 定向深化：最薄弱主题 | 提取：模拟评估中第二薄弱的主题 |
| 6 | 3 | 定向深化：第二薄弱主题 | 混合穿插提取：全部5个主题，侧重缺口领域 |
| 6 | 4 | 最终巩固 | 全面头脑倾倒：12分钟内写出关于全部5个主题所知的一切 |
| 6 | 5 | **终结性评估** | — |

### 间隔学理依据

这一示范性时间表将复习分布在整个学期中，与 Cepeda 等人（2006）关于间隔效应的总体证据一致。它采用早期高频提取与后期每周重温的安排；并非严格的递增间隔表，也非实证最优表。板块构造题目的重复出现也意味着，距首次教学的时间并不等同于距最近一次提取的间隔。在需要对比的场景下采用了跨主题混合复习，且第6周的复习应依据模拟评估的实际数据而非预设班级表现进行调整。

### 复习活动建议

- **头脑倾倒（Brain dump）：** “5分钟内写下你关于[主题]知道的一切。不看笔记。”要求最高——用于教学结束2周及以上的主题。
- **空白填图：** “凭记忆绘制并标注[具体图表]。”非常适合空间/过程类知识。
- **自由回忆题：** 5道需要凭记忆书面作答的简答题，耗时 8–10 分钟。
- **穿插小测：** 以随机顺序混合3个以上主题的问题，迫使学生辨别相似概念。
- **纠错练习：** 提供一段包含 3–4 处刻意错误的文字，学生凭记忆识别并改正。

### 教师指南

- 每次复习导入最多耗时 **10–15 分钟**。它替代的是传统课堂导入，而非主体新授课。
- **当复习暴露知识缺口时：** 作为一项示范性决策启发法，若超过 40% 的学生无法回忆出某一概念，可考虑进行简短重教（约5分钟）并在约3天后安排另一次提取机会。这些百分比与时间并非经过验证的绝对阈值；请结合错误性质与可用教学时间判断是否需要更完整的重新讲授。
- **向学生解释目的：** “这会感觉比重读笔记更难，你甚至可能觉得自己学得没那么扎实。仅有努力感并不能证明学习发生。我们会核对答案、纠正错误并调整进度表，让练习始终保持效用。”
- **保持复习导入的低风险性。** 用答案来指导反馈与后续教学，而非给学生排名。

---

## 已知局限

1. **进度表假设各主题篇幅相对均衡。** 如果某个主题需要8节课的新授而另一个只需2节，间隔周期将会不均。教师需要根据实际主题权重调整进度表——本工具提供的是起步框架，而非僵化计划。

2. **Cepeda 等人（2006）主要综述的是实验室言语回忆任务，而非这一具体课堂时间表。** 向复杂程序性技能（如数学解题、论文写作）的迁移证据相对较少，尽管 Carpenter 等人（2012）提供了支持性的课堂证据。

3. **进度表未计入学校突发日程变动**（集会、实地考察、停课、教师缺勤）。当变动发生时，教师应将进度表视为目标模式，顺延复习时段，而不是直接跳过。
