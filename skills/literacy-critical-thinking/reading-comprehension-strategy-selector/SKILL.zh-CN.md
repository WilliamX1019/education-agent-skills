---
# AGENT SKILLS STANDARD FIELDS (v2)
name: reading-comprehension-strategy-selector
description: "根据特定文本的挑战与要求选择并排序阅读理解策略。适用于学生在阅读文本遇到困难或需要针对性阅读支持时。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "literacy-critical-thinking/reading-comprehension-strategy-selector"
skill_name: "阅读理解策略选择器"
domain: "literacy-critical-thinking"
version: "1.0"
evidence_strength: "strong"
evidence_sources:
  - "Duke & Pearson (2002) — Effective practices for developing reading comprehension"
  - "Pressley (2002) — Metacognition and self-regulated comprehension"
  - "National Reading Panel (2000) — Teaching children to read: an evidence-based assessment"
  - "Palincsar & Brown (1984) — Reciprocal teaching of comprehension-fostering and comprehension-monitoring activities"
  - "Shanahan et al. (2010) — Improving reading comprehension in kindergarten through 3rd grade: IES practice guide"
input_schema:
  required:
    - field: "text_description"
      type: "string"
      description: "学生将阅读的文本描述——体裁、主题、篇幅及主要挑战"
    - field: "reader_challenge"
      type: "string"
      description: "学生在这篇文本上可能面临的具体理解困难"
    - field: "student_level"
      type: "string"
      description: "年龄/年级及当前的阅读能力"
  optional:
    - field: "reading_purpose"
      type: "string"
      description: "学生为什么阅读这篇文本——例如提取信息、分析、欣赏、比较"
    - field: "student_profiles"
      type: "array"
      description: "来自上下文引擎：阅读水平、解码能力、EAL 状态"
    - field: "subject_area"
      type: "string"
      description: "课程学科——策略选择因学科而异"
    - field: "text_extract"
      type: "string"
      description: "实际文本的简短节选，以便提供更精准的策略建议"
output_schema:
  type: "object"
  fields:
    - field: "recommended_strategies"
      type: "array"
      description: "针对该文本与读者挑战选定的 2–3 项策略，附带依据"
    - field: "implementation_guide"
      type: "object"
      description: "结合该文本教授每项策略的分步指南——阅读前、阅读中与阅读后"
    - field: "teacher_modelling_script"
      type: "string"
      description: "展示教师示范主要策略的简短出声思维脚本"
    - field: "strategy_pitfalls"
      type: "string"
      description: "策略教学可能出什么问题以及如何避免"
chains_well_with:
  - "text-complexity-analyser"
  - "think-aloud-script-generator"
  - "vocabulary-tiering-tool"
  - "scaffolded-task-modifier"
teacher_time: "3 分钟"
tags: ["reading", "comprehension", "strategy-instruction", "reciprocal-teaching", "metacognition"]
---

# 阅读理解策略选择器

## 本技能的作用

为特定文本与读者挑战匹配最恰当的阅读理解策略，并提供包含教师示范脚本在内的完整实施指南。本技能不采用“把所有策略全用上”这种常见却低效的做法，而是将具体策略精准匹配到具体的理解挑战——当文本结构陌生时使用“预测（predicting）”，当内容密集时使用“提问（questioning）”，当词汇专业晦涩时使用“澄清（clarifying）”，当文本冗长繁杂时使用“概括（summarising）”。输出不仅告诉教师用“哪项”策略，更说明如何结合“这篇”具体文本来教。AI 在此尤为有价值，因为策略选择需要同时权衡文本要求、读者可能的困难以及每项策略的证据基础——这种三向匹配是大多数教师没有时间显性完成的。

## 循证基础

Duke & Pearson (2002) 确立了具有强有力证据支持的六项理解策略：预测、提问、监控/澄清、视觉化、建立联系与概括。关键在于，他们强调策略教学必须是显性的——教师必须通过出声思维示范策略、引导学生在实践中应用，并逐步移交责任。Pressley (2002) 表明，熟练读者会灵活且有选择性地使用策略，针对不同的阅读挑战选用不同策略——教学生随时使用全部策略反而会造成认知过载与浅层套用。美国国家阅读专家组（National Reading Panel, 2000）证实理解策略教学能产生显著效果（尤其是提问与概括），但也提醒策略只是通向理解的手段，而非目的本身——目标是“理解”，而不是“使用策略”。Palincsar & Brown (1984) 证明了交互式教学（reciprocal teaching）的有效性——学生轮流应用四项策略（预测、提问、澄清、概括）——在理解提升上取得了 0.74 的效应量。Shanahan 等 (2010) 指出，策略教学对能够解码但在理解意义上遇到困难的中阶读者最为有效；对于初阶读者，解码教学应居于首位。

