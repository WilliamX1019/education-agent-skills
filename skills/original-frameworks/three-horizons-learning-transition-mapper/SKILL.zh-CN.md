---
# AGENT SKILLS STANDARD FIELDS (v2)
name: three-horizons-learning-transition-mapper
description: "在三个共存的地平线上映射已界定范围的主题——承受压力的现行系统（H1）、理想未来（H3）以及分类为 H2+ 或 H2- 的转型创新——以理解变革动态并识别负责任的下一步行动。"
disable-model-invocation: false
user-invocable: true
effort: high

# EXISTING FIELDS
skill_id: "original-frameworks/three-horizons-learning-transition-mapper"
skill_name: "三地平线学习转型映射器"
domain: "original-frameworks"
version: "1.0"
evidence_strength: "emerging"
evidence_sources:
  - "Curry, A., & Hodgson, A. (2008). Seeing in multiple horizons: connecting futures to strategy. Journal of Futures Studies, 13(1), 1–20."
  - "Sharpe, B., Fazey, I., Hodgson, A., Leicester, G., & Lyon, A. (2016). Three horizons: A pathways practice for transformation. Ecology and Society, 21(2), 47."
  - "Sharpe, B., & Hodgson, A. (2019). Anticipation in three horizons. In R. Poli (Ed.), Handbook of Anticipation. Springer."
  - "H3Uni Three Horizons tutorials and facilitation guides (CC BY-SA 4.0, practitioner method)"
input_schema:
  required:
    - field: "scoped_topic"
      type: "string"
      description: "探究主题，理想情况下来自已完成的范围界定陈述——具体到足以为每个地平线生成实证证据"
    - field: "value_dimension"
      type: "string"
      description: "群体关切的价值或品质——即纵轴所代表的内容。例如：生态健康、学生幸福感、学习深度、归属感、公平性、社区韧性"
  optional:
    - field: "student_level"
      type: "string"
      description: "年级或年龄范围"
    - field: "existing_evidence"
      type: "string"
      description: "关于当前处境的已有数据、观察记录或学生作品"
    - field: "h3_seeds"
      type: "string"
      description: "在某处已经可见的理想未来萌芽——真实案例、原型或鼓舞人心的实践"
    - field: "prior_hexagon_map"
      type: "string"
      description: "如已有，先前六边形映射练习中的关键聚类或洞察"
output_schema:
  type: "object"
  fields:
    - field: "h1_map"
      type: "object"
      description: "承受压力的现行系统：失调证据、维持因素、H1 依然提供的功能"
    - field: "h3_map"
      type: "object"
      description: "理想未来模式：价值观、规范、关系；已经可见的萌芽"
    - field: "h2_map"
      type: "object"
      description: "分类为 H2+（向 H3 生长）与 H2-（以新语言延续 H1）的转型活动"
    - field: "transition_story"
      type: "string"
      description: "3–5 句话的转型故事，描述什么在衰退、什么在涌现、什么存在争议以及行动可能在何处起效"
    - field: "h2_plus_opportunities"
      type: "array"
      description: "值得支持或学习的具体 H2+ 创新"
    - field: "quality_gate_results"
      type: "object"
      description: "对三地平线图谱进行结构质量检查的结果"
    - field: "next_step_options"
      type: "array"
      description: "基于图谱洞察建议的后续技能"
chains_well_with:
  - "scoping-for-transformative-learning-inquiry"
  - "hexagon-complexity-mapper"
  - "dilemma-navigation-for-education-design"
  - "systems-awareness-iceberg"
  - "agency-circles-for-systems-action"
  - "place-based-inquiry-anchor"
  - "regenerative-project-design-orchestrator"
teacher_time: "20 分钟"
tags: ["h3uni", "three-horizons", "futures-thinking", "transition", "h2-plus", "h2-minus", "original-framework", "emerging-evidence", "systems-change", "programme-planning"]
---

# 三地平线学习转型映射器

## 本技能的功能

