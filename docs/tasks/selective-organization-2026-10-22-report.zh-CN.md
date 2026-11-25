# 选择性技能组织报告 — 2026 年 10 月 22 日

**状态：候选方案已实施；范围内检查通过；独立只读审阅待定。** 本工作包仅改进本地源文件组织。它不改变教育方法或提取出的 MCP 提示词，不确立模型遵循度或学习者收益，不集成生成视图，也不发布任何内容。

检出路径：`/Users/garethmanning/Github/education-agent-skills`；分支：`codex/agent-skills-standards-quality-2026-10-22`；继承 HEAD：`6bbbce418f82e11044009c9f3b7373a354de5bd0` 加已验收的未提交运行时/便携/内容工作。保护这些已验收变更的是修改前即刻快照，而非 HEAD。负责人增量精确为列出的八个 `SKILL.md` 正文、八个新建技能本地 Markdown 参考资料以及本报告。其余全部 157 个源技能与修改前即刻快照按字节完全一致。

## 授权与阅读

已阅读仓库 `AGENTS.md`、`CLAUDE.md` 与 `STATE.md`；完整组织简报；质量量规；计划第 4 节/第 2 阶段/附录 B 及受保护核心记录；课程/证据报告与独立审阅；以及随后的课程连贯性修复报告/ACCEPT 回执。后者取代了两个已修复课程源文件的哈希。编辑前通读了全部八个受影响技能，包括其方法、示例与局限。14 个未编辑的提示性候选接受了对当前比率、示例场景/章节结构与保留记录的有界组织筛查，而非全新的完整教育/内容审计。

任务明确将审阅后的生成注册表/打包产物/导出集成交由协调器处理，并禁止工作代理提交/推送/发布。这些有界指令为本工作包延后了仓库指南中的提交前重新生成与会话状态工作流；未修改任何 `STATE.md`、注册表、打包产物、便携输出、运行时、客户端设置或其他负责人的文件。未使用任何子代理、模型调用、托管请求、真实学习者数据、部署、付费服务、外部消息、服务器或后台进程。仅为检查在仓库外生成了临时导出/复制输出，并已自动移除。

## 变更内容与交付效果

八份原本较长的指南现已通过明确的“Read … when …”条件链接至其完整的可选示例。每个移出的章节均从已验收的修改前即刻文件原样复制；紧凑节选保留在内联正文中。未删除或重写任何研究阐释或引用。头部、schema 键、必需性、占位符、ID、名称、步骤、核心例外、必需输出与最终局限均未改变。`Example Output` 之前的文件前缀与之后的文件后缀完全精确；仅替换了该可选示例区间。

在这八个 Markdown 正文中，代理计数从 **77,434 降至 45,518**（减少 31,916，约 41%）。这是针对初始仅读取 `SKILL.md` 而不加载其可选参考资料的客户端的源激活代理指标，而非实测上下文用量或计费。读取所有参考资料的客户端仍将加载完整示例，外加少量的指引/节选重复。**MCP 提示词节省按设计为零**：每个当前加载器提取的提示词按字节完全一致。参考资料无法通过当前托管 MCP 适配器获取，且执行新 MCP 步骤时也不需要它们；未向任何提取出的提示词中插入指引。

计数使用可用的 tiktoken `o200k_base` 编码器，正文不含 YAML，核心遵循当前加载器提取规则。它们并非 Claude token。修改前即刻的已验收修复使倾向性评价的核心为 **5,955**，而非早期提案中的 5,789；本工作包刻意完整保留该核心。学习目标撰写与 `panel-review` 也保持较长，因为它们的方法与角色/维度契约比配额更重要。

## 精确源与资源映射

每个参考资料均位于其各自的技能文件夹内。“移动前所在行”标识 `/tmp/selective-organization-before-20261022/<source>` 中的完整原样示例区间。其他章节保持未变。

