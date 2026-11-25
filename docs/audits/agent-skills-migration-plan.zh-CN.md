# Education Agent Skills — 拟议实施计划

审计日期：2026-10-22。基线 main：`6bbbce418f82e11044009c9f3b7373a354de5bd0`。**仅为提案；以下任何内容均尚未实施。** 开始前请先阅读审计报告、证据与 165 行矩阵。这是一个独立的教育项目。

## 预期成果与受保护部分

使安装流程可靠，并提供一份可通过参考校验器检查的分发版本，同时不丢失教育 schema、文献引用、仅显式调用行为、源 URL 或 MCP/手动使用方式。保留 `skills/<domain>/<slug>/SKILL.md`、全部 165 个 ID/名称、现有教育元数据、提示词以及刻意留空的 `chain_edges` 占位符。作为本计划的一部分，切勿扁平化源码树、创建新的教学法技能、扩展司法管辖范围、更改存储架构、自动激活仅显式调用工作流、发布软件包或进行线上部署。

当前的 `AGENTS.md` 禁止删除或重命名原始前置元数据字段。推荐的便携配置文件路径遵守了这一规定：原始文件继续作为规范源文件，现有读取方保留其契约。下文中的内容修正属于单独明确界定范围的教育工作包；在编辑教育学含义前须先批准该变更集。后续实施请求应将基础设施变更与教育内容变更范围区分开来。

## P0 — 必需的纠偏工作包

### Q0. 移除可执行的前置元数据解析 — 0.5 人天；对当前有效内容无破坏性

**涉及文件：** `mcp-server/src/skill-loader.ts`；`mcp-server/package.json`；`mcp-server/package-lock.json`；拟议的 `mcp-server/tests/skill-loader.spec.ts`；`.github/workflows/validate.yml`。

**现状/证据：** 加载器第 134 行调用默认的 `gray-matter` 引擎。无害的 `---js` 标记会执行代码。CI 打包作业独立于校验作业运行。当前没有任何技能使用 JS 分隔符，且托管请求也不会传入这些文件。

**变更/必要性：** 仅接受普通的 `---` YAML 区块，使用非执行式的安全 YAML 解析器解析，然后保留现有的元数据/运行时校验及提示词提取。在选择引擎前拒绝语言后缀、可执行标签与畸形分隔符。限制允许的 YAML 类型，并在失败时报告文件路径。优先使用现有的现代 YAML 依赖或明确的直接依赖；切勿为了迎合审计建议而降级 `gray-matter`。使任何校验前置条件显性化，但不要依赖 CI 作业顺序作为防代码执行的防线。

**风险/测试：** 标量的解析语义可能存在差异。将全部 165 条解析出的元数据记录与全部提取出的提示词正文同基线进行深度相等比对，测试普通/流式/块状 YAML 及支持的提示词布局，在不执行代码的情况下拒绝 `js`/`javascript`/标签载荷，随后重新构建打包产物并运行 MCP 测试套件。仅对超出当前库契约的可执行/不可信格式刻意触发中断。

### C0. 修复 Codex 市场根目录与安装说明 — 2–4 小时；非破坏性修复

**涉及文件：** `.agents/plugins/marketplace.json:8`；`README.md:47–72`；`docs/CODEX.md:20–58`；`tests/skills-library.spec.ts`。

**现状/证据：** `source.path="./../.."`；当前上游 Codex 从市场根目录解析路径并拒绝包含父目录的组件。已安装的 CLI 未列出任何教育插件。文档只写了注册市场并重启，遗漏了显式的 `plugin add` 步骤。

**变更/必要性：** 将根源路径改为 `./`；在文档中记录注册之后需执行 `codex plugin add education-agent-skills@education-agent-skills` 以及针对已测试版本的启用/新会话行为。将清单根目录说明更新为现有的领域目录数组。保留单个技能复制的回退方案。

**风险/测试：** 旧版客户端可能对根目录有不同解释；记录受支持的版本。使用隔离的临时配置/存储或经审阅的 CLI/API 测试工具（切勿修改维护者的真实插件配置）来列出/安装/发现全部 165 个技能。验证一个显式技能与一个隐式发现案例；仅在授权成本/用量的情况下进行模型试验。简单的“路径存在”断言是不够的。保留 Claude 清单布局与所有源文件路径。

### Q1. 修复依赖门禁并限制 SDK 校验边界 — 0.5–1 人天；旨在保持协议兼容

