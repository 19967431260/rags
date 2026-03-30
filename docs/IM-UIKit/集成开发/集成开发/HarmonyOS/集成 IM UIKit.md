<!--keywords: 快速开始,快速集成 IM UIkit,UIKit,demo,IM UIKit,IMUIKit,Kit -->

网易云信 IM UIKit 是基于鸿蒙版本 [网易云信 IM SDK（简称 NIM SDK）](https://doc.yunxin.163.com/messaging2/concept?platform=client) 开发的一款 <a href="https://doc.yunxin.163.com/messaging-uikit/concept/TI3NTgyNDA?platform=client">即时通讯 UI 组件库</a>，功能涵盖了聊天、会话、群管理。本文介绍鸿蒙项目如何按照以下流程集成 IM UIKit。

```mermaid
graph LR
    classDef default fill:#337EFF,stroke:#337EFF,stroke-width:0px,color:#FFFFFF;
导入组件 --> 添加权限 --> 初始化 --> 登录 --> 搭建界面
```

<a id="preparation"></a>

## 准备工作

在开始集成 IM UIKit 前，请确保您已完成以下操作：

- 在 [网易云信控制台](https://app.yunxin.163.com/global/home) 上，[创建应用](https://doc.yunxin.163.com/console/concept/TIzMDE4NTA?platform=console)，并获取应用密钥（App Key）。
- [注册 IM 账号](https://doc.yunxin.163.com/messaging2/quick-start/jU0Mzg0MTU?platform=client#第二步注册-im-账号)，获取账号 ID（`account_id`）和凭证（`token`）。
- 访问 [Gitee 仓库地址](https://gitee.com/growth-ease/nim-uikit-harmony) 或 [GitHub 仓库地址](https://github.com/netease-kit/nim-uikit-harmony) 的网易云信 IM UIKit 鸿蒙源码项目。

- 准备如下开发环境：

    环境 | 版本要求 |
    ---- | ---- |
    DevEco Studio | NEXT Beta1(Build Version: 5.0.3.810) 及以上 |
    OpenHarmony SDK API | API Version 12 及以上 |

## 注意事项

由于 IM UIKit 的初始化与登录是通过底层调用 NIM SDK 接口实现的，因此重复调用 IM UIKit 和 NIM SDK 的初始化与登录接口会相互覆盖传入的信息（包括 **推送配置信息**）。

所以，若您同时集成 IM UIKit 和 NIM SDK，只需要调用一次 [初始化](#init) 与 [登录](#loginIM) 接口即可。

## 第一步：按需导入组件

1. 根据业务需要，将 **源码模块** 复制到您的工程目录中。

2. 在您的工程目录下，声明导入模块。

3. 在主工程的 `oh-package.json5` 中，以添加依赖的形式添加相应的 IM UIKit 组件。

### 导入组件

根据您的业务需要，将源码中组件模块复制到您的工程目录中，具体目录可以是您工程根目录，也可以是您新建的子目录。本文档以根目录为例。

源码中组件目录如下：

目录 | 组件 | 说明 | 是否必须依赖
:---- | :---- | :---- | :----
`corekit` | 底层架构组件 | 底层框架 | 是
`common` | 通用 UI 组件 | 公用 UI 库 | 是
`chatkit` | 业务接口组件 | 业务逻辑层，依赖 [NIM SDK](https://doc.yunxin.163.com/messaging2/concept?platform=client) 提供各个业务数据接口 | 是
`chatkit_ui` | 聊天 UI 组件 | 聊天模块，包括单聊和群聊页面，以及消息发送、消息接受和消息 UI 等 | 否
`contactkit_ui` | 通讯录 UI 组件 | 通讯录、黑名单、系统通知组件 | 否
`callkit` | 呼叫组件 | 提供音视频通话功能 | 否
`callkit-ui` | 含 UI 的呼叫组件 | 提供含 UI 的音视频通话，具体请参考 [实现呼叫功能](https://doc.yunxin.163.com/nertccallkit/guide/jA4MzgyNTk?platform=harmonyos) | 否
`localconversationkit_ui` | 本地会话 UI 组件 | 本地会话列表组件 <note type=notice>实际使用时，本地会话列表组件和云端会话列表组件二选一即可。 | 否
`conversationkit_ui` | 云端会话 UI 组件 | 云端会话列表组件 | 否
`teamkit_ui` | 群管理 UI 组件 | 群管理组件，群聊设置、群管理等 | 否
`imkit_sample` | 组件 Demo | Demo 源码，组件初始化、登录和设置相关功能 | 否
`libs` | SDK 依赖 | NIM SDK har 包，可以替换更新 NIM SDK | 是

### 声明组件

在工程根目录下声明导入组件，具体可参考源码 **build-profile.json5** 文件，如下所示：

```JSON
{
  "app": {
    ...
  },
  "modules": [
    {
      "name": "common",
      "srcPath": "./common",
      "targets": [
        {
          "name": "default",
          "applyToProducts": [
            "default"
          ]
        }
      ]
    },
    //本地会话列表申明，实际使用中，本地会话与云端会话需要二者选一
    {
      "name": "localconversationkit_ui",
      "srcPath": "./localconversationkit_ui",
      "targets": [
        {
          "name": "default",
          "applyToProducts": [
            "default"
          ]
        }
      ]
    },
    //云端会话列表声明
    {
      "name": "conversationkit_ui",
      "srcPath": "./conversationkit_ui",
      "targets": [
        {
          "name": "default",
          "applyToProducts": [
            "default"
          ]
        }
      ]
    },
    {
      "name": "chatkit_ui",
      "srcPath": "./chatkit_ui",
      "targets": [
        {
          "name": "default",
          "applyToProducts": [
            "default"
          ]
        }
      ]
    },
    {
      "name": "chatkit",
      "srcPath": "./chatkit",
    },
    {
      "name": "corekit",
      "srcPath": "./corekit",
    },
    {
      "name": "contactkit_ui",
      "srcPath": "./contactkit_ui",
    },
    {
      "name": "teamkit_ui",
      "srcPath": "./teamkit_ui",
      "targets": [
        {
          "name": "default",
          "applyToProducts": [
            "default"
          ]
        }
      ]
    }
  ]
}
```

### 引用组件

引用组件是指根据业务所需引入所依赖的组件。例如，如果您的业务中需要本地/云端会话列表、聊天和通讯录功能，那么您需要依赖所有组件，具体可参考源码 **imkit_sample/oh-package.json5** 文件，如下所示：

:::::: div linked-codes
::: code 本地会话模式
```JSON
"dependencies": {
  "@nimkit/localconversationkit_ui": "file:..//localconversationkit_ui",// 本地会话列表组件，实际使用时，本地会话列表组件和云端会话列表组件需要二选一
  "@nimkit/contactkit_ui": "file:../contactkit_ui", // 通讯录组件
  "@nimkit/teamkit_ui": "file:../teamkit_ui", // 群管理组件
  "@nimkit/chatkit_ui": "file:../chatkit_ui", // 聊天组件组件
  "@nimkit/chatkit": "file:../chatkit", // 业务能力模块
  "@nimkit/common": "file:../common", // 通用UI组件
  "@nimkit/corekit": "file:../corekit", // 底层架构组件

  // NIM SDK 包依赖，您也可以参考 SDK 文档，使用远端仓库依赖
  "@nimsdk/localconversation": "10.x.x", 
  "@nimsdk/message": "10.x.x",
  "@nimsdk/team": "10.x.x",
  "@nimsdk/user": "10.x.x",
  "@nimsdk/friend": "10.x.x",
  "@nimsdk/nim": "10.x.x",
  "@nimsdk/base": "10.x.x",
  "@nimsdk/signalling": "10.x.x",

  // 呼叫组件，自 10.4.0 版本引入呼叫组件，提供音视频通话功能
  "@yunxin/callkit": "4.0.2",
  "@yunxin/callkit_ui": "4.0.3",
  "@nertc/nertc_sdk": "5.9.11"
}
```
:::
::: code 云端会话模式
```JSON
"dependencies": {
  "@nimkit/conversationkit_ui": "file:../conversationkit_ui", // 云端会话列表组件，实际使用时，本地会话列表组件和云端会话列表组件需要二选一
  "@nimkit/contactkit_ui": "file:../contactkit_ui", // 通讯录组件
  "@nimkit/teamkit_ui": "file:../teamkit_ui", // 群管理组件
  "@nimkit/chatkit_ui": "file:../chatkit_ui", // 聊天组件组件
  "@nimkit/chatkit": "file:../chatkit", // 业务能力模块
  "@nimkit/common": "file:../common", // 通用UI组件
  "@nimkit/corekit": "file:../corekit", // 底层架构组件

  // NIM SDK 包依赖，您也可以参考 SDK 文档，使用远端仓库依赖
  "@nimsdk/conversation": "10.x.x", 
  "@nimsdk/message": "10.x.x",
  "@nimsdk/team": "10.x.x",
  "@nimsdk/user": "10.x.x",
  "@nimsdk/friend": "10.x.x",
  "@nimsdk/nim": "10.x.x",
  "@nimsdk/base": "10.x.x",
  "@nimsdk/signalling": "10.x.x",

  // 呼叫组件，自 10.4.0 版本引入呼叫组件，提供音视频通话功能
  "@yunxin/callkit": "4.0.2",
  "@yunxin/callkit_ui": "4.0.3",
  "@nertc/nertc_sdk": "5.9.11"
}
```
:::
::::::

## 第二步：添加权限

在即时通讯应用场景中，在鸿蒙系统中所需的权限申请相机和麦克风权限，其他文件和图片权限官方推荐不需要单独申请。具体请参考 `chatkit_ui` 目录中 **/src/main/module.json5**，您需要添加所需权限的文件配置如下所示：

```JSON
"requestPermissions": [
      {
        "name": "ohos.permission.CAMERA",
        "reason": "$string:chat_permission_camera_desc",
        "usedScene": {
          "abilities": [
            "FormAbility"
          ],
          "when": "always"
        }
      },
      {
        "name": "ohos.permission.MICROPHONE",
        "reason": "$string:chat_permission_micro_phone_desc",
        "usedScene": {
          "abilities": [
            "FormAbility"
          ],
          "when": "always"
        }
      }
    ]
```

<a id="init"></a>

## 第三步：初始化

在应用启动时候，注册和初始化 NIM SDK，然后使用初始化后的 NIM 实例，再初始化 UI 组件。初始化需要使用到您在 [准备工作](#preparation) 阶段获取的网易云信应用 App Key。

具体请参考源码工程 **NimRepository.ets** 文件。您可以在 `UIAbility` 中进行初始化，示例代码如下：

:::::: div linked-codes
::: code 本地会话模式
```TypeScript
export default class DefaultAbility extends UIAbility {
  //NIM 示例，全局使用可以放在全局的类中，参考源码中'NimRepository'类
  private _nim: NIMInterface | undefined

  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    // 初始化参数
    let initializeOptions: NIMInitializeOptions = {
      appkey: '',// 网易云信应用密钥（App Key）
      logLevel: LogLevel.Debug, //日志级别配置
      isOpenConsoleLog: true // 打开后可以将 nimsdk 的日志输出到控制台
      // ...其他属性
    };

    // 服务参数
    let serviceOptions: NIMServiceOptions = {
      loginServiceConfig: {
        lbsUrls: ['https://lbs.netease.im/lbs/webconf.jsp'],
        linkUrl: 'weblink.netease.im:443'
      },
      pushServiceConfig: {
        harmonyCertificateName: '' // 推送证书配置，参考 NIM SDK 推送配置
      }
    }
    //初始化 NIM SDK(使用本地会话)
    NIMSdk.registerCustomServices(V2NIMProvidedServiceType.V2NIM_PROVIDED_SERVICE_TEAM,
      (core, serviceName, serviceConfig) => new V2NIMTeamServiceImpl(core, serviceName, serviceConfig))
    NIMSdk.registerCustomServices(V2NIMProvidedServiceType.V2NIM_PROVIDED_SERVICE_CLIENT_ANTISPAM_UTIL,
      (core, serviceName, serviceConfig) => new V2NIMClientAntispamUtil(core, serviceName, serviceConfig));
    NIMSdk.registerCustomServices(V2NIMProvidedServiceType.V2NIM_PROVIDED_SERVICE_LOCAL_CONVERSATION,
      (core, serviceName, serviceConfig) => new V2NIMLocalConversationServiceImpl(core, serviceName, serviceConfig));
    NIMSdk.registerCustomServices(V2NIMProvidedServiceType.V2NIM_PROVIDED_SERVICE_MESSAGE,
      (core, serviceName, serviceConfig) => new V2NIMMessageServiceImpl(core, serviceName, serviceConfig));
    NIMSdk.registerCustomServices(V2NIMProvidedServiceType.V2NIM_PROVIDED_SERVICE_USER,
      (core, serviceName, serviceConfig) => new V2NIMUserServiceImpl(core, serviceName, serviceConfig));
    NIMSdk.registerCustomServices(V2NIMProvidedServiceType.V2NIM_PROVIDED_SERVICE_FRIEND,
      (core, serviceName, serviceConfig) => new V2NIMFriendServiceImpl(core, serviceName, serviceConfig));
    NIMSdk.registerCustomServices(V2NIMProvidedServiceType.V2NIM_PROVIDED_SERVICE_SIGNALLING,
      (core, serviceName, serviceConfig) => new V2NIMSignallingServiceImpl(core, serviceName, serviceConfig));
    this._nim = NIMSdk.newInstance(this._context, initializeOptions, serviceOptions)
    // 始化 NIM SDK 之后，您需要初始化 UI 组件（`ChatKitClient.init()`）才能正常使用 UI 组件
    ChatKitClient.init(this._nim, initializeOptions.appkey)
  }
}
```
::: 
::: code 云端会话列表
```TypeScript
export default class DefaultAbility extends UIAbility {
  //NIM 示例，全局使用可以放在全局的类中，参考源码中'NimRepository'类
  private _nim: NIMInterface | undefined

  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    // 初始化参数
    let initializeOptions: NIMInitializeOptions = {
      appkey: '',// 网易云信应用密钥（App Key）
      logLevel: LogLevel.Debug, //日志级别配置
      isOpenConsoleLog: true // 打开后可以将 nimsdk 的日志输出到控制台
      // ...其他属性
    };

    // 服务参数
    let serviceOptions: NIMServiceOptions = {
      loginServiceConfig: {
        lbsUrls: ['https://lbs.netease.im/lbs/webconf.jsp'],
        linkUrl: 'weblink.netease.im:443'
      },
      pushServiceConfig: {
        harmonyCertificateName: '' // 推送证书配置，参考 NIM SDK 推送配置
      }
    }
    //初始化 NIM SDK(使用云端会话)
    NIMSdk.registerCustomServices(V2NIMProvidedServiceType.V2NIM_PROVIDED_SERVICE_TEAM,
      (core, serviceName, serviceConfig) => new V2NIMTeamServiceImpl(core, serviceName, serviceConfig))
    NIMSdk.registerCustomServices(V2NIMProvidedServiceType.V2NIM_PROVIDED_SERVICE_CLIENT_ANTISPAM_UTIL,
      (core, serviceName, serviceConfig) => new V2NIMClientAntispamUtil(core, serviceName, serviceConfig));
    NIMSdk.registerCustomServices(V2NIMProvidedServiceType.V2NIM_PROVIDED_SERVICE_CONVERSATION,
      (core, serviceName, serviceConfig) => new V2NIMConversationServiceImpl(core, serviceName, serviceConfig));
    NIMSdk.registerCustomServices(V2NIMProvidedServiceType.V2NIM_PROVIDED_SERVICE_MESSAGE, 
      (core, serviceName, serviceConfig) => new V2NIMMessageServiceImpl(core, serviceName, serviceConfig));
    NIMSdk.registerCustomServices(V2NIMProvidedServiceType.V2NIM_PROVIDED_SERVICE_USER,
      (core, serviceName, serviceConfig) => new V2NIMUserServiceImpl(core, serviceName, serviceConfig));
    NIMSdk.registerCustomServices(V2NIMProvidedServiceType.V2NIM_PROVIDED_SERVICE_FRIEND,
      (core, serviceName, serviceConfig) => new V2NIMFriendServiceImpl(core, serviceName, serviceConfig));
    NIMSdk.registerCustomServices(V2NIMProvidedServiceType.V2NIM_PROVIDED_SERVICE_SIGNALLING,
      (core, serviceName, serviceConfig) => new V2NIMSignallingServiceImpl(core, serviceName, serviceConfig));
    this._nim = NIMSdk.newInstance(this._context, initializeOptions, serviceOptions) 
    // 始化 NIM SDK 之后，您需要初始化 UI 组件（`ChatKitClient.init()`）才能正常使用 UI 组件
    ChatKitClient.init(this._nim, initializeOptions.appkey)
  }
}
```
:::
::::::

<a id="loginIM"></a>

## 第四步：登录

调用登录的方法时，将如下示例代码中的 `accountId` 和 `token` 分别替换为您在 [准备工作](#preparation) 阶段获取的账号 ID （即 `accountId`）和 Token。

```TypeScript
async login(accountId: string, token: string) {
    try {
      await this._nim.loginService.login(accountId, token);
      promptAction.showToast({
        message: "登录成功",
        alignment: Alignment.Center
      })
    } catch (error) {
      console.log('----------- 登录失败 -----------', error)
      AlertDialog.show(
        {
          title: '登录失败',
          message: '登录失败',
          autoCancel: true,
          alignment: DialogAlignment.Bottom,
          offset: { dx: 0, dy: -20 },
          gridCount: 3,
          confirm: {
            value: 'OK',
            action: () => {
              console.info('Button-clicking callback')
            }
          },
          cancel: () => {
            console.info('Closed callbacks')
          }
        }
      )
    }
  }

```

## 第五步：搭建 UI 界面

网易云信 IM UIKit 提供通用的 [UI 组件库](https://doc.yunxin.163.com/messaging-uikit/concept/TI3NTgyNDA?platform=client)。

<a id="界面集成详情"></a>

IM UIKit 为鸿蒙项目提供的常用业务场景界面及相关详细集成说明如下：

界面 | 所属组件 | 说明
---- | ---- | ----
`LocalConversationPage` | `localconversationkit_ui` | 本地会话列表界面，实际使用时，本地会话列表界面和云端会话列表界面需要二选一
`ConversationPage` | `conversationkit_ui` | 云端会话列表界面
`ContactPage` | `contactkit_ui` | 通讯录界面
`ChatP2PPage` | `chatkit_ui` | 单聊会话界面
`ChatTeamPage` | `chatkit_ui` | 群聊会话界面

以搭建 Demo 中 **本地会话列表**、**通讯录**、**我的** 界面为例，在您应用中创建新的 ETS（Entry Table Source）类，声明为界面。示例代码如下：

```TypeScript
// tab 数据结构
@ObservedV2
class TabBarItem {
  title: ResourceStr = "";
  targetIndex: number = 0;
  @Trace showRedPoint: boolean = false;
  normalIcon: Resource;
  selectedIcon: Resource;

  constructor(title: ResourceStr, targetIndex: number, normalIcon: Resource, selectedIcon: Resource,
    showRedPoint: boolean = false) {
    this.title = title;
    this.targetIndex = targetIndex;
    this.showRedPoint = showRedPoint;
    this.normalIcon = normalIcon;
    this.selectedIcon = selectedIcon;
  }
}

// 界面
@Entry
@ComponentV2
struct TabIndex {
  //导航
  pathStack: NavPathStack = new NavPathStack()
  @Local currentIndex: number = 0;
  // 创建三个界面
  @Local tabs: Array<TabBarItem> = [
    new TabBarItem($r('app.string.tab_conversation'), 0, $r('app.media.tab_conversation'),
      $r('app.media.tab_conversation_light')),
    new TabBarItem($r('app.string.tab_contact'), 1, $r('app.media.tab_contact'), $r('app.media.tab_contact_light')),
    new TabBarItem($r('app.string.tab_mine'), 2, $r('app.media.tab_mine'), $r('app.media.tab_mine_light'))
  ];

  loadUnreadApplication = async () => {
    try {
      const unreadCount = await ContactRepo.getAddApplicationUnreadCount()
      this.tabs[1].showRedPoint = unreadCount > 0
    } catch (err) {
      console.log(err)
    }
  }
  onUnreadApplicationChange = (unreadCountString?: string) => {
    this.tabs[1].showRedPoint = unreadCountString !== undefined
  }
  //未读消息回调
  onUreadMessageChange = (unreadCount?: number) => {
    this.tabs[0].showRedPoint = (unreadCount ?? 0) > 0
  }
  //获取会话列表未读数
  loadUnreadMessageCount = () => {
    const unreadCount = ConversationRepo.getTotalUnreadCount()
    if (unreadCount) {
      this.tabs[0].showRedPoint = unreadCount > 0
    }
  }

  async aboutToAppear(): Promise<void> {
    ChatKitClient.nim.friendService?.on("onFriendAddApplication", async (application: V2NIMFriendAddApplication) => {
      await this.loadUnreadApplication()
    })

    try {
      await this.loadUnreadApplication()
    } catch (err) {
      console.log(err)
    }
    this.loadUnreadMessageCount()
  }

  @Builder
  TabBarBuilder(item: TabBarItem) {
    Stack() {
      Column() {
        Image(this.currentIndex === item.targetIndex ? item.selectedIcon : item.normalIcon)
          .size({ width: 28, height: 28 })
          .margin({ top: 8 })

        Text(item.title)
          .fontColor(this.currentIndex === item.targetIndex ? '#337EFF' : '#999999')
          .margin({ top: 4 })
      }
      .justifyContent(FlexAlign.Center)

      if (item.showRedPoint) {
        Column()
          .width(6)
          .height(6)
          .borderRadius(3)
          .backgroundColor('#F24957')
          .margin({
            top: 7
          })
      }
    }
    .alignContent(Alignment.TopEnd)
  }

  // 界面构建
  build() {
    Navigation(this.pathStack) {
      Tabs({ barPosition: BarPosition.End, index: 0 }) {
        ForEach(this.tabs, (item: TabBarItem) => {
          TabContent() {
            if (item.targetIndex == 0) {
              // 创建会话列表界面
              LocalConversationPage({
                pathStack: this.pathStack,
                onUreadMessageChange: this.onUreadMessageChange
              })
            } else if (item.targetIndex == 1) {
              // 创建通讯录界面
              ContactPage({
                pathStack: this.pathStack,
                onUnreadApplicationChange: this.onUnreadApplicationChange
              })
            } else if (item.targetIndex == 2) {
              // 创建我的界面
              MinePage({
                pathStack: this.pathStack
              })
            }
          }
          .tabBar(this.TabBarBuilder(item))
        })
      }
      .barHeight(60)
      .backgroundColor("#F6F8FA")
      .barPosition(BarPosition.End)
      .onChange((index: number) => {
        this.currentIndex = index
      })
    }
    .backgroundColor(Color.Transparent)
    .mode(NavigationMode.Auto)
    .hideTitleBar(true)
  }
}
```

## 下一步

为保障通信安全，如果您在调试环境中的使用的是网易云信控制台生成的测试用 IM 账号 和 `token`，请确保在后续的正式生产环境中，将其替换为通过 <a href="https://doc.yunxin.163.com/messaging2/server-apis/TQyNjgyMzc?platform=server" target="_blank">IM 服务端 API</a> 生成的正式 IM 账号（`accout_id`）和 `token`。

## 相关参考

更多云信呼叫组件集成相关文档请参考 [快速实现呼叫](https://doc.yunxin.163.com/nertccallkit/guide/jA4MzgyNTk?platform=harmonyos)。