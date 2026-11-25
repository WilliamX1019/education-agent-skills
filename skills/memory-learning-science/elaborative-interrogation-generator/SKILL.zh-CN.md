---
# AGENT SKILLS STANDARD FIELDS (v2)
name: elaborative-interrogation-generator
description: "生成精致化询问提示，通过有针对性的“为什么”和“如何”问题深化记忆编码。适用于学生死记硬背而不理解或需要对内容进行深层加工时。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "memory-learning-science/elaborative-interrogation-generator"
skill_name: "精致化询问提示生成器"
domain: "memory-learning-science"
version: "1.0"
evidence_strength: "strong"
evidence_sources:
  - "Pressley et al. (1992) — Elaborative interrogation facilitates acquisition of confusing facts"
  - "Woloshyn et al. (1994) — Use of elaborative interrogation to help students acquire information consistent with prior knowledge"
  - "Dunlosky et al. (2013) — Elaborative interrogation rated moderate-utility learning strategy"
  - "McDaniel & Donnelly (1996) — Learning with analogy and elaborative interrogation"
  - "Ozgungor & Guthrie (2004) — Interactions among elaborative interrogation, knowledge, and interest in the process of constructing knowledge from text"
input_schema:
  required:
    - field: "topic"
      type: "string"
      description: "学生正在学习的概念、事实集合或内容领域"
    - field: "student_level"
      type: "string"
      description: "年龄/年级及大致先验知识水平"
    - field: "prompt_count"
      type: "integer"
      description: "需生成的精致化提示数量（建议 5–8 条）"
  optional:
    - field: "content_text"
      type: "string"
      description: "学生正在研习的具体文本或内容"
    - field: "prior_knowledge"
      type: "string"
      description: "学生已掌握且可与本主题相连接的内容"
    - field: "student_profiles"
      type: "array"
      description: "来自上下文引擎：语言水平、先验知识数据"
    - field: "learning_objectives"
      type: "string"
      description: "提示应支持的具体学习目标"
output_schema:
  type: "object"
  fields:
    - field: "elaborative_prompts"
      type: "array"
      description: "有序的“为什么/如何”提示列表，附目标知识与预期深度"
    - field: "implementation_guide"
      type: "string"
      description: "如何使用这些提示——时机、分组、书面或口头形式"
    - field: "connection_prompts"
      type: "array"
      description: "将新知识与先验知识连接起来的提示"
chains_well_with:
  - "retrieval-practice-generator"
  - "self-regulation-scaffold-generator"
  - "metacognitive-prompt-library"
  - "reading-comprehension-strategy-selector"
teacher_time: "3 分钟"
tags: ["elaboration", "encoding", "comprehension", "deep-processing", "questioning"]
---

# 精致化询问提示生成器

## 本技能的功能

生成一组“为什么？”和“这与已知内容有何联系？”的提示，旨在通过迫使学生生成将新信息与已有知识相连接的解释来深化记忆编码。与理解检查题（仅核对是否读懂）不同，精致化询问提示要求学生解释**为什么**某个事实成立或它**如何**与他们已知的内容相关联——生成解释这一行为本身就会强化记忆痕迹。AI 在此处具有独特价值，因为有效的精致化提示必须精准定位于学生正在学习的内容与已有知识之间的交汇点——脱离先验知识太远则学生无法生成解释；过于显而易见则无需精致化加工。

## 循证基础

Pressley 等人（1992）证明，针对事实性信息回答“为什么？”问题所产生的保持效果显著优于单纯阅读相同事实，效应量约为 0.59。其机制在于精致化编码——生成解释会为信息创造额外的提取路径。Woloshyn 等人（1994）表明，当学生具备足够的先验知识以生成合理解释时，精致化询问最为有效——该策略需要有现有图式可供连接。Dunlosky 等人（2013）将精致化询问评定为“中等效用”学习策略，指出其在事实性学习方面证据充分，但在复杂概念学习方面的有效性尚不完全明确。McDaniel 与 Donnelly（1996）证明，将精致化询问与类比推理相结合，比单独使用任一策略都能产生更强的编码效果。Ozgungor 与 Guthrie（2004）发现，精致化询问的有效性与先验知识和兴趣存在交互作用——具备一定相关知识的学生获益最大，而知识极少者可能在生成解释时遇到困难。

## 输入模式

教师必须提供：
- **主题：** 学生正在学习的概念或内容。*例如：“金属与非金属的性质” / “法国大革命的起因” / “十四行诗的结构”*
- **学生水平：** 年级与先验知识。*例如：“九年级化学，中等能力，已学过原子结构”*
- **提示数量：** 所需提示数量。*例如：6*

可选（如有，由上下文引擎注入）：
- **内容文本：** 学生正在研习的具体文本、段落或资源
- **先验知识：** 学生已具备的相关先验知识（可提高提示校准度）
- **学生档案：** 语言水平及个体先验知识数据
- **学习目标：** 提示应支持的具体目标

## 提示词

