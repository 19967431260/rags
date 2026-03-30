本文为您展示通过 NEMeetingKit 实现音视频会议的相关步骤，帮助您在业务中实现创建会议、预约会议、查询会议信息、遥控器服务等在线会议场景下的相关能力。

## 前提条件

在根据本文操作前，请确保您已在网易云信控制台上，完成以下设置：

1. 在控制台创建至少一个应用。若无应用，请参考 <a href="https://doc.yunxin.163.com/console/concept/TIzMDE4NTA">创建应用并获取 AppKey</a>。
2. 开通 **视频会议** 解决方案。具体步骤可参考 [方案开通](https://doc.yunxin.163.com/meeting/concept/TkzMjExNDY?platform=client)。

## 开发环境

在客户端实现音视频会议功能之前，请您准备以下开发环境：

:::::: div linked-codes
::: code macOS

| 环境类型 | 具体要求 |
| ---- | ---- |
| OS | macOS 11.0 以上 |
| Node.js | 18.19 以上 |
| Electron | 24.8.3 |

:::
::: code Windows

| 环境类型 | 具体要求 |
| ---- | ---- |
| OS | Windows 10 以上 |
| Node.js | 18.19 以上 |
| Electron | 24.8.3 |

:::
::::::

## 获取 SDK

- NPM 方式引入：

    ```NPM
    $ npm install --save nemeeting-electron-sdk
    ```

- Yarn 方式引入：

    ```Yarn
    $ yarn add nemeeting-electron-sdk
    ```

- PNPM 方式引入：

    ```PNPM
    $ pnpm add nemeeting-electron-sdk
    ```

## 导入 SDK

:::::: div linked-codes
::: code TypeScript

```TypeScript
// 需在主进程引入
import NEMeetingKit from 'nemeeting-electron-sdk'
```
:::
::: code JavaScript

```TypeScript
// 需在主进程引入
const { default: NEMeetingKit } = require('nemeeting-electron-sdk')
```
:::
::::::

## 下一步

调用网易会议组件接口 [实现基础功能](https://doc.yunxin.163.com/meeting/guide/zYxOTE1MzA?platform=electron)，例如调用初始化接口，并传入您在网易云信控制台上创建应用时获取的密钥（AppKey）。