---
# AGENT SKILLS STANDARD FIELDS (v2)
name: scaffolded-task-modifier
description: "通过添加语言支架来修改课堂任务，同时为 EAL 学习者保留认知要求。适用于为不同英语水平的学生调整现有任务时。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "eal-language-development/scaffolded-task-modifier"
skill_name: "支架式任务修改器"
domain: "eal-language-development"
version: "1.0"
evidence_strength: "strong"
evidence_sources:
  - "Gibbons (2002, 2015) — Scaffolding Language, Scaffolding Learning: scaffolding that challenges rather than simplifies"
  - "Cummins (2000) — Language, Power and Pedagogy: the BICS/CALP and quadrant frameworks"
  - "Hammond & Gibbons (2005) — Putting scaffolding to work: the contribution of scaffolding in articulating ESL education"
  - "Vygotsky (1978) — Mind in Society: the zone of proximal development"
  - "Walqui (2006) — Scaffolding instruction for English language learners: a conceptual framework"
input_schema:
  required:
    - field: "original_task"
      type: "string"
      description: "原本为全班设计的任务"
    - field: "target_proficiency"
      type: "string"
      description: "需要为其搭建支架的学生的语言水平——例如 New to English、Early Acquisition、Developing、Consolidating"
    - field: "subject_area"
      type: "string"
      description: "课程学科"
  optional:
    - field: "student_level"
      type: "string"
      description: "年龄/年级"
    - field: "student_profiles"
      type: "array"
      description: "来自上下文引擎：第一语言、具体语言需求、认知能力"
    - field: "learning_objective"
      type: "string"
      description: "学习目标——无论语言水平如何，所有学生都应理解的内容"
    - field: "task_materials"
      type: "string"
      description: "原任务中使用的文本、练习纸或资源的描述"
output_schema:
  type: "object"
  fields:
    - field: "modified_task"
      type: "object"
      description: "添加了语言支持并保持认知要求的支架化任务版本"
    - field: "cognitive_demand_check"
      type: "string"
      description: "明确验证修改后的任务是否保持了认知挑战"
    - field: "scaffold_types_used"
      type: "array"
      description: "所应用的支架策略清单及每项策略的依据"
    - field: "removal_plan"
      type: "string"
      description: "随着语言水平提高，如何以及何时撤除支架"
chains_well_with:
  - "language-demand-analyser"
  - "vocabulary-tiering-tool"
  - "academic-language-sentence-frame-generator"
  - "cognitive-load-analyser"
teacher_time: "4 分钟"
tags: ["scaffolding", "EAL", "differentiation", "cognitive-demand", "task-modification"]
---

# 支架式任务修改器

## 本技能的作用

针对特定的语言水平调整课堂任务，同时明确保持认知要求——确保 EAL 学生与同伴进行同样深度的思考，即使他们需要语言支持才能做到这一点。关键的设计原则是：支架应当降低“语言”障碍，而不是降低“思维”要求。许多出发点良好的任务修改在无意中降低了认知要求：给 EAL 学生一个更简单的版本、删去分析部分，或将开放式问题替换为选择题。本技能通过生成修改后的任务及明确的认知要求检查来防范这一点，验证修改只改变了语言进入的路径，而没有改变智识上的目的地。AI 在此尤为有价值，因为在搭建支架的同时保持认知要求，需要同时理解任务的智识目的、学生的语言水平以及既能支持理解又不降低挑战的具体支架策略——这种三方分析是大多数教师没有时间完成的。

## 循证基础

Gibbons (2002, 2015) 确立了一项基本原则：为 EAL 学生提供的支架必须具有挑战性，而不是简单化——目标是支持学生做到比单独完成时“更多”，而不是减少对他们的要求。Cummins (2000) 提出了四象限模型，表明任务沿两个维度变化：认知要求（高/低）与情境支持（嵌入/抽离）。有效的 EAL 支架将任务从 D 象限（高要求、低情境支持——难以企及）移至 B 象限（高要求、高情境支持——有挑战性但可及）——而不是从 D 象限移至 A 象限（低要求、高情境支持——容易接触但缺乏挑战）。Hammond & Gibbons (2005) 识别了支架的两个层面：预设支架（课前规划——图形组织器、句式框架、预教词汇）和交互支架（课中教师的即时支持——重述、延展、引导）。Vygotsky (1978) 指出，学习发生在最近发展区（Zone of Proximal Development）——学习者在支持下能够做到、但尚不能独立做到的区域。Walqui (2006) 为 EAL 学习者总结了六种支架策略：示范（modelling）、架桥（bridging）、情境化（contextualising）、构建图式（building schema）、文本重构（representing text）以及发展元认知（developing metacognition）。

