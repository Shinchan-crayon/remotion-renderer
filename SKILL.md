---
name: remotion-renderer
description: 调用 Remotion 使用 runtime/scenes.json、runtime/style-profile.json 和 口播音频.mp3 渲染 Shin-video 预览视频与最终成片，并做基础质量检查。
---

# Remotion 渲染成片

调用 Remotion 渲染视频。

## 输入

```text
runtime/scenes.json
runtime/style-profile.json
口播音频.mp3
```

## 输出

预览：

```text
runtime/preview.mp4
```

最终：

```text
成品/成品.mp4
```

## 环境检查

在 Shin-video 项目根目录先检查：

```bash
node -v
npm -v
npx remotion --version
ffmpeg -version
```

如果 `npx remotion --version` 失败，先读取：

```text
references/WhisperX和Remotion部署说明.md
```

已有 Shin-video 项目时，优先执行：

```bash
npm install
```

如果仍缺 Remotion：

```bash
npm install remotion @remotion/cli @remotion/renderer @remotion/bundler
```

## 渲染规则

- 先生成 `runtime/preview.mp4`。
- 用户确认预览后，再输出 `成品/成品.mp4`。
- 如果 `成品/` 不存在，先创建。
- 不要把最终视频输出到其他目录。

## 命令模板

预览：

```bash
npm run render:preview
```

最终成片：

```bash
npm run render:final
```

如果项目没有这两个脚本，先不要乱猜命令；读取当前项目 `package.json`，找到 Remotion 渲染脚本后再执行。

## 基础质量检查

渲染后检查：

- 视频文件是否存在。
- 文件大小是否明显异常。
- 视频是否能播放。
- 是否有音频。
- 是否黑屏。
- 视频时长是否接近口播音频时长。
- 字幕和主要文字是否明显溢出。

如果检查失败，先修复再交付。

## 失败提示

缺 Remotion 时：

```text
当前项目还没有可用的 Remotion 环境。我需要先执行 npm install，并确认 npx remotion --version 可以正常输出。
```

缺 FFmpeg 时：

```text
当前机器缺少 FFmpeg，Remotion 渲染可能无法正常编码视频。我需要先安装 FFmpeg。
```

渲染失败时：

```text
Remotion 渲染失败。我会先检查 scenes.json、style-profile.json、口播音频.mp3、FFmpeg 和输出目录，再重新渲染。
```
