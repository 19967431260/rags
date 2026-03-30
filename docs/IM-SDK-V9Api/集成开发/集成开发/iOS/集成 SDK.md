<!--keywords: iOS,集成,CocoaPods,手动,SDK,初始化-->

本文介绍如何快速将网易云信 IM SDK（NetEase Instant Messaging SDK，NIM SDK）集成到您的 iOS 项目中。

## 开发环境要求

开发环境需满足 iOS 9.0 及以上版本，可使用 iPhone/iPad 真机或模拟器。

## 第一步：新建项目

<details><summary>单击查看如何新建项目，若需集成到已有项目，可 <b>忽略本步骤</b>。</summary>
1. 启动 Xcode，在左上角选择<strong>File > New > Project</strong>。<br/>2. 在出现的工作表中，选择 <strong>iOS</strong> 平台，并在 <strong>Application</strong> 下选择 <strong>App</strong>。<br/>3. 配置新建项目，完成后，单击 <strong>Next</strong>。<br/>必须填写 <strong>Product Name</strong> 和 <strong>Organization Identifier</strong>。<br/>4. 选择项目存储路径，单击 <strong>Create</strong> 创建项目。<br/><img src="https://yx-web-nosdn.netease.im/common/7b768a4a522c286b2cd4cbba27ad40d8/新建项目.png" alt="新建项目">

</details>

## <span id="集成 SDK">第二步：集成 SDK</span>

网易云信即时通讯 NIM SDK 支持两种集成方式，您可按需选择。

### 方式一：（推荐）**<span id="CocoaPods 集成">CocoaPods 集成</span>**

1. 安装 CocoaPods 后，在项目所在目录下执行以下命令，创建 Podfile 文件。
    ```
    pod init
    ```
