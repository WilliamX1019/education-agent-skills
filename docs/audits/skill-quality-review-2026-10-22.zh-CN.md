# Education Agent Skills — 实用质量审阅与优化建议

2026 年 10 月 22 日。仓库 `GarethManning/education-agent-skills`；基线 `main`：`6bbbce418f82e11044009c9f3b7373a354de5bd0`。独立教育开源项目。**仅为审阅与提案：未更改任何技能、前置元数据、注册表、打包产物、工作流、已安装插件或远程仓库。** 早期的标准审计文档另行保留。

## 核心建议

**通过针对性修正与选择性重组来强化技能库，同时保留其教育实质、身份标识与架构。** 既有的纳入/排除规则非常有价值，但它们的存在本身并不自动保证每一条指令、示例、交接环节和生成主张都一以贯之地落实了这些规则。

应用拟议的八项标准实用质量量规后，产生以下处置队列：

| 主要操作 | 技能数 | 解读 |
|---|---:|---|
| 保留（Keep） | 108 | 在本次有界审阅中未发现有充分理由的内容变更；部分存在可选的元数据/输入约定优化空间 |
| 重组（Reorganize） | 20 | 保留教学方法；考虑采用更轻量的代理入口并将示例/背景外链为参考资料 |
| 修订（Revise） | 37 | 由具体段落支撑的针对性内容、工作流、证据标注或边界改进 |
| 移除（Remove） | 0 | 没有任何证据支持删除某个技能或放弃其教育方法 |

这些属于**编辑/工作流决策，而非通过率、教育效能评分或“37 个不安全技能”**。其中多项修订体量很小。七项获得更高优先级，因为它们涉及安全保护/支持、捏造学习者证据或无边界的互动门控；这是对指令文本的评估，而非实际造成伤害的证据。原创框架身份不是降级的理由。仅涉及证据标签或建议串联元数据的问题，本身不会将技能列入实质性修订队列。

**覆盖范围说明：** 全部 165 个文件均接受了结构化源码筛查并记录了 1,320 条标准判断。一名独立检查员通读了 `student-learning`、`inclusive-design` 和 `wellbeing-motivation-agency` 领域中的 28 个技能；主审计员审阅了其余 137 个技能的结构化档案，并对跨领域被标记的段落进行了聚焦深读。第二名独立质疑者复核了存在争议的判断。这不代表宣称其余 137 个文件的每一行都接受了同等深度的专家审阅。计数用于排定工作优先级，切勿因审阅深度不同而据此推断各领域的失败率。实际模型遵循度、对比实用性、课堂可行性与学习者收益均尚未测量。

## 这套标准为现有规则补充了什么

配套的[量规](skill-quality-rubric-2026-10-22.md)保留了纳入/排除政策，并追问：

1. 任务与目标用户是否足够清晰，以便选对技能？
2. 是否提供了具体的教育专业知识或有用的决策规则？
3. 输入、工作流、示例与交接环节是否彼此一致？
4. 教育/证据主张是否适度且诚实标注？
5. 是否在保留教师/学习者能动性的同时适应相关情境？
6. 所承诺的输出是否能以相称的工作负荷投入使用？
7. 重要边界与失败回退路径是否出现在做出决策的位置？
8. 信息组织是否精炼，且不丢失必要实质内容？

单一的平均分会掩盖重大问题。一个设计精巧、引用研究的工作流仍可能包含一处相互矛盾的分支或不恰当的安全边界。反之，一份包含有益完整示例的长文档并不单纯因为篇幅长就是坏文档。每项建议均附有源码证据、保留其余部分的声明以及最小有用修改。开展本审阅无需以试点或学习者实验为前置条件。

## 应当优先修改的内容

### 1. 修正矛盾与示例准确性

这些是最明确的改进，因为它们不依赖于证明某种新的教学法。

- `skills/student-learning/fading-manager/SKILL.md:111–117,195–201`：进阶规则要求连续三次会话且提示层级为 0–1，但示例在两次且提示层级为 1–2 后就进阶了。其提取标签也与上游生产方不一致。使规则与示例保持一致，同时保留阈值明确标注为启发式的属性。
- `skills/memory-learning-science/retrieval-practice-generator/SKILL.md:109–115,150`：允许针对初学者的识别类题目，随后却被一条“所有题目”规则/自检项禁止。请一贯地陈述预期例外。
- `skills/curriculum-alignment/developmental-band-translator/SKILL.md:126,148–152`：最初的无年龄中止规则与覆盖/扁平框架逻辑冲突。明确优先级，保留不确定性与人工审阅。
- `skills/curriculum-alignment/kud-chart-author/SKILL.md:129,141`：所建议的阶段转换器需要已完成拆解的输入，它并非原始文档拆解服务。
- `skills/student-learning/stuck-and-error-diagnosis-coach/SKILL.md:184,188,224`：数值示例将 2.5 变成了 2，且其“运动学需要时间”的一般性说法是错误的。在匀加速运动下，`v² = u² + 2aΔx` 不需要经过时间。修正示例，同时保留基于诊断的帮助。
- `skills/student-learning/transfer-bridge/SKILL.md:177–236`：示例测试的是均分分配算术，却声称测试了市场价格形成机制的迁移。请使用相同的目标机制，或说明类比局限且不将其计为已证实的迁移。

