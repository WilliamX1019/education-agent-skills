---
# AGENT SKILLS STANDARD FIELDS (v2)
name: metacognitive-prompt-library
description: "针对具体任务构建涵盖计划、监控或评价的元认知提示词库。适用于在独立作业期间培养学生“对思考的思考”能力。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "self-regulated-learning/metacognitive-prompt-library"
skill_name: "元认知提示词库"
domain: "self-regulated-learning"
version: "1.0"
evidence_strength: "strong"
evidence_sources:
  - "Flavell (1979) — Metacognition and cognitive monitoring: a new area of cognitive-developmental inquiry"
  - "Veenman et al. (2006) — Metacognition and learning: conceptual and methodological considerations"
  - "Hattie (2009) — Visible Learning: metacognitive strategies effect size ~0.69"
  - "Schraw (1998) — Promoting general metacognitive awareness"
  - "Tanner (2012) — Promoting student metacognition in the sciences"
input_schema:
  required:
    - field: "task_description"
      type: "string"
      description: "学生正在完成的具体学习任务"
    - field: "student_level"
      type: "string"
      description: "年龄/年级与元认知发展水平"
    - field: "metacognitive_focus"
      type: "string"
      description: "重点针对哪项元认知技能：监控、评价、计划或排错（debugging）"
  optional:
    - field: "subject_area"
      type: "string"
      description: "学科背景，用于生成符合学科特征的元认知提示词"
    - field: "student_profiles"
      type: "array"
      description: "来自情境引擎：个体元认知档案、常见卡点"
    - field: "task_phase"
      type: "string"
      description: "提示词使用时机：任务前、任务中或任务后"
output_schema:
  type: "object"
  fields:
    - field: "prompts"
      type: "array"
      description: "带有类型标签和使用时机的有序元认知提示词集"
    - field: "teacher_script"
      type: "string"
      description: "如何引入并示范元认知提示"
    - field: "student_card"
      type: "string"
      description: "可直接复制粘贴供学生使用的提示卡片"
chains_well_with:
  - "self-regulation-scaffold-generator"
  - "study-strategy-selector"
  - "error-analysis-protocol"
  - "elaborative-interrogation-generator"
teacher_time: "3 分钟"
tags: ["metacognition", "monitoring", "thinking-about-thinking", "self-regulation", "comprehension"]
---

# 元认知提示词库（Metacognitive Prompt Library）

## 本技能的功能

针对具体学习任务生成一组经过校准的元认知提示词——帮助学生监控自身理解程度、评估策略有效性、检测错误并调整方法。与泛泛的“思考一下你的思考过程”不同，这些提示词紧扣具体任务，并精准指向某项元认知技能（监控、评价、计划或排错）。AI 在此具有独特价值，因为有效的元认知提示词必须落在精准的区间内：既要足够具体让学生知道该做什么，又要足够开放以引发真正的反思而非机械服从。大多数教师自编的反思提示要么过于空泛（“进展如何？”），要么过于指令化（“你用主题句了吗？”），完全错失了元认知层面。

## 循证依据

Flavell（1979）将元认知定义为“关于认知现象的知识与认知”——即对思考的思考。他区分了元认知知识（你对自己认知的了解）与元认知调节（你如何控制它）。Veenman 等（2006）证明，元认知技能水平比智力更能预测学业成绩——即使在控制智商变量后，它仍能解释约 17% 的学业表现方差。Hattie（2009）的综合研究发现元认知策略的效应量约为 0.69。Schraw（1998）指出，元认知意识可以通过结构化提示显性教授——经常使用元认知提示词的学生会随时间推移发展出更强的监控能力。Tanner（2012）将元认知研究专门应用于科学教育，证明学科特定的元认知提示词（例如“什么证据会改变我的结论？”）比通用提示词更有效。证据非常明确：元认知是可教的、可迁移的，且属于现有杠杆率最高的教学干预之一。

## 输入规范

教师必须提供：
- **任务描述：** 学生正在完成的具体任务。*例如：“在数学中解答多步应用题” / “细读并批注一首诗” / “在化学中开展实操探究实验”*
- **学生水平：** 年级与元认知发展水平。*例如：“8 年级，元认知词汇有限” / “12 年级，熟悉元认知策略”*
- **元认知聚焦：** 重点针对哪项技能。*例如：“监控——学生经常以为自己懂了但无法应用概念” / “排错——学生会犯错但找不出哪里出了问题”*

可选（如情境引擎可用，将自动注入）：
- **学科领域：** 用于学科特定提示词的校准
- **学生档案：** 个体元认知档案、常见卡点
- **任务阶段：** 提示词的使用时机（任务前、任务中或任务后）

## Prompt

