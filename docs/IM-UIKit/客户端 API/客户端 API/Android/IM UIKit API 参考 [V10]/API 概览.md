本文介绍在网易云信即时通讯 IM UIKit（简称 NIM UIKit）层因为上层业务需要，在 NIM UIKit 层提供的接口。NIM UIKit 层接口位于 `ChatKit` 模块中，该模块提供 UI 层使用到的会话、通讯录、群、消息等相关接口。

在 `ChatKit` 层中接口主要分布在如下类中：

<style>
table th:first-of-type {width: 30%;}
</style>

| 类名 | 概述 |
| --- | --- |
| [`IMKitConfigCenter`](https://doc.yunxin.163.com/messaging-uikit/guide/zg2NjgzMjU?platform=android#IMKitConfigCenter) | 提供 NIM UIKit 功能配置开关，可以对已实现的功能进行全局控制。如是否使用@功能、PIN 功能等。 |
| [`AIRepo`](https://doc.yunxin.163.com/messaging-uikit/client-apis/Tc2MjM1NDk?platform=android) | AI 数字人接口类，提供 AI 数字人获取和变更监听方法等。 |
| [`ChatRepo`](https://doc.yunxin.163.com/messaging-uikit/client-apis/jg0MTE5NTk?platform=android) | 消息相关接口类，提供消息发送、撤回、接受监听等。 |
| [`ContactRepo`](https://doc.yunxin.163.com/messaging-uikit/client-apis/TM0NjU0ODY?platform=android) | 通讯录相关接口，好友、黑名单相关接口等。 |
| [`ConversationRepo`](https://doc.yunxin.163.com/messaging-uikit/client-apis/DExNjE2NDA?platform=android) | 会话相关业务逻辑接口。该类根据 UI 层业务逻辑，提供会话相关的数据获取、设置等操作，通过 IM SDK [V2NIMConversationService](https://doc.yunxin.163.com/messaging2/references/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1v2_1_1conversation_1_1_v2_n_i_m_conversation_service.html) 提供的接口实现。 |
| [`ResourceRepo`](https://doc.yunxin.163.com/messaging-uikit/client-apis/jQ3NjYzODA?platform=android) | 资源相关业务逻辑接口。 |
| `SearchRepo` | 好友和群组相关搜索接口。UIKit 业务实现搜索功能。 |
| [`SettingRepo`](https://doc.yunxin.163.com/messaging-uikit/client-apis/jk2NzA2NjI?platform=android) | 设置相关业务逻辑接口。 |
| [`TeamRepo`](https://doc.yunxin.163.com/messaging-uikit/client-apis/zg0MzA0Njc?platform=android) | 群组相关接口。为 [teamkit-ui](https://github.com/netease-kit/nim-uikit-android/tree/master/teamkit-ui) 模块中业务提供群组相关接口，根据业务需求对 SDK 接口进行组合封装。 |
| [`MiscRepo`](https://doc.yunxin.163.com/messaging-uikit/client-apis/DI1NzA4MDM?platform=android) | SDK 杂项业务逻辑接口。该类根据 UI 层业务逻辑，提供 SDK 杂项相关的数据获取、设置等操作，通过 IM SDK [MiscService](https://doc.yunxin.163.com/messaging2/references/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1misc_1_1_misc_service.html) 提供的接口实现。 |

<!-- ## IMKitConfigCenter

提供 NIM UIKit 功能配置开关，可以对已实现的功能进行全局控制。如是否使用@功能、PIN 功能等。更多详情，请参考《全局配置》[IMKitConfigCenter](https://doc.yunxin.163.com/messaging-uikit/guide/zg2NjgzMjU?platform=android#IMKitConfigCenter) 章节。 -->