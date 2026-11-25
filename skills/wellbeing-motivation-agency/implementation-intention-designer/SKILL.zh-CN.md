---
# AGENT SKILLS STANDARD FIELDS (v2)
name: implementation-intention-designer
description: "为学生的具体行为改变目标创建“如果-那么”（if-then）执行意图与 WOOP 计划。适用于学生知道该做什么、但难以坚持习惯或常规的场合。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "wellbeing-motivation-agency/implementation-intention-designer"
skill_name: "执行意图设计器"
domain: "wellbeing-motivation-agency"
version: "1.0"
evidence_strength: "strong"
evidence_sources:
  - "Gollwitzer (1999) — Implementation intentions: strong effects of simple plans"
  - "Gollwitzer & Sheeran (2006) — Implementation intentions and goal attainment: a meta-analysis"
  - "Duckworth et al. (2013) — From self-control to self-regulation: a declaration of independence"
  - "Oettingen & Gollwitzer (2010) — Strategies of setting and implementing goals: mental contrasting and implementation intentions"
  - "Bettinger et al. (2012) — The role of application assistance and information in college decisions"
input_schema:
  required:
    - field: "target_behaviour"
      type: "string"
      description: "学生需要培养的具体行为或习惯——他们应当开始做什么或停止做什么"
    - field: "student_level"
      type: "string"
      description: "年龄/年级"
  optional:
    - field: "current_barrier"
      type: "string"
      description: "目前阻碍学生做出目标行为的具体障碍"
    - field: "context"
      type: "string"
      description: "面向单个学生、小组还是全班"
    - field: "student_profiles"
      type: "array"
      description: "来自情境引擎：先前行为模式、目标、自我调节能力"
    - field: "subject_area"
      type: "string"
      description: "如果执行意图与学业相关，所属的课程学科"
    - field: "time_horizon"
      type: "string"
      description: "行为改变需要维持多久——一节课、一周、一学期"
output_schema:
  type: "object"
  fields:
    - field: "implementation_intention"
      type: "object"
      description: "具体的“如果-那么”计划——触发线索、行为与情境"
    - field: "mental_contrasting"
      type: "object"
      description: "WOOP 框架——愿望（Wish）、结果（Outcome）、障碍（Obstacle）、计划（Plan）"
    - field: "student_script"
      type: "string"
      description: "供学生书写、口述或演练的精确措辞"
    - field: "monitoring_plan"
      type: "object"
      description: "如何追踪执行意图是否被使用以及是否有效"
chains_well_with:
  - "self-efficacy-builder-sequence"
  - "agency-scaffold-generator"
  - "self-regulated-learning-strategy-selector"
  - "metacognitive-prompt-generator"
teacher_time: "2 分钟"
tags: ["implementation-intentions", "Gollwitzer", "if-then-plans", "WOOP", "habits", "self-regulation", "behaviour-change"]
---

# 执行意图设计器（Implementation Intention Designer）

## 本技能的功能

设计具体的“如果-那么”（if-then）计划（即执行意图，implementation intentions），帮助学生跨越“有想法”与“付诸行动”之间的鸿沟——将空泛的目标（“我要多复习”）转化为具体、绑定特定情境的行动方案（“如果在上学日的下午 4 点坐在书桌前，那么我就花 25 分钟针对最薄弱的学科做间隔提取练习”）。Gollwitzer 研究的核心洞见在于：有些学生内心已经认同了目标，但需要一个明确**何时、何地、如何**行动的计划；使用前需先确认这符合学习者的实际情况。执行意图通过预先加载决策来自动化行动：学生提前决定好在特定情境下具体做什么，从而减少临场犹豫，尽管这并不保证百分之百落实。输出包括标准“如果-那么”格式的执行意图、强化承诺感的心理对比练习（WOOP：愿望、结果、障碍、计划）、可直接演练的学生脚本以及监测计划。AI 在此具有独特价值，因为制定有效的执行意图需要精准锁定情境触发线索（不是“等我有心情时”，而是“晚饭后坐到书桌前时”）、预判障碍并将行为校准到切实可行的尺度——这种精确性是泛泛的目标设定建议所欠缺的。

## 循证依据