| 源文件 | 移动/复制前所在行 | 新建资源 | 正文 改前 → 改后 | 核心 改前 → 改后 | 参考资料代理 token |
|---|---:|---|---:|---:|---:|
| `skills/original-frameworks/learning-target-authoring-guide/SKILL.md` | 490–764 | `skills/original-frameworks/learning-target-authoring-guide/references/worked-examples.md` | 11,743 → 6,927 | 1,938 → 1,938 | 5,100 |
| `skills/original-frameworks/dispositional-knowledge-assessment-designer/SKILL.md` | 378–634 | `skills/original-frameworks/dispositional-knowledge-assessment-designer/references/worked-agency-assessment.md` | 13,754 → 9,754 | 5,955 → 5,955 | 5,076 |
| `skills/professional-learning/panel-review/SKILL.md` | 467–621 | `skills/professional-learning/panel-review/references/worked-kud-review.md` | 11,717 → 6,870 | 4,967 → 4,967 | 5,085 |
| `skills/professional-learning/pedagogical-content-knowledge-developer/SKILL.md` | 260–393 | `skills/professional-learning/pedagogical-content-knowledge-developer/references/worked-examples.md` | 7,510 → 4,042 | 1,991 → 1,991 | 3,713 |
| `skills/professional-learning/technological-pedagogical-content-knowledge-developer/SKILL.md` | 274–404 | `skills/professional-learning/technological-pedagogical-content-knowledge-developer/references/worked-examples.md` | 7,472 → 4,234 | 2,085 → 2,085 | 3,562 |
| `skills/curriculum-assessment/scope-and-sequence-designer/SKILL.md` | 386–573 | `skills/curriculum-assessment/scope-and-sequence-designer/references/worked-examples.md` | 9,351 → 5,264 | 2,658 → 2,658 | 4,243 |
| `skills/curriculum-assessment/kud-knowledge-type-mapper/SKILL.md` | 259–406 | `skills/curriculum-assessment/kud-knowledge-type-mapper/references/worked-examples.md` | 8,187 → 4,657 | 2,358 → 2,358 | 3,933 |
| `skills/curriculum-assessment/curriculum-knowledge-architecture-designer/SKILL.md` | 228–410 | `skills/curriculum-assessment/curriculum-knowledge-architecture-designer/references/worked-examples.md` | 7,700 → 3,770 | 1,745 → 1,745 | 4,134 |

移出的资源有意保留原 Example Output 标题与原始示例（含其插图说明与警示）。主文件中的紧凑节选重复了选定的原文本；这是有意为之的可选资源重复，而非内容丢失。

- **original-frameworks/learning-target-authoring-guide**：移出两个扩展示例；保留分类表、能力/倾向警示以及 Band A 观察指标。完整的分类/撰写/检查清单/输出步骤与实践者局限性均保留在内联正文中。
- **original-frameworks/dispositional-knowledge-assessment-designer**：移出扩展的六部分能动性示例；保留一条具体的带日期观察记录以及完整修正后的实施成本/可持续性示例。全部六个设计章节、阶段校准、可选照护者输入、矛盾处理、评审校准、反身性与成本均保留在内联正文中。
- **professional-learning/panel-review**：移出精简版 KUD 刺激材料与完整的七角色模拟 JSON 对话记录；保留推演后的底线规则解读。全部七份角色简报、五组维度/角色分配、公式、输出形态以及范围/模拟/启发式警示均保留在内联正文中。
- **professional-learning/pedagogical-content-knowledge-developer**：移出扩展的压力科学案例；保留烟雾报警器表征行及其失真与年龄警示。七步法、输出契约、主题特异性与高风险核查局限保留在内联正文中。
- **professional-learning/technological-pedagogical-content-knowledge-developer**：移出扩展的一战/AI 案例；保留两阶段思维需求建议以及完整的示例数据隐私子章节。TCK/TPK/TPACK、核查、自主性-依赖性、非 AI 跳过、伦理与放弃决策均保留在内联正文中。
- **curriculum-assessment/scope-and-sequence-designer**：移出扩展的福祉项目案例；保留其显式输入状态与置信度限定。A–E 路由/状态 E 拒绝、全部先备/覆盖逻辑、元认知例外、教师提问、违规检查与输出均保留在内联正文中。
- **curriculum-assessment/kud-knowledge-type-mapper**：移出扩展的情绪调节案例；保留对比技能/倾向行以及私人习惯边界。全部类型定义、强制 Do 拆分、评价路由、复合标志、知识依附性先备条件与输出字段均保留在内联正文中。
- **curriculum-assessment/curriculum-knowledge-architecture-designer**：移出扩展的湿地案例；保留混合比例与评价模式张力。类型定义、硬/软链条、枢纽/视角、四阶段倾向、六项输出、判断边界与近似比例局限均保留在内联正文中。

