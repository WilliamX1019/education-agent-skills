---
# AGENT SKILLS STANDARD FIELDS (v2)
name: study-strategy-selector
description: "根据学习材料类型、学习目标与学生习惯选择循证学习策略。适用于指导学生复习技巧、家庭作业或独立学习方法的场景。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "self-regulated-learning/study-strategy-selector"
skill_name: "学习策略选择器与指南"
domain: "self-regulated-learning"
version: "1.0"
evidence_strength: "strong"
evidence_sources:
  - "Dunlosky et al. (2013) — Improving students' learning with effective learning techniques: promising directions from cognitive and educational psychology"
  - "Roediger & Pyc (2012) — Inexpensive techniques to improve education: applying cognitive psychology to enhance educational practice"
  - "Kornell & Bjork (2007) — The promise and perils of self-regulated study"
  - "Hartwig & Dunlosky (2012) — Study strategies of college students: are self-testing and scheduling related to achievement?"
  - "Miyatsu et al. (2018) — Five popular study strategies: their pitfalls and optimal implementations"
input_schema:
  required:
    - field: "learning_task"
      type: "string"
      description: "具体的学习任务或学习目标"
    - field: "student_level"
      type: "string"
      description: "年龄/年级及当前学习习惯"
    - field: "material_type"
      type: "string"
      description: "材料类型：事实性/概念性/程序性/混合型"
  optional:
    - field: "time_available"
      type: "string"
      description: "学生拥有多少学习时间"
    - field: "assessment_type"
      type: "string"
      description: "备考的评估类型：考试、论文、展示或实操"
    - field: "student_profiles"
      type: "array"
      description: "来自情境引擎：当前学习习惯、学业表现数据"
    - field: "subject_area"
      type: "string"
      description: "用于学科特定策略适配的学科背景"
output_schema:
  type: "object"
  fields:
    - field: "recommended_strategies"
      type: "array"
      description: "按循证等级排序的策略清单，附带实施指南与时间分配"
    - field: "strategies_to_avoid"
      type: "array"
      description: "学生应当替换掉的常见但低效的策略"
    - field: "study_plan"
      type: "string"
      description: "将推荐策略应用于该具体任务的可执行学习计划"
    - field: "student_guide"
      type: "string"
      description: "可直接复制粘贴使用的面向学生的策略指南"
chains_well_with:
  - "retrieval-practice-generator"
  - "spaced-practice-scheduler"
  - "metacognitive-prompt-library"
  - "goal-setting-protocol-designer"
teacher_time: "3 分钟"
tags: ["study-skills", "learning-strategies", "revision", "self-regulation", "metacognition"]
---

# 学习策略选择器与指南（Study Strategy Selector & Guide）

## 本技能的功能

分析具体的学习任务并推荐最有循证依据的学习策略，为每项策略提供明确的操作实施指南。尤为关键的是，本技能还会识别学生当前很可能在使用的低效策略（荧光笔划重点、反复重读、抄写笔记），并提供附带循证依据的具体替代策略。AI 在此具有独特价值，因为学生几乎总是默认选择最低效的学习策略——Kornell 与 Bjork（2007）发现，最受学生欢迎的策略（重读、划重点）在研究中被评为“低效用”，而最高效的策略（提取练习、间隔练习）却最少被使用。本技能将 Dunlosky 等（2013）的里程碑式综述转化为可落地的、针对具体任务的指导。

## 循证依据

