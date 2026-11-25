---
# AGENT SKILLS STANDARD FIELDS (v2)
name: dilemma-navigation-for-education-design
description: "识别并驾驭课程、学校或社区情境中的真实两难困境——无法被消除、只能被驾驭的竞争性善（competing goods）之间的张力。生成结构化的两难图谱，明确命名两极并提出“兼顾/兼容（both/and）”可能性。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS
skill_id: "original-frameworks/dilemma-navigation-for-education-design"
skill_name: "教育设计两难困境驾驭器"
domain: "original-frameworks"
version: "1.0"
evidence_strength: "emerging"
evidence_sources:
  - "H3Uni Dilemma Thinking tutorial and Dilemma Resolution mapping guide (CC BY-SA 4.0, practitioner method)"
  - "Johnson, B. (1992). Polarity Management: Identifying and Managing Unsolvable Problems. HRD Press."
  - "Hampden-Turner, C. (1990). Charting the Corporate Mind: From Dilemma to Strategy. Basil Blackwell."
input_schema:
  required:
    - field: "tension_or_dilemma"
      type: "string"
      description: "对张力的描述——看似相互冲突的两种价值、需求或方法分别是什么"
    - field: "context"
      type: "string"
      description: "该张力出现的课程、学校或社区情境"
  optional:
    - field: "value_a"
      type: "string"
      description: "第一极的名称——一侧的价值或原则"
    - field: "value_b"
      type: "string"
      description: "第二极的名称——另一侧的价值或原则"
    - field: "student_level"
      type: "string"
      description: "年级或年龄范围"
    - field: "related_systems_work"
      type: "string"
      description: "先前的三地平线映射或六边形映射中浮现出该困境的洞察"
output_schema:
  type: "object"
  fields:
    - field: "dilemma_statement"
      type: "string"
      description: "清晰陈述该两难困境，将两极均命名为正当价值"
    - field: "value_a_pole"
      type: "object"
      description: "价值 A：它提供什么、过度强调时的风险、它需要价值 B 提供什么、它能向价值 B 贡献什么"
    - field: "value_b_pole"
      type: "object"
      description: "价值 B：它提供什么、过度强调时的风险、它需要价值 A 提供什么、它能向价值 A 贡献什么"
    - field: "compromise_zone"
      type: "string"
      description: "看似能解决张力但实际上对两种价值都造成辜负的诱人中间地带"
    - field: "conflict_zone"
      type: "string"
      description: "真实痛点、权衡或互不相容感最尖锐的所在"
    - field: "both_and_possibilities"
      type: "array"
      description: "同时尊重两种价值而非以一种牺牲另一种的构想"
    - field: "implementation_constraints"
      type: "array"
      description: "任何整合构想面临的现实约束——资源、权限、时间、文化或结构"
    - field: "quality_gate_results"
      type: "object"
      description: "对两难图谱进行结构质量检查的结果"
chains_well_with:
  - "three-horizons-learning-transition-mapper"
  - "multi-perspective-decision-wheel"
  - "systems-awareness-iceberg"
  - "assessment-validity-checker"
  - "hexagon-complexity-mapper"
teacher_time: "15 分钟"
tags: ["h3uni", "dilemma-navigation", "values", "both-and-thinking", "original-framework", "emerging-evidence", "curriculum-design", "ethics"]
---

# 教育设计两难困境驾驭器

## 本技能的功能

帮助学生识别并驾驭课程、学校或社区情境中的真实两难困境——即双方都蕴含正当价值的张力，其目标不是选出赢家，而是寻找能够同时尊重两端的“兼顾/兼容（both/and）”可能性。本技能将**两难困境（dilemma）**与**问题（problem）**区分开来：问题有解决方案；而两难困境是真实的张力，若以牺牲另一方为代价去解决一方，就会造成另一种伤害。

产出是一份结构化的两难图谱：将两极均命名为正当价值、划定妥协区（看似诱人却两头不讨好的中间地带）、识别冲突区（痛点最尖锐之处）、明确两极之间的“提供与请求（offers and requests）”，以及附带现实约束的“兼顾/兼容”整合可能性。

在教育中，真实的两难困境十分普遍：个体成就 vs. 协作学习；标准化 vs. 个性化；安全感 vs. 挑战性；传统 vs. 创新；深度 vs. 广度；教师主导 vs. 学生能动性。两端都包含着真实的善。驾驭意味着寻找同时尊重两端的方法，而非非此即彼地二选一。

## 证据空间与证据强度

本技能编码了 H3Uni 两难困境驾驭（Dilemma Navigation）方法，并辅以 Barry Johnson 的极性管理（Polarity Management）框架。

### 组件证据

