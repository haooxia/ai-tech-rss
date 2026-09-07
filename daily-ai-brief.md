每次执行时，使用 Scheduled Tasks 当时可用的最强模型、推理能力和联网搜索能力；不要为了速度主动降级。

北京时间每日执行一次 AI 技术情报简报。核心目标是：**准确总结过去24小时真实发生的新变化，并持续发现对端侧/移动 AI 业务有替换价值的新模型与新框架。**

日报必须避免两类问题：
1. 被固定链接限制住，只看到少数已知来源；
2. 把旧模型、旧能力、旧 NPU 支持、页面刷新或媒体重复报道当成当天新闻。

---

【一、执行前：先做历史去重】

在搜索当天新闻前，先读取 GitHub 仓库 `haooxia/ai-tech-rss` 中最近14天的 `posts/YYYY-MM-DD.md`；历史不足14天时检查全部已有简报。

把历史简报当作“已报信息索引”，识别已经报过的：
- 模型 / release
- 模型转换
- benchmark
- 手机 NPU / runtime 部署支持
- 行业热点事件
- 重要来源 URL

规则：
- 同一模型、同一 release、同一事件，如果只是被其他媒体再次报道、页面再次编辑、社区再次转述，没有过去24小时新增事实，不重复报道。
- 如果过去24小时出现了实质新进展，可以继续跟进，但标题或 `更新` 开头标注“跟进”，只写新增部分。
- “替换候选”同样去重：最近已经推荐过、没有新的 benchmark / 部署 / 质量证据时，不要重复推荐。
- 去重不是停止跟踪；手机 NPU、强相关模型、重要行业模型仍需持续关注，有新进展就做增量跟进。

---

【二、搜索采用两条并行主线】

### 主线 A：业务技术雷达

重点发现：
- small LLM / small VLM / LLM / VLM
- 图文检索 / 相册语义搜索 / 视频 / CLIP / Embedding / Reranker
- 机器翻译 / machine translation / speech translation
- 语音模型 / ASR / TTS / speech model / voice agent
- LiteRT / LiteRT-LM / LiteRT Torch 
- Qualcomm Genie / GenieX / QNN / HTP
- MNN、ExecuTorch、ONNX Runtime Mobile、MLC、MediaPipe、TensorFlow Lite 等端侧框架
- AI OS / 系统级 AI
- 量化、模型优化、kernel、KV Cache、编译优化
- NPU / HTP / Hexagon NPU / GPU / DSP / SoC / SDK / benchmark

### 主线 B：AI 行业热点雷达

独立搜索当天即使与端侧无关也值得知道的 AI 大事，包括：
- 旗舰/重要大模型正式发布、开源、open-weight
- Qwen、DeepSeek、GLM/Z.ai、Kimi/Moonshot、Tencent/Hunyuan 等重要中国模型进展
- OpenAI、Anthropic、Google/DeepMind、Meta、xAI 等重要厂商事件
- 行业级 Agent framework / Agent 平台
- MCP / Skills 出现生态级进展
- 突然形成明显热度的重要开源项目
- 重要 AI 基础设施、模型路由、训练/推理范式变化

`AI 行业热点` 每天 0-6 条，宁缺毋滥。普通 SDK 小版本、一般 Coding CLI、普通 MCP server、普通 Skill、一般论文和小型开源项目不进入这一栏，除非达到行业级影响力。

**固定源检查和全网搜索是两条并行路径。固定链接只是必查源，不是白名单，也不得挤占全网搜索。只有完成对应 topic 的全网搜索后，才允许写“今日无高价值新增”。**

---

【三、固定必查源】

### A. GitHub Releases：每天逐个检查

以下仓库只看 Releases / latest release / pre-release / nightly release notes，不把普通 commit、issue、PR 作为日报新闻：

- https://github.com/google-ai-edge/LiteRT-LM
- https://github.com/google-ai-edge/LiteRT
- https://github.com/google-ai-edge/litert-torch
- https://github.com/google-ai-edge/gallery
- https://github.com/qualcomm/GenieX
- https://github.com/alibaba/MNN

对这些框架重点看：
- Android / iOS / 移动端支持
- 新模型支持
- QNN / HTP / NPU / GPU backend
- 模型导出 / 编译 / 量化
- 性能、内存、兼容性
- 部署阻塞问题与 release 级修复

llama.cpp 不再作为独立框架单独检查；如果 GenieX 的 release 中涉及 llama.cpp 集成、模型支持、性能、QNN/HTP 或兼容性变化，则放在 GenieX 内汇报。

### B. Hugging Face 固定组织：每天检查 Activity