Dunlosky 等（2013）开展了迄今为止最全面的学习策略综述，依据四项标准（跨学习条件、学生特征、材料类型及效标任务的普适性）系统评估了十种学习技术。仅有两项策略获得“高效用”评级：练习测试（提取练习 retrieval practice）与分散练习（间隔练习 distributed practice）。三项获得“中等效用”：穿插练习（interleaved practice）、精细提问（elaborative interrogation）与自我解释（self-explanation）。五项尽管在学生中最流行，却被评为“低效用”：划重点、重读、做摘要、关键词助记法以及文本意象法。Kornell 与 Bjork（2007）证明，学生对自己学习效果的判断力很差——他们倾向于选择“感觉有效”的策略（重读带来流畅感，让人误以为学会了），而非“真正有效”的策略（提取练习感觉更吃力，但能带来更强的记忆保持）。Hartwig 与 Dunlosky（2012）发现，采用自我测试与间隔安排的学生成绩显著更高。Miyatsu 等（2018）指出，即使是“好”策略也有陷阱——如果提取练习后不核对答案，效果就会打折；如果间隔时间过长，收益也会下降。

## 输入规范

教师必须提供：
- **学习任务：** 学生需要学习的内容。*例如：“备考 10 年级生物关于细胞与物质运输的考试（70% 事实回忆，30% 应用题）” / “复习 GCSE 历史试卷 2：冷战的起因与事件”*
- **学生水平：** 年级与当前习惯。*例如：“10 年级，目前习惯重读笔记和划重点” / “12 年级，使用闪卡但没有间隔安排”*
- **材料类型：** 事实性、概念性、程序性或混合型。*例如：“混合型——需要记忆关键术语，同时需要理解并应用生物过程”*

可选（如情境引擎可用，将自动注入）：
- **可用时间：** 考前可用于学习的时间
- **评估类型：** 备考对象（考试、论文、展示、实操）
- **学生档案：** 当前学习习惯、学业表现数据
- **学科领域：** 学科背景

## Prompt

```
You are an expert in the cognitive psychology of learning, specialising in evidence-based study strategies. You have deep knowledge of Dunlosky et al.'s (2013) comprehensive review of learning techniques, Kornell & Bjork's (2007) research on self-regulated study, and the implementation pitfalls identified by Miyatsu et al. (2018).

Your task is to recommend study strategies for the following:

**Learning task:** {{learning_task}}
**Student level:** {{student_level}}
**Material type:** {{material_type}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Time available:** {{time_available}} — if not provided, design a general study plan and note how to adjust for more or less time.
**Assessment type:** {{assessment_type}} — if not provided, infer from the learning task description and recommend strategies that transfer across assessment types.
**Student profiles:** {{student_profiles}} — if not provided, assume the student uses common but ineffective strategies (re-reading, highlighting) and needs to be guided toward evidence-based alternatives.
**Subject area:** {{subject_area}} — if not provided, infer from the task and adapt strategies to the domain.

Apply these evidence-based principles:

1. **Rank strategies by Dunlosky et al.'s (2013) utility ratings:**
   - **High utility (recommend first):** Practice testing (retrieval practice), distributed practice (spacing). These should form the backbone of any study plan.
   - **Moderate utility (recommend second):** Interleaved practice, elaborative interrogation, self-explanation. Use as complements to the high-utility strategies.
   - **Low utility (identify and replace):** Highlighting, re-reading, summarisation, keyword mnemonic, imagery for text. If the student is currently using these, explicitly explain why they don't work and what to do instead.

2. **Explain *why* ineffective strategies feel effective (Kornell & Bjork, 2007):** Re-reading produces fluency — the text feels familiar, which the brain misinterprets as understanding. Highlighting feels productive — the coloured marks feel like engagement. But familiarity is not learning, and marking text is not encoding it. Students need to understand this illusion to break the habit.

3. **Provide implementation detail, not just strategy names (Miyatsu et al., 2018):** "Use retrieval practice" is not a recommendation. "Close your notes. Write down everything you remember about cell transport. Then open your notes and check — focus your next study session on what you couldn't recall" is a recommendation. Every strategy must include exactly how to do it.

4. **Flag pitfalls for each strategy (Miyatsu et al., 2018):**
   - Retrieval practice pitfall: not checking answers — students must verify and correct, or retrieval practice can reinforce errors.
   - Spacing pitfall: gaps too large — forgetting too much between sessions reduces the benefit. Start with short gaps and expand.
   - Self-testing pitfall: only testing what you already know — students must test weak areas, not just practise easy recall.

5. **Match strategies to material type:**
   - Factual recall (terms, dates, names) → flashcard retrieval practice, spaced repetition
   - Conceptual understanding (processes, relationships) → elaborative interrogation, self-explanation, concept mapping from memory
   - Procedural skills (calculations, methods) → interleaved practice problems, worked example study
   - Application/transfer → practice with varied problem types, self-explanation of why each approach works

6. **Create a concrete, schedulable plan:** Don't just list strategies — show the student exactly what to do, when, and for how long.

Return your output in this exact format:

## Study Strategy Guide: [Task]

**For:** [Student level]
**Material type:** [Type]

### Strategies to STOP Using (and Why)
[2–3 ineffective strategies the student is likely using, with honest explanation of why they don't work despite feeling productive]

### Recommended Strategies (Ranked by Evidence)
For each strategy:
- **Strategy name** — [Dunlosky rating]
- **What to do:** [Specific, step-by-step implementation]
- **Why it works:** [1–2 sentence evidence-based explanation]
- **Pitfall to avoid:** [The common implementation error]
- **Time needed:** [How long per session]

### Study Plan
[A concrete, schedulable plan applying these strategies to this specific task — laid out by session or by day]

### Student Guide
[Copy-pasteable, student-friendly version with practical instructions]

**Self-check before returning output:** Verify that (a) every recommended strategy has specific implementation instructions, not just a name, (b) ineffective strategies are identified with honest explanations, (c) pitfalls are flagged for each recommended strategy, (d) the study plan is concrete and schedulable, and (e) strategies are matched to the material type.
```

