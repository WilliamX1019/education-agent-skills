# 本地客户端检查 — 2026 年 10 月 22 日

协调器在便携/发现修复前的只读基线检查。无模型运行、安装、认证变更或托管调用。

- `codex --version`：`0.163.0-alpha.11.1`。`codex plugin --help` 确认存在 `marketplace` 和 `add`/`list` 命令。不确立安装/发现/激活。
- `claude --version`：`2.1.307`。`claude plugin validate .`：通过但伴随警告。当前清单 `display_name` 被忽略；建议使用 `displayName`。根目录 `CLAUDE.md` 不作为插件交付的项目上下文。仅限目录列表的图标指引属于提示性建议；未尝试目录提交。报告了磁盘上被忽略的 `.DS_Store` 文件；`git ls-files -- '*.DS_Store'` 返回空，因此它们未通过 Git 分发。切勿为了本任务删除无关的本地系统文件。
- Claude 校验器为 2.1.275+ 推荐 `/plugin install education-agent-skills --marketplace GarethManning/education-agent-skills`。实际激活未测试，且清单校验不意味着激活成功。
- `hermes skills --help`：CLI 存在；支持 browse/search/inspect/install/update/tap。未修改源文件或安装技能。后续便携副本检查可另行记录；不宣称完整的 Hermes 验证。

隔离的 Codex 结果属于便携配置文件工作包报告。未来的 README 必须将这些观察结果与模型行为及托管发布状态区分开来。

## 离线便携配置文件读取检查

`python3 /tmp/education-skills-build-20261022/hermes_portable_read_check.py` 使用已安装的 Hermes 本地 Python API（`skills_list`、`skill_view(preprocess=False)`）运行通过。在特定 `profiles/audit` 目录下新建的临时 `HERMES_HOME` 仅包含 165 个便携技能的副本；环境中不包含任何服务商凭据，且 Python 套接字连接被阻断。Hermes 列出了 165 项；打开了 `learning-target-authoring-guide`、`spaced-practice-scheduler` 与 `confidence-calibration-check` 的主文件及 `references/education.json`。无模型调用、模板/shell 预处理、hub/网络安装器、真实配置文件/配置变更或运行中的服务器。临时文件已清理。

本次首次运行读取的是内容修订前的导出产物。在组织变更后应针对最终重新生成的配置文件重复检查，并在届时检查一个移动后的示例资源。它验证的是本地发现/可读性，而非自动激活或教学法收益。

Hermes 已安装版本：`v0.18.0 (2026.7.1)`；本地源码修订版 `a6b9597d5fb92969d605a858d5f14536e805553a`，Python 3.11.15。版本查询独立于断网读取检查；未执行更新/安装。
