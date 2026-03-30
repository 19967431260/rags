网易云信 IM SDK（NetEase Instant Messaging SDK，NIM SDK）为 Node.js 应用，提供完善的即时通信功能开发能力，屏蔽其内部复杂细节，对外提供较为简洁的 API 接口，方便您快速集成即时通信功能。通过 NIM SDK，可以将即时通讯应用业务场景推广到拥有 Node.js 环境的服务端，充分运用到 **服务器即客户端、客户端即服务器** 的使用场景中，诸如 Linux 工业控制、聊天机器人、数据管道、单机监控、规模化数据分析等。

本文介绍如何快速将 NIM SDK 集成到您的 Node.js 项目中。

## 注意事项

由于浏览器环境的全局变量为 `window`，而 Node.js 的全局变量为 `global`，为了做到兼容及适配，NIM SDK 会模拟（mock）一些属性，诸如 `navigator`、`location`、`WebSocket` 等对象到 `global` 中，一般不影响您的正常使用。

## 环境要求

Node.js v12 及以上版本。

## 第一步：安装 SDK

通过如下 NPM 命令安装最新版 SDK。

```
npm install @yxim/nim-web-sdk@latest
```

<a id="files"></a>

## 第二步：选择文件

使用 `require` 方式引入您所需 SDK 文件。以下示例为引入同时包含 IM 对象和聊天室对象的 SDK 文件：

```JavaScript
const SDK = require('@yxim/nim-web-sdk/dist/SDK/NIM_Web_SDK_nodejs')
const nim = SDK.NIM.getInstance({
    // ...
})
```

SDK 所包含的文件如下：

```
dist/SDK
├── NIM_Web_NIM_nodejs.js       // 提供常规 IM 功能，包括单聊、会话、群聊等，Node.js 适配版（UMD 格式）
├── NIM_Web_Chatroom_nodejs.js  // 提供聊天室功能，Node.js 适配版 UMD 格式
├── NIM_Web_SDK_nodejs.js       // 提供常规 IM 和聊天室功能，Node.js 适配版 UMD 格式
```

::: note important
引入 SDK 文件时，**请勿同时引入以下两种文件组合**：
- 勿同时引入 `NIM_Web_SDK_nodejs_vX.X.X.js` 和 `NIM_Web_Chatroom_nodejs_v.X.X.X.js`。
- 勿同时引入 `NIM_Web_SDK_nodejs_vX.X.X.js` 和 `NIM_Web_NIM_nodejs_vX.X.X.js`。
:::

请根据下表的说明引入您所需的 SDK 文件。初始化不同 SDK 文件，需调用不同的 SDK API。

