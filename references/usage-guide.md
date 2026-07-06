# 使用指南

## 适用场景

当 Shin-video 工作流进入「视觉风格与渲染成片」阶段，并需要执行「Remotion 渲染成片」时使用。

## 推荐提示词

```text
请使用「Remotion 渲染成片」处理当前 Shin-video 项目。
```

## 项目文件结构

```text
视频项目/
├── 文章正文.md
├── 口播文案.md
├── 口播音频.mp3
├── runtime/
│   ├── asr.json
│   ├── scenes.json
│   ├── style-profile.json
│   └── preview.mp4
└── 成品/
    └── 成品.mp4
```

## 前期准备

开始完整工作流前，Agent 需要确认：

- Node.js 和 npm 可用；
- Python 可用；
- FFmpeg 可用；
- WhisperX 和 faster-whisper 模型可用；
- Remotion 和 Shin-video 视频模板可用；
- Remotion 4.0.484 与 `zod` 4.3.6 版本对齐；
- 用户已经提供文章或文章链接；
- 用户确认后的口播音频命名为 `口播音频.mp3`。

渲染前执行：

```bash
npm ls zod @remotion/bundler @remotion/cli @remotion/renderer remotion --depth=0
```

如果出现 `Remotion version mismatch` 或 `zod` 版本不一致，先执行：

```bash
npm install zod@4.3.6 remotion@4.0.484 @remotion/cli@4.0.484 @remotion/bundler@4.0.484 @remotion/renderer@4.0.484 --save-exact
```

## 失败处理

- 缺文章：请用户提供文章或链接。
- 缺音频：提醒用户把口播音频放入项目并命名为 `口播音频.mp3`。
- 缺 WhisperX：先部署本地 WhisperX 环境，不要手工编时间戳。
- 缺 Remotion：先部署 Remotion 环境，不要跳过预览。

## 输出原则

- 中间文件放 `runtime/`。
- 预览视频放 `runtime/preview.mp4`。
- 最终成片放 `成品/成品.mp4`。
