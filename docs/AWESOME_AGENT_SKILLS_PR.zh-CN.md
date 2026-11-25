# Pull Request 草案：收录至 VoltAgent/awesome-agent-skills 列表

本文档仅为草案。未经 Gareth 批准，请勿提交。

## 目标仓库

- 仓库：`VoltAgent/awesome-agent-skills`
- 文件：`README.md`
- 章节：`Community Skills` → `Specialized Domains`

## 选择该章节的原因

该 awesome 列表目前尚未设立 Education（教育）分类。其贡献指南要求将社区条目添加到最接近的子分类中，若无合适分类则添加到 `Other`。对于专门面向教育的技能库，`Specialized Domains` 是当前最贴切的归属。

## 拟议 PR 标题

```text
Add skill: GarethManning/education-agent-skills
```

## 拟议 README 条目

将以下内容添加到 `Community Skills` → `Specialized Domains` 末尾：

```markdown
- **[GarethManning/education-agent-skills](https://github.com/GarethManning/education-agent-skills)** - Evidence-based education skills for curriculum, assessment, and learning
```

破折号后的描述为 8 个英文单词，符合该仓库“10 个词以内”的要求。

## 拟议 PR 正文

```markdown
## Summary

Adds the Education Agent Skills Library to the Community Skills → Specialized Domains section.

## Why it fits

- Public GitHub repository with working `SKILL.md` files.
- 165 education skills across 20 domains.
- Supports Claude Code, Codex, Hermes Agent selected installs, and a read-only hosted MCP server.
- Includes README, evidence standards, exclusions, privacy notes, and contribution guidance.
- Education is a specialised domain not currently represented in the list.

## Link checked

- https://github.com/GarethManning/education-agent-skills
```

## 贡献指南注意事项

该仓库的 `CONTRIBUTING.md` 指出技能应当具备“真实的社区使用”，且可能会拒绝全新创建的技能。如果现在提交，PR 应重点强调本仓库是一个成熟的公共技能库，而非刚刚创建的单一技能。如果希望降低被拒风险，可等待 Hermes 文档合并且出现可见的外部使用记录后再提交。
