# 提示词优化 · Prompt Optimizer Skill

> 把「帮我写个提示词」变成一次有结构的对话：先诊断，再让你选角色、受众、格式和约束，最后交一段能直接复制去跑的成品。

一个面向 AI 编码助手（OpenCode、Claude Code 等支持 Agent Skill 的工具）的技能包。它不替你猜，而是**用选项引导你一起把模糊需求打磨成可执行的规格**。

## 为什么需要它

大多数人写提示词的失败点不是「写得不够长」，而是缺了可检验的标准：

- 只给目标，不给受众和格式 → 每次输出都不一样
- 角色写成「你是资深专家」→ 只是装饰，不改变关注点
- 一次塞多个任务 → 每样都半吊子
- 堆「专业、详细、高质量」→ 模型无法执行

这个技能把这些缺口变成一次**最多三轮的选择题**，然后产出结构完整、可直接复用的提示词。

## 它怎么工作

| 步骤 | 做什么 |
|---|---|
| 0. 判断模式 | 从零起草 / 优化现有 / 只要模板 / 快速模式（说「别问了」就直接给，但列出假设） |
| 1. 诊断 | 用六要素打勾，一行说清缺什么 |
| 2. 引导提问 | 每轮 3–4 个问题，用选项让你选角色、受众、格式、约束 |
| 3. 起草 | 按「角色 / 任务 / 背景 / 输入 / 要求 / 输出格式 / 自检」填充 |
| 4. 自检 | 7 项硬检查，不过就改 |
| 5. 交付 | 成品代码块 + 待填变量表 + 使用说明 |

### 角色选择示例

技能会按任务类型给出差异明显的候选，而不是三个同义词：

| 选项 | 角色 | 关注点 |
|---|---|---|
| A | 资深从业者 | 落地、风险、真实项目经验 |
| B | 挑剔的评审者 | 边界、漏洞、维护成本 |
| C | 面向新手的教练 | 拆步骤、给类比、少术语 |

角色库覆盖：写作、编程、分析、教学、商业、客服、创意，共 8 类、20+ 个候选，并支持自定义。

## 安装

### 项目级（推荐）

把 `.opencode/skills/prompt-optimizer/` 复制到目标项目的 `.opencode/skills/` 下：

```text
your-project/
└── .opencode/
    └── skills/
        └── prompt-optimizer/
            ├── SKILL.md
            └── references/
```

### 全局

复制到用户级技能目录，所有项目可用：

- macOS / Linux：`~/.config/opencode/skills/prompt-optimizer/`
- Windows：`%USERPROFILE%\.config\opencode\skills\prompt-optimizer\`

### 直接克隆

```bash
git clone https://github.com/SC-CATL/prompt-optimizer-skill.git
```

然后把 `.opencode/skills/prompt-optimizer/` 拷到目标位置，或直接把仓库克隆进项目根目录。

## 使用

说下面这类话就会触发：

- 「帮我优化这段提示词」
- 「写个提示词，让 AI 帮我改周报」
- 「AI 输出总是不稳定 / 格式不对」
- 「给我一个代码审查的提示词模板」

示例对话：

```text
你：帮我写个提示词，让 AI 帮我改周报

助手：这个提示词主要用来做什么？
      [写文案/内容] [写代码/改代码] [分析数据/文档] [知识讲解/教学]

你：写文案

助手：希望 AI 以什么身份来回答？
      [A 资深编辑] [B 目标读者本人] [C 品牌守门人]

你：A

助手：……（继续问受众、长度、格式，然后交付成品）
```

## 目录结构

```text
.
├── README.md
├── LICENSE
├── CONTRIBUTING.md
├── SECURITY.md
├── CHANGELOG.md
└── .opencode/
    └── skills/
        └── prompt-optimizer/
            ├── SKILL.md              # 主流程与铁律
            └── references/
                ├── role-library.md   # 8 类任务的角色候选
                └── patterns.md       # few-shot、输出契约、兜底等技巧
```

## 设计原则

1. **先问再写**：缺关键信息不出成品。
2. **给选项，别问开放题**：降低回答成本。
3. **不编造事实**：没提供的信息变成 `{{占位符}}` 并列出待填清单。
4. **可检验**：每句话都要对应一个能判断是否达成的要求。
5. **短而有效**：删掉所有无法执行的形容词。

## 自定义

- 加角色：编辑 `references/role-library.md`，按「身份 + 关注点 + 适合任务」补充。
- 加技巧：编辑 `references/patterns.md`，写清「什么时候用 + 写法 + 示例」。
- 改流程：编辑 `SKILL.md` 的「工作流」一节，保持五步结构即可。

## 贡献

欢迎补充角色候选和提示词技巧。提交前请阅读 [CONTRIBUTING.md](CONTRIBUTING.md)，并遵守 [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md)。

发现安全问题时，请按 [SECURITY.md](SECURITY.md) 私下报告，不要开公开 issue。

## 许可证

[MIT](LICENSE) © 2026 SC-CATL