**涉及文件：** `mcp-server/package.json`、`mcp-server/package-lock.json`、`mcp-server/src/server.ts:22–49`、`mcp-server/src/request-body.ts`、`mcp-server/tests/mcp-server.spec.ts`、`mcp-server/tests/http-auth.spec.ts`、`.github/workflows/validate.yml`。

**现状/证据：** 锁文件 SDK 为 1.30.0，10 条受影响的包记录；高危阈值审计失败。SDK 校验内存通告在 Bearer 认证之后依然相关；数组目前没有元素数量上限。尚未证实在应用 1 MiB 上限下会发生崩溃。

**变更/必要性：** 升级至兼容的 SDK >=1.32.0，并显式将 `maxToolInputElements` 配置在合理最大教育输入略上方；保留字节限制。若仍保留 `proxy-addr` >=2.0.8 和 `fast-uri` >=3.1.8 等兼容传递依赖，一并刷新。在实施时重新评估安全通告。切勿盲目使用 `npm audit fix --force`。

**风险/测试：** 过小的上限会拒绝合法的课程数据。测试常规最大测试集与安全有界的超限数组/对象、413 字节行为、未授权快速失败、现有的 157 个工具/165 个提示词、严格标量 schema 以及所有认证测试。无需开展内存耗尽负载攻击。`npm audit --audit-level=high` 必须通过，或具有逐项论证并经审阅的例外说明。依赖锁变更可能影响受支持的 Node 版本；CI 使用 Node 20，本地审计使用 Node 22。

### S0. 修正合规契约表述 — 1–2 小时；仅限文档

**涉及文件：** `README.md`、`docs/ARCHITECTURE.md:86–121`、`docs/AGENT_SKILLS.md`、`CHANGELOG.md`、`CONTRIBUTING.md`、`scripts/validate-skills.py` 文档字符串/消息；在 `AUDIT.md` 与 `docs/AGENT_SKILLS_V2_SPEC.md` 中添加归档声明，而非重写历史结论。

**现状/证据：** 本地的“v2 标准”/250 字符/厂商控制与开放格式要求被混为一谈；官方校验器通过率为 0/165，而必需的名称/描述通过率为 165/165。

**变更/必要性：** 将规范源文件描述为带有厂商扩展的 Agent Skills；明确区分项目政策与开放规范，并链接至经测试的精确权威来源。在选定配置文件通过前，切勿宣称通过严格校验。说明参考解析器对合法 YAML 子集的限制，而非笼统宣称“所有 YAML 均无效”。如仍有实用价值，保留 250 字符作为本地设计选择。

**风险/测试：** 无运行时风险。执行链接/路径检查与一致性审阅；在没有证据前不得新增任何语义版本号声明或认证徽章。

## P1 — 高价值互操作性与针对性正确性修复

### S1. 增加确定性的便携配置文件 — 1–1.5 人天；增量式/非破坏性

**涉及文件：** 拟议的 `scripts/export-standard-skills.py`；拟议的 `tests/standard-export.spec.ts`（或等效 Python 测试）；`.github/workflows/validate.yml`；`CONTRIBUTING.md`；`README.md`；`.gitignore`。输出为位于 `dist/agent-skills/<slug>/` 下生成的未提交分发产物，而非第二套手动编辑的源码树。

**现状/证据：** 解析时全部 165 个文件均未通过官方允许列表；其中 160 个首先在 strictyaml 流式语法解析器处失败。现有消费方需要丰富的嵌套元数据。开放规范的 `metadata` 映射仅接受字符串值，因此单纯将现有列表/对象移入其中是不够的。

**变更/必要性：** 导出必需的 `name`/`description`、可选的 `license: CC-BY-SA-4.0` 以及字符串值的命名空间元数据（源 ID/修订版与资源路径）。将完整的原始富元数据导出为 `references/education.json`、本地 `LICENSE` 声明以及一条指向该元数据的确定性单行指令。在该附加指引之后原样保留原始正文不变。以兼容固定版本官方工具的块状风格序列化前置元数据。初期保持 Claude 源文件配置与 MCP 加载器不变。显式提供便携版下载包；在证明一致性前切勿重指向现有适配器。在适用处包含生成的 Codex 附属文件。不得存在独立维护的副本、符号链接依赖或手动编辑导出产物。

