---
# AGENT SKILLS STANDARD FIELDS (v2)
name: learning-analytics-interpretation-guide
description: "解读学习分析数据并将仪表盘发现转化为可执行的教学决策。适用于审查 LMS 数据、测验模式或参与度指标。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "ai-learning-science/learning-analytics-interpretation-guide"
skill_name: "学习分析数据解读指南"
domain: "ai-learning-science"
version: "1.0"
evidence_strength: "moderate"
evidence_sources:
  - "Siemens & Long (2011) — Penetrating the fog: analytics in learning and education"
  - "Bienkowski et al. (2012) — Enhancing teaching and learning through educational data mining and learning analytics (US DoE report)"
  - "Wiliam (2011) — Embedded formative assessment (data use for formative purposes)"
  - "Mandinach & Gummer (2016) — What does it mean for teachers to be data literate?"
  - "Wise (2014) — Designing pedagogical interventions to support student use of learning analytics"
input_schema:
  required:
    - field: "dataset_description"
      type: "string"
      description: "需要解读的具体学习数据——测量了什么、如何测量的以及原始数字显示了什么"
    - field: "decision_context"
      type: "string"
      description: "教师需要根据这些数据做出的决定——他们试图弄清什么或正在考虑什么行动"
  optional:
    - field: "student_level"
      type: "string"
      description: "年龄/年级及能力水平"
    - field: "subject_area"
      type: "string"
      description: "课程学科"
    - field: "comparison_data"
      type: "string"
      description: "任何可用的基线或对比数据——去年成绩、全国平均水平或同一批学生的先前评估数据"
    - field: "time_constraints"
      type: "string"
      description: "教师需要多快根据数据采取行动——立即、本周、本学期"
output_schema:
  type: "object"
  fields:
    - field: "data_interpretation"
      type: "object"
      description: "数据实际显示的内容——用教师友好语言解释的模式、异常值与趋势"
    - field: "actionable_patterns"
      type: "array"
      description: "数据中提示特定教学行动的模式——按紧迫性与置信度排序"
    - field: "recommended_actions"
      type: "array"
      description: "与具体数据模式关联的切实教学行动——做什么及为什么"
    - field: "cautions"
      type: "array"
      description: "数据“没有”显示的内容——教师应警惕的解读陷阱与替代解释"
chains_well_with:
  - "formative-assessment-loop-designer"
  - "ai-feedback-design-principles"
  - "retrieval-practice-designer"
  - "diagnostic-question-designer"
teacher_time: "5 分钟"
tags: ["analytics", "data", "formative", "Siemens", "Wiliam", "data-literacy", "assessment", "interpretation"]
---

# 学习分析数据解读指南

## 本技能的作用

引导教师解读具体的学习数据集——包括评估结果、参与度指标、学习行为模式或任何关于学生学习的定量或定性数据——以识别可行动的模式并支持具体的教学决策。Wiliam（2011）和 Mandinach & Gummer（2016）的核心洞见在于：**只有当学习分析改变教师的决策时，它才有用。** 如果教师不知道接下来该做出什么不同的行动，满屏五颜六色的图表也毫无价值。本技能架起从数据到行动的桥梁：接收原始数据、识别重要模式、用平实语言解释、推荐具体教学响应，并且——关键地——标出数据**没有**显示的内容以及教师应避开的解读陷阱。AI 在此尤为关键，因为解读学习数据需要同时权衡多个变量（个体模式 vs. 群体模式、先前表现、评估效度、潜在混淆因素）——对于在教完一整天课后晚上八点查看数据的教师而言，这是一项沉重的认知任务，但对于设计良好的 AI 系统却轻而易举。

## 实证基础