### 2. 让挑战富有成效，而非困住学习者

保留提取练习、自我解释、分级提示与建设性挣扎。问题不在于这些方法要求学习者思考。

- `productive-failure-protocol:84,110,129–142` 可能在巩固讲解前无限期要求不同尝试。增加有限、可调节的探索/恢复路径。在正确解答之后分析一个有缺陷的替代方案可以保留：这是正当的对比案例教学，本质上并非缺陷。
- `progressive-hint-ladder:149` 将挫败感视为难度恰当的证据。仅凭挫败感无法确立这一点；应检查理解度、可及性以及期望的下一步支持。六级阶梯与不给完整答案的设计在其职责范围内仍是合理选择。
- `retrieve-first-gate` 与 `explain-first-interrogator` 需要针对缺失先备知识的可及暂停/基础教学路径，而非无限期要求再次尝试。保留基于尝试的反馈方法。
- `unassisted-evidence-checkpoint` 可以保留诚实的无辅助标注，同时允许停止/推迟/有辅助恢复；停止并不需要虚假地通过检查点。

### 3. 保留观察结果与不确定性，而非捏造证据

- `confidence-calibration-check:135–139` 指示将未见过主题的学习者信心设为 5。请保留“未知/未采集”或学习者自己的报告，而非凭空捏造数字；反馈应描述本次任务，而非从单次回应诊断稳定的个人特质。
- `ai-claim-checker:62,90–92,102,139,153,157–161` 教授识别潜在不确定性并提出验证方法。保留这一核心任务。允许有理有据的认同，并区分“检查计划”与“实际已执行的核查”。切勿仅因表示认同就贴上“认知警觉度低”标签，也不要将查阅外部信源设为每次使用的强制要求。
- `weekly-agency-review` 应区分记录在案的证据、回忆估算与解读；切勿从不可比的任务中推断因果性的巩固或依赖。
- `wellbeing-learning-connection-mapper:184,203–215,225,249–255` 包含缺乏支撑/过度泛化的影响主张以及虚构场景中并未提供的本地趋势。显式标注假设/示例数据，并允许得出“证据不足”的结论。这是示例中的问题，不证明任何真实学校数据被伪造。

### 4. 将支持与安全保护例外置于决策之前

- `original-frameworks/inclusive-design-orchestrator:124–128,202,239,248` 将个别化支持设为取决于前序层级。保持普遍设计优先作为规划原则，同时并行保留既有的/紧急的无障碍支持。切勿推断单一司法管辖区的法律规则。
- `trauma-informed-practice-designer:215,225–227,250–265,286–293` 需要清晰区分可观察行为与创伤假设、即时安全/本地预案与常规支持转介。流泪并不证实创伤机制。保留冷静回应、可预测性与尊严；由合格专家审阅具有重大影响的回应指南，而非用另一套通用脚本取而代之。
- `restorative-practice-protocol-designer:192–224,301` 已经认识到持续霸凌/权力不对等会使面对面会议不适用，但在持续口音嘲弄案例中却选择了面对面会议。应在选择会议前应用该既有的适用性/同意警示。切勿宣称该技能完全没有同意保护机制。
- `ruler-emotional-literacy-sequence:194–206,227` 需要为情绪与原因披露提供一致的私密/虚构/跳过路径。在座位摆放可见的教室里，未署名的公开便签并不必然匿名。

避免为每个技能添加泛泛的安全长文。将简短、相关的边界放在重大决策点；将支持性背景单独存放。两个存在争议的 UDL 技能予以保留：简短的群体/任务背景本身并不意味着收集/存储实名个人计划。采用共用的可选功能需求/数据最小化约定是适度的。

### 5. 校准证据措辞，而不重开纳入资格争论

早前的审计已独立核查了抽样主张：间隔练习中 Cepeda 的研究计数与声称的精确最优时间表；先解释后追问的持久性/迁移主张；将 CAST 2018 描述为最新版；以及 Woloshyn 文献目录错误。修正这些窄范围要点即可。某框架的证据标签不能证明该具体生成脚本或阈值的有效性，但缺乏精确脚本试验也并不使教学适配归于无效。

对于原创/复合方法，保留有用的独特规则以及清晰的实践者/综合标签。切勿将所有框架改写为泛泛建议或删除其研究引用。结合语境审阅缺乏支撑的词汇（如“confirms（证实）”、“guarantees（保证）”、“validates（验证）”、“always（总是）”和“never（绝不）”）；不能仅凭单个关键词就删除陈述。例如，`professional-learning/competency-framework-translator:116,128–130` 应将模型解读与经核实的“原始框架原文（Original Framework Wording）”区分开来。

### 6. 让实际交付的技能携带其核心警示

本仓库有两个存在实质差异的阅读界面。本地客户端可以读取完整技能；MCP 仅提取 Prompt/System Prompt。部分有价值的警示仅存在于提取范围之外的“已知局限（Known Limitations）”中。通过精确的源文件与打包产物对比核实的示例包括：

