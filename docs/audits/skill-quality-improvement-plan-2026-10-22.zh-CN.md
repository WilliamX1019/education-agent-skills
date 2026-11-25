# 教育技能强化 — 综合实施与评估计划

**日期：** 2026 年 10 月 22 日。**状态：** 供后续授权使用的提案；仅限规划。**仓库：** `GarethManning/education-agent-skills`，独立开源教育技能库。**检查基线：** `main` `6bbbce418f82e11044009c9f3b7373a354de5bd0`。

## 1. 预期成果与范围

在保留技能教育实质的前提下，使其更加可靠、实用且精炼。使用明确的质量标准为每一项修改提供依据，优先修正已证实的问题，并保留有助于教育者或代理做出更佳决策的细节。切勿假定全面重写是有益的。

推荐的方案包含三个可分离的部分：

1. **针对性修正：** 细读并处理 37 个带有具体修订提案的技能。其中多项修改仅涉及几句话或一个示例；被列入此队列并不意味着整个技能质量不佳。
2. **选择性组织：** 审视 20 个重组候选以及已在修订队列中的 3 个长技能。仅当移出材料能够改善导航或实际激活开销且不丢失功能时才移动。经过论证的“不予修改”结果也是可接受的。
3. **持久化质量控制：** 保留量规、可追溯的变更记录、聚焦示例及现有打包测试。仅在需要回答未决决策时才引入基于模型的任务评估；不以试点或学习者成效研究作为前置条件。

除非新发现的有来源支撑的问题证明有必要进行有界补充，否则保持其余 108 个技能不变。保留全部 165 个身份标识、现有发现架构、证据基础以及有用的独特方法。不提议移除任何技能。

本文档不授权编辑技能、提交、推送、发布版本、更改已安装插件、运行付费评估或部署 MCP 服务。为本次请求唯一新建的产物即为本计划。早期审计与审阅产物保持完整。

### 权威输入及其局限

- [质量量规](skill-quality-rubric-2026-10-22.md)：八项标准、任务类别区分与优化规则。
- [质量审阅](skill-quality-review-2026-10-22.md)、[165 技能矩阵](skill-quality-review-matrix.csv)与[结构化证据](skill-quality-review-evidence.json)：拟议操作、源文件哈希、行号证据、需保留材料、核心指令与潜在参考资料。
- [标准审计](agent-skills-standard-audit-2026-10-22.md)、[独立基础设施迁移计划](agent-skills-migration-plan.md)与[审计证据](agent-skills-audit-evidence.md)：打包、校验、客户端集成与安全工作。本计划与该工作协同，但并不静默扩大其范围或批准该计划。
- [AGENTS.md](../../AGENTS.md)、[CLAUDE.md](../../CLAUDE.md)、[CONTRIBUTING.md](../../CONTRIBUTING.md)、[STATE.md](../../STATE.md)、[证据指南](../EVIDENCE.md)与[排除清单](../EXCLUSIONS.md)：本地约定与现行纳入政策。历史状态仅供参考；计数以实际源文件清单为准。

审阅筛查了全部 165 个源文件并记录了 1,320 条标准判断。独立全文检查覆盖了 28 个技能；其余 137 个接受了结构化筛查与选定深读。这属于不等深度的静态审阅，而非实测模型表现或教育有效性认证。编辑某个候选技能前，请通读其完整文件、直接上下游契约以及相关的引用文献段落。如果更深入的阅读不支持某项发现，则撤回或收窄该发现。切勿在开工前再强制开展一次全库审计。

## 2. 卓越的含义与判断标准

既有的教育纳入/排除要求仍是资格基线。以下标准评估一个符合资格的方法作为代理技能的实现质量。Agent Skills 格式合规性与厂商编写指南本身不构成完整的实用性量规。

| 标准 | 审阅者提问 | 接受改进的充分证据 |
|---|---|---|
| C1 目的与选择 | 任务、用户与合适触发器是否清晰？ | 描述与正文范围一致；能够区分真实使用与非使用场景。 |
| C2 增值专业度 | 技能是否增加了具体的教育专业判断？ | 保留了具名区分、决策规则或程序；泛泛鼓励未取代专业知识。 |
| C3 连贯性与可操作性 | 输入、分支、示例与交接是否一致？ | 实际矛盾已解决；核心与示例中的同一案例遵循同一规则。 |
| C4 证据完整性 | 主张是否准确、可追溯且适度？ | 争议主张已对照一手来源核查；区分了引文、解读、证据与启发式规则。 |
| C5 情境与能动性 | 方法是否妥善处理准备度、可及性与用户选择？ | 相关边界案例具备可用分支；现有支持与教师/学习者判断在编辑后得以保留。 |
| C6 实用性 | 所承诺的输出是否能以相称的工作负荷使用？ | 产物回应了既定任务；在相关处明确了后续行动、假设与实施负担。 |
| C7 边界与恢复 | 当常规路径不适用时，用户能否安全恢复？ | 必要例外出现在每个交付界面的决策点；无捏造的学习者证据或虚假完成。 |
| C8 精炼度与组织 | 每条信息是否位于正确位置？ | 核心规则保持立即可用；可选细节具备明确加载条件，且在支持时可在仓库外工作。 |

保留**文本中有支撑 / 存在疑虑 / 尚未证实**三档判断，并附上解释与源码引用。切勿将八项得分平均为及格线。准确性、支持或安全保护问题无法被华丽的文风所抵消。源文件审阅者可能批准某项文字修复；这并不代表确立了代理的一致遵循度。

对于每项拟议编辑，记录：具体问题、受影响标准、源码段落、最小修正、保留的行为、受影响的交付界面以及具体的验收示例。避免为了满足检查清单而堆砌套话。只要定位与局限性诚实清晰，实践者原创方法无需先对其精确脚本开展试验即可发挥效用。

### 实用验收规则

当一个内容工作包满足以下条件时，即具备集成就绪状态：已识别的疑虑已解决或有据撤回；受保护行为得以保留；示例与接口一致；必要边界在交付中得以留存；适用检查通过；以及剩余未知项已如实报告。已知且存在重大影响的未决问题不得标记为已验收。延后的可选改进不阻塞本身稳健的修正。

运用任务类别判断：评价技能必须评估预期构念；课程映射器必须保留来源原始表述与歧义；实时辅导技能需要有界互动与诚实辅助记录；福祉规划技能必须避免诊断、强迫披露与缺乏支撑的干预主张。不存在强制性的通用模板。

## 3. 评估设计：无需研究计划即可获得的实用证据

### A 层 — 打包与契约检查

使用现有的校验器与测试来验证确定性属性：可解析性、ID、必需字段、注册表/打包产物新鲜度及服务器契约。仅针对新引入的资源处理或已证实的回归问题添加聚焦检查。诸如“包含 agency 一词”的关键词断言不是质量测试。格式检查无法确立有用性。

### B 层 — 专家源文件审阅与具体案例

这是拟议修正的默认验收路径。通读受影响的整个技能、检查精确 diff、审阅其教育主张并走查指定的常规与边界案例。审阅者必须给出理由并指出回归，而不仅仅是批准量规标签。保留一个展示修改后为何更好的虚构案例；切勿将人工推理走查称为已执行的模型测试。

尽可能使用已暴露缺陷的案例：缺失的信心值、缺乏先备知识的初学者、持续的针对性嘲弄、原始课程文档，或错误的迁移示例。包含一个常规成功案例以保护有用方法。案例体量应与变更成比例；一处引用修正不需要新建一套基准测试。

对于实质性教育变更——尤其是 Q1 以及证据含义的变更——应使用独立内容审阅者。模型审阅可以挑战推理并发现不一致；它不能替代合格人类专家对具有重大影响的安全保护/应对流程的审阅。在寻求专家意见前，先准备好具体草案与证据。若暂时无法获得此类专业审阅，应延后该重大协议修订，或将验收范围限制在无争议的文字修正内，并显式保留剩余疑虑。

### C 层 — 任务输出对比（仅当仍存在实际未决问题时）

仅在需要决定例如“移除材料是否会降低任务质量”或“新分支在真实代理中是否有效”时使用。它不是强制性试点。切勿将明显的事实或矛盾指令修正推迟到该层建成之后，也切勿仅凭 token 计数就宣称缩短后的版本更好。

未来的轻量级测试工具应当：

1. 在生成输出前先定义精确决策与特定于任务的验收量规。冻结测试用例与候选修订；切勿为了偏向某版本而修改预期。
2. 在相同模型、参数设置、工具、来源、输入与上下文预算下对比**当前技能与修订技能**。仅在测试技能的增值效用时才加入**无技能**对照。跨版本保持相同的工具/资源访问权限；若检索设计本身是预期变量，记录该例外并检查读取轨迹。
3. 将显式执行与技能发现分开：强制注入技能后得到好答案，并不证明已安装的代理会主动选择它。当发现机制在范围内时，使用实际已安装清单分别评估匹配及相邻不匹配的提示词。
4. 使用小型、刻意多样化的案例集：常规任务、缺失/歧义输入、相关可及性或准备度差异、恢复路径以及任何特定的安全/证据边界案例。使用虚构/最小化信息。为激活变更纳入看似合理的非触发案例。切勿强求每个技能使用相同数量的案例。
5. 保留模型/版本、参数、完整交付的提示词/资源版本、输出、错误、工具/资源读取记录、延迟以及可用时的实测输入/输出 token。对未修改版本进行重复运行有助于揭示正常波动；对接近的决策重复运行，而非将一次走运的输出视为决定性证据。
6. 对审阅者隐去版本身份并随机化对比顺序；通过交换部分子集检查位置/冗长偏好。使用特定于任务的锚点评估教育准确性、任务完成度、可用性、忠实度与能动性。单独报告严重违规并保留平局/不确定性。
7. 仅当证据支持所声称的收益且无实质性回归时才偏好某版本。对于重组任务，等效的任务质量加上更低的冗余上下文或更清晰的检索即已足够；不存在强制性的百分比缩减目标。报告计数与配对结果，而非从小样本中虚构统计显著性。

若日后自动裁判有用，应针对教育者审阅过的示例进行校准，检查一致性与重大假阴性，并人工复核分歧项。切勿将本库自身的 `panel-review` 分数或未经验证的 88 分门禁当作独立质量标准。若开始反复调优，请维护一个小型未见回归测试集；记录用于开发的案例，以便使基准过拟合可见。裁判的提示词与模型本身也是受版本控制的评估依赖。

### 最小化的未来案例/结果记录

以下是拟议字段，而非本规划任务创建的实际文件或测试工具。若 C 层获批，请从简单的 JSONL 与小型运行器起步，而非构建评估平台。建议位置：`evals/skill-quality/cases.jsonl`、`evals/skill-quality/README.md` 与 `scripts/evaluate-skill-quality.py`；仅在检查可用代理执行路径后再选择运行器接口。将生成的对话记录保存在指定的被忽略本地结果目录中，仅在单独授权时提交经审阅的摘要。

