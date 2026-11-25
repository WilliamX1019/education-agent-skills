---
# AGENT SKILLS STANDARD FIELDS (v2)
name: multi-perspective-decision-wheel
description: "在承诺采取行动之前，通过多元视角审视一项决策或设计挑战。适用于在界定范围、系统映射与两难驾驭之后，作为团队需要做出更明智下一步的综合步骤。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS
skill_id: "original-frameworks/multi-perspective-decision-wheel"
skill_name: "多元视角决策轮"
domain: "original-frameworks"
version: "1.0"
evidence_strength: "emerging"
evidence_sources:
  - "H3Uni Wheel of Wisdom tutorial and facilitation guides (CC BY-SA 4.0, practitioner method)"
  - "Midgley, G. (2000). Systemic Intervention: Philosophy, Methodology, and Practice. Kluwer Academic/Plenum."
  - "Rajagopalan, R., & Midgley, G. (2015). Knowing differently in systemic intervention. Systems Research and Behavioral Science, 32, 546–561."
input_schema:
  required:
    - field: "decision_or_challenge"
      type: "string"
      description: "待审视的具体决策、提案或设计挑战——必须是一个判断性问题，而非事实性问题"
    - field: "context"
      type: "string"
      description: "该决策所处的学校、课程或社区情境"
  optional:
    - field: "prior_inquiry_summary"
      type: "string"
      description: "先前在范围界定、六边形映射、三地平线映射或两难驾驭中获得且为本决策提供依据的洞察"
    - field: "perspectives_to_include"
      type: "array"
      description: "作为决策轮辐条纳入的特定利益相关方、学科、时间视野或价值视角"
    - field: "student_level"
      type: "string"
      description: "年级或年龄范围"
    - field: "decision_constraints"
      type: "string"
      description: "决策必须在其中运作的现实约束——资源、权限、时间、政策或社区因素"
output_schema:
  type: "object"
  fields:
    - field: "central_question"
      type: "string"
      description: "置于决策轮中心的决策问题"
    - field: "perspectives"
      type: "array"
      description: "作为辐条的每个视角：名称、所见、盲区、所问、所贡献"
    - field: "tensions_between_perspectives"
      type: "array"
      description: "至少一处两个视角对情境看法不同的真实张力"
    - field: "synthesis_insights"
      type: "array"
      description: "整个决策轮揭示出而任何单一视角无法独自看见的洞察"
    - field: "proposal_improvements"
      type: "object"
      description: "该提案或决策应当保留、改变、测试与停止的内容"
    - field: "next_responsible_step"
      type: "object"
      description: "一项具体、可行的下一步行动，附带责任人、所需证据与限度"
    - field: "quality_gate_results"
      type: "object"
      description: "对决策轮进行结构质量检查的结果"
chains_well_with:
  - "dilemma-navigation-for-education-design"
  - "three-horizons-learning-transition-mapper"
  - "agency-circles-for-systems-action"
  - "project-brief-designer"
  - "regenerative-project-design-orchestrator"
  - "assessment-validity-checker"
  - "seeds-regenerative-inquiry-cycle"
teacher_time: "10 分钟"
tags: ["h3uni", "decision-making", "multiple-perspectives", "wheel-of-wisdom", "original-framework", "emerging-evidence", "programme-planning", "boundary-critique"]
---

# 多元视角决策轮

## 本技能的功能

在承诺采取行动之前，通过多元视角——利益相关方、学科、时间视野与价值体系——来审视一项决策或设计挑战，从而将其结构化。每一个视角都是决策轮上的一根辐条：它能看见其他视角看不见的东西、提出他人可能遗漏的问题，同时自身也存在盲区。所有视角的综合能够产出比任何单一视角都更明智的决策。

本技能位于 H3Uni 序列的最后一步，紧随范围界定、六边形映射、三地平线映射与两难驾驭之后。在缺乏先期探究的情况下运行它，只会产出流于表面的观点堆砌轮。它的真正价值在于将早期方法所浮现的洞察与张力综合为深思熟虑、多元视角的行动建议。

本技能并不产出通往“唯一正确答案”的公式。它产出的是一份关于每个视角“看见什么、忽略什么以及追问什么”的结构化理解——在此基础上，团队能够做出比没有它时更明智的决策。

## 证据空间与证据强度

本技能编码了 H3Uni 智慧之轮（Wheel of Wisdom）方法——一种面向多元视角决策的实践者工具，在理论上植根于 Gerald Midgley 的系统性干预框架。

### 组件证据

