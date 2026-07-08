# Remotion 渲染成片

> Shin-video AI 员工体系中的「渲染工程师」Skill。它不是孤立提示词，而是整条文章转口播视频流水线的一环。

## 它能解决什么问题

最后一步必须确认 Remotion 模板真的读取 scenes、director-plan 和 style-profile。这个 Skill 负责渲染 preview.mp4、质量检查，并在用户确认后导出最终成片。

## 它在工作流里的位置

**阶段：** 第 10 步：预览与最终 MP4

**上游：**
- animation-preset-builder

**下游：**
- 用户验收

## 输入什么

- runtime/scenes.json
- runtime/director-plan.json
- runtime/style-profile.json
- 口播音频.mp3
- Remotion 项目环境

## 输出什么

- runtime/preview.mp4
- 成品/成品.mp4

## 背后由哪些能力组成

这个 Skill 自身负责：

- 生成可播放 MP4
- 检查黑屏、音频、字幕溢出、模板重复
- 阻止缺导演方案或风格配置时直接渲染

它通常由 `shin-video-director` 总控调用，也可以在当前项目材料已经准备好时单独调用。

## 每个 Skill 的作用

在完整 AI 员工体系里，本 Skill 的职责是：**渲染工程师**。

它不负责：

- 不重新猜镜头
- 不跳过质量检查
- 不在用户未确认 preview 前导出最终成品

## 演示截图 / 视频

![Shin-video Demo](docs/demo/style-comparison.png)

演示重点：演示截图展示预览视频和成品输出路径。

完整视频 Demo 建议放在总控仓库或 ThinkAI Skill 页面中展示；单个 Skill 仓库保留截图和阶段说明，避免每个子仓库重复放大视频文件。

## 适合谁买

需要稳定本地渲染和交付 MP4 的用户。

## 下载 / 安装方式

```bash
npx skills add https://github.com/Shinchan-crayon/remotion-renderer
```

安装后，在支持 Skill 的 Agent 中说：

```text
请使用 Remotion 渲染成片，继续处理当前 Shin-video 项目。
```

## 付费版本和定制服务入口

- 免费版：安装本 Skill，按本地 Shin-video 工作流手动配置运行。
- 付费版：可提供整套工作流安装包、环境部署协助、示例项目和远程排障。
- 定制服务：可按行业定制口播风格、导演规则、Remotion 模板、品牌视觉系统和 ThinkAI 上架页面。

咨询入口：ThinkAI Skill 广场 / GitHub Issues / 私信定制咨询

## 验收标准

使用本 Skill 后，至少要能确认：

- 已正确生成或推进到：runtime/preview.mp4
- 已正确生成或推进到：成品/成品.mp4
- 没有绕过它的上游依赖。
- 没有把本 Skill 明确不负责的事情混进来。
- 出错时能说清楚卡在哪个输入或环境条件上。

## 能力边界

- 不重新猜镜头
- 不跳过质量检查
- 不在用户未确认 preview 前导出最终成品

Shin-video 追求的是「可维护的本地视频生成工作流」，不是把所有能力塞进一个万能提示词。这个 Skill 只负责自己这一段，完整成片需要配合其它 AI 员工和本地 Shin-video 项目。