```
You are an expert in the cognitive psychology of encoding and memory, specialising in elaborative processing. You have deep knowledge of Pressley et al.'s (1992) research on elaborative interrogation, Woloshyn et al.'s (1994) work on elaboration and prior knowledge, and McDaniel & Donnelly's (1996) research on elaboration and analogy.

Your task is to generate {{prompt_count}} elaborative interrogation prompts for students learning about "{{topic}}" at the {{student_level}} level.

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Specific content:** {{content_text}} — if provided, generate prompts that target the key claims and relationships in this text. If not provided, generate prompts based on general subject knowledge of the topic.
**Student prior knowledge:** {{prior_knowledge}} — if provided, calibrate prompts to connect new learning to this existing knowledge. If not provided, assume standard prior knowledge for the stated year group and subject.
**Learning objectives:** {{learning_objectives}} — if provided, focus prompts on the most important learning targets. If not provided, target the core causal relationships and mechanisms within the topic.
**Student profiles:** {{student_profiles}} — if provided, adjust language complexity and provide differentiated versions where appropriate. If not provided, design for a typical mixed-ability class.

Apply these evidence-based principles:

1. **"Why?" is the core prompt type.** The primary mechanism of elaborative interrogation is generating explanations for why facts or relationships are true. Every prompt should begin with or be reducible to a "why?" question. "What?" and "how?" are useful secondary types but only when they force explanation, not recall.

2. **Target causal relationships, not isolated facts.** Elaborative prompts should target the relationships between concepts, causes and effects, and mechanisms — not definitions or labels. "Why do metals conduct electricity?" forces elaboration. "What is a metal?" forces recall. Both are useful but only the first is elaborative interrogation.

3. **Calibrate to prior knowledge (Woloshyn et al., 1994).** Prompts only work if students have enough prior knowledge to generate a plausible explanation. If students know nothing about a topic, they can't elaborate — they need direct instruction first. Calibrate each prompt to connect to something students already know.

4. **Include connection prompts (McDaniel & Donnelly, 1996).** Some prompts should explicitly ask students to connect new information to analogous concepts they've already learned. "How is this similar to...?" or "Why might this work in the same way as...?"

5. **Vary the prompt type.** Include a mix of:
   - **Causal why:** "Why does X happen?"
   - **Contrastive why:** "Why does X happen but not Y?"
   - **Mechanism how:** "How does X lead to Y?"
   - **Connection:** "How is X similar to Y, which you learned about in [previous topic]?"
   - **Predictive:** "Based on what you know about X, what would you predict about Z? Why?"

6. **Avoid disguised recall questions.** A prompt that has a single correct factual answer is a recall question, not an elaborative prompt. Elaborative prompts should have multiple plausible explanations that students can generate from their existing knowledge.

Return your output in this exact format:

## Elaborative Interrogation Prompts: [Topic]

**For:** [Student level]
**Prior knowledge assumed:** [What students need to know for these prompts to work]

### Prompts

For each prompt:
- The prompt text
- **Type:** [Causal why / Contrastive why / Mechanism how / Connection / Predictive]
- **Targets:** [What knowledge or relationship this prompt deepens]
- **Prior knowledge activated:** [What existing knowledge students draw on to answer]

### Connection Prompts

2–3 prompts specifically connecting this topic to previously learned material.

### Implementation Guide

- When to use (during reading, after instruction, as homework)
- How to structure (individual written → pair discussion → class share)
- Time needed
- What to do if students can't generate explanations (prior knowledge is insufficient)

**Self-check before returning output:** Verify that (a) every prompt requires explanation, not just recall, (b) prompts are calibrated to the stated prior knowledge level — students can plausibly generate answers, (c) no prompt has a single-word or single-fact answer, and (d) the prompts target relationships and mechanisms, not definitions.
```

## 示例输出

**场景：** *主题：“沙漠动物的适应性” / 学生水平：“八年级生物，已学过基本细胞结构与栖息地/生态系统” / 提示数量：6*

---

## 精致化询问提示：沙漠动物的适应性

**适用对象：** 八年级生物
**预设先验知识：** 学生理解细胞需要水才能发挥功能，知道什么是栖息地，理解生物体受环境影响，并接触过食物链概念。他们**尚未**详细学习演化或自然选择。

### 提示列表

**1.** 与体型相比，耳廓狐的耳朵非常大，而北极狐的耳朵则很小。为什么耳朵大小会与在炎热沙漠还是寒冷苔原中生存有关？

- **类型：** 对比型“为什么”
- **目标：** 表面积与体积比作为体温调节的机制；身体特征与环境压力之间的联系
- **激活的先验知识：** 学生知道炎热和寒冷环境的存在；即使尚未正式学过表面积体积比，也能推理出大耳朵 = 更多皮肤表面 = 更多热量散失

**2.** 许多沙漠动物是夜行性的——夜晚活动、白天睡觉。尽管在黑暗中更难觅食，为什么夜间活动能帮助动物在沙漠中生存？

- **类型：** 因果型“为什么”
- **目标：** 作为节能/保水策略的行为适应；权衡推理（接受一项劣势以换取更大的优势）
- **激活的先验知识：** 学生知道沙漠白天炎热、夜晚凉爽；理解动物需要水和能量

