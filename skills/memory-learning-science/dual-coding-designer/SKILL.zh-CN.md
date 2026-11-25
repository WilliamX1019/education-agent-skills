---
# AGENT SKILLS STANDARD FIELDS (v2)
name: dual-coding-designer
description: "运用双重编码原则为口头/文字内容设计视觉补充，以强化记忆编码。适用于制作幻灯片、图表、海报或复杂概念的视觉解释。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "memory-learning-science/dual-coding-designer"
skill_name: "双重编码设计器"
domain: "memory-learning-science"
version: "1.0"
evidence_strength: "strong"
evidence_sources:
  - "Paivio (1986) — Mental Representations: A Dual Coding Approach"
  - "Clark & Paivio (1991) — Dual coding theory and education"
  - "Mayer (2009) — Multimedia learning: second edition (multimedia principle and related principles)"
  - "Mayer & Moreno (2003) — Nine ways to reduce cognitive load in multimedia learning"
  - "Caviglioli (2019) — Dual Coding with Teachers (practical application of the research)"
input_schema:
  required:
    - field: "verbal_content"
      type: "string"
      description: "需要为其设计视觉补充的解释、概念或文本"
    - field: "subject_and_level"
      type: "string"
      description: "学科领域与年级"
  optional:
    - field: "visual_constraints"
      type: "string"
      description: "视觉形式的任何限制（如“必须可在白板上手绘”/“用于幻灯片演示”）"
    - field: "student_profiles"
      type: "array"
      description: "来自上下文引擎：语言熟练度、视觉加工需求"
    - field: "existing_visuals"
      type: "string"
      description: "该主题已在使用的视觉材料，应与之互补而非重复"
output_schema:
  type: "object"
  fields:
    - field: "visual_design"
      type: "object"
      description: "推荐的图表类型、空间布局、标注策略及具体描述"
    - field: "integration_notes"
      type: "string"
      description: "如何将口头与视觉内容结合呈现以避免分散注意"
    - field: "annotation_strategy"
      type: "string"
      description: "图表上应保留哪些文字以及哪些保留为口头讲解"
    - field: "common_pitfalls"
      type: "array"
      description: "会增加而非降低认知负荷的视觉设计误区"
chains_well_with:
  - "cognitive-load-analyser"
  - "worked-example-fading-designer"
  - "text-complexity-analyser"
  - "explicit-instruction-sequence-builder"
teacher_time: "4 分钟"
tags: ["dual-coding", "visual-representation", "multimedia", "cognitive-load", "diagrams"]
---

# 双重编码设计器

## 本技能的功能

接收一段口头解释或概念，设计与之互补的视觉表征——明确最能支持理解的图表类型、空间布局、标注策略与注释方法。这**不是**为了让内容“更视觉化”或迎合“视觉型学习者”（一个已被证伪的概念），而是为了利用一项已被充分证实的研究发现：同时通过言语与视觉双通道加工信息，比单一通道能形成更牢固、更易提取的记忆痕迹。AI 在此处具有独特价值，因为为一个概念选择正确的视觉表征需要同时理解知识结构（顺序型？层级型？因果型？空间型？）和多媒体学习原则——大多数教师默认使用装饰性图片或过于复杂的图表，反而增加了而非降低了认知负荷。

## 循证基础

Paivio（1986）的双重编码理论确立了人类认知通过两个独立通道运作——言语通道（基于语言）与非言语通道（基于图像），且通过双通道编码的信息比仅通过单一通道编码的信息更容易提取。Clark 与 Paivio（1991）将其应用于教育领域，证明互补的言语与视觉表征能够提升学习成效。Mayer（2009）将双重编码操作化为十二项多媒体学习原则，包括多媒体原则（人们从文字加图片中学得比仅从文字中学得更好）、邻近性原则（文字与图片应一起呈现而非分离）以及一致性原则（无关的视觉材料会损害学习）。Mayer 与 Moreno（2003）确定了降低多媒体学习认知负荷的九种具体方法，包括消除诱人细节（有趣但无关的图片）、运用空间邻近性（将文字放在对应视觉元素附近）以及信号提示（使用视觉线索引导注意力）。**关键区分：** 双重编码关乎**互补性**表征——视觉呈现的是文字无法高效传达的内容（空间关系、过程、层级）。它**绝不是**将内容匹配到学生的“偏好学习风格”，后者已被证伪（Pashler et al., 2008）。无论所谓的风格偏好如何，所有学习者都能从精心设计的双重编码中受益。

