<!-- keywords: 即时通讯,IM,基本功能,集成,集成 SDK,快速开始 -->

网易云信即时通讯 SDK Electron 版（以下简称为 NIM Electron SDK）封装了 NIM PC SDK，同时具有原生平台性能，为 Electron 应用提供完善的即时通信功能开发框架。您可以在前端框架中使用 PC 端所有功能，通过简洁的 API 调用快速实现即时通信功能。

本文介绍如何快速将 NIM SDK 集成到您的 Electron 项目中。

## 开发环境

使用 NIM Electron SDK 请确保您的开发环境满足以下要求：

- Electron 8.5.5 及以上版本
- Node.js 12.13.0 及以上版本
- 各端开发环境要求：

    平台 | 架构 | 系统版本
    ---- | ---- | ----
    Windows | x64/IA-32 | Windows 7 及以上
    macOS | x64/arm64 | 10.14.0 及以上 |
    Linux | x64/arm64 | glibc 2.23 及以上 |

## 第一步：安装 SDK 及依赖

1. 打开终端并进入您的项目目录，执行以下命令安装 `node-nim` 模块：

    ```NPM
    npm install node-nim --save-dev
    ```

    安装完成后，您可以在当前目录下看到一个名为 `node_modules` 的文件夹，其中包含了 `node-nim` 模块及其所有依赖项。

2. 如果您需要在 x64 平台上构建 IA-32 应用程序或类似操作，可以使用 `--arch` 和 `--platform` 参数来指定要构建的平台。

    :::::: div linked-codes
    ::: code Windows x64
    ```
    npm install node-nim --save-dev --arch=x64 --platform=win32
    ```
    :::
    ::: code windows x86
    ```
    npm install node-nim --save-dev --arch=ia32 --platform=win32
    ```
    :::
    ::: code macOS x64
    ```
    npm install node-nim --save-dev --arch=x64 --platform=darwin
    ```
    :::
    ::: code macOS arm64
    ```
    npm install node-nim --save-dev --arch=arm64 --platform=darwin
    ```
    :::
    ::: code Linux x64
    ```
    npm install node-nim --save-dev --arch=x64 --platform=linux
    ```
    :::
    ::: code Linux arm64
    ```
    npm install node-nim --save-dev --arch=arm64 --platform=linux
    ```
    :::
    ::::::

## 第二步：导入 NIM 模块

在 js 文件中，添加以下 `import` 代码，将 NIM 模块导入到您的项目。

```JavaScript
import * as node_nim from 'node-nim'
```

## 下一步

完成 SDK 集成后，需进行 [初始化](https://doc.yunxin.163.com/messaging/docs/DU1NjYyMzY?platform=electron)。

## 相关参考

### 示例项目

网易云信在 Github 上提供了开源的 [示例项目](https://github.com/netease-im/node-nim)，为您后续的 IM 集成提供参考。

### API 参考

您可以在 [Electron SDK API](https://doc.yunxin.163.com/messaging/references/electron/typedoc/Latest/zh/index.html) 了解 SDK API 信息。