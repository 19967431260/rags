本文介绍呼叫组件（NERtcCallKit）Android 端的更新日志和升级说明。

## 4.1.0 (2025-12-19)

**新增特性**

- **AI 字幕功能**：支持通话中实时 AI 字幕显示。
- **用户信息查询**：支持根据 rtcUid 获取用户信息。

**API 变更**

类/方法/回调/错误码 | 说明
--- | ---
`NECallEngine.getUserWithRtcUid` | 新增接口，用来根据 rtcUid 获取用户信息。

**兼容版本**

- 兼容 `NIMSDK` 10.9.52 版本。
- 兼容 `NERtcSDK` 5.9.10 版本。                          

## 3.8.0 (2025-11-6)

**新增特性**

- **音质优化：** 引入 AI 降噪模式，显著提升通话音质。
- **群呼体验升级：**
   - 支持自定义铃声，个性化呼叫提醒。
   - 新增通话中外放切换功能，灵活调整音频输出。
   - 增加推送配置选项，优化离线通知体验。
- **界面优化：** 调整挂断按钮样式，与 iOS 版本保持一致，提升跨平台体验。

**API 变更**

**新增：**

类/方法/回调/错误码 | 说明
--- | ---
`NECallEngine.setAINSMode` | 新增方法，用于设置 AI 降噪模式。
`GroupCallParam` | 群呼入参新增 `pushParam` 字段，支持配置推送信息。

**删除**：

- 删除 `NECallEngine.setPushConfigProviderForGroup(PushConfigProviderForGroup provider)` 方法，后续使用 `GroupCallParam.pushParam` 方法设置推送相关的配置。
- 删除 `NECallParam.rtcUid` 属性，后续使用 `NECallEngine.setup(Context context, NESetupConfig config)` 中的 `NESetupConfig.currentUserRtcUid` 自定义配置 `rtcUid`。

**问题修复**

- 修复通话中视频切换音频导致的小窗消失的问题。
- 修复退出登录时未关闭通话的问题。
- 修复离线消息导致的收到异常通话的问题（离线信令处理逻辑对齐 iOS 端）。

**兼容版本**

- 适配 NIM SDK 10.9.52 版本。
- 适配 NERtc SDK 5.9.10 版本。

**升级建议**

由于本次更新涉及接口删除，建议开发者在升级时全面检查相关接口。

## 3.7.0 (2025-09-26)

**新增特性**

- **多人通话结束通知**：新增通话结束回调机制，支持获取详细的会话终止信息，方便开发者进行后续业务逻辑处理。
- **挂断操作信息扩展**：挂断事件中新增消息参数，可传递更丰富的挂断原因和上下文信息。

**API 变更**

类/方法/回调/错误码 | 说明
--- | ---
`ChannelProfile` | 默认值修改为 `STANDARD_VIDEOCALL`。
`NEGroupCallDelegate.onGroupCallEnd` | 新增回调，支持获取多人通话结束的详细信息。
`GroupCallHangupEvent` | 新增 `message` 参数，支持获取挂断操作的详细信息。

**接口合并优化**：

- 将回调 `NEGroupCall.configGroupActionObserver(NEGroupCallActionObserver observer)` 合并到 `NEGroupCall.addGroupCallDelegate(NEGroupCallDelegate delegate)`。
- 将回调 `NEGroupCall.configGroupIncomingReceiver(NEGroupIncomingCallReceiver receiver)` 合并到 `NEGroupCall.addGroupCallDelegate(NEGroupCallDelegate delegate)`。

**问题修复**

修复前台进程无法正常关闭的问题。

**兼容版本**

- 适配 NIM SDK 10.9.45 版本。
- 适配 NERtc SDK 5.9.10 版本。

**升级建议**

- 由于本次更新涉及回调接口合并，建议开发者在升级时全面检查通话相关回调的实现逻辑。
- 如已自定义 `ChannelProfile` 配置，请评估默认值变更对现有业务的影响。

## 3.6.0 (2025-08-26)

**新增特性**

- 新增扬声器开关配置。
- 新增麦克风开关配置。

**API 变更**