引导学生完成三地平线（Three Horizons）映射练习，帮助他们理解现行系统如何变化、他们希望培育何种未来，以及哪些创新真正通向那个未来。本技能产出一份结构化的三地平线图谱，包含：当前主导模式承受压力的证据（第一地平线 H1）；附带扎实案例的理想未来模式描述（第三地平线 H3）；以及一份区分 H2+（培育理想未来）与 H2-（用新语言延续旧模式）的转型创新分类清单。

三地平线**不是**一条时间线。三个地平线同时共存于当下：H1 要素在当下占据主导，H3 的萌芽在当下已经存在，而 H2 创新是当下正在争夺的场域。本技能编码了一套引导逻辑，使这种共存变得清晰可见且富有分析价值。

## 证据空间与证据强度

本技能编码了 H3Uni 三地平线（Three Horizons）方法——一种面向未来思维与变革性转型引导的实践者框架。

### 组件证据

- **Curry & Hodgson（2008）多重地平线**（新兴）：这篇奠基性论文将三地平线框架描述为战略未来思维的工具，为 H1/H2/H3 的区分及 H2+/H2- 分类提供了概念基础。该论文偏重理论与实践导向，而非对照研究。
- **Sharpe 等人（2016）路径实践**（新兴）：这篇发表于 *Ecology and Society* 的论文将三地平线描述为参与式转型路径工具，记录了其在专业与社区情境中的应用。它提供了关于该方法最系统的学术论述，包括 H2+/H2- 区分与引导序列。该论文不包含随机或比较研究设计。
- **Sharpe & Hodgson（2019）预期框架**（新兴）：本章将三地平线置于更广泛的预期与未来意识文献中，将其与群体如何发展共同未来思维的认知及社会学阐释相连接。
- **H3Uni 三地平线教程与引导指南**（实践者框架）：H3Uni 资源库包含面向政策、生态与组织情境中成人团队的分步三地平线映射引导指南。这些属于实践者资源，而非同行评审评估。

### 综合证据

本技能中编码的课堂改编版——包括引导序列、学生学习单提示、质量把关点以及 H2+/H2- 区分——由 Gareth Manning 在布达佩斯 REAL School 基于 H3Uni 的开放引导指南及上述学术论文为学龄学生开发。这一改编版本尚未接受过独立评估。核心知识框架归属于 H3Uni；课堂操作化由实践者综合而成。

H3Uni 方法由 Anthony Hodgson 与 Bill Sharpe 创立的 H3Uni 以 CC BY-SA 4.0 协议发布。H3Uni 的正式运营已于 2026 年 5 月结束；其资源库现由 Future Stewards 作为开放共享资源维护。

### 本技能不应声称的内容

H3Uni 三地平线原本面向与政策实践者、战略团队和专业群体合作的成人引导者设计。此处的课堂改编版本并不声称具备经过同行评审的证据以证明其能提升学生的未来思维、更好的转型设计成果或可迁移的系统变革能力。教师应将其视为具有理论基础且在课堂改编中经过专业实地检验的方法——而非经过验证的教育干预方案。

### 适用范围

在完成范围界定练习之后使用本技能，且尽可能在六边形映射之后使用。当学生已经认真思考过他们在调查什么并对系统结构有了某种共同理解时，该图谱效果最佳。避免将其作为独立的首发活动——没有先期范围界定，学生往往会在 H1 填满抱怨、在 H3 填满幻想，而非扎实的系统结构分析。

## 输入模式

教师必须提供：
- **已界定范围的主题：** 探究主题，理想情况下来自已完成的范围界定陈述。应足够具体，使学生能为 H1 提供具体证据并点出真实的 H3 萌芽。
- **价值维度：** 群体关切并希望放在纵轴上的价值或品质。这并非关于“H1 很坏”的道德判断——而是群体对“我们试图保护或培育什么”的共同宣言。

可选：
- **学生水平：** 年级或年龄范围，用于校准语言与抽象程度。
- **已有证据：** 关于当前处境的数据、观察记录、学生调查、故事或社区输入。
- **H3 萌芽：** 某处已经存在的理想未来的具体实例。
- **先前六边形图谱：** 如学生已完成六边形映射练习，从中获得的关键聚类或洞察。

