# Education Skill Library — 构建简报 v3
*致 Claude Code：在编写任何单个技能之前，请先通读本全文。*
*修订：2026 年 3 月 — 扩展范围、三层架构、面向编排的设计。*

---

## 愿景

为教育者打造一套精选的 Claude 技能库——现有最严谨、以证据为基础、具备实际可用性的课程智能系统。不是提示词库，不是聊天机器人合集，而是一个**执行引擎（doing engine）**：原子化、可组合的技能，能够产出具体且立即可用的结果，从一开始就设计为既能单独运行（教师调用），也能协同运行（代理编排）。

最终，该技能库将成为 Kaku 内部的智能层。眼下，它是当今使用 Claude所能构建的最具价值的教育技术开源贡献。

**许可证：** CC BY-SA 4.0。开放、可分叉。贡献须满足纳入标准。

---

## 三层架构

在构建任何内容之前，理解这一架构至关重要。

### 第 1 层：技能（你现在正在构建的部分）
原子化、可调用的单元。每个技能接收已定义的输入、应用循证处理流程，并返回结构化输出。技能是基本原语。它们必须既能独立工作，又能组合——设计为使一个技能的输出可以作为另一个技能的输入。

### 第 2 层：上下文引擎（Kaku 的数据层 — 尚未构建）
使输出具有针对性而非泛泛而谈的层级。连接后，技能不仅知道“八年级 EAL 学生”——它还知道*这些*具体学生：他们的语言熟练度水平、上学期测评暴露的知识缺口、工作记忆特征、已学内容、即将学习的内容、学校采用的胜任力框架以及成绩报告系统的要求。

没有上下文引擎时：输出是高质量的通用模板。
接入上下文引擎后：输出是针对特定学生、特定课程和特定学校量身定制的方案。

设计技能时应使上下文引擎能够以可选参数的形式注入额外上下文——既不要假定泛化场景，也不要强制要求特定数据。

### 第 3 层：编排器（尚未构建）
一个接收高层教师目标（“为这个班级设计一个为期 6 周的气候变化单元”）的代理：查询上下文引擎、选择并排序合适的技能、串联它们的输出，并呈现完整结果供教师审阅与反馈。

**编排就绪要求：** 每个技能必须拥有机器可读的 schema 头部，以便编排器能够自动发现、选择和串联技能。现在就构建这一基础；编排器留待后续构建。

---

## 三重张力（保持不变 — 仍是核心设计约束）

每个技能都处于三项相互竞争的要求的交汇点。失去其中任何一项，技能就会失败。

**1. 严谨性（学习科学家的要求）**
每一项主张都必须扎根于可重复、经同行评审的证据。指明来源。如果证据薄弱或存在争议，该技能要么被裁剪，要么在“已知局限（Known Limitations）”中明确标出。经验之锥、学习风格、健脑操、左右脑优势、将多元智能作为*教学风格*处方——这些并非证据薄弱，而是**已被证伪**。它们不配获得脚注，而是直接被排除。

**2. 可用性（教师的要求）**
一位教师只有 20 分钟、面对一个具体班级、解决一个具体问题。输入必须是他们实际掌握的信息。输出必须可直接复制粘贴或直接付诸行动。如果教师需要花费大量额外思考才能使用输出，那么该技能就失败了。

**3. 精确性（提示词工程师的要求）**
精确的输入 schema。明确的输出格式。足够的约束，使得两位输入相似的教师能够获得结构一致、高质量的输出。绝不允许模糊的提示词产生模糊的输出。

---

## 纳入标准

一个技能只有同时满足**全部三项**条件才能入选：

1. **有证据支撑** — 扎根于具名且成熟的研究传统。不能说“研究表明”，而要说明*哪项*研究、*谁*的研究。
2. **产出具体成果** — 产出具体且可用的东西。不是建议，不是忠告，而是一个教师能直接使用的*实体产物*。
3. **高专业门槛** — 如果没有 AI，要做好这项工作需要耗费大量时间或专门知识。