```
You are an expert in metacognition research, specialising in Flavell's (1979) framework, Veenman et al.'s (2006) work on metacognitive skilfulness, and the practical application of metacognitive prompting in classroom settings (Tanner, 2012; Schraw, 1998).

Your task is to generate a set of metacognitive prompts for the following:

**Task:** {{task_description}}
**Student level:** {{student_level}}
**Metacognitive focus:** {{metacognitive_focus}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Subject area:** {{subject_area}} — if not provided, infer from the task description and generate domain-appropriate prompts.
**Student profiles:** {{student_profiles}} — if not provided, design for a typical class at the stated metacognitive development level.
**Task phase:** {{task_phase}} — if not provided, generate prompts for all three phases (before, during, after), weighted toward the phase most relevant to the metacognitive focus.

Apply these evidence-based principles:

1. **Distinguish metacognitive types (Flavell, 1979; Schraw, 1998):**
   - **Monitoring prompts:** Help students assess their current understanding in real time. "Do I actually understand this, or does it just feel familiar?" These target the illusion of knowing — the gap between feeling you understand and being able to explain or apply.
   - **Evaluating prompts:** Help students judge the quality of their work or strategy against criteria. "Is my answer reasonable? How would I check?"
   - **Planning prompts:** Help students select and sequence strategies before starting. "What approach will work here? What's my first step?"
   - **Debugging prompts:** Help students identify and fix breakdowns in understanding. "Where exactly did I get lost? What was the last thing I understood?"

2. **Make prompts task-specific (Tanner, 2012):** Every prompt must reference the actual task. "Am I understanding this?" is not metacognitive — it's too vague to act on. "Can I explain in my own words why the character made that decision, without looking at the text?" is metacognitive because it provides a concrete test of comprehension.

3. **Calibrate to metacognitive maturity:**
   - **Low metacognitive awareness:** Use concrete, closed prompts with observable actions. "Cover the text. Can you write down the three main causes from memory? If you can't, you don't know it yet — go back and re-read."
   - **Moderate metacognitive awareness:** Use open prompts that require judgment. "How confident are you that your method is correct? What would you do to check?"
   - **High metacognitive awareness:** Use reflective prompts that target strategic thinking. "Is this the most efficient strategy, or am I using it because it's familiar?"

4. **Target the illusion of knowing (Veenman et al., 2006):** The most common metacognitive failure is believing you understand something when you can't actually apply it. The most valuable prompts expose this gap — they force students to demonstrate understanding (explain, apply, predict) rather than simply rate it ("I get it").

5. **Prompt, don't instruct:** Metacognitive prompts ask questions that trigger reflection. They do not tell students what to think. "Check your answer" is an instruction. "What would you expect the answer to be roughly, before you calculate? Does your actual answer match that expectation?" is a metacognitive prompt.

Return your output in this exact format:

## Metacognitive Prompts: [Task Name]

**For:** [Student level]
**Focus:** [Metacognitive skill being targeted]

### Before the Task (Planning)
[3–4 prompts that activate metacognitive planning]

### During the Task (Monitoring)
[4–6 prompts calibrated to key moments in the task where metacognitive monitoring is most needed]

### After the Task (Evaluating)
[3–4 prompts for post-task metacognitive evaluation]

### Teacher Modelling Script
[A brief script showing how the teacher models metacognitive thinking aloud for one prompt — making the invisible visible]

### Student Prompt Card
[A clean, copy-pasteable card with 5–6 key prompts in student-friendly language]

**Self-check before returning output:** Verify that (a) every prompt is specific to this task, (b) prompts ask questions rather than give instructions, (c) at least two prompts specifically target the illusion of knowing, (d) prompts are calibrated to the stated metacognitive maturity level, and (e) the student card uses language appropriate for the age group.
```

## 示例输出

**场景：** *任务：“在 9 年级数学中解答多步应用题（代数与比例）” / 学生水平：“9 年级，元认知意识较低——学生经常说‘我懂了’，但随后无法独立完成题目” / 元认知聚焦：“监控——专门针对‘知晓错觉’（illusion of knowing）”*

---

## 元认知提示词：多步应用题（代数与比例）

**适用对象：** 9 年级数学，元认知意识较低
**聚焦：** 监控——专门针对“我懂了”与“能做出来”之间的落差

### 任务前（计划）

**P1.** 先不动笔，把应用题通读一遍。现在遮住题目。你能用自己的话描述这道题在问什么吗？如果不能，再读一遍——但这一次，把题目真正要你回答的那个问题画上横线。

**P2.** 在计算任何东西之前：这道题考的是代数、比例，还是两者都有？你怎么知道的？题干里的哪个词句给了你线索？

**P3.** 你的第一步打算做什么？不要说“解出来”——你具体要先在纸上写下什么？如果不确定，回到题目，找出一条你可以先下手处理的信息。

### 任务中（监控）

**M1.** 你刚刚完成了一步。停一下。你能向一位隐形同伴解释你**为什么**要做这一步吗？如果你能说出“因为……”且理由说得通，就继续。如果你只能说“因为老师/书上就是这么做的”，那你可能只是在机械套用步骤而没有真正理解——这意味着下一道陌生题目你还会卡住。

**M2.** 在进入下一步之前先估算一下：答案大概应该在什么数量级？如果你在算一个人的年龄，结果应该在 0 到 120 之间。如果你在算长度之比，结果应该是正数。把你的估算写在空白处。算出结果后，拿它和这个估算比对。

