# Agents & Skills Repository

这是一个个人用的 agent 与 skill 存放仓库，用于集中管理自定义的 OpenCode 风格 agent 配置与可复用的 skill 文档。

## 目录（示例）
- `agents/english-tutor.md`
- `skills/vocabulary-learning/SKILL.md`

## 已有项说明

`agents/english-tutor.md`
- 类型：agent 配置（YAML/Markdown 风格）
- 作用：英文单词、词组和句子学习助手，提供翻译、音标、词性、例句与用法解析。
- 关键点：使用 `github-copilot/gpt-5-mini`，低温度（0.3），支持 `webfetch` 和 `skill` 工具；禁止写文件与执行 bash。
- 集成：当用户要求系统化学习时，会通过 `skill` 工具加载 `vocabulary-learning`。

`skills/vocabulary-learning/SKILL.md`
- 类型：skill 文档（能力/流程说明）
- 作用：系统化的英文词汇学习流程与最佳实践，包含学习方法论、记忆技巧、标准学习步骤与复习计划（间隔重复）。

## 如何使用
1. 在与 agent 交互时，agent 根据自身配置决定是否调用 skill（例如 `vocabulary-learning`）。
2. agent 文件采用带元数据的 Markdown/YAML frontmatter（示例见 `agents/english-tutor.md`），包含描述、模型、工具权限与行为规范。
3. skill 文件用于文档化流程、方法论或可复用能力说明，agent 可在运行时参考或加载这些内容。

## 添加新 agent / skill（快速指南）
1. 新 agent：在 `agents/` 下添加 `.md` 文件，文件顶部用 frontmatter 指定 `description`、`mode`、`model`、`temperature`、`tools` 与 `permission` 等字段，正文描述行为与输出格式。
2. 新 skill：在 `skills/` 下添加目录或 `.md` 文件，包含 `name`、`description`、兼容性与详细流程/方法论。为可复用能力写清楚调用契约（输入/输出/副作用）。
3. 权限与安全：在 agent frontmatter 中明确禁用危险工具（如 `bash`、`edit`）或限制写入权限以降低风险。