业务需求 | 需引入的文件 | 初始化实例的接口
---- | ---- | ----
常规 IM（单聊、群聊等） | `NIM_Web_NIM_nodejs_vX.X.X.js` | [`NIM.getInstance`](https://doc.yunxin.163.com/docs/interface/messaging/web/typedoc/Latest/zh/NIM/classes/nim.NIM.html#getInstance)
聊天室 | `NIM_Web_Chatroom_nodejs_vX.X.X.js` | [`Chatroom.getInstance`](https://doc.yunxin.163.com/docs/interface/messaging/web/typedoc/Latest/zh/Chatroom/classes/chatroom.Chatroom.html#getInstance)
常规 IM 和聊天室 | `NIM_Web_SDK_nodejs_vX.X.X.js` | <ul><li>[`SDK.NIM.getInstance`](https://doc.yunxin.163.com/docs/interface/messaging/web/typedoc/Latest/zh/NIM/classes/nim.NIM.html#getInstance)</li><li>[`SDK.Chatroom.getInstance`](https://doc.yunxin.163.com/docs/interface/messaging/web/typedoc/Latest/zh/Chatroom/classes/chatroom.Chatroom.html#getInstance)</li><ul>

## 第三步：初始化

完成 SDK 集成后，您需要 [初始化并登录 IM](https://doc.yunxin.163.com/messaging/guide/zE0NDY4Njc?platform=web)。

## 第四步：使用 SDK

### **<span id="实例调用方式">实例调用方式</span>**

集成 NIM SDK 后，所有 SDK 能力均通过 NIM SDK 单例调用，例如：

```JavaScript
  // 引入 SDK 类的引用以后，获取 SDK 对象实例
  var nim = SDK.NIM.getInstance({
    debug: true,
    appKey: appKey,
    account: account,
    token: token,
    // ...
  });
```

以发送点对点消息为例：

```JavaScript
  var msg = nim.sendText({
    scene: 'p2p',
    to: account,
    text: 'hello',
    done: function sendMsgDone (error, msg) {
      // ...
    }
  });
```

### **<span id="事件通知方式">事件通知方式</span>**

NIM SDK 通过回调（`callback`）和委托（`delegate`）两种方式通知上层 API 调用结果，均 **只在主线程触发**。

- 一般回调接口直接反映在相应接口的 `done` 参数上，**调用时设置即可**。
- 委托则需要您在合适时机，在 **初始化异步监听函数** 上进行处理。

    ```JavaScript
    // 委托通知示例
    var nim = NIM.getInstance({
        // ... 此处省略其他配置
        onmsg: function (msg) {
        // 此处为委托消息事件，消息发送成功后，成功消息也在此处处理
        }
    });

    // 回调通知示例
    var msg = nim.sendText({
        scene: 'p2p',
        to: account,
        text: 'hello',
        done: function sendMsgDone (error, msg) {
        // 此处为回调消息事件，仅仅通知开发者，消息是否发送成功
        }
    });
    ```

### **<span id="本地数据库">本地数据库</span>**

由于服务器环境的存储系统具有多样性，SDK 不在内部再对数据库进行集成，您可以自行使用诸如 mysql、oracle、ms-sql、sqlite、mongodb、hbase 等等数据存储服务。

使用 Node.js SDK 的同时，您依然可以调用 [服务端接口](https://doc.yunxin.163.com/messaging/server-apis?platform=server)，直接对服务器数据进行操作。

### **<span id="文件">发送文件</span>**

Node.js 的上传接口请使用 `filePath` 参数：

```JavaScript
  nim.previewFile({
    type: 'image',
    maxSize: maxSize,
    commonUpload: true,
    filePath: options.filePath,
    uploadprogress(obj) {
      // ...
    },
    done: (error, file) => {
      const { scene, to } = options;
      if (!error) {
        constObj.nim.sendFile({
          type: 'image',
          scene,
          to,
          file,
          done: (err, msg) => {
            if (err) {
              return;
            }
            this.appendMsg(msg);
          },
        });
      }
    },
  });
```

### **<span id="日志记录">日志记录</span>**

SDK 支持使用第三方日志记录工具，辅助您在服务器端使用文件 log 的方式记录日志，以下以 `npm`-`log4js 3.*` 第三方库为例，进行 SDK 的日志记录。

- 初始化 `log4js`：

    ```JavaScript
    const log4js = require('log4js');
    log4js.configure({
        replaceConsole: true,
        appenders: { nimlog: { type: 'file', filename: 'nim-debug.log' } },
        categories: { default: { appenders: ['nimlog'], level: 'ALL' } }
    });
    const logger = log4js.getLogger('nimlog');
    ```

- IM 及聊天室部分日志插件引入方式：

    ```JavaScript
    global.nim = NIM.getInstance({
        debug: true,
        logFunc: logger,
        // ...
    })
    ```

<!-- **备注**：RN 还不适合对外，暂时隐藏

<span id="React Native">React Native</span>

<span id="React Native 概述">React Native 概述</span>

v5.3.0 开始，网易云信 Web-SDK 对 React Native 做了适配，推荐 RN 版本 >=0.51。网易云信 WebSDK React Native(以下简称 RN-SDK)的大部分 API 使用方法与 SDK 在 Web 浏览器环境使用相同，以减少开发者使用 SDK 所带来的障碍。

<span id="本地数据库">本地数据库</span>

RN-SDK 支持含数据库和不含数据库的使用方式，根据开发者的业务场景，可自行处理。

- **不使用数据库，即在 IM 初始化时对 `db` 设为 `false` 即可，如**：

```JavaScript
  const nim = NIM.getInstance({
    debug: true,
    appKey: appKey,
    account: account,
    token: token,
    db: false, // 不使用数据库
    onconnect: onConnect,
    onwillreconnect: onWillReconnect,
    ondisconnect: onDisconnect,
    onerror: onError
  });
```

- **使用数据库，需要开发者安装使用 [realm](https://realm.io/docs/javascript/latest/#getting-started)，RN-SDK 目前自身不支持但不限制使用 `sqlite3` 作为本地数据库。可以通过 `usePlugin` 方法将数据库挂在到 SDK 实例上，用法如下**：

```JavaScript
  const SDK = require('NIM_Web_SDK_vx.x.x.js');
  const Realm = require('realm');
  // 此处将外置的 realm 数据库挂载到 sdk 上，供 sdk 使用
  SDK.usePlugin({
    db: Realm,
  });
  const nim = SDK.NIM.getInstance({
    debug: true,
    appKey: appKey,
    account: account,
    token: token,
    db: true,   // 使用数据库
    onconnect: onConnect,
    onwillreconnect: onWillReconnect,
    ondisconnect: onDisconnect,
    onerror: onError
  });
```

<span id="本地日志">本地日志</span>

RN-SDK 支持本地日志存储及远程拉取，您可以根据需求选择是否使用本地日志功能。

使用本地日志功能后，SDK 会将日志以文件的形式写到用户的终端（手机）上，用户在线时，可以调用服务端接口拉取用户终端上的日志，便于排查问题。

本地存储依赖 [react-native-fs](https://github.com/itinance/react-native-fs) 库，具体使用方法如下：

1. 安装 react-native-fs

  ```
  npm install react-native-fs --save
  ```

2. 通过 usePlugin 方法将数据库挂在到 sdk 上，如下

  ```JavaScript
  const RNFS = require('react-native-fs');

  const params = {
    rnfs: RNFS
  };
  params.rnfs.size = 1024 * 1024; // 日志文件体积上限，单位:bytes; 选填，默认为 1M
  SDK.usePlugin(params);

  const nim = SDK.NIM.getInstance({
    // .....
    // 初始化 IM
  });
  ```

<span id="消息推送">消息推送</span>

v5.3.0 版本开始支持推送能力，开发者在配置工程时，需要引入相应的安卓和 APNs 推送依赖。

- APNs 推送
  - APNs 推送配置首先需要开发者去苹果官网申请具有推送能力的证书。
  - 配置完证书后，按照 [RN 推送配置](https://reactnative.cn/docs/pushnotificationios/)添加相关能力。

- 安卓推送
  - 参考 RN-Demo 的 `./android/nimpush **与** ./nim/NIM_Android_Push.js`。
  - 配置参考 [安卓推送配置](https://github.com/netease-im/NIM_ReactNative_Demo/blob/master/%E5%AE%89%E5%8D%93%E6%8E%A8%E9%80%81%E9%85%8D%E7%BD%AE.md)。

若不需要推送，则初始化时相关的 `iosPushConfig` 与 `androidPushConfig` 参数不填即可。

**示例代码**：

```JavaScript
  // iOS/安卓端外推送代码
  const iosPushConfig = {
    tokenName: 'push_online',
  };
  const androidPushConfig = {
    xmAppId: '2882303106219',
    xmAppKey: '59717219',
    xmCertificateName: 'RN_MI_PUSH',
    hwCertificateName: 'RN_HW_PUSH',
    mzAppId: '11398',
    mzAppKey: 'b74148973e60a2af4c2f6779',
    mzCertificateName: 'RN_MZ_PUSH',
    fcmCertificateName: 'RN_FCM_PUSH',
    vivoCertificateName: "vivopush",
    oppoAppId: "xxx", // oppoAppId，oppoAppKey，oppoAppSercet 在 oppo 推送平台注册得到
    oppoAppKey: "xxx",
    oppoAppSercet: "xxx",
    oppoCertificateName: "oppopush"
  };
  var nim = SDK.NIM.getInstance({
    // ...
    iosPushConfig,
    androidPushConfig,
    // ...
  })

  // 安卓端内推送示例代码，非远程推送
  import { showNotification } from '../nim/NIM_Android_Push';
  showNotification({
    icon: '', title: msg.from, content: showText, time: `${msg.time}`,
  });
```

<span id="文件发送">文件发送</span>

由于 RN-SDK 发送文件消息需要额外获取文件消息的属性一起发送，所以不建议直接使用 `sendFile` 接口发送文件，而是先通过 `previewFile` 获取文件的句柄，通过其他 api 方法将文件属性添加回文件对象，最后再使用 `sendFile` 接口发送文件。以下为发送图片文件的示例：

```JavaScript
  nim.previewFile({
    type: 'image',
    filePath: options.filePath,
    maxSize: maxSize,
    commonUpload: true,
    uploadprogress(obj) {
      // ...
    },
    done: (error, file) => {
      // 通过其他 API 接口获取到长、宽、大小等图片属性
      file.w = options.width;
      file.h = options.height;
      file.md5 = options.md5;
      file.size = options.size;
      const { scene, to } = options;
      if (!error) {
        constObj.nim.sendFile({
          type: 'image',
          scene,
          to,
          file,
          done: (err, msg) => {
            if (err) {
              return;
            }
            this.appendMsg(msg);
          },
        });
      }
    },
  });
```

- **消息需要额外附加属性列表**：
  - 图片对象
    - size: 大小，单位 byte
    - md5: 图片文件的 md5 转换后的值
    - w: 宽，单位 px
    - h: 高，单位 px
  - 音频对象
    - size: 大小，单位 byte
    - md5: 音频文件的 md5 转换后的值
    - dur: 长度，单位 ms
  - 视频对象
    - size: 大小，单位 byte
    - md5: 视频文件的 md5 转换后的值
    - w: 宽，单位 px
    - h: 高，单位 px
    - dur: 长度，单位 ms
  - 文件对象
    - size: 大小，单位 byte
    - md5: 文件的 md5 转换后的值 -->