**风险/测试：** 通用客户端可能会忽略 `metadata`，因此正文指引必须使核心 schema 可被访问。验证 165 个唯一叶子目录；精确的名称/描述/ID；原始正文按字节完整保留为确定后缀；每个原始 schema/引用/标志均保留在 JSON 中；路径保持在包内；存在 `LICENSE`；官方 `validate` 165/165 通过；官方 `to-prompt` 覆盖 165 项；重复导出产生完全一致的哈希。测试在仓库外复制单个选定技能的场景。保持官方校验器版本固定；将项目校验分开运行。基础设施或内容重写均非本项的前置条件。便携配置文件版本控制独立于源文件 schema 版本控制，必须加以记录。

### C1. 在 Codex 中匹配仅显式调用行为 — 2–4 小时；有意的调用修复

**涉及文件：** 在以下现有技能目录中拟议添加 `agents/openai.yaml`：

- `skills/ai-learning-science/cognitive-tutoring-architecture-designer/`
- `skills/ai-learning-science/individual-spacing-algorithm-explainer/`
- `skills/curriculum-assessment/formative-assessment-technique-selector/`
- `skills/original-frameworks/coherent-rubric-logic-builder/`
- `skills/original-frameworks/developmental-band-system-designer/`
- `skills/original-frameworks/developmental-progression-synthesis/`
- `skills/original-frameworks/dispositional-knowledge-assessment-designer/`
- `skills/original-frameworks/learning-target-authoring-guide/`
- `skills/original-frameworks/seeds-regenerative-inquiry-cycle/`
- `skills/original-frameworks/self-determined-project-design-protocol/`
- `skills/original-frameworks/single-point-rubric-designer/`
- `skills/professional-learning/panel-review/`

以及 `tests/skills-library.spec.ts`、`docs/CODEX.md`、导出器。

**现状/证据：** Claude 标志已存在，Codex 附属文件缺失。上游解析器从 `agents/openai.yaml` 读取策略并忽略该前置元数据标志。

**变更：** 以块状 YAML 编码最小化的 `policy: {allow_implicit_invocation: false}`。切勿为每个技能添加不必要的工具依赖或 UI 品牌字段。

**风险/测试：** 降低这 12 个技能在 Codex 中的自动激活率，以匹配既定意图；显式调用依然可用。断言源标志与附属文件 12/12 等价，其余 153 个技能无误设策略，且当前 Codex 元数据解析/发现及显式可用性正常。标准校验不认证调用策略。

### Q2/C3. 修复输入保留与能力真实性 — 2–4 小时；非破坏性修复

**涉及文件：** `mcp-server/src/tool-handler.ts:5–16`、`mcp-server/tests/mcp-server.spec.ts`；`mcp-server/src/oauth.ts:110–122`、`mcp-server/tests/http-auth.spec.ts`、`mcp-server/tests/oauth-handlers.spec.ts`、`docs/HOSTED_MCP_ACCESS.md`。

**现状/证据：** `$&` 替换符会被 JS 解释；OAuth 通告了不受支持的 URL 客户端元数据文档能力。

**变更：** 使用基于回调的替换、转义的 schema 键以及仅匹配原始模板占位符的单遍扫描，使插入的 `{{text}}` 不会被二次处理。移除不受支持的元数据能力通告，而非在本工作包中实现新的客户端注册系统。说明固定的受支持客户端范围。

**风险/测试：** 美元符号、字面量花括号、缺失的可选参数、数组与字符串均须完好保留；保持提示词与用户输入的隔离以及现有模板不变。断言该能力缺失/为 false，已批准的 Claude 流程未变，未知客户端拒绝策略保留。不放宽 OAuth 信任边界。

### E1–E6/E8/E9. 有界教育内容修复 — 1–2 人天外加专家审阅；内容变更需经审阅

**涉及 `skills/` 下文件（均以 `/SKILL.md` 结尾） / 现状问题 / 拟议窄范围修正：**

