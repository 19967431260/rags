本文介绍在网易云信即时通讯 IM UIKit（简称 NIM UIKit）层因为上层业务需要，在 NIM UIKit 层提供的接口。NIM UIKit 层接口位于 `ChatKit` 模块中，该模块提供 UI 层使用到的会话、通讯录、群、消息等相关接口。

在 `ChatKit` 层中接口主要分布在如下类中：

| 类名 | 说明 |
| --- | --- |
| [`IMKitConfigCenter`](https://doc.yunxin.163.com/messaging-uikit/guide/TYyODI3MjE?platform=iOS#IMKitConfigCenter) | NIM UIKit 配置中心，用于配置 NIM UIKit 相关功能开关。 |
| [`AIRepo`](https://doc.yunxin.163.com/messaging-uikit/client-apis/jIxNzI4MzM?platform=iOS) | 包含 AI 数字人相关接口，提供 AI 数字人获取和变更监听方法等。 |
| [`ChatRepo`](https://doc.yunxin.163.com/messaging-uikit/client-apis/jM0MTAxMjg?platform=iOS) | 包含消息相关接口类，提供消息发送、撤回、接受监听等。 |
| [`ContactRepo`](https://doc.yunxin.163.com/messaging-uikit/client-apis/zM1NTI4MTc?platform=iOS) | 包含通讯录相关接口，好友、黑名单相关接口等。 |
| [`ConversationRepo`](https://doc.yunxin.163.com/messaging-uikit/client-apis/Tc2MTYxNDA?platform=iOS) | 包含云端会话相关业务逻辑接口。该类根据 UI 层业务逻辑，提供会话相关的数据获取、设置等操作，通过 IM SDK [V2NIMConversationService](https://doc.yunxin.163.com/messaging2/references/iOS/doxygen/Latest/zh/d4/d16/protocol_v2_n_i_m_conversation_service-p.html) 提供的接口实现。 |
| [`LocalConversationRepo`](https://doc.yunxin.163.com/messaging-uikit/client-apis/Tc2MTYxNDA?platform=iOS) | 包含本地会话相关业务逻辑接口。该类根据 UI 层业务逻辑，提供会话相关的数据获取、设置等操作，通过 IM SDK [V2NIMLocalConversationService](https://doc.yunxin.163.com/messaging2/references/iOS/doxygen/Latest/zh/d4/d16/protocol_v2_n_i_m_conversation_service-p.html) 提供的接口实现。 |
| [`ResourceRepo`](https://doc.yunxin.163.com/messaging-uikit/client-apis/TA5NjQ3ODE?platform=iOS) | 包含资源相关业务逻辑接口。 |
| [`SettingRepo`](https://doc.yunxin.163.com/messaging-uikit/client-apis/DQ3MzY5OTc?platform=iOS) | 包含设置相关业务逻辑接口。 |
| [`TeamRepo`](https://doc.yunxin.163.com/messaging-uikit/client-apis/TA1MDQ4MTk?platform=iOS) | 包含群组相关接口。为 [NETeamUIKit](https://github.com/netease-kit/nim-uikit-ios/tree/master/NETeamUIKit) 模块中业务提供群组相关接口，根据业务需求对 SDK 接口进行组合封装。 |
| `SubscribeRepo` | 包含用户状态订阅管理接口。该类根据 UI 层业务逻辑，提供状态管理相关的发布、查询、订阅事件等接口，通过 IM SDK [V2NIMSubscriptionService](https://doc.yunxin.163.com/messaging2/references/iOS/doxygen/Latest/zh/d3/d20/protocol_n_i_m_event_subscribe_manager-p.html) 提供的接口实现。 |


<!-- ## IMKitConfigCenter

提供 NIM UIKit 功能配置开关，可以对已实现的功能进行全局控制。如是否使用@功能、PIN 功能等。

| 参数 | 类型 | 说明 | 默认 |
| --- | --- | --- | --- |
| `enableTeam` | [Bool] | 是否使用群功能。如果设置为 false，将不会出现跟群相关功能。 |  true | 
| `enableAtMessage` | [Bool] | 是否使用@功能。 |  true | 
| `enableCollectionMessage` | [Bool] | 是否使用消息收藏功能。 |  true | 
| `enablePinMessage` | [Bool] | 是否使用 Pin 消息功能。 |  true | 
| `enableTopMessage` | [Bool] | 是否使用消息置顶功能。 |  true | 
| `enableOnlineStatus` | [Bool] | 是否开启订阅在线状态。 |  true | 
| `enableOnlyFriendCall` | [Bool] | 是否只能和好友通话。 | true | 
| `enableDismissTeamDeleteConversation` | [Bool] | 是否解散群或者被踢出群聊后删除会话。 |  true | 
| `enableAIUser` | [Bool] | 是否使用 AI 数字人。 |  true | 
| `enableAIChatHelper` | [Bool] | 是否开启 AI 聊天助手。 |  true | 
| `enableRichTextMessage` | [Bool] | 是否使用换行消息功能。 |  true | 
| `enableAIStream` | [Bool] | 是否开启流式消息。 |  true | 


<!--
| `enableTypingStatus` | [Bool] | 是否支持正在输入状态功能，默认 true。 | 

功能设置需要在 NIM UIKit 功能或者页面加载之前配置，推荐在 `AppDelegate` 的 `application(_: didFinishLaunchingWithOptions:)` 方法中设置 NIM UIKit 的配置。以 `enableAIUser` 为例，设置方法如下所示：

:::::: div linked-codes
::: code Swift
```Swift
    IMKitConfigCenter.shared.enableAIUser = true
```
:::
::: code Objective-C
```Objective-C
    IMKitConfigCenter.shared.enableAIUser = YES;
```
:::
:::::: -->