## 示例输出

**场景：** *学习任务：“备考 10 年级综合科学考试——生物主题：细胞结构、跨膜运输、细胞分裂。共 40 分：20 分回忆题，10 分应用题，10 分论述题。” / 学生水平：“10 年级，目前习惯重读课本并制作色彩缤纷的笔记” / 材料类型：“混合型——需要回忆术语、理解过程，并完成需要结构化解释的 6 分大题”*

---

## 学习策略指南：10 年级生物考试——细胞单元

**适用对象：** 10 年级，目前使用重读与装饰性记笔记
**材料类型：** 混合型（事实回忆 + 概念理解 + 论述写作）

### 应当停止使用的策略（及原因）

**1. 反复重读课本**
你觉得自己在学习，是因为文字变得越来越熟悉——你认出了这些词，大脑就把这种熟悉感误判为“理解了”。但 Kornell 与 Bjork（2007）证明这是一种错觉。做个测试：现在合上课本，凭记忆讲出有丝分裂的各个阶段。如果讲不出来，说明重读并没有教会你——它只是让书页看起来眼熟而已。Dunlosky 等（2013）将重读评为“低效用”。

**2. 制作精美详尽的抄写笔记**
把课本内容工整地抄成笔记感觉很充实——你花了时间、产出了成果，看起来还很美观。但你做的其实相当于“人工复印”。信息从书本直接转移到笔记本上，并没有真正经过大脑的深度加工。Dunlosky 等（2013）将做摘要评为“低效用”，因为被动抄写不需要你主动加工或提取信息。

**3. 用荧光笔划重点**
划重点只是标记了文本，并没有加工它。你是在判断什么重要（有时有用），但没有采取任何行动去记住它。一本画满荧光笔的课本看起来像是学过了——其实并没有。Dunlosky 等（2013）：“低效用”。

### 推荐策略（按循证等级排序）

**1. 提取练习（练习测试）** —— 高效用（Dunlosky et al., 2013）

**具体做法：**
1. 学习一个主题 10–15 分钟（例如细胞结构）。
2. 彻底合上所有笔记和课本。
3. 拿出一张白纸，凭记忆写下你能记住的关于该主题的**所有内容**。凭记忆画示意图，凭记忆下定义。
4. 打开笔记。核对写对的（打钩）、遗漏的（用另一种颜色补上）以及写错的（用红笔订正）。
5. 你遗漏或写错的内容，就是你下一轮学习的优先重点。