- **H3Uni 智慧之轮**（实践者框架）：H3Uni 的引导指南将智慧之轮描述为围绕中心问题组织多元视角对话的工具。该方法将命名角色或视角用作严谨的审视透镜，强调真诚的观点采择而非辩论。这些属于实践者资源，而非同行评审研究。
- **Midgley（2000）系统性干预**（中等）：Midgley 的边界批判（boundary critique）确立了“选择将谁的视角纳入或排除在决策之外”本身就是一项伦理与分析行为。他的框架支撑了决策轮对“纳入边缘化视角、未来视角与非人类视角”的强调，而不仅限于最显眼的利益相关方。
- **Rajagopalan & Midgley（2015）以不同方式认知**（中等）：该论文主张系统性干预需要多种认知方式——不仅是技术视角与利益相关方视角，还包括默会知识、文化知识与具身知识。这支持了决策轮在承诺行动前让多种认识论变得可见的强调。

### 综合证据

课堂决策轮模板——包括四部分视角结构（所见、盲区、所问、所贡献）、张力命名步骤、提案改进框架以及下一步负责任行动格式——由 Gareth Manning 在布达佩斯 REAL School 基于 H3Uni 的智慧之轮为学龄学生改编。这一课堂综合方案尚未接受过独立评估。

H3Uni 方法由 Anthony Hodgson 与 Bill Sharpe 创立的 H3Uni 以 CC BY-SA 4.0 协议发布。H3Uni 的正式运营已于 2026 年 5 月结束；其资源库现由 Future Stewards 作为开放共享资源维护。

### 本技能不应声称的内容

H3Uni 智慧之轮原本面向与专业及政策群体合作的成人引导者设计。此处的课堂改编版本并不声称具备经过同行评审的证据以证明其能提升学生的决策质量、观点采择或伦理推理能力。教师应将其视为具有理论基础且在课堂改编中经过专业实地检验的方法——而非拥有已验证学生成效的循证干预方案。

### 适用范围

将本技能用作探究序列末端的综合步骤：当团队已经绘制了现状图景、理解了系统动态并处理了核心张力，现在准备好做出深思熟虑的决策或设计负责任的下一步时。避免将其作为独立的首发活动——没有先期探究，学生缺乏使多元视角综合富有意义的共同理解。

## 输入模式

教师必须提供：
- **决策或挑战：** 置于决策轮中心的具体判断性问题。不应是事实性问题，而应是决策问题：“我们应该[提案]吗？”或“什么会让这项提案更明智？”如果学生正在审阅一项提案，请将该提案放在此处。
- **情境：** 学校、课程或社区背景。

可选：
- **先期探究摘要：** 来自范围界定、六边形映射、三地平线或两难驾驭且为本决策提供依据的洞察。这正是使决策轮言之有物的关键。
- **待纳入视角：** 特定的利益相关方、学科或透镜。若未提供，本技能将根据情境生成恰当视角。
- **学生水平：** 年级或年龄范围。
- **决策约束：** 决策必须在其中运作的现实约束。

## 提示词

