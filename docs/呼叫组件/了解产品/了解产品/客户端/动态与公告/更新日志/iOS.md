本文介绍呼叫组件（NERtcCallKit）iOS 端的更新日志和升级说明。

## 4.1.0 (2025-12-19)

**新增特性**

- **AI 字幕功能**：支持通话中实时 AI 字幕显示。
- **用户信息查询**：支持根据 rtcUid 获取用户信息。

**API 变更**

类/方法/回调/错误码 | 说明
--- | ---
`NECallEngine.getUserWithRtcUid` | 新增接口，用来根据 rtcUid 获取用户信息。

**兼容版本**

- 兼容 `NIMSDK` 10.9.53 版本。
- 兼容 `NERtcSDK` 5.9.10 版本。  

## 3.8.0 (2025-11-6)

**新增特性**

- **音质优化：** 引入 AI 降噪模式，显著提升通话音质。
- **群呼体验升级：**
   - 支持自定义铃声，个性化呼叫提醒。
   - 新增通话中外放切换功能，灵活调整音频输出。
   - 新增自定义配置频道名称。
- **界面优化：** 优化通话时关闭视频的显示界面。

**API 变更**

类/方法/回调/错误码 | 说明
--- | ---
`NECallEngine.setAINSMode` | 新增方法，用于设置 AI 降噪模式。
`NEUIGroupCallParam` | 群呼入参新增 `callId` 字段，支持自定义配置 `rtcChannelName`。
`NECallEngine.setupRemoteCanvas` | 新增方法，用于设置自定义远端画布属性。
`NECallEngine.dismissIncomingCall` | 新增方法，用于关闭系统接听 UI。
`NECallSystemIncomingCallParam` | 新增 `autoAccept` 参数，用于设置当用户按下接听按钮时的自定义接听逻辑，默认为 SDK 实现。


**变更**：

- 单聊呼叫默认超时时间调整为 30 秒。
- 登出 IM 时，将自动结束正在进行中的通话。

**问题修复**

修复连续两次点击接听按钮可能导致的通话中页面异常消失的问题。

**兼容版本**

- 适配 NIM SDK 10.9.53 版本。
- 适配 NERtc SDK 5.9.10 版本。

## 3.7.0 (2025-09-26)

**新增特性**

- **多人通话结束通知**：新增通话结束回调机制，支持获取详细的会话终止信息，便于开发者处理后续业务逻辑。
- **单呼小窗功能**：支持通话界面小窗拖拽功能，提升多任务操作体验。
- **群呼 UI 支持**：全新群组通话界面，优化多人通话视觉交互体验。

**API 变更**

类/方法/回调/错误码 | 说明
--- | ---
`ChannelProfile` | 默认值修改为 `STANDARD_VIDEOCALL`。
`onGroupEndCallWithReason` | 回调参数变更，`Reason` 参数改为 NSInteger 类型，并新增 `message` 参数，用来获取挂断相关的信息。

**兼容版本**

- 适配 NIM SDK 10.9.40 版本。
- 适配 NERtc SDK 5.9.10 版本。

**升级建议**

- 注意检查 `onGroupEndCallWithReason` 回调中 `Reason` 参数的使用逻辑，确保兼容类型变更。
- 如有自定义通话界面，请评估新增小窗和群呼功能的集成方案。

## 3.6.0 (2025-08-26)

**新增特性**

- 新增扬声器开关配置。
- 新增麦克风开关配置。

**API 变更**

类/方法/回调/错误码 | 说明
--- | ---
`NECallEngine.isSpeakerphoneOn()` | 新增方法，用于获取是否开启扬声器。
`NECallEngine.setSpeakerphoneOn(boolean enable)` | 新增方法，用于设置是否开启麦克风。

**缺陷修复**

修复 **LiveCommunicationKit** 可能出现的崩溃问题。

**兼容版本**

- 适配 NIM SDK 10.9.10 版本。
- 适配 NERtc SDK 5.9.5 版本。

## 3.5.0 (2025-02-18)

**新增特性**