## 输入模式

教师必须提供：
- **言语内容：** 需要视觉补充的解释或概念。*例如：“渗透作用的过程：水分子通过半透膜从高水浓度区域向低水浓度区域移动” / “第一次世界大战的成因可分为长期原因、短期原因和导火索”*
- **学科与水平：** 学科领域与年级。*例如：“九年级生物” / “十一年级历史”*

可选（如有，由上下文引擎注入）：
- **视觉限制：** 格式要求。*例如：“必须能在2分钟内画在白板上” / “用于打印学习单”*
- **学生档案：** 语言熟练度、视觉加工需求
- **现有视觉材料：** 已在使用的视觉材料，以避免重复

## 提示词

```
You are an expert in multimedia learning and cognitive psychology, specialising in Paivio's (1986) dual coding theory, Mayer's (2009) multimedia learning principles, and their practical application to classroom instruction. You understand the critical difference between decorative visuals (which add cognitive load) and complementary visuals (which reduce it and strengthen encoding).

Your task is to design a visual representation that complements this verbal content:

**Verbal content:** "{{verbal_content}}"
**Subject and level:** {{subject_and_level}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Visual constraints:** {{visual_constraints}} — if provided, design within these constraints. If not provided, design a visual that can be drawn on a whiteboard or created in simple presentation software.
**Existing visuals:** {{existing_visuals}} — if provided, design something complementary, not duplicative. If not provided, design the single most effective visual for this content.
**Student profiles:** {{student_profiles}} — if provided, consider language and visual processing needs. If not provided, design for a typical mixed-ability class.

Apply these evidence-based multimedia learning principles:

1. **Multimedia principle (Mayer, 2009):** The visual must ADD information that the verbal content alone does not efficiently convey. If the visual just restates what the text says (e.g., a picture of a book next to text about books), it is decorative and adds extraneous load. Ask: what does the visual show that the words cannot easily describe?

2. **Match the visual type to the knowledge structure:**
   - **Sequential process → flowchart or cycle diagram** (shows order and direction)
   - **Hierarchical relationship → tree diagram or nested boxes** (shows levels and containment)
   - **Causal relationship → arrow diagram with cause-effect labelling** (shows causation, not just correlation)
   - **Spatial/physical structure → labelled diagram or cross-section** (shows location and spatial relationships)
   - **Comparison → side-by-side or Venn diagram** (shows similarities and differences)
   - **Part-whole relationship → exploded diagram or pie chart** (shows proportion and composition)
   - **Timeline → horizontal timeline with intervals** (shows chronological sequence and duration)

   The wrong diagram type for the knowledge structure actively hinders learning. A hierarchy shown as a timeline, or a process shown as a Venn diagram, creates confusion.

3. **Contiguity principle (Mayer, 2009):** Text labels must be placed directly on or immediately adjacent to the visual elements they describe — NOT in a separate legend or key that forces the learner to split attention between the diagram and the legend. Integrated labels reduce split-attention effect (Sweller, 1994).

4. **Coherence principle (Mayer, 2009):** Remove ALL decorative elements. No clip art. No background images. No decorative borders. No colour used purely for aesthetics. Every visual element must carry information. Seductive details — interesting but irrelevant images — actively harm learning (Harp & Mayer, 1998).

5. **Signalling principle (Mayer, 2009):** Use visual cues (colour, size, arrows, numbering) to direct attention to the most important elements and relationships. Colour should encode meaning (e.g., red for danger/hot, blue for cold, green for growth), not decoration.

6. **NOT learning styles (Pashler et al., 2008):** This visual is for ALL learners, not for "visual learners." Dual coding works because two complementary representations create more retrieval pathways than one, regardless of any supposed style preference. Do not reference learning styles anywhere in the output.

Return your output in this exact format:

## Dual Coding Design: [Topic]

**For:** [Subject and level]

### Recommended Visual Type
[Diagram type and why it matches the knowledge structure]

### Visual Description
[Detailed description of the visual: layout, elements, spatial arrangement, labels, arrows, colour coding. Sufficient detail for a teacher to draw it or create it digitally.]

### Spatial Layout
[ASCII sketch or detailed spatial description showing element placement]

### Annotation Strategy
- **On the visual:** [What text goes directly on the diagram]
- **Verbal (teacher narration):** [What the teacher says while showing the visual — this goes in the verbal channel, not on the diagram]
- **DO NOT include on the visual:** [What should be kept out to avoid redundancy]

### Integration Notes
[How to present the verbal and visual together in the classroom — sequence, timing, whether to build the diagram progressively or show it complete]

### Common Pitfalls to Avoid
[2–3 specific mistakes that would turn this from a learning aid into a cognitive load problem]

**Self-check before returning output:** Verify that (a) the visual adds information the verbal content cannot easily convey, (b) the diagram type matches the knowledge structure, (c) all text is integrated directly onto the visual (no separate legends), (d) there are no decorative elements, (e) colour is used for meaning not aesthetics, and (f) no reference is made to learning styles.
```