一条案例记录 `case_id`、`skill_id`、任务类别、修订版本、输入/上下文、交付模式、测试标准、预期属性、禁止结果、相关资源与来源出处。一条结果记录案例、候选/源文件哈希、实际客户端/模型/设置、交付内容、资源读取、输出/错误、可用时的执行时间/成本、审阅者身份、判断结论以及该案例是否在开发期间见过。增加 `execution_status`，以区分未运行、人工走查与实际执行。切勿在测试集或结果中放入凭据、真实学生计划或可识别的学习者记录。

### 此类评估能确立与不能确立什么

它可以确立某处源码矛盾已被消除、特定代理完成了既定任务，或在记录条件下某个候选版本更受青睐。它不能证明课堂学习收益、跨所有模型的普遍行为、诊断效度或在每所学校的安全实施。这些局限不应阻碍有益的指令改进。

## 4. 如何在不丢失专业知识的前提下优化长度

审阅测得 23 个正文超过 5,000 代理 token，50 个包含元数据的完整文件超过该水平，而仅有一个提取出的 MCP 提示词超过该水平。正文与 MCP 提示词的中位数分别为 3,895 与 1,118 token。计数使用 `tiktoken 0.14.0 / o200k_base`；它们并非 Claude token 计数或实测账单。长度是筛查信号，而非质量评分或严格的规范失败。

针对每个候选技能，绘制一张章节地图：核心执行规则、决策相关例外、简短示例、扩展示例、研究阐释、替代模板或重复解释。记录每个章节防止什么错误。移除真正的重复内容；在移出前先修正有缺陷的示例。将独特概念、判断所需的理由以及一个紧凑示例保留在工作流附近。

**核心必须保留：** 任务/范围、不可或缺的输入、重要区分、主要决策、必需的输出语义、恰当的例外、不确定性以及停止/恢复行为。**参考资料可存放：** 冗长对话记录、附加示例、研究阐释与可选组件细节。使用技能本地路径（如 `references/worked-examples.md` 或 `references/research-notes.md`），并配有明确的“何时读取……”指引。切勿仅仅为了拆分长指南而创建额外可发现的 `SKILL.md` 文件。

两项交付约束至关重要：

- 本地客户端有可能读取技能本地的参考资料，但完整文件夹必须一并流转。检查仓库外复制单个选定技能的场景；切勿在基本执行中引入对仓库根目录指南或兄弟技能的依赖。
- 当前的 MCP 适配器提取 Prompt/System Prompt；它不会自动提供周围的 Markdown 或新的参考文件。请将核心规则保留在提取出的文本内部。对于仅限源文件的组织变更，应力求完全保留提取后的提示词文本。若 MCP 提示词有意发生变更，须显式评估其行为增量。托管客户端无法读取的相对路径不是渐进式披露。

切勿仅为了达成 token 目标而构建参考资料服务系统。首先使用精炼的内联规则，并仅在生成资源可访问处移出面向人类的可选解释。如果某项提案确实需要新的运行时资源交付机制，请将该部分延后至单独界定范围的基础设施变更中。

对于 `dispositional-knowledge-assessment-designer`，首先厘清设计与实施工作负荷。组件选择可能很有帮助，但不能静默移除强制输出或更改必需输入。对组件的兼容解释与可选参考资料可独立推进；可选择输出的接口则需要明确的契约决策与向后兼容的默认值。对全部 20 个提示性重组候选应用同样的克制：“按原样保留”是一个有效的有据结论。

## 5. 受保护的其余部分与兼容性

| 保留项 | 验证方式 |
|---|---|
| 全部 165 个路径、名称与稳定 ID | 将清单与哈希同冻结基线比对；不扁平化、不重命名、不复制 old/v2 技能。 |
| 现有纳入/排除政策与具名研究 | 对照来源审阅变更后的主张；保留引用并区分修正与删除。不作泛化重写或自动降级证据评级。 |
| 现有输入、输出、可选默认值与调用意图 | 比对 schema 与生产方/消费方用法。保持 12 个仅显式调用技能为仅显式调用；不作为副作用扩大自动激活范围。 |
| 独特方法与教师/学习者判断 | 审阅常规成功案例及每条记录的 `preserve`/`mandatory_core` 条目。保留建设性挑战、反思性实践与原创框架。 |
| 规范源文件加注册表与 MCP 快照 | 从源文件重新生成；不维护第二套手动技能库。保留预期的 165 个提示词与 157 个工具（153 个技能工具加 4 个发现工具）。 |
| 当前审计证据与用户工作 | 保持原始审阅文件完整；另行记录新结果，切勿将所有未追踪文件一并扫入提交。 |

### 元数据规则与必要例外

`AGENTS.md` 要求精确保留前置元数据字段。因此默认实施范围仅修改 Markdown 正文内容，并保留完整的原始前置元数据字节。这比仅仅保留字段名称更加严格。

少数提案涉及受保护的值：间隔练习 `evidence_sources` 中的研究计数；`panel-review` 的发现描述；存在歧义的工作负荷元数据；缺乏支撑的证据标签；建议串联引用；任何拟议的输入/输出变更。后续实施简报必须显式授权其计划修正的精确字段/值作为有界替代。切勿推断普通编辑批准就允许这些变更。先准备好精确的拟议值与理由，使任何所需决策具体明确。切勿仅为了迎合校验器而重命名/删除字段或改变含义。

如果无需触及元数据即可连贯地完成正文修正，则先完成该部分。如果保留原元数据会维持矛盾，则将该项保持为待处理，而非宣称为已完成。切勿为了解决正文歧义而替换引入新的必需输入。当现有占位符未被使用时，优先在不改变 schema 的前提下澄清其用法；移除属于需要单独授权的契约变更。

## 6. 执行顺序与工作包

以下是可管理的实施工作包，并非强制要求拆分为独立的 PR、新任务或工作代理会话。一名实施者可以连续完成多个连贯的工作包，每完成一个并关闭后再开始下一个。精确成员与验收案例如下所示；附录 A 提供了逐技能增量与证据。若审阅负担过重，可将工作包进一步细分。

### 第 0 阶段 — 在编辑源文件前冻结与准备

1. 确认仓库、远程仓库、当前修订版本与工作区树。协调处理与检查基线之间的漂移；切勿自动执行 pull/reset/stash。当前的审计文件属于未追踪的本地产物，并非丢弃或发布它们的许可。
2. 当实施/版本控制获批时，使用清晰的本地标签或不可变提交引用在 Git 中保留已验收基线；记录来自证据 JSON 的源文件哈希。本地标签不会自动推送。编辑前保护任何后续的用户修改。
3. 建立明确的变更文件列表与受保护其余部分清单。通读完整候选文件、来源证据与直接契约；保留、收窄或撤回每项发现。无需在第一次窄范围修正前重读全部 165 个未修改文件。
4. 解决第一个工作包所需的精确元数据/契约例外。当某个无关例外尚待决策时，继续推进独立的纯正文工作。
5. 从干净构建记录实际现有的测试基线。过往审计结果是证据，而非永久有效的绿灯证书。在实施环境中首次执行前须检查现有脚本。不得为了采集基线而变更任何托管端点或安装位置。

**完成标志：** 可复现的修订版/哈希引用、明确的工作包范围、已知的基线测试状态以及无未解释的源文件漂移。第 0 阶段不制定任何新的教育政策。

### 第 1 阶段 — 针对性内容修正

默认顺序为 Q1–Q10。Q1 优先处理具有重大影响的支持，Q2–Q3 防止虚假证据与困住学习者的互动，随后依次处理一致性、研究与实用性。机械性事实修正可在独立时提前推进；切勿让待定的专家决策阻塞无关工作。每个工作包结束时均须附带源文件 diff、适用检查、审阅结论以及（若获验收）重新生成的产物。

#### Q1 — 支持、披露与安全保护（4 个技能）

**精确源码范围：**

- [wellbeing-motivation-agency/trauma-informed-practice-designer](../../skills/wellbeing-motivation-agency/trauma-informed-practice-designer/SKILL.md)
- [wellbeing-motivation-agency/restorative-practice-protocol-designer](../../skills/wellbeing-motivation-agency/restorative-practice-protocol-designer/SKILL.md)
- [wellbeing-motivation-agency/ruler-emotional-literacy-sequence](../../skills/wellbeing-motivation-agency/ruler-emotional-literacy-sequence/SKILL.md)
- [original-frameworks/inclusive-design-orchestrator](../../skills/original-frameworks/inclusive-design-orchestrator/SKILL.md)

**允许增量：** 将适用性、既有支持、隐私选择以及即时安全/本地预案边界置于重大建议之前。保留冷静、包容的教育实践。切勿虚构通用的临床或法律协议。

**验收示例：** 检查既有支持计划、紧急无障碍需求、持续针对性嘲弄、拒绝披露情绪以及紧迫危险披露。常规课堂支持保持可用；示例遵循核心规则。具有重大影响的回应措辞在被描述为实质性验收前，需要经过合格人类审阅。

#### Q2 — 诚实的学习者证据（3 个技能）

**精确源码范围：**

- [student-learning/ai-claim-checker](../../skills/student-learning/ai-claim-checker/SKILL.md)
- [student-learning/confidence-calibration-check](../../skills/student-learning/confidence-calibration-check/SKILL.md)
- [student-learning/weekly-agency-review](../../skills/student-learning/weekly-agency-review/SKILL.md)

**允许增量：** 区分观察、自我报告、估算、假设与已核实事实；保留核查计划练习与反思目的。

**验收示例：** 准确的 AI 内容可获得有理有据的认同；拟议的核查不被报告为已执行。缺失的信心值保持未知或向学生询问。凭记忆回顾的一周被标注为估算；不可比的任务不能确立因果依赖或进步。不暗示自动记录持久化。

#### Q3 — 有限挑战与可及的恢复路径（5 个技能）

**精确源码范围：**

- [student-learning/productive-failure-protocol](../../skills/student-learning/productive-failure-protocol/SKILL.md)
- [student-learning/retrieve-first-gate](../../skills/student-learning/retrieve-first-gate/SKILL.md)
- [student-learning/explain-first-interrogator](../../skills/student-learning/explain-first-interrogator/SKILL.md)
- [student-learning/progressive-hint-ladder](../../skills/student-learning/progressive-hint-ladder/SKILL.md)
- [student-learning/unassisted-evidence-checkpoint](../../skills/student-learning/unassisted-evidence-checkpoint/SKILL.md)

**允许增量：** 保留建设性挣扎、提取、自我解释、分级提示与诚实的无辅助证据。增加恰当的有限恢复、可及性、暂停与停止路径。

**验收示例：** 审阅首次正确回应、缺失先备知识、替代回应方式、多次不成功尝试以及停止请求。学习者可以获得基础支持或退出而不被给予虚假通过。不单凭挫败感诊断为最佳难度。精确尝试次数保持为可调节的启发式规则。

#### Q4 — 一致的学习工作流与示例（5 个技能）

**精确源码范围：**

- [student-learning/fading-manager](../../skills/student-learning/fading-manager/SKILL.md)
- [student-learning/stuck-and-error-diagnosis-coach](../../skills/student-learning/stuck-and-error-diagnosis-coach/SKILL.md)
- [student-learning/transfer-bridge](../../skills/student-learning/transfer-bridge/SKILL.md)
- [student-learning/srl-session-wrapper](../../skills/student-learning/srl-session-wrapper/SKILL.md)
- [student-learning/teach-back-evaluator](../../skills/student-learning/teach-back-evaluator/SKILL.md)

