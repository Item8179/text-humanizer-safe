# 去AI味

![Codex Skill](https://img.shields.io/badge/Codex-Skill-111827) ![Text only](https://img.shields.io/badge/运行方式-纯文本处理-16a34a) ![No Python](https://img.shields.io/badge/Python-不需要-2563eb)

“去AI味”是一个面向 Codex 的文本改写 Skill。它通过多阶段、多语言的重写与回译，调整机械、重复和模板化的表达，同时尽量保留原文的事实、观点和语气。

这个仓库只包含 Skill 说明与界面配置，不需要运行 Python，不会自动安装依赖，也不会下载或执行外部代码。

## 主要功能

- 改善文字的自然度和可读性
- 减少重复句式、机械衔接和模板化表达
- 尽量保留人名、数据、日期、术语、链接、引文和原文立场
- 支持根据用途调整语气与写作风格
- 支持直接粘贴文本或处理本地 Markdown、TXT 等文本文件
- 支持多轮改写、历史重置和 JSON 输出
- 支持 `en`、`ja`、`zh`、`ko`、`de`、`fr`、`es`、`tr` 八种语言

## 工作流程

### 1. 重写并转为中文

先梳理原文的语义和信息结构，再生成意思一致、句式更自然的中文中间稿。原文已经是中文时，也会重新调整表达。

### 2. 转为土耳其语

将中文中间稿转换为土耳其语，利用两种语言在语序和表达习惯上的差异，进一步打散固定句式。长文本会按句子边界分段处理，避免遗漏内容。

### 3. 转为日语（可选）

配置 DeepL API Key 后，可以增加土耳其语到日语的转换步骤。未检测到 Key 时，Skill 会先提醒用户配置或明确选择跳过，不会静默省略。

即使已经配置 Key，也只有在用户明确同意后，才会把本次正文发送到 DeepL 官方服务。

### 4. 重构为目标语言

最后按照指定语言重新组织文本，清理多轮转换留下的生硬表达，并恢复连贯性和可读性。默认只输出最终结果，不展示中间稿。

## 安装

将这个仓库下载或克隆到 Codex 的 Skills 目录，并把目录名称设为 `qu-ai-wei`：

- Windows：`C:\Users\<用户名>\.codex\skills\qu-ai-wei`
- macOS / Linux：`~/.codex/skills/qu-ai-wei`

安装后应能看到以下结构：

```text
qu-ai-wei/
├── SKILL.md
├── agents/
│   └── openai.yaml
└── .gitignore
```

重新打开 Codex 或刷新 Skills 后即可使用。

## 使用方法

直接粘贴文字：

```text
使用 $qu-ai-wei 改写下面的文字：

这里放需要处理的正文。
```

处理本地文件：

```text
使用 $qu-ai-wei 改写 "E:\文档\文章.md"
```

也可以补充具体要求，例如：

```text
使用 $qu-ai-wei 改写下面的内容，保持中文，语气自然一些，不要改动数字和引用。
```

## DeepL 配置

如果需要启用第三步，可在 Skill 目录创建本地配置文件 `config.local.toml`：

```toml
[general]
deepl_api_key = "填写你自己的 DeepL API Key"
```

`config.local.toml` 已被 `.gitignore` 排除，不应提交到 GitHub。不要把 API Key 写入 `SKILL.md`、README、示例配置、提交记录或聊天截图。

## 隐私与安全

- 默认在当前模型内处理文本，不自动请求外部服务
- 调用 DeepSeek、Google Translate、DeepL、Niutrans、OpenRouter 或 Ollama 前，需要用户明确同意发送正文
- 外部调用只使用服务商的官方端点
- 不运行 Shell，不下载脚本，不安装第三方依赖
- 不读取或上传与当前改写任务无关的文件
- API Key 只保存在本机忽略文件中

## 使用边界

这个 Skill 用于改善自然度、表达方式和文风，不保证通过任何 AI 内容检测器。不同检测器的规则会变化，结果也可能互相矛盾。

涉及合同、医学、财务、学术引用或其他高风险内容时，请在使用最终文本前人工核对事实、术语和引用。