---

## 明确排除清单

以下内容已被证伪、证据薄弱或过于泛泛而未达到专业门槛。请勿收录、引用或暗示：

- **学习风格（VARK、Dunn & Dunn 等）** — 没有可信证据表明将教学匹配到偏好学习风格能改善成效。Pashler 等人（2008）的系统综述已给出定论。
- **学习金字塔 / 经验之锥** — 错误归因于 Edgar Dale，他从未提出过百分比主张。“阅读记住 10%、教授他人记住 90%”这些数字完全是捏造的。
- **健脑操（Brain Gym）** — 没有神经学依据，是向学校推销的伪科学。
- **左右脑优势作为教学框架** — 已被神经影像学研究证伪。Nielsen 等人（2013）。
- **将多元智能用作教学处方** — Gardner 的多元智能理论描述的是智能，而非学习。“按每个学生的智能类型施教”的做法缺乏证据支持。Gardner 本人也曾反对这种用法。
- **将布鲁姆分类法视为质量层级** — 布鲁姆是一个分类系统，而非“高阶”任务永远更好的价值层级。对布鲁姆的误用极为普遍。要么精确使用，要么不用。
- **当前常见实施形式的成长型思维干预** — Dweck 的研究是真实的；但学校实施文献显示其大规模应用效果微弱且不稳定。若使用，须附上充分警示。
- **将坚毅力（Grit）作为可教授的特质** — Duckworth 的研究很有趣，但旨在学校中培养坚毅力的干预措施证据非常薄弱。
- **VAK（视觉/听觉/动觉）学习** — 学习风格的变体，问题相同，予以排除。
- **大多数“21 世纪技能”框架** — 往往定义模糊、证据薄弱且产出泛泛建议。仅当其中具体技能（例如 Wineburg 的横向阅读）自身拥有强大证据基础时才予收录。

---

## 机器可读 Schema 头部

每个技能文件必须在人类可读正文之前以此 YAML 头部开头，以支持编排。

```yaml
---
skill_id: "learning-science/retrieval-practice-generator"
domain: "learning-science"
name: "Retrieval Practice Question Generator"
version: "1.0"
evidence_strength: "strong"        # strong | moderate | emerging | practitioner
requires_context_engine: false     # true = 需要 Kaku 数据层才能发挥作用
chains_well_with:
  - "learning-science/spaced-practice-scheduler"
  - "assessment/formative-question-bank"
input_type: "topic + year_group + prior_knowledge_level"
output_type: "structured_question_set"
tags: ["retrieval", "memory", "formative-assessment"]
---
```

**字段定义：**
- `evidence_strength`：`strong` = 多项元分析；`moderate` = 一致的随机对照试验（RCT）；`emerging` = 有前景的早期研究；`practitioner` = 经过一线实践检验，尚无正式研究基础
- `requires_context_engine`：若为 `true`，该技能需要学生/课程数据才能产出有用输出。请如实标注——不要假装一个技能在缺乏数据时也能通用工作。
- `chains_well_with`：本技能输出可作为输入馈送给哪些 `skill_id`

---

## 技能文件模板

```markdown
---
[如上所示的 YAML 头部]
---

# [技能名称]

## What This Skill Does
[1–2 句话。产出什么具体成果？从输出成果讲起，而非流程。
为什么 AI 辅助在此处尤其有价值——不只是“节省时间”，而是它编码了什么专业知识。]

## Evidence Foundation
[3–5 句话。具体的研究传统。关键发现。带年份的具体引用。如果证据存在争议或课堂实施效果与实验室效果不同，在此说明。]

## Input Schema

教师必须提供：
- **[字段]：** [描述。斜体示例：*例如："photosynthesis" / "the water cycle" / "quadratic equations"*]

可选（若可用，由上下文引擎注入）：
- **[字段]：** [描述]

## Prompt

[实际的 Claude 提示词。必须包含：]
- [具备特定专业知识的专家角色设定]
- [Claude 用来评估自身输出的循证标准]
- [明确的输出格式：结构、标题、长度、包含与排除项]
- [输入占位符：{{double_brackets}}]
- [自检指令]

## Example Output

[针对特定场景的真实、高质量示例。]

## Known Limitations

[1–3 条诚实、具体的声明。]
```