| `skills/` 下文件（以 `/SKILL.md` 结尾） | 证据 / 问题 | 拟议窄范围修正 |
|---|---|---|
| `memory-learning-science/spaced-practice-scheduler` | `:18,78,113,206`；研究数量有误且将实证最优解泛化 | 修正为 317 项实验 / 184 篇文章；将时间表标注为启发式规则；限定遗忘百分比表述 |
| `student-learning/explain-first-interrogator` | `:23,67`；夸大近期预印本结论 | 引用作者/标题/版本、实际的解释质量终点指标及不确定性 |
| `student-learning/fading-manager` 与 `student-learning/retrieve-first-gate` | `:111–117/:195–203` 对比 `retrieve:148–155` | 统一状态词汇、阈值示例与教师覆盖机制；保留启发式标签 |
| `curriculum-alignment/developmental-band-translator` | `:126` 与 `:148–152` 及覆盖逻辑冲突 | 明确优先级、保守的无年龄处理以及保留来源的审阅标志 |
| `curriculum-alignment/kud-chart-author` | `:129,141` 推荐将元数据标注器用于原始文档拆解 | 指明实际的拆解前提要求，然后再进行标注 |
| `curriculum-assessment/differentiation-adapter` | `:78` 将 2018 版称为最新版本 | 指明所用版本并承认 3.0 版；不作全面重写 |
| `wellbeing-motivation-agency/trauma-informed-practice-designer` | `:284–293` 将紧急披露与常规转介混为一谈 | 经专家审阅的、司法管辖区中立的本地安全保护/紧迫危险路由；保留现有的“非心理治疗”边界 |
| `student-learning/*/SKILL.md`（全部 13 个；矩阵逐一列出） | 无独立的隐私契约；`weekly:237` 提及存储 | 精简的数据最小化、授权存储/保留及人工求助边界；不引入后端 |
| `student-learning/srl-session-wrapper` | `:33–35` 输入未插入提示词 | 增加条件性的中期/结束目标检查与实际的提示词包含 |
| `student-learning/teach-back-evaluator` | `:33–35` 未使用的先备理解上下文 | 有意识地使用传入的输入，同时保留 schema 以保持兼容性 |
| `student-learning/transfer-bridge` | `:177–236` 示例篡改了原始核心原理 | 修正类比与成功标准检查；不接受无关的算术题作为价格形成迁移 |

**原因：** 在不改变整体技能设计的前提下，消除相互矛盾的决策与不准确/安全不完整的指导。

**风险/测试：** 会改变被标记案例的预期输出。开展修改前后的人工内容审阅；针对撤架边界、有年龄/无年龄/覆盖路由、孤立中期目标、原始迁移目标及紧急披露路由运行若干虚构测试集；确保常规任务输出与文献引用保持完整。切勿将通过文本测试宣传为临床或教育实证验证。技能文本变更时重新生成 `registry.json` 与 `mcp-server/src/skills.json`，然后运行源同步/构建/测试。切勿自动部署。

## P2 — 可选改进（各项均可独立回退）

1. **资源拆分（仅在测量上下文开销后开展，0.5–1 人天）。** 精确的初期候选为报告中列出的四个 >500 行文件，拟议搭配技能本地的 `references/` 文件。将强制指令/安全边界保留在主正文中。MCP 目前仅提取 Prompt/System Prompt，因此移出提示词材料需要加载器/打包资源的刻意支持以及完整的提示词一致性测试。切勿按模板一刀切拆分全部 165 个技能。若遗漏资源则存在破坏风险；除非实测有益，否则延后处理。
2. **串联完整性与证据标签（2–4 小时）。** 仅编辑证据附录中列出的 13 个技能路径与 2 个评级路径；在 `scripts/validate-skills.py` 与 `tests/skills-library.spec.ts` 中增加检查。仅在语义匹配确认后映射别名，否则显式标注为外部目标。在 README/`docs/EVIDENCE.md` 中记录所有可接受标签的含义，而非静默改变其含义。重建生成的视图。建议串联并非必需依赖；对声明的外部目标发出警告而非报错失败。
3. **发布/CI 检查（0.5 人天）。** 拟议为 `mcp-server/package.json` 增加 `prepack` 构建、`mcp-server/tests/` 打包后 CLI 冒烟测试、`mcp-server/tsconfig.json`/拟议的 API 检查配置、`.github/workflows/validate.yml` 最小权限/固定 Action 版本/Python 工具版本、`CONTRIBUTING.md:84–90` 移除提交被忽略 `dist` 的指令。干净构建后源测试通过。在临时存储中测试 npm tarball 而不发布；确认无环境密钥或源路径假设。本地缓存输出无需成为受追踪源码。
4. **研究索引/主张（0.5–1 人天外加后续研究工作）。** 修正 `docs/EVIDENCE.md:39` 中的 Woloshyn 引用；标明文献目录对早期领域的覆盖范围。补充稳定标识符/审阅日期，而非复制付费墙全文。在 `professional-learning/panel-review/SKILL.md:3` 中显性化福祉/SEL 适用范围。在 `original-frameworks/developmental-band-system-designer/SKILL.md:85` 中，将“validates”替换为支持理由。复核 `eal-language-development/academic-language-sentence-frame-generator`、`curriculum-assessment/backwards-design-unit-planner`、`global-cross-cultural-pedagogies/cross-cultural-task-validity-checker` 中缺乏充分支撑的 Strong 门槛；不作自动降级。审阅针对性引用，保留现有指导建议。
5. **许可/版本清晰度（1–2 小时）。** `LICENSE`、`mcp-server/LICENSE`、`package.json` 文件、清单、`CHANGELOG.md`、docs。阐明内容/软件许可意图以及不同的插件/schema/服务器/包版本。切勿静默重新授权或强行将所有界面统一为单一版本号。可能需要人工做出许可决策。
6. **托管事件限制（文档 1 小时；共享状态单独评估）。** `docs/HOSTED_MCP_ACCESS.md`、`docs/PRIVACY.md`、`mcp-server/src/oauth.ts`、`src/http-auth.ts`。记录单个令牌吊销与家族吊销的差异以及单实例重放/速率限制。仅当更广泛的托管需求确实合理时，才设计持久化的家族/资源/受众控制；保留现有客户端并要求单独的安全审阅。