**允许增量：** 对齐规则、证据标签、示例、占位符、阶段过渡与反馈。修正数学/构念错误，同时保留预期的辅导方法。

**验收示例：** 三次会话撤架规则与示例记录一致；生产方/消费方标签匹配。解决 2.5 对比 2 的示例与无时间运动学案例。迁移检查所声称的共享机制并标注辅助情况。中期/结束 SRL 阶段在缺少计时器集成时恢复缺失的目标上下文。费曼回教结果与证据匹配，并允许在存在未解决缺口时结束。

#### Q5 — 课程与来源交接（3 个技能）

**精确源码范围：**

- [curriculum-alignment/developmental-band-translator](../../skills/curriculum-alignment/developmental-band-translator/SKILL.md)
- [curriculum-alignment/kud-chart-author](../../skills/curriculum-alignment/kud-chart-author/SKILL.md)
- [professional-learning/competency-framework-translator](../../skills/professional-learning/competency-framework-translator/SKILL.md)

**允许增量：** 使分支优先级与数据交接连贯；区分精确来源文本与解读。

**验收示例：** 审阅年龄覆盖、缺少年龄与扁平框架案例。原始课程文档在进入需要已拆解 JSON 的消费方前先完成拆解。缺失官方措辞时产出显式标注的解读或来源请求，绝不捏造引文。保留现有标识符与不确定性标志。

#### Q6 — 研究精确性与提取一致性（4 个技能）

**精确源码范围：**

- [memory-learning-science/retrieval-practice-generator](../../skills/memory-learning-science/retrieval-practice-generator/SKILL.md)
- [memory-learning-science/spaced-practice-scheduler](../../skills/memory-learning-science/spaced-practice-scheduler/SKILL.md)
- [curriculum-assessment/differentiation-adapter](../../skills/curriculum-assessment/differentiation-adapter/SKILL.md)
- [original-frameworks/developmental-band-system-designer](../../skills/original-frameworks/developmental-band-system-designer/SKILL.md)

**允许增量：** 修正窄范围证据主张与矛盾；保留已被接纳的教育方法与原创框架身份。

**验收示例：** 初学者识别例外与自检项一致；所教来源核查出现在活跃提示词中。核实 Cepeda 来源/计数，区分示例时间表与经证实的最优解，并限定遗忘泛化表述。准确指明 CAST 版本。混龄支持研究不被称作整套原创架构的验证。

#### Q7 — 能动性、动机与可行支持（5 个技能）

**精确源码范围：**

- [wellbeing-motivation-agency/agency-scaffold-generator](../../skills/wellbeing-motivation-agency/agency-scaffold-generator/SKILL.md)
- [wellbeing-motivation-agency/implementation-intention-designer](../../skills/wellbeing-motivation-agency/implementation-intention-designer/SKILL.md)
- [wellbeing-motivation-agency/flow-state-condition-designer](../../skills/wellbeing-motivation-agency/flow-state-condition-designer/SKILL.md)
- [wellbeing-motivation-agency/motivation-diagnostic-task-redesign](../../skills/wellbeing-motivation-agency/motivation-diagnostic-task-redesign/SKILL.md)
- [wellbeing-motivation-agency/self-efficacy-builder-sequence](../../skills/wellbeing-motivation-agency/self-efficacy-builder-sequence/SKILL.md)

**允许增量：** 结合学习者视角与观察到的可及性/先备需求；使进阶、线索与恢复无需依赖缺乏支撑的心理学结论即可使用。

**验收示例：** 审阅拒绝、可及性障碍、重复错误、学生认可的目标与内部线索。保留学习目标、必要基础工作与辅助工具。切勿仅凭任务设计推断动机、承诺心流/成功，或将困难等同于学习证明。启发式阈值须明确标注且可调节。

#### Q8 — 福祉设计与适度主张（4 个技能）

**精确源码范围：**

- [wellbeing-motivation-agency/awe-wonder-experience-designer](../../skills/wellbeing-motivation-agency/awe-wonder-experience-designer/SKILL.md)
- [wellbeing-motivation-agency/belonging-classroom-culture-designer](../../skills/wellbeing-motivation-agency/belonging-classroom-culture-designer/SKILL.md)
- [wellbeing-motivation-agency/perma-based-lesson-designer](../../skills/wellbeing-motivation-agency/perma-based-lesson-designer/SKILL.md)
- [wellbeing-motivation-agency/wellbeing-learning-connection-mapper](../../skills/wellbeing-motivation-agency/wellbeing-learning-connection-mapper/SKILL.md)

**允许增量：** 保留有用的规划视角与课堂实践；移除强制性情绪反应、诊断捷径与缺乏支撑的本地影响主张。

**验收示例：** 用户可拒绝个人披露；安静/眼神接触属于模糊信号。提供可及替代方案并保持学习目标可见。PERMA 映射可留空未涉及的要素。证据图谱保留未知/零效果/负效果发现，标注虚构假设，且不迁移无关效应量或捏造本地趋势。

#### Q9 — MCP 界面上的关键局限（2 个技能）

**精确源码范围：**

- [historical-thinking/historical-document-set-curator](../../skills/historical-thinking/historical-document-set-curator/SKILL.md)
- [systems-thinking/ladder-of-inference-reflection](../../skills/systems-thinking/ladder-of-inference-reflection/SKILL.md)

**允许增量：** 将精炼的来源出处/适用性限制置于实际提取出的提示词内部；保持完整支持性解释可访问。

**验收示例：** 不可用/未核实的历史文献被标注为建议，而非已提供的证据。近期的重大伤害或权力不对等在反思前触发恰当的适用性边界。同时检查完整文件与打包提示词；仅在“已知局限”中保留警示对于本工作包是不够的。

#### Q10 — 大型原创工作流与清晰范围（2 个技能）

**精确源码范围：**

- [original-frameworks/dispositional-knowledge-assessment-designer](../../skills/original-frameworks/dispositional-knowledge-assessment-designer/SKILL.md)
- [professional-learning/panel-review](../../skills/professional-learning/panel-review/SKILL.md)

**允许增量：** 在前端厘清工作负荷、预期用途与启发式状态；保留独特的多组件评估与有用审阅视角。仅在修正已识别问题后才考虑组织调整。

**验收示例：** 区分设计时间与实施工作负荷；保留观察、多方知情人判断与可选照护者参与。现有输出契约保持可用。评审小组范围在正文中可见；阈值属于实践启发式规则，模拟角色并非独立评分者。任何描述/元数据编辑或组件选择 schema 变更在实施前均需获得专门授权的例外。

### 第 2 阶段 — 选择性重组

在任何重叠技能的内容修正完成后开始。以下 20 个技能存在组织优化机会，而非已证实的缺陷。编辑每个技能前，先选定要移出的章节、证明其新的可访问性并说明收益。若仅移动周边阐释，则保留当前活跃提示词。三个长修订技能——倾向性评价、`panel-review` 与 `kud-chart-author`——在其原 Q 工作包或后续有界跟进中检查，切勿产生归属权冲突。

| 工作包 | 范围 | 体量与预期处理 |
|---|---|---|
| R1 | 原创框架指南 | 4 个技能；保留核心与正确示例，考虑技能本地的可选参考资料。精确路径与实测体量见附录 B。 |
| R2 | 课程设计指南 | 5 个技能；保留核心与正确示例，考虑技能本地的可选参考资料。精确路径与实测体量见附录 B。 |
| R3 | 专业学习指南 | 3 个技能；保留核心与正确示例，考虑技能本地的可选参考资料。精确路径与实测体量见附录 B。 |
| R4 | 历史探究与工作周期指南 | 4 个技能；保留核心与正确示例，考虑技能本地的可选参考资料。精确路径与实测体量见附录 B。 |
| R5 | AI 学习科学指南 | 4 个技能；保留核心与正确示例，考虑技能本地的可选参考资料。精确路径与实测体量见附录 B。 |

**完成标志：** 每个候选均获得已验收的重组方案或明确的“不予修改”理由；所有强制性指令保持可用；移出材料得以保留并链接；预期分发路径正常工作。无强制性 token 缩减目标。已验收的“不予修改”决策不计为已编辑技能。

### 第 3 阶段 — 质量记录与贡献者指南

当该方法经受住实际已验收编辑的检验后，在 `CONTRIBUTING.md` 中补充精炼指引，并在有用时建立聚焦的 `docs/SKILL_QUALITY.md`；采用链接而非重复完整量规。阐明八项标准、任务类别区分、证据对比启发式规则、源文件/核心一致性、相关处的数据最小化以及必需的变更理由。保留现有纳入/排除政策。在获得授权前，切勿将本提案宣称为项目正式政策。

维护一份紧凑的变更台账，包含技能 ID、工作包、基线/候选哈希、发现与证据、保留行为、变更界面、元数据例外（如有）、实际执行的检查、审阅结果与剩余局限。建议未来位置：`docs/audits/skill-quality-change-log.md`。保留原始矩阵作为历史审阅；创建更新的处置记录，而非静默让旧的拟议判断看起来像已验收的修复。状态值可为 `planned`、`in review`、`accepted`、`withdrawn`、`deferred`、`reverted`。

仅针对经证实可维护的检查添加自动化。切勿将每项编辑偏好都编码为测试、创建第二套评分质量标准，或要求每次贡献都调用模型。在价值与运行成本确立前，C 层可继续作为可选本地工作流。

### 第 4 阶段 — 集成验收与单独授权的分发

在切实可行处验证组合内容、生成视图以及常规已安装客户端行为，保留精确客户端版本并清晰标明未测试的客户端。本地包检查不证明托管服务已更新。Claude 本地完整文件交付、Codex 本地发现与 MCP 提取提示词交付属于不同界面；单一冒烟测试成功不能认证全部三者。

若安装/更新真实用户的客户端超出授权范围，请使用隔离的测试位置。记录哪些功能可发现、可显式调用、可读且边界正确，以及哪些无法测试。切勿为了收集证据而覆盖现有安装或凭据。切勿将文档预期称为已验证结果。

仅在获得明确发布授权后，才可发布已验收的提交/标签或更新分发包。部署需要其自身独立授权；计划批准、测试通过或推送源码提交均不授权托管构建/部署。在实施时重新核查相关的客户端/安全事实，而非照抄旧的通告状态。

## 7. 验证命令与证据契约

以下命令为**计划中的实施检查**，并非为创建本计划而全部执行过的命令。在修改行为的工作及依赖/脚本检查后，从指定仓库目录运行。需要时对产生生成输出的检查使用临时隔离副本；切勿让测试更改未经批准的线上服务。若身份已知可复用现有依赖；安装前检查安装钩子。切勿盲目运行远程安装器命令或 `npm audit fix --force`。

```bash
# 从仓库根目录开始；先重新生成已验收的源文件视图。
python3 scripts/generate-registry.py
cd mcp-server
npm run bundle-skills
npm run build
npm test
cd ..

# 校验重新生成的源文件视图，并在不含托管冒烟测试的情况下运行根目录测试。
python3 scripts/validate-skills.py
python3 scripts/validate-registry.py
env -u HOSTED_MCP_BASE_URL npm test
```