## 提示词

```text
You are facilitating a Three Horizons mapping exercise. Students will map a complex topic across three coexisting patterns: the current dominant system under strain (H1), the preferred future pattern they want to grow (H3), and transition innovations (H2) sorted as H2+ (grows toward H3) or H2- (extends H1 in new language).

CRITICAL SEQUENCE: Always map in this order: H1 → H3 → H2. Never H1 → H2 → H3. Without mapping H3 first, it is impossible to distinguish H2+ from H2-. H2 innovations can only be classified once students know what future they are testing them against.

CRITICAL FRAMING: H1 is not "bad" and H3 is not "good." H1 elements persist in any real system and supply functions that must not be lost. H3 pockets already exist in the present. Frame the map as change dynamics, not moral categories.

Inputs:
Scoped topic: {{scoped_topic}}
Value dimension: {{value_dimension}}
Student level: {{student_level}}
Existing evidence: {{existing_evidence}}
H3 seeds: {{h3_seeds}}
Prior hexagon map: {{prior_hexagon_map}}

Step 1 — Map Horizon 1 (current pattern under strain):
H1 is the dominant current pattern: the dominant assumptions, practices, structures, metrics, and relationships that currently govern the topic. The vertical axis measures the value dimension. H1 is declining not because it is evil but because it is losing fit with changing conditions or values.

Ask: What evidence shows the current pattern is under strain? What keeps H1 in place even as it loses fit? Who benefits from H1 continuing? What does H1 still provide that we need?

Generate:
- Evidence of H1 strain: specific, observable examples showing the value dimension is being compromised
- H1 persistence factors: the structures, incentives, habits, or beliefs that sustain H1 even under pressure
- What H1 still provides: valuable functions any transition must preserve

Step 2 — Map Horizon 3 (preferred future pattern):
H3 is the pattern of life the group wants to grow: the values, norms, relationships, and practices that would represent genuine improvement in the value dimension. H3 is not a fantasy — it must be grounded in pockets already visible somewhere.

Ask: What would this system look like if the value dimension were genuinely flourishing? Where can we already see pockets of this future — in other schools, communities, projects, or places? What values and norms characterise H3?

Generate:
- H3 pattern description: what the preferred future looks, feels, and works like
- H3 pockets: real examples already existing somewhere that embody elements of H3
- H3 values: the shared values or principles this future is built on

Step 3 — Map Horizon 2 (transition innovations, sorted as H2+ or H2-):
H2 innovations are the experiments, projects, practices, and actors responding to pressure between H1 and H3. Some grow the preferred future (H2+). Others extend the old pattern in new language — they look like change but reinforce H1's core logic (H2-).

For each H2 item, test: Does this innovation genuinely move toward H3, or does it adapt H1 to survive? H2- items often use H3 language (sustainability, wellbeing, innovation) while leaving H1 structures intact.

For each H2 item generate:
- Description of the innovation or experiment
- Classification: H2+ or H2-
- Reasoning: why it grows H3 or why it extends H1

Step 4 — Tell the transition story:
Write a narrative (3–5 sentences) describing: what is declining in H1, what is emerging in H3, which H2 innovations are genuinely transitional, what is contested, and where the group might focus action.

Step 5 — Quality check:
Apply these gates:
- FLAG if H3 is empty or contains only vague aspirations with no grounded pockets (cannot distinguish H2+ from H2- without a concrete H3)
- FLAG if no H2 items are classified as H2+ or H2- (H2 listed without analysis)
- FLAG if H1 contains only complaints or blame without structural analysis (H1 needs evidence of strain AND persistence factors)
- REJECT if the output frames H1 as "bad" and H3 as "good" without nuance
- FLAG if H3 has no real-world pockets — aspiration only with no connection to present reality

Return exactly:

## Three Horizons Map: [Topic] — [Value Dimension]

**Scoped topic:** [topic]
**Value dimension:** [what the group cares about protecting or growing]

---

### Horizon 1 — Current Pattern Under Strain

**What H1 looks like:**
[Description of the dominant current pattern]

**Evidence of strain:**
- [Specific, observable example]

**What keeps H1 in place:**
- [Persistence factor — structure, incentive, habit, or belief]

**What H1 still provides:**
- [Function or value that any transition must preserve]

---

### Horizon 3 — Preferred Future Pattern

**What H3 looks like:**
[Description of the preferred future — grounded, not utopian]

**Pockets of H3 already visible:**
- [Real example — a school, community, project, or practice already embodying elements of H3]

**H3 values:**
- [Shared values or norms characterising this future]

---

### Horizon 2 — Transition Activity

| Innovation or Experiment | H2+ or H2-? | Reasoning |
|---|---|---|
| [name] | H2+ | [grows toward H3 because...] |
| [name] | H2- | [extends H1 in new language because...] |

**H2+ opportunities worth supporting:**
- [Key H2+ innovations with brief explanation]

---

### Transition Story
[3–5 sentence narrative: what is declining, what is emerging, what is contested, where action might help]

---

### Quality Gate Results
- [ ] H3 is grounded with at least one concrete pocket: [pass/flag]
- [ ] H2 items are classified as H2+ or H2-: [pass/flag]
- [ ] H1 includes structural analysis, not only complaints: [pass/flag]
- [ ] Map avoids moral framing of H1 as bad, H3 as good: [pass/flag]
- [ ] H3 is a pattern of life, not a list of innovations: [pass/flag]

### Next Step Options
[dilemma-navigation-for-education-design if the map surfaces a genuine tension between values; agency-circles-for-systems-action if students are ready to act; regenerative-project-design-orchestrator if a project design is needed]
```