- **H3Uni 两难困境驾驭方法**（实践者框架）：H3Uni 资源库包含面向专业与政策情境中成人团队的《两难思维教程》与《两难解决映射指南》。其中阐述了两难/问题的区分、“兼顾/兼容”解决逻辑以及“提供与请求”框架。这些属于实践者资源，而非同行评审研究。
- **Johnson（1992）极性管理**（中等）：Johnson 的极性管理框架为组织情境中的真实两难困境提供了最系统的论述。他描述了“极性（polarities）”——无法被解决、只能被管理的价值对——并提供了识别每一极正面价值与负面风险的结构化方法。该框架已应用于教育与组织发展领域，具有中等实践证据支持。
- **Hampden-Turner（1990）《Corporate Mind》**（新兴）：Hampden-Turner 关于战略中两难困境的研究为竞争性善之间的真实张力提供了补充框架，特别是“最高价值的方案是同时尊重两极而非彼此妥协”这一理念。

### 综合证据

课堂两难困境驾驭模板——包括“兼顾/兼容”整合结构、“提供与请求”框架、妥协区/冲突区区分以及教育专属示例——由 Gareth Manning 在布达佩斯 REAL School 基于 H3Uni 的成人引导指南改编，以供学龄学生使用。这一课堂综合方案尚未接受过独立评估。

H3Uni 方法由 Anthony Hodgson 与 Bill Sharpe 创立的 H3Uni 以 CC BY-SA 4.0 协议发布。H3Uni 的正式运营已于 2026 年 5 月结束；其资源库现由 Future Stewards 作为开放共享资源维护。

### 本技能不应声称的内容

H3Uni 两难困境驾驭原本面向与专业及政策群体合作的成人引导者设计。此处的课堂改编版本并不声称具备经过同行评审的证据以证明其能提升学生的伦理推理、课程设计质量或冲突解决能力。教师应将其视为具有理论基础且在课堂改编中经过专业实地检验的工具——而非拥有已验证学生成效的循证干预方案。

### 适用范围

当探究中浮现出真实张力——理想情况下源于三地平线映射或六边形映射——且学生在提出行动方案前需要审慎思考时，使用本技能。当班级正在分化为两个阵营、当某个拟议方案看似顾全一种价值却损害另一种价值、或当学生需要针对教育设计、校规或社区决策练习伦理推理时，本技能尤为有价值。

## 输入模式

教师必须提供：
- **张力或两难困境：** 对已浮现张力的描述。现阶段可以较为模糊——本技能将协助命名两极。例如：“有些学生想要更多选择权；另一些学生在没有结构时会感到迷失”或“我们既想挑战学生，又想确保他们的安全”。
- **情境：** 该张力出现的课程、学校或社区情境。

可选：
- **价值 A：** 第一极的名称——一侧的价值或原则。
- **价值 B：** 第二极的名称。
- **学生水平：** 年级或年龄范围。
- **相关系统工作：** 先前在三地平线或六边形映射中浮现出该困境的洞察。

## 提示词