- `retrieval-practice-generator:221`：答案/术语应对照所教材料核对；在提取出的提示词中缺失。
- `ladder-of-inference-reflection:173–175`：近期的重大伤害与权力不对等限制了适用范围；核心中已有通用尊严规则，但缺少这一具体边界。
- `historical-document-set-curator:290`：它提出史料建议，但无法实际提供史料；活跃输出却要求给出具体史料身份而未清晰标注“已核实/拟议”状态。

这并非要求将所有研究段落都内联进提示词，而是在核心中保留最小的决策相关警示。可选的详细资源必须对需要它的客户端可用；在无法访问的托管环境中，相对路径不是完整的解决方案。在精简的核心修正足以解决问题时，避免进行基础设施重构。

## 长度证据真正说明了什么

全部 165 个技能均使用 **tiktoken 0.14.0 / o200k_base** 进行了测量——这是一个可重复的代理指标，而非 Claude 分词器或实际观测到的运行时账单。正文（Body）不含 YAML 前置元数据；完整文件（Full file）包含元数据。MCP 计数使用的是输入替换前当前打包提取的提示词。这些是不同的分母。

| 指标 | 结果 |
|---|---:|
| 超过 5,000 代理 token 的正文 | 23 |
| 超过 5,000 的完整文件（含元数据） | 50 |
| 超过 5,000 的提取后 MCP 提示词 | 1 |
| 正文 token 中位数 | 3,895 |
| 提取后提示词 token 中位数 | 1,118 |
| 正文总词数 / 提取后提示词总词数 | 484,285 / 141,346 |

早期报告中“16 个文件超过 4,000 **词**、4 个超过 500 **行**”是准确但不够完整的长度筛查。Token 测量细化了这一图景；它既不确立最优长度，也不否定早期计数。多个文件仅略高于 5,000 代理 token，无需自动采取行动。对于在激活时加载整个文件的客户端，丰富的元数据也会增加完整文件体量，但未必影响仅加载元数据的启动阶段。

| 技能 | 正文代理 token | MCP 提示词代理 token | 主要操作 |
|---|---:|---:|---|
| `dispositional-knowledge-assessment-designer` | 13,219 | 5,789 | revise |
| `learning-target-authoring-guide` | 11,743 | 1,938 | reorganize |
| `panel-review` | 11,448 | 4,808 | revise |
| `scope-and-sequence-designer` | 9,351 | 2,658 | reorganize |
| `kud-knowledge-type-mapper` | 8,187 | 2,358 | reorganize |
| `curriculum-knowledge-architecture-designer` | 7,700 | 1,745 | reorganize |
| `pedagogical-content-knowledge-developer` | 7,510 | 1,991 | reorganize |
| `technological-pedagogical-content-knowledge-developer` | 7,472 | 2,085 | reorganize |
| `discipline-specific-critical-thinking-task-designer` | 6,686 | 1,928 | reorganize |
| `self-determined-project-design-protocol` | 6,536 | 1,666 | reorganize |
| `kud-chart-author` | 6,155 | 3,397 | revise |
| `seeds-regenerative-inquiry-cycle` | 6,118 | 1,805 | reorganize |
| `sourcing-skill-builder` | 5,971 | 1,534 | reorganize |
| `uninterrupted-work-cycle-designer` | 5,678 | 1,131 | reorganize |
| `developmental-progression-synthesis` | 5,659 | 2,528 | reorganize |
| `project-brief-designer` | 5,533 | 1,534 | reorganize |
| `document-based-lesson-designer` | 5,281 | 1,574 | reorganize |
| `cognitive-tutoring-architecture-designer` | 5,091 | 999 | reorganize |
| `productive-failure-desirable-difficulty-designer` | 5,059 | 1,137 | reorganize |
| `contextualisation-skill-builder` | 5,031 | 1,138 | reorganize |
| `formative-assessment-loop-designer` | 5,029 | 1,140 | reorganize |
| `lesson-study-cycle-designer` | 5,005 | 1,136 | reorganize |
| `intelligent-tutoring-dialogue-designer` | 5,004 | 1,053 | reorganize |

最适合进行核心模块化的候选是 `dispositional-knowledge-assessment-designer`：正文 13,219 token、核心提示词 5,789 token、包含多个有意义的组件以及可观的实施工作负荷。应允许用户选择所需组件、保留其核心区分/安全边界，并使完整方法保持可用。切勿把所有源文件体量都当成冗余：例如 `learning-target-authoring-guide` 正文有 11,743 token，但提取出的提示词只有 1,938 token。

在重组时，应在核心中保留输入、决策序列、关键例外、输出契约以及一个紧凑示例。冗长的对话记录、替代模板与研究阐释可转为命名清晰、按条件加载的参考资料。移出前先修正相互矛盾的示例。保持一份可读的人类指南。切勿仅因某条规则较长就删减它；先问它防止什么错误以及在何处需要它。

## 若后续获准变更，建议的执行顺序

