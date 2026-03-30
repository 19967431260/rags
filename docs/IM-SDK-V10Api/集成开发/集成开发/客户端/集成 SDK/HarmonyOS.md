网易云信即时通讯 SDK（NetEase Instant Messaging SDK，简称 NIM SDK）为 HarmonyOS 项目提供完善的即时通信功能开发能力。NIM HarmonyOS SDK 屏蔽其内部复杂细节，对外提供较为简洁的 API，方便您快速集成即时通信功能。

::: note note 
本文主要介绍底层 HarmonyOS SDK 的集成，若您需要集成对应的 UI 组件，请参考 [集成 HarmonyOS UIKit](https://doc.yunxin.163.com/messaging-uikit/guide/TU4MTkzNTk?platform=harmonyos)。
:::

## 功能模块

IM HarmonyOS SDK 提供的功能包括登录、会话、消息、群组、用户、好友、存储服务、推送、自定义通知、设置、信令、聊天室、圈组等功能。

对应上述功能提供业务组件 har 包，包括 connversation、conversationgroup、localconversation、message、team、user、friend、signalling、chatroom<!-- 、qchat（开发中，暂不提供） -->。模块架构如下图所示：

<img alt="NIMSDK 架构图.png" src="https://yx-web-nosdn.netease.im/common/b6ee237d91c173370db8fa3a5858ae11/NIMSDK架构图.png" style="width:65%;border: 1px solid #BFBFBF;">

## 开发环境要求

- DevEco Studio NEXT Developer Beta1（5.0.3.300） 及以上。
- HarmonyOS SDK API 12 及以上。
- 运行环境 HarnomyOS NEXT 2.1.2.5 (Canary1) 以上。

## 集成 SDK

1. 通过 [官网](https://doc.yunxin.163.com/messaging2/resource?platform=harmonyos) 下载 `.har` 形式的 NIM SDK 产物。

2. 将 SDK 文件拷贝到 HarmonyOS 工程，例如放至 `entry` 模块下的 `libs` 目录。

3. 修改模块目录的 `oh-package.json5` 文件，在 `dependencies` 节点增加依赖声明。

4. 执行 `ohpm install` 命令安装依赖。

    - 本地依赖：

    ```JSON
    {
        "name": "entry",
        "version": "1.0.0",
        "description": "Please describe the basic information.",
        "main": "",
        "author": "",
        "license": "",

        ...

        "dependencies": {
            <!-- 业务模版 har 包，可以按需添加 -->
            "@nimsdk/conversation": "file:../../libs/conversation.har",
            <!-- 业务模版 localconversation 与 conversation 和 conversationgroup 为互斥关系，不可以同时使用-->
            "@nimsdk/localconversation": "file:../../libs/localconversation.har",
            <!-- 业务模版 localconversation 与 conversation 和 conversationgroup 为互斥关系，不可以同时使用-->
            "@nimsdk/message": "file:../../libs/message.har",
            "@nimsdk/team": "file:../../libs/team.har",
            "@nimsdk/user": "file:../../libs/user.har",
            "@nimsdk/friend": "file:../../libs/friend.har",
            "@nimsdk/signalling": "file:../../libs/signalling.har",
            <!-- HarmonyOS IMSDK 基础业务模块，必须添加 -->
            "@nimsdk/nim": "file:../../libs/nim.har",
            "@nimsdk/base": "file:../../libs/base.har",
            <!-- HarmonyOS IMSDK 检索模块，如需要使用本地检索功能，必须添加 -->
            "@nimsdk/search": "file:../../libs/search.har"
        }
      ...

    }
    ```

    - 云端依赖 （以10.7.0 版本为例）：

    ```JSON
    {
        "name": "entry",
        "version": "1.0.0",
        "description": "Please describe the basic information.",
        "main": "",
        "author": "",
        "license": "",

        ...

        "dependencies": {
            <!-- 业务模版 har 包，可以按需添加 -->
            "@nimsdk/conversation": "10.7.0",
            <!-- 业务模版 localconversation 与 conversation 和 conversationgroup 为互斥关系，不可以同时使用-->
            "@nimsdk/localconversation": "10.7.0",
            <!-- 业务模版 localconversation 与 conversation 和 conversationgroup 为互斥关系，不可以同时使用-->
            "@nimsdk/message": "10.7.0",
            "@nimsdk/team": "10.7.0",
            "@nimsdk/user": "10.7.0",
            "@nimsdk/friend": "10.7.0",
            "@nimsdk/signalling": "10.7.0",
            <!-- HarmonyOS IMSDK 基础业务模块，必须添加 -->
            "@nimsdk/nim": "10.7.0",
            "@nimsdk/base": "10.7.0"
        }
      ...
    }
    ```

    示例代码中的插件关系如下（实线箭头表示强引用关系，虚线箭头表示弱引用关系）：

    <img alt="插件关系图.png" src="https://yx-web-nosdn.netease.im/common/a58666a276819e082c7d695417ae38ff/插件关系图.png" style="width:70%;border: 1px solid #BFBFBF;">

4. 单击 **File > Sync and Refresh Project** 按钮，直到同步完成。

5. 在工程 **build-profile.json5** 中设置支持字节码 HAR 包。

    ::: note notice
    V10.9.10 及以上版本都必须引入。
    :::

    ```JSON
    {
      "app": {
        "products": [
          {
            "buildOption": {
              "strictMode": {
                "useNormalizedOHMUrl": true
              }
            }
          }
        ]
      }
    }
    ```

## 调用 API

集成 NIM SDK 后，所有 SDK 能力均通过 NIM SDK 实例提供的 `service` 进行调用，例如：

- 通过 `loginService` 进行登录：

    ```TypeScript
    const nim: NIMInterface = NIMSdk.newInstance(context, initializeOptions, serviceOptions)

    nim.loginService.on('onLoginStatus', loginStatus => {
    console.log('收到 V2NIMLoginService 模块的 onLoginStatus 事件', loginStatus);
    })
    await nim.loginService.login("YOUR_ACCOUNT", "YOUR_TOKEN")
    ```

- 通过 `messageService` 进行消息发送：

    ```TypeScript
    const message = nim.messageCreator.createTextMessage("hello")
    nim.messageService?.sendMessage(message, 'YOUR_ACCOUNT|1|RECEIVER_ACCOUNT')
    ```

## API 参考

您可以参考 [API 概览](https://doc.yunxin.163.com/messaging2/client-apis/DY2Mjk0MjU?platform=client)，查看并了解 NIM SDK API。

## 下一步

完成 SDK 集成后，您可以尝试 [初始化](https://doc.yunxin.163.com/messaging2/guide/TY4MTAxNzE?platform=client)。