## 示例输出

**场景：** *言语内容：“水循环包括水体蒸发、植物蒸腾、凝结成云、以雨或雪的形式降水，以及在河流、湖泊和地下水中汇集。该循环由太阳能和重力驱动。” / 学科与水平：“七年级地理” / 视觉限制：“必须能在3分钟内画在白板上”*

---

## 双重编码设计：水循环

**适用对象：** 七年级地理

### 推荐视觉类型
**带空间语境的循环图**——水循环是一个包含空间要素（地表、大气、地下）的连续过程，因此视觉表征必须同时展示顺序过程（循环）以及每个阶段发生的物理位置（空间）。简单的编号流程图会遗漏空间关系；纯粹的空间图（地形剖面图）则会遗漏循环性质。本设计将两者结合：一幅带有展示过程流向循环箭头的地形剖面图。

### 视觉描述
一幅占据白板全宽的简化地形剖面图，展示：

- **左侧：** 水体（海洋/湖泊）——画成一条带标签的简单弧形水面
- **中部：** 陆地表面，画有一棵树和一座简化的山丘/高山
- **右侧：** 陆地向下倾斜，一条河流流回水体
- **上方：** 画在白板顶部中央的云朵
- **地下（右侧）：** 一层虚线表示的地下水层

过程箭头将各要素连接成一个循环：
1. **从水面指向云朵的向上箭头**，标注“EVAPORATION（蒸发）”，附注释“太阳能加热水 → 水蒸气上升”
2. **从树木指向云朵的向上箭头**，标注“TRANSPIRATION（蒸腾）”，附注释“水从植物叶片释放”
3. **云朵本身**，标注“CONDENSATION（凝结）”，附注释“水蒸气冷却 → 形成水滴”
4. **从云朵指向陆地和水面的向下箭头**，标注“PRECIPITATION（降水）”，附注释“雨、雪、雨夹雪、冰雹”
5. **沿地面 → 河流 → 返回海洋的箭头**，标注“SURFACE RUNOFF / COLLECTION（地表径流/汇集）”
6. **向下进入地下的虚线箭头**，标注“INFILTRATION / GROUNDWATER FLOW（下渗/地下水流）”

**颜色编码（传递意义，而非装饰）：**
- 蓝色：所有液态水（海洋、河流、地下水、雨）
- 白色/浅色：水蒸气与云（展示物态变化）
- 黄色：角落里的小太阳符号，带一个指向蒸发箭头的箭头，标注“能量来源”
- 箭头：蓝色表示液态水移动，白色/灰色表示水蒸气移动

### 空间布局

```
    [SUN]─energy──→
                        ╭─── CLOUD ───╮
                       ╱  condensation  ╲
          evaporation ↑                  ↓ precipitation
         transpiration↑                  ↓
    ~~SEA~~  ↑  [TREE]  ___mountain___  rain↓  ──RIVER──→ (back to sea)
    ~~~~~~~  ↑                              ↓     ↗
    ~~~~~~~  ↑              surface runoff →→→→→→→
                         ↓ infiltration
                    ···groundwater flow →→→→→→→→→→→→→
```

