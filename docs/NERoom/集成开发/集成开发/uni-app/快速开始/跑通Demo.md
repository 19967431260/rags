本文介绍如何快速跑通  RoomKit(uts插件) 示例工程。

## 开发环境要求

在运行示例项目之前，请确保开发环境满足以下要求：

环境要求 |说明 |
---- | -------------- | ---------
[HBuilderX](https://www.dcloud.io/hbuilderx.html) | 最新版本 | 
iOS 及 Android 设备 | App 运行环境满足如下要求：|\
 | - iOS 13.0 或以上版本的 iOS 设备。暂不支持模拟器。 |\
 | - Android 系统 5.0 或以上版本的 Android 设备。暂不支持模拟器。 | 


## 示例源码目录结构说明
```
以下是项目完整目录结构：
uniapp-neroom/
├── src/
│   ├── router/                       # 路由
│   │   ├── index.ts
│   │   ├── queryString.ts
│   │   └── wxRouter.ts
│   └── roomkit/
│       ├── config/
│       │   └── basic-info-config.js  # AppKey / SDKAPPID 配置
│       ├── pages/
│       │   ├── login.vue             # 登录页
│       │   ├── home.vue              # 主页
│       │   └── room.nvue             # 房间页（nvue）
│       └── NERoom/
│           ├── conference.ts / .vue  # 入口 & 会议组件
│           ├── preConference.vue     # 入会前预览
│           ├── hooks/
│           │   ├── useRoomEngine.ts  # 各类实例封装（new RoomEngine 等）
│           │   ├── useChatRoom.ts
│           │   ├── useDeviceManager.ts
│           │   └── ...
│           ├── services/
│           │   ├── neRoomService.ts  # 核心事件监听服务
│           │   └── manager/
│           ├── stores/               # Pinia 状态管理
│           │   ├── neroom.ts 
│           ├── components/           # UI 组件
│           ├── locales/              # 国际化（zh-CN / en-US）
│           ├── utils/
│           └── assets/
│               ├── icons/            # 120+ SVG/PNG 图标
│               ├── imgs/
│               └── style/
├── uni_modules/
│   └── netease-roomkit/              # UTS 插件（核心）
│       ├── package.json              # version: 1.41.0
│       └── utssdk/
│           ├── interface.uts         # 公共接口定义
│           ├── app-android/
│           │   ├── index.uts         # 安卓端所有类实现（~9000行）
│           │   ├── types/            # 类型定义
│           │   ├── utils/            # 工具函数
│           │   ├── ScreenShareManager.kt
│           │   └── VideoViewStore.uts
│           └── app-ios/
│               ├── index.uts         # iOS 端所有类实现
│               ├── utils/
│               └── *Bridge.swift     # iOS 事件桥接（Listener Bridge）
├── pages/                            # UniApp 页面路由配置目录
├── static/                           # 全局静态资源
├── App.vue / main.ts / pages.json
├── manifest.json
└── package.json                      # scripts: pack:plugin / pack:demo
```  
## 步骤1：运行示例源码 

::: note important
示例源码仅供开发者接入参考，实际应用开发场景中，请结合具体业务需求修改使用。

若您计划将源码用于生产环境，请确保应用正式上线前已经过全面测试，以免因兼容性等问题造成损失。
:::

1. 下载 [Demo 源码](https://yx-web-nosdn.netease.im/package/1774330816928/NERoomKit_Demo_1.41.0.zip?download=NERoomKit_Demo_1.41.0.zip)至您本地。
2. 使用 HBuilderX 打开示例项目源码。
3. 示例源码需要在 `basic-info-config.js` 文件中配置应用的 SDKAPPID 。

4. 打开项目根目录下的 `manifest.json` 文件，在基础配置页面，单击 **uni-app应用标识（AppID）** 文本框右侧的**自动获取**。

::: note important
uts插件已经在项目中注入(uniapp-neroom\uni_modules\netease-roomkit)
:::


## 步骤2：制作自定义调试基座

您需要使用自定义基座打包 uni-app 插件，以便在手机上运行调试，并且可以在 HBuilder 控制台看到日志。

::: note note
uni-app 官方自定义调试基座使用说明请参考 [什么是自定义调试基座及使用说明](https://uniapp.dcloud.net.cn/tutorial/run/run-app.html#customplayground)。
:::

1. 在 HBuilderX 的顶部菜单栏中选择 **运行** > **运行到手机或模拟器** > **制作自定义调试基座**。 


    ![image2.png](https://yx-web-nosdn.netease.im/common/54bf0e88899b3f815e1641e97dc647bd/image2.png)



2. 在弹出的对话框中选择**打自定义调试基座**，单击**打包**。详细步骤请参见 [uni-app 官网的自定义基座](https://uniapp.dcloud.net.cn/tutorial/run/run-app.html#customplayground)。

    
    ![image3.png](https://yx-web-nosdn.netease.im/common/4722b3dd8ce646cd6ad5226e1eaa9aff/image3.png)



    打包成功后，控制台会收到 uni-app 的相关提示。


    ![image4.png](https://yx-web-nosdn.netease.im/common/1f72e0eaa1415504daf84194ca56a34a/image4.png)



3. 使用自定义调试基座。

    在 HBuilderX 的顶部菜单栏中选择**运行** > **运行到手机或模拟器** > **运行基座选择**  > **自定义调试基座**。


    ![image5.png](https://yx-web-nosdn.netease.im/common/2ec4a5abf0b253b68a98bd89be46327c/image5.png)



## 步骤3：运行代码

选择**运行** > **运行到手机或模拟器**，选择自己的设备，并运行。

![image6.png](https://yx-web-nosdn.netease.im/common/f5c232f0211245694da58f79dff15d98/image6.png)
