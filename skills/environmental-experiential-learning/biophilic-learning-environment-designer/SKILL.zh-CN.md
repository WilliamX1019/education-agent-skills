---
# AGENT SKILLS STANDARD FIELDS (v2)
name: biophilic-learning-environment-designer
description: "运用亲自然设计（biophilic design）原则重新设计学习空间，以提升专注力、平静感与身心健康。适用于教室环境导致焦躁、注意力不集中或压力过大时。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "environmental-experiential-learning/biophilic-learning-environment-designer"
skill_name: "亲自然学习环境设计师"
domain: "environmental-experiential-learning"
version: "1.0"
evidence_strength: "emerging"
evidence_sources:
  - "Kellert (2005) — Building for Life: designing and understanding the human-nature connection"
  - "Kellert, Heerwagen & Mador (2008) — Biophilic Design: the theory, science, and practice of bringing buildings to life"
  - "Kaplan & Kaplan (1989) — The Experience of Nature: a psychological perspective (Attention Restoration Theory)"
  - "Wells (2000) — At home with nature: effects of 'greenness' on children's cognitive functioning"
  - "Browning, Ryan & Clancy (2014) — 14 Patterns of Biophilic Design: improving health and well-being in the built environment"
input_schema:
  required:
    - field: "current_space"
      type: "string"
      description: "当前学习空间的描述——大小、布局、窗户、照明、表面材质、现有自然元素"
    - field: "design_goal"
      type: "string"
      description: "教师希望实现的目标——更好的专注力、更平静的氛围、更高的参与度、减轻压力"
  optional:
    - field: "student_level"
      type: "string"
      description: "使用该空间的年龄组"
    - field: "budget_level"
      type: "string"
      description: "可用预算——零成本、低成本（100 英镑以内）、中等（500 英镑以内）或可投入资金"
    - field: "space_constraints"
      type: "string"
      description: "限制条件——不允许摆放活体植物、墙面空间有限、共用教室、房东限制"
    - field: "existing_nature_access"
      type: "string"
      description: "当前接触自然的机会——窗外视野、与户外空间的距离"
    - field: "sensory_needs"
      type: "string"
      description: "学生是否有特定的感官需求——例如自闭症谱系、感官处理差异"
output_schema:
  type: "object"
  fields:
    - field: "biophilic_design"
      type: "object"
      description: "完整的设计方案——对空间的具体改造，按亲自然设计模式组织"
    - field: "priority_changes"
      type: "array"
      description: "按证据强度、成本和实施难易度排序的 3–5 项最具影响力的改造"
    - field: "implementation_plan"
      type: "object"
      description: "如何实施这些改造——预算受限时分阶段推进，条件允许时立即实施"
    - field: "evidence_rationale"
      type: "object"
      description: "每项改造为何重要——将具体设计元素与研究证据联系起来"
chains_well_with:
  - "outdoor-learning-sequence-designer"
  - "flow-state-condition-designer"
  - "belonging-classroom-culture-designer"
  - "ecological-inquiry-anchor-designer"
teacher_time: "3 分钟"
tags: ["biophilic-design", "Kellert", "Kaplan", "attention-restoration", "classroom-environment", "nature", "wellbeing"]
---

# 亲自然学习环境设计师

## 本技能的作用

重新设计教室或学习空间以融入亲自然设计（biophilic design）元素——即基于“人类与自然环境的接触能够改善认知功能、降低压力水平并提升注意力”的证据，将使用者与自然及自然过程联系起来的要素。该方法借鉴了 Kellert (2005, 2008) 的亲自然设计框架与 Kaplan & Kaplan (1989) 的注意力恢复理论（Attention Restoration Theory）。核心洞察在于：大多数教室都是“亲自然荒漠”——封闭、人工的环境，充斥着荧光灯、单一的表面材质、没有生命体，也缺乏感官多样性——而哪怕是很小的改变（植物、自然光、自然视野、天然材料、水声），都能显著提升注意力、减轻压力并提高参与度。输出包括按亲自然设计模式组织的具体空间改造方案、按影响力和成本排序的优先建议、实施计划，以及每项改造的循证依据。AI 在此尤为有价值，因为将亲自然设计原则转化为切实可行的教室改造，需要同时权衡证据基础、空间物理限制、预算以及学生的具体需求——这是一个适合通过系统性模式匹配来解决的设计挑战。

## 循证基础

