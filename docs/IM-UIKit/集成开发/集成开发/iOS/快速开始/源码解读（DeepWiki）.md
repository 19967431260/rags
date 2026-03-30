本文介绍了基于 NIM SDK（网易即时通讯 SDK）构建的网易即时通讯 UIKit iOS 版，这是一个 UI 组件库。本文提供了系统架构、核心组件和设计原则的全面概述，帮助开发者快速构建功能丰富的即时通讯应用。

:::note note
本文是 [DeepWiki - netease-kit/nim-uikit-ios](https://deepwiki.com/netease-kit/nim-uikit-ios/1-overview) 项目概述的英译中翻译版本，为您介绍 IM Demo 开源项目。您可以前往 [DeepWiki - netease-kit/nim-uikit-ios](https://deepwiki.com/netease-kit/nim-uikit-ios/1-overview) 查看更多内容，如需实现相关功能，可调用 DeepSearch 参考实现。

<img alt="image.png" src="https://yx-web-nosdn.netease.im/common/b0c39121bf67f6f1c5b1a66287b5df15/image.png" style="width:80%;border: 0px solid #BFBFBF;">
:::

## 产品介绍

网易即时通讯 UIKit 是一套与 NIM SDK 配合使用的 UI 组件集合，为常见的即时通讯功能提供现成的用户界面。它包含了聊天、会话、通讯录、群组管理、搜索等组件。通过使用 IM UIKit，您可以快速实现功能完善的消息界面，而无需从零开始构建。

IM UIKit 的主要目标是通过处理 UI 展示和复杂业务逻辑，简化开发过程，让开发者能够专注于他们特定的应用需求。

## 主要优势

| 优势 | 说明 |
| ---- | ---- |
| 解耦的 UI 组件 | 不同组件可以独立运行，允许开发者仅选择应用所需的组件，减少不必要的依赖。 |
| 简洁的 UI 层 | 业务逻辑和 UI 层相互独立。UI 层仅专注于视图展示和事件处理，清晰的数据流处理使 UI 代码更加简洁易懂。 |
| 全面的业务逻辑 | 业务逻辑层提供完整的处理能力，将复杂的 SDK 交互简化为直观的接口。 |

## 系统架构

IM UIKit 采用 MVVM（Model-View-ViewModel）架构模式构建，将 UI 展示与业务逻辑分离。

### 架构图

```mermaid
graph TD
    subgraph a["UI层 (View)"]
        A1["NEChatUIKit"]
        A2["NEContactUIKit"]
        A3["NEConversationUIKit"]
        A4["NEQChatUIKit"]
        A5["NETeamUIKit"]
    end

    subgraph b["仓储层 (ViewModel)"]
        B1["NEChatKit"]
        B2["NEContactKit"]
        B3["NEQChatKit"]
    end

    subgraph c["核心层 (Model)"]
        C["NECoreKit"]
    end

    subgraph d["SDK层"]
        D["NIMSDK/V2NIM SDK"]
    end

    A1 --> B1
    A2 --> B2
    A3 --> B1
    A4 --> B3
    A5 --> B1

    B1 --> C
    B2 --> C
    B3 --> C

    C --> D

    %% 为节点定义样式
    classDef process fill:#cce5ff,stroke:#6699ff,stroke-width:1px;
    classDef decision fill:#ffffff,stroke:#ff4da6,stroke-width:1px;
    classDef endpoint fill:#e5ffe5,stroke:#009900,stroke-width:1px;

    class A1,A2,A3,A4,A5 process;
    class C,F,H,L decision;
    class B1,B2,B3 endpoint;

    %% 为子图定义样式
    classDef linkGroup fill:#f2f2f2,stroke:#f2f2f2,stroke-width:2px
    classDef statusGroup fill:#f3e5f5,stroke:#f3e5f5,stroke-width:2px
    classDef clientGroup fill:#ffe5ff,stroke:#ffe5ff,stroke-width:2px
    classDef resultGroup fill:#ffffcc,stroke:#ffffcc,stroke-width:2px

    %% 应用样式到子图
    class a,b,c,d linkGroup
```

该架构包含四个不同层次：

1. **UI 层**：包含处理用户界面展示和交互的视图控制器和 UI 组件
2. **仓储层**：实现处理业务逻辑并与核心层通信的 ViewModels
3. **核心层**：提供通用功能并抽象与 SDK 的交互
4. **SDK 层**：提供核心消息功能的底层网易 IM SDK

### 数据流

```mermaid
sequenceDiagram
    participant View as UIViewController/View
    participant ViewModel as ViewModel
    participant BusinessLogic as 业务逻辑层
    participant SDK as NIM SDK

    View->>ViewModel: 发送请求
    ViewModel->>BusinessLogic: 处理请求
    BusinessLogic->>SDK: 转发至 SDK
    SDK-->>BusinessLogic: 返回回调数据
    BusinessLogic-->>ViewModel: 处理数据
    ViewModel-->>View: 返回处理后的数据
    View->>View: 根据数据更新 UI
```

IM UIKit 中的数据流遵循以下步骤：

1. UI 层的 View/ViewController 向响应层的 ViewModel 发送请求
2. ViewModel 通过业务逻辑层将请求转发给 NIM SDK
3. NIM SDK 处理请求并返回回调数据
4. 回调数据通过业务逻辑层和响应层流回 View/ViewController
5. View 根据数据中的标识符确定适当的 UI 表示

有关架构的更详细信息，请参考 [架构](https://deepwiki.com/netease-kit/nim-uikit-ios/2-architecture)。

## 核心组件

IM UIKit 由几个专业的 UI 组件库组成，每个组件库在消息应用中都有特定用途：

```mermaid
graph TD
    A["网易即时通讯 UIKit"] --> B["NEChatUIKit"]
    A --> C["NEConversationUIKit"]
    A --> D["NEContactUIKit"]
    A --> E["NETeamUIKit"]
    A --> F["NEQChatUIKit"]

    B["NEChatUIKit"] --> B1["聊天界面"]
    B1 --> B1a["消息单元格"]
    B1 --> B1b["输入组件"]
    B1 --> B1c["消息操作"]

    C["NEConversationUIKit"] --> C1["会话列表"]
    C1 --> C1a["最近会话"]
    C1 --> C1b["会话搜索"]

    D["NEContactUIKit"] --> D1["通讯录管理"]
    D1 --> D1a["通讯录列表"]
    D1 --> D1b["好友操作"]

    E["NETeamUIKit"] --> E1["群组管理"]
    E1 --> E1a["群组创建/设置"]
    E1 --> E1b["成员管理"]

    F["NEQChatUIKit"] --> F1["圈组功能"]

    %% 为节点定义样式
    classDef default fill:#cce5ff,stroke:#6699ff,stroke-width:1px;
```

- **NEChatUIKit**：提供聊天界面的 UI 组件，包括消息单元格、输入视图和消息操作菜单
- **NEConversationUIKit**：处理会话列表界面，包含最近聊天和搜索功能
- **NEContactUIKit**：管理通讯录列表显示和好友操作
- **NETeamUIKit**：提供群组创建、设置和成员管理界面
- **NEQChatUIKit**：实现社区式交互的圈组功能

这些组件与其对应的仓储层模块（NEChatKit、NEContactKit 等）交互以处理业务逻辑。

有关各个组件的详细信息，请参考 [主要 UI 组件](https://deepwiki.com/netease-kit/nim-uikit-ios/4-main-ui-components)。

## 快速开始

要在您的 iOS 应用中开始使用网易即时通讯 UIKit：

1. 使用 CocoaPods 安装所需组件
2. 使用您的应用程序密钥初始化 IM UIKit
3. 在应用程序流程中实现必要的 UI 控制器

有关详细集成步骤，请参考 [快速开始](https://deepwiki.com/netease-kit/nim-uikit-ios/3-getting-started) 和 [安装](https://deepwiki.com/netease-kit/nim-uikit-ios/3.1-installation)。

## 界面预览

IM UIKit 为消息应用程序提供现代、简洁的界面，支持各种消息类型、会话管理和社交功能。这些 UI 组件可以自定义以匹配您应用程序的设计。

以下是 IM UIKit 提供的一些关键界面：

| 组件 | 主要功能 |
| ---- | ---- |
| 聊天界面 | 文本消息、媒体共享、文件传输、表情支持 |
| 会话列表 | 最近聊天、未读指示器、最后消息预览 |
| 通讯录 | 好友管理、用户资料、搜索功能 |
| 群组管理 | 群创建、成员管理、设置 |

有关实现示例，请参考 [实现示例](https://deepwiki.com/netease-kit/nim-uikit-ios/8-implementation-examples)。

## 自定义选项

IM UIKit 提供广泛的自定义选项，包括：

- 在 UI 风格之间切换（基础版和通用版）。
- 创建自定义消息单元格、通讯录单元格和会话单元格。
- 为各种事件实现自定义行为。
- 支持多语言本地化。

有关自定义的更多信息，请参考 [自定义](https://deepwiki.com/netease-kit/nim-uikit-ios/6-customization)。