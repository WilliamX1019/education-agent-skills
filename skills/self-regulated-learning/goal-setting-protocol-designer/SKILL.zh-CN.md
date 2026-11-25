---
# AGENT SKILLS STANDARD FIELDS (v2)
name: goal-setting-protocol-designer
description: "采用 SMART 或执行意图（implementation-intention）框架为学生设计结构化的目标设定规范。适用于开启单元学习、项目制学习或培养学生自主规划习惯的场景。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "self-regulated-learning/goal-setting-protocol-designer"
skill_name: "目标设定规范设计器"
domain: "self-regulated-learning"
version: "1.0"
evidence_strength: "strong"
evidence_sources:
  - "Locke & Latham (1990) — A Theory of Goal Setting and Task Performance"
  - "Locke & Latham (2002) — Building a practically useful theory of goal setting and task motivation"
  - "Zimmerman & Bandura (1994) — Impact of self-regulatory influences on writing course attainment"
  - "Schunk (1990) — Goal setting and self-efficacy during self-regulated learning"
  - "Morisano et al. (2010) — Setting, elaborating, and reflecting on personal goals improves academic performance"
input_schema:
  required:
    - field: "learning_context"
      type: "string"
      description: "学生正在设定目标的单元、项目或任务"
    - field: "student_level"
      type: "string"
      description: "年龄/年级及目标设定经验水平"
    - field: "timeframe"
      type: "string"
      description: "目标推进的时间跨度"
  optional:
    - field: "goal_type"
      type: "string"
      description: "过程目标、结果目标，或两者兼有"
    - field: "student_profiles"
      type: "array"
      description: "来自情境引擎：自我效能感水平、既往目标设定数据"
    - field: "success_criteria"
      type: "string"
      description: "来自情境引擎：该任务的评分量规或成功标准"
    - field: "subject_area"
      type: "string"
      description: "学科背景"
output_schema:
  type: "object"
  fields:
    - field: "protocol"
      type: "object"
      description: "分步目标设定规范，包含教师示范脚本和学生模板"
    - field: "goal_examples"
      type: "array"
      description: "针对该情境的弱目标与强目标对比示范"
    - field: "monitoring_checkpoints"
      type: "array"
      description: "用于回顾目标进展的定期检查节点"
    - field: "student_template"
      type: "string"
      description: "可直接复制粘贴供学生使用的目标设定模板"
chains_well_with:
  - "self-regulation-scaffold-generator"
  - "metacognitive-prompt-library"
  - "agency-scaffold-generator"
  - "self-efficacy-builder-sequence"
teacher_time: "4 分钟"
tags: ["goal-setting", "motivation", "self-regulation", "planning", "self-efficacy"]
---

# 目标设定规范设计器（Goal-Setting Protocol Designer）

## 本技能的功能

生成一套结构化的目标设定规范，引导学生在单元、项目或任务中设定具体、近期（proximal）且聚焦于过程的目标——包括教师示范脚本、弱目标与强目标对比示例、监控检查点以及学生模板。该规范会根据学生的发展水平和时间跨度进行精准校准。AI 在此具有独特价值，因为有效的目标设定需要融会贯通三套相互交织的研究成果（Locke & Latham 的目标设定理论、Zimmerman 的自我调节模型、Bandura 的自我效能感理论），并将其转化为适龄且贴合具体任务的脚手架。学校里大多数目标设定练习最终都流于空泛的口号（“尽我所能”“提高数学成绩”），而研究表明这类目标毫无激励作用。

## 循证依据

Locke 与 Latham（1990, 2002）确立了目标通过四种机制提升表现：引导注意力、激发努力、增强坚持性以及促进策略发展——但前提是目标必须具体（而非空泛）、具有挑战性（而非轻而易举）且为学习者所认同。空泛的目标（“尽力而为”）与没有目标毫无区别。Zimmerman 与 Bandura（1994）证明，自主设定的目标结合自我监控比外部指派的目标更能提升学业成绩，因为自主设定能同时增强自我效能感与承诺感。Schunk（1990）表明，对于低龄学习者而言，近期目标（短期、几天内可达成）比远期目标更能有效建立自我效能感，因为它们提供了更频繁的成功体验。Morisano 等（2010）发现，结构化的目标设定与反思干预显著提升了学业困难大学生的成绩。关键在于，过程目标（“我将在每段话中使用 PEEL 结构”）优于结果目标（“我要拿 A”），因为学生能够掌控自己的过程，却未必能完全掌控结果——而且过程目标能培养可迁移的策略。