Kellert (2005) 将亲自然性（biophilia）定义为“人类与自然系统和过程建立联系的内在倾向”，并指出旨在满足这一倾向的建筑能够为使用者带来更好的认知、情感和身体健康结果。Kellert, Heerwagen & Mador (2008) 构建了一套全面的亲自然设计框架，识别出六大要素：环境特征（植物、水、自然光）、自然形状与形态（植物纹样、曲线）、自然模式与过程（感官变化、生长、老化）、光与空间（自然光、空间变化）、基于场所的关系（与当地生态和文化的联系）以及演化而来的人与自然关系（远眺与庇护、神秘感、风险/刺激）。Kaplan & Kaplan (1989) 提出了注意力恢复理论（ART），认为定向注意力（完成学术工作所需的费力专注）是一种会消耗的资源，而接触自然能够使其恢复。自然环境具有“柔和的吸引力（softly fascinating）”——它们在不要求费力的情况下吸引注意力，从而让定向注意力得以恢复。这对教室具有直接启示：处于与自然相连空间中的学生，应当比处于缺乏自然元素的空间中的学生展现出更好的持续注意力。Wells (2000) 发现，搬入“绿化度”（自然视野、植被、自然元素）更高住宅的儿童，即使在控制其他变量后，认知功能也出现了显著提升。Browning, Ryan & Clancy (2014) 将相关证据综合为 14 种实用的亲自然设计模式，为将亲自然原则应用于特定空间提供了最具可操作性的框架。

## 输入模式

教师必须提供：
- **Current space（当前空间）：** 房间现在的样子。*例如："Standard classroom — 30 desks in rows, fluorescent strip lighting, two windows facing the car park, cream walls, vinyl floor, one whiteboard, one display board. No plants. Blinds usually closed because of screen glare." / "Open-plan learning area — flexible seating, some natural light from skylights, carpet, display walls, no windows at student eye-level. Currently quite cluttered."*
- **Design goal（设计目标）：** 他们希望改善什么。*例如："Students struggle to focus after lunch — energy is scattered and attention is poor" / "The room feels sterile and institutional — I want it to feel calmer and more inviting" / "I want to create a calming corner for students who need sensory regulation"*

可选（如上下文引擎可用则自动注入）：
- **Student level（学生水平）：** 年龄组
- **Budget level（预算水平）：** 可用资源
- **Space constraints（空间限制）：** 限制条件
- **Existing nature access（现有自然接触）：** 当前的自然连接
- **Sensory needs（感官需求）：** 学生感官特征

## Prompt

```
You are an expert in biophilic design for learning environments, with deep knowledge of Kellert's (2005, 2008) biophilic design framework, Kaplan & Kaplan's (1989) Attention Restoration Theory, Wells' (2000) research on nature and cognitive functioning, and Browning, Ryan & Clancy's (2014) 14 Patterns of Biophilic Design. You understand that biophilic design is not interior decoration — it is evidence-informed environmental design that connects occupants to nature and natural processes to improve cognitive functioning, emotional regulation, and wellbeing.

CRITICAL PRINCIPLES:
- **Start with what's already there.** Most classrooms have SOME connection to nature — a window, natural light, a view of trees. Identify and amplify existing connections before adding new ones. Opening blinds costs nothing. Rearranging desks so students face a window costs nothing. These are often the highest-impact, lowest-cost changes.
- **Nature connection is multi-sensory.** Biophilic design is not just visual (plants and pictures). It includes auditory (water sounds, birdsong), olfactory (natural scents), tactile (natural materials — wood, stone, fabric), and even thermal (temperature variation, air movement). The most effective biophilic spaces engage multiple senses.
- **Prioritise by evidence strength.** Natural light has the strongest evidence base. Plants and nature views have moderate evidence. Natural materials, sounds, and patterns have emerging evidence. Recommend changes in order of evidence strength, not aesthetic preference.
- **Be realistic about constraints.** Many schools prohibit live plants (allergy policies, maintenance concerns), have sealed windows, use fluorescent lighting, and have zero budget. The design must work WITHIN these constraints — not wish them away. There is always something that can be done, even with zero budget.
- **Attention restoration, not distraction.** Biophilic elements should be "softly fascinating" (Kaplan & Kaplan) — present in the peripheral visual field, gently engaging the senses, not demanding attention. A fish tank in the middle of the room may be more distracting than restorative. A plant on the windowsill, visible but not dominant, is restorative.

Your task is to design a biophilic learning environment for:

**Current space:** {{current_space}}
**Design goal:** {{design_goal}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Student level:** {{student_level}} — if not provided, design for a general classroom context.
**Budget level:** {{budget_level}} — if not provided, design a phased plan starting with zero-cost changes.
**Space constraints:** {{space_constraints}} — if not provided, identify common constraints and design around them.
**Existing nature access:** {{existing_nature_access}} — if not provided, assess from the space description.
**Sensory needs:** {{sensory_needs}} — if not provided, include a note about sensory sensitivity.

Return your output in this exact format:

## Biophilic Learning Environment: [Design Goal]

**Current space:** [Summary]
**Design goal:** [What to improve]
**Key biophilic principle:** [The main Attention Restoration Theory or biophilic design principle this redesign activates]

### Assessment of Current Space

[What biophilic elements are already present (if any) and what's missing — identifying the biggest gaps]

### Priority Changes (Ranked by Impact)

For each change (3–5):
**Priority [N]: [Change]**
- **What to do:** [Specific, practical action]
- **Biophilic pattern:** [Which of Browning et al.'s 14 patterns this addresses]
- **Evidence:** [Why this matters — link to research]
- **Cost:** [Zero / Low / Moderate / Investment needed]
- **Implementation:** [How to do it — practical steps]

### Sensory Design Map

[How the redesigned space engages multiple senses — visual, auditory, tactile, olfactory — through natural elements]

### Implementation Plan

**Phase 1 — Immediate (zero cost):** [Changes that can be made today]
**Phase 2 — Low cost (under £50):** [Changes that need a small budget]
**Phase 3 — Investment (when budget allows):** [Changes that need more significant resources]

### Considerations for Specific Needs

[How to adapt the design for students with sensory sensitivities, allergies, or other needs]

**Self-check before returning output:** Verify that (a) changes are prioritised by evidence strength, (b) the design is realistic given the described constraints, (c) the plan starts with zero-cost changes, (d) multiple senses are addressed, and (e) the biophilic elements are restorative, not distracting.
```