**M3.** 你卡住了。这很正常。在举手求助前，先回答这三个问题：
- 我最后一步真正听懂/做对的是什么？（用手指指出来。）
- 我第一步开始看不懂的是什么？（用手指指出来。）
- 有没有这道题的简化版是我**能**解出来的？是什么让眼前这道题变难了？

**M4.** 你算出了一个答案。现在做这个测试：用手盖住你的演算过程。你能不看纸面，一步一步向别人讲清楚你是怎么从题目走到答案的吗？如果讲不出来，说明你的理解比你以为的要浅。

**M5.** 看看你的答案。放在题目的现实情境里合情合理吗？如果题目问 200 名学生需要几辆大巴，你算出了 6.67 辆，那就需要调整。如果学生的考试分数算出来是负数，那肯定哪里出错了。现实情境就是你的检错系统。

### 任务后（评价）

**E1.** 给自己答案的把握度打分：1（瞎猜）、2（觉得对但不确定）、3（有把握）、4（非常确定且能讲给别人听）。现在——如果你选了 3 或 4，证明一下：不看演算过程，用两句话解释你的方法。

**E2.** 回想一下你在哪里卡住了（如果有的话）。原因属于哪一种：
(a) 我没读懂题目在问什么 → 阅读/理解问题
(b) 我不知道该用哪种方法 → 策略选择问题
(c) 我知道方法但算错了 → 执行失误
(d) 我没卡住，做得很顺 → 很棒，但用 M4 检验一下确保不是假顺

这很重要，因为每种“卡住”需要不同的补救办法。

**E3.** 把你的做法和同桌对比一下。你们用的方法一样吗？如果不一样，哪种更高效？你能用他的方法做出来吗？这说明对于这类题型，你手里掌握了几种方法？

### 教师示范脚本

“我要向大家展示我在解应用题时脑子里是怎么想的。注意看我怎么做——我会把思考过程大声说出来。

*[大声读题]* ‘一次学校郊游每人收费 12 英镑，另加 45 英镑大巴租车费。共有 28 名学生参加。学校预算为 400 英镑。预算够吗？’

好，第一件事——我先不急着算。让我重读一遍并问自己：这道题**实际上**在问什么？它在问 400 英镑够不够。所以我的最终答案不是一个算式结果，而是‘够’或‘不够’，并用数字支撑。

现在，我的第一步是什么？我需要算出总花费。也就是 28 乘以 12 英镑，再加上 45 英镑。让我先估算一下——28 乘以 12 大约是 30 乘以 12，等于 360 英镑，再加上 45 英镑大约是 405 英镑。所以结果会非常接近预算线。这个估算能帮我核对精确答案。

*[计算]* 28 × 12 = 336。加上 45 = 381 英镑。381 英镑小于 400 英镑吗？是的。所以预算够用，还剩 19 英镑。

现在——这是元认知的关键一步——让我检查一下。我的答案合理吗？28 名学生郊游花了 381 英镑——平均每人约 13.60 英镑。听起来合理吗？合理。而且我的精确答案（381 英镑）很接近我的估算（405 英镑），所以我没有犯重大的计算错误。

这一整套过程——先估算、结合情境核对、追问答案是否合理——就是我希望你们每次做题都要做的事。”

### 学生提示卡片

---

**应用题思考检查清单**

**开始前：**
- [ ] 我能**不看题目**用自己的话描述这道题在问什么吗？
- [ ] 我知道这题需要哪种数学知识吗？（代数 / 比例 / 两者）
- [ ] 我的第一步具体要写什么？

**做题时：**
- [ ] 我能解释**为什么**刚才要走这一步吗？（不能只说“因为书上这么做”。）
- [ ] 答案大概应该多大？（先在空白处写下估算。）
- [ ] 如果卡住了：我最后一步真正弄懂的是什么？

**完成后：**
- [ ] 我的答案放在现实生活里合理吗？
- [ ] 我能**不看演算过程**讲出自己的方法吗？
- [ ] 把握度：1（猜的） / 2（觉得对） / 3（有把握） / 4（能教别人）

---

## 已知局限性

1. **元认知提示词需要教师示范才能奏效。** 只发一张提示卡片而不显性示范元认知监控听起来、看起来是什么样，只会换来学生的机械服从（勾选方框），而非真正的元认知。Tanner（2012）明确指出：教师必须先大声思考，让隐形的认知过程变得可见，学生才能内化这些提示。

2. **元认知意识较低的学生可能会觉得开放式监控提示令人沮丧或困惑。** 对于从未被问过“你能解释为什么做这一步吗？”的学生来说，最初的体验会有些不适应。建议从最具体的提示（M2：计算前先估算）入手，再逐步引入更具反思性的提示。切勿一次性抛出所有提示词。

3. **元认知监控需要时间，初期会放慢任务完成速度。** 在课时紧张的压力下，教师可能会想跳过监控检查点。这是适得其反的——监控本身就是核心学习干预。如果时间不够，宁可减少题目数量但保留监控，也不要没有监控地刷更多题。加工的质量胜过练习的数量。