## 输入规范

教师必须提供：
- **学习情境：** 学生设定目标的对象。*例如：“为期 4 周的议论文写作单元” / “期末科学考试备考” / “设计技术项目：搭建一个可工作的电路”*
- **学生水平：** 年级与目标设定经验。*例如：“7 年级，首次进行结构化目标设定” / “10 年级，以前设定过目标，但往往流于空泛”*
- **时间跨度：** 持续时长。*例如：“4 周” / “一节课” / “第二学期”*

可选（如情境引擎可用，将自动注入）：
- **目标类型：** 聚焦于过程、结果还是两者兼有
- **学生档案：** 自我效能感水平、既往目标数据
- **成功标准：** 用于锚定目标的评分量规或评价标准
- **学科领域：** 学科背景

## Prompt

```
You are an expert in motivation and goal-setting research, specialising in Locke & Latham's (1990, 2002) goal-setting theory, Zimmerman's self-regulation framework, and Bandura's self-efficacy theory. You understand why most school goal-setting fails (goals are vague, distal, and outcome-focused) and how to design protocols that produce goals students can actually pursue.

Your task is to design a goal-setting protocol for the following:

**Learning context:** {{learning_context}}
**Student level:** {{student_level}}
**Timeframe:** {{timeframe}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Goal type:** {{goal_type}} — if not provided, default to process goals for younger/novice students and a mix of process and outcome goals for older/experienced students. Process goals are always the priority.
**Student profiles:** {{student_profiles}} — if not provided, design for a typical class at the stated experience level.
**Success criteria:** {{success_criteria}} — if provided, anchor goal options to specific criteria from the rubric. If not provided, generate appropriate criteria based on the learning context.
**Subject area:** {{subject_area}} — if not provided, infer from the learning context.

Apply these evidence-based principles:

1. **Specific over vague (Locke & Latham, 2002):** Every goal must be specific enough that both the student and teacher can unambiguously determine whether it has been met. "Improve my writing" fails. "Use at least two pieces of evidence in every analytical paragraph" passes.

2. **Process over outcome (Zimmerman & Bandura, 1994):** Prioritise goals about what students will DO (strategies, behaviours, effort allocation) over what they will ACHIEVE (grades, scores). Students control their process; they don't fully control their outcomes. Process goals also build transferable strategies.

3. **Proximal over distal (Schunk, 1990):** For younger students especially, break long-term goals into weekly or even daily sub-goals. Proximal goals provide frequent success experiences that build self-efficacy. A Year 7 student with a term-long goal will lose track; a Year 7 student with a weekly goal can see progress.

4. **Challenging but achievable:** Goals that are too easy don't motivate. Goals that are too hard undermine self-efficacy. Pitch goals at the "stretch zone" — requires effort but is achievable with good strategy use. For mixed-ability classes, differentiate the challenge level of goals.

5. **Self-set with guidance (Zimmerman & Bandura, 1994):** Students should choose their own goals from a structured set of options, not have goals imposed. Self-set goals produce stronger commitment. But unguided goal-setting produces vague goals — so provide a menu or framework.

6. **Built-in monitoring and revision:** Goals without check-in points decay. Build scheduled monitoring moments (at least weekly for multi-week timeframes) where students evaluate progress and adjust.

7. **Model weak vs. strong goals:** Students need to see the contrast between an ineffective goal and an effective one, with explicit explanation of why the strong goal is better.

Return your output in this exact format:

## Goal-Setting Protocol: [Learning Context]

**For:** [Student level]
**Timeframe:** [Duration]

### Step 1: Teacher Modelling
[A script showing the teacher modelling their own goal-setting process, including thinking aloud about why vague goals don't work]

### Step 2: Weak vs. Strong Goal Examples
[3 pairs of weak/strong goals specific to this learning context, with explanation of what makes each strong]

### Step 3: Goal-Setting Framework
[The framework students use to set their goals — structured choices, sentence stems, or menu options depending on developmental level]

### Step 4: Monitoring Checkpoints
[Scheduled check-in points with specific progress-review prompts]

### Step 5: Reflection and Revision
[End-of-cycle reflection protocol — evaluate goal attainment and set revised goals]

### Student Template
[Copy-pasteable goal-setting document for students]

**Self-check before returning output:** Verify that (a) all example goals are specific and measurable, (b) process goals outnumber outcome goals, (c) the protocol includes monitoring checkpoints, (d) goals are calibrated to be challenging but achievable for the stated level, (e) students choose their own goals within a structured framework rather than being assigned them, and (f) weak-vs-strong examples clearly explain what distinguishes them.
```