Gollwitzer（1999）证明，执行意图——将情境线索与目标行为绑定的具体“如果-那么”计划——能大幅提高付诸行动的概率。他的元分析（Gollwitzer & Sheeran, 2006）跨越 94 项研究发现了中等偏大的效应量（d = 0.65）：制定了执行意图的人比动机相同但缺乏具体计划的人显著更有可能达成目标。其认知机制在于：“如果-那么”格式在情境（“如果”）与行为（“那么”）之间建立了心理联结，使得遇到线索时计划好的行动更容易被激活，减少了当下的犹豫消耗；当然，这并不能消除外部客观障碍或保证必然行动。Oettingen 与 Gollwitzer（2010）将执行意图与心理对比（WOOP）结合，证明两者结合比单独使用任何一种都更有效：心理对比产生承诺感（让人意识到障碍是真实的、自己确实需要计划），而执行意图提供了具体的行动方案。Duckworth 等（2013）将其应用于教育领域，证明执行意图有助于学生改善学习习惯、按时完成作业与备考。Bettinger 等（2012）研究了大学申请过程中的协助与信息支持；解决实际障碍的辅助措施是相关背景，但并非本“如果-那么”脚本的直接证据，也不能将入学率效应直接套用到本脚本上。

## 输入规范

教师必须提供：
- **目标行为：** 学生需要做到的事。*例如：“在布置作业当天就开始做，而不是拖到截止前一晚” / “复习时使用提取练习，而不是反复重读笔记” / “在课堂讨论中举手发言，而不是一直保持沉默” / “当察觉考试焦虑时，使用学习者自选且感到舒适的支持策略”*
- **学生水平：** 年级。*例如：“10 年级”*

可选（如情境引擎可用，将自动注入）：
- **当前障碍：** 阻碍该行为的因素
- **情境：** 个人、小组或全班
- **学生档案：** 先前行为模式、目标
- **学科领域：** 所属学科
- **时间跨度：** 行为改变需要维持多久

## Prompt

```
You are an expert in implementation intentions and behaviour change, with deep knowledge of Gollwitzer's (1999) if-then planning research, Gollwitzer & Sheeran's (2006) meta-analysis, Oettingen & Gollwitzer's (2010) WOOP framework (mental contrasting + implementation intentions), and Duckworth et al.'s (2013) application to educational settings. You understand that implementation intentions work because they automate decisions — the student decides in advance what they will do in a specific situation, potentially reducing deliberation in the moment, not guaranteeing action.

IMPORTANT: Implementation intentions must be SPECIFIC. "I will try harder" is a goal intention, not an implementation intention. "If I sit down at my desk after dinner, then I will open my revision folder and do 15 minutes of flashcard practice" is an implementation intention. The power is in the specificity: a precise situational cue ("if") linked to a precise behaviour ("then").

IMPORTANT: The "if" must be a specific, recognisable cue, not vague permission to act only when motivated. A feasible time/place cue or an internal cue the learner reliably notices (such as the urge to switch away) can work as a planning cue. Test its reliability with the learner; no cue guarantees action.

Your task is to design implementation intentions for:

**Target behaviour:** {{target_behaviour}}
**Student level:** {{student_level}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Current barrier:** {{current_barrier}} — if absent, offer tentative possibilities for learner confirmation; do not invent a personal barrier.
**Context:** {{context}} — if not provided, design for an individual student.
**Student profiles:** {{student_profiles}} — if not provided, design for a typical student at this level.
**Subject area:** {{subject_area}} — if not provided, design for general academic use.
**Time horizon:** {{time_horizon}} — if not provided, design for sustained behaviour change (one term).

First confirm the student endorses the goal and the proposed action is accessible. A teacher-selected target is not automatically the student's WOOP wish. If endorsement or the barrier is unknown, provide a provisional plan for discussion rather than putting invented motives in the student's voice. Check external barriers (time, space, care duties, access) and arrange practical support; don't recast them as an inner failure. Preserve required support and learning goals.

Optional chaining note: self-regulated-learning-strategy-selector and metacognitive-prompt-generator are not supplied library skills; neither is required to use this plan.

Apply these principles:

1. **Craft the if-then plan (Gollwitzer, 1999):**
   - **If:** A specific cue the learner can recognise reliably; a feasible time/place or a clearly noticed internal obstacle. "If it's 4pm and I'm at my desk" is better than "If I have free time."
   - **Then:** A specific, doable action. "Then I will open my revision folder and complete 5 flashcards" is better than "Then I will revise."
   - Make the start small and achievable; refusal or difficulty is a reason to check fit and barriers, not to presume poor motivation. Starting is harder than continuing — design the "then" to overcome the starting barrier.

2. **Use mental contrasting — WOOP (Oettingen & Gollwitzer, 2010):**
   - **Wish:** What does the learner want to achieve? Confirm endorsement rather than scripting a teacher's goal as their wish.
   - **Outcome:** What would be the best thing about achieving it? (The motivation.)
   - **Obstacle:** After checking external barriers, invite the learner to identify an internal obstacle if one fits (e.g. an urge to switch activities). If none is known, record unknown/not applicable and the practical support needed; do not invent one.
   - **Plan:** If [obstacle], then [strategy]. This is the implementation intention.
   - WOOP works because mental contrasting (imagining the positive outcome AND the real obstacle) creates commitment — the student recognises that the obstacle is real and that they need a plan.

3. **Anticipate obstacles (Gollwitzer & Sheeran, 2006):**
   - For each implementation intention, design a "coping plan": If the obstacle occurs, then...
   - Common obstacles: distraction (phone, siblings, TV), fatigue, forgetting, negative self-talk ("What's the point?").
   - Each obstacle gets its own if-then plan.

4. **Make it rehearsable:**
   - Implementation intentions work best when the student says or writes the if-then plan repeatedly.
   - Offer accessible rehearsal by writing, speaking or visualising; use the learner's preferred mode without requiring all three.
   - Physical artefacts (a card on the desk, a phone alarm with the plan as the label) serve as external triggers.

5. **Design monitoring (Duckworth et al., 2013):**
   - Simple tracking: did the student do the behaviour when the cue occurred? Yes/no.
   - A weekly check-in: "How many times this week did the situation arise? How many times did you follow through?"
   - Adjust the plan if follow-through is low — the plan may be too ambitious, the cue unreliable, the goal not endorsed, or an external barrier unresolved.

Return your output in this exact format:

## Implementation Intention: [Target Behaviour]

**Target behaviour:** [What the student needs to do]
**For:** [Student level]

### The Implementation Intention

**If** [specific situational cue], **then** [specific behaviour].

[Explanation of why this cue and this behaviour are chosen]

### WOOP Framework

**Wish:** [The goal]
**Outcome:** [Best thing about achieving it]
**Obstacle:** [Learner-confirmed inner obstacle, unknown/not applicable, and any external support needed]
**Plan:** If [obstacle], then [strategy]

### Student Script

[The exact words the student should write, say, or rehearse — ready to use]

### Coping Plans

For each likely obstacle:
**If** [obstacle], **then** [coping strategy].

### Monitoring Plan

[How to track whether the plan is working — what to measure, when to check, when to adjust]

**Self-check before returning output:** Verify that (a) the "if" is a specific, recognisable external or internal cue, (b) the "then" is a specific, small, doable action, (c) the wish is learner-endorsed and any inner obstacle is confirmed, with external barriers addressed, (d) coping plans address the most likely obstacles, and (e) the monitoring plan is simple enough for the student to maintain.
```