针对重新生成的候选版本运行检查，而非误将刻意保持旧状态的编辑前快照当成回归。检查根目录与 MCP 测试配置/环境，使托管测试在未单独授权时保持跳过。`build` 必须先于 MCP 测试运行，以免混淆过时的被忽略 `dist/` 输出与当前源码行为。记录通过/失败/跳过计数及原因；切勿宣称未执行的检查已通过。在一个工作包的最后一次相关变更后运行一次完整的适用测试套件；仅在后续变更或存在未决疑虑时重复。纯计划/贡献者文档编辑需要轻量级一致性/链接检查，而非模型基准测试。

额外的工作包检查：

- 清单保持 165 个唯一技能身份；108 个保留文件无意外变更。比对原始前置元数据与语义契约；任何例外必须与其精确获批范围匹配。
- 将生成的注册表和打包产物与规范源文件比对；妥善解释注册表生成时间戳，而非忽略语义差异。除非经单独批准的行为变更，否则预期基线保持 165 个 MCP 提示词、157 个工具和 12 个仅显式调用技能。
- 对于已变更的技能，检查实际提取的 MCP 提示词与本地完整文件内容；核心安全边界、必要区分、默认值与输出含义保持一致。在其他位置保留完整正文文本不能弥补核心规则的丢失。
- 检查所有新增/移动的相对路径、技能本地复制、无路径穿越/包外依赖、来源/引用保留及示例准确性。将资源文件纳入任何后续获批的提交/分发包中。
- 官方 Agent Skills 校验器结果属于标准轨道。切勿期望仅针对质量的正文编辑就能使当前的富前置元数据源文件配置文件通过严格参考校验器。若实施了获批的便携版导出，请对该导出单独运行固定版本的参考校验器。将项目校验与官方校验记录为不同的结果。

对于每个工作包，交付通俗易懂的结果说明、精确变更路径、修改前后理由、受保护行为、实际完成的测试与审阅、未决问题以及回滚单元。将生成输出与对应的源码修订版本保持一致。若必需的源文件检查或专家审阅尚未完成，切勿宣称“全绿通过”。

## 8. 与标准、安装及安全工作的关系

内容质量与开放标准打包彼此关联但相互独立。保留领域结构、规范技能、注册表、Claude/Codex 插件适配器以及有用处的 MCP 服务。切勿为了看起来更符合标准而扁平化或重写技能。现有的[迁移计划](agent-skills-migration-plan.md)包含精确的基础设施发现与拟议测试；执行前刷新其时效性事实。

| 现有基础设施提案 | 与本内容计划的关系 |
|---|---|
| 将技能前置元数据解析限制为安全 YAML；更新存在漏洞的依赖与合理输入边界 | 保持在单独经审阅的变更中。这是将任意新提交的技能文件视为可安全执行的前提；源码细读与规划可独立继续。切勿将内容回滚与恢复不安全解析混为一谈。 |
| 修正 Codex 市场路径/安装指南与仅显式调用策略 | 有助于安装/发现。它不改变教育写作，也不证明在所有客户端中的激活。在隔离环境中测试；切勿静默更改已安装客户端。 |
| 在保留富源元数据的同时记录或生成严格便携配置文件 | 潜在的标准收益，并非教育修正的前置条件。任何导出都必须保留身份、schema、参考资料与核心正文指令；切勿手动维护 165 份重复副本。 |
| 修复模板替换与包/构建新鲜度 | 独立的功能可靠性工作。保留必需输入/输出并使用现有回归契约。 |
| 证据索引引用修正、可选串联与证据标签定义 | 与 Q6/Q10 及受影响记录协调归属权；每处修正只做一次。当该文档变更获批时，依据一手文献来源修正 `docs/EVIDENCE.md` 的 Woloshyn 引用。缺失的建议串联条目属于提示性建议，除非工作流实际依赖它们。 |

切勿要求所有基础设施建议都完成后才可验收稳健的源文件修正。反之，内容改进也不证明悬而未决的解析器、依赖或安装问题已解决。为每条轨道维护独立的验收与发布回执。

## 9. 版本、保留与回滚

**默认建议：** 在原位改进现有技能文件，在 Git 中保留旧版本，并保持 ID/路径稳定。切勿让用户在每个技能的两个活跃版本之间做选择。历史版本属于不可变修订版与发布标签，并附带解释有意义变更的简短更新日志。

在未来获批的编辑前，记录基线修订版与源文件哈希；验收后，保留候选修订版/哈希、理由、测试与资源。仓库级发布版本控制应遵循现有项目约定（在实施时核查）。切勿虚构开放标准版本要求或静默递增受保护的逐技能元数据。即使不需要新身份标识，内容修正也可以在行为上具有重要意义。

显式分类变更：

- **兼容性修正：** 同一任务与契约内更准确的主张/示例、一致的分支、更清晰的安全边界或可选解释。路径/ID 稳定；记录有意义的变更。
- **兼容性组织：** 带有核心规则依然可用且输入/输出不变的可选参考文件。保留完整文件夹分发与独立行为。
- **潜在破坏性变更：** 新的必需输入、移除输出、在无消费方处理的情况下改变状态词汇、实质性不同的目标受众/教学法，或不可访问的新依赖。针对该变更集暂停，等待具体的契约决策。适当时优先采用向后兼容的适配器/默认值；只有真正不同的任务才值得赋予新的技能身份。

**当获准提交时**，使用小型逻辑提交，将源文件连同重新生成的注册表/打包产物一并提交，并将安全变更分开。这是一个包含未追踪产物的审计工作区树；切勿使用 `git add -A`、破坏性 reset 或一刀切清理作为保留策略。切勿自动推送本地标签、归档副本或文档。

**回滚顺序：** 识别失败的已验收工作包及其下游依赖；保留当前用户工作；回退该工作包的源/参考资料变更并从恢复后的源文件重新生成注册表/打包产物；运行相关检查；记录已回退状态与原因。若后续工作包依赖它，按逆向依赖顺序有意识地调整或回退它们。保留独立的安全修复。避免回退整份旧的生成快照，以免覆盖后续已验收的技能。若单独授权过托管部署，该部署需要明确的运维回滚流程与授权；仅回退源码不能证明线上服务已改变。

## 10. 归属权、工作量与停止条件

默认每次使用一名实施负责人，配以有界的独立审阅。向实施者提供精确的修订版本、允许修改的文件、受保护其余部分、发现、验收示例与停止条件；无需继承整个对话。保持顺序与集成负责人明确。仅当预期节省的时间超过协调成本时，才并行化真正独立的只读审阅或隔离工作包；切勿让两名工作人员同时编辑同一候选文件、打包产物或生成注册表。

这项工作不是 57 次全面重写：而是 37 个针对性审阅/修正候选外加 20 个可选组织决策。按变更的主张、工作流分支、接口与审阅需求评估工作量：

| 工作类型 | 相对工作量 | 主要不确定性 |
|---|---|---|
| 引用/措辞/示例修正 | 小 | 定位并核查精确的一手证据、与受保护元数据的重叠。 |
| 分支、交接或实时互动修正 | 小至中 | 相关消费方、诚实状态标签与可及的恢复路径。 |
| 重大支持/安全保护指导 | 中，依赖专家 | 合格审阅与本地预案边界；切勿用自信的泛泛建议取而代之。 |
| 长指南组织 | 中；可选 | 保留有用上下文、参考资料可及性与实际收益。 |
| 模型对比运行器或运行时资源交付 | 单独界定范围 | 代理执行接口、预算、校准与维护负担。 |

切勿仅凭文件数量就承诺数天的迁移工期。从已完成的工作包中记录实际活跃编辑/审阅时间、返工与测试时间，然后更新剩余估算。等待专家输入不同于编码时间。现有的包标准修复有其自身的计划与估算；切勿把所有事情揉进一个数字里而人为夸大教育工作量。

仅当受影响变更集需要未批准的 schema/元数据变更、未决的教育学含义决策、重大建议缺少合格审阅、真实学习者数据、付费 API 预算、实时客户端变更、外部发布或部署时，才暂停该受影响部分。先准备好精确的拟议变更及其后果，再请求所需的最小决策。继续推进无关的已授权工作。切勿将提案标记为创始人决策，或将待定检查标记为已完成。

### 即用型实施简报模板

对于每个获批的工作包，交接内容应包含：

- **预期成果：** 解决具名发现，保留其余方法。
- **基线：** 精确检出/修订版与源文件哈希；当前工作区树说明。
- **允许增量：** 工作包的源路径、获批元数据例外、所需的技能本地参考资料及生成的注册表/打包产物。无无关清理。
- **受保护其余部分：** ID、路径、schema/默认值、引用、调用意图、实践者原创状态以及列出的方法/安全边界。
- **证据：** 相关的附录 A 条目、完整源码记录以及针对争议主张的一手来源直接段落。
- **验收：** 工作包示例加上适用的第 7 节检查与独立审阅；区分人工审阅与实际执行。
- **停止条件：** 未决的教学法/接口含义或重大权威性问题；保留具体候选并继续推进范围内的无关工作。
- **收尾：** 已验收/延后/撤回/回退处置、变更文件、检查计数、剩余局限、回滚引用与实际工作量。若委派执行，记录工作代理数/峰值、继承历史例外、模型组合、首次通过率、返工及可用用量遥测。

## 11. 完成标准与刻意排除的工作

当每项拟议修订均拥有有据可依的处置结论、已验收变更均经过检查与审阅、组织候选均得出有理有据的结论、生成视图保持一致、受保护技能/契约完好无损，且未决问题与分发状态均已清晰记录时，本方案即告完成。完成并不意味着每条建议都必须实施、每个客户端都必须获得认证，或每个技能都必须变短。

保留有用的教育技能库、丰富元数据、原创方法、既有纳入政策与多种交付路径。避免批量重写、一刀切缩短、武断评分、165 个重复的 v2 目录、自动评级降级、为了图方便而新增必需输入、强制性研究试点、模型裁判走过场以及在没有已证实问题的情况下更改架构。让每一项获批编辑都凭借具体改进赢得其位置。

## 附录 A — 精确修订队列、变更内容与源码证据

以下条目采用了先前审阅的结构化记录，并将每项修订唯一分配给一个主工作包。它们目前仍为提案。在独立计划审阅期间，十二条保留声明得到了澄清，因为早期提取的片段不完整或包含了正在被修正的错误规则。下方完整的保留声明与明确允许的修正取代了那些片段，用于指导未来实施；历史审阅证据保持完整。基线行号指向被检查的修订版本；编辑前请重新定位实际段落。完整 JSON 保留了审阅深度、全部八项判断、源文件哈希与附加证据。通用的强制核心条目只是起点，并非完整性证明：请从完整文件中映射实际决策与例外。第 5 节的元数据保护依然适用。

### Q1 — 支持、披露与安全保护

#### `wellbeing-motivation-agency/trauma-informed-practice-designer`

