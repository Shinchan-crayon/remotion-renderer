# 来源、职责与边界：Remotion 渲染成片

## 基本信息

- 中文名：Remotion 渲染成片
- 英文名：`remotion-renderer`
- 工作流角色：渲染工程师
- 所属阶段：第 10 步：预览与最终 MP4

## 要解决的问题

最后一步必须确认 Remotion 模板真的读取 scenes、director-plan 和 style-profile。这个 Skill 负责渲染 preview.mp4、质量检查，并在用户确认后导出最终成片。

## 输入

- runtime/scenes.json
- runtime/director-plan.json
- runtime/style-profile.json
- 口播音频.mp3
- Remotion 项目环境

## 输出

- runtime/preview.mp4
- 成品/成品.mp4

## 上下游关系

上游：
- animation-preset-builder

下游：
- 用户验收

## 具体职责

- 生成可播放 MP4
- 检查黑屏、音频、字幕溢出、模板重复
- 阻止缺导演方案或风格配置时直接渲染

## 不负责什么

- 不重新猜镜头
- 不跳过质量检查
- 不在用户未确认 preview 前导出最终成品

## 在 AI 员工体系中的位置

这个 Skill 是一个员工能力模块，不是完整员工页面。完整员工页面会说明：

- 这个 AI 员工能解决什么问题；
- 背后由哪些 Skill 组成；
- 适合谁使用；
- 如何安装；
- 有哪些 Demo；
- 免费版、付费版和定制服务如何区分。

## 质量要求

- 必须遵守上游输入，不编造缺失文件。
- 必须生成明确输出，不能只写建议。
- 必须在边界内工作，不能抢下游 Skill 的职责。
- 失败时要说明缺哪个输入、哪个环境或哪个用户确认。

## 来源说明

本 Skill 属于 Shin-video 工作流封装，用于把文章、口播、音频、时间轴、导演方案、视觉风格和 Remotion 渲染串成稳定流程。它调用或依赖的外部工具以各自官方能力为准；本仓库只负责工作流编排、中文化说明和执行约束。
