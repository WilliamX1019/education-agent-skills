---
# AGENT SKILLS STANDARD FIELDS (v2)
name: hexagon-complexity-mapper
description: "通过将要素放置在六边形磁贴上绘制复杂主题图谱，其中“相邻”代表主张存在某种关联。适用于学生在分析或行动前需要揭示系统隐藏关联的场景。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS
skill_id: "systems-thinking/hexagon-complexity-mapper"
skill_name: "六边形复杂性映射器"
domain: "systems-thinking"
version: "1.0"
evidence_strength: "emerging"
evidence_sources:
  - "Hodgson, A. (1992). Hexagons for systems thinking. European Journal of System Dynamics, 59(1), 220–230."
  - "Meadows, D. (2008). Thinking in Systems. Chelsea Green. (systemic structure, feedback, unintended consequences)"
  - "Senge, P. (1990). The Fifth Discipline. Doubleday. (mental models, systems archetypes, seeing wholes)"
  - "H3Uni Hexagon Mapping tutorial and facilitation guides (CC BY-SA 4.0, practitioner method)"
input_schema:
  required:
    - field: "topic_or_challenge"
      type: "string"
      description: "学生正在映射的复杂主题、议题或挑战——具体到足以生成 8–20 个不同要素"
    - field: "context"
      type: "string"
      description: "锚定本次映射的学校、社区、生态或课程背景"
  optional:
    - field: "student_level"
      type: "string"
      description: "年级或年龄范围，用于校准词汇与抽象度"
    - field: "mapping_question"
      type: "string"
      description: "聚焦映射的具体问题——例如‘哪些因素正在塑造这一局面？’"
    - field: "prior_scoping_statement"
      type: "string"
      description: "如果已完成，来自 scoping-for-transformative-learning-inquiry 的范围界定陈述"
    - field: "existing_evidence"
      type: "string"
      description: "关于该主题已有的资料、故事、观察或学生作品"
output_schema:
  type: "object"
  fields:
    - field: "mapping_question"
      type: "string"
      description: "引导六边形图谱的聚焦问题"
    - field: "factor_list"
      type: "array"
      description: "供学生填写在六边形卡片上的所有要素"
    - field: "clusters"
      type: "array"
      description: "带有成员要素及各聚类所讲述故事的命名聚类"
    - field: "named_relationships"
      type: "array"
      description: "六边形或聚类之间至少三条具体关系，包含方向与解释"
    - field: "boundary_hexagons"
      type: "array"
      description: "位于图谱边缘的要素，代表外部力量或变革切入点"
    - field: "map_insights"
      type: "array"
      description: "完成后的图谱揭示了哪些映射前不明显的信息"
    - field: "quality_gate_results"
      type: "object"
      description: "图谱结构质量检查的结果"
    - field: "next_step_options"
      type: "array"
      description: "基于图谱结构建议的后续衔接技能"
chains_well_with:
  - "systems-awareness-iceberg"
  - "mental-model-mapper"
  - "three-horizons-learning-transition-mapper"
  - "leverage-and-response-design"
  - "agency-circles-for-systems-action"
  - "place-based-inquiry-anchor"
teacher_time: "15 分钟"
tags: ["systems-thinking", "hexagon-mapping", "complexity", "relationships", "h3uni", "visual-facilitation", "emerging-evidence", "student-inquiry"]
---

# 六边形复杂性映射器（Hexagon Complexity Mapper）

## 本技能的功能

引导学生开展六边形映射练习：他们识别塑造某个复杂主题的要素，将每个要素写在一张六边形卡片上，并排列这些卡片，使“相邻”（物理接触）标示两个要素之间存在主张的关联。这种排列不是按类别归类，而是一种集体的“关系主张”行为。当两个六边形靠在一起时，学生是在断言“这两个事物在某种程度上相互影响”，并且必须能够解释**如何**影响。

这一区分至关重要。六边形映射不是换了个好看形状的头脑风暴。它是一个揭示复杂情境隐藏连接脉络的工具：哪些要素因为相互强化而聚在一起，哪些作为外部力量处于系统边界，以及哪些要素通过出现在多个聚类中而起到连接全图的桥梁作用。

本技能产出一张共享的视觉图谱，成为后续工具（如“三视野映射 Three Horizons”、系统意识冰山或能动性圈）的输入。

## 循证空间与证据强度

本技能编码了由 Anthony Hodgson 开发的实践框架——H3Uni 六边形映射法（Hexagon Mapping）。它并非经过实证验证的课堂干预措施。

### 组成部分证据

