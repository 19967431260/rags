## 问题描述

在 Xcode 开发环境下，将采用网易云信的音视频产品适配的 iOS 客户端 SDK（例如 [NERtcSDK](https://doc.yunxin.163.com/nertc/concept?platform=client) 或 [播放器](https://doc.yunxin.163.com/live-player/concept?platform=client)）开发的应用打包提交到苹果应用商店（App Store）审核时，出现包含 Bitcode 的报错，诸如如下报错：

```sh
Invalid Executable. The executable 'XXX.app/Frameworks/NERtcSDK.framework

NERtcSDK' contains bitcode.
```

其中，Xcode16 报错情况较多。

## 原因分析

请参考 [App Store 审核应用时出现包含 bitcode 的报错](https://doc.yunxin.163.com/messaging2/faq/jE4MjAwMTI?platform=client)。


## 解决方法

您可以下载 [`remove_nertc_bitcode.sh`](https://yx-web-nosdn.netease.im/common/cf24944d8706e60e115701e91a570afb/remove_nertc_bitcode.sh?download=remove_nertc_bitcode.sh) 脚本，批量去除引入了网易云信音视频产品 SDK 系列的 iOS 项目中的 Bitcode。

### NERTC SDK

1. 通过 `cd` 命令进入到 NERtcSDK frameworks 所在路径。

    :::note note
    如果是 pods 集成，NERtcSDK frameworks 所在路径为 `Pods/NERtcSDK/NERTC/NERtcSDK`。
    :::

2. 拷贝 [`remove_nertc_bitcode.sh`](https://yx-web-nosdn.netease.im/common/cf24944d8706e60e115701e91a570afb/remove_nertc_bitcode.sh?download=remove_nertc_bitcode.sh) 脚本到 frameworks 所在路径。

3. 执行以下命令：

    ```sh
    sh remove_nertc_bitcode.sh
    ```

### 播放器

1. 通过 `cd` 命令进入到播放器的 frameworks 所在路径。

    :::note note
    如果是 pods 集成 `pod 'NELivePlayer', '3.2.7'`，则 NELivePlayer 的 frameworks 所在路径为 `Pods/NELivePlayer/LivePlayer_iOS_SDK_v3.2.7`。
    :::

2. 拷贝 [`remove_nertc_bitcode.sh`](https://yx-web-nosdn.netease.im/common/cf24944d8706e60e115701e91a570afb/remove_nertc_bitcode.sh?download=remove_nertc_bitcode.sh) 脚本到 frameworks 所在路径。

3. 执行以下命令：

    ```sh
    sh remove_nertc_bitcode.sh
    ```

4. 同理，如果 `NMCBasicModuleFramework` 有问题，将脚本拷贝到 `NMCBasicModuleFramework.framework` 所在路径，并执行 `sh remove_nertc_bitcode.sh` 命令。