## 输入模式

教师必须提供：
- **Text description（文本描述）：** 学生将阅读什么。*例如："A Year 9 History textbook extract (800 words) about the causes of the Industrial Revolution — dense with unfamiliar vocabulary and multiple causal factors" / "A short story by Roald Dahl with an unexpected twist ending — Year 5 reading level"*
- **Reader challenge（读者挑战）：** 具体困难。*例如："Students tend to read the surface events but miss the underlying causes" / "Students don't notice the clues that foreshadow the ending" / "Students get lost in the technical vocabulary and give up"*
- **Student level（学生水平）：** 年级与阅读能力。*例如："Year 7, can decode fluently but struggle with inference" / "Year 4, mixed — some confident readers, some still developing fluency"*

可选（如上下文引擎可用则自动注入）：
- **Reading purpose（阅读目的）：** 学生为什么读这篇文本
- **Student profiles（学生档案）：** 阅读水平、解码能力、EAL 状态
- **Subject area（学科领域）：** 课程学科
- **Text extract（文本节选）：** 实际文本的简短节选

## Prompt

```
You are an expert in reading comprehension instruction, with deep knowledge of Duke & Pearson's (2002) strategy instruction research, Pressley's (2002) work on metacognitive comprehension, Palincsar & Brown's (1984) reciprocal teaching, and the National Reading Panel's (2000) findings on comprehension instruction. You understand that effective strategy instruction is SELECTIVE (matching specific strategies to specific challenges), EXPLICIT (modelled by the teacher before students apply independently), and PURPOSEFUL (strategies serve comprehension, not the other way around).

Your task is to select and plan comprehension strategy instruction for:

**Text description:** {{text_description}}
**Reader challenge:** {{reader_challenge}}
**Student level:** {{student_level}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Reading purpose:** {{reading_purpose}} — if not provided, infer the most likely purpose from the text description and subject area.
**Student profiles:** {{student_profiles}} — if not provided, design for a mixed-ability class with generally fluent decoding but variable comprehension.
**Subject area:** {{subject_area}} — if not provided, infer from the text description.
**Text extract:** {{text_extract}} — if provided, use it to ground the modelling script in the actual text. If not, create a plausible example.

Apply these evidence-based principles:

1. **Select strategies based on the specific comprehension challenge (Duke & Pearson, 2002; Pressley, 2002):**
   - Do NOT recommend all strategies at once. Select 2–3 strategies that directly address the stated reader challenge.
   - Match strategies to challenges:
     - Unfamiliar text structure → Predicting (activates expectations about structure)
     - Dense content with many ideas → Summarising (forces identification of main ideas)
     - Implicit meaning, inference required → Questioning (focuses attention on what's not said)
     - Technical or unfamiliar vocabulary → Clarifying/Monitoring (teaches students to identify and resolve confusion)
     - Narrative with complex character motivation → Making connections + Questioning
     - Informational text with complex processes → Visualising + Summarising
   - Explain WHY each strategy is appropriate for THIS text and THIS challenge.

2. **Explicit instruction sequence (Duke & Pearson, 2002):**
   - For each strategy, provide:
     a. Teacher modelling (I Do): The teacher demonstrates the strategy through think-aloud
     b. Guided practice (We Do): Students try the strategy with teacher support
     c. Independent application (You Do): Students apply the strategy independently
   - The modelling script should show the teacher's actual thinking process, not just the strategy label.

3. **Strategies are tools, not rituals (National Reading Panel, 2000):**
   - Warn against turning strategies into worksheet activities. "Write three predictions" is not prediction instruction — it's a compliance task.
   - The goal is COMPREHENSION, not strategy performance. If students can comprehend the text without the strategy, they don't need the strategy.
   - Strategy instruction should feel like thinking, not like form-filling.

4. **Developmental appropriateness (Shanahan et al., 2010):**
   - For younger or less fluent readers: focus on a single strategy, with heavy modelling and supported practice.
   - For intermediate readers: 2 strategies, with gradual release.
   - For advanced readers: flexible strategy use — teach students to select their own strategies based on the reading challenge.
   - If students are still struggling with decoding, strategy instruction is premature — note this.

5. **Before, during, and after reading structure:**
   - Organise the implementation around the reading process:
     - Before reading: activate prior knowledge, set purpose, introduce strategy
     - During reading: apply strategy at specific points in the text
     - After reading: reflect on comprehension, evaluate strategy effectiveness

Return your output in this exact format:

## Reading Comprehension Strategies: [Brief text description]

**For:** [Student level]
**Text:** [Text description]
**Key challenge:** [Reader challenge]
**Reading purpose:** [Stated or inferred]

### Recommended Strategies

For each strategy (2–3):
- **Strategy [N]: [Name]**
  **Why this strategy for this text:** [Specific rationale — what about this text and these readers makes this strategy the right choice]
  **What it looks like in practice:** [Brief description of what students will actually DO]

### Implementation Guide

**Before Reading (X minutes)**
[What the teacher does to set up the reading — activating prior knowledge, introducing the strategy, setting purpose]

**During Reading (X minutes)**
[Specific points in the text where the strategy should be applied, and how — teacher-guided for first application, then student-led]

**After Reading (X minutes)**
[How students reflect on their comprehension and evaluate the strategy's effectiveness]

### Teacher Modelling Script

[A think-aloud script where the teacher models the primary strategy with a specific section of the text — showing the internal thinking process, not just the strategy label]

### Strategy Pitfalls

[2–3 things that can go wrong with strategy instruction for this text, and how to avoid them]

**Self-check before returning output:** Verify that (a) strategies are matched to the specific comprehension challenge, not generically recommended, (b) the implementation includes explicit teacher modelling before student application, (c) the modelling script shows actual thinking, not just strategy labelling, (d) the approach is developmentally appropriate, and (e) the strategies serve comprehension, not the other way around — a student who understands the text has succeeded, whether or not they "used the strategy correctly."
```