## 保持不变的部分

保留源领域/路径、名称/ID、具名研究与诚实局限、教师专业判断、复合技能的 `emerging` 标签、独立提示词、现有类型化输入 schema、注册表与 MCP 快照、仅显式调用标志、本地/手动/离线选项以及可选的托管认证。在真正的设计落地前保留 `chain_edges` 占位符。不要为了本次审计而构建新的编排器、内容引擎、注册表服务、通用安装器或存储平台。

## 实施顺序与验收标准

1. 重新绑定 `main` 并保留任何新的本地工作；比对审计修订版本。捕获源/正文/schema 哈希与协议清单。切勿自动拉取/重置。
2. 实施 Q0/Q1 并使用安全的合成输入测试解析器/安全边界。作为一个有界的基础设施工作包进行审阅。
3. 修复 C0、C1 与 C2 的安装/更新说明；验证实际的隔离环境发现、仅显式调用控制与选择性复制。保留当前的领域清单数组。
4. 修正 S0 契约并添加带有独立项目/参考校验的 S1 导出器。在宣传该配置文件前，要求严格配置文件 165/165 通过且通过元数据/正文/许可证往返检查。现有源文件在扩展源文件继续受支持的同时，可刻意继续不通过严格校验器；精确标注各界面定位。
5. 修复 Q2/C3。变更后运行完整的认证/协议检查；本序列不新增 OAuth 功能。
6. 审阅教育工作包；仅实施经审阅的窄范围变更集，重建生成视图并测试相关虚构案例。
7. 应用可独立获益的 P2 项，或明确延后。记录版本、命令、证据与剩余局限。测试通过不代表允许包发布、GitHub 推送或部署。

必需的最终检查：项目 Python 校验器、根目录测试、重新生成索引的一致性、MCP 干净构建与全量测试、打包后 CLI 冒烟测试、独立的官方配置文件 165/165 校验、许可证/资源检查、隔离的 Claude/Codex 发现与控制检查、若在授权测试范围内则执行选择性 Hermes 安装、依赖安全审计。除非经单独批准的内容变更刻意调整计数，否则测试应保留当前的 165 个提示词 / 157 个工具 / 12 个仅显式调用行为。

## 回滚策略

在后续经授权的实施会话中使用小型独立提交，并预先记录变更前的源/索引哈希以及先前的构建产物。将失败的工作包及其重新生成的视图一并回退；切勿回退无关工作。便携版导出器属于增量组件：禁用/移除其分发引用并保留原始路径即可。移除附属文件无需重命名技能。仅将恢复先前的 `package.json`/锁文件对作为临时遏制手段；切勿将恢复可执行解析或已知依赖风险当作发布修复。将安全修复与内容编辑分开，以免教学内容回滚撤销安全防护。已安装的测试配置文件位于一次性存储中，可在不触及真实设置的情况下移除。托管回滚/发布需要其自身的明确授权与当前部署证据；本计划未授予任何此类权限。