2. 在 Podfile 文件中添加对应的资源。

    `CocoaPods` 集成资源关键词说明：

    关键词 | 所含资源
    :-- | :-
    NIMSDK_LITE | IM 即时通讯，默认引入网易对象存储（NetEase Object Storage，NOS）文件存储能力
    NIMSDK_LITE/FCS | IM 即时通讯，默认引入 S3 文件存储能力
    NIMSDK/QChat | IM 即时通讯的圈组能力<note type=notice>自 V9.17.0 起，实现圈组能力插件化。因此对于升级使用圈组的用户，除了需要引入 NIMSDK，还需要单独引入 NIMSDK/QChat。对于未使用圈组的用户，忽略该变动。
    NIMKit | NIMSDK_LITE+NIM_iOS_UIKit+[特定版本](https://github.com/netease-im/NIM_iOS_UIKit/blob/master/NIMKit.podspec) 的第三方依赖库
    NIMKit/Lite_Free | NIMSDK_LITE+NIM_iOS_UIKit+不限制版本的第三方依赖库

    如只需要即时通讯功能（NOS），且不需 `NIM_iOS_UIKit` 组件，可在 `Podfile` 中写入：

    ```
    pod 'NIMSDK_LITE'
    ```

    如需要即时通讯功能（NOS）和圈组能力，且不需 `NIM_iOS_UIKit` 组件，可在 `Podfile` 中写入：

    ```
    pod 'NIMSDK_LITE'
    pod 'NIMSDK/QChat'
    ```

    如需要使用海外即时通讯功能（S3），可在 `Podfile` 中写入：

    ```
    pod 'NIMSDK_LITE/FCS'
    ```

3. 执行以下命令更新本地仓库，查看版本信息。最新版本信息请参考 <a href="https://doc.yunxin.163.com/messaging/guide/jQ3NzQ3NDI?platform=iOS" target="_blank">更新日志</a>。
    ```
    pod search NIMSDK_LITE   //本地仓库中查询资源的版本信息
    pod repo update          //更新本地仓库
    ```
4. 执行以下命令安装 SDK：

    ```
    pod install
    ```
### 方式二：**<span id="手动集成">手动集成</span>**

1. <a href="https://doc.yunxin.163.com/messaging/resource">下载</a> 对应的 SDK。

    Framework | 说明
    --- | ---
    NIMSDK | IM 即时通讯基础功能
    NIMNOS | NOS 文件存储能力，需要与 NIMSDK 一起使用（不能与 NIMFCS 一起使用）
    NIMFCS | S3 文件存储能力，需要与 NIMSDK 一起使用（不能与 NIMNOS 一起使用）
    NIMSocketRocket | WebSocket 能力，用于提升联通性，可自主选择集成。若选择集成，需要与 NIMSDK 一起使用
    NIMQUIC | QUIC 能力，用于提升联通性，可自主选择集成。若选择集成，需要与 NIMSDK 一起使用

    :::note note
    - NIMSDK 需要与 NIMNOS 或者 NIMFCS 搭配使用，无法单独使用。
        - 若开发者服务的对象在国内，则使用 NIMSDK 和 NIMNOS Frameworks。
        - 若开发者服务的对象在海外，需要 S3 文件存储能力，那么使用 NIMSDK 和 NIMFCS Frameworks。
    - NIMNOS 和 NIMFCS 无法同时使用。
    :::

2. 将解压得到的 framework 文件拷贝到工程项目文件夹下。
3. 选择 **TARGETS > Project Name > General > Frameworks, Libraries, and Embedded Content** 菜单，添加对应的 framework 文件，并将 **Embed** 属性设置为 **Embed & Sign**，以使得 SDK 动态库和应用签名保持一致。至此，SDK 导入完成。

    <img src="https://yx-web-nosdn.netease.im/common/6cd2d54908b03b3b8c06ca74509f912d/2022-10-10_173543.png" />

## 下一步

完成 SDK 集成后，需进行 [初始化](https://doc.yunxin.163.com/messaging/guide/TE0MDc5MTI?platform=iOS)。

## 相关参考

### Demo 参考

网易云信在 Github 上提供了 [开源的 IM Demo](https://github.com/netease-kit/nim-uikit-ios)，为您后续的 IM 集成提供参考。

### 核心 API 列表

您可在 [iOS SDK API](https://doc.yunxin.163.com/messaging/guide/jY3NTQ0NTU?platform=iOS) 了解 SDK API 的调用方式和通知方式，并查看核心 API 列表和核心类列表。

## 常见问题

### 为什么打包失败？

在[手动集成 SDK](#手动集成) 时，由于库包含模拟器版本，可能会导致打包失败。所以需要在打包之前去掉模拟器版本。

1. 在工程里创建 `nim_strip_archs.sh` 脚本到指定目录，如 `Supporting Files`。
2. 在 `Build Phases` 中增加过程，类型为 `New Run Script Phase`。
3. 在工程里添加以下内容。如 `/bin/sh "${SRCROOT}/NIMDemo/Supporting Files/nim_strip_archs.sh"`。
    ```Bash
    /bin/sh 您的脚本路径
    ```
4. 将以下内容复制到脚本中。
    ```Bash
    #!/bin/sh

    # Strip invalid architectures

    strip_invalid_archs() {
    binary="$1"
    echo "current binary ${binary}"
    # Get architectures for current file
    archs="$(lipo -info "$binary" | rev | cut -d ':' -f1 | rev)"
    stripped=""
    for arch in $archs; do
    if ![[ "${ARCHS}" == *"$arch"* ]]; then
    if [ -f "$binary" ]; then
    # Strip non-valid architectures in-place
    lipo -remove "$arch" -output "$binary" "$binary" | | exit 1
    stripped="$stripped $arch"
    fi
    fi
    done
    if [[ "$stripped" ]]; then
    echo "Stripped $binary of architectures:$stripped"
    fi
    }

    APP_PATH="${TARGET_BUILD_DIR}/${WRAPPER_NAME}"

    # This script loops through the frameworks embedded in the application and
    # removes unused architectures.
    find "$APP_PATH" -name '*.framework' -type d | while read -r FRAMEWORK
    do
    FRAMEWORK_EXECUTABLE_NAME=$(defaults read "$FRAMEWORK/Info.plist" CFBundleExecutable)
    FRAMEWORK_EXECUTABLE_PATH="$FRAMEWORK/$FRAMEWORK_EXECUTABLE_NAME"
    echo "Executable is $FRAMEWORK_EXECUTABLE_PATH"

    strip_invalid_archs "$FRAMEWORK_EXECUTABLE_PATH"
    done
    ```