```text
You are facilitating a dilemma navigation exercise. Students are working with a genuine tension — a situation where two values both matter and choosing one at the expense of the other causes a different harm. The goal is not to pick a winner but to find both/and possibilities that honour each side.

CRITICAL DISTINCTION: A dilemma is not a problem. Problems have solutions that eliminate the tension. Dilemmas are genuine tensions where both sides contain legitimate value. If one side is obviously wrong, it is not a dilemma — it is a problem to solve. Check that both poles have real value before proceeding.

Inputs:
Tension or dilemma: {{tension_or_dilemma}}
Context: {{context}}
Value A: {{value_a}}
Value B: {{value_b}}
Student level: {{student_level}}
Related systems work: {{related_systems_work}}

Step 1 — Confirm this is a dilemma:
Check: Does each side contain real value that would be lost if it disappeared entirely? If yes, proceed. If one side is obviously wrong, name this and help the teacher reframe as a problem to solve rather than a dilemma to navigate.

Step 2 — Name both poles generously:
Name Value A and Value B. Each pole must be stated in its most generous form — what does this value genuinely protect, enable, or make possible? Name it as a legitimate good, not as an obstacle to the other side.

Step 3 — Map the compromise zone:
What is the tempting middle-ground response that appears to resolve the tension but actually fails both values? Name this trap specifically.

Step 4 — Map the conflict zone:
Where is the genuine pain, incompatibility, or trade-off most sharply felt in this specific context?

Step 5 — Offers and requests:
For each pole:
- What can Value A offer to Value B? (what does A contribute that B needs?)
- What does Value A need from Value B to function well without causing harm?
[Repeat for Value B]

Step 6 — Both/and integration possibilities:
Generate 2–3 ideas that honour both values simultaneously. These should:
- Go beyond compromise (not just "a bit of both")
- Name how each idea preserves the core of each value
- Acknowledge constraints and difficulties of implementation

Step 7 — Name implementation constraints:
For each both/and idea, name real constraints: resource, authority, time, cultural, structural, or relational factors that make implementation difficult.

Step 8 — Quality check:
Apply these gates:
- REJECT if one pole is obviously wrong (this is a problem — help the teacher reframe)
- FLAG if neither pole has named values — just positions or preferences
- FLAG if the output declares a winner ("Value A is more important") rather than seeking integration
- FLAG if both/and ideas are just compromises (50/50 splits) rather than genuine integration
- NOTE: Different students can legitimately hold different positions. Forced consensus is not the goal.

Return exactly:

## Dilemma Map: [Topic/Context]

**Dilemma statement:**
[Clear statement naming both poles as genuine values. Format: "Between [Value A] — [what it protects] — and [Value B] — [what it protects] — lies a genuine tension in which honouring one fully can compromise the other."]

---

### Value A — [Name]

**What Value A offers:** [what it protects, enables, or makes possible]
**What happens when Value A is over-emphasised:** [what is lost or harmed]
**What Value A needs from Value B:** [to function well without causing harm]
**What Value A can offer Value B:** [what it contributes that B needs]

---

### Value B — [Name]

**What Value B offers:** [what it protects, enables, or makes possible]
**What happens when Value B is over-emphasised:** [what is lost or harmed]
**What Value B needs from Value A:** [to function well without causing harm]
**What Value B can offer Value A:** [what it contributes that A needs]

---

### Compromise Zone (trap to avoid)
[The tempting middle-ground that fails both values in this context]

### Conflict Zone (where the pain is felt)
[Where the genuine incompatibility is felt most sharply]

---

### Both/And Integration Possibilities

**Option 1:** [Idea]
- Preserves Value A by: [how]
- Preserves Value B by: [how]
- Constraints: [what makes this difficult]

**Option 2:** [Idea]
- Preserves Value A by: [how]
- Preserves Value B by: [how]
- Constraints: [what makes this difficult]

---

### Quality Gate Results
- [ ] Both poles contain real value: [pass/fail — if fail, suggest reframing as problem]
- [ ] Both poles stated generously: [pass/flag]
- [ ] No winner declared: [pass/flag]
- [ ] Both/and ideas go beyond compromise: [pass/flag]
- [ ] Implementation constraints named: [pass/flag]

**Note on consensus:** Different students can legitimately hold different positions on this dilemma. The goal is shared understanding of why the tension is genuine, not forced agreement.

### Next Step Options
[multi-perspective-decision-wheel if the dilemma needs broader perspective before deciding; agency-circles-for-systems-action if students want to act within their sphere of control; assessment-validity-checker if this is a curriculum design dilemma]
```

## 常见误区

1. **把“问题”当成“两难困境”。** 如果其中一方明显是错的，那就不是两难困境。请将两难框架保留给竞争性善之间的真实张力。
2. **把两极表述为立场而非价值。** “有些学生想要 X，另一些想要 Y”只是立场表述。两难框架要求点明每种立场背后所守护的深层价值。
3. **宣布一个赢家。** “在此情境下价值 A 更重要”等于关闭了困境，而非驾驭困境。目标永远是“兼顾/兼容”——寻找同时尊重两种价值的方法，哪怕并不完美。
4. **把妥协当成整合。** 给每种价值各让步 50% 往往两边都无法满足。真正的整合是寻找方法同时守住每种价值的核心，而非各打五十大板。
5. **强迫达成共识。** 学生完全可以合法地对哪种价值更重要持有不同立场。目标是共同理解为什么这一张力是真实的，以及做出更明智的决策，而非强求一致。

## 已知局限

1. **需要真实的两难困境。** 只有当两极确实都蕴含价值时，本技能才有用。如果教师拿来一个伪装成两难的普通问题，本技能会标记出来，但无法自动生成恰当的重构。
2. **“兼顾/兼容”构想只是提案，而非现成方案。** 生成的整合可能性是设计的起点，而非成品政策。它们需要教师判断、社区协商与实施规划。
3. **无法评估群体心理安全感。** 特定班级是否适合公开探讨某一特定两难困境，取决于群体的信任度、成熟度以及议题的敏感性。教师的专业判断无可替代。
4. **具有高度情境依赖性。** 同一个两难困境在不同的学校文化、年级或学科领域中可能呈现出截然不同的面貌。本技能无法评估情境特定约束将如何决定哪些“兼顾/兼容”构想真正可行。

## 核验清单

- [ ] 该张力已确认为真实的两难困境（两极均具有真实价值）。
- [ ] 两极均以最宽容、最充分的形式被命名为正当的善。
- [ ] 妥协区被明确标示为陷阱，而非解决方案。
- [ ] 冲突区指出了在本情境中痛点实际发生在哪里。
- [ ] 每一极都陈述了“提供”与“请求”。
- [ ] “兼顾/兼容”整合构想超越了简单的 50/50 妥协。
- [ ] 每个构想都列明了实施约束。
- [ ] 全部五项质量把关点均已应用并报告。
- [ ] 包含了关于共识的说明。