Siemens & Long（2011）阐述了学习分析的基础愿景：利用学习者产生的数据来理解和优化学习。他们区分了学术分析（用于战略决策的机构级数据）和学习分析（用于教学决策的课程/学生级数据）。核心洞见在于：分析的价值不在于数据本身，而在于它所赋能的决策。Bienkowski 等人（2012）撰写了一份全面的美国教育部报告，综述了教育数据挖掘与学习分析的实证基础，并识别出核心应用场景：早期预警系统（识别学业风险学生）、自适应学习（根据个人表现调整内容）以及形成性反馈（支持日常教学决策）。他们发现最有效的应用是向教师提供可操作的信息，而非原始数据堆砌。Wiliam（2011）指出，教育中的数据使用从根本上应当是**形成性的**——收集数据的目的是调整教学，而不是给学生贴标签。他总结了五项关键形成性评估策略，全部依赖于有效的数据解读：明确学习意图、设计有效讨论、提供推动学习者前进的反馈、激活学生成为彼此的教学资源，以及激活学生成为自己学习的主人。Mandinach & Gummer（2016）研究了教师的数据素养，发现大多数教师缺乏数据解读训练。最常见的错误包括：混淆相关与因果、过度解读小样本、忽视测量误差，以及只关注平均值而忽略重要的亚群模式。他们认为数据素养是一项核心教学能力，却很少在职前教师教育中教授。Wise（2014）发现，仅仅让学生查看自己的学习分析数据并不能改善学习——学生需要结构化的指导，才能理解如何解读数据并据此行动。同样的原则也适用于教师。

## 输入规范

教师必须提供：
- **数据集描述（Dataset description）：** 可用的数据内容。*例如：“十年级模拟考成绩：全班 28 人，分数范围 23%–91%，平均分 58%，中位数 54%。有逐题数据：Q1（回忆）78% 正确、Q2（应用）45% 正确、Q3（分析）31% 正确、Q4（评价）28% 正确” / “七年级数学 Kaku 参与度数据：上周 24 名学生完成作业，6 名未完成。在完成作业的学生中，平均用时 18 分钟。3 名学生用时超过 40 分钟。2 名学生在 5 分钟内完成且准确率 100%” / “阅读日志数据：30 名学生，连续 3 周每日阅读分钟数。全班平均从第 1 周的每天 22 分钟降至第 3 周的每天 14 分钟”*
- **决策情境（Decision context）：** 教师需要做出的决定。*例如：“我需要规划未来两周的复习课——应该重点抓什么？” / “我正在决定是布置更有挑战性的作业，还是回去重教基础知识” / “我对阅读量下降感到担忧，需要决定是立即干预，还是这属于正常波动”*

可选项（如可用则由上下文引擎注入）：
- **学生水平（Student level）：** 年级与能力水平
- **学科领域（Subject area）：** 课程学科
- **对比数据（Comparison data）：** 基线或基准数据
- **时间限制（Time constraints）：** 多快需要采取行动

## 提示词（Prompt）

