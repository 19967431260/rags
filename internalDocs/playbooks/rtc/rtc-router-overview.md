# RTC Router Overview

Use this overview when the user reports a RTC problem but the exact failure stage is still unclear.

## Typical user complaints
- 没声音 / 声音小 / 回声 / 噪声
- 没画面 / 黑屏 / 花屏 / 模糊
- 加入房间失败
- 不确定用户是否真的加入了房间
- 服务端接口调用异常

## Stage-based routing
### A. Audio complaint
Use when the main symptom is audio-related.

Questions to ask first:
- 单向无声、双向无声、声音小、回声还是噪声？
- 平台、系统、SDK 版本？
- 有没有 QS 指标、audioDeviceEvent、日志？

Then read:
- `audio-troubleshooting.md`

### B. Video complaint
Use when the main symptom is video-related.

Questions to ask first:
- 黑屏、花屏、模糊、首帧慢还是小流异常？
- 平台、系统、SDK 版本？
- 是否可复现？有没有相关日志和关键指标？

Then read:
- `video-troubleshooting.md`

### C. Join-room failure
Use when the complaint is explicitly about entering the room failing.

Questions to ask first:
- 有没有 join 错误、token 线索、roomserver 线索？
- 是否使用信令/组件？
- 日志里是否有 response is null / token / roomserver 相关信息？

Then read:
- `join-room-failure.md`

### D. Server-side reverse check for join status
Use when you lack SDK logs but still need to know whether the user actually reached the room/join stage.

Questions to ask first:
- 是否至少有 cid / uid / 时间范围？
- 房间看起来是不是只有一人？

Then read:
- `server-data-join-room-check.md`

### E. Server API abnormal / interface abnormal
Use when the complaint focuses on API calls, server returns, or interface-level error typing.

Then read in this order:
1. `../../evidence/triage/interface-exception-triage.md`
2. `server-api-diagnostics.md`

## Cross-links and caveats
- Many user complaints that look like “SDK 问题” are actually network / config / permission / device / app-side handling issues.
- If you do not have enough evidence, ask for the minimum context before blaming SDK or server.
- Treat historical case snippets as hints, not universal laws.
