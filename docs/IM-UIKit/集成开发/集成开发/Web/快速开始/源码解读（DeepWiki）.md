nim-uikit-web 仓库提供了一套完整的 UI 工具包，用于在 Web 应用中集成即时通讯功能。该工具包基于网易即时通讯(NIM) SDK 构建，提供预制组件，简化会话、消息界面和通讯录管理等聊天功能的实现。该工具包同时支持 React 和 Vue 框架，使开发者能够快速部署功能齐全的消息界面，而无需从零开始构建 UI 组件。

本文介绍了 IM UIKit 的高级架构、核心组件和主要概念。有关特定框架的集成详情，请参考 [React 集成](https://deepwiki.com/netease-kit/nim-uikit-web/2.1-react-integration) 和 [Vue 集成](https://deepwiki.com/netease-kit/nim-uikit-web/2.2-vue-integration)。

:::note note
本文是 [DeepWiki - netease-kit/nim-uikit-web](https://deepwiki.com/netease-kit/nim-uikit-web/1-overview) 项目概述的英译中翻译版本，为您介绍 IM Demo 源码项目。您可以前往 [DeepWiki - netease-kit/nim-uikit-web](https://deepwiki.com/netease-kit/nim-uikit-web/1-overview) 查看更多内容，如需实现相关功能，可调用 DeepSearch 参考实现。

<img alt="image.png" src="https://yx-web-nosdn.netease.im/common/b0c39121bf67f6f1c5b1a66287b5df15/image.png" style="width:80%;border: 0px solid #BFBFBF;">
:::

## 主要特性

- **跨框架支持**：兼容 React 和 Vue 框架
- **完整的消息 UI**：为所有核心消息功能提供预制组件
- **状态管理**：通过 MobX stores 实现集中状态处理
- **聊天类型**：支持一对一(P2P)和团队/群组聊天
- **通讯录管理**：好友和群组管理功能
- **高级消息功能**：包括消息转发、已读回执和@提及功能
- **自定义选项**：灵活的样式和行为配置

## 系统架构

以下图表展示了 IM UIKit 的高级架构：

```mermaid
graph TD
    subgraph 1["应用层"]
        ReactApp["React 应用"]
        VueApp["Vue 应用"]
    end

    subgraph 2["UIKit 层"]
        IMUIKit["IMUIKit 类"]
        CoreComponents["核心 UI 组件"]
    end

    subgraph 3["状态层"]
        RootStore["RootStore"]
        subgraph 5["Store 模块"]
            ConversationStore["会话 Store"]
            MessageStore["消息 Store"]
            UserStore["用户 Store"]
            TeamStore["团队 Store"]
            RelationStore["关系 Store"]
            UIStore["UI Store"]
        end
    end

    subgraph 4["SDK 层"]
        V2NIM["V2NIM (nim-web-sdk-ng)"]
    end

    ReactApp -->|"初始化"| IMUIKit
    VueApp -->|"初始化"| IMUIKit
    IMUIKit -->|"渲染"| CoreComponents
    IMUIKit -->|"创建"| RootStore
    RootStore -->|"包含"| ConversationStore & MessageStore & UserStore & TeamStore & RelationStore & UIStore
    ConversationStore & MessageStore & UserStore & TeamStore & RelationStore -->|"与之交互"| V2NIM


    %% 为子图定义样式
    classDef linkGroup fill:#f2f2f2,stroke:#f2f2f2,stroke-width:2px
    classDef statusGroup fill:#cce5ff,stroke:#ffe5ff,stroke-width:2px

    %% 应用样式到子图
    class 1,2,3,4,5 linkGroup
    class 5 statusGroup

```

该架构由四个主要层次组成：

1. **应用层**：集成 UIKit 的 React 或 Vue 宿主应用
2. **UIKit 层**：包含核心 UI 组件的主要接口层
3. **状态层**：管理应用状态的基于 MobX 的存储
4. **SDK 层**：处理核心消息功能的 NIM SDK

## 组件组织

UIKit 将其组件组织为功能模块，如下图所示：

```mermaid
graph TD
    subgraph 1["IMUIKit"]
        Provider["IMUIKit 提供者"]

        subgraph 2["功能模块"]
            ConversationModule["会话模块"]
            ChatModule["聊天模块"]
            ContactModule["通讯录模块"]
        end

        subgraph 3["通用组件"]
            CommonUI["UI 元素"]
        end
    end

    Provider -->|"为以下提供上下文"| ConversationModule & ChatModule & ContactModule
    ConversationModule & ChatModule & ContactModule -->|"使用"| CommonUI

    subgraph 4["会话组件"]
        ConversationList["会话列表"]
        ConversationItem["会话项"]
    end

    subgraph 5["聊天组件"]
        P2PChat["一对一聊天"]
        TeamChat["团队聊天"]
        MessageInput["消息输入"]
        MessageForward["消息转发"]
    end

    subgraph 6["通讯录组件"]
        FriendList["好友列表"]
        GroupList["群组列表"]
        UserProfile["用户资料"]
    end

    ConversationModule -->|"包含"| ConversationList & ConversationItem
    ChatModule -->|"包含"| P2PChat & TeamChat & MessageInput & MessageForward
    ContactModule -->|"包含"| FriendList & GroupList & UserProfile


    %% 为子图定义样式
    classDef linkGroup fill:#f2f2f2,stroke:#f2f2f2,stroke-width:2px
    classDef statusGroup fill:#ffe5ff,stroke:#ffe5ff,stroke-width:2px

    %% 应用样式到子图
    class 1,2,3,4,5,6 linkGroup
```

主要组件组包括：

1. **会话组件**：显示和管理用户会话
2. **聊天组件**：处理一对一和团队聊天
3. **通讯录组件**：管理好友和群组
4. **通用组件**：整个工具包中使用的共享 UI 元素

## 集成流程

以下时序图展示了应用如何集成并与 IM UIKit 交互：

```mermaid
sequenceDiagram
    participant App as 应用
    participant UIKit as IMUIKit
    participant NIM as V2NIM SDK
    participant Server as IM 服务器

    App->>NIM: 使用 appkey、账号、token 初始化 SDK
    NIM->>Server: 登录 IM 服务
    App->>UIKit: 使用 NIM 和选项创建 UIKit 实例
    UIKit->>UIKit: 初始化存储结构
    UIKit->>NIM: 注册事件监听器
    App->>UIKit: 渲染 UIKit 组件
    UIKit->>NIM: 获取初始数据（会话、通讯录）
    NIM->>Server: API 请求
    Server-->>NIM: 数据响应
    NIM-->>UIKit: 用数据更新存储
    UIKit-->>App: 使用数据渲染 UI

    Note over App,Server: 持续通信

    Server->>NIM: 新消息通知
    NIM->>UIKit: 更新消息存储
    UIKit-->>App: 更新 UI 显示新消息
```

该图展示了应用如何初始化 SDK、创建 UIKit 实例并渲染组件。它还说明了接收新消息的数据流。

## 核心配置选项

IM UIKit 支持多种配置选项来自定义其行为：

| 选项 | 说明 | 默认值 |
| ---- | ---- | ---- |
| `addFriendNeedVerify` | 是否需要验证才能添加好友 | `true` |
| `teamAgreeMode` | 处理团队邀请的模式 | `NO_AUTH` |
| `p2pMsgReceiptVisible` | 是否显示 P2P 消息的已读回执 | `false` |
| `teamMsgReceiptVisible` | 是否显示团队消息的已读回执 | `false` |
| `needMention` | 是否启用@提及功能 | `true` |
| `loginStateVisible` | 是否显示在线/离线状态 | `true` |
| `allowTransferTeamOwner` | 是否允许转让团队所有权 | `true` |
| `enableV2CloudConversation` | 是否启用云端会话 | `false` |

这些选项可以在初始化 UIKit 时提供，以根据应用需求自定义其功能。

## 入门指南

要开始使用 IM UIKit，您需要：

1. 有效的网易 IM AppKey
2. 用户账号和令牌凭证
3. React 或 Vue 开发环境

基本实现包括：

1. 安装适合您框架的软件包
2. 使用您的凭证初始化 NIM SDK
3. 使用 SDK 和选项创建 IMUIKit 实例
4. 在您的应用中渲染 UIKit 组件

有关详细的设置说明，请参考 [入门](https://deepwiki.com/netease-kit/nim-uikit-web/2-getting-started) 页面，以及特定框架的指南，如 [React 集成](https://deepwiki.com/netease-kit/nim-uikit-web/2.1-react-integration) 和 [Vue 集成](https://deepwiki.com/netease-kit/nim-uikit-web/2.2-vue-integration)。

## 与 NIM SDK 的关系

IM UIKit 基于 NIM SDK (nim-web-sdk-ng) 构建，如下图所示：

```mermaid
graph LR
    subgraph 1["应用代码"]
        App["您的应用"]
    end

    subgraph 2["UIKit 层"]
        IMUIKit["@xkit-yx/im-kit-ui"]
        ReactComponents["React 组件"]
        VueComponents["Vue 组件"]
        MobXStores["MobX 存储"]
    end

    subgraph 3["SDK 层"]
        NIMSDK["nim-web-sdk-ng (V2NIM)"]
        subgraph 4["SDK 服务"]
            LoginService["V2NIM 登录服务"]
            MsgService["V2NIM 消息服务"]
            ConversationService["V2NIM 会话服务"]
            TeamService["V2NIM 团队服务"]
            UserService["V2NIM 用户服务"]
        end
    end

    App -->|"集成"| IMUIKit
    IMUIKit -->|"包含"| ReactComponents & VueComponents & MobXStores
    IMUIKit -->|"使用"| NIMSDK
    NIMSDK -->|"提供"| LoginService & MsgService & ConversationService & TeamService & UserService

    %% 为子图定义样式
    classDef linkGroup fill:#f2f2f2,stroke:#f2f2f2,stroke-width:2px
    classDef statusGroup fill:#ffe5ff,stroke:#ffe5ff,stroke-width:2px

    %% 应用样式到子图
    class 1,2,3,4,5,6 linkGroup
```

UIKit 通过以下方式抽象 NIM SDK 的复杂性：

1. 提供与 SDK 服务交互的即用 UI 组件
2. 通过与 SDK 数据同步的 MobX 存储管理状态
3. 处理来自 SDK 的事件监听器和数据更新
4. 提供常见消息操作的高级 API

这种分层方法允许开发者实现功能完备的消息功能，而无需直接与低级 SDK API 交互。

## 下一步

有关 IM UIKit 特定方面的更详细信息，请参考：

- [关键概念和术语](https://deepwiki.com/netease-kit/nim-uikit-web/1.1-key-concepts-and-terminology) - 重要术语的定义
- [系统架构](https://deepwiki.com/netease-kit/nim-uikit-web/1.2-system-architecture) - 深入了解技术架构
- [核心组件](https://deepwiki.com/netease-kit/nim-uikit-web/3-core-components) - 主要组件类别的详细信息
- [状态管理](https://deepwiki.com/netease-kit/nim-uikit-web/4-state-management) - 有关如何使用 MobX 处理状态的信息