```text
You are facilitating a multi-perspective decision wheel. Students will examine a specific decision or design challenge through multiple perspectives, identify tensions between them, and synthesise the insights into a wiser next step.

CRITICAL SEQUENCE: This skill works best after students have completed prior inquiry — scoping, hexagon mapping, Three Horizons, dilemma navigation. Without prior inquiry the wheel produces surface opinions. With prior inquiry it synthesises understanding into a considered recommendation.

CRITICAL PRINCIPLE: Each perspective is a lens, not a performance or stereotype. The goal is disciplined perspective-taking — genuinely trying to see what that perspective sees — not role-play theatre.

Inputs:
Decision or challenge: {{decision_or_challenge}}
Context: {{context}}
Prior inquiry summary: {{prior_inquiry_summary}}
Perspectives to include: {{perspectives_to_include}}
Student level: {{student_level}}
Decision constraints: {{decision_constraints}}

Step 1 — Frame the central question:
Place the decision or design challenge at the centre. The question must be a genuine question of judgement (what should we do, prioritise, change, protect, or try?). If the input is a proposal, reframe: "Should we [proposal]? What would make it wiser?"

Step 2 — Select perspectives:
If perspectives are provided, use them. If not, generate 4–6 perspectives appropriate to the context. Good perspective sets include:
- At least one perspective of someone not present in the room (future students, community members, non-humans, those most affected)
- At least one time perspective (what does the long-term view see that the immediate view misses?)
- At least one values perspective (what does an equity, fairness, or sustainability lens see?)
- At least one practical or implementation perspective (what does the person who has to do this every day see?)

Avoid stereotyped role-play roles. Prefer descriptive perspectives ("the long-term view," "students most affected," "the ecological perspective") over theatrical ones.

Step 3 — Apply each perspective:
For each perspective, generate:
- **Sees:** What does this perspective see that others might miss?
- **Misses:** What does this perspective tend to underweight or overlook?
- **Asks:** What question does this perspective put to the decision that must be answered?
- **Contributes:** What does honouring this perspective add to the decision?

Step 4 — Name tensions between perspectives:
Identify at least one genuine tension — where two perspectives see the situation differently, value different things, or recommend incompatible directions. Name the tension without resolving it. A wheel where all perspectives agree is not probing the decision deeply enough.

Step 5 — Synthesise wheel insights:
Based on the full wheel, identify what the combined perspectives reveal that no single perspective could see alone. This is the synthesis insight — the understanding that makes multi-perspective work valuable.

Step 6 — Improve the proposal:
Based on the wheel, state what the proposal or decision should:
- **Keep:** what is already wise and should be preserved
- **Change:** what would be improved by incorporating a perspective's insight
- **Test:** what is uncertain and needs a small experiment before full commitment
- **Stop:** what the wheel suggests dropping

Step 7 — Next responsible step:
Produce one specific, feasible next action:
- What the action is
- Who is responsible for it
- What evidence or permission is needed before the action is taken
- The limit — what this action should NOT do without further consultation

Step 8 — Quality check:
Apply these gates:
- FLAG if fewer than 4 perspectives are included (decision not examined broadly enough)
- FLAG if all perspectives agree (wheel is confirming a decision already made, not examining it)
- REQUIRE at least one tension between perspectives to be named
- REJECT outputs that go directly to "what we should do" without naming what each perspective contributes and misses
- FLAG if no perspective represents those most affected who are not present in the room

Return exactly:

## Decision Wheel: [Decision/Challenge]

**Central question:** [question at the centre of the wheel]
**Context:** [brief context]
**Prior inquiry drawn on:** [summary of insights informing this wheel]

---

### Perspectives

**Perspective 1 — [Name]**
- Sees: [what this perspective reveals]
- Misses: [what it tends to underweight]
- Asks: [the question it puts to the decision]
- Contributes: [what honouring this perspective adds]

[Repeat for each perspective — 4–6 total]

---

### Tensions Between Perspectives

- **[Perspective A] vs. [Perspective B]:** [What they see differently and why it matters for the decision]

---

### Synthesis Insights

[What the whole wheel reveals that no single perspective could see alone — 2–3 key insights]

---

### Proposal Improvements

**Keep:** [what is already wise]
**Change:** [what the wheel suggests improving]
**Test:** [what needs a small experiment before full commitment]
**Stop:** [what the wheel suggests dropping]

---

### Next Responsible Step

**Action:** [specific and feasible]
**Responsible:** [who will do this]
**Evidence or permission needed:** [what is required before acting]
**Limit:** [what this action should not do without further consultation]

---

### Quality Gate Results
- [ ] 4+ perspectives included: [pass/flag — state number used]
- [ ] Not all perspectives agree: [pass/flag]
- [ ] At least one tension named: [pass/flag]
- [ ] Perspectives examined before conclusions reached: [pass/flag]
- [ ] At least one perspective represents those most affected but not present: [pass/flag]
```

## 常见误区

1. **没有先期探究就运行决策轮。** 缺乏范围界定、系统映射与两难驾驭，决策轮只会产出伪装成多元视角的浅层意见。它的价值在于综合，而非凭空生成。
2. **使用戏剧化角色而非真实视角。** 让学生扮演“唱反调的人”或“乐观主义者”是角色扮演游戏，而非观点采择。请使用扎根于实际决策情境的描述性视角。
3. **跳过张力。** 一个所有视角都达成一致的决策轮并没有真正在审视决策——它只是在为早已做出的决定背书。请寻找视角之间真实的分歧点。
4. **还没看清整个决策轮就跳到下一步。** 顺序至关重要：先视角，再张力，后综合，最后才是下一步行动。
5. **忘记不在场的人。** 最值得纳入的视角往往属于那些受影响最深却不在场的人——未来的学生、社区成员、非人类存在，以及被现有权力结构边缘化的群体。

## 已知局限

1. **综合需要人类判断。** 本技能为明智决策产出结构化输入；它并不直接做出决策。权衡相互竞争的洞察并在不确定性下行动，需要教师与学生的判断。
2. **质量取决于先期探究。** 决策轮的分析价值取决于先前范围界定、映射与两难驾驭的质量。基于表面印象绘制的决策轮只能产出表面结果。
3. **视角选择具有实质后果。** 纳入与排除哪些视角直接塑造了综合结果。教师应将视角选择视为一项明确的分析和伦理抉择，而非中立练习。
4. **无法评估实施可行性。** 下一步负责任行动基于所提供的约束生成，无法评估该行动在特定学校的真实文化、治理结构或资源环境中是否真正可行。

## 核验清单

- [ ] 中心问题是真正的判断性问题，而非事实性问题。
- [ ] 至少纳入了 4 个视角。
- [ ] 每个视角均包含：所见、盲区、所问与所贡献。
- [ ] 至少有一个视角代表了不在场但受影响最深的群体。
- [ ] 至少命名了一处视角之间的真实张力。
- [ ] 综合洞察超越了任何单一视角所能提供的认知。
- [ ] 提案改进步骤明确列出了保留、改变、测试与停止的内容。
- [ ] 下一步负责任行动明确列出了行动、责任人、所需证据与限度。
- [ ] 全部五项质量把关点均已应用并报告。
