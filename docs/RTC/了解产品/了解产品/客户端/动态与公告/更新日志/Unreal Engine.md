本文介绍了网易云信音视频通话（NERTC）为 Unreal 引擎提供的 SDK 的更新日志，后续简称 NERTC Unreal SDK。具体功能请前往 [下载 SDK 体验](https://doc.yunxin.163.com/nertc/resource?platform=UE) 和 [查看 API 文档](https://doc.yunxin.163.com/nertc/client-apis/Dc0MTIxMDE?platform=UE)。

## v5.4.128 (2024-09-26)

- 引入语音消息审核功能，增强内容管理。
- 扩展平台兼容性，新增 XBox 设备支持。如有需求，可 [提交工单](https://app.yunxin.163.com/global/service/ticket/create) 联系网易云信技术支持工程师。
- 提升系统性能，优化用户体验。

## v5.4.124 (2024-05-24)

新增 [语音消息](https://doc.yunxin.163.com/nertc/guide/jQ2MTU3NTY?platform=UE)。

## v5.4.111 (2023-11-16)

改进优化：

- 优化 `join` 流程的耗时，非中国大陆地区用户入会更快。
- 隐藏不必要的符号。
- 修复一些缺陷。

## v5.4.109 (2023-10-23)

NERTC Unreal Engine SDK 正式发布，提供了基于跨平台底层的纯音频功能，主要功能如下表所示。

| 新增特性 | 特性描述 | 参考文档
| ---- | ---- | ----
| 实时语音 | NERTC 可实现两人或多人实时语音通话，应用于游戏小队语音开黑、游戏陪玩语聊、游戏主播、狼人杀、剧本杀等需要实时通话的桌游场景。 | [实现语音通话](https://doc.yunxin.163.com/nertc/guide/Tg3NjE0NDg?platform=UE) |
| 设置音频属性 | 在游戏语音场景中，您需要根据游戏场景的特点，设置合适的音频 Profile 档位和音频场景，以确保音质和通话流畅性。 | [设置音频属性](https://doc.yunxin.163.com/nertc/guide/jExMDgxMTM?platform=UE) |
| 设置通话音量 | NERTC SDK 支持调整各种声音的音量，例如调整 SDK 采集的声音、播放的声音等。音量调节功能适用于多种需要自定义调节音量的场景。 | [设置通话音量](https://doc.yunxin.163.com/nertc/guide/TQ2NTczNDg?platform=UE) |
| 监测发言者音量 | NERTC SDK 提供监听房间内用户发送的音量值的功能，同时监听本端用户的音频数据中是否存在有效的人声信息。 | [监测发言者音量](https://doc.yunxin.163.com/nertc/guide/zEyMDQ1Mzg?platform=UE) |
| 通话中质量监测 | NERTC SDK 支持将关键的音视频状况、网络状况、设备状态的相关指标实时回调给 App 应用层，应用层可以将收到的数据进行展示或统计，以便您及时了解当前通话的整体质量。 | [通话中质量监测](https://doc.yunxin.163.com/nertc/guide/Tk3NTQ0MzA?platform=UE) |
| 美声变声 | NERTC SDK 支持设置多种预设的美声与变声音效。玩家可以将音色调整成**大叔音**、**萝莉音**等形式，在语音聊天、游戏互动等场景中展现更加有趣和吸引人的声音形象。 | [美声变声](https://doc.yunxin.163.com/nertc/guide/TExNjUwOTc?platform=UE) |

请在 [网易云信 SDK 下载中心](https://doc.yunxin.163.com/nertc/sdk-download) 下载最新的 Unreal Engine 版本。