**文件：** [skills/wellbeing-motivation-agency/trauma-informed-practice-designer/SKILL.md](../../skills/wellbeing-motivation-agency/trauma-informed-practice-designer/SKILL.md)。**审阅优先级：** high。**计划状态：** 尚未实施。

**拟议修正：** 将因果/神经科学确定性表述替换为可观察需求与合理解释。将即时危险/披露安全保护及既有个人/应急预案置于首位；避免通用的退出/等待/无要求规则。区分普遍支持性实践与心理治疗及诊断；要求由合格人类审阅具有重大影响的回应协议。

**保留：** 绝不诱导创伤史倾诉；教师不充当治疗师；可预测的常规流程；尊严；全班安全；富有同情心的边界。

**基线证据：** `skills/wellbeing-motivation-agency/trauma-informed-practice-designer/SKILL.md:146`、`215`、`225`、`250`、`78`、`128`、`140`、`254`、`101`、`102`。其余证据与提取/核心检查见完整记录。

#### `wellbeing-motivation-agency/restorative-practice-protocol-designer`

**文件：** [skills/wellbeing-motivation-agency/restorative-practice-protocol-designer/SKILL.md](../../skills/wellbeing-motivation-agency/restorative-practice-protocol-designer/SKILL.md)。**审阅优先级：** high。**计划状态：** 尚未实施。

**拟议修正：** 将权力不对等/安全保护/同意筛查移至活跃第一步。将仅按严重程度选择方案替换为准备度与受保护的自愿替代方案。修正示例中的持续嘲弄案例，不再假定必须召开面对面会议；增加防止复发/报复的后续保护。限定对比效应主张。

**保留：** 会前准备；受伤害方拥有发声权；具体且由参与者自主认同的协议；后续跟进；实用回退方案以及与校规后果的共存。

**基线证据：** `skills/wellbeing-motivation-agency/restorative-practice-protocol-designer/SKILL.md:109`、`138`、`192`、`200`、`301`、`77`、`81`、`303`、`220`、`222`。其余证据与提取/核心检查见完整记录。

#### `wellbeing-motivation-agency/ruler-emotional-literacy-sequence`

**文件：** [skills/wellbeing-motivation-agency/ruler-emotional-literacy-sequence/SKILL.md](../../skills/wellbeing-motivation-agency/ruler-emotional-literacy-sequence/SKILL.md)。**审阅优先级：** high。**计划状态：** 尚未实施。

**拟议修正：** 将短序列标注为区别于经过评估的完整 RULER 实施的改编版；检查教师培训/材料授权，而非暗示项目保真度。默认将情绪/原因设为私密或虚构，并可选择跳过；不从外表推断内部状态。将治疗性保证与通用呼吸脚本替换为选择权与转介。

**保留：** 教师先行示范；精确情绪词汇；调节而非压抑；全校范围与临床局限性；持续性日常练习。

**基线证据：** `skills/wellbeing-motivation-agency/ruler-emotional-literacy-sequence/SKILL.md:110`、`111`、`170`、`239`、`15`、`75`、`196`、`206`、`215`、`194`。其余证据与提取/核心检查见完整记录。

#### `original-frameworks/inclusive-design-orchestrator`

**文件：** [skills/original-frameworks/inclusive-design-orchestrator/SKILL.md](../../skills/original-frameworks/inclusive-design-orchestrator/SKILL.md)。**审阅优先级：** high。**计划状态：** 尚未实施。

**拟议修正：** 在将通用设计保留为规划优先级的同时，并行尊重既有的支持/紧急无障碍需求；标记专家介入，同时不暂停常规包容性支持。

**保留：** 使路径选择可见、通过通用设计主动减少障碍、有用的针对性/个别化选项与专家协作。将通用设计作为规划优先级与既有及紧急个别化无障碍支持并存保留。

**明确允许的修正：** 当强制性的顺序层级会延误既有或紧急支持时，可修改该层级。此例外具有实质性且有意为之：通用优先规划不得意味着在耗尽其他层级前扣留恰当支持。

**基线证据：** `skills/original-frameworks/inclusive-design-orchestrator/SKILL.md:124`、`128`、`202`、`239`、`246`、`188`、`283`。其余证据与提取/核心检查见完整记录。

### Q2 — 诚实的学习者证据

#### `student-learning/ai-claim-checker`

**文件：** [skills/student-learning/ai-claim-checker/SKILL.md](../../skills/student-learning/ai-claim-checker/SKILL.md)。**审阅优先级：** high。**计划状态：** 尚未实施。

**拟议修正：** 保留三步核查计划练习。允许有理有据的认同/未发现问题，移除仅因认同就诊断为警觉度低的做法，并将拟议核查与已执行核查/错误确认分开。不将查阅外部信源设为每次使用的新强制任务。

**保留：** 聚焦具体主张；独立学科信源；超越泛泛搜索的方法；初学者支架。

**基线证据：** `skills/student-learning/ai-claim-checker/SKILL.md:96`、`119`、`157`、`66`、`102`、`139`、`127`、`153`、`100`、`141`。其余证据与提取/核心检查见完整记录。

#### `student-learning/confidence-calibration-check`

**文件：** [skills/student-learning/confidence-calibration-check/SKILL.md](../../skills/student-learning/confidence-calibration-check/SKILL.md)。**审阅优先级：** high。**计划状态：** 尚未实施。

**拟议修正：** 绝不捏造学习者信心值；增加“未采集”与可选口头评级。将问题锚定到具体的前瞻性任务，并跨时间对比可比任务的表现。将模式标签视为暂定结论，允许学习者质疑评估。

**保留：** 同时关注信心不足与过度自信；下一步行动；坦诚说明量表与准确度局限性。

**基线证据：** `skills/student-learning/confidence-calibration-check/SKILL.md:96`、`111`、`135`、`139`、`64`、`114`、`214`、`216`、`145`、`151`。其余证据与提取/核心检查见完整记录。

#### `student-learning/weekly-agency-review`

**文件：** [skills/student-learning/weekly-agency-review/SKILL.md](../../skills/student-learning/weekly-agency-review/SKILL.md)。**审阅优先级：** medium。**计划状态：** 尚未实施。

**拟议修正：** 区分观察记录与回忆估算；增加最低限度的可比性/来源检查以及暂定性替代解释。补充简短的数据处理边界、无自动持久化，以及学习者对保留摘要的审阅权。

**保留：** 先解读后分析；具体策略而非空洞努力目标；首次复盘回退方案；按累积证据调整节奏。

**基线证据：** `skills/student-learning/weekly-agency-review/SKILL.md:82`、`91`、`155`、`117`、`123`、`125`、`239`、`35`、`237`、`71`。其余证据与提取/核心检查见完整记录。

### Q3 — 有限挑战与可及的恢复路径

#### `student-learning/productive-failure-protocol`

**文件：** [skills/student-learning/productive-failure-protocol/SKILL.md](../../skills/student-learning/productive-failure-protocol/SKILL.md)。**审阅优先级：** high。**计划状态：** 尚未实施。

**拟议修正：** 保留建设性探索、对比方法与关联式巩固讲解。使尝试次数/时间上限可由教师/学习者调节，为缺乏先备知识或感到痛苦的情况提供有限退出路径，且在未经来源核查前不宣称“两次尝试”精确规则已被研究证实。首次正确后的对比案例分析可保持可选。

**保留：** 显式的巩固依赖；真实方法对比；概念/迁移适用范围；诚实的时间成本说明。

**基线证据：** `skills/student-learning/productive-failure-protocol/SKILL.md:77`、`84`、`110`、`132`、`66`、`136`、`216`、`129`、`135`、`148`。其余证据与提取/核心检查见完整记录。

#### `student-learning/retrieve-first-gate`

**文件：** [skills/student-learning/retrieve-first-gate/SKILL.md](../../skills/student-learning/retrieve-first-gate/SKILL.md)。**审阅优先级：** medium。**计划状态：** 尚未实施。

**拟议修正：** 将激活范围限定为复习此前接触过的材料；增加初学者/可及回应/直接教学与停止路径。使提示词中不确定的 AI 评分可被质疑，避免对疑似粘贴内容做确定性判定，并与消费方技能对齐证据术语。

**保留：** 先回忆再泛泛重教；准确/缺失/误解图谱；热启动支架；非正式评估警示。

**基线证据：** `skills/student-learning/retrieve-first-gate/SKILL.md:72`、`108`、`118`、`151`、`63`、`67`、`83`、`188`、`76`、`126`。其余证据与提取/核心检查见完整记录。

#### `student-learning/explain-first-interrogator`

**文件：** [skills/student-learning/explain-first-interrogator/SKILL.md](../../skills/student-learning/explain-first-interrogator/SKILL.md)。**审阅优先级：** medium。**计划状态：** 尚未实施。

**拟议修正：** 明确在达到追问上限或缺乏先备知识后何时适合进行简短解释/直接教学。使示例与“不代写”规则对齐，允许替代解释格式，并限定从研究到脚本的外推。

**保留：** 具体而非泛泛的提问；先肯定优势再指出缺口；三轮上限；学习者主导的综合。

**基线证据：** `skills/student-learning/explain-first-interrogator/SKILL.md:63`、`101`、`115`、`175`、`23`、`67`、`131`、`107`、`197`、`195`。其余证据与提取/核心检查见完整记录。

#### `student-learning/progressive-hint-ladder`

**文件：** [skills/student-learning/progressive-hint-ladder/SKILL.md](../../skills/student-learning/progressive-hint-ladder/SKILL.md)。**审阅优先级：** medium。**计划状态：** 尚未实施。

**拟议修正：** 保留六级最小必要辅助与基础回退。澄清诊断/起始层级措辞，将“挫败感意味着难度恰当”的推断替换为中立的准备度/可及性检查，并允许有界的暂停/切换回应方式。不将其全面替换为直接给答案。

**保留：** 分级最小必要帮助；升级前先反思；不因使用高层级提示而羞辱；基础回退。

**基线证据：** `skills/student-learning/progressive-hint-ladder/SKILL.md:76`、`87`、`93`、`67`、`147`、`149`、`84`、`128`、`247`、`143`。其余证据与提取/核心检查见完整记录。

#### `student-learning/unassisted-evidence-checkpoint`

**文件：** [skills/student-learning/unassisted-evidence-checkpoint/SKILL.md](../../skills/student-learning/unassisted-evidence-checkpoint/SKILL.md)。**审阅优先级：** medium。**计划状态：** 尚未实施。

**拟议修正：** 增加自愿停止/推迟或有辅助恢复选项，并定义允许的无障碍调适；保留诚实标注。对齐信心评分时机，当检查点被跳过时提供真实结果而非预填 `completed` 元数据。

**保留：** 证据/学习的区分；明确的 Bastani 外推说明；可比新任务；标签污染规则；单点警示。

**基线证据：** `skills/student-learning/unassisted-evidence-checkpoint/SKILL.md:117`、`203`、`205`、`111`、`148`、`154`、`247`、`175`、`221`、`239`。其余证据与提取/核心检查见完整记录。

### Q4 — 一致的学习工作流与示例

#### `student-learning/fading-manager`

