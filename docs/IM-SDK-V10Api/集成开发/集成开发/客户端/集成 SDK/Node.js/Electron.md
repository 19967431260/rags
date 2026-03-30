网易云信即时通讯 Electron SDK（以下简称 NIM Electron SDK）是基于原生 [NIM C++ SDK](https://doc.yunxin.163.com/messaging2/guide/zQ3MzQyMzQ?platform=client) 进一步封装、提供 TypeScript、JavaScript 接口的 SDK。本文以 [`nim-electron-quick-start`](https://github.com/netease-im/nim-electron-quick-start) 项目举例描述如何接入 NIM Electron SDK 到您的业务项目中，适用于已经了解 Electron 相关的工作原理的开发者。

::: note note 
本文主要介绍底层 Electron SDK 的集成，若您需要集成对应的 UI 组件，请参考 [集成 Electron UIKit](https://doc.yunxin.163.com/messaging-uikit/guide/DM1NjMzNjA?platform=electron)。
:::

## 适配平台

- NIM Electron SDK 可工作在任何基于 Node.js 的环境中，例如 Electron、Express 等项目。
- NIM Electron SDK 支持的平台及架构有：

    平台架构 | Windows | Linux | macOS |
    :---- | :---- | :---- | :---- |
    x86 | ✔️ | - | - |
    x86\_64 | ✔️ | ✔️ | ✔️ | 
    arm64 | - | ✔️ | ✔️ |

## 前提条件

根据本文操作前，请确保您已经完成了以下设置，以用在下文第四步功能测试阶段：

- 在 [网易云信控制台](https://app.yunxin.163.com/global/home) 上，[创建应用](https://doc.yunxin.163.com/console/guide/TIzMDE4NTA?platform=console)，获取 App Key 和 App Secret。
- [注册网易云信 IM 账号](https://doc.yunxin.163.com/messaging2/guide/jU0Mzg0MTU?platform=client#%E7%AC%AC%E4%BA%8C%E6%AD%A5%E6%B3%A8%E5%86%8C-im-%E8%B4%A6%E5%8F%B7)，获取 IM 账号和 Token。

## 第一步：克隆工程

```bash
git clone https://github.com/netease-im/nim-electron-quick-start.git
```

## 第二步：安装 SDK

进入工程目录，安装 NIM Electron SDK 依赖。

```bash
cd electron-quick-start
npm install node-nim@latest
```

## 第三步：修改源码

1. 为了快速演示，网易云信将在渲染进程引入 NIM Electron SDK 模块，您首先需要修改 [`main.js`](https://github.com/electron/electron-quick-start/blob/main/main.js) 的 `createWindow` 代码段，修改方式可参考 [Commit f8e52a6](https://github.com/netease-im/nim-electron-quick-start/commit/f8e52a63b4628a129974760caf9437f8a2b4bfc3)，效果如下所示：

    ```JavaScript
    function createWindow () {
    // Create the browser window.
    const mainWindow = new BrowserWindow({
        width: 800,
        height: 600,
        webPreferences: {
        preload: path.join(__dirname, 'preload.js'),
        nodeIntegration: true,
        contextIsolation: false,
        }
    })

    // and load the index.html of the app.
    mainWindow.loadFile('index.html')

    // Open the DevTools.
    mainWindow.webContents.openDevTools()
    }
    ```

2. 如果您的项目有安全性要求，可在 [`preload.js`](https://github.com/netease-im/nim-electron-quick-start/blob/main/preload.js) 中引入 NIM Electron SDK，具体请参考《Electron 官方文档》[Security](https://www.electronjs.org/docs/latest/tutorial/security)。

3. 修改 [`index.html`](https://github.com/netease-im/nim-electron-quick-start/blob/main/index.html)，增加登录登出 UI 入口，修改方式可参考 [Commit 1982ed2](https://github.com/netease-im/nim-electron-quick-start/commit/1982ed27b90c9e3dcd133ff342e98ed90924c083)。

    ```HTML
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="UTF-8">
        <!-- https://developer.mozilla.org/en-US/docs/Web/HTTP/CSP -->
        <meta http-equiv="Content-Security-Policy" content="default-src 'self'; script-src 'self'; style-src 'self' 'unsafe-inline'">
        <link href="./styles.css" rel="stylesheet">
        <title>Hello World!</title>
        <style>
        .container {
            margin: 0 auto;
            text-align: center;
        }
        </style>
    </head>
    <body>
        <div class="container">
        <div class="form-group">
            <input type="text" id="appkey" name="appkey" placeholder="Your appkey" required>
        </div>
        <div class="form-group form-group--buttons">
            <button id="init">Init</button>
            <button id="uninit">Uninit</button>
        </div>
        <div class="form-group">
            <input type="text" id="account" name="account" placeholder="Your account ID" required>
        </div>
        <div class="form-group">
            <input type="password" id="password" name="password" placeholder="Password" required>
        </div>
        <div class="form-group form-group--buttons">
            <button id="login">Login</button>
            <button id="logout">Logout</button>
        </div>
        </div>
        <script src="./renderer.js"></script>
    </body>
    </html>
    ```

4. 修改 [`renderer.js`](https://github.com/netease-im/nim-electron-quick-start/blob/main/renderer.js) 处理各个按钮事件，修改方式可参考 [Commit 24c880c](https://github.com/netease-im/nim-electron-quick-start/commit/24c880c846dbb46a469adfa60f269c7355b0b2fe)。

    ```JavaScript
    /**
     * This file is loaded via the <script> tag in the index.html file and will
     * be executed in the renderer process for that window. No Node.js APIs are
     * available in this process because `nodeIntegration` is turned off and
     * `contextIsolation` is turned on. Use the contextBridge API in `preload.js`
     * to expose Node.js functionality from the main process.
    */

    const { v2 } = require('node-nim')

    window.onload = () => {
    document.getElementById('init').onclick = () => {
        const appkey = document.getElementById('appkey').value
        const result = v2.init({ appkey })
        if (result) {
        console.error(`[nim] failed to initialize NIM SDK, result: ${result}`)
        } else {
        v2.loginService.on('loginStatus', (status) => {
            // 登录状态变更回调
            console.log(`[nim] login status changed: ${status}`)
        })
        v2.loginService.on('loginFailed', (error) => {
            // 登录失败状态回调
            console.error(`[nim] login failed: ${JSON.stringify(error)}`)
        })
        v2.loginService.on('kickedOffline', (details) => {
            // 被踢下线回调
            console.warn(`[nim] kicked offline: ${details}`)
        })
        v2.loginService.on('connectStatus', (connectStatus) => {
            // 连接状态变更回调
            console.log(`[nim] connect status changed: ${connectStatus}`)
        })
        v2.loginService.on('disconnected', (error) => {
            // 断开连接回调
            console.warn(`[nim] disconnected: ${JSON.stringify(error)}`)
        })
        v2.loginService.on('connectFailed', (error) => {
            // 连接失败回调
            console.error(`[nim] connect failed: ${JSON.stringify(error)}`)
        })
        v2.loginService.on('dataSync', (syncType, syncState, error) => {
            // 数据同步回调
            console.log(`[nim] data sync: ${syncType}, ${syncState}, ${JSON.stringify(error)}`)
        })
        console.log('[nim] init success')
        }
    }
    document.getElementById('uninit').onclick = () => {
        const result = v2.uninit()
        if (result) {
        console.error(`[nim] failed to uninitialize NIM SDK, result: ${result}`)
        } else {
        console.log('[nim] uninit success')
        }
    }
    document.getElementById('login').onclick = async () => {
        const account = document.getElementById('account').value
        const password = document.getElementById('password').value
        try {
            await v2.loginService.login(account, password, {})
        } catch (error) {
            console.error(`[nim] failed to login, error: ${JSON.stringify(error)}`)
        }
    }
    document.getElementById('logout').onclick = async () => {
        try {
            await v2.loginService.logout()
        } catch (error) {
            console.error(`[nim] failed to logout, error: ${JSON.stringify(error)}`)
        }
    }
    }
    ```

## 第四步：功能测试

1. 在终端中输入 `npm start` 启动项目，您可看到如下效果图：

    <img alt="image" src="https://yx-web-nosdn.netease.im/common/288e29801dec630b80179cde323b6542/image.png" style="width:80%;border: 0px solid #BFBFBF;">

2. 输入 `appkey` 后单击 **Init** 按钮进行初始化，输入 **account ID** 及 **password** 后，单击 **Login** 登录，即可看到控制台输出内容：

    <img alt="image" src="https://yx-web-nosdn.netease.im/common/fa314d9dfdfd25751b0a297ba19cc937/image.png" style="width:80%;border: 0px solid #BFBFBF;">