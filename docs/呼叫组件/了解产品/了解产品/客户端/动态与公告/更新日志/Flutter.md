本文介绍网易云信音视频呼叫（原呼叫组件）Flutter 端的更新日志和升级说明。

## 4.1.0 (2025-12-19)

**新增特性**

- **AI 字幕功能**：支持通话中实时 AI 字幕显示。
- **用户信息查询**：支持根据 rtcUid 获取用户信息。

**API 变更**

类/方法/回调/错误码 | 说明
--- | ---
`NECallEngine.startASRCaption` | 新增接口，用来开启字幕。
`NECallEngine.stopASRCaption` | 新增接口，用来关闭字幕。
`NECallEngine.getUserWithRtcUid` | 新增接口，用来根据 rtcUid 获取用户信息。

- `NECallEngine.call(...)` 接口的返回值修改为 `Future<NEResult<NECallInfo>>`，呼叫结果中可以获取呼叫信息。
- `NECallEngine.accept(...)` 接口的返回值修改为 `Future<NEResult<NECallInfo>>`，接听结果中可以获取呼叫信息。
- `NECallEngine.hangup(...)` 接口参数中的 `channelId` 改为可选。

**兼容版本**

- 适配 CallKit Android 4.1.0 版本。
- 适配 CallKit iOS 4.1.0 版本。

## 3.8.0 (2025-11-6)

**新增特性**

- **悬浮窗支持**：新增退后台弹出悬浮窗功能。
- **多端登录优化**：支持多端登录时，一方接听后，其他端弹出 toast 提示。

**API 变更**

类/方法/回调/错误码 | 说明
--- | ---
`NECallKitUI.instance.enableFloatWindowOutOfApp` | 新增方法，用于设置退后台弹出悬浮窗。

**问题修复**

- 优化通话页面大小画面切换黑屏的问题.
- 修复部分机型（小米 mix3）应用外小窗通话时，点击小窗无法调起通话页面，停留在应用外的问题。

**兼容版本**

- 适配 CallKit Android 3.8.0 版本。
- 适配 CallKit iOS 3.8.0 版本。

## 3.6.0 (2025-08-26)

网易云信音视频呼叫（原呼叫组件）Flutter SDK 的首次发布！

- 兼容 Android 和 iOS 平台。
- 实现一对一音视频通话基础功能。

<!--Demo
## 2025-01-20

适配 Android 14 & iOS 18 系统。

## 2024-06-13

首次发布音视频呼叫（原呼叫组件）Flutter Demo。更多详情，请访问 [Demo 体验](https://doc.yunxin.163.com/nertccallkit/guide/DYyMDk4OTY?platform=flutter)。

-->