## 输入模式

教师必须提供：
- **Original task（原任务）：** 为全班设计的任务。*例如："Write a balanced argument essay on whether school uniforms should be compulsory" / "Analyse the data in the table and explain what it shows about population growth" / "Read the extract and answer the inference questions"*
- **Target proficiency（目标语言水平）：** 需要搭建支架的语言水平。*例如："Early Acquisition" / "Developing" / "New to English"*
- **Subject area（学科领域）：** 学科。*例如："English" / "Geography" / "Science"*

可选（如上下文引擎可用则自动注入）：
- **Student level（学生水平）：** 年级
- **Student profiles（学生档案）：** 第一语言、认知能力、具体需求
- **Learning objective（学习目标）：** 所有学生都应学到的内容
- **Task materials（任务材料）：** 原任务中使用的资源

## Prompt

```
You are an expert in EAL scaffolding and differentiation, with deep knowledge of Gibbons' (2002, 2015) principle that scaffolding must challenge rather than simplify, Cummins' (2000) quadrant model of cognitive demand and contextual support, and Walqui's (2006) scaffolding strategies for English language learners. You understand that the most common error in EAL differentiation is reducing cognitive demand — giving students an easier task instead of the same task with better support.

Your task is to scaffold:

**Original task:** {{original_task}}
**Target proficiency:** {{target_proficiency}}
**Subject area:** {{subject_area}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Student level:** {{student_level}} — if not provided, assume a secondary school student.
**Student profiles:** {{student_profiles}} — if not provided, assume the student has age-appropriate cognitive ability but limited academic English proficiency, with conversational fluency.
**Learning objective:** {{learning_objective}} — if not provided, infer the learning objective from the original task. This is critical — the modified task must achieve the SAME objective.
**Task materials:** {{task_materials}} — if not provided, infer typical materials for this task type.

Apply these evidence-based principles:

1. **Maintain cognitive demand (Gibbons, 2002; Cummins, 2000):**
   - The modified task must require the SAME level of thinking as the original.
   - If the original task requires analysis, the modified task must also require analysis — not description.
   - If the original task requires evaluation, the modified task must also require evaluation — not recall.
   - If the original task requires an extended written response, the scaffolded version may provide language support (sentence frames, word banks, graphic organisers) but must still require the student to construct meaning, not just fill blanks.
   - EXPLICITLY check and state: "The original task requires [thinking type]. The modified task also requires [same thinking type] because..."

2. **Scaffold language, not thinking (Gibbons, 2015):**
   - Identify the LANGUAGE barriers in the original task (vocabulary, grammar, text structure, reading load).
   - Add language supports that address these specific barriers.
   - Do NOT: simplify the question, reduce the number of steps, provide the answer in the scaffold, remove the requirement for original thinking, or substitute a lower-order task.

3. **Use appropriate scaffold types (Walqui, 2006; Hammond & Gibbons, 2005):**
   - **Modelling:** Provide a worked example or annotated model showing what a good response looks like.
   - **Bridging:** Connect to the student's existing knowledge or first language.
   - **Contextualising:** Add visual support, diagrams, or concrete examples that make abstract content accessible.
   - **Sentence frames:** Provide the linguistic structure while requiring the student to supply the content and thinking.
   - **Graphic organisers:** Provide a visual structure for organising ideas before writing.
   - **Word banks:** Supply key vocabulary, but require the student to select and use words meaningfully.
   - **Glossary/bilingual support:** Define key terms, ideally with first-language equivalents.

4. **Match scaffold intensity to proficiency level:**
   - **New to English:** Heavy scaffolding — visual support, bilingual resources, adapted text with glossary, sentence frames with minimal gaps, graphic organisers that structure the entire response. The student may respond partially in their first language. The thinking demand remains.
   - **Early Acquisition:** Substantial scaffolding — adapted text, sentence starters (not complete frames), word banks, graphic organisers, models. The student produces English with significant support.
   - **Developing:** Moderate scaffolding — original text with glossary, sentence starters for complex constructions only, optional word bank. The student produces mostly independent English with targeted support.
   - **Consolidating:** Light scaffolding — original text, a few sentence starters for the most complex academic constructions, no word bank (student should be building independence). Nearly independent.

5. **Plan for scaffold removal:**
   - Scaffolds are temporary. Every scaffold should include a note about when and how to remove it.
   - The goal is independence — if the scaffold becomes permanent, it has become a crutch.

Return your output in this exact format:

## Scaffolded Task: [Brief description]

**Original task:** [The original task]
**Scaffolded for:** [Target proficiency level]
**Subject:** [Subject area]
**Learning objective:** [Stated or inferred — must be the SAME for both versions]

### Modified Task

[The complete scaffolded version of the task — including all language supports, visual organisers, sentence frames, word banks, etc.]

### Cognitive Demand Check

**Original task requires:** [Type of thinking — analysis, evaluation, synthesis, application, etc.]
**Modified task requires:** [SAME type of thinking]
**How cognitive demand is maintained:** [Specific explanation of why the scaffolded version still requires the same thinking]
**What was changed:** [Only language access — not intellectual demand]
**What was NOT changed:** [The thinking, the learning objective, the analytical requirement]

### Scaffold Types Used

For each scaffold:
- **[Scaffold type]:** [What was added and why — connected to a specific language barrier]

### Scaffold Removal Plan

[How to progressively remove each scaffold as the student's proficiency increases — specific, practical steps]

**Self-check before returning output:** Verify that (a) the learning objective is the same for both versions, (b) the modified task requires the same TYPE of thinking as the original, (c) scaffolds address language barriers specifically, (d) no scaffold inadvertently provides the answer or removes the need for original thinking, (e) the scaffold intensity matches the stated proficiency level, and (f) the scaffold removal plan is included.
```

