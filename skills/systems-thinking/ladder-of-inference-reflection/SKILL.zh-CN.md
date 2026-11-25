---
# AGENT SKILLS STANDARD FIELDS (v2)
name: ladder-of-inference-reflection
description: "放慢从观察到行动的解读过程。适用于学生或成人需要在冲突、对话或探究中审视自身假设的场景。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "systems-thinking/ladder-of-inference-reflection"
skill_name: "推论阶梯反思"
domain: "systems-thinking"
version: "1.0"
evidence_strength: "moderate"
evidence_sources:
  - "Argyris (1990) — Overcoming Organizational Defenses (ladder of inference and defensive reasoning)"
  - "Argyris & Schön (1974) — Theory in Practice (reflection on reasoning and action)"
  - "Senge et al. (1994) — The Fifth Discipline Fieldbook (ladder of inference as dialogue tool)"
  - "Yeager & Walton (2011) — Social-psychological interventions in education (meaning-making and interpretation)"
input_schema:
  required:
    - field: "situation"
      type: "string"
      description: "需要审视的时刻、冲突、观察、决策或解读"
    - field: "context"
      type: "string"
      description: "事件发生的地点及涉及人员"
  optional:
    - field: "student_level"
      type: "string"
      description: "年龄/年级"
    - field: "current_interpretation"
      type: "string"
      description: "某人目前认为该情境意味着什么"
    - field: "desired_use"
      type: "string"
      description: "反思、修复性对话、偏见核查、讨论或探究"
output_schema:
  type: "object"
  fields:
    - field: "ladder_map"
      type: "object"
      description: "观察、筛选的数据、赋予的意义、假设、结论、信念与行动"
    - field: "alternative_ladders"
      type: "array"
      description: "其他合理的解释"
    - field: "questions_to_test"
      type: "array"
      description: "寻求证据的提问"
    - field: "dialogue_script"
      type: "object"
      description: "适合课堂安全使用的对话话术"
chains_well_with:
  - "mental-model-mapper"
  - "restorative-practice-protocol-designer"
  - "dialogic-teaching-move-generator"
  - "socratic-questioning-sequence-generator"
  - "systems-awareness-iceberg"
teacher_time: "5 分钟"
tags: ["ladder-of-inference", "assumptions", "dialogue", "reflection", "conflict", "bias", "compassionate-systems"]
---

# 推论阶梯反思（Ladder of Inference Reflection）

## 本技能的功能

帮助学生和成人放慢从观察、解读到采取行动的跳跃过程。当某人从有限的数据直接跳到强烈结论时，推论阶梯（Ladder of Inference）尤为有用：“她不理我，是因为她讨厌我”“学生就是懒”“学校根本不在乎”或“社区永远不会改变”。

本技能不会否定人们的感受。它将“实际观察到的事实”与“筛选出来的数据、赋予的意义、假设、结论、信念和行动”分离开来，随后打开替代推论阶梯和寻求证据的提问。

## 循证依据

推论阶梯源于 Argyris 关于推理、防御性惯例与组织学习的研究，并通过 Senge 及其同事推广为系统学习工具。它在慈悲系统工作中尤为有用，因为心智模式往往正是通过人们从筛选数据中构建意义的过程显现出来的。

## 输入规范

必填：
- **情境：** 具体的时刻、冲突、决策或解读。
- **背景：** 发生在何处以及涉及谁。

可选：
- **学生水平：** 年龄/年级。
- **当前解读：** 某人目前认为该情境意味着什么。
- **期望用途：** 反思、修复性对话、偏见核查、探究、教职工讨论。

## Prompt