**文件：** [skills/student-learning/fading-manager/SKILL.md](../../skills/student-learning/fading-manager/SKILL.md)。**审阅优先级：** medium。**计划状态：** 尚未实施。

**拟议修正：** 使示例与来源标签同明确标准对齐；保持阈值显式标注为启发式规则。允许学习者/教师调整、特定任务支持与可及热启动；要求经核实的最小历史记录与宿主级数据同意。

**保留：** 透明撤架；恢复支持；主题特定支架；启发式局限性；外部支持警示。

**基线证据：** `skills/student-learning/fading-manager/SKILL.md:111`、`113`、`115`、`195`、`201`、`234`、`100`、`131`、`156`、`29`。其余证据与提取/核心检查见完整记录。

#### `student-learning/stuck-and-error-diagnosis-coach`

**文件：** [skills/student-learning/stuck-and-error-diagnosis-coach/SKILL.md](../../skills/student-learning/stuck-and-error-diagnosis-coach/SKILL.md)。**审阅优先级：** medium。**计划状态：** 尚未实施。

**拟议修正：** 修正数值与运动学示例；将错误分类框架化为允许混合/不明确的假设；将“难度恰当”断言替换为中立确认。对明显的笔误保持简短诊断。

**保留：** 过程层面的针对性反馈；讲解前的自我纠正；包含表征维度；未来的防错检查问题。

**基线证据：** `skills/student-learning/stuck-and-error-diagnosis-coach/SKILL.md:72`、`103`、`212`、`83`、`188`、`224`、`65`、`178`、`208`。其余证据与提取/核心检查见完整记录。

#### `student-learning/transfer-bridge`

**文件：** [skills/student-learning/transfer-bridge/SKILL.md](../../skills/student-learning/transfer-bridge/SKILL.md)。**审阅优先级：** medium。**计划状态：** 尚未实施。

**拟议修正：** 将价格/分配类比替换为有效的共享机制任务，或显式标注有限类比。记录线索/支持层级，区分即时支架应用与独立延迟迁移；修复占位符/状态词汇。

**保留：** 近/远迁移区分；显式结构对比；支架局限性；学生自主生成的第三个应用。

**基线证据：** `skills/student-learning/transfer-bridge/SKILL.md:131`、`152`、`167`、`75`、`193`、`201`、`244`、`166`、`170`、`68`。其余证据与提取/核心检查见完整记录。

#### `student-learning/srl-session-wrapper`

**文件：** [skills/student-learning/srl-session-wrapper/SKILL.md](../../skills/student-learning/srl-session-wrapper/SKILL.md)。**审阅优先级：** medium。**计划状态：** 尚未实施。

**拟议修正：** 插入开场目标输入，若在中期/结束模式下缺失则恢复或询问一次；除非存在计时器集成，否则说明用户如何返回触发后续阶段。解决模糊的证据条目并限定实测收益主张。

**保留：** 简短阶段；真实的学习者评估；拒绝处理；将包装器与有效学习内容区分开。

**基线证据：** `skills/student-learning/srl-session-wrapper/SKILL.md:33`、`80`、`112`、`125`、`23`、`69`、`73`、`104`、`145`、`209`。其余证据与提取/核心检查见完整记录。

#### `student-learning/teach-back-evaluator`

**文件：** [skills/student-learning/teach-back-evaluator/SKILL.md](../../skills/student-learning/teach-back-evaluator/SKILL.md)。**审阅优先级：** medium。**计划状态：** 尚未实施。

**拟议修正：** 移除“视觉型思考者”标签；允许不带学习者类型归因的真实示例。使通过信息与分数对齐并标注为非正式形成性判断；限制修改轮次并允许在存在未解决缺口时结束。通过受控的未来编辑使用或移除未使用的输入。

**保留：** 好奇/非对抗的新手角色；带解释的评分锚点；针对性修改；恰当的内容类型局限。

**基线证据：** `skills/student-learning/teach-back-evaluator/SKILL.md:62`、`134`、`141`、`97`、`239`、`139`、`145`、`157`、`64`、`185`。其余证据与提取/核心检查见完整记录。

### Q5 — 课程与来源交接

#### `curriculum-alignment/developmental-band-translator`

**文件：** [skills/curriculum-alignment/developmental-band-translator/SKILL.md](../../skills/curriculum-alignment/developmental-band-translator/SKILL.md)。**审阅优先级：** medium。**计划状态：** 尚未实施。

**拟议修正：** 明确覆盖与来源类型优先级；保留保守的歧义/教师审阅标志。

**保留：** 来源进阶结构、原始阶段标签与来源原始表述；对不确定年龄对齐的保守处理及教师审阅。当年龄证据确实必要且缺失时保留显式请求/标志。

**明确允许的修正：** 可修改无条件无年龄中止逻辑，使提供的覆盖映射与合法的扁平框架处理具有连贯的优先级；切勿捏造年龄或静默抹除不确定性。

**基线证据：** `skills/curriculum-alignment/developmental-band-translator/SKILL.md:31`、`39`、`126`、`148`、`152`、`18`、`118`、`42`。其余证据与提取/核心检查见完整记录。

#### `curriculum-alignment/kud-chart-author`

**文件：** [skills/curriculum-alignment/kud-chart-author/SKILL.md](../../skills/curriculum-alignment/kud-chart-author/SKILL.md)。**审阅优先级：** medium。**计划状态：** 尚未实施。

**拟议修正：** 将原始文档路由至真实的拆解步骤，然后再进行阶段标注；保持直接起草回退路径的诚实性。

**保留：** 知道、理解与做到（KUD）之间的区分；显式的先备推理、来源对齐以及教师对草案的审阅。保留带有诚实假设的直接起草路径，以及硬性先备与仅有益背景之间的区分。

**明确允许的修正：** 可将无效的原始文档交接修改为在阶段标注前执行的实际拆解步骤；切勿重命名目标技能或假装其必需的结构化输入是可选的。

**基线证据：** `skills/curriculum-alignment/kud-chart-author/SKILL.md:129`、`141`、`19`、`133`、`55`、`401`。其余证据与提取/核心检查见完整记录。

#### `professional-learning/competency-framework-translator`

**文件：** [skills/professional-learning/competency-framework-translator/SKILL.md](../../skills/professional-learning/competency-framework-translator/SKILL.md)。**审阅优先级：** medium。**计划状态：** 尚未实施。

**拟议修正：** 将经核实的引文与解读拆分为不同标签的输出；对于精确主张请求来源/版本；切勿捏造官方文本。

**保留：** 可观察指标、质性区分的进阶层级、学科/情境特定应用以及与所提供框架的可追溯关联。当翻译属于解读性质时保留不确定性与教育者审阅。

**明确允许的修正：** 输出可区分经核实的来源引文与模型解读。切勿在“原始框架原文”标签下保留重构文本，或在来源缺失时捏造官方文本。

**基线证据：** `skills/professional-learning/competency-framework-translator/SKILL.md:116`、`128`、`130`、`16`、`255`。其余证据与提取/核心检查见完整记录。

### Q6 — 研究精确性与提取一致性

#### `memory-learning-science/retrieval-practice-generator`

**文件：** [skills/memory-learning-science/retrieval-practice-generator/SKILL.md](../../skills/memory-learning-science/retrieval-practice-generator/SKILL.md)。**审阅优先级：** medium。**计划状态：** 尚未实施。

**拟议修正：** 使该例外在所有规则/自检项中保持一致；保留提取聚焦与可及的初学者选项。

**保留：** 以提取为中心的练习、丰富的题型与反馈、可及的初学者支持，以及对照所教内容核对答案。保留回忆与识别之间的区分，而非将其混为一谈。

**明确允许的修正：** 可修改通用的反识别规则/自检项，以一贯尊重既有的初学者例外。可将所教来源核查警示移入活跃核心。

**基线证据：** `skills/memory-learning-science/retrieval-practice-generator/SKILL.md:109`、`115`、`150`、`223`、`22`、`96`、`46`、`100`。其余证据与提取/核心检查见完整记录。

#### `memory-learning-science/spaced-practice-scheduler`

**文件：** [skills/memory-learning-science/spaced-practice-scheduler/SKILL.md](../../skills/memory-learning-science/spaced-practice-scheduler/SKILL.md)。**审阅优先级：** medium。**计划状态：** 尚未实施。

**拟议修正：** 修正抽样研究主张；将选定时间表与回退规则标注为可调节的启发式规则。保留排程方法。

**保留：** 分布式复习、实用排程、根据记忆保持目标与学习者表现进行的调整，以及支持间隔效应的具名研究。在有帮助处保留可用的示例时间表。

**明确允许的修正：** 精确间隔时间表与回退百分比可标注为可调节的实践者选择；存在争议的研究计数、普适遗忘主张以及精确最优性归因可予以修正。它们不受“既定实证事实”的保护。

**基线证据：** `skills/memory-learning-science/spaced-practice-scheduler/SKILL.md:18`、`78`、`113`、`206`、`22`、`96`、`46`、`16`、`225`。其余证据与提取/核心检查见完整记录。

#### `curriculum-assessment/differentiation-adapter`

**文件：** [skills/curriculum-assessment/differentiation-adapter/SKILL.md](../../skills/curriculum-assessment/differentiation-adapter/SKILL.md)。**审阅优先级：** medium。**计划状态：** 尚未实施。

**拟议修正：** 指明所用版本并承认后续 3.0 版；保留保护学习目标的方法。

**保留：** 对学习目标的保护、基于相关准备度/可及性需求的差异化、UDL 路径选项以及对学习风格匹配的拒绝。保留有用的 UDL 知情适配流程及其具名研究。

**明确允许的修正：** 可修改“CAST 2018 是最新版本”的表述；准确指明历史版本无需用新框架替换整个方法。

**基线证据：** `skills/curriculum-assessment/differentiation-adapter/SKILL.md:78`、`16`、`234`。其余证据与提取/核心检查见完整记录。

#### `original-frameworks/developmental-band-system-designer`

**文件：** [skills/original-frameworks/developmental-band-system-designer/SKILL.md](../../skills/original-frameworks/developmental-band-system-designer/SKILL.md)。**审阅优先级：** medium。**计划状态：** 尚未实施。

**拟议修正：** 使用“支持理由”而非“验证”；保留显式原创方法论。

**保留：** 连接使命、发展进阶与学校设计的实践者原创架构；透明假设与教育专业判断。保留混龄研究作为支持理由并保留原创框架身份。

**明确允许的修正：** 可将“组件研究验证了整个拟议架构”的表述修改为适度的理由陈述；切勿抹除该框架或将其重新标注为已通过实验验证。

**基线证据：** `skills/original-frameworks/developmental-band-system-designer/SKILL.md:79`、`85`、`16`、`271`。其余证据与提取/核心检查见完整记录。

### Q7 — 能动性、动机与可行支持

#### `wellbeing-motivation-agency/agency-scaffold-generator`

**文件：** [skills/wellbeing-motivation-agency/agency-scaffold-generator/SKILL.md](../../skills/wellbeing-motivation-agency/agency-scaffold-generator/SKILL.md)。**审阅优先级：** medium。**计划状态：** 尚未实施。