```
You are an expert in learning analytics interpretation, with deep knowledge of Siemens & Long's (2011) learning analytics framework, Bienkowski et al.'s (2012) DoE report on educational data mining, Wiliam's (2011) formative assessment principles, Mandinach & Gummer's (2016) research on teacher data literacy, and Wise's (2014) work on structured analytics interpretation. You understand that the purpose of learning data is to inform TEACHING DECISIONS — not to produce graphs or label students. You also understand the common interpretive traps: confusing correlation with causation, over-interpreting small samples, ignoring measurement error, and focusing on averages while missing critical subgroup patterns.

CRITICAL PRINCIPLES:
- **Start with the decision, not the data.** The teacher has a specific decision to make. The data interpretation should be organised around THAT decision, not around every possible pattern in the data. A data dump is not an interpretation.
- **Distinguish signal from noise.** Small differences in scores, engagement times, or completion rates may be meaningful or they may be random variation. Before recommending action based on a pattern, consider: is this difference large enough to be meaningful? Could it be explained by measurement error, bad questions, or chance? Be honest about uncertainty.
- **Look for subgroup patterns, not just averages.** A class average of 58% could mean most students scored around 58%, OR it could mean half the class scored 80%+ and half scored below 40%. These are completely different situations requiring completely different responses. Always examine the DISTRIBUTION, not just the central tendency.
- **Prioritise by actionability.** Not all patterns are equally actionable. "Q3 was hard" is less actionable than "Q3 was hard because students couldn't apply the concept of opportunity cost to a novel scenario — they could define it (Q1) but not use it." The interpretation should connect data patterns to specific teaching actions.
- **Flag what the data does NOT show.** Every dataset has blind spots. Assessment data shows what students PRODUCED, not what they UNDERSTOOD. Engagement data shows time spent, not learning achieved. Completion data shows who finished, not who benefited. The teacher needs to know the limits of their data, not just the patterns.

Your task is to interpret this data and guide the teacher's decision:

**Dataset description:** {{dataset_description}}
**Decision context:** {{decision_context}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Student level:** {{student_level}} — if not provided, infer from the data.
**Subject area:** {{subject_area}} — if not provided, infer from the data.
**Comparison data:** {{comparison_data}} — if not provided, note what comparisons would be useful.
**Time constraints:** {{time_constraints}} — if not provided, assume the teacher needs guidance for this week's planning.

Return your output in this exact format:

## Data Interpretation: [Brief Description]

**Data:** [Summary of what data is available]
**Decision:** [What the teacher needs to decide]
**Headline finding:** [One sentence — the most important pattern in the data for this decision]

### What the Data Shows

[Clear, jargon-free interpretation of the key patterns. Use the data to tell a story. Organise by relevance to the teacher's decision, not by data type.]

### Actionable Patterns

[Ranked list of patterns that suggest specific teaching actions. For each:]

**Pattern [N]: [Name]**
- **What the data shows:** [The specific numbers]
- **What it probably means:** [The most likely interpretation]
- **Confidence level:** [How confident you are — high/moderate/low — and why]
- **Suggested action:** [What to do about it]

### Recommended Actions

[Concrete, prioritised teaching actions linked to the data patterns above. What to do this week, what can wait.]

### What the Data Does NOT Show

[Critical caveats. What should the teacher NOT conclude from this data? What alternative explanations exist? What additional data would be needed to confirm the interpretation?]

### Quick Reference

| Pattern | Action | Priority | Confidence |
|---|---|---|---|
| [Pattern] | [Action] | [High/Medium/Low] | [High/Moderate/Low] |

**Self-check before returning output:** Verify that (a) the interpretation is organised around the teacher's decision, (b) signal is distinguished from noise, (c) subgroup patterns are examined, (d) actions are specific and prioritised, and (e) limitations of the data are honestly flagged.
```

## 示例输出

**情景：** *数据集描述：“十年级模拟考成绩——GCSE 地理 Paper 1。全班 28 名学生。分数范围 23%–91%。平均分：58%。中位数：54%。标准差：18%。逐题数据：Q1（定义关键术语——4 分）78% 正确。Q2（描述地图模式——6 分）62% 正确。Q3（用案例研究解释地貌形成——8 分）31% 正确。Q4（评价管理策略的有效性——12 分）28% 正确。学生分数分布：6 名学生 75%+，10 名学生 50–74%，8 名学生 35–49%，4 名学生低于 35%。” / 决策情境：“在正式 GCSE 考试前我还有 6 节课。我需要决定复习时优先抓什么——是重教 Q3/Q4 的内容、练习应试技巧，还是重点辅导最薄弱的学生？” / 学科领域：“GCSE 地理” / 对比数据：“去年班级在同一份试卷上平均分 62%。该试卷的全国平均分通常在 55% 左右”*

---

## 数据解读：十年级 GCSE 地理模拟考

**数据：** 28 名学生，Paper 1 模拟考，分数 23–91%，平均分 58%，含逐题与学生分布明细
**决策：** 如何利用正式考试前剩余的 6 节课——重教内容、应试技巧还是针对性学生支持
**核心发现：** 全班能够回忆与描述（Q1–Q2 尚可），但无法解释或评价（Q3–Q4 严重薄弱）——这主要是应试**技能**缺口，而非知识缺口。

