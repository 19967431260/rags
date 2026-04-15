# Evidence Card: RTC 安卓日志解读

## 定位
这不是“怎么修”的 SOP，而是 **Android RTC 日志关键锚点说明卡**。适合在已经拿到日志后，快速判断 SDK 是否正常完成初始化、参数下发、入会、音频采集、画布初始化和首帧渲染。

## 适用场景
- 安卓 RTC 通话黑屏/无画面，但不确定问题停在哪个阶段。
- 怀疑适配配置 `nertc.cfg`、线上兼容性参数未正确生效。
- 需要确认是否真的 joinChannel、是否启用了外部音频采集、是否发生首帧渲染。
- 需要把零散日志片段翻译成“流程证据”。

## 关键证据点

### 1. 设备与 SDK 基线
- 设备信息示例：`Compat device info -> VS#KA2#mbox#0bda:3035`
- SDK 版本/分支/构建信息示例：
  `nertc: {ver:4.2.0.2301, rev:..., branch:..., host:..., type:release}`

**可证明什么**
- 当前日志来自什么设备环境。
- 使用的是哪个 SDK 版本、分支、构建机，便于和已知缺陷/适配问题对齐。

### 2. 本地兼容性配置是否被读取
- 配置路径：`local config file path is : .../nertc.cfg`
- 本地配置 dump：`dump local =>`

**可证明什么**
- SDK 是否尝试读取本地 `nertc.cfg`。
- 若 `dump local =>` 为空，文档提示要优先怀疑 **本地 json 格式错误或配置未生效**。

### 3. 线上兼容性参数拉取
- 示例：`Compat init: https://lbs.netease.im/cc/nrtc/v2 ... sdkVersion=... manufacturer=... model=... appKey=...`

**可证明什么**
- SDK 已进入线上兼容参数拉取阶段。
- 可从 URL 参数反推出设备型号、sdkVersion、appKey 等上下文，辅助判断是否命中特定机型适配。

### 4. RTC 参数设置与入会
- 参数设置：`set parameter: [KEY_VIDEO_DECODE_MODE, media_codec_hardware]`
- 入会：`joinChannel token: ... channelName: ... uid: ...`

**可证明什么**
- 某些音视频能力参数是否已下发。
- 是否真正执行到 joinChannel；若没有这类日志，问题可能还停留在初始化或业务层调用前。

### 5. 外部音频采集/镜像/画布初始化
- 外部音频：`setExternalAudioSource enable: true sampleRate:16000 channel:2`
- 镜像：`setMirror: false`
- 画布初始化：`Initializing EglRenderer`
- 画布尺寸变化：`onMeasure(). New size: 1920x1080`

**可证明什么**
- 业务层是否启用了外部音频输入。
- 视频渲染链路至少走到了视图/画布初始化阶段。

### 6. 首帧与渲染统计
- 首帧：`Reporting first rendered frame.`
- 渲染统计：`Frames received: 173. Dropped: 0. Rendered: 173. Render fps: 28.0 ...`

**可证明什么**
- 一旦出现首帧日志，至少说明“远端视频接收并渲染成功”已经发生。
- 渲染统计可辅助判断是否有掉帧、渲染卡顿、swapBuffer 过慢等现象。

## 建议给主 skill 的使用方式
1. 先从用户日志中匹配上述锚点，判断停留阶段：
   - 连 `nertc:` / `Compat init` 都没有：先查初始化是否执行。
   - 有 `joinChannel` 但无 `Initializing EglRenderer`：更偏业务层未绑定画布或渲染前链路异常。
   - 有画布初始化但无 `Reporting first rendered frame`：优先排查订阅、解码、远端上行、首帧前中断。
   - 有首帧但体验差：看渲染统计、设备性能、掉帧指标。
2. 把它当作“日志翻译卡”，不要把它当作覆盖所有 RTC 故障的排障手册。
3. 若用户尚未提供日志，这张卡价值有限，应先引导其补齐 RTC 客户端日志。

## 局限与注意事项
- 仅覆盖少量关键日志样例，不能替代完整日志知识库。
- 文档时间较早，日志字段可能随 SDK 版本变化。
- 更偏“发生了什么”的证据解释，不直接给出根因闭环。
