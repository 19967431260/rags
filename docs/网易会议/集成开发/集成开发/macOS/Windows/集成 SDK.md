本文为您介绍在 Windows 和 macOS 应用中，集成 NEMeetingKit 的步骤。NEMeetingKit 主要用于实现音视频会议，帮助您在业务中实现创建会议、预约会议、查询会议信息、遥控器服务等在线会议场景下的相关能力。

## 前提条件

在根据本文操作前，请确保您已在网易云信控制台上，完成以下设置：

1. 在控制台创建至少一个应用。若无应用，请参考 <a href="https://doc.yunxin.163.com/console/concept/TIzMDE4NTA">创建应用并获取 AppKey</a>。
2. 开通 **视频会议** 解决方案。具体步骤可参考 [方案开通](https://doc.yunxin.163.com/meeting/concept/TkzMjExNDY?platform=client)。

## 版本环境

:::::: div linked-codes
::: code Windows

- 适用的 SDK 版本：v2.18.0.0 及以上版本
- 支持 Win 10 及以上操作系统

:::

::: code macOS

- 系统版本：macOS 10.11 + 版本
- Xcode 10 + 版本
- VSCode 拓展：CMake
- Qt 6.+ 版本

:::
::::::

## 安装环境

### 安装 Qt

根据您的操作系统版本，前往 [Qt Group 官方网站](https://download.qt.io/official_releases/qt/) 下载并安装适合的 Qt 安装程序。

### 安装 CMake

CMake 广泛用于管理 C++ 项目的编译过程。根据您的操作系统类型，安装方式如下：

:::::: div linked-codes
::: code Windows
前往 [CMake 官网](https://cmake.org/download/) 按需下载。
:::
::: code macOS
```Homebrew
$ /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
# or
$ brew install cmake
```
:::
::::::

## 下载 SDK

:::::: div linked-codes
::: code Windows

单击下载会议组件离线包 <a href="https://yx-web-nosdn.netease.im/package/NEMeet_Windows_SDK_V4.9.0_202410232140_1c2d48042f.zip?download=NEMeet_Windows_SDK_V4.9.0_202410232140_1c2d48042f.zip?download=0" target="_blank">NEMeet_Windows_SDK_V4.8.0_202408300946_9e48ad8bae.zip</a>。下载并解压缩完成后，Windows SDK 目录结构如下：

- `meeting_sdk_example_qt`
- SDK 打开文件夹，包含以下几个部分：

    目录名 | 说明 |
    ---- | ---- |
    include | SDK 接口头文件 |
    lib | SDK 依赖的资源文件和库文件 |
    bin/libnemeet_base.dll | 64 位 App 依赖的库文件 |
    nemeet_sdk.exe | ^^ |

:::
::: code macOS

单击下载会议组件离线包 <a href="https://yx-web-nosdn.netease.im/package/NEMeet_MacOS_SDK_V4.9.0_202410232146_1c2d48042f.zip?download=NEMeet_MacOS_SDK_V4.9.0_202410232146_1c2d48042f.zip?download=0" target="_blank">NEMeet_MacOS_SDK_V4.8.0_202408300950_9e48ad8bae.zip</a>。下载并解压缩完成后，macOS SDK 目录结构如下：

```Bash
.
├── docs <-- 文档
├── meeting_sdk_example_qt <-- 示例程序
└── sdk <-- SDK (arm64&x86_64)
```
:::
::::::

## Demo 工程

Demo 工程主要用于展示 SDK 功能和 API 调用示例。Demo 工程存放在 `meeting_sdk_example_qt` 目录下。

### 编译与运行 Demo App 

:::::: div linked-codes
::: code Windows

1. 根据当前系统的硬件架构，将对应目录下的 `sdk` 复制到 `meeting_sdk_example_qt` 目录下。

2. 配置 Qt，下载并配置 Qt 环境。

    <img alt="image_qt_path.png" src="https://yx-web-nosdn.netease.im/common/85c1bd0ef06548a09afb5d8559660989/image_qt_path.png" style="width:80%;border: 1px solid #BFBFBF;">

4. 在 Visual Studio Code 中，打开 `meeting_sdk_example_qt` 工程。

    :::note note
    建议使用 Visual Studio Code 2019，其他版本未经过严格测试。
    :::

5. 删除 Demo 工程中原有的 `sdk` 文件夹。

    <img alt="image_example_sdk.png" src="https://yx-web-nosdn.netease.im/common/fe7899b0223012d4bfac6ad6d1379e1b/image_example_sdk.png" style="width:40%;border: 1px solid #BFBFBF;">

4. 运行工程。

    ```Shell
    $ cd meeting_sdk_example_qt
    $ .\build.bat // build.bat Qt 环境替成本地环境
    ```

    <img alt="image_run.png" src="https://yx-web-nosdn.netease.im/common/bccd6f39f884dde116215c2f32a6b528/image_run.png" style="width:80%;border: 1px solid #BFBFBF;">
:::
::: code macOS
1. 从下载的 SDK 包解压后，进入 `sdk` 目录。

2. 在 Visual Studio Code 中打开 `meeting_sdk_example_qt/` 工程。

3. 如果 Demo 工程中有 `sdk` 文件夹，则删除。

4. 根据当前系统的硬件架构，将对应目录下的 `sdk` 复制到 `meeting_sdk_example_qt/` 目录下。

    <img alt="image_example_sdk.png" src="https://yx-web-nosdn.netease.im/common/fe7899b0223012d4bfac6ad6d1379e1b/image_example_sdk.png" style="width:40%;border: 1px solid #BFBFBF;">

5. 运行工程。

    - 方式一：

        ```Shell
        $ cd meeting_sdk_example_qt
        $ sh build.sh // build.sh Qt 环境替成本地环境
        ```

    - 方式二：

        <img alt="image_run.png" src="https://yx-web-nosdn.netease.im/common/bccd6f39f884dde116215c2f32a6b528/image_run.png" style="width:80%;border: 1px solid #BFBFBF;">
:::
::::::

### 运行和使用 Demo App

运行起来后的 Sample App 界面如下，需要填写您在 [网易云信控制台](https://app.yunxin.163.com/global/home) 已经申请好的应用 `appKey`，单击 **初始化** 进入后续流程。

`nemeet_sdk.app` 的路径为 `sdk/bin` 目录下的 `nemeet_sdk.app` 文件。需要确定本地 `nemeet_sdk.app` 文件的路径是否正确。

:::::: div linked-codes
::: code Windows
- 本地路径示例：`sdk/bin/nemeet_sdk`

    <img alt="image_nemeet_sdk_path1.png" src="https://yx-web-nosdn.netease.im/common/5092930c59c5de7e3b5d437482a95ae4/image_nemeet_sdk_path1.png" style="width:80%;border: 1px solid #BFBFBF;">

- 调试运行

    <img alt="image_init.png" src="https://yx-web-nosdn.netease.im/common/1ebab12ff8ca9663ee092aa3bfc7a75f/image.png" style="width:80%;border: 1px solid #BFBFBF;">

<!-- <img alt="image_sdk.png" src="https://yx-web-nosdn.netease.im/common/d613e880ecb094a08320d0f267089fbf/image_sdk.png" style="width:80%;border: 1px solid #BFBFBF;"> -->
:::
::: code macOS

- 本地路径示例：`sdk/bin/nemeet_sdk.app`

    <img alt="image_nemeet_sdk_path1.png" src="https://yx-web-nosdn.netease.im/common/32d97013e64fcc2375544b027427978f/image_nemeet_sdk_path1.png" style="width:80%;border: 1px solid #BFBFBF;">

- 本地路径示例：`sdk/bin/nemeet_sdk.app/Contents/MacOS/nemeet_sdk`

    <img alt="image_nemeet_sdk_path2.png" src="https://yx-web-nosdn.netease.im/common/16fe7dcf8f3b231abd58eb8fe71896d9/image_nemeet_sdk_path2.png" style="width:80%;border: 1px solid #BFBFBF;">

- 调试运行

    <img alt="image_init.png" src="https://yx-web-nosdn.netease.im/common/1ebab12ff8ca9663ee092aa3bfc7a75f/image.png" style="width:80%;border: 1px solid #BFBFBF;">
<!-- <img alt="image_sdk.png" src="https://yx-web-nosdn.netease.im/common/ed16048f74fb3a64afc2e67c10ad533a/image_sdk.png" style="width:80%;border: 1px solid #BFBFBF;"> -->
:::
::::::