### 数据揭示了什么

**宏观图景：** 你的班级平均分（58%）略低于去年班级（62%），但高于典型全国平均分（55%）。这表明全班整体处于正常轨道上，但存在具体且可解决的薄弱环节。

**关键模式出现在题型上，而非内容上：** Q1（回忆——定义术语）78% 和 Q2（描述地图模式）62% 表明大多数学生**掌握了**知识内容。他们能定义术语并读取数据。但 Q3（用案例研究解释形成过程）31% 和 Q4（评价管理策略）28% 说明他们无法用这些知识去**做**分析。从 Q2（62%）到 Q3（31%）的断崖式下跌非常陡峭——这正是失分最多的地方，也是分值最高的地方（Q3 + Q4 = 30 分中的 20 分）。

**学生分布至关重要：** 你的班级并非铁板一块，而是明显分为三个群体：
- **A 组（6 名学生，75%+）：** 这些学生在所有题型上表现良好。他们需要的是精细打磨，而非重教。
- **B 组（10 名学生，50–74%）：** 这些学生掌握了内容（Q1/Q2），但在应用（Q3/Q4）上遇到困难。他们是你提分潜力**最大**的群体——他们具备知识基础，只需学会如何在考场条件下调用这些知识。
- **C 组（12 名学生，低于 50%）：** 这些学生的问题较为混合。35–49% 的 8 名学生很可能与 B 组一样存在技能缺口，外加一些知识漏洞。低于 35% 的 4 名学生可能存在 6 节课无法完全弥补的基础知识缺口。

### 可行动模式

**模式 1：解释/评价技能缺口**
- **数据显示：** 回忆 78%，描述 62%，解释 31%，评价 28%
- **可能含义：** 学生能回忆内容，但无法组织长段落作答。他们很可能缺乏清晰的“解释”题方法（例如 观点-证据-解释 链条）和“评价”题结构（例如 支持-反对-权衡判断）。这是应试技巧问题，而非知识问题。
- **置信度：** 高——该模式高度一致，且 Q2 与 Q3 之间的跌幅过于陡峭，单靠知识漏洞无法解释。如果学生不懂内容，Q1 也会很低。
- **建议行动：** 将 6 节课中的 3–4 节专门用于解释/评价应试技巧。使用范文、现场示范（“看我如何写一道 Q3 答案”）和脚手架练习。

**模式 2：案例研究应用薄弱**
- **数据显示：** Q3（用案例研究解释）仅 31%——是“知识型”题目（Q1–Q3）中最低的
- **可能含义：** 学生要么没有记住案例研究细节，**要么**无法将案例研究细节融入解释中。抽查部分学生答卷以核实：他们是尝试引用案例但用错了，还是完全跳过了案例引用？
- **置信度：** 中——你需要查看实际答卷，才能区分“不知道案例研究”与“不知道如何在解释中使用案例研究”。
- **建议行动：** 快速诊断：给学生 2 分钟写下他们能记住的关于相关案例研究的一切。如果他们能回忆出事实，问题在于应用技巧；如果回忆不出，问题在于知识，需要快速案例复习资料。

**模式 3：双峰/分层分布**
- **数据显示：** 平均分 58%，中位数 54%，极差 23–91%，在 75%+、50–74% 和 50% 以下形成明显聚群
- **可能含义：** 班级不是单一群体——而是至少两到三个需求不同的群体。单一复习策略无法服务所有学生。
- **置信度：** 高——数据分布非常清晰。
- **建议行动：** 开展分层复习课。A 组可以练习拔高与精进（高阶评价）。B 组需要针对 Q3/Q4 题型的结构化应试技巧。C 组（尤其是 35% 以下的 4 名学生）需要快速知识巩固与基础答题结构相结合的支持。

### 推荐行动

