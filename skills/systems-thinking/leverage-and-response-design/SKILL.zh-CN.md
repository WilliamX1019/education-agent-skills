---
# AGENT SKILLS STANDARD FIELDS (v2)
name: leverage-and-response-design
description: "基于现有的系统分析设计明智的系统干预方案。将拟议行动对应到 Meadows 杠杆点层级，排查非预期后果，并生成替代方案。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "systems-thinking/leverage-and-response-design"
skill_name: "杠杆点与应对设计"
domain: "systems-thinking"
version: "1.0"
evidence_strength: "moderate"
evidence_sources:
  - "Meadows (2008) — Thinking in Systems (leverage points hierarchy, 12 places to intervene)"
  - "Meadows (1999) — Leverage Points: Places to Intervene in a System"
  - "Senge (1990) — The Fifth Discipline (unintended consequences, systems archetypes)"
  - "Sterman (2000) — Business Dynamics (policy resistance, feedback loops)"
  - "Kim (1999) — Systems Archetypes (shifting the burden, fixes that fail, limits to growth)"
input_schema:
  required:
    - field: "systems_analysis"
      type: "string"
      description: "已完成的系统分析——冰山图、心智模式图、能动性圈输出，或对系统及其模式的描述"
    - field: "proposed_action"
      type: "string"
      description: "学生或教育者目前考虑针对该问题采取的行动"
  optional:
    - field: "age_range"
      type: "string"
      description: "学生年龄范围"
    - field: "scope_constraints"
      type: "string"
      description: "学生现实中能够做到的范围（时间、预算、权限、触达面）"
    - field: "context"
      type: "string"
      description: "社区、学校或环境背景"
output_schema:
  type: "object"
  fields:
    - field: "leverage_assessment"
      type: "object"
      description: "拟议行动在 Meadows 层级中所处位置，以及是否存在更高杠杆点的替代方案"
    - field: "alternative_responses"
      type: "array"
      description: "位于不同杠杆层级的 2–3 个应对方案，各自附带系统效应、反馈回路、风险与可行性"
    - field: "unintended_consequences"
      type: "array"
      description: "拟议行动可能触发的反馈回路以及需要警惕的系统基模"
    - field: "proportionality_check"
      type: "object"
      description: "应对方案是否与学生实际能影响的程度相匹配"
    - field: "do_less_harm_check"
      type: "string"
      description: "在此情境下“不行动”或“少行动”是否是更明智的回应"
chains_well_with:
  - "systems-awareness-iceberg"
  - "agency-circles-for-systems-action"
  - "mental-model-mapper"
  - "compassionate-systems-awareness-orchestrator"
teacher_time: "10–15 分钟"
tags: ["systems-thinking", "leverage-points", "intervention-design", "unintended-consequences", "meadows", "feedback-loops", "action-design"]
---

# 杠杆点与应对设计（Leverage and Response Design）

## 本技能的功能

在学生和教育者知道该在系统的何处着手后，帮助他们设计审慎的干预方案。本技能填补了系统思考中的“行动缺口”：现有工具帮助学生分析系统（冰山图）、揭示假设（心智模式、推论阶梯）并识别自身能动性所在（能动性圈）。本技能通过追问连接分析与行动：基于我们对系统的已知认识，什么样的回应才是明智的？

核心洞见在于：在复杂系统中，最显而易见的干预很少是最明智的。高可见度的行动（海报、请愿、一次性活动）往往只针对表层症状；更高杠杆率的干预则瞄准产生症状的结构、反馈回路和心智模式。本技能并不否定低杠杆行动——有时它正是唯一可行且恰当的回应——但它确保学生在做出选择前已通盘考量了完整谱系。

## 循证依据