---

## 构建顺序

- 第 1 阶段（当前）：编写简报与架构（本文档）。
- 第 2 阶段（Claude Code）：将所有技能构建为带有 YAML 头部与完整模板的 Markdown 文件。
- 第 3 阶段（测试）：针对 D2R 项目与福祉课程进行测试。
- 第 4 阶段（编排器）：在技能稳定并经过测试后，构建编排器代理。
- 第 5 阶段（Kaku）：上下文引擎集成。

---

## 致 Claude Code 的构建指令

**针对每个技能，按此顺序执行：**

1. 调研证据基础。编写 3–5 条带年份的具体引用。
2. 编写 YAML schema 头部。
3. 编写输入 schema。
4. 编写提示词。循证标准必须写在提示词*内部*。
5. 编写一个真实的示例输出。
6. 编写“已知局限（Known Limitations）”。

**硬性规则：**
- 绝不使用“研究表明”而不指明研究者与研究内容。
- 绝不产出没有结构的纯建议列表。
- 如果证据基础存在争议，在“已知局限”中说明。
- 如果某个技能与排除清单重叠，标记出来。
- 完整构建第 1 领域并审阅后再继续。

---

## 跨 14 个领域的 106 个技能

### 第 1 领域：记忆与学习科学（10 个技能）

1. Retrieval Practice Question Generator
2. Spaced Practice Schedule Builder
3. Interleaving Unit Planner
4. Cognitive Load Analyser
5. Worked Example Designer
6. Desirable Difficulty Task Designer
7. Elaborative Interrogation Prompt Generator
8. Self-Explanation Protocol Designer
9. Dual Coding Activity Designer
10. Prior Knowledge Activation Designer

### 第 2 领域：形成性评价与反馈（8 个技能）

1. Exit Ticket Designer
2. Hinge Question Designer
3. Feedback Quality Analyser
4. Live Observation Note Converter
5. Misconception Diagnostic Designer
6. Success Criteria Generator
7. Peer Assessment Protocol Designer
8. Whole-Class Feedback Template

### 第 3 领域：课程设计（8 个技能）

1. Backwards Design Unit Planner
2. Concept Map Generator
3. Prerequisite Knowledge Mapper
4. Transfer Task Designer
5. Threshold Concept Identifier
6. Curriculum Coherence Analyser
7. Cross-Curricular Connection Finder
8. Spiral Curriculum Planner

### 第 4 领域：差异化与包容性（8 个技能）

1. Tiered Task Designer
2. EAL Scaffold Generator
3. Worked Example Adaptation Tool (SEN)
4. Universal Design for Learning Checklist
5. Gifted Extension Task Designer
6. Reading Level Adaptor
7. Sensory Processing Accommodation Designer
8. Executive Function Scaffold Designer

### 第 5 领域：提问与讨论（7 个技能）

1. Socratic Seminar Question Designer
2. Bloom's Question Spectrum Builder
3. Cold Call Protocol Designer
4. Think-Pair-Share Optimiser
5. Discussion Facilitation Guide
6. Philosophical Enquiry Prompt Generator
7. Accountable Talk Stem Generator

### 第 6 领域：元认知与自我调节（8 个技能）

1. Implementation Intention Designer
2. Self-Regulation Strategy Selector
3. Metacognitive Reflection Prompt Generator
4. Goal-Setting Protocol Designer
5. Study Strategy Recommender
6. Affect Regulation Activity Designer
7. Attention Management Protocol
8. Self-Assessment Rubric Designer

### 第 7 领域：项目式学习（7 个技能）