1. 在 Git 中保留带标签/冻结的已验收基线；切勿复制活跃的 old/new/v2 技能目录。
2. 以小型编辑修正高置信度的事实与规则/示例矛盾。
3. 在适当的人类专业知识参与下修正重大支持、安全保护与学习者证据边界。
4. 改进情境/能动性恢复路径，并确保核心警示在 MCP 提取后得以保留。
5. 有选择地重组长入口指南；切勿批量缩减 165 个提示词或强迫每个技能套用同一模板。
6. 保留 ID/schema/引用；为已验收的源文件变更重新生成注册表与打包产物；检查源文件/核心一致性与现有测试。将安全/基础设施修复与内容编辑分开。
7. 为每次获批变更保留理由与具体的修改前后示例。任务输出对比可在日后解决有争议的选择，但本审阅不要求在修复明确缺陷前先开展试点或学习者研究。

完整的逐技能提案见[矩阵](skill-quality-review-matrix.csv)，包含全部八项判断与源码链接。[结构化证据](skill-quality-review-evidence.json)还列明了需保留内容、强制核心指令、可选资源候选、源文件哈希与审阅深度。工作量规与队列仅为提案，并非已记录的创始人决策或实施授权。

## 逐技能操作索引

优先级反映的是建议改进顺序，而非 165 个已部署系统的严重程度标签。仅限元数据的提示性建议可能伴随 Keep；正文体量优化机会可能伴随 Revise。由于完整文件独立阅读聚焦于 28 个技能，各领域的决策并非同等深度验证；审阅深度已在矩阵中明确标明。