- **Hodgson（1992）六边形系统思考**（新兴证据）：Hodgson 的论文将六边形描述为一种定性系统映射工具，特别适用于揭示在列表或层级结构中看不见的关系。该论文为“相邻 = 关系”原则提供了理论基础，但未包含课堂评估数据。
- **Meadows（2008）系统结构**（强证据）：Meadows 对系统结构（存量、流量、反馈回路与杠杆点）的论述提供了理论框架，使六边形映射在其中具有意义。理解复杂行为源自系统结构而非孤立要素，正是基于关系的映射的理论依据。
- **Senge（1990）心智模式与系统基模**（中等证据）：Senge 关于学习型组织的研究确立了心智模式会过滤人们看到的要素与关系。六边形映射将这些心智模式外显化，使其变得可见且可共同修订。
- **H3Uni 六边形映射引导指南**（实践者框架）：H3Uni 资源库包含面向政策与战略领域成人团队的分步引导指南和教程。这些属于实践者资源，而非同行评审研究。

### 综合证据

将六边形映射应用于学龄学生与课堂探究情境属于一种课堂适配。本技能中编码的引导流程、质量关卡、学生学习单提示和教师策略由 Gareth Manning 在布达佩斯 REAL School 借鉴 H3Uni 开放引导指南开发而成。该综合适配尚未经过独立评估。

H3Uni 方法由 Anthony Hodgson 和 Bill Sharpe 创立的 H3Uni 依据 CC BY-SA 4.0 协议发布。H3Uni 正式运营于 2026 年 5 月结束；资源库由 Future Stewards 作为开放公共资源维护。

### 本技能不应宣称的内容

H3Uni 六边形映射最初是为政策实践者、战略团队和专业群体服务的成人引导师设计的。此处的课堂适配不宣称拥有改善学生成绩、深化系统思维或培养可迁移复杂性驾驭能力的同行评审证据。教师应将其视为在课堂适配下有理论基础且经过专业实地检验的方法——而非具有已验证效应的循证干预。

### 适用场景

当学生需要在分析或行动规划之前，将他们对复杂情境的集体理解外显化并进行协商时，使用本技能。它在范围界定练习明确了小组调查对象之后、以及在使用需要共享情境模型的工具（三视野映射、能动性圈、系统冰山）之前最为有用。避免将其用作热身头脑风暴或单纯的分类工具——必须全程积极维持“关系逻辑”。

## 输入规范

教师必须提供：
- **主题或挑战：** 一个复杂议题，具体到足以生成 8–20 个不同要素。例如：“是什么在塑造我们学校与技术的关系？”或“哪些因素正在影响本年级学生的身心健康？”
- **情境：** 这一探究在何处发生以及为何重要。

可选：
- **学生水平：** 年级或年龄，以校准语言、抽象度及预期的六边形数量。
- **映射问题：** 锚定练习的具体问题。如未提供，本技能将根据主题自动生成。
- **先前的范围界定陈述：** 如果学生已完成范围界定练习，请包含该陈述以便映射问题与之对齐。
- **现有证据：** 可供参考的相关数据、观察、学生反馈或社区输入。

## Prompt