## 示例输出

**场景：** *Text description: "A Year 8 History textbook extract (600 words) explaining the causes of the Black Death's spread across Europe — the text presents multiple causal factors (trade routes, fleas on rats, lack of medical knowledge, overcrowded cities) and students need to understand how these factors interacted" / Reader challenge: "Students tend to list the causes without understanding how they connect — they can say 'trade routes spread the plague' but can't explain the chain of causation" / Student level: "Year 8, fluent decoders, can identify explicit information but struggle with implicit connections between ideas"*

---

## 阅读理解策略：黑死病蔓延的原因

**适用对象：** 八年级历史
**文本：** 关于黑死病在欧洲蔓延原因的课本节选（600 词）
**核心挑战：** 学生倾向于孤立罗列原因，却不理解它们如何相互关联——无法解释因果链条
**阅读目的：** 理解瘟疫蔓延的相互关联成因，为撰写因果解释做准备

### 推荐策略

**策略 1：自我提问（Questioning）——“这与前面有什么联系？”**
**为何选择此策略：** 理解挑战在于观念之间的“联结”，而非理解单个事实。学生能提取信息（“贸易路线”、“老鼠身上的跳蚤”），但不会自发追问一个原因如何与另一个原因关联。自我提问迫使学生在阅读时生成联结性问题："How did trade routes help fleas spread?" / "Why did overcrowded cities make the plague worse?"
**实践中的表现：** 学生在每段末尾停下来问自己："How does this cause connect to the ones I've already read about?" 他们记录下问题并尝试作答。

**策略 2：概括（Summarising）——因果链条映射**
**为何选择此策略：** 文本呈现了多个原因，学生需要识别的不仅是它们是什么，还有它们如何形成一条链条。概括迫使学生筛选最重要的信息并加以组织——在这里是组织为因果链条，而非平铺清单。这种概括具有学科针对性："What caused what?" 而非 "What are the main points?"
**实践中的表现：** 每读完两段，学生用以下框架写一句概括："[Cause A] led to [Cause B] because..." 这强制要求建立因果联结，而非单纯罗列。

### 实施指南

**阅读前（5 分钟）**

1. *激活先验知识：* "Before we read, what do you already know about the Black Death? When was it? Where?" 快速头脑风暴——2 分钟。

2. *设定阅读挑战：* "Today's text explains WHY the plague spread so quickly across Europe. It gives several causes. Your job isn't just to find the causes — I want you to understand how they CONNECT. One cause didn't work alone — they worked together like a chain."

3. *引入提问策略：* "As you read, I want you to keep asking one question: 'How does this connect to what I just read?' When the text tells you about trade routes, ask: 'How did trade routes connect to the fleas?' When it tells you about overcrowded cities, ask: 'Why did overcrowding make the other causes worse?'"