Meadows 的 12 个杠杆点层级（1999, 2008）提供了结构框架：干预从调整参数（最低杠杆）出发，经由改变规则、信息流与目标，直至转变范式与超越系统（最高杠杆）。Meadows 提醒我们，杠杆率更高并不总是意味着更容易触及——范式转变需要与修改规则截然不同的工作。Senge 的系统基模（舍本逐末 shifting the burden、饮鸩止渴 fixes that fail、成长上限 limits to growth）为识别干预设计中的常见失效模式提供了模式识别工具。Sterman 关于政策阻抗（policy resistance）的研究揭示了为何善意的干预往往产生与初衷相反的结果。Kim 的《系统基模》工具箱为教育情境下的实践者提供了命名这些模式的语言。

## 输入规范

必填：
- **系统分析：** 学生已完成的前期系统工作——可以是冰山分析、心智模式图、能动性圈输出，或对系统及其内在模式的描述。前期分析越丰富，应对设计就越具体。
- **拟议行动：** 学生目前打算采取的做法。这是杠杆分析的起点，而非最终答案。

可选：
- **年龄范围：** 学生年龄范围，用于校准复杂度与语言。
- **范围限制：** 考虑到时间、预算、权限与触达面，学生现实中能做到的程度。
- **情境：** 社区、学校或环境背景。

## Prompt

```text
You are a systems thinking specialist with expertise in intervention design and unintended consequences, drawing on Meadows' leverage points hierarchy, Senge's systems archetypes, and Sterman's work on policy resistance.

Inputs:
Systems analysis: {{systems_analysis}}
Proposed action: {{proposed_action}}
Age range: {{age_range}}
Scope constraints: {{scope_constraints}}
Context: {{context}}

Use these rules:

1. MAP THE PROPOSED ACTION against Meadows' leverage points hierarchy. Identify where it sits:
   - Parameters (numbers, sizes, flows) — lowest leverage
   - Buffers and stocks
   - Stock-and-flow structures
   - Delays
   - Balancing feedback loops
   - Reinforcing feedback loops
   - Information flows
   - Rules (incentives, constraints, regulations)
   - Self-organisation (power to change the system structure)
   - Goals
   - Paradigms (shared assumptions, goals, values)
   - Transcendence — highest leverage
   
   Ask: Is there a higher-leverage intervention available that is within the students' scope? Does the proposed action target symptoms or the structures that produce them?

2. ANALYSE FOR UNINTENDED CONSEQUENCES using systems archetypes:
   - Shifting the burden: Does the proposed action make the symptom more comfortable, reducing pressure to address the root cause?
   - Fixes that fail: Does the proposed action trigger a delayed negative side effect that cancels the benefit?
   - Limits to growth: What feedback loop will eventually limit the effect of the proposed action?
   - What reinforcing loops might the action trigger? What balancing loops might push back?

3. GENERATE 2-3 ALTERNATIVE OR REFINED RESPONSES at different leverage levels. For each:
   - What it changes in the system (which leverage point it targets)
   - What feedback loops it creates or disrupts
   - What could go wrong (unintended consequences, archetype risks)
   - What makes it more or less feasible for these students in this context

4. PROPORTIONALITY CHECK for each response option:
   - Is this response proportionate to what students can actually influence?
   - Does it place systemic burdens (emotional, civic, logistical) on young people that belong to adults, institutions, or wider society?
   - If the intervention is disproportionate to student power, say so clearly and redirect toward appropriately scaled action.

5. DO LESS HARM CHECK:
   - Is doing nothing or doing less actually the wisest response in this case?
   - Sometimes the best systems response is observation, understanding, and honest naming rather than intervention.
   - Are there reasons why acting now, with current information, might cause more harm than good?

Self-check: Am I helping students think carefully about intervention, or am I just helping them plan a more elaborate version of their first idea? Have I considered that the wisest response might be smaller, not bigger? Have I checked whether the proposed action risks 'shifting the burden' away from structural accountability?

Return exactly:

## Leverage and Response Design: [Brief system/issue label]

**Prior analysis summary:** [One-sentence synthesis of the systems analysis provided]
**Proposed action:** [Restate the proposed action clearly]

### Leverage Assessment
- **Leverage level of proposed action:** [Which of Meadows' levels it targets]
- **What it changes:** [Which system element it affects]
- **What it does not change:** [Structures or mental models the action leaves untouched]
- **Higher-leverage alternatives to consider:** [Yes/No — if yes, identified below]

### Unintended Consequence Analysis
- **Archetype risks:**
  - [Archetype name]: [How it might operate here]
- **Feedback loops triggered:**
  - [Loop]: [What it reinforces or balances]
- **Policy resistance risk:** [How the system might push back against the action]

### Response Options

**Option 1: [Name — e.g. the proposed action, refined]**
- Targets: [leverage level]
- System effect: [what changes]
- Feedback loop created: [reinforcing or balancing]
- What could go wrong: [specific risk]
- Feasibility: [honest assessment for these students]

**Option 2: [Name — e.g. higher-leverage alternative]**
- Targets: [leverage level]
- System effect: [what changes]
- Feedback loop created: [reinforcing or balancing]
- What could go wrong: [specific risk]
- Feasibility: [honest assessment for these students]

**Option 3: [Name — e.g. lower-leverage but more accessible]**
- Targets: [leverage level]
- System effect: [what changes]
- Feedback loop created: [reinforcing or balancing]
- What could go wrong: [specific risk]
- Feasibility: [honest assessment for these students]

### Proportionality Check
[Is each option proportionate to student power? Are any interventions placing structural responsibility on students that belongs elsewhere?]

### Do Less Harm Check
[Is acting now, with current knowledge, wiser than observing and naming? What evidence would justify action over continued inquiry?]

### Recommended Next Step
[One specific, proportionate, well-reasoned first action or decision point]
```

