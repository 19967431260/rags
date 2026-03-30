<!--keywords: iOS,集成,CocoaPods,手动,SDK,初始化-->

网易云信即时通讯（NetEase IM）SDK V10（以下简称 NIM SDK）融合了 V9 接口，本文介绍如何快速将 NIM SDK 集成到您的 iOS 项目中。

::: note note 
本文主要介绍底层 iOS SDK 的集成，若您需要集成对应的 UI 组件，请参考 [集成 iOS UIKit](https://doc.yunxin.163.com/messaging-uikit/guide/DA0MjY3ODY?platform=iOS)。
:::

## 开发环境

开发环境要求需满足 iOS 9.0 及以上版本，可使用 iPhone/iPad 真机或模拟器。

## 第一步：新建项目

::: details 单击展开查看如何新建项目，若需集成到已有项目，可忽略此步骤。

1. 启动 Xcode，在左上角选择 <strong>File > New > Project</strong>。
2. 在出现的工作表中，选择 <strong>iOS</strong> 平台，并在 <strong>Application</strong> 下选择 <strong>App</strong>。
3. 配置新建项目，完成后，单击 <strong>Next</strong>。

    必须填写 <strong>Product Name</strong> 和 <strong>Organization Identifier</strong>。

4. 选择项目存储路径，单击 <strong>Create</strong> 创建项目。

    <img src="https://yx-web-nosdn.netease.im/common/7b768a4a522c286b2cd4cbba27ad40d8/新建项目.png" style="width:100%;border: 1px solid #BFBFBF;">
:::

## <span id="集成 SDK">第二步：集成 SDK</span>

### **<span id="CocoaPods 集成">方式一：（推荐）CocoaPods 集成</span>**

1. 安装 CocoaPods 后，在项目所在目录下执行以下命令，创建 Podfile 文件。

    ```CocoaPods
    pod init
    ```

2. 在 Podfile 文件中添加对应的资源。

    `CocoaPods` 集成资源关键词说明：

    关键词 | 所含资源
    ---- | ----
    NIMSDK_LITE | IM 即时通讯，默认使用网易对象存储（NetEase Object Storage，NOS）文件存储能力。
    NIMSDK_LITE/NOS | IM 即时通讯，引入网易对象存储（NetEase Object Storage，NOS）文件存储能力。
    NIMSDK_LITE/FCS | IM 即时通讯，引入 S3 文件存储能力。
    NIMSDK_LITE/FTS | 本地检索库，若需要使用本地检索功能，需要提前引入。
    NIMSDK_LITE/QChat | IM 即时通讯的圈组能力，若需要使用圈组功能，需要提前引入。

    若需要使用 **IM UIKit**，请参考 [集成 IM UIKit](https://doc.yunxin.163.com/messaging-uikit/guide/DA0MjY3ODY?platform=iOS)。

    现以只需要集成即时通讯功能（NOS）为例，您可在 `Podfile` 中写入：

    ```CocoaPods
    pod 'NIMSDK_LITE'
    //若需要使用本地检索功能，单独引入 FTS
    //pod 'NIMSDK_LITE/FTS'
    ```

3. 执行以下命令更新本地仓库，查看版本信息。最新版本信息请参考 <a href="https://doc.yunxin.163.com/messaging2/docs/TIxNTgxOTk?platform=client" target="_blank">更新日志</a>。

    ```CocoaPods
    pod search NIMSDK_LITE   //本地仓库中查询资源的版本信息
    pod repo update          //更新本地仓库
    ```

4. 执行以下命令安装 SDK：

    ```CocoaPods
    pod install
    ```

### **<span id="手动集成">方式二：手动集成</span>**

1. 前往 <a href="https://doc.yunxin.163.com/messaging2/resource?platform=iOS">资源下载</a> 获取 SDK。

    :::::: div linked-codes
    ::: code 国内服务（NOS）
    Framework | 是否必选 | 说明
    --- | --- | ---
    NIMSDK | 是 | IM 即时通讯基础功能。
    NIMNOS | 是 | NOS 文件存储能力。
    NIMSocketRocket | 否 | WebSocket 能力，用于提升联通性。
    NIMQUIC | 否 | QUIC 能力，用于提升联通性。
    NIMQChat | 否 | IM 即时通讯的圈组能力，可自主选择集成。
    NIMDBEx | 否 | 本地检索库，用于使用本地检索功能，可自主选择集成。
    :::
    ::: code 海外服务（FCS）
    Framework | 是否必选 | 说明
    --- | --- | ---
    NIMSDK | 是 | IM 即时通讯基础功能。
    NIMNOS | 是 | NOS 文件存储能力。
    NIMAWSCore | 是 | S3 文件存储能力，NIMAWSCore 和 NIMAWSS3 必须同时引入。
    NIMAWSS3 | 是 | S3 文件存储能力，NIMAWSCore 和 NIMAWSS3 必须同时引入。
    NIMSocketRocket | 否 | WebSocket 能力，用于提升联通性。
    NIMQUIC | 否 | QUIC 能力，用于提升联通性。
    NIMQChat | 否 | IM 即时通讯的圈组能力，可自主选择集成。
    NIMDBEx | 否 | 本地检索库，用于使用本地检索功能，可自主选择集成。
    :::
    ::::::    
    
    :::note note
    - 针对海外服务的文件存储 NIMFCS（历史的 S3 文件存储能力）由于体积过大，现以使用 NIMAWSCore&NIMAWSS3 替换。若您之前引入了 NIMFCS，请及时替换。
    - NIMNOS 和 NIMFCS 无法同时使用。
    :::

2. 将解压得到的 framework 文件拷贝到工程项目文件夹下。
3. 选择 **TARGETS > Project Name > General > Frameworks, Libraries, and Embedded Content** 菜单，添加对应的 framework 文件，并将 **Embed** 属性设置为 **Embed & Sign**，以使得 SDK 动态库和应用签名保持一致。至此，SDK 导入完成。

    <img src="https://yx-web-nosdn.netease.im/common/6cd2d54908b03b3b8c06ca74509f912d/2022-10-10_173543.png" style="width:70%;border: 1px solid #BFBFBF;"/>

## 下一步

完成 SDK 集成后，您需要 [初始化 SDK](https://doc.yunxin.163.com/messaging2/docs/jU5MTUwMDY?platform=client)。

此外，您可在 [API 概览](https://doc.yunxin.163.com/messaging2/docs/DY2Mjk0MjU?platform=client) 了解 API 的调用方式。

## 常见问题

- [手动集成打包失败问题](https://doc.yunxin.163.com/messaging2/faq/TM4MjcwMDQ?platform=client)
- [App Store 审核应用时出现包含 bitcode 报错问题](https://doc.yunxin.163.com/messaging2/faq/jE4MjAwMTI?platform=client)

