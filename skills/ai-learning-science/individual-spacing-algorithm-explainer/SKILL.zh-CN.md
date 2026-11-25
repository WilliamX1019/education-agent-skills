---
# AGENT SKILLS STANDARD FIELDS (v2)
name: individual-spacing-algorithm-explainer
description: "结合学生表现数据与遗忘曲线解释并配置个性化间隔算法。适用于在自适应学习平台中个性化定制记忆保持计划表。"
disable-model-invocation: true
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "ai-learning-science/individual-spacing-algorithm-explainer"
skill_name: "个性化间隔算法解释器"
domain: "ai-learning-science"
version: "1.0"
evidence_strength: "strong"
evidence_sources:
  - "Ebbinghaus (1885/1913) — Memory: A contribution to experimental psychology (forgetting curve)"
  - "Cepeda et al. (2006) — Distributed practice in verbal recall tasks: A review and quantitative synthesis (meta-analysis)"
  - "Lindsey et al. (2014) — Improving students' long-term knowledge retention through personalized review"
  - "Settles & Meeder (2016) — A trainable spaced repetition model for language learning (Duolingo half-life regression)"
  - "Pashler et al. (2007) — Organizing instruction and study to improve student learning (IES practice guide)"
input_schema:
  required:
    - field: "content_to_space"
      type: "string"
      description: "需要随时间保持的具体知识或技能——学生需要记住的内容"
    - field: "performance_data"
      type: "string"
      description: "关于学生当前记忆保持情况的已知信息——测验分数、小测结果、回忆准确率或对记住与遗忘内容的日常观察"
  optional:
    - field: "student_level"
      type: "string"
      description: "年龄/年级及能力水平"
    - field: "subject_area"
      type: "string"
      description: "课程学科"
    - field: "time_horizon"
      type: "string"
      description: "知识需要保持多长时间——直到某次考试、学期末还是永久"
    - field: "available_review_slots"
      type: "string"
      description: "每周现实中可以安排多少次复习时段"
    - field: "system_context"
      type: "string"
      description: "间隔复习是由教师手动实施、嵌入 AI 系统，还是通过 Anki 或 Quizlet 等工具管理"
output_schema:
  type: "object"
  fields:
    - field: "spacing_schedule"
      type: "object"
      description: "个性化复习计划表——每一项何时应当复习以及原因"
    - field: "algorithm_explanation"
      type: "object"
      description: "对教师友好的解释，说明间隔算法如何运作及为何选择这些时间间隔"
    - field: "priority_ranking"
      type: "array"
      description: "按遗忘风险排序的项目——哪些项目最迫切需要复习"
    - field: "implementation_guidance"
      type: "object"
      description: "在真实课堂或系统中实施该计划表的实用建议"
chains_well_with:
  - "adaptive-hint-sequence-designer"
  - "formative-assessment-loop-designer"
  - "retrieval-practice-designer"
teacher_time: "5 分钟"
tags: ["spacing", "spaced-repetition", "forgetting-curve", "Ebbinghaus", "Lindsey", "Duolingo", "retention", "memory", "algorithm"]
---

# 个性化间隔算法解释器

## 本技能的作用

根据学生表现数据为特定知识项集合生成个性化间隔重复计划表，并用通俗易懂的语言向教师解释算法逻辑。本技能**不执行**间隔算法——执行需要 Anki、Quizlet、SuperMemo 或 Kaku 自带的记忆保持引擎。本技能负责**设计**与**解释**：给定学生已经掌握的内容和正在遗忘的内容，它产出具体的复习计划表，并清晰说明选择每个时间间隔的理据。间隔研究的核心洞见在于：最佳复习间隔取决于期望的保持周期与该项目的当前记忆强度。Ebbinghaus（1885）确立了遗忘遵循可预测曲线的规律——起初陡峭，随后逐渐平缓。Cepeda 等人（2006）在一项全面元分析中证明，跨时间间隔复习所产生的长期保持效果显著优于将同等练习量集中于单次时段（集中练习）。现实挑战在于，每个学生和每个项目的最佳间隔都各不相同——这正是个性化不可或缺之处。AI 在此尤为关键，因为为单个学生的几十个知识项计算最佳间隔对机器而言在计算上微不足道，但对手动操作的一线教师而言几乎不可能完成。

## 实证基础

