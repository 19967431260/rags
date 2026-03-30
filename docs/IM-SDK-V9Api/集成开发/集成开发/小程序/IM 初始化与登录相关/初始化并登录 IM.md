
本文提供小程序环境下， NIM 实例初始化以及登录 IM 的详细说明。






## 前提条件




开始前，请确保：

- 已[集成 SDK](https://doc.yunxin.163.com/messaging/guide/jUwODczMzI?platform=miniProgram)。
- 已在云信控制台[创建应用](https://doc.yunxin.163.com/console/docs/TIzMDE4NTA?platform=console)，获取 App Key。
- 已[配置 IM 登录策略](https://doc.yunxin.163.com/messaging/concept/TE3MTMyMTY?platform=miniProgram#控制台配置)。如未配置相应的登录策略，可能导致后续调用登录接口时因无登录权限而报错（状态码：403）。

## 实现流程


### 步骤1：准备 Token


登录 IM 需要通过`token`进行鉴权。云信提供静态和动态这 2 种 `token` 类型，您可根据业务需求进行选择。

- 静态`token`：默认为永久有效。如有需要，可通过云信服务端 API [主动刷新 Token](https://doc.yunxin.163.com/messaging/guide/DUxNDQ3NjA?platform=server)。


- 动态`token`：具备时效性，可在生成时设置`token`的有效期。


#### 获取静态Token

- 方式1：在控制台获取静态Token

    如果您只需要进行简单的**体验或者快速测试**，那么可以在云信控制台创建测试用的 IM 账号，并获取与该 IM 账号相应的**静态`token`**。具体参见[注册调试用的 IM 账号](https://doc.yunxin.163.com/messaging-enhanced/guide/TYzNjAzMDU?platform=web#4-注册-im-账号)。获取的静态token可用于下文提及的**静态 Token 登录**的鉴权。

- 方式2：调用服务端 API 获取静态Token


    如果您有正式的**生产环境**，且您的业务**仅需保障基础的用户信息安全**，那么需要通过云信 IM 服务端 API 注册 IM 账号，并获取与之相对应的**静态`token`**。具体参见[注册云信 IM 账号](https://doc.yunxin.163.com/messaging/guide/DQ3Nzk1MTY?platform=server)。获取的静态`token`可用于[静态 Token 登录](#静态-token-登录)的鉴权



#### 获取动态Token

如果您有正式的**生产环境**，且您的业务**对用户信息安全有较高的要求**，可使用动态`token`。动态token可用于动态 Token 登录的鉴权。

1. [注册云信 IM 账号](https://doc.yunxin.163.com/messaging/guide/DQ3Nzk1MTY?platform=server)，获取 IM 账号（`accid`）和静态`token`。

2. 基于App Key、App Secret 和`accid`，通过[约定算法](https://doc.yunxin.163.com/TM5MzM5Njk/docs/zE2NzA3Mjc?platform=server#动态token鉴权)在应用服务端生成**动态`token`**。


### 步骤2：初始化并登录

<!-- 目前登录方式是在初始化时配的， 这点与移动端的逻辑不一致，后续增强版 Web 的接口逻辑应该会调整 -->



开始初始化前，需明确应用采用的 IM 登录方式。不同的登录方式，初始化配置有所差异。 


  
:::::: div custom-tabs


::: tab 静态 token 登录

1. 创建 NIM 实例，同时配置初始化参数和初始化同步数据，并注册 NIM 实例事件。


    v0.11.0 之前，通过 new 创建 NIM 实例。v0.11.0 开始，通过调用[`getInstance`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.NIMInterfaceStatic.html#getInstance) 方法创建 NIM 实例（单例模式）。

    - 必传参数
    
    
      
      无论是通过 new 还是 `getInstance` 创建 NIM 实例，采用静态 token 登录时，都需传入如下参数。



      参数 | 类型 | 描述
      ---- | -------------- | ---------
      `appKey`  | string   |  当前应用的 App Key，一个 App Key 对应一个账号体系
      `account` | string  | 用户的 IM 账号，即 accid 
      `token` | string   |  获取到的静态 token 

      初始化可选参数及事件说明，参见下文的 [NIM 初始化参数与事件](#nim-初始化参数与事件)。

    
    
    - 初始化同步配置

      创建 NIM 实例时，需配置 NIM 实例需要从云信服务端同步哪些数据。具体配置项，参见[`SyncOptions`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/modules/src_NIMInterface.html#SyncOptions)。    
    
    


2. 调用[`connect`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.NIMInterface.html#connect)方法建立 SDK 与云信服务端的长连接，登录 IM。 

    NIM 实例在建立长连接后会发起同步操作，从云信服务端同步漫游消息、离线消息、好友关系等。同步过程中将触发对应的事件，具体参见文末的[同步过程事件](#同步过程事件)同步完成后触发[`syncdone`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.IMEventInterface.html#syncdone)事件。
<br>




示例代码：


```
import NIMSDK from 'nim-web-sdk-ng/dist/NIM_MINIAPP_SDK

// 创建实例
const nim = NIMSDK.getInstance({
  appkey: 'YOUR_APPKEY',
  account: 'YOUR_ACCID',
  token: 'YOUR_TOKEN',
  debugLevel: 'debug',
  lbsUrls: [
    "https://lbs.netease.im/lbs/wxwebconf.jsp"
  ],
  linkUrl: "wlnimsc0.netease.im"
});

const eventList = [
  'logined',
  
  'multiPortLogin',

  'kicked',

  'willReconnect',

  'disconnect',

  'msg',

  'syncdone',

  'proxyMsg', 'syncRoamingMsgs', 'syncOfflineMsgs',
  'syncMyNameCard', 'syncdone', 'sessions', 'updateMyNameCard', 'updateBlackList', 'updateMuteList',
  'sysMsg', 'syncSysMsgs', 'syncFriend', 'friends', 'users', 'updateSystemMessages', 'sysMsgUnread', 'pushEvents',
  'msgReceipts', 'teamMsgReceipts', 'updateSession',
  
  'teams', 'myTeamMembers',
  'createTeam',
  'updateTeamMember',
  'updateTeam', 'addTeamMembers', 'updateTeamManagers', 'transferTeam', 'removeTeamMembers', 'dismissTeam', 'updateTeamMembersMute',
]

eventList.forEach((key: any) => {
  nim.on(key, (res) => {
    console.log(`Receive ${key} event：`, res ? JSON.parse(JSON.stringify(res)) : res);
  });
})

// then，receive event 'logined'
await nim.connect();

```

:::

::: tab 动态 token 登录




1. 创建 NIM 实例，同时配置初始化参数并注册 NIM 实例事件。


    v0.11.0 之前，通过 new 创建 NIM 实例。v0.11.0 开始，通过调用[`getInstance`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.NIMInterfaceStatic.html#getInstance) 方法创建 NIM 实例（单例模式）。



    - 必传参数

      无论是通过 new 还是 `getInstance` 创建 NIM 实例，采用动态 token 登录时，都需传入如下参数。


      参数 | 类型 | 描述
      ---- | -------------- | ---------
      `appKey`  | string   |  当前应用的 App Key，一个 App Key 对应一个账号体系
      `account` | string  | 用户的 IM 账号，即 accid 
      `authType` | number  |  **采用动态`token`登录时必须传入 1**，表示通过动态`token`鉴权，动态`token`[基于 App Secret 计算生成](https://doc.yunxin.163.com/messaging/guide/zE2NzA3Mjc?platform=server#动态token鉴权)
      `token` | string   |  获取到的动态 token 


      初始化可选参数及事件说明，参见下文的 [NIM 初始化参数与事件](#nim-初始化参数与事件)。


    - 初始化同步配置



      创建 NIM 实例时，需配置 NIM 实例需要从云信服务端同步哪些数据。具体配置项，参见[`SyncOptions`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/modules/src_NIMInterface.html#SyncOptions)。






2. 调用[`connect`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.NIMInterface.html#connect)方法建立 SDK 与云信服务端的长连接，登录 IM。 


    NIM 实例在建立长连接后会发起同步操作，从云信服务端同步漫游消息、离线消息、好友关系等。同步完成后触发[`syncdone`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.IMEventInterface.html#syncdone)事件。
<br>





:::



::: tab 通过第三方回调登录

如采用该登录方式，**云信服务端不做 IM 登录鉴权**，鉴权工作需由指定的第三方服务器（可以是应用服务器）进行。

实现该登录方式，需完成如下操作：

1. 实现该登录方式，需提前[开通和配置第三方回调服务](https://doc.yunxin.163.com/messaging/guide/jI3ODc2ODE?platform=server#开通和配置第三方回调)。


2. 创建 NIM 实例，同时配置初始化参数并注册 NIM 实例事件。


    v0.11.0 之前，通过 new 创建 NIM 实例。v0.11.0 开始，通过调用[`getInstance`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.NIMInterfaceStatic.html#getInstance) 方法创建 NIM 实例（单例模式）。

    - 必传参数


      无论是通过 new 还是 `getInstance` 创建 NIM 实例，通过第三方回调登录时，都需传入如下参数。



      参数 | 类型 | 描述
      ---- | -------------- | ---------
      `appKey`  | string   |  当前应用的 App Key，一个 App Key 对应一个账号体系
      `account` | string  | 用户的 IM 账号，即 accid 
      `authType` | number  | 登录 IM 的鉴权方式，采用该登录方式时必须传入 2，表示通过第三方回调进行鉴权
      `token` | string   |  获取到的 token 

      初始化可选参数及事件说明，参见下文的 [NIM 初始化参数与事件](#nim-初始化参数与事件)。


    - 初始化同步配置



      创建 NIM 实例时，需配置 NIM 实例需要从云信服务端同步哪些数据。具体配置项，参见[`SyncOptions`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/modules/src_NIMInterface.html#SyncOptions)。





3. 调用[`connect`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.NIMInterface.html#connect)方法建立 SDK 与云信服务端的长连接，登录 IM。 


    NIM 实例在建立长连接后会发起同步操作，从云信服务端同步漫游消息、离线消息、好友关系等。同步完成后触发[`syncdone`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.IMEventInterface.html#syncdone)事件。




4. 发起[登录相关回调](https://doc.yunxin.163.com/messaging/guide/jc3MzA5NTk?platform=server)的请求，由第三方服务器进行鉴权并判定 IM 登录事件是否放行通过。

    若不通过，云信服务端将返回 302 错误码。

:::

::::::







::: note notice 
事件必须在调用 `connect` 方法前声明才会生效，声明方式可以参考示例代码中 `eventList` 里的内容。
:::



















## 注意事项


- 如需配置[初始化参数`lbsUrls`](#IM-登录相关)，请确保只传入一个固定的 LBS 地址。因为实例在小程序环境中运行，会受上文的域名白名单限制，无法使用动态 LBS 服务动态调配长连接地址。


- 微信小程序 1.7.0 及以上版本，最多可同时存在 5 条 WebSocket 连接，其中同域名的 WebSocket 连接最多 2 条。
  如需在切换账号或聊天室时使用新实例，为保证不超过WebSocket 连接限制，**请务必**先调用 NIM / Chatroom 实例的 `destroy` 方法，并在 `promise` 完成后以后再去创建新的实例。

- 微信小程序初始化时必须设置 LBS 地址，以及默认的连接地址。示例代码如下：

  ```
  import NIMSDK from 'nim-web-sdk-ng/dist/NIM_MINIAPP_SDK

  const nim = new NIMSDK({
    appkey: "YOUR_APPKEY",
    token: "YOUR_TOKEN",
    account: "YOUR_ACCOUNT",
    lbsUrls: [
      "https://lbs.netease.im/lbs/wxwebconf.jsp"
    ],
    linkUrl: "wlnimsc0.netease.im"
  })
  ```


::: note note
更多相关限制信息和已知问题，请参见[已知问题及处理建议](https://doc.yunxin.163.com/messaging/guide/Dk5MzQyOTM?platform=miniProgram)。
:::



## 相关信息

### 同步过程事件


同步过程中会触发如下事件：



事件 | 对应回调
---- | --------------
关系（包括黑名单列表和静音列表）| [`relations`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.IMEventInterface.html#relations)
好友|  [`friends`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.IMEventInterface.html#friends)
我的名片  |  [`syncMyNameCard`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.IMEventInterface.html#syncMyNameCard)
好友的名片  |  [`users`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.IMEventInterface.html#users)
群  |  [`teams`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.IMEventInterface.html#teams)
会话  |  [`sessions`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.IMEventInterface.html#sessions)
漫游消息  |  [`syncRoamingMsgs`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.IMEventInterface.html#syncRoamingMsgs)
离线消息  |  [`syncOfflineMsgs`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.IMEventInterface.html#syncOfflineMsgs)
离线系统通知  |  [`syncSysMsgs`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.IMEventInterface.html#syncSysMsgs)






### 更新 NIM 初始化配置


可调用[`setOptions`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.NIMInterface.html#setOptions)方法更新原 SDK 实例的初始化配置，具体参数见下文的[NIM 初始化参数与事件](#nim-初始化参数与事件)。



### 断网重连机制

SDK 提供了自动重连机制（自动重新建立与云信服务器的连接并重新登录），即将进入重连逻辑会触发事件 `willReconnect`。

SDK 在两种场景下会自动进行重连：

* 手动/自动登录成功后，网络不佳导致链接断开的情况。
* 网络不佳时，账号密码本身正常（未被封禁，且账号密码均正确），启动App时调用自动登录接口的情况。

满足上述中一个条件，当用户遇到普通网络问题如连接超时等，会自动进行重连登录，不需要应用上层去做额外的重登逻辑。

```js
nim.on('disconnect', function (obj) {
  console.log('已断开连接', obj)
})

nim.on('willReconnect', function (obj) {
  console.log('收到了重连事件', obj)
})
```

### 多端登录与互踢


当前 NIM SDK 支持配置四种不同的 IM 多端登录与互踢策略，具体参见[多端登录与互踢](https://doc.yunxin.163.com/messaging/guide/DU2MTQ4NDM?platform=miniProgram)。



### NIM 初始化参数与事件



<details><summary>点击查看初始化参数与回调</summary>


- [IM 登录相关](#IM-登录相关)
- [SDK 日志相关](#SDK-日志相关)
- [消息相关](#消息相关)
- [系统通知相关](#系统通知相关)
- [会话相关](#会话相关)
- [群组相关](#群组相关)
- [超大群相关](#超大群相关)
- [用户资料相关](#用户资料相关)
- [好友关系相关](#好友关系相关)
- [事件订阅相关](#事件订阅相关)


<span id="IM-登录相关"><strong>IM 登录相关</strong></span>


<div style="width:160px">参数/事件</div> | <div style="width:90px">类型</div> | 是否必传 |说明
---- | -------------- | ------|---
`account` | string | 是 | IM 账号（即`accid`）
`appKey` | string |  是  | 应用的 App Key，在云信控制台创建应用后获取
`token`  | string  | 是 |校验用户身份的令牌，分为静态 token 和动态 token 两种，只会在建立连接时校验一次
`authType`| number | 否  | IM 登录的鉴权方式，默认为 0 <ul><li>0：通过静态`token`鉴权，token 恒定不变，除非主动[调用服务端 API 刷新](https://doc.yunxin.163.com/messaging/guide/DUxNDQ3NjA?platform=server)</li><li>1：通过动态`token`鉴权，动态`token`[基于 App Secret 生成](https://doc.yunxin.163.com/messaging/guide/zE2NzA3Mjc?platform=server#动态token鉴权)，可在生成时指定动态`token`的过期时间</li><li>2：通过[第三方回调](https://doc.yunxin.163.com/messaging/guide/jI3ODc2ODE?platform=server)，由开发者指定的第三方服务器进行 IM 登录的鉴权，云信服务端仅负责在收到 IM 登录请求后将登录信息转发至开发者服务器，并返回第三方服务器的鉴权结果</li></ul>
`customClientType` | number | 否 | 自定义客户端类型，请设置大于 0 的整数<note type=note>默认端类型只有 Web，PC，android，iOS，如果开发者需要加以更细致的类型区分，如微信小程序等环境，可用这个字段自行做映射。</note>
`needReconnect` | boolean | 否 |是否开启自动重连，默认 true，即如果长连接因为网络问题、心跳超时等原因断开，NIM SDK 默认自动尝试重连  <note type=note>重连的时间间隔从 1.6～8s 之间累加，每次重连将触发`onwillreconnect`事件</note>
`reconnectionAttempts` |boolean | 否 |NIM SDK 尝试重连的最大次数。达到最大重连次数后将不再重连，并触发`ondisconnect`回调，表示连接彻底断开
`lbsUrls`| string[] | 否  | LBS 地址。NIM SDK 需要先请求 LBS 地址，再建立长连接（WebSocket 连接）。若不传此参数，默认将使用云信提供的公网地址。<note type=note>为了防止 LBS 链接被网络运营商劫持，开发者可以传入自己代理的地址做备份，示例：`['https://address1', 'https://address2']`</note><note type=important>实例在小程序环境中运行，会受上文的域名白名单限制，无法使用动态的基于位置的 LBS 服务自动调配长连接地址，所以只能使用一个固定的 LBS 地址。</note>
`linkUrl` |  string | 否 |  WebSocket 备用地址，当 LBS 请求失败时，尝试直接连接 WebSocket 备用地址<note type=note>优先级最高的是 LBS 地址下发的 WebSocket 连接地址， 次为开发者在此填的 WebSocket 备用地址（如果不填这个字段， SDK 会有内部默认的备用地址）</note>
`isFixedDeviceId`  | boolean | 否  | 是否需要固定设备 ID，默认 false<ul><li>true：SDK 随机对设备生成一个设备标识并存入 localstorage 缓存起来，即对于一个浏览器来说，所有建立 SDK 实例与云信服务端之间的长连接的设备都被认为是相同的设备</li><li>false：每一个 SDK 实例连接时，使用随机的字符串作为设备标识，即每个 SDK 实例通过不同的设备建立长连接</li></ul>
[`logined`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.IMEventInterface.html#logined) | -|  -  |   IM 登录成功的事件  
[`disconnect`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.IMEventInterface.html#disconnect) | -   | -| NIM 实例与云信服务端断开长连接的事件
[`willReconnect`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.IMEventInterface.html#willReconnect)| - |  -|  即将自动重连的事件
[`kicked`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.IMEventInterface.html#kicked)   |  - | -  |   被使用相同 IM 账号（accid）登录的其他设备端踢下线的事件
[`multiPortLogin`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.IMEventInterface.html#multiPortLogin)  | -  | -| 多个设备端使用相同 IM 账号（accid）登录的事件
[`syncdone`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.IMEventInterface.html#syncdone) | - | -|  从云信服务端同步数据完成的事件

<span id="SDK-日志相关"><strong>SDK 日志相关</strong></span>



<div style="width:160px">参数</div> | <div style="width:90px">类型</div> | 是否必传 |说明
---- | -------------- | ------|---
`debugLevel`   | string   | 否  | <ul><li>off：关闭日志</li><li>error：最高，只打印 error 级别的日志</li><li>warn：打印 error 和 warn 级别的日志</li><li>log：打印 error、warn、log 级别的日志</li><li>debug：最低，打印 error、warn、log 和 debug 级别的日志</li></ul>




<span id="消息相关"><strong>消息相关</strong></span>


事件 |说明
---- | -------------- 
[`msg`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.IMEventInterface.html#msg) |  在线消息到达事件   
[`syncOfflineMsgs`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.IMEventInterface.html#syncOfflineMsgs) |  初始化时从云信服务端同步离线消息的事件
[`syncRoamingMsgs`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.IMEventInterface.html#syncRoamingMsgs)  | 初始化时从云信服务端同步漫游消息的事件
[`broadcastMsgs`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.IMEventInterface.html#broadcastMsgs) |  广播消息到达事件的事件（在线或者离线同步收到均会触发）
[`clearServerHistoryMsgs`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.IMEventInterface.html#clearServerHistoryMsgs)| 清除历史消息的事件（初始化同步或多端同步触发）
[`deleteSelfMsgs`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.IMEventInterface.html#deleteSelfMsgs)  |  单向删除某条消息的事件  
[`proxyMsg`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.IMEventInterface.html#proxyMsg)  | 代理消息（透传的）到达事件的事件 
[`msgReceipts`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.IMEventInterface.html#msgReceipts)|消息已读事件，包括单聊和群聊消息

<span id="系统通知相关"><strong>系统通知相关</strong></span>


事件 |说明
---- | -------------- 
[`syncSysMsgs`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.IMEventInterface.html#syncSysMsgs) | 初始化时从云信服务端同步漫游/离线系统的事件
[`sysMsg`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.IMEventInterface.html#sysMsg) | 在线系统通知到达事件的事件
[`updateSystemMessages`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.IMEventInterface.html#updateSystemMessages)  |  系统通知更新的事件

<span id="会话相关"><strong>会话相关</strong></span>




事件 |说明
---- | -------------- 
[`sessions`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.IMEventInterface.html#sessions)  | 初始化时从云信服务端同步会话的事件
[`updateSession`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.IMEventInterface.html#updateSession)  |  会话更新的事件




<span id="群组相关"><strong>群组相关</strong></span>



事件 |说明
---- | -------------- 
[`teams`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.IMEventInterface.html#teams) | 初始化时从云信服务端同步群组的事件
[`createTeam`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.IMEventInterface.html#createTeam)  | 创建群组的事件
[`addTeamMembers`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.IMEventInterface.html#addTeamMembers)  | 添加群成员的事件
[`dismissTeam`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.IMEventInterface.html#dismissTeam)  | 群组解散的事件
[`removeTeamMembers`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.IMEventInterface.html#removeTeamMembers)  |  成员离群的事件，例如成员 A 调用了 leaveTeam 离群，其他成员会收到这个事件
[`teamMsgReceipts`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.IMEventInterface.html#teamMsgReceipts) | 接收端到群消息已读回执的事件
[`transferTeam`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.IMEventInterface.html#transferTeam) | 群组转让的事件
[`updateTeam`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.IMEventInterface.html#updateTeam)  |   群组信息更新的事件
[`updateTeamManagers`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.IMEventInterface.html#updateTeamManagers)  | 群管理更新的事件
[`updateTeamMember`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.IMEventInterface.html#updateTeamMember)  |   群成员更新的事件
[`updateTeamMembersMute`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.IMEventInterface.html#updateTeamMembersMute)  |  群成员静音列表更新的事件
[`myTeamMembers`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.IMEventInterface.html#myTeamMembers)|当前账户所在的所有高级群中的成员信息变更的事件

<span id="超大群相关"><strong>超大群相关</strong></span>


事件 |说明
---- | -------------- 
[`superTeams`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.IMEventInterface.html#superTeams)  | 超大群初始化同步的事件
[`addSuperTeamMembers`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.IMEventInterface.html#addSuperTeamMembers)  | 添加超大群成员的事件
[`removeSuperTeamMembers`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.IMEventInterface.html#removeSuperTeamMembers)   | 移除超大群成员的事件
[`dismissSuperTeam`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.IMEventInterface.html#dismissSuperTeam)   |   超大群解散的事件
[`transferSuperTeam`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.IMEventInterface.html#transferSuperTeam) | 超大群转让的事件
[`updateSuperTeam`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.IMEventInterface.html#updateSuperTeam)  |  超大群更新的事件
[`updateSuperTeamManagers`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.IMEventInterface.html#updateSuperTeamManagers)   |  超大群管理员更新的事件
[`updateSuperTeamMember`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.IMEventInterface.html#updateSuperTeamMember)  | 超大群成员更新的事件
[`updateSuperTeamMembersMute`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.IMEventInterface.html#updateSuperTeamMembersMute)  | 超大群成员静列表更新的事件
[`mySuperTeamMembers`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.IMEventInterface.html#mySuperTeamMembers)|当前账户所在的所有超大群中的成员信息变更的事件


<span id="用户资料相关"><strong>用户资料相关</strong></span>



事件 |说明
---- | -------------- 
[`syncMyNameCard`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.IMEventInterface.html#syncMyNameCard)  |   初始化时从云信服务端同步个人资料的事件
[`users`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.IMEventInterface.html#users)       |   初始化时从云信服务端同步其他用户相关资料的事件
[`updateMyNameCard`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.IMEventInterface.html#updateMyNameCard) | 个人资料更新的事件


<span id="好友关系相关"><strong>好友关系相关</strong></span>



事件 |说明
---- | -------------- 
[`syncFriend`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.IMEventInterface.html#syncFriend)   | 好友相关资料进行多端同步的事件
[`friends`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.IMEventInterface.html#friends) | 好友资料初始化同步的事件
[`relations`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.IMEventInterface.html#relations) |  黑名单或静音列表初始化同步的事件
[`updateBlackList`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.IMEventInterface.html#updateBlackList) | 黑名单更新的事件
[`updateMuteList`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.IMEventInterface.html#updateMuteList) | 静音列表更新的事件



<span id="事件订阅相关"><strong>事件订阅相关</strong></span>




事件 |  说明
----- |------
[`pushEvents`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.IMEventInterface.html#pushEvents) | 订阅事件的事件




</details>