## 全部 20 项附录 B 提示性处置

**六项已编辑；十四项无明确收益；20 候选队列内零项延后。** 下方另有两份重叠的长内容指南属于额外已编辑决策。“无明确收益”是有理有据的有界筛查结论，不证明未来没有任何重组能够带来帮助。比率为当前实际正文/核心计数，并与内容结合判断，而非作为及格/不及格截断线。

| 精确候选源文件 | 改前 正文/核心 | 改后 正文/核心 | 结论与理由 |
|---|---:|---:|---|
| `skills/ai-learning-science/cognitive-tutoring-architecture-designer/SKILL.md` | 5,091 / 999 | 5,091 / 999 | **无明确收益。** 单一的线性方程案例将知识组件粒度、依赖图、追踪、选题与反馈串联在一个视图中。拆出独立的小型示例资源会割裂该架构演示；未确立明确收益。 |
| `skills/ai-learning-science/formative-assessment-loop-designer/SKILL.md` | 5,029 / 1,140 | 5,029 / 1,140 | **无明确收益。** 面积/周长案例追踪了从引出到解读再到实际教学回应与仪表盘的完整过程。保留完整闭环胜过在提示性阈值处拆分。 |
| `skills/ai-learning-science/intelligent-tutoring-dialogue-designer/SKILL.md` | 5,004 / 1,053 | 5,004 / 1,053 | **无明确收益。** 自由落体对话将引出、最小帮助与误解恢复具体化。在刚过 5k 正文代理 token 的体量下，增加一次读取步骤无已确立收益。 |
| `skills/ai-learning-science/productive-failure-desirable-difficulty-designer/SKILL.md` | 5,059 / 1,137 | 5,059 / 1,137 | **无明确收益。** 单课时标准差案例关联了生成、巩固、失败防护与认知卸载风险。将中等体量示例保留在安全防护附近更为妥当。 |
| `skills/curriculum-assessment/curriculum-knowledge-architecture-designer/SKILL.md` | 7,700 / 1,745 | 3,770 / 1,745 | **已编辑。** 移出扩展湿地案例；保留混合比例与评价模式张力。类型定义、硬/软链条、枢纽/视角、四阶段倾向、六项输出、判断边界与近似比例局限均保留在内联正文中。 |
| `skills/curriculum-assessment/discipline-specific-critical-thinking-task-designer/SKILL.md` | 6,686 / 1,928 | 6,686 / 1,928 | **无明确收益。** 一战示例将特定提供的知识基线、学科标准、任务、智力资源与评价串联起来。这个中等体量的完整任务有益地演示了内容依赖型思维；本工作包中未发现需要新建文件的导航问题。 |
| `skills/curriculum-assessment/kud-knowledge-type-mapper/SKILL.md` | 8,187 / 2,358 | 4,657 / 2,358 | **已编辑。** 移出扩展情绪调节案例；保留对比技能/倾向行以及私人习惯边界。全部类型定义、强制 Do 拆分、评价路由、复合标志、知识依附性先备条件与输出字段均保留在内联正文中。 |
| `skills/curriculum-assessment/project-brief-designer/SKILL.md` | 5,533 / 1,534 | 5,533 / 1,534 | **无明确收益。** 河流调查任务书结合了学生作品、里程碑、教师教学图谱与差异化。保留单一可用的完整任务书可避免为了微小激活节省而割裂师生视图。 |
| `skills/curriculum-assessment/scope-and-sequence-designer/SKILL.md` | 9,351 / 2,658 | 5,264 / 2,658 | **已编辑。** 移出扩展福祉项目案例；保留其显式输入状态与置信度限定。A–E 路由/状态 E 拒绝、全部先备/覆盖逻辑、元认知例外、教师提问、违规检查与输出均保留在内联正文中。 |
| `skills/historical-thinking/contextualisation-skill-builder/SKILL.md` | 5,031 / 1,138 | 5,031 / 1,138 | **无明确收益。** 1892 年宣言案例演示了如何运用语境而非仅仅复述哥伦布评论。进阶、示范、提示与错误模式构成单一简短教学序列。 |
| `skills/historical-thinking/document-based-lesson-designer/SKILL.md` | 5,281 / 1,574 | 5,281 / 1,574 | **无明确收益。** 两课时的史密斯/波卡洪塔斯计划在同一时间表内连接了史料探究、策略教学、讨论、写作与评价。接近阈值的单一完整课例适合保留在内联。 |
| `skills/historical-thinking/sourcing-skill-builder/SKILL.md` | 5,971 / 1,534 | 5,971 / 1,534 | **无明确收益。** 成对的史密斯记述展示了从注意作者到推理出处的转变。将示范序列、提示与失败模式放在一起支持了该区分，无需额外读取资源。 |
| `skills/montessori-alternative-approaches/uninterrupted-work-cycle-designer/SKILL.md` | 5,678 / 1,131 | 5,678 / 1,131 | **无明确收益。** 90 分钟工作周期案例使实际时间、材料、教师观察与过渡可操作化。拆分单一可管理的课堂常规只会增加导航成本而无已确立的执行收益。 |
| `skills/original-frameworks/developmental-progression-synthesis/SKILL.md` | 5,659 / 2,528 | 5,659 / 2,528 | **无明确收益。** 双 LT 分析推理案例将提供的 KUD 同时连接至矩阵与发展指南。将 Type 2/Type 3 对比保留在近处可防止混淆表现进阶与倾向证据；源文件体量适中。 |
| `skills/original-frameworks/learning-target-authoring-guide/SKILL.md` | 11,743 / 1,938 | 6,927 / 1,938 | **已编辑。** 移出两个扩展胜任力示例；保留分类表、能力/倾向警示以及 Band A 观察指标。完整的分类/撰写/检查清单/输出步骤与实践者局限性均保留在内联正文中。 |
| `skills/original-frameworks/seeds-regenerative-inquiry-cycle/SKILL.md` | 6,118 / 1,805 | 6,118 / 1,805 | **无明确收益。** 庭院案例将同一真实场所贯穿全部五个阶段、守护行动与诚实影响记录。跨阶段连贯性很有价值；移出这一中等体量的完整循环未见明确收益。 |
| `skills/original-frameworks/self-determined-project-design-protocol/SKILL.md` | 6,536 / 1,666 | 6,536 / 1,666 | **无明确收益。** 气候书籍案例将学生自主权与独立导师研究、并行知识获取、里程碑、完成与可行性校准联系在一起。单一中等案例保留了这些跨阶段联结，无需单独的参考依赖。 |
| `skills/professional-learning/lesson-study-cycle-designer/SKILL.md` | 5,005 / 1,136 | 5,005 / 1,136 | **无明确收益。** 组合图形案例将四次会议连接至研究课、学习者观察与课后研讨。这个接近阈值的可运行循环从拆出另一文件中未见明确收益。 |
| `skills/professional-learning/pedagogical-content-knowledge-developer/SKILL.md` | 7,510 / 1,991 | 4,042 / 1,991 | **已编辑。** 移出扩展压力科学案例；保留烟雾报警器表征行及其失真与年龄警示。七步法、输出契约、主题特异性与高风险核查局限保留在内联正文中。 |
| `skills/professional-learning/technological-pedagogical-content-knowledge-developer/SKILL.md` | 7,472 / 2,085 | 4,234 / 2,085 | **已编辑。** 移出扩展一战/AI 案例；保留两阶段思维需求建议以及完整的示例数据隐私子章节。TCK/TPK/TPACK、核查、自主性-依赖性、非 AI 跳过、伦理与放弃决策均保留在内联正文中。 |