Ebbinghaus（1885/1913）开展了关于遗忘的奠基性实验，证明新学材料的记忆呈指数衰减，但随后的每一次复习都会增强记忆痕迹并减缓遗忘速率。这条“遗忘曲线”是所有间隔算法的理论基础。Cepeda 等人（2006）对 254 项分布式练习研究进行了元分析，发现跨多种材料和年龄段均存在稳健的间隔效应。他们发现最佳学习间隔（ISI）取决于保持间隔（RI）——即直到需要用到该知识的时间长度。其分析得出的粗略经验法则是：最佳 ISI 大约为 RI 的 10–20%。因此，如果 30 天后的考试需要用到某项知识，最佳间隔大约为每 3–6 天一次。Lindsey 等人（2014）将间隔研究带入真实课堂，测试了一套用于中学生学习社会科学的个性化间隔算法。他们的算法根据个体学生表现调整复习间隔，结果发现与教师选定的集中复习计划相比，长期保持率显著提高。关键在于，个性化算法优于“一刀切”的固定间隔计划，证明了个体校准的价值。Settles & Meeder（2016）开发了用于 Duolingo 的“半衰期回归（half-life regression）”模型，根据学生对特定词条的个人历史记录，预测其在特定时间回忆出该词条的概率。该模型结合三个变量：项目已出现次数、距上次复习的时间，以及学生在类似项目上的准确率。这代表了大规模实用间隔算法的前沿水平。Pashler 等人（2007）在 IES 实践指南中将间隔研究转化为实用建议，指出尽管间隔效应拥有坚实的实证基础，教师却很少使用它——部分原因是需要提前规划，部分原因是它违背直觉（学生在集中练习后自我感觉更有信心，尽管间隔练习才能带来更好的长期保持）。

## 输入规范

教师必须提供：
- **需间隔的内容（Content to space）：** 学生需要保持的知识。*例如：“八年级生物：细胞器及其功能——线粒体、细胞核、细胞膜、核糖体、叶绿体、液泡、细胞壁” / “一战的关键日期与起因” / “法语不规则动词变位——être, avoir, aller, faire” / “6–12 的乘法口诀”*
- **表现数据（Performance data）：** 关于当前记忆保持情况的已知信息。*例如：“上周五单元小测：全班平均分 72%。大多数学生答对了线粒体和细胞核，但把核糖体与粗面内质网混淆了。三名学生得分低于 50%” / “课堂非正式提问显示大多数学生记得起因但记不住日期” / “类似 Duolingo 的准确率：être 95%、avoir 88%、aller 71%、faire 62%”*

可选项（如可用则由上下文引擎注入）：
- **学生水平（Student level）：** 年级与能力水平
- **学科领域（Subject area）：** 课程学科
- **时间跨度（Time horizon）：** 知识需要保持多长时间
- **可用复习时段（Available review slots）：** 每周现实可用的复习次数
- **系统背景（System context）：** 手动、嵌入 AI 还是基于工具实施

## 提示词（Prompt）