## 示例输出

**场景：** *Current space: "Year 5 classroom — standard rectangular room, 30 desks in rows facing the whiteboard. Two large windows on the left wall facing east — good morning light but blinds are usually closed because of interactive whiteboard glare. Fluorescent strip lighting. Cream walls. Vinyl flooring. One display board covered with student work (laminated, very colourful). No plants. No natural materials. The room feels blank and institutional. The only colour is the display board, which is visually busy." / Design goal: "Students struggle with sustained attention, especially after lunch. The room feels sterile. I want a calmer, more focused environment that helps students concentrate." / Budget level: "Very low — maybe £30 from my own money. Could apply for a small school improvement grant (up to £200) if I make a case." / Sensory needs: "Two students are on the autism spectrum and are sensitive to bright lights and visual clutter."*

---

## 亲自然学习环境：恢复五年级学生的注意力

**当前空间：** 标准五年级教室——课桌成排、荧光灯、百叶窗拉上、无自然元素、除了一块杂乱的展示板外视觉上显得单调冰冷
**设计目标：** 提升持续注意力，营造更平静、更专注的氛围
**核心亲自然原则：** 注意力恢复理论（Kaplan & Kaplan, 1989）——定向注意力会因持续的认知努力而消耗，并通过接触自然环境得以恢复。这间教室目前提供的恢复性元素为零。

### 当前空间评估

**现有亲自然元素：** 左侧墙上有两扇朝东的大窗，上午采光良好——这是该空间最大的优势，但目前因百叶窗拉上而被浪费。窗户可能还能看到树木、天空或绿地——值得确认。

**缺失元素：** 自然光无法照进教室（百叶窗关闭）。没有生命体。没有天然材料（乙烯基地板、塑料、塑封膜占主导）。没有感官变化（单一照明、单一色彩、单一温度）。展示板虽然提供了视觉刺激，但处于“视觉杂乱”状态，而非柔和吸引——它在索取注意力，而不是恢复注意力。两名自闭症谱系学生很可能尤其受到荧光灯和视觉杂乱的影响。

### 优先改造（按影响力排序）

**优先级 1：拉开百叶窗并管理眩光**
- **具体做法：** 拉开百叶窗。调整交互式白板的位置或屏幕亮度，使其在不遮挡全部自然光的情况下清晰可见。如果完全拉开百叶窗仍会产生过多眩光，可将百叶窗半开（下半部分打开、上半部分闭合），或用柔光帘、磨砂膜替代遮光百叶窗。
- **亲自然模式：** 与自然的视觉连接（模式 1 —— Browning 等）
- **循证依据：** 自然日光是证据最强的单一亲自然干预措施。Wells (2000) 发现，包括自然光在内的“绿化度”提高能够带来认知改善。Heschong Mahone Group (1999) 发现，日光最充足教室里的学生在数学上进步快 20%，在阅读上进步快 26%，优于日光最少的教室。即使控制其他因素，日光也能持续改善注意力、情绪和学业表现。
- **成本：** 零
- **实施步骤：** 明早即可开始。查看窗外视野（是否能看到天空、树木或绿地？）。如果可以，这将立刻成为教室里最有力的自然连接。如有需要，重新调整学生课桌朝向，使白板不直接正对窗户。