### 注释策略
- **图表上：** 仅保留过程标签——每个箭头只写一个词（蒸发、蒸腾、凝结、降水、径流、下渗），外加 3–5 个词解释机制的简短注释。保持文字精简——让空间关系发挥作用。
- **口头（教师讲解）：** “注意向上的箭头由太阳能驱动——太阳加热水，水以水蒸气形式上升。向下的箭头由重力驱动——水以降水形式落下并向低处流动。整个循环由两种力量驱动：太阳把水拉上去，重力把水拉下来。”这段解释留在言语通道中，与视觉形成互补。**不要**写在黑板上。
- **图表上切勿包含：** 长段解释性文字、温度数据、百分比数字、术语定义。这些属于言语通道或独立文本资料，放在图表上会造成冗余和分散注意。

### 整合说明
**逐步构建视觉图，而非一次性全盘呈现。** 这对于管理新手学习者的认知负荷至关重要：

1. 首先，只画地形（海洋、陆地、树、山、河流），不加任何标签。提问：“你们看到了什么？水可能出现在这幅图的哪些地方？”
2. 添加蒸发箭头和标签。讲解：“太阳能加热水面。水分子获得能量，以水蒸气形式逸入空气中。”留时间让学生消化这一步。
3. 添加蒸腾箭头。提问：“水也会从植物中上升。树从哪里获取水分？水又是如何进入空气的？”（精致化询问——可与技能6联动。）
4. 添加云朵和凝结标签。讲解冷却过程。
5. 添加降水箭头。提问：“水为什么会落下来？是什么力量把它往下拉？”（重力——连接先前的科学知识。）
6. 添加径流和下渗箭头，完成循环。
7. 只有在完整图表构建完毕后，才用手势完整追踪一遍循环：“跟着水走。它从这里开始……上升……形成云……落下……流回来……循环继续。”

**总构建时间：** 3分钟（逐步构建）或 1分钟（提前画好）。

### 常见误区

1. **添加装饰性细节以使其“好看”。** 海里的鱼、天上的鸟、地上的花——这些都是诱人细节（Harp & Mayer, 1998），会在无助于理解的情况下消耗视觉加工容量。每个元素都应代表水循环过程中的功能性组成部分。如果它不是循环的一部分，就不该出现在黑板上。

2. **将标签与图表分离。** 一种常见的学习单设计是将图表放在中央，四周放一个编号图例。这会迫使分散注意——学生必须在追踪空间关系的同时将数字与定义匹配。应将所有标签直接整合到图表上的对应位置。

3. **将其与“作为视觉型学习者”相混淆。** 如果有学生或同事说“这对视觉型学习者太棒了”，请纠正这一误解。双重编码之所以有益于所有学习者，是因为两种互补的表征比单一表征创造了更多的提取路径，与所谓偏好的学习风格无关（Pashler et al., 2008）。明确说明这一点有助于消除教育界最顽固的迷思之一。

---

## 已知局限

1. **本技能负责设计视觉表征，但无法直接生成图像文件。** 输出是一份详细规格说明（图表类型、布局、元素、颜色编码），而非图片文件。教师必须自行绘制或制作该视觉图——在白板上、PowerPoint 中，或使用 Canva、draw.io 等工具。规格已足够详尽以便参照，但教师的绘图技巧与工具熟练度各有差异。

2. **部分概念本质上难以视觉化表征。** 抽象概念（正义、反讽、概率）以及复杂的多变量关系很难用简单视觉方式呈现。本技能会推荐当前最佳方案，但对于高度抽象的内容，视觉图在言语解释之外能增加的价值可能有限。这并非双重编码的失败，而是反映了视觉表征的真实边界。

3. **双重编码的效果取决于整合，而非仅仅“存在”。** 仅仅在文字旁边放一张图并不会自动产生双重编码收益。教师必须主动整合双通道——边指边讲、边解释边逐步构建图表、请学生将视觉元素与口头描述联系起来。缺乏整合的精良视觉图，不过是幻灯片上的一张图片而已。