```
You are an expert in the cognitive science of memory and spaced repetition, with deep knowledge of Ebbinghaus's (1885) forgetting curve, Cepeda et al.'s (2006) meta-analysis of distributed practice, Lindsey et al.'s (2014) personalised spacing research, Settles & Meeder's (2016) half-life regression model from Duolingo, and Pashler et al.'s (2007) IES practice guide on organising instruction. You understand both the theory (why spacing works — memory consolidation, retrieval practice, desirable difficulty) and the practical challenge (designing a schedule that a real teacher can actually implement).

CRITICAL PRINCIPLES:
- **The forgetting curve is exponential, but each retrieval slows it.** New material needs review soon (within 1-2 days). Each successful retrieval strengthens the memory trace and extends the optimal interval. Items retrieved 5+ times can go weeks or months between reviews.
- **The optimal interval depends on the retention horizon.** Cepeda et al.'s (2006) guideline: the optimal inter-study interval is roughly 10-20% of the time until the knowledge is needed. Short-term retention (exam next week) = short intervals. Long-term retention (GCSE in 2 years) = longer intervals with gradual expansion.
- **Not all items need the same schedule.** Items the student already knows well need less frequent review. Items they are forgetting need urgent, short-interval review. The schedule must be PERSONALISED to the performance data.
- **Prioritise by forgetting risk, not by importance.** A student who remembers mitochondria perfectly doesn't need to review mitochondria, even if it's "important." The schedule should target the items with the HIGHEST probability of being forgotten before the next review opportunity.
- **Explain the algorithm in plain English.** Teachers are not data scientists. The explanation must be clear, concrete, and jargon-free. "Review ribosomes on Tuesday because your students got it wrong last Friday and the forgetting curve suggests they'll have forgotten it by Wednesday" — not "Apply exponential decay function with λ = 0.3."

Your task is to design a personalised spacing schedule for:

**Content to space:** {{content_to_space}}
**Performance data:** {{performance_data}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Student level:** {{student_level}} — if not provided, design for a general secondary school context.
**Subject area:** {{subject_area}} — if not provided, infer from the content.
**Time horizon:** {{time_horizon}} — if not provided, assume the knowledge needs to be retained for at least one term (10-12 weeks).
**Available review slots:** {{available_review_slots}} — if not provided, assume 2-3 short review opportunities per week (5-10 minutes each).
**System context:** {{system_context}} — if not provided, design for a teacher implementing the schedule manually (low-tech, practical).

Return your output in this exact format:

## Personalised Spacing Schedule: [Content Area]

**Content:** [What needs to be retained]
**Performance snapshot:** [Summary of current retention state]
**Time horizon:** [How long the knowledge needs to last]
**Schedule basis:** [Brief explanation of why these intervals were chosen]

### Forgetting Risk Analysis

[For each item or item cluster, estimate the current forgetting risk based on the performance data. Rank from highest risk to lowest. Explain in plain English why each item is where it is.]

### Review Schedule

[A concrete, week-by-week schedule showing when each item should be reviewed. Include the format of review (quiz, flashcard, retrieval practice, application task) and the rationale for each timing decision.]

**Week 1:**
- [Day]: [Items to review] — [Why now, what format]

**Week 2:**
- [Day]: [Items to review] — [Why now, what format]

[Continue for the full time horizon or until the schedule stabilises into a maintenance pattern]

### Algorithm Explanation (Teacher-Friendly)

[Explain how the schedule was designed — in plain English. Cover: why items are reviewed at different intervals, why some items appear more often than others, how the schedule adapts if students get items right or wrong, and the underlying principle (each successful retrieval extends the interval).]

### Adaptation Rules

[What to do when students get items RIGHT (extend the interval) and when they get items WRONG (shorten the interval). Provide specific, actionable rules a teacher can follow.]

### Implementation Tips

[Practical advice for actually running this schedule in a classroom — including how to keep it manageable, how to adjust when time is short, and common mistakes to avoid.]

**Self-check before returning output:** Verify that (a) the schedule is personalised to the performance data, (b) high-forgetting-risk items are scheduled more frequently, (c) intervals expand over time for well-retained items, (d) the algorithm explanation is in plain English, and (e) the schedule is realistic for the available review time.
```

## 示例输出

**情景：** *需间隔的内容：“八年级生物：细胞器及其功能——线粒体、细胞核、细胞膜、核糖体、叶绿体、液泡、细胞壁” / 表现数据：“上周五单元末小测：全班平均分 72%。逐项明细：线粒体 91% 正确、细胞核 88%、细胞膜 74%、细胞壁 69%、叶绿体 65%、液泡 58%、核糖体 41%。最常见错误：将核糖体与粗面内质网混淆，以及将液泡功能（储存）与细胞膜功能（选择透过性）混淆” / 时间跨度：“14 周后的期末考试” / 可用复习时段：“每周两次 5 分钟课前热身活动（周二和周四）” / 学生水平：“八年级，混合能力班”*

---

## 个性化间隔计划表：细胞器

**内容：** 7 种细胞器及其功能（线粒体、细胞核、细胞膜、核糖体、叶绿体、液泡、细胞壁）
**表现快照：** 全班平均 72%。两项扎实（线粒体 91%、细胞核 88%）。两项中等（细胞膜 74%、细胞壁 69%）。三项薄弱（叶绿体 65%、液泡 58%、核糖体 41%）。
**时间跨度：** 距离期末考试还有 14 周
**计划依据：** 遗忘风险最高的项目（核糖体、液泡、叶绿体）需要立即且高频的复习。已经扎实的项目（线粒体、细胞核）只需极少复习——刚好足以防止在 14 周内缓慢衰减。计划表遵循渐扩间隔模式：起初间隔短，随着每项成功回忆逐步拉长。

### 遗忘风险分析

