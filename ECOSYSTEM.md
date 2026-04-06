# Cerul 插件分发生态对比

> 更新时间：2026-04-06

## 总览

| 平台 | 插件生态 | 分发方式 | 优先级 | 状态 |
|------|---------|---------|-------|------|
| **Claude Code** | Plugin Marketplace | GitHub 仓库 → `/plugin marketplace add` | P0 | ✅ 已完成 |
| **Gemini CLI** | Extensions 系统 | GitHub + MCP server，无需审批 | P1 | ✅ 已完成 |
| **OpenClaw** | ClawHub 技能注册表 | `clawhub publish`，13,700+ skills | P1 | ⬜ 待做 |
| **Codex CLI** | 插件系统（2026.3 上线） | plugin.json，结构类似 Claude Code | P2 | ⬜ 等第三方发布开放 |
| **Windsurf** | Skills 系统 | SKILL.md，兼容 Agent Skills 标准 | P2 | ⬜ 复用现有 SKILL.md |
| **Cline** | Skills（v3.48+） | LobeHub / n-skills marketplace | P3 | ⬜ 复用现有 SKILL.md |
| **OpenCode** | 插件系统 | npm 发布 + opencode.cafe | P3 | ⬜ 待做 |
| **Roo Code** | Modes Gallery | 自定义 Mode | P4 | ⬜ 低优先 |
| **Cursor** | 无独立插件系统 | 仅 VS Code 扩展 | — | ❌ 不适合 |
| **Aider** | 仅 hooks | 无 marketplace | — | ❌ 不适合 |
| **Amp** | 仅 MCP | 无 marketplace | — | ❌ 不适合 |

## 各平台详情

### P0: Claude Code Plugin（已完成）

- **仓库**: https://github.com/cerul-ai/cerul-plugin-cc
- **安装方式**:
  ```bash
  claude plugin marketplace add cerul-ai/cerul-plugin-cc
  claude plugin install cerul@cerul-plugin
  ```
- **结构**: marketplace.json → plugin.json → skills/cerul/SKILL.md
- **自动更新**: 支持

---

### P1: Gemini CLI Extension（已完成）

- **仓库**: https://github.com/cerul-ai/cerul-gemini-ext
- **安装方式**:
  ```bash
  gemini extensions install https://github.com/cerul-ai/cerul-gemini-ext
  ```
- **结构**: gemini-extension.json + MCP server（cerul_search / cerul_usage 工具）+ GEMINI.md
- **自动更新**: 支持

---

### P1: OpenClaw ClawHub

- **文档**: https://docs.openclaw.ai/tools/clawhub
- **优势**: 社区活跃（13,700+ skills），语义搜索发现，低门槛发布
- **实现方式**:
  - 安装 clawhub CLI
  - 复用现有 SKILL.md（可能需要调整 frontmatter 格式）
  - `clawhub publish ./skills/cerul/`
- **要求**: GitHub 账号（>1 周），semver 版本管理
- **注意**: 支持 stars 和评论，有社区反馈机制

---

### P2: Codex CLI Plugin

- **文档**: https://developers.openai.com/codex/plugins
- **优势**: 结构与 Claude Code 几乎一致（plugin.json + skills + MCP）
- **实现方式**:
  - 创建仓库（如 `cerul-ai/cerul-plugin-codex`）
  - 结构: `.codex-plugin/plugin.json` + skills 目录
  - 跨兼容 Claude Code 生态
- **阻塞**: 第三方自助发布目前标注 "coming soon"，需等开放
- **参考**: openai/codex-plugin-cc 是目前最成熟的 Codex 插件案例

---

### P2: Windsurf Skills

- **优势**: 2025 Gartner 领导者象限，质量导向生态
- **实现方式**:
  - 复制 SKILL.md 到 `~/.codeium/windsurf/skills/cerul/`
  - 遵循质量指南（metadata < 100 tokens, body < 500 行）
  - 兼容 Agent Skills 标准规范
- **注意**: 和 Claude Code / Codex / Cline 使用同一个 SKILL.md 标准

---

### P3: Cline Skills

- **实现方式**:
  - 复用现有 SKILL.md
  - 发布到 LobeHub（115,000+ skills）或 n-skills marketplace
  - 遵循 Agent Skills 规范
- **参考**: https://lobehub.com/skills, https://github.com/numman-ali/n-skills

---

### P3: OpenCode Plugin

- **文档**: https://opencode.ai/docs/plugins/
- **实现方式**:
  - 创建 JS/TS 模块，导出 plugin 函数
  - 定义 AI 可调用的 tools（video search）
  - 发布到 npm（如 `@cerul/opencode-plugin`）
  - 注册到 opencode.cafe 社区平台
- **注意**: 原 OpenCode 项目已归档，后续项目为 "Crush"

---

## 跨平台策略

2025年12月 Anthropic 发布 **Agent Skills 标准规范**，OpenAI 也已采纳。核心文件 SKILL.md 可跨以下平台复用：
- Claude Code
- Codex CLI
- Windsurf
- Cline
- OpenClaw（ClawHub）

**建议**: 维护一份核心 SKILL.md，各平台仅做分发层适配（marketplace.json / extension manifest 等）。