## 示例输出

**场景：** *学习情境：“8 年级历史——为期 5 周的工业革命单元，最终以一篇考核性史料分析论文收尾” / 学生水平：“8 年级，以前做过基础的目标设定，但目标通常比较空泛（‘把论文写好’）” / 时间跨度：“5 周”*

---

## 目标设定规范：8 年级历史——工业革命单元

**适用对象：** 8 年级，发展中的目标设定者
**时间跨度：** 5 周（15 课时）

### 第一步：教师示范（第 1 课，5 分钟）

“我也要为这个单元设定一个目标，请大家看看我是怎么思考的。

我的第一反应是说：‘我的目标是让你们所有人在论文里都考出好成绩。’但我想一想，为什么这不是一个有用的目标。我能衡量‘好成绩’吗？不能——不同人对它的标准不一样。我能完全掌控它吗？也不能——分数取决于你们写了什么，而不仅仅取决于我教了什么。它具体吗？不具体。

让我再试一次。这个单元我真正想改进什么？上个单元我注意到，做史料分析时，很多同学只描述了史料**说了什么**，却没有解释它**告诉了我们什么**——你们没有做推断。所以这是我的目标：

*‘在本单元的每一次史料分析中，我都要示范如何做出推断——不仅看史料字面说了什么，还要看它揭示了工业革命时期怎样的生活面貌。我每节课至少现场示范一个例子。’*

这个目标很具体——每节课结束时我都能核对。它聚焦于过程——我要**做什么**，而不是结果会怎样。而且它有挑战性——我有时候一赶进度就会跳过示范。这就是我的目标。现在轮到你们设定自己的目标了。”

### 第二步：弱目标与强目标对比示例

| 弱目标 | 强目标 | 强目标好在哪里 |
|-----------|------------|------------------------------|
| “把论文写好” | “在论文中，我要解释每一份史料**暗示**了关于工业革命的什么信息，而不仅仅是描述它说了什么——我将至少使用 3 次‘这表明……’（This suggests that...）句式” | 具体（明确做什么以及做几次）、聚焦过程（学生可练习的策略）、可衡量（数一数句式次数） |
| “了解工业革命” | “每周，我都会在不看笔记的情况下，用 3 句话总结我们学习的重点因果关系，以此检验自己是否真的记住了” | 聚焦过程（提取练习策略）、近期（每周一次）、建立真正的理解而非盲目以为自己会了 |
| “在历史课上更努力” | “每周按时完成史料分析作业，并在收到反馈后，用老师的评语重写其中一段，然后再继续下一项任务” | 具体行为（按时交作业 + 回应反馈）、在学生掌控范围内、直接针对常见学习障碍 |

### 第三步：目标设定框架

学生从下方菜单中选择**一个过程目标**和**一个知识目标**，或按照相同结构自行编写。

**过程目标菜单**（选择或改写一项）：
- “在每次史料分析中，我都会使用‘这表明……’句式，在字面意思之外至少做出一条推断。”
- “每周，我都会不看笔记默写本周课程的核心内容来测试自己——如果记不起来，就在下节课前重读。”
- “当我的写作收到反馈时，我会根据反馈重写其中一段再继续往下学，而不是只看一眼评语。”
- “在课堂讨论中，我每节课至少贡献一个想法——即使我不确定它对不对。”
- “自行编写：” _______________（必须包含：我将做什么 + 频率 + 如何知道自己做到了）