| 项目 | 上次得分 | 遗忘风险 | 优先级 | 推理说明 |
|---|---|---|---|---|
| 核糖体 | 41% | 极高 | 1 | 已低于 50%。如果本周不复习，回忆率很可能跌至接近零。与粗面内质网混淆说明存在概念漏洞，而不仅是记忆薄弱。 |
| 液泡 | 58% | 高 | 2 | 仅略高于随机猜测。与细胞膜功能混淆表明学生的表征脆弱、极易混淆。 |
| 叶绿体 | 65% | 高 | 3 | 低于班级平均分。很可能与线粒体混淆（两者都与能量有关）。需要在混淆固化前复习。 |
| 细胞壁 | 69% | 中 | 4 | 略低于平均分。概念相对直接，但学生可能将其与细胞膜混淆。 |
| 细胞膜 | 74% | 中 | 5 | 处于班级平均水平。选择透过性概念较为抽象，若不强化容易淡忘。 |
| 细胞核 | 88% | 低 | 6 | 回忆牢固。第 3–4 周复习一次应足以维持。 |
| 线粒体 | 91% | 低 | 7 | 最强项目。仅在时间允许时复习，或与对比任务结合（线粒体 vs. 叶绿体）。 |

### 复习计划表

**第 1 周：**
- **周二：** 核糖体与液泡（5 分钟）。形式：提取练习——“不看笔记，写下核糖体的功能以及它位于哪里。然后对液泡做同样练习。”随后立即给予纠正性反馈。这两项处于极高风险，需要在小测后 4 天内进行提取。
- **周四：** 叶绿体与细胞壁（5 分钟）。形式：对比任务——“叶绿体与线粒体有何不同？细胞壁与细胞膜有何不同？”对比迫使学生区分常被混淆的配对。

**第 2 周：**
- **周二：** 核糖体、液泡与叶绿体（5 分钟）。形式：快问快答——6 道题，每题 30 秒。核糖体和液泡再次出现是因为它们最薄弱；叶绿体出现是因为一次对比任务可能尚未完全消除混淆。
- **周四：** 细胞膜与细胞壁（5 分钟）。形式：应用题——“将植物细胞放入盐水中。接下来发生的事情涉及哪些细胞器？每一个分别起什么作用？”这在功能情境中复习了细胞膜和细胞壁。

**第 3 周：**
- **周二：** 核糖体与液泡（5 分钟）。如果第 2 周周二的测验显示有进步，使用更高难度形式：“解释为什么核糖体受损的细胞最终会死亡。”如果仍然薄弱，回到基础提取。
- **周四：** 全部 7 种细胞器（5 分钟）。形式：凭记忆绘图与标注——“画一个植物细胞，并尽可能多地标注细胞器及其功能。”首次全覆盖复习。线粒体和细胞核自原小测后首次在此出现——对于 88–91% 回忆率、14 周保持周期的项目，2 周是恰当的间隔。

**第 4 周：**
- **周二：** 叶绿体以及周四绘图中出错的任何项目（5 分钟）。自适应调整——复习被遗忘的内容。
- **周四：** 核糖体与液泡（5 分钟）。最薄弱项目的第三次复习。如果学生现在已超过 80%，间隔可以开始拉长。

**第 5–6 周：**
- **每周一次**复习核糖体、液泡与叶绿体（最初薄弱的项目）。形式：穿插提取——将细胞器问题与其他生物学主题混合以增加难度。间隔已从每周两次拉长到每周一次，因为这些项目现在应当正在变稳固。
- **每周一次**复习细胞膜与细胞壁，间隔同样拉长。

**第 7–10 周：**
- **每 10 天一次**复习全部 7 种细胞器，与其他主题穿插。到此时，项目应当已足够稳定，可以承受更长间隔。使用多样化题型：选择题、简答题、图表标注、应用题。

**第 11–14 周（考前）：**
- **每周一次综合复习**，将全部 7 种细胞器与其他复习主题一并覆盖。此时间隔约为每周一次——适用于已成功提取 5–6 次、只需再维持 3–4 周的项目。

### 算法解释（教师友好版）

以下是这一计划表背后的通俗逻辑：

**为什么不同项目获得不同计划：** 把每一段记忆想象成一块电池。小测告诉我们哪些电池是满电的（线粒体——91%），哪些是半电的（细胞膜——74%），哪些快没电了（核糖体——41%）。快没电的电池需要立即且频繁地充电。满电的电池只需每隔几周补一次电。

