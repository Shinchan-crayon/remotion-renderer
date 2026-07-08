# 使用指南：Remotion 渲染成片

## 最短使用方式

```text
请使用 Remotion 渲染成片，继续处理当前 Shin-video 项目。
```

## 使用前确认

请先确认上游输入已经准备好：

- runtime/scenes.json
- runtime/director-plan.json
- runtime/style-profile.json
- 口播音频.mp3
- Remotion 项目环境

## 正常输出

- runtime/preview.mp4
- 成品/成品.mp4

## 常见失败

- 缺少上游文件：先回到上游 Skill。
- 用户确认不足：暂停追问，不要自行默认。
- 本地环境缺失：先按总控仓库安装指南修环境。
- 输出文件不存在：不要继续下游步骤。

## 和总导演配合

通常不需要用户手动调用本 Skill。最稳的方式是先使用 `shin-video-director`，由总导演判断当前项目应该调用哪个 Skill。