附录 B 之外的额外重叠决策：

- **Dispositional Knowledge Assessment Designer — 已编辑：** 正文/核心 `13,754/5,955 → 9,754/5,955`。移出完整的示例性 Agency 案例；完整方法与全部六项必需输出保留。未添加组件选择输入或可选择输出接口。完整的工作负荷计算保留在内联，因为它在采用前影响可行性。仅为了满足 5k 而缩减该核心被延后，视为无正当理由的契约风险，而非本工作包未完成的要求。
- **Panel Review — 已编辑：** `11,717/4,967 → 6,870/4,967`。移出冗长对话记录，同时保留每项操作性角色/维度/输出要素。均值/底线解读保留为紧凑示例；模拟与启发式警示保留在内联。
- **KUD Chart Author — 无明确收益；未变：** 当前正文/核心 `6,286/3,513`。新近修正的路由与来源拆解说明连同其示例保留在一起。相对于打乱刚刚审阅过的上下文，进一步可选拆分收益有限；未行使可选编辑权。

## 精确保留回执

所有哈希均为 UTF-8 字节的 SHA-256。头部哈希包含原始分隔符与字段；每行单一核心哈希表示**改前 = 改后完全相等**，而非近似语义相似。这些哈希描述的是当前已验收修改前即刻状态的提取行为，不代表宣称加载器暴露了所有周边源章节。