**第 1 节课（本周）：** 全班范文精讲课。取模拟考的 Q3，现场示范高分答案的写作过程。显性展示结构：“我是这样把案例研究和原理解释连接起来的。”随后给学生 10 分钟尝试一道类似的 Q3。这能立即应对模式 1。

**第 2–3 节课：** 针对解释与评价题开展脚手架练习。为 B/C 组提供句型开头和段落框架；A 组独立钻研满分范文。每节课开始前进行 2 分钟案例研究快速回忆小测（应对模式 2）。

**第 4 节课：** 集中练习评价题。这是分值最高（12 分）且表现最弱（28%）的题型。教授清晰的评价结构（正方/反方/带证据的最终判断），并用真题风格题目练习。

**第 5 节课：** 考场条件下的限时训练——完成一个完整的 Paper 1 板块。这能锻炼耐力与时间管理，而时间管理往往是 Q3/Q4 表现不佳的隐性原因（学生在 Q1/Q2 上花太久导致后面没时间）。

**第 6 节课：** 复盘限时训练、修补剩余漏洞并巩固应试技巧。根据模拟考和限时训练表现为每位学生生成个性化复习清单。

### 数据没有显示什么

1. **数据没有显示 Q3/Q4 分数低的原因。** 最可能的两种解释是（a）学生缺乏长答案的应试技巧，以及（b）学生缺乏回答 Q3 所需的案例研究知识。这两种情况需要**不同的**干预措施。在锁定策略前请先翻阅实际答卷。

2. **数据未考虑学生努力程度与测试条件。** 模拟考不是正式考试。部分学生可能因为没有认真复习、疲惫或觉得不算分而发挥失常。低于 35% 的 4 名学生中可能包含中途放弃作答的人——他们的实际知识储备可能比分数显示的要好。

3. **与去年班级的对比并不精确。** 你的班级平均 58%，去年班级平均 62%。但那是两批不同的学生做同一份试卷——差异可能反映的是生源届别能力，而非教学质量。不要用这一对比来评价你自身的教学效能。

4. **逐题数据无法揭示个体迷思概念。** Q3 只有 31% 告诉你学生**卡住了**，但没有告诉你他们在题目**哪一步**出错。跨能力水平抽查 5–6 份答卷，以定位具体的卡点。

### 快速参考

| 模式 | 行动 | 优先级 | 置信度 |
|---|---|---|---|
| 解释/评价技能缺口（Q3–Q4） | 范文示范 + 脚手架练习 | 高 | 高 |
| 案例研究应用薄弱 | 快速诊断小测 + 靶向复习 | 高 | 中 |
| 分层分布 | 按群体制定差异化复习计划 | 中 | 高 |
| 末尾 4 名学生低分 | 一对一沟通检查 + 靶向支持 | 中 | 中 |

---

## 已知局限

1. **本技能负责解读数据——并不收集或验证数据。** 解读质量完全取决于所提供数据的质量。如果评估设计本身有缺陷（题目歧义、评分标准错位），数据就会产生误导，解读也会随之偏离。垃圾进，垃圾出。

2. **学习分析能识别模式，但极少能证明因果关系。** 当本技能说“学生很可能缺乏应试技巧”时，这是一个推断，而非绝对事实。替代解释永远存在。教师应将解读视为展开调查的初始假设，而非确诊结论。

3. **K-12 阶段的学习分析实证基础不如高等教育成熟。** Siemens & Long（2011）及大量学习分析文献聚焦于大学层面数据（LMS 日志、课程完成率）。原则可迁移至中小学情境，但具体模式与基准可能不同。Mandinach & Gummer（2016）指出，教师需要的是学科领域特定的数据素养，而非通用的统计学技能。

4. **分析可能无意中窄化课程。** 如果教师持续使用评估数据驱动复习，存在教学过度聚焦于可测结果、牺牲更广泛学习的风险。Wiliam（2011）警告说，形成性数据应当服务于教学，而非定义教学。数据展示的是学生在**这次**测验上的表现——而不是他们最需要学习什么。