## 示例输出

**场景：** *Original task: "Read the extract from 'An Inspector Calls' (Act 1, Mr Birling's speech about the Titanic). Analyse how Priestley uses dramatic irony to undermine Mr Birling's authority. In your response, explain what dramatic irony is, identify specific examples from the extract, and explain the effect on the audience." / Target proficiency: "Developing" / Subject area: "English Literature" / Student level: "Year 10"*

---

## 支架化任务：《An Inspector Calls》中的戏剧反讽

**原任务：** 分析 Priestley 如何在《An Inspector Calls》（第一幕）Mr Birling 关于泰坦尼克号的演讲中运用戏剧反讽来削弱其权威性。解释什么是戏剧反讽，找出具体例证，并解释其对观众的影响。
**支架适用对象：** Developing 水平
**学科：** 英国文学
**学习目标：** 学生分析 Priestley 如何将戏剧反讽作为一种写作手法，塑造观众对 Mr Birling 的看法。

### 修改后的任务

**第 1 步：理解概念（配视觉支持）**

**戏剧反讽（Dramatic irony）** = 当观众知道某件事，而剧中人物却不知道。

| Mr Birling 说了什么（1912 年） | 观众知道什么（1945 年及以后观看） |
|---|---|
| "The Titanic... unsinkable, absolutely unsinkable" | 泰坦尼克号于 1912 年首航即沉没——超过 1,500 人遇难 |
| "I say there isn't a chance of war" | 第一次世界大战于 1914 年爆发，第二次世界大战于 1939 年爆发 |

**这就是戏剧反讽：** Mr Birling 完全错了，而且在他自信满满地发表演讲时，观众清楚地知道他错了。

**第 2 步：分析——为什么 Priestley 要这样做？**

重读节选文本。使用下面的问题构建你的分析。你必须解释你的思考——仅回答一个词是不够的。

1. 当观众听到 Mr Birling 说泰坦尼克号“绝对不会沉没（unsinkable）”时，他们对 Mr Birling 有什么看法？他们会信任他的判断吗？

2. Mr Birling 极其自信地说出这些错误的预言（"I say there isn't a chance of war"）。他的自信产生了什么效果？一个犯错却极其自信的人，比一个犯错但不确定的人更可笑还是更不可笑？

3. Mr Birling 还对商业和社会责任做出了预测——他说人们应该只顾自己。Priestley 希望观众不同意这种观点。关于泰坦尼克号和战争的戏剧反讽，如何帮助 Priestley 让观众也不同意 Mr Birling 的其他观点？

**第 3 步：撰写你的回答**

使用以下结构。每个部分都需要你自己的思考——句首提示为你提供学术语言，但你必须填充分析内容。

**第 1 段——什么是戏剧反讽以及 Priestley 如何使用它：**

Dramatic irony is when ___. In Mr Birling's speech, Priestley uses dramatic irony when Birling says "___" (quote from the extract). The audience in 1945 would know that ___, which means Birling is ___.

**第 2 段——对观众的影响：**

This dramatic irony affects the audience because ___. When they hear Birling speak so confidently about something they KNOW is wrong, they begin to ___. Priestley's purpose in doing this is to ___ because ___.

**第 3 段——这如何联系到 Priestley 更宏大的主题：**

Priestley uses the dramatic irony to undermine Birling's authority so that when Birling argues that people should only look after themselves, the audience ___. If the audience already knows Birling is wrong about the Titanic, they are more likely to think he is also wrong about ___. This supports Priestley's message that ___.

**分析性语言词库：**

