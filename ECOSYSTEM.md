# Cerul 插件分发生态对比

> 更新时间：2026-04-06

## 总览

### 已完成的插件/扩展

| 平台 | 类型 | 安装方式 | 状态 |
|------|------|---------|------|
| **Claude Code** | Plugin Marketplace | `claude plugin marketplace add cerul-ai/cerul-plugin-cc` | ✅ 已完成 |
| **Gemini CLI** | Extension (MCP) | `gemini extensions install https://github.com/cerul-ai/cerul-gemini-ext` | ✅ 已完成 |
| **OpenClaw** | ClawHub Skill | `clawhub install cerul` | ✅ 已完成 |

### 待提交的分发渠道

| 渠道 | 类型 | 提交方式 | 投入 | 状态 |
|------|------|---------|------|------|
| **awesome-opencode** | GitHub 策展列表 (4.8k stars) | PR 提交 | 5 分钟 | ⬜ 待做 |
| **opencode.cafe** | 社区 marketplace 网站 | 网站表单 | 5 分钟 | ⬜ 待做 |
| **opencode.ai/ecosystem** | OpenCode 官方生态页 | PR 到 anomalyco/opencode | 5 分钟 | ⬜ 待做 |
| **n-skills** | 策展型 skill 合集 | Issue + PR | 10 分钟 | ⬜ 待做 |
| **SkillHub** | 7,000+ skills 网站 | 网站上传 | 10 分钟 | ⬜ 待做 |
| **Cline MCP Marketplace** | 官方 Cline 插件市场 | Issue + PR 到 cline/mcp-marketplace | 10 分钟 | ⬜ 待做 |
| **Windsurf** | 文档引导安装 | 在 cerul 主 repo README 加说明 | 5 分钟 | ⬜ 待做 |
| **claude-plugins.dev** | 通用 AI agent 索引 | GitHub 自动索引 | 0 分钟 | ⬜ 待确认 |

### 暂缓的平台

| 平台 | 原因 | 状态 |
|------|------|------|
| **Codex CLI** | 第三方发布标注 "coming soon"，需等开放 | ⏸ 等待 |
| **OpenCode npm plugin** | 已有 cerul npm SDK，可后续加 plugin 入口 | ⏸ 低优先 |
| **Roo Code** | 用户量小，需写自定义 Mode | ❌ 暂不做 |
| **Cursor** | 无独立插件系统，仅 VS Code 扩展 | ❌ 不适合 |
| **Aider** | 仅 hooks，无 marketplace | ❌ 不适合 |
| **Amp** | 仅 MCP，无 marketplace | ❌ 不适合 |

---

## 已完成的平台详情

### Claude Code Plugin

- **仓库**: https://github.com/cerul-ai/cerul-plugin-cc
- **安装方式**:
  ```bash
  claude plugin marketplace add cerul-ai/cerul-plugin-cc
  claude plugin install cerul@cerul-plugin
  ```

### Gemini CLI Extension

- **仓库**: https://github.com/cerul-ai/cerul-gemini-ext
- **安装方式**:
  ```bash
  gemini extensions install https://github.com/cerul-ai/cerul-gemini-ext
  ```

### OpenClaw ClawHub

- **Slug**: `cerul`
- **安装方式**:
  ```bash
  clawhub install cerul
  ```
- **更新**: `clawhub publish ./cerul-openclaw-skill --slug cerul --version X.Y.Z`

---

## 待提交渠道操作指南

### 1. awesome-opencode

- **地址**: https://github.com/awesome-opencode/awesome-opencode
- **提交方式**: Fork → 编辑 README.md → 在合适分类下添加 Cerul 条目 → 提交 PR
- **条目格式**: `- [Cerul](https://github.com/cerul-ai/cerul) - Video search for AI agents — search what was said, shown, or presented in tech talks, podcasts, and conferences.`
- **分类**: 放在 Tools 或 Plugins 下

### 2. opencode.cafe

- **地址**: https://www.opencode.cafe/
- **提交方式**: 访问网站 → 点击 Submit → 填写表单（GitHub 仓库 URL + 描述）
- **分类**: Tools 或 MCP Servers

### 3. opencode.ai/ecosystem

- **地址**: https://opencode.ai/docs/ecosystem/
- **提交方式**: PR 到 https://github.com/anomalyco/opencode 的文档目录
- **内容**: 添加 Cerul 到生态页

### 4. n-skills

- **地址**: https://github.com/numman-ali/n-skills
- **提交方式**: 先开 Issue 描述 Cerul skill → 审核通过后提交 PR
- **注意**: 策展型，有质量门槛

### 5. SkillHub

- **地址**: https://www.skillhub.club
- **提交方式**: 网站上传 SKILL.md
- **内容**: 复用现有 SKILL.md

### 6. Cline MCP Marketplace

- **地址**: https://github.com/cline/mcp-marketplace
- **提交方式**: 用 Issue 模板提交（GitHub 仓库 URL + 400×400 logo + 描述）→ 审核（约 2 天）
- **内容**: 指向 cerul-gemini-ext 的 MCP server

### 7. Windsurf

- **无 marketplace**: 在 cerul 主 repo 的 README 添加 Windsurf 安装说明
- **安装路径**: `~/.codeium/windsurf/skills/cerul/SKILL.md`

### 8. claude-plugins.dev

- **地址**: https://claude-plugins.dev
- **提交方式**: 自动索引 GitHub 上的 Claude Code plugin
- **操作**: 确认 cerul-plugin-cc 已被收录即可

---

## 跨平台策略

核心资产：
- **SKILL.md** — 跨 Claude Code / Codex / Windsurf / Cline / OpenClaw / OpenCode 复用
- **MCP Server** (cerul-gemini-ext) — 跨 Gemini CLI / Cline / OpenCode 复用
- **npm SDK** (cerul) — https://github.com/cerul-ai/cerul-js

维护一份核心 SKILL.md + 一个 MCP server，各平台仅做分发层适配。