- https://huggingface.co/litert-community
- https://huggingface.co/Qwen
- https://huggingface.co/openbmb
- https://huggingface.co/qualcomm
- https://huggingface.co/tencent
- https://huggingface.co/XHToken

检查过去24小时所有 `published a model` 事件；同时对 `litert-community` 的模型卡、文件与 benchmark 变化做部署相关核验，但必须区分“新发布 / 新适配 / 新 benchmark”与单纯页面刷新或普通编辑。

发现候选后核验：
- 参数量 / 文件大小
- 模态
- 模型卡
- 量化版本
- License
- Android / iOS / LiteRT / MNN / ExecuTorch / ONNX Runtime / QNN / GenieX / Core ML 适配或 benchmark

### C. Hugging Face 全站

主动扫描过去24小时新模型与 Trending，不限于固定组织。重点找：
- 约0.1B-4B small LLM / VLM
- CLIP
- Embedding
- Reranker
- MT
- ASR
- TTS
- speech model

发现候选必须回到模型卡、官方仓库或官方发布页核验，不能只根据 Trending 排名判断。

---

【四、业务强相关模型：必须主动做替换价值扫描】

以下类别与业务强相关，不允许简单依赖固定源后写“无高价值新增”：
- small LLM / small VLM
- CLIP / 相册语义搜索 / 图文检索
- Embedding / Reranker
- MT / speech translation
- ASR / TTS / speech model / voice agent
- 其他适合手机部署的 LLM / VLM

过去24小时内要主动搜索：
- 官方模型发布
- Hugging Face 全站 / Trending
- 模型团队博客
- GitHub Releases
- 论文 / 技术博客
- 主要 AI 公司与研究团队发布渠道

发现候选后，不只判断“是不是新模型”，还要判断“是否值得替换现有方案”，重点比较：
- benchmark / 质量
- 参数量、量化体积
- RAM / latency
- 中文 / 多语言能力
- context
- License
- 模型用途限制
- Android / iOS / LiteRT / MNN / ExecuTorch / ONNX Runtime / QNN / GenieX / Core ML 支持

对 CLIP / Embedding / Reranker / MT / ASR / TTS 不设统一参数门槛，只看质量、计算量、内存和手机部署可行性。

如果过去24小时没有明显新模型，再做一次**近7天轻量替换候选扫描**。近7天候选只能作为辅助内容，并明确标注“非当日新闻”；不能喧宾夺主，也不能把旧模型伪装成当天发布。

更小但效果接近、更低内存、更低延迟、更好中文/多语言、更好的移动 runtime / NPU 适配，都可以构成“更强”的替换理由。

---

【五、手机 NPU 是部署判断的最高优先级之一】

对于框架和模型部署，优先核验真正的手机 NPU 支持，而不是泛化的“硬件加速”。重点关注：
- Snapdragon / Qualcomm HTP / QNN / Hexagon
- SM8750 / SM8845 / SM8850 以及其他QC SoC
- MediaTek NPU / APU
- Google Tensor TPU / Edge TPU
- Samsung Exynos NPU

需要尽量确认：
- 是否真正运行在手机 SoC 上
- 支持哪些 SoC / SDK / backend
- 是否新增 NPU backend
- 哪些模型 / 算子真正 offload 到 NPU
- graph partition / fallback 情况
- full delegation 是否真的成立
- calibration / quantization 路径
- device allowlist / driver / SDK 依赖
- 真机 latency / throughput / prefill / decode / RAM / load time / power
- 输出正确性、tokenizer、pre/post-processing 是否与上游一致

**必须明确区分“可编译 / 可运行 / full delegation / 实际更快”四个层级。Full delegation 不等于性能一定优于 GPU/CPU。**

若只有 CPU / GPU 或桌面/服务器 NPU 支持，要明确区分，不能写成“手机 NPU 已支持”。只有宣称支持、没有可核验设备/backend/模型路径时，要谨慎表述。

---

【六、严格判断“是不是今天的新变化”】

日报正文优先只写过去24小时真实发生的：
- 新模型发布
- 新 release
- 新能力
- 新适配
- 新 benchmark
- 新部署支持
- 重要 release 级修复
- 对端侧部署结果有实质影响的模型包修复（例如 tokenizer / preprocessing / quantization / accelerator artifact），但必须有可核验的实际变化，不得仅依据更新时间

对固定推理框架 GitHub：普通 commit、issue、PR 不进入日报正文，只有进入正式 release / pre-release / nightly release notes 才汇报。

对 Hugging Face 模型仓库：如果模型包本身在过去24小时出现了**已合并、可下载、会改变部署能力/正确性/benchmark 的实质更新**，可以进入日报；但普通模型卡编辑、页面刷新、discussion、open PR 不进入正文。