| 技能 | 主要操作 | 优先级 |
|---|---|---|
| [ai-claim-checker](../../skills/student-learning/ai-claim-checker/SKILL.md) | revise | high |
| [confidence-calibration-check](../../skills/student-learning/confidence-calibration-check/SKILL.md) | revise | high |
| [inclusive-design-orchestrator](../../skills/original-frameworks/inclusive-design-orchestrator/SKILL.md) | revise | high |
| [productive-failure-protocol](../../skills/student-learning/productive-failure-protocol/SKILL.md) | revise | high |
| [restorative-practice-protocol-designer](../../skills/wellbeing-motivation-agency/restorative-practice-protocol-designer/SKILL.md) | revise | high |
| [ruler-emotional-literacy-sequence](../../skills/wellbeing-motivation-agency/ruler-emotional-literacy-sequence/SKILL.md) | revise | high |
| [trauma-informed-practice-designer](../../skills/wellbeing-motivation-agency/trauma-informed-practice-designer/SKILL.md) | revise | high |
| [agency-scaffold-generator](../../skills/wellbeing-motivation-agency/agency-scaffold-generator/SKILL.md) | revise | medium |
| [awe-wonder-experience-designer](../../skills/wellbeing-motivation-agency/awe-wonder-experience-designer/SKILL.md) | revise | medium |
| [belonging-classroom-culture-designer](../../skills/wellbeing-motivation-agency/belonging-classroom-culture-designer/SKILL.md) | revise | medium |
| [competency-framework-translator](../../skills/professional-learning/competency-framework-translator/SKILL.md) | revise | medium |
| [developmental-band-system-designer](../../skills/original-frameworks/developmental-band-system-designer/SKILL.md) | revise | medium |
| [developmental-band-translator](../../skills/curriculum-alignment/developmental-band-translator/SKILL.md) | revise | medium |
| [differentiation-adapter](../../skills/curriculum-assessment/differentiation-adapter/SKILL.md) | revise | medium |
| [dispositional-knowledge-assessment-designer](../../skills/original-frameworks/dispositional-knowledge-assessment-designer/SKILL.md) | revise | medium |
| [explain-first-interrogator](../../skills/student-learning/explain-first-interrogator/SKILL.md) | revise | medium |
| [fading-manager](../../skills/student-learning/fading-manager/SKILL.md) | revise | medium |
| [flow-state-condition-designer](../../skills/wellbeing-motivation-agency/flow-state-condition-designer/SKILL.md) | revise | medium |
| [historical-document-set-curator](../../skills/historical-thinking/historical-document-set-curator/SKILL.md) | revise | medium |
| [implementation-intention-designer](../../skills/wellbeing-motivation-agency/implementation-intention-designer/SKILL.md) | revise | medium |
| [kud-chart-author](../../skills/curriculum-alignment/kud-chart-author/SKILL.md) | revise | medium |
| [ladder-of-inference-reflection](../../skills/systems-thinking/ladder-of-inference-reflection/SKILL.md) | revise | medium |
| [motivation-diagnostic-task-redesign](../../skills/wellbeing-motivation-agency/motivation-diagnostic-task-redesign/SKILL.md) | revise | medium |
| [panel-review](../../skills/professional-learning/panel-review/SKILL.md) | revise | medium |
| [perma-based-lesson-designer](../../skills/wellbeing-motivation-agency/perma-based-lesson-designer/SKILL.md) | revise | medium |
| [progressive-hint-ladder](../../skills/student-learning/progressive-hint-ladder/SKILL.md) | revise | medium |
| [retrieval-practice-generator](../../skills/memory-learning-science/retrieval-practice-generator/SKILL.md) | revise | medium |
| [retrieve-first-gate](../../skills/student-learning/retrieve-first-gate/SKILL.md) | revise | medium |
| [self-efficacy-builder-sequence](../../skills/wellbeing-motivation-agency/self-efficacy-builder-sequence/SKILL.md) | revise | medium |
| [spaced-practice-scheduler](../../skills/memory-learning-science/spaced-practice-scheduler/SKILL.md) | revise | medium |
| [srl-session-wrapper](../../skills/student-learning/srl-session-wrapper/SKILL.md) | revise | medium |
| [stuck-and-error-diagnosis-coach](../../skills/student-learning/stuck-and-error-diagnosis-coach/SKILL.md) | revise | medium |
| [teach-back-evaluator](../../skills/student-learning/teach-back-evaluator/SKILL.md) | revise | medium |
| [transfer-bridge](../../skills/student-learning/transfer-bridge/SKILL.md) | revise | medium |
| [unassisted-evidence-checkpoint](../../skills/student-learning/unassisted-evidence-checkpoint/SKILL.md) | revise | medium |
| [weekly-agency-review](../../skills/student-learning/weekly-agency-review/SKILL.md) | revise | medium |
| [wellbeing-learning-connection-mapper](../../skills/wellbeing-motivation-agency/wellbeing-learning-connection-mapper/SKILL.md) | revise | medium |
| [academic-language-sentence-frame-generator](../../skills/eal-language-development/academic-language-sentence-frame-generator/SKILL.md) | keep | low |
| [backwards-design-unit-planner](../../skills/curriculum-assessment/backwards-design-unit-planner/SKILL.md) | keep | low |
| [cognitive-tutoring-architecture-designer](../../skills/ai-learning-science/cognitive-tutoring-architecture-designer/SKILL.md) | reorganize | low |
| [contextualisation-skill-builder](../../skills/historical-thinking/contextualisation-skill-builder/SKILL.md) | reorganize | low |
| [cpa-sequence-designer](../../skills/global-cross-cultural-pedagogies/cpa-sequence-designer/SKILL.md) | keep | low |
| [cross-cultural-task-validity-checker](../../skills/global-cross-cultural-pedagogies/cross-cultural-task-validity-checker/SKILL.md) | keep | low |
| [curriculum-knowledge-architecture-designer](../../skills/curriculum-assessment/curriculum-knowledge-architecture-designer/SKILL.md) | reorganize | low |
| [developmental-progression-synthesis](../../skills/original-frameworks/developmental-progression-synthesis/SKILL.md) | reorganize | low |
| [discipline-specific-critical-thinking-task-designer](../../skills/curriculum-assessment/discipline-specific-critical-thinking-task-designer/SKILL.md) | reorganize | low |
| [document-based-lesson-designer](../../skills/historical-thinking/document-based-lesson-designer/SKILL.md) | reorganize | low |
| [erroneous-example-designer](../../skills/ai-learning-science/erroneous-example-designer/SKILL.md) | keep | low |
| [formative-assessment-loop-designer](../../skills/ai-learning-science/formative-assessment-loop-designer/SKILL.md) | reorganize | low |
| [formative-assessment-technique-selector](../../skills/curriculum-assessment/formative-assessment-technique-selector/SKILL.md) | keep | low |
| [individual-spacing-algorithm-explainer](../../skills/ai-learning-science/individual-spacing-algorithm-explainer/SKILL.md) | keep | low |
| [intelligent-tutoring-dialogue-designer](../../skills/ai-learning-science/intelligent-tutoring-dialogue-designer/SKILL.md) | reorganize | low |
| [kud-knowledge-type-mapper](../../skills/curriculum-assessment/kud-knowledge-type-mapper/SKILL.md) | reorganize | low |
| [learning-analytics-interpretation-guide](../../skills/ai-learning-science/learning-analytics-interpretation-guide/SKILL.md) | keep | low |
| [learning-target-authoring-guide](../../skills/original-frameworks/learning-target-authoring-guide/SKILL.md) | reorganize | low |
| [lesson-study-cycle-designer](../../skills/professional-learning/lesson-study-cycle-designer/SKILL.md) | reorganize | low |
| [mixed-age-learning-task-designer](../../skills/montessori-alternative-approaches/mixed-age-learning-task-designer/SKILL.md) | keep | low |
| [pedagogical-content-knowledge-developer](../../skills/professional-learning/pedagogical-content-knowledge-developer/SKILL.md) | reorganize | low |
| [productive-failure-desirable-difficulty-designer](../../skills/ai-learning-science/productive-failure-desirable-difficulty-designer/SKILL.md) | reorganize | low |
| [project-brief-designer](../../skills/curriculum-assessment/project-brief-designer/SKILL.md) | reorganize | low |
| [prompt-literacy-sequence-designer](../../skills/ai-literacy/prompt-literacy-sequence-designer/SKILL.md) | keep | low |
| [scope-and-sequence-designer](../../skills/curriculum-assessment/scope-and-sequence-designer/SKILL.md) | reorganize | low |
| [seeds-regenerative-inquiry-cycle](../../skills/original-frameworks/seeds-regenerative-inquiry-cycle/SKILL.md) | reorganize | low |
| [self-determined-project-design-protocol](../../skills/original-frameworks/self-determined-project-design-protocol/SKILL.md) | reorganize | low |
| [sourcing-skill-builder](../../skills/historical-thinking/sourcing-skill-builder/SKILL.md) | reorganize | low |
| [technological-pedagogical-content-knowledge-developer](../../skills/professional-learning/technological-pedagogical-content-knowledge-developer/SKILL.md) | reorganize | low |
| [three-part-lesson-designer](../../skills/montessori-alternative-approaches/three-part-lesson-designer/SKILL.md) | keep | low |
| [uninterrupted-work-cycle-designer](../../skills/montessori-alternative-approaches/uninterrupted-work-cycle-designer/SKILL.md) | reorganize | low |
| [variation-theory-task-designer](../../skills/global-cross-cultural-pedagogies/variation-theory-task-designer/SKILL.md) | keep | low |
| [adaptive-hint-sequence-designer](../../skills/ai-learning-science/adaptive-hint-sequence-designer/SKILL.md) | keep | none |
| [agency-circles-for-systems-action](../../skills/systems-thinking/agency-circles-for-systems-action/SKILL.md) | keep | none |
| [ai-expertise-interrogation-designer](../../skills/ai-literacy/ai-expertise-interrogation-designer/SKILL.md) | keep | none |
| [ai-facilitated-collaborative-learning-designer](../../skills/ai-learning-science/ai-facilitated-collaborative-learning-designer/SKILL.md) | keep | none |
| [ai-feedback-design-principles](../../skills/ai-learning-science/ai-feedback-design-principles/SKILL.md) | keep | none |
| [ai-hallucination-fact-check-protocol](../../skills/ai-literacy/ai-hallucination-fact-check-protocol/SKILL.md) | keep | none |
| [ai-learning-boundary-mapper](../../skills/ai-literacy/ai-learning-boundary-mapper/SKILL.md) | keep | none |
| [ai-output-critical-audit-designer](../../skills/ai-literacy/ai-output-critical-audit-designer/SKILL.md) | keep | none |
| [ai-socratic-dialogue-designer](../../skills/ai-literacy/ai-socratic-dialogue-designer/SKILL.md) | keep | none |
| [argument-structure-scaffold-generator](../../skills/literacy-critical-thinking/argument-structure-scaffold-generator/SKILL.md) | keep | none |
| [aspirational-systems-iceberg](../../skills/systems-thinking/aspirational-systems-iceberg/SKILL.md) | keep | none |
| [assessment-design-orchestrator](../../skills/original-frameworks/assessment-design-orchestrator/SKILL.md) | keep | none |
| [assessment-validity-checker](../../skills/curriculum-assessment/assessment-validity-checker/SKILL.md) | keep | none |
| [biophilic-learning-environment-designer](../../skills/environmental-experiential-learning/biophilic-learning-environment-designer/SKILL.md) | keep | none |
| [central-historical-question-evaluator](../../skills/historical-thinking/central-historical-question-evaluator/SKILL.md) | keep | none |
| [checking-for-understanding-protocol-designer](../../skills/explicit-instruction/checking-for-understanding-protocol-designer/SKILL.md) | keep | none |
| [close-reading-skill-builder](../../skills/historical-thinking/close-reading-skill-builder/SKILL.md) | keep | none |
| [cognitive-load-analyser](../../skills/memory-learning-science/cognitive-load-analyser/SKILL.md) | keep | none |
| [coherent-rubric-logic-builder](../../skills/original-frameworks/coherent-rubric-logic-builder/SKILL.md) | keep | none |
| [compassionate-systems-awareness-orchestrator](../../skills/original-frameworks/compassionate-systems-awareness-orchestrator/SKILL.md) | keep | none |
| [competency-unpacker](../../skills/curriculum-assessment/competency-unpacker/SKILL.md) | keep | none |
| [corroboration-skill-builder](../../skills/historical-thinking/corroboration-skill-builder/SKILL.md) | keep | none |
| [coverage-audit](../../skills/curriculum-alignment/coverage-audit/SKILL.md) | keep | none |
| [criterion-referenced-rubric-generator](../../skills/curriculum-assessment/criterion-referenced-rubric-generator/SKILL.md) | keep | none |
| [critical-thinking-task-designer](../../skills/literacy-critical-thinking/critical-thinking-task-designer/SKILL.md) | keep | none |
| [culturally-responsive-teaching-designer](../../skills/global-cross-cultural-pedagogies/culturally-responsive-teaching-designer/SKILL.md) | keep | none |
| [curriculum-crosswalk](../../skills/curriculum-alignment/curriculum-crosswalk/SKILL.md) | keep | none |
| [dialogic-teaching-move-generator](../../skills/questioning-discussion/dialogic-teaching-move-generator/SKILL.md) | keep | none |
| [digital-worked-example-sequence](../../skills/ai-learning-science/digital-worked-example-sequence/SKILL.md) | keep | none |
| [dilemma-navigation-for-education-design](../../skills/original-frameworks/dilemma-navigation-for-education-design/SKILL.md) | keep | none |
| [disciplinary-ai-literacy-sequence-designer](../../skills/ai-literacy/disciplinary-ai-literacy-sequence-designer/SKILL.md) | keep | none |
| [disciplinary-writing-scaffold](../../skills/literacy-critical-thinking/disciplinary-writing-scaffold/SKILL.md) | keep | none |
| [discussion-protocol-selector](../../skills/questioning-discussion/discussion-protocol-selector/SKILL.md) | keep | none |
| [dual-coding-designer](../../skills/memory-learning-science/dual-coding-designer/SKILL.md) | keep | none |
| [ecological-inquiry-anchor-designer](../../skills/environmental-experiential-learning/ecological-inquiry-anchor-designer/SKILL.md) | keep | none |
| [elaborative-interrogation-generator](../../skills/memory-learning-science/elaborative-interrogation-generator/SKILL.md) | keep | none |
| [emergent-project-design-scaffold](../../skills/global-cross-cultural-pedagogies/emergent-project-design-scaffold/SKILL.md) | keep | none |
| [error-analysis-protocol](../../skills/self-regulated-learning/error-analysis-protocol/SKILL.md) | keep | none |
| [experiential-learning-cycle-designer](../../skills/environmental-experiential-learning/experiential-learning-cycle-designer/SKILL.md) | keep | none |
| [explicit-instruction-sequence-builder](../../skills/explicit-instruction/explicit-instruction-sequence-builder/SKILL.md) | keep | none |
| [feedback-quality-analyser](../../skills/memory-learning-science/feedback-quality-analyser/SKILL.md) | keep | none |
| [gap-analysis-from-student-work](../../skills/curriculum-assessment/gap-analysis-from-student-work/SKILL.md) | keep | none |
| [goal-setting-protocol-designer](../../skills/self-regulated-learning/goal-setting-protocol-designer/SKILL.md) | keep | none |
| [hexagon-complexity-mapper](../../skills/systems-thinking/hexagon-complexity-mapper/SKILL.md) | keep | none |
| [hinge-question-designer](../../skills/questioning-discussion/hinge-question-designer/SKILL.md) | keep | none |
| [historical-source-adapter](../../skills/historical-thinking/historical-source-adapter/SKILL.md) | keep | none |
| [historical-thinking-assessment-designer](../../skills/historical-thinking/historical-thinking-assessment-designer/SKILL.md) | keep | none |
| [historical-thinking-strategy-modelling-guide](../../skills/historical-thinking/historical-thinking-strategy-modelling-guide/SKILL.md) | keep | none |
| [instructional-coaching-conversation-guide](../../skills/professional-learning/instructional-coaching-conversation-guide/SKILL.md) | keep | none |
| [interdisciplinary-real-world-connection-mapper](../../skills/environmental-experiential-learning/interdisciplinary-real-world-connection-mapper/SKILL.md) | keep | none |
| [interleaving-unit-planner](../../skills/memory-learning-science/interleaving-unit-planner/SKILL.md) | keep | none |
| [language-demand-analyser](../../skills/eal-language-development/language-demand-analyser/SKILL.md) | keep | none |
| [learning-progression-builder](../../skills/curriculum-assessment/learning-progression-builder/SKILL.md) | keep | none |
| [lesson-observation-protocol-designer](../../skills/professional-learning/lesson-observation-protocol-designer/SKILL.md) | keep | none |
| [lesson-opening-designer](../../skills/explicit-instruction/lesson-opening-designer/SKILL.md) | keep | none |
| [leverage-and-response-design](../../skills/systems-thinking/leverage-and-response-design/SKILL.md) | keep | none |
| [media-literacy-deconstruction-protocol](../../skills/literacy-critical-thinking/media-literacy-deconstruction-protocol/SKILL.md) | keep | none |
| [mental-model-mapper](../../skills/systems-thinking/mental-model-mapper/SKILL.md) | keep | none |
| [metacognitive-monitoring-ai-contexts](../../skills/ai-learning-science/metacognitive-monitoring-ai-contexts/SKILL.md) | keep | none |
| [metacognitive-prompt-library](../../skills/self-regulated-learning/metacognitive-prompt-library/SKILL.md) | keep | none |
| [multi-perspective-decision-wheel](../../skills/original-frameworks/multi-perspective-decision-wheel/SKILL.md) | keep | none |
| [outdoor-learning-sequence-designer](../../skills/environmental-experiential-learning/outdoor-learning-sequence-designer/SKILL.md) | keep | none |
| [perspective-taking-designer](../../skills/questioning-discussion/perspective-taking-designer/SKILL.md) | keep | none |
| [phenomenon-based-unit-anchor](../../skills/global-cross-cultural-pedagogies/phenomenon-based-unit-anchor/SKILL.md) | keep | none |
| [place-based-curriculum-orchestrator](../../skills/original-frameworks/place-based-curriculum-orchestrator/SKILL.md) | keep | none |
| [place-based-inquiry-anchor](../../skills/global-cross-cultural-pedagogies/place-based-inquiry-anchor/SKILL.md) | keep | none |
| [practice-problem-sequence-designer](../../skills/explicit-instruction/practice-problem-sequence-designer/SKILL.md) | keep | none |
| [prepared-environment-designer](../../skills/montessori-alternative-approaches/prepared-environment-designer/SKILL.md) | keep | none |
| [professional-development-session-designer](../../skills/professional-learning/professional-development-session-designer/SKILL.md) | keep | none |
| [reading-comprehension-strategy-selector](../../skills/literacy-critical-thinking/reading-comprehension-strategy-selector/SKILL.md) | keep | none |
| [reflective-practice-prompt-generator](../../skills/professional-learning/reflective-practice-prompt-generator/SKILL.md) | keep | none |
| [regenerative-project-design-orchestrator](../../skills/original-frameworks/regenerative-project-design-orchestrator/SKILL.md) | keep | none |
| [reggio-documentation-protocol](../../skills/global-cross-cultural-pedagogies/reggio-documentation-protocol/SKILL.md) | keep | none |
| [scaffolded-task-modifier](../../skills/eal-language-development/scaffolded-task-modifier/SKILL.md) | keep | none |
| [scoping-for-transformative-learning-inquiry](../../skills/original-frameworks/scoping-for-transformative-learning-inquiry/SKILL.md) | keep | none |
| [self-explanation-prompt-designer](../../skills/ai-learning-science/self-explanation-prompt-designer/SKILL.md) | keep | none |
| [self-regulation-scaffold-generator](../../skills/self-regulated-learning/self-regulation-scaffold-generator/SKILL.md) | keep | none |
| [service-learning-project-designer](../../skills/environmental-experiential-learning/service-learning-project-designer/SKILL.md) | keep | none |
| [sheltered-instruction-lesson-modifier](../../skills/eal-language-development/sheltered-instruction-lesson-modifier/SKILL.md) | keep | none |
| [single-point-rubric-designer](../../skills/original-frameworks/single-point-rubric-designer/SKILL.md) | keep | none |
| [socratic-questioning-sequence-generator](../../skills/questioning-discussion/socratic-questioning-sequence-generator/SKILL.md) | keep | none |
| [source-credibility-evaluation-protocol](../../skills/literacy-critical-thinking/source-credibility-evaluation-protocol/SKILL.md) | keep | none |
| [study-strategy-selector](../../skills/self-regulated-learning/study-strategy-selector/SKILL.md) | keep | none |
| [systems-awareness-iceberg](../../skills/systems-thinking/systems-awareness-iceberg/SKILL.md) | keep | none |
| [systems-wellbeing-impact-mapper](../../skills/systems-thinking/systems-wellbeing-impact-mapper/SKILL.md) | keep | none |
| [teacher-inquiry-cycle-designer](../../skills/professional-learning/teacher-inquiry-cycle-designer/SKILL.md) | keep | none |
| [text-complexity-analyser](../../skills/literacy-critical-thinking/text-complexity-analyser/SKILL.md) | keep | none |
| [think-aloud-script-generator](../../skills/explicit-instruction/think-aloud-script-generator/SKILL.md) | keep | none |
| [three-horizons-learning-transition-mapper](../../skills/original-frameworks/three-horizons-learning-transition-mapper/SKILL.md) | keep | none |
| [ubuntu-collective-knowledge-task-designer](../../skills/global-cross-cultural-pedagogies/ubuntu-collective-knowledge-task-designer/SKILL.md) | keep | none |
| [udl-barrier-anticipator](../../skills/inclusive-design/udl-barrier-anticipator/SKILL.md) | keep | none |
| [udl-lesson-auditor](../../skills/inclusive-design/udl-lesson-auditor/SKILL.md) | keep | none |
| [udl-options-designer](../../skills/inclusive-design/udl-options-designer/SKILL.md) | keep | none |
| [vocabulary-tiering-tool](../../skills/eal-language-development/vocabulary-tiering-tool/SKILL.md) | keep | none |
| [worked-example-fading-designer](../../skills/memory-learning-science/worked-example-fading-designer/SKILL.md) | keep | none |
| [worked-example-to-problem-solving-transition-designer](../../skills/ai-learning-science/worked-example-to-problem-solving-transition-designer/SKILL.md) | keep | none |

## 验证与局限

未测试任何技能输出、学习者成效、对比模型行为或缩短篇幅的效果。保留既有的纳入/排除决策；引用/主张核查仍属于抽样性质，而非对 872 条文献的系统综述。未运行任何新的付费任务模型评估、外部研究、软件包发布、提交、推送或部署。临时分词器依赖仅安装在现有的临时虚拟环境中。在 `docs/audits` 下仅编写了这四份新的质量审阅产物；早期审计文件保持不变。已检查源字节哈希、路径/行号边界、165 行唯一性与 1,320 条标准覆盖率。

本次审阅的协作情况：峰值同时活跃派生工作代理数为 1；两名独立检查员均携带紧凑工作包且无继承历史；没有任何工作代理派生子代理。主审阅员负责综合及剩余源码筛查。质疑环节将两项隐私/仅限专家的 UDL 修订提案降级为 Keep，并收窄了声明核查/对比案例建议。模型组合：配置的默认 Codex 模型，无显式覆盖。源文件中无实施/返工。自创建档案起审阅耗时约 14 分钟；Token/额度遥测不可用。