类/方法/回调/错误码 | 说明
--- | ---
`NECallEngine.isSpeakerphoneOn()` | 新增方法，用于获取是否开启扬声器。
`NECallEngine.setSpeakerphoneOn(boolean enable)` | 新增方法，用于设置是否开启麦克风。
`NECallEngine.setupLocalView` | 接口变更，入参 `videoRender` 的类型由 `NERtcVideoView` 变更为 `IVideoRender`。
`NECallEngine.setupRemoteView` | 接口变更，入参 `videoRender` 的类型由 `NERtcVideoView` 变更为 `IVideoRender`。

**兼容版本**

- 适配 NIM SDK 10.9.10 版本。
- 适配 NERtc SDK 5.9.5 版本。

## 3.5.5 (2025-04-21)

**缺陷修复**

- 修复了通话结束后前台服务未自动关闭的问题。通话结束后将正确释放系统资源，减少后台耗电。
- 修复了来电显示时被叫方的昵称和头像显示错误的问题。在多人通话或企业通讯场景，确保用户身份信息正确展示，提升用户识别体验。

**兼容版本**

- 适配 NIM SDK 10.8.0 版本。
- 适配 NERtc SDK 5.7.0 版本。

## 3.5.0 (2025-02-18)

**新增特性**

升级兼容的 NIM SDK 和 NERtc SDK 版本。

**兼容版本**

- 适配 NIM SDK 10.8.0 版本。
- 适配 NERtc SDK 5.7.0 版本。

## 3.4.0 (2025-02-14)

**新增特性** 

支持 iOS 的系统电话接听（LiveCommunicationKit）功能。

**兼容版本**

- 适配 NIM SDK 10.6.0 版本。
- 适配 NERtc SDK 5.6.50 版本。

## 3.3.0 (2025-01-23)

**新增特性** 

适配 Target SDK 34。

**兼容版本**

- 适配 NIM SDK 10.6.0 版本。
- 适配 NERtc SDK 5.6.50 版本。

## 3.2.0 (2024-12-30)

