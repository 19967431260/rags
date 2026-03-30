网易云信即时通讯 SDK（NetEase Instant Messaging SDK，简称 NIM SDK）为 HarmonyOS 项目提供完善的即时通信功能开发能力。NIM HarmonyOS Atomic Service SDK 屏蔽其内部复杂细节，对外提供较为简洁的 API，方便您快速集成即时通信功能。

::: note note 
本文主要介绍底层 HarmonyOS Atomic Service SDK 的集成。
:::

## 功能模块

IM HarmonyOS 元服务 SDK 提供的功能包括登录、会话、消息、群组、用户、好友、自定义通知、设置、信令等功能。

## 开发环境要求

- DevEco Studio 6.0.2 Release 及以上。
- HarmonyOS SDK API 18 及以上。
- 运行环境 HarnomyOS NEXT 5.1.0 以上。

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
            "@nimsdk/atomic": "file:../XXX/libs/nimsdk.har"
        }
      ...

    }
    ```

    - 云端依赖 （以10.9.76 版本为例）：

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
            "@nimsdk/atomic": "10.9.76"
        }
      ...
    }
    ```

4. 单击 **File > Sync and Refresh Project** 按钮，直到同步完成。

5. 在工程 **build-profile.json5** 中设置支持字节码 HAR 包。

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
    const nim: NIMInterface = NIMAtomicSdk.newInstance(context, initializeOptions, serviceOptions)

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