在使用 SDK 其它功能前，必须先进行初始化。本文中详细说明 IM UIKit 初始化的方法。

::: note notice
- 如果您尚未集成过网易云信 NIM SDK，可采用本文方式初始化 IM UIKit。
- 如果您已集成过网易云信 NIM SDK，并且在自己的代码中拥有 NIM SDK 实例，请参考 [初始化（已集成 NIM SDK）](https://doc.yunxin.163.com/messaging-uikit/guide/zEyMDEyNDg?platform=web) 进行初始化。
:::

## 准备工作

根据本文操作前，请确保您已经完成了以下设置：

- [导入组件](https://doc.yunxin.163.com/messaging-uikit/guide/TM0ODQxMTM?platform=web)。
- [集成 IM UIKit](https://doc.yunxin.163.com/messaging-uikit/guide/zcwOTQzNTM?platform=web)
- [注册 IM 账号](https://doc.yunxin.163.com/messaging-uikit/guide/jEyNDg5NTU?platform=android#4-注册-im-账号)，获取账号 ID（`account_id`）和凭证（Token）。

## 注意事项

- 在应用生命周期内，只需初始化一次。
- Provider 内部管理 IM UIKit 与 IM 服务端的连接与断连。如果需要手动连接和断连，请参考 [登录登出](https://doc.yunxin.163.com/messaging-uikit/guide/DAxNTg1NjM?platform=web)。
- Provider 内部管理着全局的状态，一般无需开发者关心。如需访问上下文，请参考 [全局上下文](https://doc.yunxin.163.com/messaging-uikit/guide/TIzNDI0OTc?platform=web)。

## 参数说明

| 参数 | 类型 | 是否必选 | 说明 |
| :---- | :---- | :---- | :---- |
| `sdkVersion` | Number | 是 | 传入 `1` 或 `2` 选择基于哪个 IM SDK 集成 IM UIKit <br>`1`：基于 NIM Web SDK <br>`2`：基于 NIM Web SDK 的含圈组版（即 NIM Web Elite SDK）。 |
| `initOptions` | Object | 是 | NIM SDK 初始化参数。请参考 [NIM SDK 初始化参数说明](https://doc.yunxin.163.com/messaging-enhanced/references/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.NIMInitializeOptions.html)。 |
| `otherOptions` | Object | 否 | NIM SDK 初始化其他参数。请参考 [NIM SDK 其他初始化参数说明](https://doc.yunxin.163.com/messaging-enhanced/references/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.NIMOtherOptions.html)。 |
| `funcOptions` | Object | 否 | NIM SDK 初始化回调函数。请参考 [NIM SDK 初始化](https://doc.yunxin.163.com/messaging/guide/zE0NDY4Njc?platform=web)。 |
| `localeConfig` | Object | 否 | 自定义文案。详细配置参考 [语言设置](https://doc.yunxin.163.com/messaging-uikit/guide/jUxMDYxMTM?platform=web)。 |
| `renderImIdle` | () => JSX.Element | 否 | 连接前的渲染函数，不传默认为 null。 |
| `renderImConnecting` | () => JSX.Element | 否 | 连接中的渲染函数，不传默认为 <span>Loading……</span>。 |
| `renderImDisconnected` | () => JSX.Element | 否 | 连接断开时的渲染函数，不传默认为 <span>当前网络不可用，请检查网络设置。 |
| `localOptions` | Object | 否 | 本地默认行为参数。 |
    `p2pMsgReceiptVisible` | boolean | 否 | 是否需要显示单聊消息的已读和未读标记，默认 false。 |
    `teamMsgReceiptVisible`      | boolean | 否 | 是否需要显示群聊消息的已读和未读标记，默认 false。 |
    `iconfontUrl` | string\[] | 否 | 静态资源地址，9.8.6 及后续版本支持。该参数适用于私有化服务场景。 |
    `loginStateVisible` | boolean | 否 | 是否显示在线离线状态，默认 true。 |
    `allowTransferTeamOwner` | boolean | 否 | 是否允许群主转让，默认 false。 |
    `addFriendNeedVerify` | boolean | 否 | 添加好友是否需要对方确认，默认 true。 |
    `needMention` | boolean | 否 | 是否需要@消息提醒，默认 true。 |
    `teamManagerVisible` | boolean | 否 | 是否需要显示群管理员功能，默认 false（不显示）<br>该配置项用来控制当身份为管理员时的主动操作是否展示，不影响其他管理员身份的显示。若需要，可设置为 true。 |
    `sendMsgBefore` | function | 否 | 发送消息前的钩子函数，异步函数，可在发送消息前拿到消息体，向消息体中添加自定义参数。原型：`sendMsgBefore: <T = ISendCustomMsgOptions | IBaseSendFileOptions | ISendTextMsgOptions>(options: T) => Promise<T>;` <br>例如给消息加上推送相关参数，具体请参考以下示例。 |

<!--
| `leaveOnTransfer` | boolean | 否 | 转让群主身份的同时是否退出群聊，默认 false。 |
-->

- 给消息加上 **推送** 相关参数的示例代码如下，在 `localOptions` 中的 [`sendMsgBefore`](https://doc.yunxin.163.com/docs/interface/messaging/web/typedoc/UIKit/Latest/zh/interfaces/LocalOptions.html#sendMsgBefore) 中获取到发送前的消息体，在消息体上挂载相关参数：

    ```JavaScript
    // 本地默认行为参数
      const localOptions = {
        addFriendNeedVerify,
        sendMsgBefore:(options:any ) => {
          const pushInfo = {
            needPushNick: '',
            isPushable: true,
            pushContent: '',
            pushPayload: JSON.stringify({channel_id:'xxxxx'}),
            apns: {
              accounts:'',
              content: '',
              forcePush: '',
            },
          }
          options = {
            ...options,
            ...pushInfo
            }
          return options
        }
      }

    <Provider
        //...
        localOptions={localOptions}
      >
        <IMApp/>
      </Provider>
    ```

- 可以在发送消息时，设置将当前消息进行 **抄送**。在 [`sendMsgBefore`](https://doc.yunxin.163.com/docs/interface/messaging/web/typedoc/UIKit/Latest/zh/interfaces/LocalOptions.html#sendMsgBefore)进行配置，将 `env` 字段挂载在发送前的消息体上即可。

    ```JavaScript
    // 本地默认行为参数
      const localOptions = {
        addFriendNeedVerify,
        sendMsgBefore:(options, type) => {
          const env = 'xxxx'
          return { ...options, env }
        },
      }

    <Provider
        //...
        localOptions={localOptions}
      >
        <IMApp/>
      </Provider>
    ```

## 示例代码

```JavaScript
import React from 'react'
import { Provider } from '@xkit-yx/im-kit-ui'

const App = () => {
  const initOptions = {
    appkey: '', //传入您的 App Key
    account: '', // 传入您的网易云信 IM 账号
    token: '', // 传入您的 Token
    debugLevel: 'debug',//设置日志 level
    // 参考 NIM SDK 的 initOptions
  }

  return (
    <Provider initOptions={initOptions} sdkVersion={1}>
      <div className="app">……</div>
    </Provider>
  )
}
```