**为何有效：** 从记忆中主动提取信息比反复重读更能强化记忆痕迹。Roediger 与 Pyc（2012）称之为“测试效应”（the testing effect）。大脑重构信息时的那份吃力感，正是产生学习的时刻。

**应避免的陷阱：** 提取后**必须**核对答案。如果你提取出了错误信息却不加纠正，反而会强化错误记忆。务必对照笔记或课本核实。

**所需时间：** 每个主题 20 分钟（10 分钟学习 + 5 分钟提取 + 5 分钟核对订正）。

---

**2. 分散练习（间隔学习）** —— 高效用（Dunlosky et al., 2013）

**具体做法：**
1. 切勿在考前一晚一口气突击完三个主题。相反，把学习分散到 2 周以上的多个短时段中。
2. 安排表：每个主题学 3 轮，轮次之间留出间隔。
   - 第 1 轮：考前 2 周
   - 第 2 轮：考前 1 周
   - 第 3 轮：考前 2–3 天
3. 每一轮都要使用提取练习（上述策略 1），而不是重读。

**为何有效：** 艾宾浩斯遗忘曲线表明，如果不复习，24 小时内你会丢失约 70% 的新学内容。在遗忘变成永久性之前以拉长的间隔进行回顾，能够有效拦截遗忘。Cepeda 等（2006）：最佳间隔取决于记忆保持的目标时长。

**应避免的陷阱：** 间隔不要拉得太长。如果到下一轮时你已经忘得一干二净，说明间隔太大了——请缩短间隔。适度的遗忘是有益的（它让提取更费力，从而强化记忆），但彻底忘光等于推倒重来。

**所需时间：** 每个主题 3 轮 × 20 分钟 = 2 周内共 3 小时（相比考前一次突击 3 小时，效果远胜后者）。

---

**3. 精细提问（Elaborative Interrogation）** —— 中等效用（Dunlosky et al., 2013）

**具体做法：** 对你学习的每一个事实，自问“**为什么**这是真的？”并尝试自己给出解释。
- 细胞膜具有选择透过性 → 为什么？因为它需要让某些物质进入（营养物质、氧气），同时把另一些物质挡在外面或排出（废物、毒素），以维持细胞内部环境稳定。
- 有丝分裂产生两个相同的细胞 → 为什么相同？因为每条染色体都先进行了复制，所以每个新细胞都获得完整的一套染色体。为什么身体需要完全相同的副本？为了生长和修复——皮肤细胞需要分裂出更多皮肤细胞，而不是变成别的细胞。

**为何有效：** 主动生成解释能为信息建立额外的提取通路（Pressley et al., 1992）。你正在把新知识与已知事物连接起来。

**应避免的陷阱：** 这一策略需要你有足够的背景知识来生成合理解释。如果你真的不知道为什么某个事实成立，先查阅弄懂，再练习用自己的话解释——不要直接跳过这个问题。

**所需时间：** 在每次提取练习环节增加 5 分钟的“为什么？”追问。

---

**4. 穿插练习（Interleaved Practice）** —— 中等效用（Dunlosky et al., 2013）

**具体做法：** 刷真题或练习题时，打乱主题顺序。不要连做 10 道细胞结构题，再做 10 道物质运输题。相反，把它们混在一起：细胞结构、运输、分裂、结构、运输、分裂。这会迫使你在答题前先判断这道题考的是哪个主题。

**为何有效：** 真实考试中，各主题的题目是混杂出现的。如果你平时只按模块集中刷题，就永远练不出“识别题目考察哪个知识点”的能力。Rohrer 等（2015）发现穿插练习使数学成绩提升了 25%。

**应避免的陷阱：** 在你单独学完每个主题之前不要穿插。你需要先掌握各个主题的基础，然后再混合练习。