| 源文件 | 改前文件哈希 | 候选文件哈希 |
|---|---|---|
| `skills/original-frameworks/learning-target-authoring-guide/SKILL.md` | `18e3f6f69e3ee62a83b16340fa0301883add3db700e19821490b00866761eff1` | `51b0eb995a87150cc9209cec07ac3c41e9f965159c77e483a395abcf8b477089` |
| `skills/original-frameworks/dispositional-knowledge-assessment-designer/SKILL.md` | `8bfdb8fb8ff536bf67b29e8e628481b10d0f91547866b9d55ae0876342556f95` | `529ffc68bbced5e994ed184968c022e24ecf862f9aa7147f67097a7f5d3e13ff` |
| `skills/professional-learning/panel-review/SKILL.md` | `5c2b15f3c92f3ae725b1c996cc8d982bba435084c17f6096eab38ba6b048918c` | `cbd87bf743f93c227711360c857d3105d147c73b0e477da8637f62492b9e5f10` |
| `skills/professional-learning/pedagogical-content-knowledge-developer/SKILL.md` | `f8a431f23538c5fda43b6eba12ea790e389646049dc24234d86ce5ba180808b5` | `d86f495722e7661d4559a3e058309c35bb1d74caa0a39189c60c7f9954f28c58` |
| `skills/professional-learning/technological-pedagogical-content-knowledge-developer/SKILL.md` | `bba497e20abdd748a52f32c7b4b18c4c8ba1ba212db8531fddac20c5f73558f1` | `40b72a8ced93ec2a48b840c55672311495aa9cb3b6847c9f4ddeeb7855ce30ea` |
| `skills/curriculum-assessment/scope-and-sequence-designer/SKILL.md` | `20630a379803fb5023608904748531e3e03b3d9dad7d554901f0885ed5a9d9de` | `7325fe9b74c40f297c666871b6815094cee45fcbcee76e732564e27ce9a08262` |
| `skills/curriculum-assessment/kud-knowledge-type-mapper/SKILL.md` | `8cd13e8b3ba6829d235aca41a2f3ff7966ab13f57d63a8fbdab1b54b368b6479` | `f8b132fe02b90a767a00848557641a8ec5e6e32ba4d4c59a17bf084423d98da5` |
| `skills/curriculum-assessment/curriculum-knowledge-architecture-designer/SKILL.md` | `e3c6ea6c5c0786ee96bf1d81ee5d33d0d98e969bc73ac657cbeced6587571a18` | `fdf20cd0cd9e72485f9623301aab52ce9c11e62302755f58fda63c020c79dab5` |