4. *展示记录格式：* 两栏表格——左栏："Cause（原因）"，右栏："How it connects to other causes（它如何与其他原因相连）"。

**阅读中（15 分钟）**

*第 1 段——教师示范（见下方脚本）*

*第 2 段——引导练习：* 一起大声朗读。停顿。"OK, this paragraph talked about fleas on rats. How does that connect to the trade routes we read about in paragraph 1? Talk to your partner — what's the connection?" 巡视。倾听因果语言。向全班分享一个好例子。

*第 3–4 段——有支持的独立阅读：* 学生结对阅读。每读完一段，暂停、提出联结问题并补充到两栏记录中。教师巡视并检查是否出现了联结性语言，而不仅仅是罗列清单。

*第 5–6 段——独立应用：* 学生独立阅读并记录。教师物色 2–3 名学生在课末分享他们的联结。

**阅读后（5 分钟）**

1. *分享联结：* "Who found a connection between two causes that surprised them?" 收集 2–3 个例子。推动使用因果语言："Don't just tell me the two causes — tell me HOW they connected."

2. *共建因果链：* 在黑板上绘制视觉化因果链：贸易路线 → 带来携带跳蚤的老鼠 → 进入过度拥挤的城市 → 缺乏医学知识导致 → 无有效应对措施。"See how none of these causes works alone? It's the chain that made the plague devastating."

3. *反思策略：* "Did asking 'How does this connect?' help you understand the text differently than if you'd just read straight through? Why?"

### 教师示范脚本

*结合第 1 段示范提问策略：*

"I'm going to read the first paragraph aloud and show you what I'm thinking as I read. Watch how I ask myself questions about connections.

[朗读关于连接亚欧的贸易路线的第 1 段]

OK, so this paragraph is telling me that trade routes connected Asia to Europe and that the Black Death started in Central Asia. So trade routes are one cause of the spread. But I'm going to ask myself: 'How does this connect to other causes?' I know that trade routes carry goods — so maybe they also carried something else? The text says 'merchants travelled with their goods along the Silk Road.' I'm thinking: if merchants are travelling, what might be travelling WITH them that they don't know about? I'm going to hold that question as I read the next paragraph.

See what I did? I didn't just say 'trade routes — that's a cause.' I asked HOW trade routes actually spread the plague. That 'how' question is what I want you to ask for every cause you find."

### 策略常见陷阱

1. **提问沦为练习纸填表。** 如果学生每段后都机械写上 "How does this connect?" 却不真正思考答案，策略就变成了走过场。避免这一点的做法是坚持要求学生“回答”自己的问题，而不仅仅是提问。巡视时不要只检查学生写了几个问题——要检查他们能否“解释”其中的联结。

2. **概括沦为列清单。** 学生可能会记下 "Cause 1: trade routes. Cause 2: fleas"——这是罗列，不是概括联结。句式框架 "X led to Y because..." 正是为了防止这一点，但需要教师督促落实。如果学生只写单词，停下来重新示范："You wrote 'fleas.' But how did fleas CONNECT to the trade routes? That's the summary I need."

3. **策略喧宾夺主掩盖内容。** 如果学生把更多精力花在思考“我用对策略了吗？”而非“瘟疫是怎么蔓延的？”，策略就成了障碍。目标是理解历史内容，而非完美执行策略。如果一名学生能清晰解释因果链条却没有正式套用策略，这名学生依然“成功了”。策略是思考的脚手架，而非硬性规定。

---

## 已知局限性

1. **策略教学对中阶读者——即能够解码但理解困难的学生——最为有效。** 对于仍在发展阅读流畅度（读得慢、逐词解码）的学生，理解策略反而会增加认知负荷而非减轻它。这些学生首先需要流畅度教学。本技能标出了这一发展性考量，但无法评估单个学生的解码水平——必须由教师做出判断。

2. **策略推荐取决于文本描述与读者挑战的准确性。** 如果教师把挑战描述为“学生看不懂词汇”，而真正的挑战其实是“学生缺乏理解内容所需的背景知识”，那么推荐的策略就会偏离靶心。策略选择具有诊断性质——它要求准确识别症结所在。

3. **如果过度使用，策略教学会变得公式化。** 如果每篇文本前都要说“今天我们要用预测和提问策略”，学生就会停止真正运用策略，开始机械表演。策略应当在“需要”时教授，而不应作为每次阅读任务的固定仪式。最好的结果是学生自己在察觉理解受阻时主动选用策略。
