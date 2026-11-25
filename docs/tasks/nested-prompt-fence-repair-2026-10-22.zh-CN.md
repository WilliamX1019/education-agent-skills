# 有界嵌套提示词围栏修复

预期成果：修复已验证存在的 Learning Target Authoring Guide MCP 截断问题，同时不改变其教育指令文本或任何其他技能的提示词。此举在 Gareth 授权的构建范围内，并保留所有已验收的源码组织/内容工作。检出路径 `/Users/garethmanning/Github/education-agent-skills`，分支 `codex/agent-skills-standards-quality-2026-10-22`，HEAD `6bbbce418f82e11044009c9f3b7373a354de5bd0` 加已验收的工作区编辑。通读 AGENTS/CLAUDE/STATE、`docs/tasks/selective-organization-2026-10-22-report.md` 与 `-review.md`；组织门禁状态为 ACCEPT。

负责：仅限 `mcp-server/src/skill-loader.ts` 中的 `extractPrompt` 围栏分支；仅限 `skills/original-frameworks/learning-target-authoring-guide/SKILL.md` 外层 Prompt 围栏；`mcp-server/tests/skill-loader.spec.ts` 中有意义的提取回归测试；回执 `docs/tasks/nested-prompt-fence-repair-2026-10-22-report.md`。勿触及其他运行时函数、源内容、前置元数据、参考资料、清单、schema、与提取无关的测试、注册表/打包产物/导出或文档。你并非独自工作；保留所有已验收的工作区编辑。禁止子代理、提交/推送/发布/部署/模型调用/托管调用/真实设置/服务器。

已验证故障：加载器第 60 行当前正则在遇到第一个三反引号序列时即停止；LT 源文件外层起始于 111 行，内部代码围栏 207–237 行，外层结束于 488 行。提取出的提示词在指标模板与其余方法/输出规则之前的“Format:”处截断。请在现有提示词外围使用正确长度的更长外层围栏（例如四个反引号），并在围栏提取中支持匹配实际起始围栏长度及完整闭合行。保留原三反引号用例以及两个无围栏 h1/h2 回退。勿重写方法或强制要求可选示例；不作解析器/库迁移。代码文本与内部示例保持精确不变。检查完整指南与实际预期结束边界，而非仅仅测试添加的关键词。

编辑前使用当前加载器捕获全部 165 个修改前即刻加载的提示词及原始元数据/描述/工具名称。编辑后，恰好只有一个提示词有意变更：LT 提示词必须等于其外层围栏之间去掉首尾空白的完整原始预期提示词内容，包含内部围栏/模板与最终方法检查清单，排除 Example Output 与 Known Limitations。其余全部 164 个提示词字节与全部 165 条元数据/描述/工具名称保持未变。除两处外层围栏分隔符外，LT 原始头部及全部指令/参考文本精确不变。现有组织报告保持历史记录；回执仅明确取代其 LT 提取提示词一致性哈希。所有其他源文件未变。

测试：运行前检查测试/脚本；添加有意义的常规围栏/嵌套长围栏/闭合行行为以及既有的 h1/h2 回归（若未覆盖）；通过临时夹具使用导出的 `loadSkills`，而非不必要地导出生产辅助函数。运行聚焦 `skill-loader` 测试与 `npm run build`。暂不需要生成产物集成或全套测试；独立审阅后由协调器负责。提供 Python 虚拟环境 `/tmp/education-skills-audit-20261022/venv/bin/python`。汇报精确的前后哈希与提示词长度、预期边界等价性、164 项一致性、实际命令/结果与局限。仅因实质性接口不确定性停止；保持这是一次微小修复并返回供只读审阅。