## 示例输出

**场景：** *目标行为：“复习时使用提取练习，而不是反复重读笔记——学生目前通过划重点和重读来‘复习’，感觉很努力但记忆保持很差” / 学生水平：“10 年级” / 当前障碍：“学生知道提取练习更有效（听老师讲过），但还是习惯性退回重读，因为重读感觉更轻松舒适——重读带来熟悉感错觉，让人以为自己学会了” / 时间跨度：“在一个学期内为 GCSE 备考养成习惯”*

---

## 执行意图：复习时运用提取练习

**目标行为：** 复习时使用提取练习（自我测试），而非反复重读
**适用对象：** 10 年级

### 执行意图

以下为针对“认同该复习目标且确认存在上述障碍”的学习者设计的示例草案；具体时长与措辞可协商调整，并保留所需的辅助工具或其他无障碍支持。

**如果**我坐到书桌前准备开始复习，**那么**我会先合上笔记，打开一张空白纸，不看资料花 5 分钟把关于这个主题能记住的一切都写下来，然后再翻开笔记。

选择这个触发线索的原因在于，“坐到书桌前准备复习”是一个具体、可观察的瞬间，每次复习都会发生。目标行为（合上笔记、打开白纸、凭记忆默写）具体到无需临时纠结。而“5 分钟”的限时让任务显得容易上手——学生不是在承诺连续做一小时高强度提取练习，而只是在干别的之前先做 5 分钟“大脑倾倒”（brain-dump）。一旦开了头，继续下去就比开头容易得多。

### WOOP 框架

**愿望（Wish）：** 我希望高效复习准备 GCSE 考试，真正记住我学过的内容。

**结果（Outcome）：** 达成后最棒的感受是走进考场时心里踏实有底，因为我**确信**自己记住了材料——不仅仅是看着眼熟，而是真能回忆并调动出来。我会少很多焦虑，更有掌控感。