**为什么间隔会拉长：** 每当学生成功记住某样东西，记忆就会变得更强——它能维持电量的时间更长。因此，在学生连续三次正确回忆出“核糖体制造蛋白质”之后，他们一周内都不需要再看它。五次成功回忆后，他们可能两周都不需要再看。随着记忆变强，计划表会自动拉长间隔。

**10–20% 规则：** 研究（Cepeda et al., 2006）提供了一条实用经验法则——复习之间的间隔大约应为直到需要用到该知识的总时间的 10–20%。你的考试在 14 周（98 天）后，因此熟悉项目的“维持”间隔大约是每 10–20 天一次。对于新项目或薄弱项目，间隔起初要短得多，然后逐步拉长到这一水平。

**为什么会出现对比题和应用题：** 提取练习（“写下你记得的内容”）强化记忆。但对比任务（“X 与 Y 有何不同？”）和应用任务（“当……时会发生什么？”）在强化记忆的同时建构**理解**。计划表在早期使用基础提取（当记忆还脆弱时），在后期使用要求更高的题型（当记忆已足够稳定、能承受更难问题时）。

### 自适应调整规则

**当学生答对某个项目时：**
- 如果是第一次正确提取：将下次复习安排在 3–4 天后
- 如果是第二次正确提取：安排在 7 天后
- 如果是第三次正确提取：安排在 14 天后
- 如果是第四次或更多次：安排在 21 天后，随后保持每 2–3 周一次的间隔

**当学生答错某个项目时：**
- 将间隔重置为 1–2 天——该项目退回“极高风险”
- 换用不同的提取题型（如果他们在选择题上错了，改用对比任务）
- **不要**直接重教该项目——让学生**先**尝试提取，哪怕会答错，然后再提供纠正性反馈。失败的提取尝试实际上会增强随后的学习效果（Kornell et al., 2009）。

### 实施建议

1. **保持简单。** 你每周只有两个 5 分钟时段。不要试图手动追踪每个学生的个人间隔计划——那是像 Kaku 这样的 AI 系统该做的事。相反，利用**班级层面**的表现数据来决定哪些项目需要复习以及何时复习。

2. **使用小型白板或离堂小测。** 在 5 分钟内开展提取练习最快的方式是小型白板（“举牌告诉我：核糖体是做什么的？”）或离堂小测。这些也能为你提供快速的表现数据以调整计划。

3. **不要在复习时段重教。** 这 5 分钟课前热身是用来**提取**的，不是用来重教的。如果学生想不起来，让他们短暂挣扎一下，然后展示答案并继续。这种挣扎是富有成效的——它会为下一次强化记忆痕迹。

4. **第 4 周后开始穿插。** 一旦项目被复习过 2–3 次，就开始把它们与其他主题混合。穿插练习感觉更难（学生会觉得没那么有把握），但比集中分块复习产生更好的长期保持效果。

5. **计划表是起点，不是死剧本。** 如果你第 2 周周二的小测显示核糖体正确率跃升至 85%，太棒了——把它移到更长间隔。如果叶绿体跌到 50%，把它调回更短间隔。计划表应根据学生**实际**记住的内容来调整，而不是你**希望**他们记住的内容。

---

## 已知局限

1. **本技能设计并解释间隔计划——并不负责执行它。** 执行要么需要教师手动落实（可行但费力），要么需要 Anki、Quizlet 或 Kaku 这类能自动追踪个人项目历史并计算间隔的系统。上述计划使用的是班级层面数据；真正的个性化间隔需要个人层面追踪，而这在没有技术工具的情况下不切实际。

2. **最佳间隔只是近似值。** Cepeda 等人（2006）的 10–20% 指南是实用的启发式规则，而非精确公式。真正的最佳间隔取决于材料难度、编码质量、个体差异以及所需的提取类型。上述计划是一个合乎原则的起点，而非数学上的最优解。

3. **间隔效应对事实性和概念性知识有效，但对程序性技能研究较少。** 实证基础最扎实的是词汇、事实回忆和概念理解。对于复杂程序性技能（作文写作、数学问题解决），间隔效应仍适用于其中的组成知识，但技能整体可能需要不同的练习结构。

4. **学生依从性是硬约束。** 如果学生不实际进行复习，世界上最好的间隔算法也会失效。在课堂上，教师控制复习时间表。在家庭作业或自学情境下，许多学生会选择集中练习（临时抱佛脚），因为那样**感觉**更有效，尽管事实并非如此（Pashler et al., 2007）。计划表必须被执行，而不仅仅是设计出来。