**拟议修正：** 将改编维度/层级与数字节奏标注为实用启发式规则；展示直接下一层级及进阶证据。在协商选择前声明受保护的安全、既有无障碍支持以及评价/课程要求；允许差异化准备度。解析/标注可选串联目标或记录证据标签含义；保留行为且不捏造缺失技能。

**保留：** 真实的有界选择；明确的决策归属权；恢复时不条件反射式剥夺能动性；能动性不等于处处最大化自由。

**基线证据：** `skills/wellbeing-motivation-agency/agency-scaffold-generator/SKILL.md:64`、`65`、`128`、`190`、`211`、`241`、`115`、`122`、`119`、`126`。其余证据与提取/核心检查见完整记录。

#### `wellbeing-motivation-agency/implementation-intention-designer`

**文件：** [skills/wellbeing-motivation-agency/implementation-intention-designer/SKILL.md](../../skills/wellbeing-motivation-agency/implementation-intention-designer/SKILL.md)。**审阅优先级：** medium。**计划状态：** 尚未实施。

**拟议修正：** 解决内部线索矛盾；区分学生认可的愿望与教师选定的顺从要求。确认真实障碍并保留环境支持路径。将监控阈值标注为示例并修正证据/努力确定性主张。解析/标注可选串联目标或记录证据标签含义；保留行为且不捏造缺失技能。

**保留：** 离散线索/行动特异性；微小的可达成起步；应对计划；简单监控；动机与外部障碍局限。

**基线证据：** `skills/wellbeing-motivation-agency/implementation-intention-designer/SKILL.md:64`、`65`、`100`、`125`、`126`、`177`、`205`、`78`、`219`、`109`。其余证据与提取/核心检查见完整记录。

#### `wellbeing-motivation-agency/flow-state-condition-designer`

**文件：** [skills/wellbeing-motivation-agency/flow-state-condition-designer/SKILL.md](../../skills/wellbeing-motivation-agency/flow-state-condition-designer/SKILL.md)。**审阅优先级：** medium。**计划状态：** 尚未实施。

**拟议修正：** 将确定性的心流/保证成功主张替换为通过学生报告与学习证据检验的设计假设。将任务目标与掌握对齐，并增加对重复错误的响应，而非无限期同水平重试。

**保留：** 差异化；低干扰；即时信息性反馈；私密进度；最低技能要求与不适用任务局限。

**基线证据：** `skills/wellbeing-motivation-agency/flow-state-condition-designer/SKILL.md:214`、`218`、`220`、`239`、`98`、`123`、`167`、`253`、`76`、`176`。其余证据与提取/核心检查见完整记录。

#### `wellbeing-motivation-agency/motivation-diagnostic-task-redesign`

**文件：** [skills/wellbeing-motivation-agency/motivation-diagnostic-task-redesign/SKILL.md](../../skills/wellbeing-motivation-agency/motivation-diagnostic-task-redesign/SKILL.md)。**审阅优先级：** medium。**计划状态：** 尚未实施。

**拟议修正：** 停止仅凭任务设计就指派内在动机；询问/核查学习者视角，允许“未知”并标注假设。保留学习目标与必要基础工作，而非宣称更高认知层级自动更好；提供同等耗时的小型重设计方案。

**保留：** 自我决定理论（SDT）特异性；自主性与结构并重；理由说明；无缺陷型学生标签；理解回退；时间成本确认。

**基线证据：** `skills/wellbeing-motivation-agency/motivation-diagnostic-task-redesign/SKILL.md:54`、`135`、`170`、`213`、`74`、`78`、`241`、`259`、`76`、`187`。其余证据与提取/核心检查见完整记录。

#### `wellbeing-motivation-agency/self-efficacy-builder-sequence`

**文件：** [skills/wellbeing-motivation-agency/self-efficacy-builder-sequence/SKILL.md](../../skills/wellbeing-motivation-agency/self-efficacy-builder-sequence/SKILL.md)。**审阅优先级：** medium。**计划状态：** 尚未实施。

**拟议修正：** 在提出动机假设前评估实际的先备知识与可及性需求；不从拒绝或口头表达能力推断心理原因。移除保证成功与“困难=学习”主张，采用学习者认可的节奏/计时器并保留辅助工具。保留成长型思维实施警示。

**保留：** 掌握体验胜过口号；具体可信的表扬；微小步子；任务相关性；隐私/尊严；正当的口头规划。

**基线证据：** `skills/wellbeing-motivation-agency/self-efficacy-builder-sequence/SKILL.md:109`、`117`、`134`、`194`、`269`、`78`、`123`、`133`、`196`、`206`。其余证据与提取/核心检查见完整记录。

### Q8 — 福祉设计与适度主张

#### `wellbeing-motivation-agency/awe-wonder-experience-designer`

**文件：** [skills/wellbeing-motivation-agency/awe-wonder-experience-designer/SKILL.md](../../skills/wellbeing-motivation-agency/awe-wonder-experience-designer/SKILL.md)。**审阅优先级：** medium。**计划状态：** 尚未实施。

**拟议修正：** 限定从情绪研究向课堂成效的迁移推论；核查示例中的具体事实与尺度。提供情绪与身体上均可及的替代方案，避免将苦难当作奇观。保持好奇心与可教目标相连，不强制要求特定情绪反应。

**保留：** 新兴证据标签；与内容相连的惊奇；探究桥梁；主观反应与过度使用局限性。

**基线证据：** `skills/wellbeing-motivation-agency/awe-wonder-experience-designer/SKILL.md:78`、`96`、`197`、`247`、`111`、`120`、`140`、`243`、`112`、`187`。其余证据与提取/核心检查见完整记录。

#### `wellbeing-motivation-agency/belonging-classroom-culture-designer`

**文件：** [skills/wellbeing-motivation-agency/belonging-classroom-culture-designer/SKILL.md](../../skills/wellbeing-motivation-agency/belonging-classroom-culture-designer/SKILL.md)。**审阅优先级：** medium。**计划状态：** 尚未实施。

**拟议修正：** 增加学习者声音与可及性检查；将眼神接触/发言/到校视为模糊信号，绝不作为归属感评分。允许无污名化的支持与安全的配对选择；直接回应霸凌/歧视。限定跨情境效能与时间主张。

**保留：** 避免公开点名突出；实质性贡献胜过象征性包容；日常常规嵌入；真诚关怀；关怀支持边界。

**基线证据：** `skills/wellbeing-motivation-agency/belonging-classroom-culture-designer/SKILL.md:118`、`130`、`139`、`171`、`251`、`15`、`78`、`249`、`98`、`190`。其余证据与提取/核心检查见完整记录。

#### `wellbeing-motivation-agency/perma-based-lesson-designer`

**文件：** [skills/wellbeing-motivation-agency/perma-based-lesson-designer/SKILL.md](../../skills/wellbeing-motivation-agency/perma-based-lesson-designer/SKILL.md)。**审阅优先级：** medium。**计划状态：** 尚未实施。

**拟议修正：** 将 PERMA 呈现为规划视角，限定成效/干预主张，并允许在映射中留空未涉及的要素。为个人或政治反思增加低披露/可及选择；将学习证据与愉悦感分开要求。

**保留：** 不强制集齐五要素；不强迫积极情绪；学术严谨性；实际教师行动；特权情境局限性。

**基线证据：** `skills/wellbeing-motivation-agency/perma-based-lesson-designer/SKILL.md:100`、`150`、`158`、`172`、`74`、`78`、`98`、`262`、`111`、`113`。其余证据与提取/核心检查见完整记录。

#### `wellbeing-motivation-agency/wellbeing-learning-connection-mapper`

**文件：** [skills/wellbeing-motivation-agency/wellbeing-learning-connection-mapper/SKILL.md](../../skills/wellbeing-motivation-agency/wellbeing-learning-connection-mapper/SKILL.md)。**审阅优先级：** medium。**计划状态：** 尚未实施。

**拟议修正：** 使证据图谱输出保持中立：关联可以是“有支撑”、“合理/间接”、“存在矛盾”或“未知”；保留零效果/负效果发现。移除捏造的本地趋势、无关效应量迁移与缺乏支撑的时间线。将预测与本地证据分开，并要求领导层进行事实审阅。

**保留：** 诚实指令；机制而非口号；产生影响的条件；警示章节；基线要求。

**基线证据：** `skills/wellbeing-motivation-agency/wellbeing-learning-connection-mapper/SKILL.md:92`、`94`、`110`、`147`、`271`、`75`、`204`、`225`、`249`、`253`。其余证据与提取/核心检查见完整记录。

### Q9 — MCP 界面上的关键局限

#### `historical-thinking/historical-document-set-curator`

**文件：** [skills/historical-thinking/historical-document-set-curator/SKILL.md](../../skills/historical-thinking/historical-document-set-curator/SKILL.md)。**审阅优先级：** medium。**计划状态：** 尚未实施。

**拟议修正：** 标注拟议/未核实文献并在使用前核查出处；将精炼的来源供应局限性补充到核心。未发现虚构来源。

**保留：** 问题导向的史料选择、有用的出处字段、对比视角与历史探究。保持拟议史料建议的实用性，同时确保用户能区分“推荐”与“实际获取并核对过的文献”。

**明确允许的修正：** 可修改输出标签与活跃核心，以暴露未核实/拟议状态及来源供应局限；切勿为了规避问题而删除所有具体史料建议。

**基线证据：** `skills/historical-thinking/historical-document-set-curator/SKILL.md:145`、`150`、`215`、`290`、`16`、`288`。其余证据与提取/核心检查见完整记录。

#### `systems-thinking/ladder-of-inference-reflection`

**文件：** [skills/systems-thinking/ladder-of-inference-reflection/SKILL.md](../../skills/systems-thinking/ladder-of-inference-reflection/SKILL.md)。**审阅优先级：** medium。**计划状态：** 尚未实施。

**拟议修正：** 将精炼的近期伤害/权力不对等适用性检查纳入核心；保留反思方法，不将替代解释变成事实调查。

**保留：** 区分观察、解读与可能替代方案的尊重式反思；承认感受而不断言某种替代解释为真。保留教师能动性与反思性教育目的。

**明确允许的修正：** 活跃核心可纳入既有的近期伤害/权力不对等适用性边界。切勿利用反思性重构来淡化已记录的伤害或替代事实调查。

**基线证据：** `skills/systems-thinking/ladder-of-inference-reflection/SKILL.md:100`、`104`、`173`、`175`、`171`。其余证据与提取/核心检查见完整记录。

### Q10 — 大型原创工作流与清晰范围

#### `original-frameworks/dispositional-knowledge-assessment-designer`

**文件：** [skills/original-frameworks/dispositional-knowledge-assessment-designer/SKILL.md](../../skills/original-frameworks/dispositional-knowledge-assessment-designer/SKILL.md)。**审阅优先级：** medium。**计划状态：** 尚未实施。

**拟议修正：** 在前端清晰说明组件选择以及设计与实施工作负荷；保留多方知情人判断与可选照护者输入。在不削弱核心区分的前提下重组特定于组件的细节。

**保留：** 基于观察、多方知情人的专业判断；指标、解读与发展模式之间的区分；可选照护者贡献与既有局限。保留完整的评价设计作为可用输出。