**障碍（Obstacle）：** 我主要的内在障碍是重读感觉更轻松、更舒适。重读笔记时一切看起来都很眼熟，让我产生“我都懂了”的错觉。而提取练习感觉更费力、更不舒服——我想不起来所有内容，这让我觉得自己好像什么都不会。为了逃避这种不适感，我又退回到了重读。

**计划（Plan）：** **如果**我感到冲动想直接重读而不是自测，**那么**我会对自己说：“费力不等于没学会。我会先做一次简短的提取尝试，核对一下，然后针对还没记住的部分去学或求助。阅读可以帮助我学习原本还不懂的内容。”

### 学生脚本

把这段话抄在卡片上，放在你的复习书桌上：

“**每次我坐下来复习时：**
1. 合上笔记
2. 拿出一张白纸
3. 写下能记住的所有内容，限时 5 分钟
4. **然后**再打开笔记，核对漏掉了什么
5. 把接下来的复习重点放在**漏掉的内容**上——那才是真正产生学习的地方

**当我觉得太难、想直接重读时：**
卡住是信息反馈，不是没学会的证明。我可以缩短这次尝试的时间、核对笔记、结合反馈练习或主动求助。”

### 应对预案（Coping Plans）

**如果**我坐下来复习时习惯性地立刻翻开了笔记，**那么**我会动手合上笔记本，深呼吸一次，再开始白纸默写。（动手合上笔记本的物理动作就是新行为的触发器。）

**如果**我做完默写发现几乎什么都记不起来（感到很受挫），**那么**我会提醒自己：“我刚刚找出的这些空白，正是这次复习最有价值的部分。现在我**精确知道**该学什么了。”随后我会查阅笔记或样例，学习缺失的内容并重新测试其中一小块；如果缺口依然存在，我会主动求助。

**如果**我太累了实在不想做提取练习，**那么**我会做一个**缩小版**：把 5 分钟默写缩成 2 分钟。同时核查是否更需要休息、更短的任务或实际支持；计划必须契合学习者的真实处境。

**如果**到周末我发现这一周一次提取练习都没用上，**那么**我不会自责（自责只会导致彻底逃避），而是立刻在手机上定一个周一 16:00 的闹钟，标签写着：“合上笔记。白纸。5 分钟。开始。”重新起步永远胜过半途而废。

### 监测计划

**每日记录：** 每次复习结束后，在简易追踪表上打勾：“我今天是用大脑倾倒开头的吗？是 / 否。”把追踪表放在显眼处——书桌上或手机主屏。

**每周回顾：** 每周末统计：这周我复习了几次？其中几次是以提取练习开头的？如实记录实际机会与使用次数，切勿捏造进步趋势。目标是养成有用的常规，而非追求必须逐周攀升的曲线；同时也要检验后续回忆效果与实际帮助度。

**两周复盘：** 教师（或学生本人）回顾：“提取练习开始变得自动化了吗？我还需要桌上的提示卡吗，还是已经不假思索就会这么做了？”不需要提示卡可能提示熟悉度提高；请向学习者核实并观察多次重复使用，切勿仅凭单一迹象就宣称已成习惯。

**参考复盘触发线（非实证阈值）：** 如果落实率较低（例如两周后低于 50%），或在学习者有意愿、计划难以执行时提前复盘。可能调整方向：触发线索不可靠（更换时间或地点）、行为门槛过高（缩减为 2 分钟），或障碍尚未解决（在制定新应对预案前，先重新核查学习者对目标的认同度、外部限制以及已确认的内在障碍）。

---

## 已知局限性

1. **执行意图在学习者原本已有一定动机时效果最佳。** 如果学生对复习完全漠不关心，“如果-那么”计划无法凭空创造动机——它搭建的是从“有意愿”到“去行动”的桥梁，而不是从“冷漠”到“有意愿”的桥梁。对于缺乏动机的学生，请先配合使用“动机诊断与任务重设计”（Motivation Diagnostic & Task Redesign）技能，再设计执行意图。

2. **执行意图最适用于简单、离散的具体行为。** “用提取练习开启复习”是一个清晰、离散的动作；“成为一名更优秀的学生”则过于庞杂，无法用单一执行意图承载。复杂的行为改变需要针对不同具体动作制定多条执行意图。

3. **外部客观障碍会压倒执行意图。** 如果学生的家庭环境根本无法支持复习（没有安静空间、需要照顾家人、家庭突发变故），设计得再完美的执行意图也无济于事。教师必须了解学生的真实处境，在指望仅靠计划改变行为之前，先协助解决环境障碍。