## 常见误区

1. **按错误顺序映射（H1 → H2 → H3）。** 没有 H3 就位，学生无法对 H2 条目进行分类。他们只会罗列创新，却说不清哪些真正具有转型性。
2. **把 H3 当成幻想愿望清单。** H3 应当扎根于世界上某处已经可见的萌芽。没有真实案例的 H3 更难朝之行动，也更难用来检验创新。
3. **把 H2- 视为显然邪恶。** H2- 创新未必是不诚实的——它们往往代表了受制于现有结构的真实改进尝试。H2- 分类是分析性的，而非道德审判。
4. **把 H1 写成抱怨清单。** 强有力的 H1 会解释为什么该模式得以持续，而不仅仅是它有什么毛病。若不理解 H1 的维持因素，学生会低估转型的难度。
5. **把 H1 当成“过去”，把 H3 当成“未来”。** 全部三个地平线同时存在于当下。这不是历史时间线。

## 已知局限

1. **H2+/H2- 分类具有解释性。** 一项创新属于 H2+ 还是 H2-，取决于所选的价值维度与所持有的 H3 愿景。持有不同价值观的群体会得出不同的分类。这正是一项特点——它让价值差异变得可见。
2. **需要清晰的价值维度。** 若没有达成共识的纵轴，图谱就缺乏分析结构。无法就价值维度达成一致的群体，可能需要先进行价值澄清步骤。
3. **产出的是理解，而非行动。** 三地平线图谱揭示了转型动态；它不直接产出项目计划。需要后续技能才能从图谱走向行动。
4. **H3 的质量限制了 H2 的分析。** 模糊的 H3 只会产出模棱两可的 H2 分类。图谱的分析价值取决于 H3 愿景的具体性与扎根程度。

## 核验清单

- [ ] 引导序列遵循 H1 → H3 → H2。
- [ ] H1 同时包含承压证据与维持因素。
- [ ] H3 扎根于至少一个具体的现实世界萌芽。
- [ ] 每个 H2 条目均被分类为 H2+ 或 H2- 并附带明确推理。
- [ ] 图谱避免了道德化框架（H1 ≠ 坏，H3 ≠ 好）。
- [ ] 产出了转型故事，点明什么在衰退、什么在涌现以及什么存在争议。
- [ ] 全部五项质量把关点均已应用并报告。
- [ ] 下一步选项按真实名称引用了本技能库中的技能。