**优先级 2：减少视觉杂乱，营造视觉平静感**
- **具体做法：** 将展示板的覆盖面积从 100% 减少到 60%。撤掉会产生反光的塑封膜。使用柔和、自然色调的衬底纸（牛皮纸、粗麻布）替代鲜艳的彩色卡纸。刻意保留一部分空白墙面——作为视觉休息区。这对两名自闭症谱系学生尤为重要。
- **亲自然模式：** 与自然的非视觉连接（模式 2）及复杂性与秩序（模式 10）——大脑在有组织、自然的规律中寻找平静，而非在视觉混乱中
- **循证依据：** Barrett, Zhang, Moffat & Kobbacy (2013) 发现，教室的“个性化程度”（色彩、展示、视觉刺激）存在一个最佳水平——过多的视觉刺激与过少一样具有负面影响。拥有适度、有序视觉环境的教室，比墙面光秃秃或视觉过载的教室能产出更好的学习结果。
- **成本：** 接近零（牛皮纸或粗麻布成本约 5–10 英镑）
- **实施步骤：** 本周内完成。撤除 40% 的展示内容。用自然色调替换鲜艳衬底。开辟一面“安静墙”——刻意留白，或只张贴一幅自然图像。

**优先级 3：引入生命体**
- **具体做法：** 增加 3–5 盆低维护成本的室内植物。将它们放在窗台上（现在百叶窗已经打开）、学生课桌视野可及的架子上，以及阅读角（如果有）。最适合教室的品种：绿萝（pothos，几乎养不死、垂吊美观）、吊兰（spider plant，净化空气、会长出小株可供学生照料）、白鹤芋（peace lily，耐弱光）或多肉植物（需水量极少）。
- **亲自然模式：** 与自然的视觉连接（模式 1）及水/生命的存在（模式 4 —— 生命体）
- **循证依据：** Lohr, Pearson-Mims & Goodwin (1996) 发现，房间内有植物能提升任务表现并减轻压力。Fjeld (2000) 发现室内植物能减少疲劳和头痛。其机制可能是多路径的：视觉柔化、改善空气质量，以及生命体所具有的不费力即可恢复注意力的“柔和吸引力”。
- **成本：** 在园艺中心或超市购买 3–5 盆植物约 15–25 英镑
- **实施步骤：** 本周内完成。如果学校政策限制活体植物（过敏问题），可使用密封生态瓶（玻璃罐内种植苔藓和蕨类——不会释放过敏原）。如果连这也受限，可在学生视线高度张贴高质量的自然摄影照片——这是退而求其次的选择，但仍然有益。

**优先级 4：在触觉环境中增添天然材料**
- **具体做法：** 用天然物品替换一件合成物品。可选方案：用木箱存放书籍（替代塑料箱）、在坐区铺一块粗麻垫、在每个小组桌上放一块光滑的石头或木制物品（学生讨论时可握在手中的“思考石”）、为阅读角靠垫套换上天然织物（棉、亚麻）。
- **亲自然模式：** 与自然的非视觉连接（模式 2）——触觉在亲自然设计中常被低估
- **循证依据：** 新兴研究表明，触摸天然材料（木材、石头、天然纤维）比触摸合成材料能激活不同的神经通路，并可能有助于减压。Sakuragawa, Miyazaki, Kaneko & Makita (2005) 发现触摸木材能产生平静的生理反应。对于两名自闭症谱系学生而言，光滑的石头或木制物品提供了一种社会可接受的感官调节工具。
- **成本：** 5–15 英镑（二手慈善商店是寻找木箱、天然织物和石头的好去处）
- **实施步骤：** 未来两周内逐步收集天然材料。让学生参与进来："Can you bring in a smooth stone from home?"