升级兼容的 NIM SDK 和 NERtc SDK 版本。

**优化**

系统来电弹窗显示兼容历史版本。

**兼容版本**

- 适配 NIM SDK 10.8.0 版本。
- 适配 NERtc SDK 5.7.0 版本。

## 3.4.0 (2025-02-14)

**新增特性** 

支持系统电话接听（LiveCommunicationKit）功能，具体请参考 [系统电话接听](https://doc.yunxin.163.com/nertccallkit/guide/TAzMjg5NjE?platform=iOS) 文档。

**API 变更**

类/方法/回调/错误码 | 说明
--- | ---
`reportIncomingCallWithParam` | 新增接口，根据传入的显示信息，进行解析并弹出系统来电提示/接听提示 UI。
`NECallSystemIncomingCallParam` | 新增参数类，配置来电信息。
`NECallSystemIncomingCustomCallParam` | 新增参数类，自定义来电信息。优先级更高，会覆盖 payload 显示信息，如自定义显示来电信息，来电类型等。

**兼容版本**

- 适配 NIM SDK 10.6.0 版本。
- 适配 NERtc SDK 5.6.50 版本。

## 3.3.0 (2025-01-23)

**新增特性** 

支持 XCFramework 框架。

**API 变更**

音视频频道信息类 `NERtcInfo` 新增 `cid` 字段，表示音视频会话 ID。 

**兼容版本**

- 适配 NIM SDK 10.6.0 版本。
- 适配 NERtc SDK 5.6.50 版本。

## 3.2.0 (2024-12-30)

修复已知问题。

## 3.1.0  (2024-11-22)

**新增特性** 

- 单呼支持自定义 Token 传入。
- 兼容 iOS 18 系统。

**API 变更**

将 `NERtcCallUIKit` 组件下 `NEVideoView` 中的 `maskView` 属性替换为 `coverView`。

**兼容版本**

- 适配 NIM SDK 10.5.0 版本。
- 适配 NERtc SDK 5.5.40 版本。

## 3.0.0 (2024-11-12)

**新增特性** 

- 支持群组通话功能，具体请参见 [群组通话](https://doc.yunxin.163.com/nertccallkit/guide/TcxNzQxNTY?platform=iOS)。
- 升级底层兼容的 IM 版本至 V10。
- 修复群组相关问题。

**兼容版本**

- 适配 NIM SDK 10.5.0 版本。
- 适配 NERtc SDK 5.5.40 版本。

## 2.5.2  (2024-12-16)

**新增特性** 

兼容 iOS 18 系统。

**API 变更**

将 `NERtcCallUIKit` 组件下 `NEVideoView` 中的 `maskView` 属性替换为 `coverView`。

## <span id="2.5.0 (2024-08-06)">2.5.0 (2024-08-06)</span>

**问题修复**

修复没有麦克风权限的情况下通话状态异常的问题。

## <span id="2.4.0 (2024-03-28)">2.4.0 (2024-03-28)</span>

**新增特性**

文案、铃声支持国际化。

**兼容版本**

- 适配 NIM SDK 9.14.2 版本。
- 适配 NERtc SDK 5.5.21 版本。

## <span id="2.3.0 (2024-03-01)">2.3.0 (2024-03-01)</span>

**问题修复**

修复部分已知问题。

**兼容版本**

- 适配 NIM SDK 9.14.2 版本。
- 适配 NERtc SDK 5.5.21 版本。

## <span id="2.2.5 (2024-01-23)">2.2.5 (2024-01-23)</span>

**兼容版本**

- 适配 NIM SDK 9.14.2 版本。
- 适配 NERtc SDK 5.5.21 版本。

## <span id="2.2.4 (2024-01-02)">2.2.4 (2024-01-02)</span>

**变更**

初始化时 `NESetupConfig` 中不需要再传入 `currentUserAccId` 参数，由内部自动获取。

**兼容版本**

- 适配 NIM SDK V9.14.0 版本。
- 适配 NERTC SDK V5.5.2 版本。

## <span id="2.2.2 (2023-12-13)">2.2.2 (2023-12-13)</span>

**变更**

`channelProfile` 参数的默认值修改为 `LIVE_BROADCASTING`。

## <span id="2.2.0 (2023-11-03)">2.2.0 (2023-11-03)</span>

**新增特性**

- UI 组件新增小窗功能，默认不开启，可在初始化时配置相应参数：

   - 新增应用内小窗功能（通过 Rtc Canvas View 实现），初始化时配置 `enableFloatingWindow` 参数。
   - 新增应用外小窗功能（通过系统画中画实现），初始化时配置 `enableFloatingWindowOutOfApp` 参数, 同时依赖 `NETranscodingKit` 转码扩展包，只需要在主工程总引入，内部会判断此插件扩展包是否集成。

- UI 组件新增被呼叫预览功能，默认不开启，可在初始化时配置 `enableCalleePreview` 参数。
- UI 组件支持铃声。只有带UI的呼叫组件支持自定义铃声。提前加入 RTC 的模式不支持铃声，请引入 UI 组件源码自行实现。
- UI 组件新增虚化（通话中）功能，默认不开启，可在初始化时配置 `enableVirtualBackground` 参数。

**改进优化**

被呼叫后调用 `accept` 接口时，如果加入 RTC 失败，此场景下除了在`accept` 接口返回对应的 error 信息，也同时触发 `onCallEnd` 回调。

**兼容版本**

- 适配 NIM SDK V9.12.0 版本。
- 适配 NERTC SDK V5.5.2 版本。

## <span id="2.1.0 (2023-08-08)">2.1.0 (2023-08-08)</span>

**API 变更**

`accept` 和 `hangup` 接口的回调函数中增加 `NECallInfo` 参数。

**改进优化**

- UI 组件内部实现替换为呼叫组件 2.0 的 API。
- UI 组件添加完全自定义的 UI 基础界面，可以通过 UI 组件控制主叫和被叫的弹出界面。
- 修改 `onCallEnd` 方法，使其一次通话只回调一次。
- 调用 `accept` 接口时，如果对方不在线，结束通话流程。

**问题修复**

修复在视频切换音频、前后摄像头切换时，未隐藏按钮的问题。

**升级说明**

从 V2.0.0  版本可直接升级至 V2.1.0 版本。

**兼容版本**

- 适配 NIM V9.12.0 版本。
- 适配 NERTC SDK V5.4.3 版本。

## <span id="2.0.0 (2023-05-29)">2.0.0 (2023-05-29)</span>

**改进优化**

Android、iOS、Web 各端接口和字段对齐，更新后的 API 接口请参见 [呼叫组件 V2.0 API参考](https://doc.yunxin.163.com/nertccallkit/references/iOS/doxygen/Latest/zh/html/index.html)。

::: note note
- 集成了呼叫组件 V2.0 版本的用户能和呼叫组件 V1.x 的用户进行通话。
- 请确保代码中全使用 V2.0 版本的接口或全使用 V1.x 版本的接口， V2.0 版本的接口和 V1.x 版本的接口请勿混用。
:::

**升级说明**

从 V1.8.2 版本升级到 V2.0.0 版本，不影响您继续使用 V1.8.2 版本的接口。详细的接口变更和升级说明请参见 [升级指南（V2）](https://doc.yunxin.163.com/nertccallkit/guide/jAxNTE0MDc?platform=iOS)。

**兼容版本**

- 适配 NIM V9.10.0 版本。
- 适配 NERTC SDK V4.6.50 版本。

## <span id="1.8.2 (2023-03-10)">1.8.2 (2023-03-10)</span>

**改进优化**

适配 IM UIKit，支持在 IM UIKit V9.4.0 及以上版本中集成呼叫组件。

**升级说明**

V1.8.0 版本可直接升级至 V1.8.2 版本。

**兼容版本**

- 适配 NIM V9.8.0 版本。
- 适配 NERTC SDK V4.6.29 版本。

## <span id="1.8.0 (2022-11-01)">1.8.0 (2022-11-01)</span>

**API 变更**

- `NERtcCallOptions` 接口中的是否同时初始化 RTC 的参数，从之前的 `shouldInitializeRtc`参数，替换为新的`globalInit`参数。
   ```objc
   /// 是否在初始化的时候初始化Rtc，默认为YES，设置为NO，主叫在呼叫时初始化，被叫在有呼叫到达的时候初始化
   @property(nonatomic, assign) BOOL globalInit;
   ```
-  `NERtcCallOptions`接口中新增 `joinRtcWhenCall` 参数，设置主叫在呼叫时是否加入 RTC 房间。
   ```objc
   /// 主叫是否在呼叫时加入rtc，默认为NO，在被叫接听时加入RTC 房间，不提前加入。如设置提前加入房间会带来通话费用的增加，同时提升首帧开画时间
   @property(nonatomic, assign) BOOL joinRtcWhenCall;                                   
   ```

**升级说明**

不可直接升级，从V1.6.5 版本升级至 V1.8.0 版本时，您需要在代码中对新增和变更的接口进行修改和适配，主要变更如下：

- 呼叫组件内部不再引用 NERTC，需要单独引用 NERTC。示例代码如下：
   ```
   #呼叫组件
   pod 'NERtcCallKit','1.8.0'
   #NERtcSDK
   pod 'NERtcSDK', '4.6.22', :subspecs => ['RtcBasic']
   ```
- 业务应用不再需要通过 `NERtcCallKitTokenHandler` 回调获取 RTC Token，呼叫组件内部已实现相关获取流程。
- `NERtcCallOptions` 接口中的是否同时初始化 RTC 的参数，删除了 `shouldInitializeRtc` 参数，替换为新的`globalInit`参数。

**兼容版本**

- 适配 NIM V9.6.4 版本。
- 适配 NERTC SDK V4.6.22 版本。

## <span id="1.6.1 (2022-08-26)">1.6.1 (2022-08-26)</span>

**新增特性**

- 支持音视频通话切换确认。
- `NERtcCallKitTokenHandler` 回调新增 `channelName` 参数。

**新增 API**

- 新增音视频切换确认，默认不开启确认。
   ```objc
   /// 音视频切换是否需要确认配置
   /// @param video 切换到视频是否需要确认
   /// @param audio 切换到音频是否需要确认
   - (void)enableSwitchCallTypeConfirmVideo:(BOOL)video audio:(BOOL)audio;
   ```

- 新增音视频切换回调，新增回调中有音视频切换指令类型，如果未开启音视频切换确认配置，可忽略第二个字段。
   ```objc
   /// 通话类型切换的回调（仅1对1呼叫有效）
   /// @param callType 切换后的类型
   /// @param state 切换应答类型:  邀请/同意/拒绝
   - (void)onCallTypeChange:(NERtcCallType)callType withState:(NERtcSwitchState)state;
   ```

** API 变更**

- 修改音视频切换接口参数，如果未开启音视频切换确认可以忽略第二个参数。
   ```objc
   /// 在通话过程中切换通话类型。非通话过程中调用无效。仅支持1对1通话。
   /// @param type 通话类型: 音频/视频
   /// @param state 切换应答类型:  邀请/同意/拒绝
   /// @param completion 回调
   /// @discussion
   /// 切换完成后，组件内部会将己端和对端调用-enableLocalVideo:，此时外部不建议再调用      -enableLocalVideo:，防止状态错乱.
   - (void)switchCallType:(NERtcCallType)type
               withState:(NERtcSwitchState)state
               completion:(nullable void (^)(NSError *_Nullable error))completion;
   ```
- 获取 Token 的 `NERtcCallKitTokenHandler` 回调增加 `channelName` 参数。
   ```objc
   // 定义示例
   typedef void (^NERtcCallKitTokenHandler)(uint64_t uid, NSString *channelName,
                                       void (^complete)(NSString *token, NSError *error));
   // 使用示例
   callkit.tokenHandler = ^(uint64_t uid, NSString *channelName, void (^complete)(NSString *token, NSError *error)){
   };                                    
   ```

**问题修复**

修复当移动端作为被叫时，概率出现 Web 端用户无法看到移动端用户的摄像头画面的问题。

**升级说明**

不可直接升级，从V1.5.7 版本升级至 V1.6.1 版本时，您需要在代码中对新增和变更的接口进行修改和适配，具体变更请参见如下新增 API 和 API 变更。

**兼容版本**

- 适配 NIM V9.2.5 版本。
- 适配 NERTC SDK V4.2.142 版本。

## <span id="1.5.7 (2022-07-19)">1.5.7 (2022-07-19)</span>

**新增特性**

- 支持自定义 `rtcUid`、`channelName`。
- 支持呼叫或接听时直接设置 `rtcToken`。

**新增 API**

- 支持自定义 `rtcUid`。
   ```objc
   /// 初始化，所有功能需要先初始化
   /// @param appKey 云信后台注册的appKey
   /// @param rtcUid  用户自定义rtc uid，如果不需要自定义传入 <= 0 任意整数(或者使用-
   /// (void)setupAppKey:(NSString *)appKey options:(nullable NERtcCallOptions *)options
   /// 初始化接口)，内部自动生成，如果初始化传入会优先使用外部传入
   - (void)setupAppKey:(NSString *)appKey
            withRtcUid:(uint64_t)rtcUid
            options:(nullable NERtcCallOptions *)options;
   ```

- 支持自定义 `channelName` 以及呼叫时传入 `rtc token`。
   ```objc
   /// 开始呼叫
   /// @param userID 呼叫的用户ID
   /// @param type 通话类型
   /// @param attachment 附件信息，透传到onInvited
   /// @param extra 全局抄送
   /// @param token  安全模式token，如果用户直接传入，不需要实现  tokenHandler  block回调
   /// @param channelName  自定义channelName，不传会默认生成
   /// @param completion 回调
   - (void)call:(NSString *)userID
         type:(NERtcCallType)type
         attachment:(nullable NSString *)attachment
         globalExtra:(nullable NSString *)extra
         withToken:(nullable NSString *)token
         channelName:(nullable NSString *)channelName
         completion:(nullable void (^)(NSError *_Nullable error))completion;            
   ```

**升级说明**

V1.5.5 版本可直接升级至 V1.5.7 版本。

**兼容版本**

- 适配 NIM V9.2.5 版本。
- 适配 NERTC SDK V4.2.142 版本。

## <span id="1.5.5 (2022-06-15)">1.5.5 (2022-06-15)</span>

**新增特性**

- 1 对 1 呼叫时，支持全局服务端抄送参数。
- 支持占线挂断。

**新增 API**
 
- 新增 `call` 接口。开始呼叫时，通过 `extra` 参数，设置呼叫时的全局抄送信息。
      ```
      /// 开始呼叫
      /// @param userID 呼叫的用户ID
      /// @param type 通话类型
      /// @param attachment 附件信息，透传到onInvited
      /// @param extra 扩展
      /// @param completion 回调
      - (void)call:(NSString *)userID
            type:(NERtcCallType)type
      attachment:(nullable NSString *)attachment
      globalExtra:(nullable NSString *)extra
      completion:(nullable void(^)(NSError * _Nullable error))completion;
      ```

- 新增 `rejectWithReason` 接口。通过 `reason` 参数控制挂断原因，实现占线挂断。
      ```
      /// 拒绝呼叫
      /// @param completion 回调
      /// @param reason  挂断原因
      - (void)rejectWithReason:(NSInteger)reason withCompletion:(nullable void(^)(NSError * _Nullable error))completion;
      ```

**升级说明**

V1.5.1 版本可直接升级至 V1.5.5 版本。

**兼容版本**

- 适配 NIM V8.5.5 版本。
- 适配 NERTC SDK V4.2.142 版本。

## 1.5.1 (2022-04-02)

**功能优化**

- 优化 App 同时使用呼叫组件和 RTC SDK 时部分 RTC 的回调无法触发的问题。
- 优化多人呼叫的静音逻辑。

**升级说明**

V1.5.0 版本可直接升级至 V1.5.1 版本。

**兼容版本**

- 适配 NIM V8.5.5 版本。
- 适配 NERTC SDK V4.2.120 版本。

## 1.5.0 (2021-12-23)

**问题修复**

修复与 Swift 混编的部分问题。

**升级说明**

V1.4.2 版本可直接升级至 V1.5.0 版本。

**兼容版本**

- 适配 NIM V8.5.5 版本。
- 适配 NERTC SDK V4.2.120 版本。

## 1.4.2 (2021-12-23)

**新增特性**

- 支持私有化配置。
- 支持呼叫前切换音视频。

**升级说明**

V1.4.0 版本可直接升级至 V1.4.2 版本。

**兼容版本**

- 适配 NIM V8.5.5 版本。
- 适配 NERTC SDK V4.2.120 版本。

## 1.4.0 (2021-09-28)

**新增特性**

- 添加呼叫通话前支持切换通话类型。
- 添加音频转视频功能。
- 增加通话中根据 `accId` 获取 `rtcUid` 或根据 `rtcUid` 获取 `accId`。
- 支持自定义呼叫推送配置。
- 支持用户通过呼叫组件的代理接收 `NERtcSDK` 回调。
- 修改组件展示 Demo，从即时通讯 Demo 更换为 1 对 1 Demo。

** API 更新**

- 添加被叫是否自动加入 `channel` 控制变量:

   ```objc
   @interface NERtcCallOptions : NSObject
   /// 被叫是否自动加入channel
   @property (nonatomic, assign) BOOL supportAutoJoinWhenCalled;
   @end
   ```

- 增加通话中根据 accId 获取 `rtcUid` 或根据 `rtcUid` 获取 accId:

   ```objc
   @interface NERtcCallKit : NSObject
   /// 根据uid 获取 accid
   /// @param uid 用户id
   /// @discussion 只有在通话中才能通过uid获取accid
   - (void)memberOfUid:(uint64_t)uid
         completion:(nullable void(^)(NIMSignalingMemberInfo * _Nullable info))completion;
   /// 根据uid 获取 accid
   /// @param accid  IM 用户id
   /// @discussion 只有在通话中才能通过accid获取获取uid
   - (void)memberOfAccid:(NSString *)accid
             completion:(nullable void(^)(NIMSignalingMemberInfo * _Nullable info))completion;
   @end
   ```

- 支持自定义呼叫推送配置:

   ```objc
   @interface NERtcCallKit : NSObject
   /// 推送配置定制化，修改config.pushTitle，config.pushContent来完成。需要的上下文内容在context对象中提供。
   @property (nonatomic, copy, nullable) NERtcCallKitPushConfigHandler pushConfigHandler。
   @end
   ```

- 支持用户通过呼叫组件的代理接收 `NERtcSDK` 回调:

   ```objc
   @interface NERtcCallKit : NSObject
   /**
     NERtcEngine 的回调接口，由用户提供
   */
   @property (nonatomic, weak) id<NERtcEngineDelegateEx> engineDelegate;
   @end
   ```

**升级说明**

V1.3.0 可直接升级至 V1.4.0。

**兼容版本**

- 适配 NIM V8.5.5 版本。
- 适配 NERTC SDK V4.2.112 版本。

## 1.3.0 (2021-06-24)

**新增特性**

- 添加 `channelName`，`channelId`，`uid`，`accid` 映射关系回调 `onJoinChannel`。
- 移动端添加 `muteLocalVideo` 接口以及 `onVideoMute` 回调。
- 移动端添加 `onAudioMute` 回调。
- 添加点对点通话类型埋点事件上报。
- `call`、`groupCall`、`groupInvite` 接口支持自定义扩展参数，被叫方在 `onInvited` 回调中解析对应参数。

**升级说明**

由 V1.2.1 升级至 V1.3.0 时，请注意以下变更：

- 添加视频采集控制接口：

   ```objc
   @interface NERtcCallKit : NSObject
   /// 开启或关闭视频采集
   /// @param muted YES：关闭，NO：开启
   /// @return 操作返回值，成功则返回 0
   - (int)muteLocalVideo:(BOOL)muted;
   @end
   ```

   接口调用会触发 `NERTCCallingDelegate.onVideoMuted()` 回调；

- 添加音频采集控制回调接口

   ```objc
   @protocol NERtcCallKitDelegate <NSObject>
      /// 音频采集变更回调
      /// @param muted 是否关闭采集
      /// @param userID 用户ID
      - (void)onAudioMuted:(BOOL)muted userID:(NSString *)userID;
      @end
   ```

- 添加 `onJoinChannel` 回调，此接口当用户加入音视频房间时触发此回调，用户可通过此回调获取用户 IM 的账号 Id 在此次通话中的 uid 以及音视频房间的房间 Id 以及名称。

   ```objc
   @protocol NERtcCallKitDelegate <NSObject>

   /// 自己加入成功的回调，通常用来上报、统计等
   /// @param event 回调参数
   - (void)onJoinChannel:(NERtcCallKitJoinChannelEvent *)event;
   @end
   @interface NERtcCallKitJoinChannelEvent : NSObject
   /// IM userID
   @property (nonatomic, copy) NSString *accid;
   /// 音视频用户id
   @property (nonatomic, assign) uint64_t uid;
   /// 音视频channelId
   @property (nonatomic, assign) uint64_t cid;
   /// 音视频channelName
   @property (nonatomic, copy) NSString *cname;
   @end
   ```

- 呼叫接口变更 `-[NERtcCallKit call]`、`-[NERtcCallKit groupCall]`、`-[NERtcCallKit groupInvite]` 均增加 `attachment` 参数，此参数用户传递自定义参数，在被叫方收到邀请通知时可解析出。

   ```objc
   /// 收到邀请的回调
   /// @param invitor 邀请方
   /// @param userIDs 房间中的被邀请的所有人（不包含邀请者）
   /// @param isFromGroup 是否是群组
   /// @param groupID 群组ID
   /// @param type 通话类型
   - (void)onInvited:(NSString *)invitor
             userIDs:(NSArray<NSString *> *)userIDs
         isFromGroup:(BOOL)isFromGroup
             groupID:(nullable NSString *)groupID
                type:(NERtcCallType)type
          attachment:(nullable NSString *)attachment; // 增加的attachment，建议用JSON字符串
   ```

**兼容版本**

- 适配 NIM V8.4.6 版本。
- 适配 NERTC SDK V4.0.7 版本。

## 1.2.1 (2021-06-08)

**问题修复**

- 修复服务端删除房间后，呼叫没有结束的问题。
- 修复服务端踢出某个成员后，该成员没有退出呼叫的问题。
- 修复主叫挂断与被叫接听同时进行时，产生的状态混乱。

**兼容版本**

- 适配 NIM V8.4.4 版本。
- 适配 NERTC SDK V4.0.7 版本。

## 1.2.0 (2021-05-14)

**新增特性**

- 添加多人通话，呼叫发起方可以在通话中途邀请其他用户。
- 增加日志，提供闭源 framework。
- 增加 groupInvite 功能。
- 状态机调整，允许接通后再拒绝。

**兼容版本**

- 适配 NIM V8.3.1 版本。
- 适配 NERTC SDK V4.0.3 版本。

## 1.1.0 (2021-04-25)

**新增特性**

首屏接通流程优化，提升接通速度；

**兼容版本**

- 适配 NIM V8.3.1 版本。
- 适配 NERTC SDK V4.0.3 版本。

**问题修复**

- 修复呼叫状态下，主叫突然断网，被叫方接受，主叫方网络恢复后没有收到对方 “接受” 的问题。
- 修复 IM 被踢后音视频房间未退出问题。

## 1.0.1

**兼容版本**

- 适配 NIM V8.1.5 版本。
- 适配 NERTC SDK V3.7.3.1 版本。

**问题修复**

- RTC SDK 升级 3731，修复一直 "操作频繁问题"。
- 自己断网离开后，重置房间状态，修复自己断网后不能再次呼叫问题。