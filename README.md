# AI Tech RSS

用于归档 ChatGPT 自动生成的《AI 技术情报简报》，聚焦 AI 模型、端侧推理、移动端部署与模型优化等技术动态。

## 关注方向

- **大模型与多模态**：LLM、VLM、小参数模型、手机可部署模型，以及 Qwen、Gemma、Hunyuan 等重点模型生态。
- **端侧推理与框架**：LiteRT、LiteRT-LM、MNN、llama.cpp、ExecuTorch、Qualcomm QNN / HTP、Genie / GenieX 等。
- **语音与跨语言**：ASR、TTS、Audio 模型、实时翻译与端侧语音交互。
- **模型优化**：Int4 / Int2 / ternary、量化、蒸馏、speculative decoding、内存占用与推理性能优化。
- **移动端与硬件**：Android、Snapdragon / Qualcomm NPU、GPU / NPU offload、SoC 兼容性与真机 benchmark。
- **检索与视觉**：CLIP / SigLIP、Embedding、端侧语义搜索、图文检索与相册搜索。
- **重要发布与工程进展**：新模型、框架 Release、部署支持、兼容性变化、关键修复及可实际影响端侧落地的更新。

## 工作方式

1. 每天生成过去 24 小时的重要 AI 技术动态。
2. 简报保存为 `posts/YYYY-MM-DD.md`。
3. 更新提交到 `main` 分支，并同步维护 `feed.xml` 供 RSS 阅读器订阅。

## RSS 订阅

```text
https://raw.githubusercontent.com/haooxia/ai-tech-rss/main/feed.xml
```

可直接添加到支持 RSS 的阅读器中。每个条目对应当天的技术简报，点击后直接打开 `posts/YYYY-MM-DD.md` 完整正文。
