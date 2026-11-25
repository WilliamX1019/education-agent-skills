# 贡献指南

感谢你考虑为 Education Agent Skills Library 做出贡献。本库的标准刻意定得较高：每个技能都应当有证据支撑、具有实用价值，并且表述清晰，以便教育者与 AI 代理都能安全使用。

## 适合纳入的内容

优质的贡献通常会新增或改进可复用的教育技能，以支持以下需求之一：

- 课程设计；
- 评价设计与效度检验；
- 学习科学与记忆研究；
- 自我调节学习与元认知；
- 读写能力、提问、对话与批判性思维；
- 福祉、动机、归属感与学生能动性；
- 包容性设计；
- AI 素养或 AI 学习支持；
- 面向学生的学习互动；
- 教师专业学习；
- 清晰标注的系统思维或实践者原创框架。

## 纳入标准

一个技能应当：

1. 解决一个反复出现的教学设计或学习支持问题；
2. 适用范围超越单一学校、课程或课节；
3. 在声称有研究支撑处列出具名的证据来源；
4. 如实标注新兴、混合、实践或原创框架证据；
5. 保留教育者的专业判断，而非假装技能可以决定一切；
6. 包含清晰的输入与输出 schema；
7. 包含实用的质量检查项与常见陷阱；
8. 避免缺乏支撑的框架，尤其是学习风格/VAK 类主张。

关于被排除的理念请参见 [`docs/EXCLUSIONS.md`](docs/EXCLUSIONS.md)，关于证据来源请参见 [`docs/EVIDENCE.md`](docs/EVIDENCE.md)。[质量指南](docs/SKILL_QUALITY.md)阐述了八项评审标准，但并不取代上述纳入规则，也不要求实证认证。

## 技能结构

技能位于：

```text
skills/<domain>/<skill-name>/SKILL.md
```

除非属于有计划的仓库级迁移，否则请勿重命名或移动现有技能文件夹。

规范源文件使用扩展的项目/厂商前置元数据；严格便携版分发包会单独生成。每个现有的 `SKILL.md` 必须保留：

- YAML 前置元数据；
- Agent Skills 标准所需的 `name` 和 `description` 字段；
- 证据强度元数据；
- 输入和输出 schema；
- 所有现有的引用文献与限制说明。

请将可选资源保留在技能文件夹内部，并在主指令中链接它们。复制/分发时请保持完整文件夹，保留 `references/`、`agents/` 及其他随附资源。对教育学含义的修改需要有清晰的理由、保留性检查以及如[技能质量](docs/SKILL_QUALITY.md)所述的独立内容审阅。请在原位改进稳定的路径/ID；通过 Git 和回执记录保留历史版本，而不是复制多个活跃版本目录。

### 技能 `name` 必须在所有领域中全局唯一

技能的 `name`（及其 `skill_id` 短标识）必须**在整个技能库中全局唯一，而不仅限于其所属领域文件夹内**。Claude Code 和 Codex 通过 `name` 识别技能；扁平的、以名称为键的加载器无法容纳两个同名的技能，否则会导致静默冲突或相互覆盖。（MCP 服务器通过附加领域前缀来容忍重名，但插件接口不支持。）

如果两个技能可能出现重名，请为其中一个赋予更具体的名称——例如使用 `discipline-specific-critical-thinking-task-designer` 而非第二个 `critical-thinking-task-designer`——并同步更新该 `SKILL.md` 前置元数据中的 `name`、`skill_id`、`skill_name` 以及对应的文件夹名称。

### 新增领域文件夹必须同时添加到两个插件清单中

每个插件清单中的 `skills` 字段都是**领域文件夹路径的显式数组**（例如 `"./skills/curriculum-assessment"`），因为 Claude Code 和 Codex 仅扫描一层目录深度，而本仓库的技能嵌套了两层（`skills/<domain>/<skill>/SKILL.md`）。仅写 `"./skills/"` 根路径会导致两个加载器均无法发现任何技能。

当你添加**新的领域文件夹**时，必须将其路径同时添加到以下**两个**文件的 `skills` 数组中：

- `.claude-plugin/plugin.json`
- `.codex-plugin/plugin.json`

（`.claude-plugin/marketplace.json` 通过其 `source` 字段继承配置，无需单独列出技能。）

## 提交 Pull Request 前的验证

请使用 Python 3.11+ 和隔离环境（包括当系统 Python 缺少 PyYAML 时）。在仓库根目录执行：

```bash
python3 -m venv .venv-standard
.venv-standard/bin/python -m pip install -r requirements/standard-validation.txt
npm ci
npm --prefix mcp-server ci
```

新增或编辑规范技能/资源后，重新生成两个受追踪的视图文件：

```bash
.venv-standard/bin/python scripts/generate-registry.py
npm --prefix mcp-server run bundle-skills
```

将项目检查与官方格式门禁分开运行：

```bash
# 项目源文件、注册表及技能库检查
.venv-standard/bin/python scripts/validate-skills.py
.venv-standard/bin/python scripts/validate-registry.py
npm test -- --reporter=dot

# 便携版往返/安全性测试、导出及固定版本的官方格式校验
.venv-standard/bin/python -m unittest discover -s tests -p test_standard_export.py -q
.venv-standard/bin/python scripts/export-standard-skills.py
.venv-standard/bin/python scripts/validate-standard-skills.py

# MCP 构建、运行时契约及依赖安全检查
npm --prefix mcp-server run build
npm --prefix mcp-server test -- --reporter=dot
npm audit --audit-level=high
npm --prefix mcp-server audit --audit-level=high
```

[CI 工作流](.github/workflows/validate.yml) 会在 Node 20 / Python 3.11 环境下运行上述各类检查，并在重新生成后校验注册表与打包产物的新鲜度。本地集成测试结果使用的是 Node 22.23.4 / Python 3.13.2；详见[验证回执](docs/audits/agent-skills-build-verification-2026-10-22.md)。CI 还会将技能数量与注册表进行核对；其工作流锁定了 Action 版本并安装声明的依赖项。本地检查不能证明远程 CI 已运行。除非配置了对应端点，否则仅限托管环境的库测试会被跳过；请勿将被跳过的测试视为托管发布检查。格式与契约测试也不能证明模型激活效果或学习者成效。

在审阅/提交中请包含修改后的**规范技能文件夹及资源**、`registry.json` 和 `mcp-server/src/skills.json`。请勿提交生成的 `dist/agent-skills/`、`mcp-server/dist/`、`.venv-standard/` 或本地测试输出。本地重新构建的快照不等于已部署的托管更新。[开发者指南](docs/AGENT_SKILLS.md)将严格便携版配置文件与固定版本的官方参考工具同源文件 schema 区分开来作了说明。

## Pull Request 指南

在你的 PR 中，请简要说明：

- 修改了哪些技能或文档；
- 为何这项修改具有教育实用价值；
- 它依赖了哪些证据或实践者框架；
- 你运行了哪些验证命令及其结果；
- 保留了哪些有用行为，如何检查了相关的常规/边界情况，以及仍有哪部分尚未验证。

小而有据可依的改进，胜过会稀释技能库质量的宽泛新增。关键不在于拥有最多技能，而在于拥有值得信赖的技能。