**3.** 骆驼可以几周不喝水存活，但如果不吃食物却无法撑那么久。结合你对细胞的了解，为什么在沙漠中水比食物是更大的生存挑战？

- **类型：** 机制型“如何”（为何水比食物对生存更关键）
- **目标：** 将细胞生物学（细胞需要水进行化学反应、运输和维持结构）与生物体层面的适应性相连接；建立“适应性解决特定环境问题”的理解
- **激活的先验知识：** 细胞结构——学生学过细胞主要由水构成，细胞内的化学反应需要水

**4.** 澳洲棘蜥皮肤上布满带刺的微小沟槽，能将雨水引导至口中。如果你要设计一种在干燥环境中收集水分的方案，你会运用什么原理？为什么棘蜥的方案如此有效？

- **类型：** 预测型 + 机制型“如何”
- **目标：** 结构-功能关系；物理特征可通过被动机制（毛细作用、表面张力）解决环境问题的理念
- **激活的先验知识：** 学生对水行为的日常知识；连接科学或设计技术课上学过的材料/表面知识

**5.** 像仙人掌这样的沙漠植物将水储存在厚实的茎中，但你在英国见到的大多数植物根本没有厚茎。为什么英国植物不需要储存水分？如果英国植物也长出像仙人掌那样厚实多肉的茎，为什么反而会成为劣势？

- **类型：** 对比型“为什么”
- **目标：** 适应性具有环境特异性——在一种环境中有利的特征在另一种环境中可能不利；理解适应性是有代价的（厚茎消耗能量、沉重且容易吸引食草动物）
- **激活的先验知识：** 学生对英国气候（降雨频繁）的知识及对本地植物的日常经验

**6.** 索诺兰沙漠的更格卢鼠从不喝水——它们全部的水分都来自所吃的干燥种子。怎么可能从干燥的种子中获取水分？想一想消化和化学反应过程中会发生什么。

- **类型：** 机制型“如何”
- **目标：** 代谢水的产生；将化学（化学反应产生水作为副产物）与生物（消化作为化学过程）相连接；深层加工“适应性不仅限于行为或结构，也包括代谢层面”这一认识
- **激活的先验知识：** 学生学过基础化学反应，知道消化会分解食物；可能知道呼吸作用会产生水

### 连接提示

**C1.** 上学期学习生态系统时，你们学过食物链展示栖息地中的能量流动。沙漠食物链往往比热带雨林食物链更短。为什么沙漠食物链中的“环节”可能更少？这与你所知的能量和资源稀缺有何联系？

**C2.** 我们学习细胞时，学过水通过渗透作用穿过细胞膜。流失过多水分的沙漠动物在细胞层面面临严重问题。运用你对渗透作用的了解，解释如果动物严重脱水，其细胞会发生什么变化？为什么这使得保水在字面意义上成为生死攸关的问题？

### 实施指南

- **使用时机：** 在完成沙漠适应性的初步教学之后（而非之前——学生需要新内容作为精致化的对象）。非常适合作为课程后半段的 15 分钟活动，或作为结构化家庭作业。
- **组织形式：** 先个人书面作答（每条提示约 5 分钟——为每位学生分配 3 条提示，而非全部 6 条）。接着同伴讨论：与同伴对比答案。最后就其中一条提示进行全班分享，重点关注学生生成的多种合理解释。
- **所需时间：** 3 条提示需 15–20 分钟（个人作答 + 同伴讨论）。切勿匆忙——学习发生在生成解释的过程中，这需要时间。
- **若学生无法生成解释：** 这表明先验知识不足。对于提示 3（细胞与水），学生可能需要简要回顾细胞结构。对于提示 6（代谢水），属于拔高挑战——若学生答不出，可改为教师引导的全班讨论，而非个人写作。不要立刻给出答案——只要挣扎是富有成效而非完全不可能的，努力生成解释的过程正是学习发生的地方。
- **重要提示：** 接纳多种合理解释。这些是精致化提示，而非只有单一标准答案的测验题。即使“课本答案”侧重于隔热与保水，一个将夜行行为解释为“躲避白天捕食者”的学生同样在进行有效的精致化加工。

---

## 已知局限

1. **精致化询问需要足够的先验知识来生成解释。** 如果学生没有相关先验知识（例如毫无科学背景的七年级学生尝试回答关于代谢水的提示 6），他们将无法进行精致化加工，提示也会从富有成效变成令人沮丧。Ozgungor 与 Guthrie（2004）发现精致化与先验知识之间的这种交互作用非常显著。教师必须核实“预设先验知识”部分是否与学生真实水平相符。

2. **实证基础在事实性/概念性学习方面最为坚实，而非程序性技能。** Pressley 等人（1992）及大多数精致化询问研究均使用事实性材料。该策略迁移到数学运算步骤、体能技能或创意任务的效果尚不明确，在这些任务中“为什么？”问题未必能以同样方式深化编码。

3. **精致化询问比重复阅读更有效，但不如提取练习有效。** Dunlosky 等人（2013）将其评为“中等效用”而非“高效用”。它最适合作为提取练习和间隔练习的补充，而非替代品。可在初始编码阶段使用精致化提示，随后转为提取练习以巩固记忆。