**明确允许的修正：** 可修改工作负荷框架与组织方式。组件选择仅为提案：不得静默移除当前必需的输出、新增必需输入或削弱情境敏感的观察。

**基线证据：** `skills/original-frameworks/dispositional-knowledge-assessment-designer/SKILL.md:85`、`219`、`633`、`635`、`58`、`131`、`631`。其余证据与提取/核心检查见完整记录。

#### `professional-learning/panel-review`

**文件：** [skills/professional-learning/panel-review/SKILL.md](../../skills/professional-learning/panel-review/SKILL.md)。**审阅优先级：** medium。**计划状态：** 尚未实施。

**拟议修正：** 在使用前显性化范围与启发式状态；保留有用视角与局限；不将同一会话中的模拟角色描绘为独立评分者。解析/标注可选串联目标或记录证据标签含义；保留行为且不捏造缺失技能。

**保留：** 多重显式审阅视角、结构化理由与可操作反馈、相关证据警示以及有用的福祉/SEL 校准范围。在有用处保留数值阈值作为透明的实践启发式规则。

**明确允许的修正：** 可澄清范围措辞、启发式标签与独立性声明。不得保护“同会话模拟角色属于独立审阅者”的主张，或将其数值门禁视为已验证的测量。发现描述编辑需要其有界元数据例外。

**基线证据：** `skills/professional-learning/panel-review/SKILL.md:3`、`70`、`614`、`618`、`622`、`11`、`12`、`612`、`94`。其余证据与提取/核心检查见完整记录。

## 附录 B — 精确组织队列

以下 20 个条目属于提示性建议。计数为任何修改前的正文/MCP 提示词代理 token。潜在移动项只是章节映射的起点，而非要求移动列出的每一节。保留每条记录的强制核心与所有有用证据。

### R1 — 原创框架指南

| 精确源路径 | 正文 / MCP 代理 token | 初步参考资料候选 |
|---|---:|---|
| [skills/original-frameworks/developmental-progression-synthesis/SKILL.md](../../skills/original-frameworks/developmental-progression-synthesis/SKILL.md) | 5,659 / 2,528 | 扩展示例章节（至第 360 行）；在核心中保留一个简短示例与所有强制例外。（`developmental-progression-synthesis/SKILL.md:283`） |
| [skills/original-frameworks/learning-target-authoring-guide/SKILL.md](../../skills/original-frameworks/learning-target-authoring-guide/SKILL.md) | 11,743 / 1,938 | 扩展示例章节（至第 766 行）；在核心中保留一个简短示例与所有强制例外。（`learning-target-authoring-guide/SKILL.md:490`） |
| [skills/original-frameworks/seeds-regenerative-inquiry-cycle/SKILL.md](../../skills/original-frameworks/seeds-regenerative-inquiry-cycle/SKILL.md) | 6,118 / 1,805 | 扩展示例章节（至第 393 行）；在核心中保留一个简短示例与所有强制例外。（`seeds-regenerative-inquiry-cycle/SKILL.md:250`） |
| [skills/original-frameworks/self-determined-project-design-protocol/SKILL.md](../../skills/original-frameworks/self-determined-project-design-protocol/SKILL.md) | 6,536 / 1,666 | 扩展示例章节（至第 425 行）；在核心中保留一个简短示例与所有强制例外。（`self-determined-project-design-protocol/SKILL.md:242`） |

### R2 — 课程设计指南

| 精确源路径 | 正文 / MCP 代理 token | 初步参考资料候选 |
|---|---:|---|
| [skills/curriculum-assessment/curriculum-knowledge-architecture-designer/SKILL.md](../../skills/curriculum-assessment/curriculum-knowledge-architecture-designer/SKILL.md) | 7,700 / 1,745 | 扩展示例章节（至第 412 行）；在核心中保留一个简短示例与所有强制例外。（`curriculum-knowledge-architecture-designer/SKILL.md:228`） |
| [skills/curriculum-assessment/discipline-specific-critical-thinking-task-designer/SKILL.md](../../skills/curriculum-assessment/discipline-specific-critical-thinking-task-designer/SKILL.md) | 6,686 / 1,928 | 扩展示例章节（至第 334 行）；在核心中保留一个简短示例与所有强制例外。（`discipline-specific-critical-thinking-task-designer/SKILL.md:231`） |
| [skills/curriculum-assessment/kud-knowledge-type-mapper/SKILL.md](../../skills/curriculum-assessment/kud-knowledge-type-mapper/SKILL.md) | 8,187 / 2,358 | 扩展示例章节（至第 408 行）；在核心中保留一个简短示例与所有强制例外。（`kud-knowledge-type-mapper/SKILL.md:259`） |
| [skills/curriculum-assessment/project-brief-designer/SKILL.md](../../skills/curriculum-assessment/project-brief-designer/SKILL.md) | 5,533 / 1,534 | 扩展示例章节（至第 340 行）；在核心中保留一个简短示例与所有强制例外。（`project-brief-designer/SKILL.md:218`） |
| [skills/curriculum-assessment/scope-and-sequence-designer/SKILL.md](../../skills/curriculum-assessment/scope-and-sequence-designer/SKILL.md) | 9,351 / 2,658 | 扩展示例章节（至第 575 行）；在核心中保留一个简短示例与所有强制例外。（`scope-and-sequence-designer/SKILL.md:386`） |

### R3 — 专业学习指南

| 精确源路径 | 正文 / MCP 代理 token | 初步参考资料候选 |
|---|---:|---|
| [skills/professional-learning/lesson-study-cycle-designer/SKILL.md](../../skills/professional-learning/lesson-study-cycle-designer/SKILL.md) | 5,005 / 1,136 | 扩展示例章节（至第 315 行）；在核心中保留一个简短示例与所有强制例外。（`lesson-study-cycle-designer/SKILL.md:186`） |
| [skills/professional-learning/pedagogical-content-knowledge-developer/SKILL.md](../../skills/professional-learning/pedagogical-content-knowledge-developer/SKILL.md) | 7,510 / 1,991 | 扩展示例章节（至第 395 行）；在核心中保留一个简短示例与所有强制例外。（`pedagogical-content-knowledge-developer/SKILL.md:260`） |
| [skills/professional-learning/technological-pedagogical-content-knowledge-developer/SKILL.md](../../skills/professional-learning/technological-pedagogical-content-knowledge-developer/SKILL.md) | 7,472 / 2,085 | 扩展示例章节（至第 406 行）；在核心中保留一个简短示例与所有强制例外。（`technological-pedagogical-content-knowledge-developer/SKILL.md:274`） |

### R4 — 历史探究与工作周期指南

| 精确源路径 | 正文 / MCP 代理 token | 初步参考资料候选 |
|---|---:|---|
| [skills/historical-thinking/contextualisation-skill-builder/SKILL.md](../../skills/historical-thinking/contextualisation-skill-builder/SKILL.md) | 5,031 / 1,138 | 扩展示例章节（至第 298 行）；在核心中保留一个简短示例与所有强制例外。（`contextualisation-skill-builder/SKILL.md:201`） |
| [skills/historical-thinking/document-based-lesson-designer/SKILL.md](../../skills/historical-thinking/document-based-lesson-designer/SKILL.md) | 5,281 / 1,574 | 扩展示例章节（至第 371 行）；在核心中保留一个简短示例与所有强制例外。（`document-based-lesson-designer/SKILL.md:265`） |
| [skills/historical-thinking/sourcing-skill-builder/SKILL.md](../../skills/historical-thinking/sourcing-skill-builder/SKILL.md) | 5,971 / 1,534 | 扩展示例章节（至第 320 行）；在核心中保留一个简短示例与所有强制例外。（`sourcing-skill-builder/SKILL.md:210`） |
| [skills/montessori-alternative-approaches/uninterrupted-work-cycle-designer/SKILL.md](../../skills/montessori-alternative-approaches/uninterrupted-work-cycle-designer/SKILL.md) | 5,678 / 1,131 | 扩展示例章节（至第 330 行）；在核心中保留一个简短示例与所有强制例外。（`uninterrupted-work-cycle-designer/SKILL.md:165`） |

### R5 — AI 学习科学指南

| 精确源路径 | 正文 / MCP 代理 token | 初步参考资料候选 |
|---|---:|---|
| [skills/ai-learning-science/cognitive-tutoring-architecture-designer/SKILL.md](../../skills/ai-learning-science/cognitive-tutoring-architecture-designer/SKILL.md) | 5,091 / 999 | 扩展示例章节（至第 284 行）；在核心中保留一个简短示例与所有强制例外。（`cognitive-tutoring-architecture-designer/SKILL.md:158`） |
| [skills/ai-learning-science/formative-assessment-loop-designer/SKILL.md](../../skills/ai-learning-science/formative-assessment-loop-designer/SKILL.md) | 5,029 / 1,140 | 扩展示例章节（至第 287 行）；在核心中保留一个简短示例与所有强制例外。（`formative-assessment-loop-designer/SKILL.md:169`） |
| [skills/ai-learning-science/intelligent-tutoring-dialogue-designer/SKILL.md](../../skills/ai-learning-science/intelligent-tutoring-dialogue-designer/SKILL.md) | 5,004 / 1,053 | 扩展示例章节（至第 288 行）；在核心中保留一个简短示例与所有强制例外。（`intelligent-tutoring-dialogue-designer/SKILL.md:162`） |
| [skills/ai-learning-science/productive-failure-desirable-difficulty-designer/SKILL.md](../../skills/ai-learning-science/productive-failure-desirable-difficulty-designer/SKILL.md) | 5,059 / 1,137 | 扩展示例章节（至第 278 行）；在核心中保留一个简短示例与所有强制例外。（`productive-failure-desirable-difficulty-designer/SKILL.md:166`） |

## 附录 C — 计划准备检查与当前状态

本计划基于既有的源文件审阅与直接核查的仓库约定编制。在编制时，全部 165 个源文件的 SHA-256 哈希与结构化审阅一致，37 个修订候选被唯一分配给各自对应的一个 Q 工作包，全部 20 个组织候选被唯一分配给各自对应的一个 R 工作包。108 条保留记录受到保护，并继续完整收录于链接的 165 技能矩阵中。本计划未将任何候选标记为已实施或已验收。

此处仅执行了只读检查以及本文档的生成与核对。现有测试套件结果记录于早期审计证据中；未仅为了编写提案而重跑测试与模型对比。受追踪仓库保持未变。一名独立的只读计划批评者指出了附录 A 中的保留片段问题；全部 12 个受影响条目均已替换为完整的保留行为声明与明确允许的修正。审阅使用了一名派生批评者（峰值 1 名），无继承对话历史。未对技能进行任何实施或返工；审阅返工仅限于本计划文档。模型用量/token 遥测不可用。

同一名独立批评者复核了这 12 处澄清，并报告在该有界审阅范围内无剩余实质性异议。最终准备检查在本地链接、引用源码行号边界、精确的 37/20 队列成员资格、全部 165 个未变更源文件哈希以及空受追踪 diff 上均已通过。这些是文档/源文件保留检查，而非教育有效性或运行时测试结果。
