# 便携配置文件与 Codex 安装报告 — 2026 年 10 月 22 日

确定性便携版导出器现已产出全部 165 个技能，同时未修改任何规范 `SKILL.md`、注册表、打包产物或已验收的 MCP 运行时文件。
全部 15 项新增导出测试均已通过，涵盖完整元数据/正文一致性、许可证/资源/策略复制、独立复制、确定性重复导出以及畸形/冲突/路径穿越/覆盖防御。
固定版本的官方参考 CLI 校验通过 165/165 个导出并在 `to-prompt` 中收录 165/165；现有本地测试套件报告 21 项通过，其仅限托管测试被跳过。
在隔离存储中，Codex 0.163.0-alpha.11.1 成功注册、安装、列出、移除并重装了该插件，其缓存包含全部 165 个未变更的源技能、20 个领域路径以及精确的 12 个仅显式调用策略附属文件。
指南记录了源文件对比便携版的使用方式、缓存刷新以及调用限制；未执行模型激活、真实客户端安装、提交、推送、发布或部署。

## 变更内容

- 新增 `scripts/export-standard-skills.py`、`scripts/validate-standard-skills.py`、`tests/test_standard_export.py` 与 `requirements/standard-validation.txt`。
- 生成被忽略的 `dist/agent-skills/<slug>/` 输出，包含仅标准前置元数据、字符串 `education.*` 元数据、位于 `references/education.json` 的完整原始元数据、源文件内容哈希、`LICENSE` 以及位于确定性元数据指引之后原样保留的原始正文。
- 资源复制包含 `references/scripts/assets/agents` 下新授权的未追踪文件，并保留可执行权限位。拒绝所有符号链接、无效或重复 YAML 键、非 JSON 值、路径穿越名称、重复名称/ID 与保留元数据冲突。仅当存在有效导出器回执且记录文件未修改时才允许替换现有输出；拒绝覆盖任意目录或用户修改。
- 将市场 `source.path` 修复为 `./`；保持两个插件领域数组未变。仅针对必需的 12 个 `disable-model-invocation: true` 技能添加 `agents/openai.yaml` 策略（`allow_implicit_invocation: false`）；其余 153 个技能无策略文件。
- CI 保留现有的项目/注册表/打包/MCP 检查，新增导出往返与固定版本官方校验，使打包检查依赖于校验，声明只读仓库权限，并将 Actions 固定至独立验证过的上游 SHA。
- 围绕实际 CLI 注册加安装、已测试计数、新会话指引、源/便携选择以及移除/重装缓存更新重写了 `docs/CODEX.md`。

## 命令与结果

| 命令/检查 | 结果 |
| --- | --- |
| `/tmp/education-skills-audit-20261022/venv/bin/python -m unittest discover -s tests -p test_standard_export.py -q` | 15 项通过，耗时 3.837 秒 |
| 同一解释器，两次运行 `scripts/export-standard-skills.py` | 各 165 项；回执与每项记录的输出内容哈希完全一致 |
| 同一解释器，`scripts/validate-standard-skills.py` | `skills-ref 0.1.0`：validate 165/165；to-prompt 165/165 |
| 对每个导出目录运行 `/tmp/education-skills-audit-20261022/venv/bin/skills-ref validate <exported-skill>` | 165/165 退出码 0 |
| 同一参考 CLI，`to-prompt <all 165 exported directories>` | 退出码 0；XML 解析并计数为 165 |
| `npm test -- --reporter=line` | 21 项通过，1 项既有仅限托管跳过，耗时 1.5 秒 |
| 同一虚拟环境解释器，`scripts/validate-skills.py` | 165 项已校验，0 错误，4 条既有警告 |
| `python3 scripts/validate-registry.py` | 有效：165 技能，20 领域 |
| `codex --version`、相关 `plugin`/`marketplace`/`add`/`list` 帮助 | 已检查版本与精确命令语法 |
| 隔离环境 `codex plugin marketplace add <repo> --json` | 退出码 0；`marketplaceName` 为 `education-agent-skills` |
| 隔离环境 `codex plugin add education-agent-skills@education-agent-skills --json` | 退出码 0；已安装版本 2.1.0 |
| 隔离环境 `codex plugin list --marketplace education-agent-skills --json` | 退出码 0；`installed=true`、`enabled=true` |
| 隔离环境 `codex plugin remove education-agent-skills@education-agent-skills`，随后再次 add/list | 全部退出码 0 |
| 已安装缓存检查 | 165 个 `SKILL.md` 字节与检出目录相等；20 个领域路径；12 个策略；无 `.env`/`auth.json`/`credentials.json` 文件名 |
| `git ls-remote` Action 标签 | checkout v4.2.2 `11bd71901bbe5b1630ceea73d27597364c9af683`；setup-python v5.6.0 `a26af69be951a213d495a4c3e4e4022e16d87065`；setup-node v4.4.0 `49933ea5288caeca8642d1e84afbd3f7d6820020` |
| 工作流解析/权限/锁定断言与范围内 `git diff --check` | 通过 |

在调用其 API/CLI 之前，已检查位于 `/tmp/education-skills-audit-20261022/standard/skills-ref` 的参考源码：解析器、校验器、提示词生成器、CLI 与包定义。CI 固定了上游提交 `69ef37e9424c0a7ea9dd2293b559e43ec8176379` 与运行时依赖版本；项目源文件校验保持为独立检查。

基线输入内容 SHA-256：`e0225e3db70e4ca90f934972d972ad88d5f9acafc06761f3c88c04aaee6a330b`。
重复导出回执 SHA-256：`077fdb6ebf4556c7a9035c1143120a0accd3da0b29cf102523f08ab240d1674b`。
源回执涵盖全部源 `SKILL.md` 字节、随附资源字节与 `LICENSE`；它包含工作区编辑，而非宣称仅 Git HEAD 即代表被评估内容。后续获批的内容变更需要重新运行导出与校验。

## 局限与清理

- 最初使用系统 `python3 scripts/validate-skills.py` 时缺少 PyYAML；改用提供的工具虚拟环境后通过。未更改系统解释器包。
- 开放格式没有全局统一的仅显式调用控制。Codex 附属文件编码了该客户端的控制；原始标志保留在富元数据中。通用客户端可能会忽略它们。格式校验不证明可移植策略执行、教育认证、模型选择或实际激活。
- CLI 测试使用了全新的进程级 `CODEX_HOME`、XDG 配置/缓存/数据目录，且未复制任何凭据。未发生付费或托管模型执行，也不宣称测试了实际模型发现/显式调用试验或桌面端重载。
- CI YAML 与组件命令均在本地检查；未在远程执行 GitHub Actions。未重复现有的 MCP 运行时测试，因为该独立验收的工作包受保护。在未配置端点的情况下，仅限托管的根目录测试保持未执行。
- 记录结果后已移除隔离客户端存储与缓存。本工作包未留下任何服务器、数据库栈或后台进程。生成的便携输出继续保持被忽略，可在本地审阅。
- 未派生子代理；未进行源内容编辑、提交、推送、发布、真实客户端更改或数据库操作。本工作包已准备好交由协调器进行独立审阅与最终合并集成。