1. Driving Question Designer
2. Project Milestone Planner
3. Authentic Audience Identifier
4. PBL Rubric Generator
5. Entry Event Designer
6. Exhibition Planning Guide
7. PBL Reflection Protocol

### 第 8 领域：福祉与积极教育（8 个技能）

1. PERMA-Based Lesson Designer
2. Strengths-Based Feedback Generator
3. Psychological Safety Audit
4. Belonging Activity Designer
5. Stress & Anxiety Psychoeducation Sequence
6. Mindfulness Integration Designer
7. Gratitude Practice Designer
8. Purpose & Ikigai Exploration Sequence

### 第 9 领域：专业学习与教学辅导（7 个技能）

1. Instructional Coaching Conversation Guide
2. Lesson Study Protocol Designer
3. Video Analysis Protocol
4. Peer Observation Framework
5. Professional Learning Community Facilitator Guide
6. Teacher Reflection Prompt Generator
7. Student Data Interpretation Guide

### 第 10 领域：媒体素养与批判性思维（8 个技能）

1. Lateral Reading Protocol Designer
2. SIFT Framework Lesson Designer
3. Source Credibility Analyser
4. Argument Mapping Tool
5. Logical Fallacy Identifier
6. Claim-Evidence-Reasoning Designer
7. Bias Detection Activity Designer
8. Misinformation Inoculation Lesson Designer

### 第 11 领域：创业精神与能动性技能（7 个技能）

1. Ikigai Exploration Sequence
2. Design Thinking Sprint Designer
3. Prototyping Protocol Designer
4. Pitch Feedback Protocol
5. Opportunity Identification Activity
6. Risk Tolerance Activity Designer
7. Agency Self-Assessment Designer

### 第 12 领域：AI 增强学习设计（7 个技能）

1. Adaptive Hint Sequence Designer
2. Erroneous Example Designer
3. Digital Worked Example Sequence
4. Individual Spacing Algorithm Explainer
5. AI Feedback Design Principles
6. Intelligent Tutoring Dialogue Designer
7. Learning Analytics Interpretation Guide

### 第 13 领域：蒙特梭利与替代性循证教学路径（4 个技能）

1. Three-Part Lesson Designer (Montessori)
2. Prepared Environment Designer
3. Mixed-Age Learning Task Designer
4. Uninterrupted Work Cycle Designer

### 第 14 领域：D2R、SEEDS 与 Gareth 原创框架（8 个技能）

> ⚠️ **本领域在构建前必须与 Gareth Manning 进行专门的简报沟通。切勿仅凭名称臆测或推断。请等待简报沟通。**

本领域中的每个技能必须在“What This Skill Does”章节开头写明：
*“This skill encodes an original practitioner framework developed by Gareth Manning at REAL School Budapest. Unlike skills in other domains, it is not drawn from peer-reviewed research traditions. It is grounded in 20 years of international education experience and is being actively tested in real classroom contexts.”*

1. 7-Stage D2R Project Cycle Designer
2. SEEDS Observation & Documentation Protocol
3. Developmental Band Competency Designer
4. Curriculum Outcome Decomposition Tool
5. Coherent Rubric Logic Builder
6. D2R Assessment Evidence Mapper
7. Habit Design Curriculum Sequence
8. Competency Framework to Developmental Band Mapper

---

## 完成全部 14 个领域后需构建的支持文件

1. **README.md** — 开篇即阐明“立即可用，任何使用 Claude 的教师今天就能上手。”
2. **ARCHITECTURE.md** — 重构为“可组合且可扩展”。
3. **IMPLEMENTATIONS.md** — 与 Strive、Hippo、Ren、Kaku 的关联。
4. **CONTRIBUTING.md** — 面向外部贡献者的纳入标准。
5. **MCP server**（新仓库：`education-agent-skills-mcp`）— 将技能暴露为可调用的 Claude 工具。MIT 许可证。

---

*简报最后更新：2026 年 3 月 — v3。新增第 10–14 领域。*
