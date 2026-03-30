网易云信在 Github 上提供开源的即时通讯示例（IM Demo）源码。您可参考 Demo 源码（[Gitee 仓库](https://gitee.com/growth-ease/nim-uikit-harmony) 或 [GitHub 仓库](https://github.com/netease-kit/nim-uikit-harmony) ），在您的鸿蒙项目中快速构建即时通讯应用。本文介绍如何快速跑通适配鸿蒙项目的 IM Demo 源码。

<!-- <img src="https://yx-web-nosdn.netease.im/common/11707474727796454a82bfdf823f5534/960主要模块.png" style="width:80%;border: 1px solid #BFBFBF;" /> -->

## 准备工作

在开始运行示例项目之前，请确保您已完成以下操作：

- 在 [网易云信控制台](https://app.yunxin.163.com/global/home) 上，[创建应用](https://doc.yunxin.163.com/console/guide/TIzMDE4NTA?platform=console)，获取应用密钥（App Key）。
- [注册 IM 账号](https://doc.yunxin.163.com/messaging2/guide/jU0Mzg0MTU?platform=client#第二步注册-im-账号)，获取账号 ID（`account_id`）和凭证（Token）。
- 在 [网易云信控制台](https://app.yunxin.163.com/global/home) 为应用开通 **云端会话** 开关。开启步骤请参考《控制台文档》[配置应用](https://doc.yunxin.163.com/console/concept/TQ2NzE5MzQ?platform=console)。

    <img alt="开通云端会话.png" src="https://yx-web-nosdn.netease.im/common/d80e78c7f8d0a5b7f0452e7f5d9c6b47/开通云端会话.png" style="width:50%;border: 1px solid #BFBFBF;">

- 准备如下开发环境：

    环境 | 版本要求 |
    ---- | ---- |
    DevEco Studio | NEXT Beta1(Build Version: 5.0.3.810) 及以上 |
    OpenHarmony SDK API | API Version 12 及以上版本 |

## 第一步：下载 Demo

前往 GitHub <a href="https://github.com/netease-kit/nim-uikit-harmony" target="_blank">下载 Demo 源码</a>，示例项目结构如下：

目录 | 组件 | 说明 | 是否必须依赖
---- | ---- | ---- | ----
`corekit` | 底层架构组件 | 底层框架 | 是
`common` | 通用 UI 组件 | 公用 UI 库 | 是
`chatkit` | 业务接口组件 | 业务逻辑层，依赖 [NIM SDK](https://doc.yunxin.163.com/messaging2/concept?platform=client) 提供各个业务数据接口 | 是
`chatkit_ui` | 聊天 UI 组件 | 聊天模块，包括单聊和群聊页面，以及消息发送、消息接受和消息 UI 等 | 否
`contactkit_ui` | 通讯录 UI 组件 | 通讯录、黑名单、系统通知组件 | 否
`localconversationkit_ui` | 本地会话 UI 组件 | 本地会话列表组件 <note type=notice>实际使用时，本地会话列表组件和云端会话列表组件二选一即可。 | 否
`conversationkit_ui` | 云端会话 UI 组件 | 云端会话列表组件 | 否
`teamkit_ui` | 群管理 UI 组件 | 群管理组件，群聊设置、群管理等 | 否
`imkit_sample` | 组件 Demo | Demo 源码，组件初始化、登录和设置相关功能 | 否
`libs` | SDK 依赖 | NIM SDK har 包，可以替换更新 NIM SDK | 是

## 第二步：导入项目

1. 将示例项目导入 DevEco Studio 开发环境。

2. 在 DevEco Studio 里找到工程目录 `imkit_sample/src/main/ets/constants/AppConfig.ets` 文件，修改文件配置：

    - appKey：替换成您在 [网易云信控制台](https://app.yunxin.163.com/global/home) 获取的应用密钥 [App Key](https://doc.yunxin.163.com/console/guide/TIzMDE4NTA?platform=console)。
    - userName：填入 [IM 账号 ID](https://doc.yunxin.163.com/messaging2/guide/jU0Mzg0MTU?platform=client#%E7%AC%AC%E4%BA%8C%E6%AD%A5%E6%B3%A8%E5%86%8C-im-%E8%B4%A6%E5%8F%B7)。
    - userToken：填入 [IM 账号 Token](https://doc.yunxin.163.com/messaging2/guide/jU0Mzg0MTU?platform=client#%E7%AC%AC%E4%BA%8C%E6%AD%A5%E6%B3%A8%E5%86%8C-im-%E8%B4%A6%E5%8F%B7)。

        ```TypeScript
        export class AppConfig {
            // appKey 和 userName 在网易云信控制台获取
            // appKey 网易云信应用 appkey
            public static appKey: string = ''
            // userName IM 应用账号 ID
            public static userName: string = ''
            // userName IM 应用账号 Token
            public static userToken: string = ''
        }
        ```

3. 签名配置，真机设备运行需要配置华为签名，请参考《华为官方文档》[应用开发准备](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides-V5/application-dev-overview-V5)。如果是采用鸿蒙虚拟机则不需要配置签名。

## 第三步：运行 Demo

将源码运行在您的鸿蒙设备上，即可进入登录页面，单击登录按钮则进入如下界面，开始体验 IM Demo。

<img src="https://yx-web-nosdn.netease.im/common/6858362055e77fc8a23285b63b0965be/Demo首页不含圈组.png" style="width:30%;border: 0px solid #BFBFBF;"/>