```text
You are guiding a Ladder of Inference reflection. Help the user move carefully from observed data to selected data, meanings, assumptions, conclusions, beliefs, and actions.

Inputs:
Situation: {{situation}}
Context: {{context}}
Student level: {{student_level}}
Current interpretation: {{current_interpretation}}
Desired use: {{desired_use}}

Suitability check before generating alternatives: do not use this reflection immediately after significant harm, to adjudicate disputed facts, or to excuse documented harm. Prioritise safety and the school's appropriate human-led safeguarding, restorative or disciplinary process. Where there is a significant power imbalance, do not press the less-powerful person to reframe their experience; use qualified human facilitation and defer the exercise if time, trust or safety is missing. If unsuitable, retain the output sections but explain the deferral, mark alternative ladders and dialogue as deferred, and give a safe next step rather than inventing alternatives. This tool supports later reflection; it is not factual investigation.

Rules:
1. Validate that interpretations can feel real while still being incomplete.
2. Distinguish observable data from selected data and meaning-making.
3. When suitable, include at least two alternative ladders that could also fit the observable data, labelled as possibilities rather than facts.
4. Do not force forgiveness, positivity, or reconciliation.
5. In conflict contexts, protect dignity and safety.
6. End with questions that gather evidence or open dialogue.

Return exactly:

## Ladder of Inference: [Situation]

**Context:** [brief]
**Purpose:** [reflection/dialogue/inquiry]

### Step 1: Observable Data
What someone could have seen/heard/read without interpretation:
- [observable fact]
- [observable fact]

### Step 2: Selected Data
What the person may have noticed most:
- [selected clue]
- [selected clue]

### Step 3: Meanings Added
Possible meanings attached to the selected data:
- [meaning]

### Step 4: Assumptions
Possible assumptions underneath the meaning:
- [assumption]

### Step 5: Conclusions
What the person may conclude:
- [conclusion]

### Step 6: Beliefs Reinforced
Wider beliefs or mental models this conclusion may strengthen:
- [belief/model]

### Step 7: Actions
What actions this ladder may lead to:
- [action/avoidance/response]

### Alternative Ladders
**Alternative ladder 1:** [same data, different possible meaning]
**Alternative ladder 2:** [same data, different possible meaning]

### Evidence-Seeking Questions
- What did I actually observe?
- What did I not observe?
- What else could this mean?
- What could I ask safely and respectfully?
- What evidence would change my interpretation?

### Dialogue Language
- "The story I'm telling myself is..."
- "What I noticed was..."
- "I may be missing something. Can you help me understand...?"
- "Another possibility is..."

Self-check: Confirm suitability before generating alternatives; if deferred, explain why and identify the human-led next step. Do not invalidate emotion or minimize documented harm. Do not present alternatives as truth. Keep safety and dignity central.
```

## 常见误区

1. **用阶梯来否定情绪。** 情绪是关于自身体验的真实信号，但未必是整件事的全貌证据。
2. **把伤害过度理智化。** 如果确实发生了伤害，切勿使用替代阶梯为施害行为开脱。
3. **跳过可观察数据。** 务必从能看到、听到、读到的客观事实开始。
4. **预设只有一个正确解读。** 目标是更好的探究，而不是强迫达成共识。

## 已知局限性

1. **不能判定实际发生了什么。** 推论阶梯是反思工具，而非调查工具。它无法解决事实争议、裁定伤害责任，也不能替代修复性或纪律处分程序。
2. **不适用于重大伤害发生后立即使用。** 对近期严重事件急于生成“替代解释”，可能会让受伤害方感到体验被否定。本技能需要时间、信任以及往往需要修复性框架的铺垫才能安全使用。
3. **权力不对称风险。** 当涉及双方权力差距较大时（如师生之间或成人与儿童之间），如果缺乏谨慎引导，提出替代阶梯可能会让弱势一方觉得自己的经历被轻视。
4. **受文化边界限制。** 当所涉解读涉及引导者并不了解的文化知识、社区历史或切身经历时，本技能可能效果不佳，可能需要引入外部文化专业知识。

## 核查清单

- [ ] 可观察数据与主观解读明确分离。
- [ ] 假设以审慎、试探性的方式命名。
- [ ] 在适用时至少包含两条试探性替代阶梯；若不适用，则明确说明推迟原因及安全下一步。
- [ ] 对话语言安全且适龄。
- [ ] 输出内容不替伤害行为开脱，也不强迫和解。
