# AI Tech RSS

用于保存 ChatGPT 每日生成的《AI 技术情报简报》。

本仓库**不运行任何 GitHub Actions、脚本、Pages 或外部服务**，也不需要 OpenAI API Key。

## 工作方式

1. ChatGPT 每天生成过去 24 小时的 AI 技术情报简报。
2. 同一轮任务把完整正文直接提交到本仓库 `main` 分支。
3. 每日文件保存为：`posts/YYYY-MM-DD.md`。
4. RSS 阅读器直接订阅 GitHub 原生 Atom Feed，即可看到每天的新提交。

## Atom / RSS 订阅地址

```text
https://github.com/haooxia/ai-tech-rss/commits/main.atom
```

可直接添加到支持 Atom/RSS 的阅读器中。

## 文件结构

```text
README.md
posts/
  YYYY-MM-DD.md
```

每个每日简报 commit 的标题格式为：

```text
AI 技术情报简报｜YYYY-MM-DD
```

## 说明

GitHub 原生 Atom Feed 的条目对应 `main` 分支的新 commit。阅读器会显示每日简报提交并提供 GitHub 跳转链接；完整正文保存在对应的 `posts/YYYY-MM-DD.md` 文件中。
