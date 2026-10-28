# 🎬 movie-matchmaker — 影片匹配技能 (DSH Skill)

根据你的**心情、精力、口味和现实条件**，帮你分析哪种影片最适合你，并给出具体片单的技能。适合"今晚看什么"、"给室友挑部片"、"给我推荐一部电影"这类场景。

> A DeepSeek Harness (DSH) skill that interviews the viewer about mood, energy, taste and practical constraints, scores candidate film types, and recommends the best-fit genre plus a ranked shortlist of concrete films.

## 工作方式

1. **采访** — 一次性问一组轻松的问题（心情、精力、和谁看、时长、口味、题材、节奏、敏感度……），跳过你已经说过的内容。
2. **评分** — 对 4-5 种候选影片类型按加权维度打分（心情匹配 ×2、精力匹配 ×2、题材契合 ×2、社交适配、现实适配），输出一张小表格。
3. **推荐** — 给出「今晚最佳」类型 + 1-3 部具体影片、一份带理由的排序片单、一部「换个心情」的备选，以及合法的观看平台。

## 安装

### DeepSeek Harness（用户技能目录）

把仓库克隆到用户技能目录即可，重启会话后技能目录会自动刷新（有文件监听）：

```powershell
git clone https://github.com/Awahara/movie-matchmaker-skill.git "$env:USERPROFILE\.dsh\skills\movie-matchmaker"
```

克隆后的结构正好满足 DSH 的目录式技能格式（`<skills-root>/<目录>/SKILL.md`）。也可以直接下载根目录的 [SKILL.md](SKILL.md) 放进任意已配置的技能目录。

### 其他 Agent 环境

任何支持 `SKILL.md`（frontmatter 含 `name`、`description`）的 Agent 环境都能直接使用本仓库根目录的 `SKILL.md`。

## 使用

在对话里直接说「帮我想想今晚看什么」即可触发；也可以显式调用 `/movie-matchmaker`。

示例：

> 用户：今晚有点累，想和室友看点轻松的，两小时以内，不喜欢恐怖片。
>
> 技能：好嘞——"轻松"是哪种？爆笑喜剧、治愈系动画、还是温馨剧情片？……

随后给出评分表和推荐片单。

## 内容边界

- 只推荐**合法正版**影片，绝不提及盗版站点、种子或非官方片源。
- 不含成人内容，也不针对此类需求推荐；对年龄敏感影片会提示分级。
- 尊重内容敏感度：用户说"不要恐怖片"，恐怖片连备选都不会出现。

## 技能格式说明

- **frontmatter**: `name`（kebab-case）、`description`（目录中展示的简介），可选 `whenToUse`、`invocation`。
- **正文**: 三段式工作流（采访 → 评分 → 推荐）+ 规则 + 示例 + 输出模板。

## License

[MIT](LICENSE) © 2026 Awahara