- 优化呼叫组件的初始化（不再依赖 [IM 即时通讯](https://doc.yunxin.163.com/messaging2/concept/DI0Nzc2NzA?platform=client) 的初始化）。
- 解决因 USE_FILL_SCREEN_INTENT 权限导致的 Google 上架失败问题。
- 修复其他已知问题。

## 3.0.0 (2024-11-12)

- 支持群组通话功能，具体请参见 [群组通话](https://doc.yunxin.163.com/nertccallkit/guide/TMwNDg3NzU?platform=android)。
- 升级底层兼容的 IM 版本至 V10。
- 修复群组相关问题。

**兼容版本**

- 适配 NIM SDK 10.5.0 版本。
- 适配 NERtc SDK 5.5.40 版本。

## 2.5.1 (2024-08-06)

**问题修复**

修复在某些场景下呼叫铃声异常的问题。

## 2.4.0 (2024-03-28)

**新增特性**

文案、铃声支持国际化。

**兼容版本**

- 适配 NIM SDK 9.14.2 版本。
- 适配 NERtc SDK 5.5.21 版本。

## 2.3.0 (2024-03-01)

**改进优化**

统一日志路径（IM 日志默认路径）。

**问题修复**

修复部分已知问题。

**兼容版本**

- 适配 NIM SDK 9.14.2 版本。
- 适配 NERtc SDK 5.5.21 版本。

## 2.2.6 (2024-01-29)

内部优化。

**兼容版本**

- 适配 NIM SDK 9.14.2 版本。
- 适配 NERtc SDK 5.5.21 版本。

## 2.2.5 (2024-01-23)

已知问题修复。

**兼容版本**

- 适配 NIM SDK 9.14.2 版本。
- 适配 NERtc SDK 5.5.21 版本。

## 2.2.4 (2024-01-02)

**新增特性**

- 支持角标通知，在呼叫时通过配置 `NECallPushConfig.needBadge` 参数来设置是否有角标通知。
- 初始化时 `NESetupConfig` 中不需要再传入 `currentUserAccId` 参数，由内部自动获取。

**兼容版本**

- 适配 NIM SDK V9.14.0 版本。
- 适配 NERTC SDK V5.5.2 版本。

## 2.2.2 (2023-12-13)

`channelProfile`参数的默认值修改为 `LIVE_BROADCASTING`。

## 2.2.0 (2023-11-07)

**新增特性**

- UI 组件新增小窗功能，默认不开启，可在初始化时配置 `enableFloatingWindow` 参数。
- UI 组件新增被呼叫预览功能，默认不开启，可在初始化时配置 `enableVideoCalleePreview` 参数。
- UI 组件新增虚化（通话中）功能，默认不开启，可在初始化时配置 `enableVirtualBlur` 参数。

**API 变更**

`UserInfoHelper` 接口移除 `fetchNicknameByTeam` 、`loadAvatar`，新增 `fetchAvatar` 接口。

**兼容版本**

- 适配 NIM SDK V9.12.0 版本。
- 适配 NERTC SDK V5.5.2 版本。

## 2.1.2 (2023-08-31)

**兼容版本**

- 适配 NIM V9.12.0 版本。

- 适配 NERTC SDK V5.4.8 版本。

## 2.1.0 (2023-08-08)

**新增特性**

支持在通话中配置 `P2PUIConfig` 参数，以开启或关闭应用进程保持前台服务的功能。

**改进优化**

- UI 组件内部实现替换为呼叫组件 2.0 的 API。

- 调用 `accept` 接口时，如果对方不在线，结束通话流程。

- 自定义 UI 的方式调整为使用 Fragment 进行自定义。

- 呼叫铃声的实现方式修改为使用 MediaPlayer 实现。

**问题修复**

修复异常挂断后通话失败的问题。

**升级说明**

- 含 UI 集成的用户，请参考 [升级指南（V2）](https://doc.yunxin.163.com/nertccallkit/guide/zUzMDU3Mzc?platform=android)从 V2.0.0 到 V2.1.0 版本。
- 不含 UI 集成的用户，可以从 V2.0.0 版本直接升级至 V2.1.0 版本。

**兼容版本**

- 适配 NIM V9.12.0 版本。
- 适配 NERTC SDK V5.4.0 版本。

## 2.0.0 (2023-05-29)

**改进优化**

Android、iOS、Web 各端接口和字段对齐，更新后的 API 接口请参见 [呼叫组件 V2.0.0 API 参考](https://doc.yunxin.163.com/nertccallkit/references/android/doxygen/Latest/zh/html/index.html)。

::: note note
- 集成了呼叫组件 V2.0 版本的用户能和呼叫组件 V1.x 的用户进行通话。
- 请确保代码中全使用 V2.0 版本的接口或全使用 V1.x 版本的接口， V2.0 版本的接口和 V1.x 版本的接口请勿混用。
:::

**API 变更**

`CallKitUIOptions#rtcInitScope` 接口，被 `CallKitUIOptions#initRtcMode` 接口替换，其中 Boolean 类型参数改为 Int 类型参数：

```java
  /** 呼叫组件初始化 rtc sdk 模式 */
public @interface NECallInitRtcMode {
  /** 全局初始化 rtc 一次 */
  int GLOBAL = 1;
  /** 按需初始化，主叫在呼叫时初始化 rtc ，被叫在收到呼叫时初始化 rtc ，通话结束销毁 rtc */
  int IN_NEED = 2;
  /** 和{@link NECallInitRtcMode#IN_NEED}类似，区别在于被叫接听时才初始化 rtc，其他一致 */
  int IN_NEED_DELAY_TO_ACCEPT = 3;
}
```

**升级说明**

从 V1.8.2 版本升级到 V2.0.0 版本，不影响您继续使用 V1.8.2 版本的接口。详细的接口变更和升级说明请参见[升级指南（V2）](https://doc.yunxin.163.com/nertccallkit/docs/zUzMDU3Mzc?platform=android)。

**兼容版本**

- 适配 NIM V9.10.0 版本。
- 适配 NERTC SDK V4.6.50 版本。

## 1.8.2 (2023-02-28)

**改进优化**

适配 IM UIKit，支持在 IM UIKit V9.4.0 及以上版本中集成呼叫组件。

**升级说明**

V1.8.1 版本可直接升级至 V1.8.2 版本。

**兼容版本**

- 适配 NIM V9.8.0 版本。
- 适配 NERTC SDK V4.6.29 版本。

## 1.8.1 (2022-11-29)

**改进优化**

优化主叫方视频预览的实现逻辑。

**升级说明**

V1.8.0 版本可直接升级至 V1.8.1 版本。

**兼容版本**

- 适配 NIM V9.6.4 版本。
- 适配 NERTC SDK V4.6.29 版本。

## 1.8.0 (2022-11-01)

**新增特性**

- 单击本地预览小窗，切换画布
- 支持设置关闭摄像头时的数据采集模式，具体请参见<a href="https://doc.yunxin.163.com/nertccallkit/guide/jE1NDM1ODI?platform=android" target="_blank">自定义 UI</a>。
- 支持设置主叫在呼叫时是否加入 RTC 房间

**API 变更**

- `NERTCVideoCall#accept`接口，删除 `invitedParam` 和 `selfAccId` 参数。修改为如下代码：
   ```java
   void accept(JoinChannelCallBack joinChannelCallBack);
   ```
- `NERTCVideoCall#reject`接口，删除 `inviteParam` 参数，修改为如下代码：

   ```java
   void reject(RequestCallback<Void> callback);
   ```

- `CallKitUIOptions`接口中新增 `joinRtcWhenCall` 参数，设置主叫在呼叫时是否加入 RTC 房间。

   ```java
   // 主叫是否在呼叫时加入rtc房间，默认为false，不提前加入，在被叫接听时加入。如果设置提前加入房间，会带来通话费用的增加，同时提升首帧开画时间
   CallKitUIOptions options = new CallKitUIOptions.Builder()
     .joinRtcWhenCall(false) // true：在呼叫时加入，false：在被叫接听时加入
     ......
     .build();
   // 初始化
   CallKitUI.init(getApplicationContext(), options);
   ```

**API 删除**

接口 | 说明
---- | -------------- 
`NERTCVideoCall#setTokenService` | 不需要您额外通过 TokenService 请求 RTC 的 Token，呼叫组件内部已实现相关获取流程。
`CallKitUIOptions#rtcTokenService` | ^^

**改进优化**

- 优化首帧时长。
- Android API 版本（compileSdkVersion）需要满足最低为 31 及以上版本。

**升级说明**

不可直接升级，从 V1.6.4 版本升级至 V1.8.0 版本时，您需要在代码中对新增和变更的接口进行修改和适配，主要变更如下：
- 引入组件库的地址修改为：

   ```groovy
   implementation 'com.netease.yunxin.kit.call:call:1.8.0'     // 基础组件包
   implementation 'com.netease.yunxin.kit.call:call-ui:1.8.0'  // UI 包
   ```

- 业务应用不再需要通过 `TokenService` 获取 RTC Token，呼叫组件内部已实现相关获取流程。

**兼容版本**

- 适配 NIM V9.6.4 版本。
- 适配 NERTC SDK V4.6.22 版本。

::: note note
为了避免出现未知错误，NIM 和 NERTC 请使用以上指定的配套版本。
:::

## 1.6.4 (2022-08-30)

**新增特性**

- UI 层支持在音频通话中显示或隐藏 **音频转视频** 按钮开关。实现方法修改如下：
- 去除呼叫组件对自定义消息的影响。

**API 变更**

UI 层支持在音频通话中显示或隐藏 **音频转视频** 按钮开关。实现方法修改如下：

- 自定义 activity（例如TestActivity） 继承 P2PCallActivity，示例代码如下：
   ```
   public class TestActivity extends P2PCallActivity {
   @NonNull
   @Override
   protected P2pUIConfig provideUIConfig() {
      // true 显示，false 隐藏；
      return new P2pUIConfig(value);
   }
   }
   ```
- 在组件初始化处注册此 Activity。

   ```
   CallKitUIOptions options = new CallKitUIOptions.Builder()
   .p2pAudioActivity(TestActivity.class) // 音频；
   .p2pVideoActivity(TestActivity.class) // 视频， 若音频/视频通话页面共用同一个页面则视频也需要注册；
   ......
   .build();
   // 初始化
   CallKitUI.init(getApplicationContext(), options);
   ```

**升级说明**

V1.6.1 版本可直接升级至 V1.6.4 版本。

**兼容版本**

- 适配 NIM V9.2.5 版本。
- 适配 NERTC SDK V4.6.12 版本。

## 1.6.1 (2022-08-22)

**新增特性**

- 支持音视频通话切换确认。
- `TokenService#getToken` 接口新增 `channelName` 参数。

**新增 API**

| 接口名称           | 接口说明                                                                         |
|:--------------------|:--------------------------------------------------------------------------------------|
|`enableSwitchCallTypeConfirm` | 音视频切换确认，默认不开启确认。 |
| `onCallTypeChange`| 音视频切换回调，新增回调中有音视频切换指令类型，如果未开启音视频切换确认配置，可忽略第二个字段。 |

**API 变更**

| 接口名称           | 接口说明                                                                         |
|:--------------------|:--------------------------------------------------------------------------------------|
|`switchCallType`|增加 `state` 参数，用于获取音视频切换确认的状态。 |
| `TokenService#getToken` | 新增 `channelName` 参数。 |

**升级说明**

V1.5.7 版本可直接升级至 V1.6.1 版本。

**兼容版本**

- 适配 NIM V9.2.5 版本。
- 适配 NERTC SDK V4.6.12 版本。

## 1.5.7 (2022-07-19)

**新增特性**
- 支持在初始化时关联呼叫组件 `accId` 对应的 `rtcUid`，以便消息抄送时能获取到对应的用户。
- 支持呼叫时绑定该呼叫对应的 RTC 房间名称（`channelName`）。
- 支持呼叫或接听时直接设置 `rtcToken`。

**改进优化**

去除对 `blankj` 三方库的依赖。

**API 变更**

- `init`接口中增加 `currentUserRtcUId` 参数，关联呼叫组件 `accId` 对应的 `rtcUid`，以便消息抄送时能获取到对应的用户。
   ```
   // 初始化时传入自定义 uid 参数
   CallKitUIOptions options = new CallKitUIOptions.Builder()
      .currentUserRtcUId(123L) // 自定义rtc uid 参数
   .currentUserAccId("accId") // 用户云信 IM sdk 登录的 accId
   ......
   .build();
   // 初始化
   CallKitUI.init(getApplicationContext(), options);
   ```
- `call` 接口中增加 `channelName` 参数，用于绑定 RTC 房间的名称。
   ```
   CallParam param = new CallParam.Builder()
   .rtcChannelName("channelName")// 自定义呼叫的音视频房间名称
      ......
   .build();
   CallKitUI.startSingleCall(context, param);// 发起呼叫
   ```

   ```
   // 自定义 ui 用户
   SingleCallParam param = new SingleCallParam(
      p2pCalledAccId, // 被叫用户 accId
      ChannelType.retrieveType(channelType), // 呼叫类型
      extJsonStr, // 主叫透传给被叫的透传参数，可无
      globalExtraCopy,// 全局抄送只用于服务端解析，可无
      rtcChannelName,// 自定义的音视频房间名称
      rtcToken //呼叫时用户加入音视频房间的token
   )；
   NERTCVideoCall.sharedInstance().call(param,callback )// 发起呼叫
   ```

-  `accept` 接口中增加 `token` 参数，用于呼叫时传入 rtc token。

      ```
      // 对于主叫参考上述 2.支持呼叫时自定义音视频房间名称
      // 对于被叫用户：accept 接口增加 token 字段
      NERTCVideoCall.sharedInstance().accept(param,  // 呼叫参数
                                             token,  // 自定义 token 可无
                                             callback) // 结果回调
      ```

**升级说明**

V1.5.5 版本可直接升级至 V1.5.7 版本。

**兼容版本**

- 适配 NIM V9.2.5 版本。
- 适配 NERTC SDK V4.6.12 版本。

## 1.5.5 (2022-06-07)

**新增特性**

- 1 对 1 呼叫时，支持全局服务端抄送参数。
- 支持占线挂断。

**新增 API**

| 接口名称           | 接口说明                                                                         |
|:--------------------|:--------------------------------------------------------------------------------------|
| `call` | 开始呼叫。通过 `globalExtraCopy` 参数，设置呼叫时的全局抄送信息。 |
| `hangup`  | 通过 `reason` 参数控制挂断原因，例如被叫用户可通过 `NERTCVideoCall#hangup(null,TerminalCode#TERMINAL_CODE_BUSY，null)` 实现占线挂断。 |

**升级说明**

V1.5.4 版本可直接升级至 V1.5.5 版本。

**兼容版本**

- 适配 NIM V8.5.5 版本。
- 适配 NERTC SDK V4.2.142 版本。

## 1.5.4 (2022-05-19)

**问题修复**

修复 Android 的系统版本较高时，因通知中缺少 `FLAG_IMMUTABLE` 而导致崩溃。

**升级说明**

V1.5.3 版本可直接升级至 V1.5.4 版本。

**兼容版本**

- 适配 NIM V8.5.5 版本。
- 适配 NERTC SDK V4.2.140 版本。

## 1.5.3 (2022-04-26)

**新增特性**

当拒接或占线时，支持关闭信令房间，避免服务端收不到对应的关闭房间抄送。

**问题修复**

修复部分已知问题。

**升级说明**

V1.5.0 版本可直接升级至 V1.5.3 版本。

**兼容版本**

- 适配 NIM V8.5.5 版本。
- 适配 NERTC SDK V4.2.124 版本。

## 1.5.0 （2021-12-23）

**问题修复**

修复部分已知问题。

**升级说明**

V1.4.2 版本可直接升级至 V1.5.0 版本。

**兼容版本**

- 适配 NIM V8.5.5 版本。
- 适配 NERTC SDK V4.2.120 版本。

## 1.4.2 (2021-11-25)

**API 变更**

`supportAutoJoinWhenCalled` 接口的参数默认值修改为 false。

**问题修复**

修复部分已知问题。

**升级说明**

从V1.4.0 版本升级至 V1.4.2 版本时，请注意如下变更：

`supportAutoJoinWhenCalled` 接口的参数默认值由 true 调整为 false。该变更影响通话接通前，切换音视频通话类型。

**兼容版本**

- 适配 NIM V8.5.5 版本。
- 适配 NERTC SDK V4.2.115 版本。

## 1.4.0 (2021-09-28)

**新增特性**

- 添加音频转视频功能。
- 增加通话中根据 accId 获取 rtcUid 或根据 rtcUid 获取 accId。
- 支持呼叫通话前支持切换通话类型。
- 修改组件展示 demo，从即时通讯 Demo 更换为 1 对 1 demo。
- 适配 SDK 版本更新。

**新增 API**

- `NERTCVideoCall#getAccIdByRtcUid`：根据 RtcUid 获取对应的 AccId。
- `NERTCVideoCall#getRtcUidByAccId`：根据 AccId 获取对应的 RtcUid。

**API 更新**

- `NERTCVideoCall#switchCallType` 支持 `ChannelType#VIDEO` 参数从音频切换为视频通话。
- `CallKitNotificationConfig` 构造函数变更，新增 `channelId` 参数。

**升级说明**

V1.3.3 版本可直接升级至 V1.4.0 版本。

**兼容版本**

- 适配 NIM V8.5.5 版本。
- 适配 NERTC SDK V4.2.105 版本。

## 1.3.3 (2021-08-26)

**新增特性**

- 支持自定义呼叫推送配置。
- 支持 UI 组件，用户可通过引入呼叫 UI 组件实现接入。
- 支持设置失败话单发送开关。
- 支持自定义 CallService 允许用户自己实现呼叫⻚面启动。
- 支持 CallExtension 用于 rtc 相关扩展（如修改 rtc 初始化流程）。

**新增 API**

- `NERTCVideoCall#setCallExtension`：RTC 功能扩展。

- `VideoCallOptions#enableOrder`：本地话单开关。

**升级说明**

若您从 V1.3.1 升级至 V1.3.3，请注意：

- 将 `implementation 'com.netease.yunxin.kit:call:1.3.3'` 替换为 `implementation 'com.netease.yunxin.kit:call-adapter:1.3.3'`；
- 将 `CallParams` 替换为 `SelfParams`；
- 将 `NERTCVideoCall` 替换为 `NERTCVideoCallWrapper`；
- 将 `VideoCallOptions` 替换为 `VideoCallOptionsWrapper`；
- `VideoCallOptions` 删除 `uiService` 字段，通过 `VideoCallOptionsWrapper` 设置此字段；
- `VideoCallOptions`中新增 `enableOrder` 字段 用于控制本地不带时长话单的发送，时长话单发送开关需到云信后台设置；
- `VideoCallOptions`中新增 `logRootPath` 字段用于配置组件日志路径，若用户设置 `IM Sdk` 路径则最好将此路径同样设置给组件；
- `NERTCVideoCall` 新增接口 `setCallExtension` 用于设置 rtc 相关配置以及调用；
- `NERTCVideoCall` 新增接口 `setPushConfigProvider` 用于设置呼叫推送配置。

**兼容版本**

- 适配 NIM V8.5.5 版本。
- 适配 NERTC SDK V4.0.9 版本。

## 1.3.1 (2021-07-16)

**问题修复**

修复外部设置视频参数无效问题。

**兼容版本**

- 适配 NIM V8.4.6 版本。
- 适配 NERTC SDK V4.0.7 版本。

## 1.3.0 (2021-06-24)

**新增特性**

- 添加回调 `onJoinChannel` 接口方法，用于告知 `channelName`，`channelId`，`uid`，`accid` 关系映射。
- 移动端添加 `muteLocalVideo` 接口以及 `onVideoMute` 回调。
- 移动端添加 `onAudioMute` 回调。
- `call`、`groupCall`、`groupInvite` 接口支持自定义扩展参数，被叫方在 `onInvited` 回调中解析对应参数。

**新增 API**

`NERTCCallingDelegate#onJoinChannel` 用于本地用户映射 `AccId`、`RtcUid`、`rtcChannelName`、`rtcChannelId`。

**升级说明**

若您从 V1.2.0 升级至 V1.3.0，请参考以下说明：

- `NERTCVideoCall`添加视频采集控制接口：

   ```java
      /**
      	* 开启/关闭视频采集
      	* @param isMute    true:视频采集关闭 false:视频采集打开
      	*/
      public abstract void muteLocalVideo(boolean isMute);
   ```

   接口调用会触发 `NERTCCallingDelegate.onVideoMuted()` 回调；

- `NERTCCallingDelegate`添加音频采集控制回调接口，通过 

   `NERtcVideoCall.muteLocalAudio` 方法调用触发：

      ```java
   /**
   	* 远端用户是否开启音频流采集
   	* @param userId    远端用户id
   	* @param isMuted   true:关闭，false:开启
   	*/
   void onAudioMuted(String userId, boolean isMuted);
      ```

- `NERTCCallingDelegate` 添加 `onJoinChannel` 接口，此接口当用户加入音视频房间时触发此回调，用户可通过此回调获取用户 IM 的账号 Id在此次通话中的 uid 以及音视频房间的房间 Id 以及名称。

   ```java
     /**
     	* 当前用户加入音视频的回调
     	*
     	* @param accId         用户 id
     	* @param uid           用户用于加入 rtc 房间的 uid
     	* @param channelName   用户加入 rtc 房间的通道名称
     	* @param rtcChannelId  rtc 房间通道 id
     	*/
     void onJoinChannel(String accId, long uid, String channelName, long rtcChannelId);
   ```

- 呼叫接口变更  `NERtcVideoCall.call`、 `NERtcVideoCall.groupCall`、 `NERtcVideoCall.grouInvite` 均增加 `extraInfo` 参数，此参数用户传递自定义参数，在被叫方收到邀请通知时可解析出。

   ```java
       private NERTCCallingDelegate callingDelegate = new NERTCCallingDelegate() {
              @Override
              public void onInvited(InvitedInfo invitedInfo) {
                  // 被叫用户通过 invitedInfo.attachment 获取对应自定义参数；
              }
         //......
       }
   ```

**兼容版本**

- 适配 NIM V8.4.6 版本。
- 适配 NERTC SDK V4.0.7 版本。

## 1.2.1 (2021-06-08)

**问题修复**

- 修复服务端删除房间/踢出某个成员后，通话没有结束。
- 修复频繁挂断通话场景下低概率导致上一通通话影响下一通通话。
- 修复一对一通话时一方加入 rtc 失败时另外一端可正常进入通话。

**兼容版本**

- 适配 NIM V8.4.6 版本。
- 适配 NERTC SDK V4.0.7 版本。

## 1.2.0 (2021-05-14)

**新增特性**

- 添加多人通话，呼叫发起方可以在通话中途邀请其他用户。
- 1v1 视频呼叫添加本地视频预览。
- 在收到首帧回调时才会刷新 UI。

**新增 API**

`NERTCVideoCall#groupInvite` 主叫在多人通话中邀请其他用户。

**问题修复**

修复已知问题，提供稳定性。

**兼容版本**

- 适配 NIM V8.3.1 版本。
- 适配 NERTC SDK V4.0.3 版本。

## 1.1.0 (2021-04-25)

**新增特性**

首屏接通流程优化，提升接通速度。

**问题修复**

- 修复呼叫状态下，主叫突然断网，被叫方接受，主叫方网络恢复后没有收到对方 “接受” 的问题。
- 修复 IM 被踢后音视频房间未退出问题。

**兼容版本**

- 适配 NIM V8.3.1 版本。
- 适配 NERTC SDK V4.0.3 版本。