**所需时间：** 在考前最后一周做练习题时，将所有主题混合编排。无需额外时间——只需改变做题顺序。

### 学习计划

**假设考前 2 周，每天学习 30 分钟：**

| 日期 | 具体安排 |
|-----|-----------|
| 第 1 天（周一） | 细胞结构：读笔记 10 分钟，合上笔记在白纸上默写所有记得的内容（15 分钟），核对并订正（5 分钟） |
| 第 2 天（周二） | 跨膜运输：同样流程——阅读、合上、提取、核对 |
| 第 3 天（周三） | 细胞分裂：同样流程——阅读、合上、提取、核对 |
| 第 4 天（周四） | **再学**细胞结构：不要重读。直接开始提取。白纸默写全部内容。对比第 1 天——这次你记住了哪些上次忘掉的？ |
| 第 5 天（周五） | **再学**跨膜运输：直接提取。重点攻克第 2 天遗漏的部分 |
| 第 6–7 天（周末） | 休息一天。另一天：在一张纸上提取**全部三个主题**。给自己计时——20 分钟完成三项 |
| 第 8 天（周一） | 细胞分裂提取 + 精细提问：针对有丝分裂的每个阶段，解释**为什么**会发生这一步 |
| 第 9 天（周二） | 做真题练习——**穿插进行**。混合全部三个主题，重点训练题型识别 |
| 第 10 天（周三） | 专项练习 6 分论述题：在限时条件下完整写出一道大题，对照评分标准批改 |
| 第 11 天（周四） | 终极提取：在白纸上默写全部内容。找出最薄弱的 3 个点，**只**复习这 3 个点 |
| 第 12 天（周五） | 针对这 3 个最薄弱的点做最后一次提取。然后停止复习——间隔练习已为你做好充分准备 |

### 学生指南

---

**如何真正高效地学习（基于科学研究的实证方法）**

**停止做这些事**（它们只是让你感觉很努力，其实没用）：
- 反复重读笔记——眼熟不等于理解
- 制作精美笔记——抄写不等于学习
- 划荧光笔——做记号不等于记住

**开始做这些事：**

**第一步：提取，而不是重读。** 合上笔记，在白纸上写下所有记得的内容，然后核对。忘掉的那些？才是你接下来要学的重点。

**第二步：拉开间隔。** 每个主题在 2 周内分 3 次学习，而不是考前一晚熬夜突击。有间隔的短时学习永远胜过一次性长时间硬塞。

**第三步：多问“为什么”。** 对每个知识点，试着解释它为什么成立。能讲出来才算懂；讲不出来，说明找到了知识漏洞。

**第四步：混着刷题。** 做练习题时打乱主题顺序，不要做完一章再做下一章——混合练习。

**黄金法则：** 如果学习过程让你觉得轻松无比，你很可能没在真正学习。提取练习比单纯重读更费脑子——这正是它的意义所在。提取时越费力，记忆越牢固。

---

## 已知局限性

1. **学生可能会抗拒用费力的策略替换掉舒适、熟悉的旧习惯。** 重读让人觉得很有成就感，而提取练习起初让人感到挫败。Kornell 与 Bjork（2007）表明，由于流畅性错觉，学生往往误以为低效策略更有效。教师应预见到这种抵触情绪，并向学生解释背后的科学原理——当学生明白**为什么**这些方法有效时，他们更有可能坚持使用费力但高效的方法。

2. **策略建议假定学生手头拥有准确的学习资料。** 如果学生的笔记本身有错误，提取练习反而会巩固这些错误。“核对并订正”步骤至关重要，但这依赖于手头有可靠的对照资料。

3. **Dunlosky 等（2013）的效用评级主要基于言语学习研究（文本理解、事实回忆）。** 向高度实操性学科（体育、音乐演奏、美术、设计技术）的迁移证据尚不充分。对于程序性技能，穿插练习有充分证据支持，但“合上笔记进行提取”的做法需要调整——身体排练与刻意练习可能更为合适。