**优先级 5：引入自然声音**
- **具体做法：** 在安静作业时间，通过教室音响以低音量播放自然声景（鸟鸣、雨声、溪流声）。音量应“几乎难以察觉”——作为背景，而非前景。
- **亲自然模式：** 与自然的听觉连接（归属于模式 2）
- **循证依据：** Kaplan & Kaplan 的注意力恢复理论指出，自然声音具有“柔和的吸引力”——它们轻柔地占据听觉注意力，掩盖令人分心的人工噪音（走廊声、施工声、交通声），而不会消耗费力的注意力。Ratcliffe, Gatersleben & Sowden (2013) 发现鸟鸣尤其被认为具有恢复作用。注意：部分学生（包括听觉敏感的学生）可能会觉得“任何”背景声音都让人分心。可提供降噪耳机作为替代方案。
- **成本：** 零（免费的自然声景应用/YouTube）
- **实施步骤：** 本周尝试。先在一次独立写作时间试播 5 分钟。观察学生反应。如果效果积极，可适当延长。如果自闭症学生觉得不适，立即停止或为他们提供降噪耳机。

### 感官设计图谱

| 感官 | 当前状态 | 拟议改造 | 元素 |
|---|---|---|---|
| 视觉 | 荧光灯、百叶窗关闭、无自然元素、展示杂乱 | 自然日光、减少杂乱、可见植物、墙面采用自然色调 | 日光、植物、精简展示 |
| 听觉 | 荧光灯嗡嗡声、走廊噪音、无自然声音 | 安静作业期间可选的鸟鸣/雨声声景 | 自然声景（极低音量） |
| 触觉 | 乙烯基、塑料、塑封膜——全为合成材料 | 木制物品、光滑石头、阅读区天然织物 | 触手可及的天然材料 |
| 嗅觉 | 机构化气味——清洁剂、白板笔 | 来自植物（如有花期）或天然材料的淡淡自然气息 | 活体植物（淡雅，非浓香型） |

### 实施计划

**第 1 阶段——立即实施（零成本，本周）：**
- 拉开百叶窗（或半开以管理眩光）
- 如需要，重新摆放课桌以便看清白板
- 撤除 40% 的展示板内容
- 在一次安静作业时段试用自然声景

**第 2 阶段——低成本（30 英镑以内，未来两周）：**
- 购买 3–5 盆室内植物（15–25 英镑）
- 用牛皮纸或粗麻布替换鲜艳的展示板衬底（5–10 英镑）
- 收集天然触觉物品（石头、木制物品——免费或二手店购买）

**第 3 阶段——如获批资助（200 英镑以内）：**
- 将荧光灯管更换为日光光谱 LED 面板（单间教室 80–150 英镑，对光线质量提升显著）
- 开辟专门的“自然角”，放置生态瓶、天然材料收藏盒以及配有天然织物的舒适座椅
- 安装小型室内水景装置（桌面喷泉，20–40 英镑）——提供视觉与听觉的自然连接

### 特殊需求考量

**针对两名自闭症谱系学生：**
- 精简展示（优先级 2）将直接使他们受益——减少视觉过载
- 对感官敏感人群而言，自然日光通常比荧光灯更受欢迎——拉开百叶窗可能会显著改善他们的体验
- “思考石”（优先级 4）提供了一种社会可接受的感官调节工具——光滑、凉爽、天然
- 自然声景（优先级 5）：需谨慎测试。部分自闭症人士觉得鸟鸣令人平静，另一些人则可能对不可预测的自然声音感到烦躁。提供降噪耳机作为替代
- 所有改变都应“循序渐进”引入——环境骤变可能引发情绪失调。每周引入一项改变，不要一次性全部改动

---

## 已知局限性

1. **亲自然设计在教室中的证据尚处于新兴阶段，而非完全确立。** 最强有力的证据来自办公场所和医疗环境（Kellert, 2008; Browning et al., 2014），针对教室的具体研究仍然有限。Wells (2000) 和 Heschong Mahone Group (1999) 提供了与教育最相关的强有力证据，但对于具体的教室改造（植物、自然声音、天然材料），现有证据更多是提示性的而非决定性的。上述建议是对得到充分支持的原则进行的合理应用，而非直接经过大规模验证的干预措施。

2. **学校政策可能限制实施。** 一些学校禁止活体植物（出于过敏顾虑）、限制墙面展示格式、密封窗户或拥有不可更改的照明系统。分阶段方案对此有所应对，但教师可能会发现，影响力最大的改造（日光、植物）恰恰是学校限制最多的部分。

3. **亲自然设计是对优质教学的补充，而非替代。** 一间美观且与自然相连的教室，如果教学质量差，依然不会产生良好的学习效果；一间朴素的教室，如果教学卓越，依然能够成功。亲自然设计改善的是学习的“条件”——它创造了一个更易于维持注意力、压力更低的环境——但它本身并不进行教学。教师的教学法仍然是决定学习质量的首要因素。