| 源文件 | 原始头部 改前 = 改后 | 提取 MCP 核心 改前 = 改后 | 原样移出资源哈希 |
|---|---|---|---|
| `skills/original-frameworks/learning-target-authoring-guide/SKILL.md` | `79912cb6b18588045945f91e51fabfa763f6df36dd0d069d2238d40aa8601259` | `0cd4f6c0e36fb8277312c29144ed4614adbd24495eb1aac40c67fdc5f11aa582` | `20bd27fc8307cea66cb71f4bab62b3a0550c8e2f9694ef03d8b53071fd0b4630` |
| `skills/original-frameworks/dispositional-knowledge-assessment-designer/SKILL.md` | `afa0296ca467634b77f87c80b65c04e0cea54a3b50b7960150d2f63d281fbcef` | `749c369e4744d9fe29ae1d3865d270a6bdd0c02d086e7690f3c2023db0362ae9` | `80b2b650f4bddd21b4ca45212cdc11152b8e1c77087f6bee8d1b9e1ef0bc4798` |
| `skills/professional-learning/panel-review/SKILL.md` | `9ec769e5d945542762a58da40807d9715ae5a87234f376028ade9006acfb72ec` | `8e059185c6ee6460e0283d651ec00981811ef649b322c0d5533fcc97608245c7` | `5942f2f46482f0f677f57aeb328db85b46eea5004a0165b4f3ac39d44e49bcc4` |
| `skills/professional-learning/pedagogical-content-knowledge-developer/SKILL.md` | `5988457cf853a97ba58eca0c4df482dfeb96715976bf1fdf119f3ef84e209edd` | `8c473a46349a05efb14b33971c0d63f54b180ccaed7043893e174a6c10e24d89` | `affdd36e563aa6fb115c4c5b5bcf732c2ebedb6ca04fd03ff24ed36ae59fecad` |
| `skills/professional-learning/technological-pedagogical-content-knowledge-developer/SKILL.md` | `6429f9638064104d2198aa466fdf4c14496eb8387ca27a7bece5babeb62467c5` | `4beb4630aa8e5930d570dbfb86f9c0d283cc6feb6f18b63c30bce15d2fb9e936` | `16a4799855aeee633573ccff56eef2a3bd8f87206b6566c933a1a54e8b57c8f0` |
| `skills/curriculum-assessment/scope-and-sequence-designer/SKILL.md` | `269625c6961ef1161f54b3a93068e1e61e614ba4a09b0d1079ed634db19b4ad6` | `c1a86fd646500a191ba3dfca6270c5bcd9eb0470125acc77bb4b13d9b067a3e9` | `3a9a7b501a0460c72755c8569244e15673e94a971ebea383ca56930a6bb5cab3` |
| `skills/curriculum-assessment/kud-knowledge-type-mapper/SKILL.md` | `d4fe728dd187a377e3b13948db149c2204f5626fbc66c8c69222e2234fab76fb` | `01bf6efd5cb2e568ee860ee2fc85cf9326b738f10bb240236f91f881730343af` | `f0d6772f1d6c1a4488617a25e30cd2af5ef55c54221315af3b3773d14f7428cc` |
| `skills/curriculum-assessment/curriculum-knowledge-architecture-designer/SKILL.md` | `3bea41d7645ec5b6c5fba4fe765814677848e06e52b701c324241c7392540179` | `3d45893a266b09ec059c3dffaaab63d413702a88d719770efdf6f05f7c1a599b` | `ee30e4a92e7176f0ca8392d1347ebab2f4231515d4c6a81d31789a8409f0a12c` |

## 实际执行的检查

