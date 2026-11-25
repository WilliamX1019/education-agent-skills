# 公开发布与托管服务退役准备

目标：准备 GitHub 发布 v3.1.0 并退役由本库运营的公共 MCP 路由，同时保留本地/自托管 MCP 以及所有经审阅的技能功能。Gareth 明确授权发布 GitHub/release/下载、更新/标准说明及退役；明确跳过成本/用量审查。独立教育项目。检出路径 `/Users/garethmanning/Github/education-agent-skills`；分支 `codex/agent-skills-standards-quality-2026-10-22`；继承 HEAD `6bbbce418f82e11044009c9f3b7373a354de5bd0` 连同已验收的未提交构建。你并非独自工作；保留先前编辑。禁止子代理。

负责：`README.md`、`CHANGELOG.md`、当前指南 `docs/{AGENT_SKILLS,ARCHITECTURE,SKILL_QUALITY,CODEX,HERMES,HOSTED_MCP_ACCESS,PRIVACY}.md`、`mcp-server/README.md`、仅 `CLAUDE.md` 当前导言、仅必要时 `AGENTS.md` 导言措辞；仅 `.claude-plugin/plugin.json` 与 `.codex-plugin/plugin.json` 版本号；仅 `mcp-server/vercel.json` 增量添加 `git.deploymentEnabled: false`；新建 `docs/releases/v3.1.0.md`；你的报告 `docs/tasks/public-release-retirement-2026-10-22-report.md`。禁止技能/源元数据/资源/ID/schema/运行时/测试断言/注册表/打包产物/导出/审计历史/许可证变更。根协调器负责 `STATE`/当前状态/发布证据及外部操作。工作代理禁止提交/推送/PR/合并/发布/部署/配置变更/模型调用/真实设置修改；审阅后由根协调器执行。这仅就工作代理归属权取代新任务的默认提交/推送指令，不取代用户的发布授权。

通读 `AGENTS`/`CLAUDE`/`STATE` 与精简构建状态、现有 README/当前指南及当前构建验证。官方便携版 165/165 结果是在固定参考提交 `69ef37e9424c0a7ea9dd2293b559e43ec8176379` 处验证的，而非基金会认证或宣称官方 1.0/v2。未提供具体 X 贴文 URL：勿捏造或暗示背书。官方规范 `https://agentskills.io/specification`。规范富格式源文件与便携版导出继续清晰区分。不宣称模型行为/教育成效认证。先前的 111 项测试（75 MCP + 21 技能库 + 15 导出）、1 项托管跳过与客户端局限均在回执中；勿捏造新鲜证明。

发布标签 `v3.1.0` 承接现有历史项目的 `v3.0` 里程碑；仓库此前无现有发布/标签（根协调器已查）。将两个插件清单从 `2.1.0` 升至 `2.2.0` 以便缓存可见更新，保留所有其他字段/20 领域数组。根/MCP npm 版本不变，因为本次范围不含 npm 发布；schema 2.0 与便携配置文件版本不变。更新当前解释性版本表格，勿改历史测试回执/旧更新日志正文。新增当前 GitHub 发布说明，包含简短人类可读摘要、稳定 ID/接口、37 项针对性修订/8 项重组、严格便携版 165 通过、隐私/正确性/安装/运行时改进以及诚实测试/客户端局限。

`README`：导言附近添加简短带日期更新说明；当前主要路径为 GitHub 发布便携下载、源码插件/手动、本地/自托管 MCP。链接 `https://github.com/GarethManning/education-agent-skills/releases/tag/v3.1.0` 与资产 `education-agent-skills-portable-v3.1.0.zip`。平实解释标准对齐并指向官方规范/验证。移除作为受支持服务的活跃注册邀约/生产 URL/配置；说明公共托管 MCP 随本发布退役（根协调器稍后确认实际暂停）。仅保留清晰标为已退役的旧 URL，绝不邀请获取令牌/注册。现有仅远程用户需要本地安装/手动或自建托管端点；不保证无缝自动迁移。避免营销式重写/冗长历史。

`mcp-server/vercel.json` 保留所有重写规则并添加 `git.deploymentEnabled: false` 以阻止自动 Git 部署（Vercel 官方文档确认 `https://vercel.com/docs/project-configuration/git-configuration`）。文档/自托管指南须说明托管方必须主动选择自己的部署，并在使用邮件时自行配置认证/基础 URL/邮件服务；本地 stdio 无需 Vercel/令牌/邮件配置。勿削弱/删除现有 OAuth/认证/运行时源码。解释公共注册已退役但源码保留供自托管者使用，仅当他们启用时才适用服务商处理。不断言零 Vercel 账单/存储费用，也不断言现有凭据已吊销/删除。GitHub/本地分发无需新部署；不将占位符生产值呈现为我方服务。

检查：聚焦 JSON/版本/领域数组/配置断言、所有新当前本地链接/锚点、完整文件夹便携消费方说明与实际输出形态一致（根协调器将创建包含 `agent-skills/` 165 文件夹 + 安装说明的 ZIP）、当前源/资源/注册表/打包产物哈希未变。适当时运行根目录库套件 `env -u HOSTED_MCP_BASE_URL npm test -- --reporter=dot`；仅文档/配置编辑无需重跑 111 项测试或外部调用。未经检查勿运行任何脚本。汇报精确编辑/命令/结果/局限与修改前即刻快照路径。在候选就绪供独立只读审阅后停止。不承担后续阶段归属权。

活跃实施期间的有界发布版本例外：根目录测试套件暴露出 `tests/skills-library.spec.ts:217` 硬编码了 `2.1.0`。仅将该预期字面量更新为 `2.2.0` 以匹配获批的清单发布，保持断言强度与所有其他断言不变。包含该文件的修改前快照/增量并重跑套件。这仅就该精确发布预期取代一般性的“不编辑测试断言”边界。