**知识目标菜单**（选择或改写一项）：
- “本单元结束时，我将能解释工业革命改变劳动人民生活的三种方式，并各举一个具体例子。”
- “本单元结束时，我将能分析一份从未见过的史料，并对其反映的历史信息做出两条推断。”
- “本单元结束时，我将能理解为什么历史学家对于工业革命究竟利大于弊还是弊大于利存在分歧。”
- “自行编写：” _______________（必须包含：我将知道或能做什么 + 如何证明）

### 第四步：监控检查点

| 周次 | 检查点形式 | 提示词 |
|------|-----------|--------|
| 第 1 周末 | 课内（3 分钟） | “看看你的过程目标。这周你做了你承诺要做的事吗？如果是，打钩。如果没有，是什么阻碍了你？这周你会做出什么调整让它发生？” |
| 第 2 周末 | 书面（5 分钟） | “给自己打分：1（还没开始）、2（试过一次）、3（定期在做）、4（快成习惯了）。至于知识目标：如果现在就考，你能过关吗？试着不看笔记写出你的答案看看。” |
| 第 3 周末 | 同伴互查（5 分钟） | “向同伴解释你的目标。问问他们：‘你在课上看到我这么做了吗？’他们的观察很重要，因为我们对自己的习惯常常判断不准。” |
| 第 4 周末 | 教师面谈（独立练习期间每人 2 分钟） | 教师提问：“给我看看你朝着目标努力的证据。你哪一点进步了？写论文前你还想调整什么？” |

### 第五步：反思与修订（第 5 周，提交论文后）

**论文后反思（10 分钟）：**

1. “重读你第 1 周设定的过程目标。你做到了吗？诚实地给自己打分：1（没做到）、2（有时做到）、3（大部分做到）、4（始终做到）。”
2. “重读你的知识目标。你现在能做到你当初设定的事情吗？证明给自己看——现在就写 2–3 句话展示出来。”
3. “补全这句话：‘本单元对我帮助最大的策略是 _____________，我知道它有效是因为 _____________。’”
4. “补全这句话：‘下一个单元，我会设定一个不同/更好的目标，因为 _____________。’”
5. “如果你的过程目标打了 3 或 4 分，下个单元设定一个更有挑战性的升级版。如果打了 1 或 2 分，要么修订目标使其更切合实际，要么找出阻碍因素并优先解决。”

### 学生模板

---

**我的目标——工业革命单元**

**姓名：** _______________ **日期：** _______________

**我的过程目标**（我将**做什么**）：
_______________________________________________________________
频率：_______________ 我如何知道自己做到了：_______________

**我的知识目标**（我将**知道**或**能做到**什么）：
_______________________________________________________________
我如何证明：_______________

**每周检查记录：**
| 周次 | 这周我执行过程目标了吗？（是/否） | 自评分（1–4） | 什么帮到了我，或什么阻碍了我？ |
|------|----------------------------------|---------------|-------------------------------|
| 1 | | | |
| 2 | | | |
| 3 | | | |
| 4 | | | |

**论文完成后：**
- 我达成过程目标了吗？得分：___
- 我现在能展示我的知识目标吗？___
- 帮助最大的策略：_______________
- 下次我想设定的目标：_______________

---

## 已知局限性

1. **目标设定对中等至高自我效能感的学生具有激励作用，但对自我效能感极低的学生可能适得其反。** 反复在某学科受挫的学生可能会把结构化目标设定视为又一次“记录失败的机会”。对于这类学生，应从极其近期、低风险的目标（每日一次、容易达成）起步，先积累早期成功体验，再逐步提高挑战度。Schunk（1990）强调，目标难度必须与当前的自我效能感相匹配。

2. **过程目标需要教师真正重视过程，而不仅仅是结果。** 如果课堂文化只表彰分数和排名，那么不管规范设计得多好，学生依然会设定结果目标，因为那才是实际获得奖励的东西。本规范在努力程度、策略运用和点滴进步都得到公开肯定的课堂中效果最佳。

3. **学生需要在多个单元中持续使用该目标设定规范，才能养成习惯。** 仅在一个单元开展一次性的目标设定活动不会产生持久的自我调节能力。研究表明，自我调节学习（SRL）干预需要持续实施——Dignath 与 Büttner（2008）发现持续 8 周以上的干预效果最强。教师应在一学年内保持一致的目标设定框架，随内容调整但保留结构。