1. 修改前快照：任何编辑前将全部 165 个当前 `SKILL.md` 文件复制到 `/tmp/selective-organization-before-20261022/skills/...`。精确变更映射与替换：`/tmp/selective-organization-map-20261022.json`。详细检查的 token/哈希清单：`/tmp/selective-organization-checks-20261022.json`。
2. `/tmp/education-skills-audit-20261022/venv/bin/python /tmp/check-selective-organization-20261022.py` — **通过（PASS）**。使用已验收的导出器解析器解析全部 165 个富源文件。断言其余 157 个非负责源文件字节未变；8/8 原始头部与当前加载器提示词相等；精确前缀/后缀保留；精确资源文本/区间/哈希；主文件加参考资料保留了每一行实质性旧行；8 个现有技能本地相对链接无路径穿越或符号链接。将全部八个完整文件夹复制到临时外部选择性安装位置并比对每个文件字节。运行临时 165 技能便携导出并确认全部八个精确资源字节与清单条目。临时副本/导出已自动移除。
3. `/tmp/education-skills-audit-20261022/venv/bin/python -m unittest discover -s tests -p test_standard_export.py -q` — **15 项测试在 3.774 秒内通过（PASS）**。覆盖现有的便携元数据/正文/许可证、确定性导出、附属文件、独立复制及防御性资源/导出测试。未削弱任何测试或断言。
4. `/tmp/education-skills-audit-20261022/venv/bin/python scripts/validate-skills.py` — **165 项已校验，零错误，一条提示警告**：`learning-target authoring` 仍为 517 行。保留该警告；它并非教育失败或删减核心指导的理由。
5. 范围内 `git diff --check -- <eight source paths> <eight reference paths> <report>` 与直接的新文件空白/末尾换行检查 — **通过（PASS）**。全部九个新建文件均干净且以换行符结尾；八个现有源文件保留其继承的末尾换行状态。初次故意更宽泛的检查曾标出 `learning-target authoring` 原本就缺少末尾换行；将检查范围限定至新文件并核实继承状态后，避免了无关的源尾部编辑。未针对纯源文件的示例移动重跑广泛的运行时测试套件。
6. 一次独立的 Node 调用执行了从当前 `mcp-server/src/skill-loader.ts` 读取的精确 `extractPrompt` 函数（仅移除了 TypeScript 参数/返回类型注解）。**全部八个当前提取提示词哈希**与 Python 回执一致，包括继承的嵌套围栏行为。
7. 临时编辑辅助脚本最初因断言停止，因为其 KUD 行选择器也匹配了差距分析行。第一次收窄移除了一处重复；第二次收窄移除了另一处，随后重跑完成。辅助脚本在恢复前将任何已写入的候选与精确预期字节进行了比对。上述最终结构检查首次运行即通过。未为了迎合选择器而丢弃或编辑任何内容；该问题仅影响临时辅助脚本。

## 人工阅读与局限性

以下为文本走查，而非已执行的模型测试：混合类型胜任力在加载任一扩展示例 LT 之前仍会到达完整的分类/模式/输出步骤；能动性评价仍产出全部六个组件并在内联暴露 163–223 分钟估算、可选照护者路径与可行性问题；评审小组仍可用全部七份角色简报、角色特定维度、输出形态与“无角色低于 70 分”的底线计算；映射依然对比任务评价技能与纵向倾向，并将私人习惯置于学校监控之外；且 TPACK 案例在可选阅读完整历史场景前仍保留学生的初始思考及其隐私条件。

此前位于可选示例区间之外的所有核心指令均保留在完全相同的源字节处，包括完整的学习目标撰写步骤——即便当前 MCP 提取器会在较早的嵌套围栏处终止。刻意保留了现有的提取行为；本组织工作包不修复或认证历史适配器的完整性。此处未重新裁决或重写任何基础主张、示例算术、教育矛盾或研究发现。原样移动示例保留了其已验收的内容与已披露的局限性；这并不使该示例成为新近验证的内容。

仅 Markdown 源视图变小。未实测已安装 Claude/Codex/Hermes 客户端中的参考资料加载行为、任务输出、计费、学习者成效与托管行为。不宣称任何新的客户端/参考资料服务能力。协调器负责独立只读验收以及后续任何注册表/打包产物重新生成、集成、文档或发布。本工作代理未启动任何后续阶段。

审阅本有界候选无需任何产品决策或新的创始人授权。未引入任何未决的教育学含义或接口变更。独立审阅为待办门禁；本报告不将候选标记为已验收。工作代理计数：仅本工作代理；派生工作代理：0；继承历史例外：0；模型/输出对比：无；可用已核实 Token/额度遥测：不可用。
