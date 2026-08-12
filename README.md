# AI Tech RSS

每天自动搜索过去 24 小时的 AI 技术动态，并生成一份面向端侧 AI / 手机部署的中文 RSS 简报。

## 订阅地址

GitHub Actions 第一次成功运行后，直接订阅：

`https://raw.githubusercontent.com/haooxia/ai-tech-rss/main/docs/feed.xml`

这个地址不依赖 GitHub Pages，Feedly、Inoreader、Reeder、NetNewsWire 等 RSS 阅读器都可以直接添加。

## 初始化（只需要做一次）

1. 打开本仓库 **Settings → Secrets and variables → Actions**。
2. 新建 Repository secret：`OPENAI_API_KEY`。
3. 打开 **Actions → Daily AI Tech RSS → Run workflow** 手动跑一次；之后会每天自动执行。
4. 成功后把上面的 `feed.xml` 地址加入 RSS 阅读器。

> 定时任务使用 GitHub Actions cron，每天 `01:30 UTC` 触发，对应北京时间 `09:30`。GitHub 的定时任务偶尔可能延迟几分钟。

## 工作方式

- 使用 OpenAI Responses API + Web Search 搜索最新公开信息。
- 默认模型：`gpt-5.6-terra`（可在 workflow 中修改 `OPENAI_MODEL`）。
- 搜索窗口严格限制为执行时刻之前 24 小时。
- 优先 Hugging Face 官方模型页 / 模型卡、GitHub Releases、官方文档和厂商技术渠道。
- 重点关注 Qwen 基础模型、Hunyuan、LiteRT/LiteRT-LM、MNN、Qualcomm Genie/GenieX/QNN/HTP、ExecuTorch、llama.cpp、小模型、ASR/TTS、机器翻译、CLIP/Embedding、AI OS、量化与移动端 benchmark。
- 默认排除 Qwen Code、Claude Code、Gemini CLI、Codex CLI、Cursor Agent 等 Coding Agent / 编码 CLI 的常规更新。
- 每天正文保存在 `posts/YYYY-MM-DD.md`，RSS 保留最近 30 期。

ChatGPT 中安装的 Skill 不能直接被 GitHub Actions 调用，因此本项目把同等的筛选规则固化在 `prompt.md` 中，由 API 的 Web Search 执行。

## 文件结构

```text
.github/workflows/daily.yml   # 每天 09:30（北京时间）运行
generate_feed.py             # 搜索、生成简报、更新 RSS
prompt.md                    # 简报筛选规则
requirements.txt
data/items.json              # 最近 30 期内容索引
posts/                       # 每日 Markdown 正文
docs/feed.xml                # RSS 2.0 feed
docs/index.html              # 可选的静态索引页
```

## 安全

`OPENAI_API_KEY` 只从 GitHub Actions Secret 读取，不会写入仓库、日志或 RSS。