| 描述 Birling | 描述观众的反应 | 描述 Priestley 的意图 |
|---|---|---|
| arrogant, overconfident, foolish, misguided, short-sighted | sceptical, distrustful, critical, amused, aware | undermines, discredits, challenges, exposes, reveals |

### 认知要求检查

**原任务要求：** 分析——学生必须解释一种手法（戏剧反讽）如何产生特定效果（削弱权威），这要求他们找出例证、解释手法的运作机制，并将其与作者意图联系起来。

**修改后的任务要求：** 同样的分析。学生仍然必须解释戏剧反讽如何削弱 Birling、找出具体例证、解释对观众的影响，并联系 Priestley 的意图。引导性问题和句首提示提供了语言支架，但每一处都要求学生提供自己的分析性思考。

**如何保持认知要求：**
- 问题 2 要求学生评估自信与犯错之间的关系——这是真正的分析，而非回忆。
- 问题 3 要求学生解释对事实预测的戏剧反讽如何迁移并削弱 Birling 的政治观点——这是最难的分析步骤，支架并未替学生回答。
- 句式框架要求学生完成分析："Priestley's purpose in doing this is to ___ because ___"——其中的 "because" 强制要求推理，而不仅仅是识别。

**改变了什么：** 阅读部分辅以对照表。写作结构用句首提示搭建支架。词库中提供了分析性词汇。任务被拆分为引导式步骤。

**没有改变什么：** 进行分析（而非描述）的要求。解释对观众影响的要求。将写作手法与作者意图联系起来的要求。使用文本证据的要求。

### 所使用的支架类型

- **情境化（对照表）：** 对照表使戏剧反讽所需的历史背景知识显性化——EAL 学生可能不具备识别 Birling 预言为何具有反讽意味的文化背景知识。该表提供了这种背景，而没有替学生做分析。
- **句式框架：** 提供分析性写作的语法结构（带有嵌入从句的复合句），同时要求学生提供内容。"Dramatic irony is when ___" 要求给出定义。"Priestley's purpose in doing this is to ___ because ___" 要求进行推理。
- **引导性问题：** 将分析拆解为循序渐进的步骤，而不是期望学生从单一的开放式提示中直接写出完整的分析性回答。每个问题针对分析的一个组成部分。
- **词库：** 提供 Developing 水平 EAL 学生不太可能掌握但分析性写作所需的评价性词汇（arrogant、sceptical、undermines）。学生必须选择合适的词——词库提供选项，而非答案。

### 支架撤除计划

| 当前支架 | 何时撤除…… | 替换为…… |
|---|---|---|
| 对照表（历史背景） | 学生在课堂讨论中能独立展现出对历史背景的了解 | 无需替换——该知识应已内化 |
| 句式框架（完整结构） | 学生仅凭句首提示即可写出分析性段落 | 仅提供句首提示："Priestley uses..." "This suggests..." "The effect on the audience is..." |
| 句首提示 | 学生能独立写出结构恰当的分析性写作 | 无句首提示——学生独立写作，并在写后获得关于结构的反馈 |
| 引导性问题 | 学生在面对开放式提示时能独立识别分析步骤 | 单一开放式提示："Analyse how Priestley uses [technique] to [effect]" |
| 词库 | 学生在不使用词库的情况下能独立使用 3 个以上分析性术语 | 无词库——但随着新分析性词汇的出现继续教授 |

**目标时间线：** 对于处于 Developing 水平的学生，争取在 4–6 周内撤除句式框架（配合定期的分析性写作练习）。词库可以逐步精简——撤除学生已正确使用 3 次以上的词汇。引导性问题可在 2–3 个月内缩减为 1–2 个提示。

---

## 已知局限性

1. **修改无法独立于语言水平之外去精准匹配学生的认知能力。** 一名英语处于 Developing 水平但在第一语言中具备很强分析能力的学生，与另一名处于相同英语水平但同样觉得分析有困难的学生，需要不同的支架。教师对单个学生的了解对于调整支架至关重要。

2. **支架撤除需要连贯的、纵向的规划。** 本技能为单个任务设计支架，但有效的支架撤除发生在数周和数月的时间跨度中。教师如果对每项任务都使用本技能，会得到支架设计良好的单个任务，但跨任务的渐进式撤除需要教师规划整体轨迹。建议结合间隔练习（spaced-practice）的方法来逐步减少支架。

3. **修改以原任务本身设计良好为前提。** 如果原任务结构混乱、不清晰或与学习目标不匹配，为其搭建支架也无济于事——需要先重新设计原任务。支架不是糟糕任务设计的补救措施；它是让好任务对不同语言水平的学生都具有可及性的方法。