## 常见误区

1. **把最初的想法当成最终方案。** 学生最初的提议通常只是针对表层症状的参数级干预。本技能应在回归行动前拓展思维，而不是用系统思考术语去包装并肯定第一个想法。
2. **把高杠杆等同于更好。** 范式层面的改变杠杆率最高，但也更困难、更缓慢、更难以触及。请将野心与真实能力相匹配。
3. **漏掉“减少伤害”选项。** 建议“少做一点”有时让人感觉像失败，但它往往是最具系统智慧的回应。
4. **把重担转嫁给学生。** 气候教育、社会公正工作和社区韧性项目可能会无意中要求年轻人去解决结构性问题。比例性检查必须明确指出何时将成人与制度责任错置给了学生。
5. **忽视反馈回路。** 只列出某项行动会改变什么，而不追问系统接下来会如何反应，这不是系统思考——而是盲目乐观的规划。

## 核查清单

- [ ] 拟议行动已对应到 Meadows 杠杆点层级。
- [ ] 至少指出了两条非预期后果路径。
- [ ] 提供了位于不同杠杆层级的 2–3 个应对选项。
- [ ] 每个选项都包含可能出错的风险。
- [ ] 比例性检查明确指出了应对方案是否适合由学生承担。
- [ ] 诚实完成了“减少伤害”检查。
- [ ] 推荐的下一步具体且可行。

## 已知局限性

1. **无法预测真实的系统行为。** 所有干预分析都基于复杂系统的简化模型。杠杆点框架是一种思维启发式工具，而非社会变革的物理学定律。
2. **杠杆率越高并不总是越好。** Meadows 本人也强调，杠杆点往往也是系统抵抗干预最激烈的地方。该层级描述的是潜在影响力，而非改变的难易程度。
3. **学生可能会感到泄气。** 分析发现自己原本的提议杠杆率有限，可能会令人感到受挫。本技能应将此正常化为系统思考的常态，而非学生或其想法的失败。
4. **比例性是一项本技能无法代做的判断。** 某项干预是否适合特定年龄段的学生，需要教师对情感与发展准备度的专业判断，而不仅仅是系统分析。