以下不能单独作为“当天新闻”的证据：
- 页面更新时间
- 模型卡编辑时间
- SDK 重新导出
- 设备列表刷新
- 已有支持矩阵重新生成
- 媒体重新报道旧模型

特别是 Qualcomm AI Hub / Hugging Face / 官方文档：看到“最近更新”后，必须继续核验到底新增了什么。如果不能证明具体变化发生在过去24小时，就不能当作当天新闻。

已长期支持 Snapdragon NPU / QNN / HTP 的模型，不得因为页面今天刷新就描述成“今天新增手机 NPU 支持”。

---

【七、信息源优先级】

官方 Release / 官方发布页 / 官方模型卡 > 官方 changelog / 文档 / 博客 / 论文 / Qualcomm AI Hub > 权威媒体 > 非官方转述。

同一事件只写一次，不用旧闻凑数。

---

【八、简报结构】

一级标题固定：
`# 今日 AI 技术情报简报`

标题下写精确统计时间范围。

若当天高价值更新少，在目录前写：
`今天高价值更新较少。`

必须有：
`## 目录`
只列实际存在的二级标题。

正文按当天实际内容选择以下栏目：
1. 模型与多模态
2. 端侧框架与运行时
3. 音频、翻译与检索
4. 系统、优化与硬件
5. AI 行业热点（仅当天有足够重要事件时出现）
6. 今日无高价值新增
7. AI点评

同一 topic 原则上最多1-3条高价值内容，同一新闻不要跨栏目重复。

所有已完成搜索但无高价值新增的 topic 放入 `## 今日无高价值新增`，按父类归纳。

---

【九、每条新闻格式】

- 简短标题
- 下一行 1-2 个标签
- `**更新：**` 1-2句，只写事实与本次新增变化
- `**判断：**` 尽量1句，最多2句；只写为什么重要、是否值得替换、或对手机/NPU部署意味着什么，不展开实现细节，不重复“更新”内容
- 如果是历史已报事项的新进展，标注“跟进”，只写增量
- `**来源：** [官方来源名称](实际URL)`，优先具体 Release、模型卡、官方文档或官方发布页

---

【十、AI点评】

末尾 `## AI点评`，写3-5条真正值得继续跟踪的趋势或下一步方向，不重复正文。

---

【十一、GitHub 与 RSS 同步】

完成简报后，将最终正文与 RSS 同步到 GitHub 仓库 `haooxia/ai-tech-rss`：
- 直接写入 `main`
- 不创建 PR
- 简报路径：`posts/YYYY-MM-DD.md`，日期使用北京时间
- 当天同名文件已存在则更新
- 文件内容与最终发送给用户的正文一致
- Markdown 最后一行：`本简报由 ChatGPT（GPT-5.6 Sol）基于公开互联网信息检索、核验与整理生成。`；若实际模型不同则替换为实际模型名

同时更新根目录 `feed.xml`：
- RSS 地址：`https://raw.githubusercontent.com/haooxia/ai-tech-rss/main/feed.xml`
- 最新 item 放最前，只保留最近30条
- title：`AI 技术情报简报｜YYYY-MM-DD`
- link：`https://github.com/haooxia/ai-tech-rss/blob/main/posts/YYYY-MM-DD.md`
- guid 与 link 相同，`isPermaLink="true"`
- pubDate 使用实际生成/同步时间，RFC 822/RFC 1123，`+0800`
- category 从当天实际有高价值更新的主题中选1-3个
- description 只写2-4个最重要重点，并使用阿拉伯数字序号增强 RSS 阅读器中的可读性。固定格式：`今日重点：1. A；2. B；3. C。`；如果只有2个重点就写 `1. A；2. B。`，如果有4个重点则写到 `4.`。每个重点尽量控制为一句短语或一个短句，避免把多个从句塞进同一项；不放全文，不追加“点击查看详情”。
- 更新 channel 的 `lastBuildDate`
- 保持 `title=AI Tech RSS`、仓库主页 link、`language=zh-CN` 和 raw feed 的 `atom:link rel="self"`
- 正确 XML 转义，保证合法 XML
- 不因 feed 更新修改历史 Markdown

【提交要求】
- `posts/YYYY-MM-DD.md` 与 `feed.xml` 必须在同一个 Git commit 中一次性提交到 `main`
- Commit message 固定英文：`Update AI tech brief for YYYY-MM-DD`
- 当天重跑时仍同时更新两个文件，并保持同一天 RSS item 的 guid 不变

GitHub 或 RSS 同步失败时，仍正常发送简报，并在末尾说明失败。