```text
You are facilitating a hexagon complexity mapping exercise. Students will identify factors shaping a complex topic, write each on a hexagonal tile, and arrange tiles so that touching hexagons signal a claimed relationship.

CRITICAL PRINCIPLE: Adjacency is the meaning. When two hexagons touch, students are asserting "these two factors affect each other." This is not a sorting or categorisation exercise. Every placement is a relationship claim that students should be able to explain.

Inputs:
Topic or challenge: {{topic_or_challenge}}
Context: {{context}}
Student level: {{student_level}}
Mapping question: {{mapping_question}}
Prior scoping statement: {{prior_scoping_statement}}
Existing evidence: {{existing_evidence}}

Step 1 — Form the mapping question:
If a mapping question was provided, use it. If not, generate one that asks what factors are shaping the topic — not what solutions are needed. The question should be broad enough to invite diverse factors and specific enough to be answerable with evidence. Format: "What factors are shaping [topic] in [context]?"

Step 2 — Factor generation:
Generate 12–18 factors for the topic. Each factor should be:
- Specific (not vague like "society" or "money")
- Expressible in 2–4 words on a hexagon tile
- A genuine mix of: people and groups; structures and systems; events and patterns; values and beliefs; resources and constraints; environmental and material conditions
Label this: "Suggested starting factors — students should add, remove, and rename these."

Step 3 — Clustering guidance:
Provide step-by-step instructions for the class:
1. Spread all tiles loosely and read them together before touching them.
2. Move tiles that clearly belong near each other. Ask: "What makes these two belong together?" — students must name the relationship, not just a shared theme.
3. Build clusters by adding tiles with a relationship to existing cluster members.
4. Name each cluster with a phrase capturing the story it tells, not a category label. Example: "trust erodes when accountability is unclear" not "accountability."
5. After clustering, add arrows between clusters where one cluster strongly influences another.
6. Identify boundary hexagons — tiles at the edge representing forces outside the group's direct control.

Step 4 — Relationship naming:
Identify at least three specific relationships. Each should state:
- Factor A
- Factor B
- How A affects B, or how they affect each other
- Whether the relationship is reinforcing (more A → more B) or balancing (A limits B)
- Evidence level: "we observed this," "we believe this," or "we're guessing"

Step 5 — Quality check:
Apply these gates:
- REJECT if the map has fewer than 6 hexagons (topic too narrow or question too simple)
- FLAG if all hexagons touch all others (no structure found — ask students to re-examine which connections are strongest and which are absent)
- FLAG if there are no boundary hexagons (ask what forces from outside the group's control are shaping the situation)
- FLAG if students cannot name 3 specific relationships (tiles placed by category, not relationship — return to clustering Step 2)

Step 6 — Map insights:
Based on map structure, identify:
- Which cluster is most central (connected to the most other clusters)?
- Which factor appears in multiple clusters (a bridge factor)?
- Which factors at the boundary are entry points for change or external forces?
- What does the map reveal that a simple list would have hidden?

Return exactly:

## Hexagon Map: [Topic]

**Mapping question:** [question]
**Context:** [brief context]

### Suggested Factors
[12–18 factors, one per line, with note that students should revise these]

### Clustering Guidance
[Step-by-step instructions for the class]

### Named Relationships
| Factor A | Factor B | How they relate | Reinforcing or balancing? | Evidence level |
|---|---|---|---|---|
[At least 3 rows]

### Cluster Stories
[For each cluster: cluster name (story-phrase), member factors, what the cluster reveals]

### Boundary Hexagons
[Factors at the edge — what they are and what they suggest]

### Map Insights
[What the completed map structure reveals]

### Quality Gate Results
- [ ] Map has 6+ hexagons: [pass/flag]
- [ ] Clusters based on relationships, not just themes: [pass/flag/note for teacher]
- [ ] Boundary hexagons present: [pass/flag]
- [ ] At least 3 specific relationships named: [pass/flag]
- [ ] No cluster contains 8+ tiles without a sub-story: [pass/flag]

### Next Step Options
[Suggest follow-on skills by name: systems-awareness-iceberg if a power or structural cluster is central; three-horizons-learning-transition-mapper if the map has a time dimension; leverage-and-response-design if students want to identify intervention points]
```

## 常见误区

1. **把它当成普通头脑风暴来跑。** 如果学生只生成要素而不提出关系主张，六边形映射就失去了其独特价值。排列过程本身就是分析工作，而非装饰。
2. **使用类别名称而非关系故事。** 命名为“社会因素”的聚类并不算完成映射。命名为“同伴压力塑造了哪些冒险行为让人觉得安全”的聚类才算。
3. **不加解释就接受相邻摆放。** 如果学生把两个六边形靠在一起却无法解释它们如何关联，那这次摆放只是猜测，而非关系主张。在继续前务必追问。
4. **跳过边界六边形。** 处于系统边界的要素往往揭示了最重要的杠杆点：哪些无法直接改变，以及哪些是从外部进入系统的力量。
5. **用图谱去印证既有偏见。** 一张看起来和教师预期一模一样的图谱应当引起警觉。追问：“什么让我们感到意外？这张图里漏掉了什么？”

## 已知局限性

1. **关系主张只是假设。** 图谱代表的是学生对系统的认知，而非经过验证的因果结构。已命名的关系应被视为需要证据检验的假设。
2. **物理媒介很重要。** 本技能产出引导指南与建议要素，但它不能替代实体六边形卡片或数字白板工具。可触碰、可移动的媒介特性本身就是该方法价值的一部分。
3. **孤立使用时效果不佳。** 六边形映射产出的是共享模型，而非行动计划。若没有后续工具（三视野、能动性圈、冰山），图谱只会沦为静态展品而非分析工具。
4. **超大群体下效果会下降。** 在超过 20 人的班级中，多组分别绘制图谱再进行“画廊漫步”对比，比全班合画一张大图更有成效。

## 核查清单

- [ ] 映射问题足够具体，能够激发多样且非显而易见的要素。
- [ ] 建议要素真正混合了人物、结构、价值观、事件与物质条件。
- [ ] 聚类指导明确说明“相邻 = 关系”，而非类别归属。
- [ ] 至少命名了 3 条具体关系，包含方向与证据等级。
- [ ] 识别并解读了边界六边形。
- [ ] 应用并报告了全部四项质量关卡。
- [ ] 下一步选项按真实技能名称引用了技能库中的后续技能。
