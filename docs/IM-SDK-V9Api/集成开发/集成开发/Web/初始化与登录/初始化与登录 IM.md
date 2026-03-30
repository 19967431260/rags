
集成 NIM SDK 之后，用户需要先调用 SDK 的初始化接口，初始化 SDK 并登录 IM。登录 IM 成功后，用户才能正常调用消息和会话等其他 SDK 接口。

本文介绍实现 IM 初始化和 IM 登录的流程以及相关的示例代码等。



::: note notice
如需初始化和登录**聊天室**，请参见[聊天室集成文档](https://doc.yunxin.163.com/messaging/guide/jgyODc1NDk?platform=web)。
:::

## 功能介绍


初始化的同时，NIM SDK 与云信服务端**建立长连接**（WebSocket 长连接），实现 IM 的**首次登录**。一旦登录成功后，NIM SDK 将接管所有的重连情况：在网络正常的情况下不停重试重连直到正常登录为止，并不需要做额外的登录操作。


初始化的模块主要包括：

- IM 消息
- 会话
- 用户资料
- 好友关系
- 用户关系
- 群组
- 超大群


## 使用限制

- **微信小程序 1.7.0 及以上**版本，**最多**可同时存在 **5** 条长连接和最多 **2** 条同域名的长连接。因此在使用多条长连接时，请务必控制连接数量。可通过销毁实例控制连接数量，具体参见[销毁 IM 实例](https://doc.yunxin.163.com/messaging/guide/jk2OTY1ODc?platform=web#销毁-im-实例)。

- 用户切换账号或者使用新的 IM 实例时，为保证不超过小程序的长连接数量限制，请务必先调用 IM 实例的`destroy`方法，并在`done`回调触发后再去发起新的连接。`destroy`方法的使用说明，参见[销毁 IM 实例](https://doc.yunxin.163.com/messaging/guide/jk2OTY1ODc?platform=web#销毁-im-实例)。


## 前提条件

- 已集成 SDK。
- 已在云信控制台[创建应用](https://doc.yunxin.163.com/console/concept/TIzMDE4NTA?platform=console)，获取 App Key 和 App Secret。
- 已[注册云信 IM 账号](https://doc.yunxin.163.com/messaging2/guide/jU0Mzg0MTU?platform=client#第二步注册-im-账号)，获取 accid 和 token。
- 已在云信控制台配置应用的 [IM 登录策略](https://doc.yunxin.163.com/messaging/guide/DIxMzI5Njk?platform=web#控制台配置)。如未配置相应的登录策略，可能导致后续调用登录接口时因无登录权限而报错（状态码：403）。
- （可选）已在控制台[配置客户端应用标识](https://doc.yunxin.163.com/console/concept/jU3MDY4Njk?platform=console)。


## 实现流程


### 步骤1：准备 Token


登录 IM 需要通过`token`进行鉴权。云信提供静态和动态这 2 种 `token` 类型，您可根据业务需求进行选择。

- 静态`token`：默认为永久有效。如有需要，可通过云信服务端 API [主动刷新 Token](https://doc.yunxin.163.com/messaging/guide/DUxNDQ3NjA?platform=server)。


- 动态`token`：具备时效性，可在生成时设置`token`的有效期。


#### 获取静态 Token

- 方式1：在控制台获取静态Token

    如果您只需要进行简单的**体验或者快速测试**，那么可以在云信控制台创建测试用的 IM 账号，并获取与该 IM 账号相应的**静态token**。具体参见[注册调试用的 IM 账号](https://doc.yunxin.163.com/messaging/guide/jMwMTQxODk?platform=android#注册-im-账号)。获取的静态token可用于下文提及的[静态 Token 登录](#静态Token登录)的鉴权。


- 方式2：调用服务端 API 获取静态Token


    如果您有正式的**生产环境**，且您的业务**仅需保障基础的用户信息安全**，那么需要通过云信 IM 服务端 API 注册 IM 账号，并获取与之相对应的**静态`token`**。具体参见[注册云信 IM 账号](https://doc.yunxin.163.com/messaging/guide/DQ3Nzk1MTY?platform=server)。获取的静态`token`可用于[静态 Token 登录](#静态-token-登录)的鉴权



#### 获取动态 Token

如果您有正式的**生产环境**，且您的业务**对用户信息安全有较高的要求**，可使用动态`token`。动态token可用于[动态 Token 登录](#动态-token-登录)的鉴权。

1. [注册云信 IM 账号](https://doc.yunxin.163.com/messaging/guide/DQ3Nzk1MTY?platform=server)，获取 IM 账号（`accid`）和静态`token`。

2. 基于App Key、App Secret 和`accid`，通过 [约定算法](https://doc.yunxin.163.com/messaging/server-apis/zE2NzA3Mjc?platform=server#动态-token-鉴权)在应用服务端生成**动态`token`**。



### 步骤2：初始化并登录


初始化 SDK 实例时，SDK 会同时与云信服务端建立连接，实现 IM 登录。默认的登录方式为**静态 Token 登录**。 


初始化方法为[`NIM.getInstance`](https://doc.yunxin.163.com/docs/interface/messaging/web/typedoc/Latest/zh/NIM/classes/nim.NIM.html#getInstance)。

::: note note 
`NIM.getInstance`方法为单例模式, 对于同一个账号, 永远返回同一个实例, 即只在第一次调用时初始化一个实例。后续调用该方法会直接返回初始化过的实例。如需更新初始化配置，不建议继续调用该方法，具体更新方法参见下文的[更新初始化配置](#更新初始化配置)。
:::


#### 登录方式概览


NIM SDK 登录方式分为静态 token 登录、动态 token 登录和通过第三方回调登录。您可按需实现**一种或多种**登录方式。



- 静态 Token 登录：采用[静态 Token 鉴权](https://doc.yunxin.163.com/messaging/guide/zE2NzA3Mjc?platform=server#静态token鉴权)  
- 动态 Token 登录：采用[动态 Token 鉴权](https://doc.yunxin.163.com/messaging/guide/zE2NzA3Mjc?platform=server#动态token鉴权) 
- 通过第三方回调登录：采用[通过第三方回调鉴权](https://doc.yunxin.163.com/messaging/guide/zE2NzA3Mjc?platform=server#基于第三方回调的鉴权) 




#### 静态 token 登录


如需实现静态 token 登录，调用[`NIM.getInstance`](https://doc.yunxin.163.com/docs/interface/messaging/web/typedoc/Latest/zh/NIM/classes/nim.NIM.html#getInstance)方法初始化 SDK 实例时，传入`account`、`appKey`和`token`这三个必传参数即可。



如果 NIM SDK 与云信服务端建立连接，将触发`onconnect`回调函数，表示登录 IM 成功。



以下仅列举了部分登录相关的初始化参数，**更多初始化参数说明，参见下文的[初始化参数](#初始化参数)**。

::: note note
如果您的应用主要服务于海外用户，需在初始化时进行出海配置。具体参见下文的[出海配置](#出海配置)。
:::

<div style="width:130px"> 参数</div> | 类型 |是否必传|  说明  
-------- | --- |------
`account` | string| 是| 用户的 IM 账号，即`accid` 
`appKey`| string | 是 | 当前应用的 App Key，一个 App Key 对应一个账号体系
`authType`|number | 否 | 登录 IM 的鉴权方式。采用静态`token`登录时，使用**默认的 0** 即可，即静态`token`鉴权
`token`| string | 是 | 获取到的静态`token`
`onconnect`| function | 否  |  NIM SDK 与云信服务端建立长连接后的回调函数<br>**若登录成功**，可通过该回调获取登录信息
`ondisconnect` | function   | 否   |  NIM SDK 与云信服务端的长连接断开后的回调函数<br>**若登录失败**，可通过该回调获取失败信息   


如下示例代码中的：

- `data`代表数据, 后续章节的示例代码中会多次用到该对象。
- `nim`代表 SDK 初始化后的 IM 实例，后续章节的示例代码中会多次用到该对象。

```
var data = {};
// 注意这里, 当引入的SDK文件是NIM_Web_NIM_v.js时，请通过 NIM.getInstance 来初始化；当引入的SDK文件为NIM_Web_SDK_v时，请使用 SDK.NIM.getInstance 来初始化。SDK文件的选择请参见集成方式。
var nim = NIM.getInstance({
  debug: true,   // 是否开启日志，将其打印到console。集成开发阶段建议打开。
  appKey: 'appKey', // 云信控制台获取的 App Key
  account: 'account', // 云信控制台获取或服务端注册的用户账号 accid
  token: 'token', // 云信控制台获取或服务端生成的静态 Token
  db:true, //若不要开启数据库请设置false。SDK默认为true。
  // privateConf: {}, // 私有化部署方案所需的配置
  onconnect: onConnect,
  onwillreconnect: onWillReconnect,
  ondisconnect: onDisconnect,
  onerror: onError
});
function onConnect() {
  console.log('连接成功');
}
function onWillReconnect(obj) {
  // 此时说明 SDK 已经断开连接, 请开发者在界面上提示用户连接已断开, 而且正在重新建立连接
  console.log('即将重连');
  console.log(obj.retryCount);
  console.log(obj.duration);
}
function onDisconnect(error) {
  // 此时说明 SDK 处于断开状态, 开发者此时应该根据错误码提示相应的错误信息, 并且跳转到登录页面
  console.log('丢失连接');
  console.log(error);
  if (error) {
    switch (error.code) {
      // 账号或者密码错误, 请跳转到登录页面并提示错误
      case 302:
        break;
      // 重复登录, 已经在其它端登录了, 请跳转到登录页面并提示错误
      case 417:
        break;
      // 被踢, 请提示错误后跳转到登录页面
      case 'kicked':
        break;
      default:
        break;
    }
  }
}
function onError(error) {
  console.log(error);
}


```


#### 动态 Token 登录




自 v8.3.0 版本起，NIM SDK 新增动态`token`登录这一登录方式。动态`token`具备时效性，可有效提升`token`破解难度，降低密码泄露风险。


1. 调用[`NIM.getInstance`](https://doc.yunxin.163.com/docs/interface/messaging/web/typedoc/Latest/zh/NIM/classes/nim.NIM.html#getInstance)方法初始化 SDK 实例并登录 IM 服务端。调用时，除了需要传入`account`、`appKey`和`token`这三个必传参数，**还需要将`authType`设置为 1**。


    如果 NIM SDK 与云信服务端建立连接，将触发`onconnect`回调函数，表示登录 IM 成功。


    以下仅列举了部分登录相关的初始化参数，**更多初始化参数说明，参见下文的[初始化参数](#初始化参数)**。

    ::: note note
    如果您的应用主要服务于海外用户，需在初始化时进行出海配置。具体参见下文的[出海配置](#出海配置)。
    :::

    参数 |类型| 是否必传|  说明  
    ----|---- | --- |------
    `account` | string | 是| 用户的 IM 账号，即`accid` 
    `authType` | number | 该登录方式必传 | **采用动态`token`登录时必须传入 1**，表示通过动态`token`鉴权，动态`token`[基于 App Secret 计算生成](https://doc.yunxin.163.com/messaging/guide/zE2NzA3Mjc?platform=server#动态token鉴权)
    `token`| string | 是 | [基于App Secret生成的动态Token](#获取动态token)  
    `appKey`| string  | 否 | 当前应用的 App Key，一个 App Key 对应一个账号体系
    `onconnect`| function | 否  |  NIM SDK 与云信服务端建立长连接后的回调函数<br>**若登录成功**，可通过该回调获取登录信息
    `ondisconnect` | function   | 否   |  NIM SDK 与云信服务端的长连接断开后的回调函数<br>**若登录失败**，可通过该回调获取失败信息
    `onwillreconnect` | function | 否  | NIM SDK 与云信服务端的长连接已断开，而且正在重连时触发的回调函数


2. 在`onwillreconnect`回调函数触发后，调用[`setOptions`](https://doc.yunxin.163.com/docs/interface/messaging/web/typedoc/Latest/zh/NIM/classes/nim.NIM.html#setOptions)方法更新动态`token`。




    ```
    // 动态token登录
    var nim = NIM.getInstance({
    debug: true, // 是否开启日志，将其打印到console。集成开发阶段建议打开。
    appKey: 'appKey', // 云信控制台获取的 App Key
    account: 'account', //  云信控制台获取或服务端注册的用户账号 accid
    token: 'token', // 服务端生成的动态 Token
    authType: 1, // 采用动态token登录
    onconnect: onConnect,
    onwillreconnect: onWillReconnect,
    ondisconnect: onDisconnect,
    onerror: onError
    })

    function onWillReconnect() {
    nim.setOptions({
        token: 'newToken' // 建议token生成逻辑在客户的服务器侧完成，以免AppSecret泄露。
    })
    }
    ```



#### 通过第三方回调登录


如采用该登录方式，**云信服务端不做 IM 登录鉴权**，鉴权工作需由指定的第三方服务器（可以是应用服务器）进行。

实现该登录方式，需完成如下 3 步操作：

1. 前往云信控制台，并进入**IM 即时通讯> 功能配置 > 第三方回调**配置第三方回调的环境地址（即第三方服务器地址）和回调失败时放行（通过）与否。


    ![第三方回调配置文案优化后.png](https://yx-web-nosdn.netease.im/common/3399fe2b490e47fb56cd6575faefa6d5/第三方回调配置文案优化后.png)


2. 调用[`NIM.getInstance`](https://doc.yunxin.163.com/docs/interface/messaging/web/typedoc/Latest/zh/NIM/classes/nim.NIM.html#getInstance)方法初始化 SDK 实例并登录 IM 服务端。调用时，除了需要传入`account`、`appKey`和`token`这三个必传参数，**还需传入`authType`必须传入 2，且必须传入`loginExt`**。
   


    如果 SDK 与云信服务端建立连接，将触发`onconnect`回调函数，表示登录 IM 成功。


    - 后续调该方法时, 如果连接已断开, SDK 会自动与云信服务端建立连接。
    - 当发生掉线时，SDK 会自动进行重连。

    以下仅列举了部分登录相关的初始化参数，**更多初始化参数说明，参见下文的[初始化参数](#初始化参数)**。

    ::: note note
    如果您的应用主要服务于海外用户，需在初始化时进行出海配置。具体参见下文的[出海配置](#出海配置)。
    :::


    <div style="width:130px">参数</div> |类型|是否必传|  说明  
    -----|--- | --- |------
    `appKey`| string  | 是 | 当前应用的 App Key，一个 App Key 对应一个账号体系
    `account` | string | 是| 用户的 IM 账号，即`accid` 
    `authType`| number | 该登录方式必传 | 登录 IM 的鉴权方式，采用该登录方式时必须传入 2，表示通过第三方回调进行鉴权
    `loginExt`| string  | 该登录方式必传 | 登录自定义扩展字段。采用该登录方式时，必须传入，用于第三方服务器鉴权。如未传入，将报错。长度上限为 1k 字符。
    `token` | string | 是 | 用户自定义 Token
    `onconnect`| function | 否  |  NIM SDK 与云信服务端建立长连接后的回调函数<br>**若登录成功**，可通过该回调获取登录信息
    `ondisconnect` | function   | 否   |  NIM SDK 与云信服务端的长连接断开后的回调函数<br>**若登录失败**，可通过该回调获取失败信息   


    ```
    // 通过第三方回调登录
    var nim = NIM.getInstance({
    debug: true, // 是否开启日志，将其打印到console。集成开发阶段建议打开。
    appKey: 'appKey', // 云信控制台获取的 App Key
    account: 'account', // 云信控制台获取或服务端注册的用户账号 accid
    token: 'token', // 用户自定义 Token
    authType: 2, // 通过第三方回调进行鉴权
    loginExt: 'loginExt', // 登录自定义扩展字段，采用该登录方式时必须传入
    onconnect: onConnect, // NIM SDK 与云信服务端建立长连接后的回调函数若登录成功，可通过该回调获取登录信息
    onwillreconnect: onWillReconnect,
    ondisconnect: onDisconnect, // NIM SDK 与云信服务端的长连接断开后的回调函数若登录失败，可通过该回调获取失败信息
    onerror: onError
    })
    ```



3. 发起[登录相关回调](https://doc.yunxin.163.com/messaging/guide/jc3MzA5NTk?platform=server)的请求，由第三方服务器进行鉴权并判定 IM 登录事件是否放行通过。

    若不通过，云信服务端将返回 302 错误码。




## 相关信息


### 示例代码

<details><summary><strong>较完整</strong>的初始化与登录的示例代码（仅以静态 token 登录为例）</summary>



如下示例代码中的：
- `data`代表数据, 后续章节的示例代码中会多次用到该对象。
- `nim`代表 SDK 初始化后的 IM 实例，后续章节的示例代码中会多次用到该对象。



```
    var data = {};
    var nim = NIM.getInstance({
        // 初始化SDK
        // debug: true
        appKey: 'appKey',
        account: 'account',
        token: 'token',
        customTag: 'TV',
        onconnect: onConnect,
        onerror: onError,
        onwillreconnect: onWillReconnect,
        ondisconnect: onDisconnect,
        // 多端登录
        onloginportschange: onLoginPortsChange,
        // 用户关系
        onblacklist: onBlacklist,
        onsyncmarkinblacklist: onMarkInBlacklist,
        onmutelist: onMutelist,
        onsyncmarkinmutelist: onMarkInMutelist,
        // 好友关系
        onfriends: onFriends,
        onsyncfriendaction: onSyncFriendAction,
        // 用户名片
        onmyinfo: onMyInfo,
        onupdatemyinfo: onUpdateMyInfo,
        onusers: onUsers,
        onupdateuser: onUpdateUser,
        // 群组
        onteams: onTeams,
        onsynccreateteam: onCreateTeam,
        onUpdateTeam: onUpdateTeam,
        // onsyncteammembersdone: onSyncTeamMembersDone,
        onupdateteammember: onUpdateTeamMember,
        // 群消息业务已读通知
        onTeamMsgReceipt: onTeamMsgReceipt,
        // 会话
        onsessions: onSessions,
        onupdatesession: onUpdateSession,
        // 消息
        onroamingmsgs: onRoamingMsgs,
        onofflinemsgs: onOfflineMsgs,
        onmsg: onMsg,
        // 系统通知
        onofflinesysmsgs: onOfflineSysMsgs,
        onsysmsg: onSysMsg,
        onupdatesysmsg: onUpdateSysMsg,
        onsysmsgunread: onSysMsgUnread,
        onupdatesysmsgunread: onUpdateSysMsgUnread,
        onofflinecustomsysmsgs: onOfflineCustomSysMsgs,
        oncustomsysmsg: onCustomSysMsg,
        // 收到广播消息
        onbroadcastmsg: onBroadcastMsg,
        onbroadcastmsgs: onBroadcastMsgs,
        // 同步完成
        onsyncdone: onSyncDone
    });

    function onConnect() {
        console.log('连接成功');
    }
    function onWillReconnect(obj) {
        // 此时说明 `SDK` 已经断开连接, 请开发者在界面上提示用户连接已断开, 而且正在重新建立连接
        console.log('即将重连');
        console.log(obj.retryCount);
        console.log(obj.duration);
    }
    function onDisconnect(error) {
        // 此时说明 `SDK` 处于断开状态, 开发者此时应该根据错误码提示相应的错误信息, 并且跳转到登录页面
        console.log('丢失连接');
        console.log(error);
        if (error) {
            switch (error.code) {
            // 账号或者密码错误, 请跳转到登录页面并提示错误
            case 302:
                break;
            // 被踢, 请提示错误后跳转到登录页面
            case 'kicked':
                break;
            default:
                break;
            }
        }
    }
    function onError(error) {
        console.log(error);
    }

    function onLoginPortsChange(loginPorts) {
        console.log('当前登录账号在其它端的状态发生改变了', loginPorts);
    }

    function onBlacklist(blacklist) {
        console.log('收到黑名单', blacklist);
        data.blacklist = nim.mergeRelations(data.blacklist, blacklist);
        data.blacklist = nim.cutRelations(data.blacklist, blacklist.invalid);
        refreshBlacklistUI();
    }
    function onMarkInBlacklist(obj) {
        console.log(obj);
        console.log(obj.account + '被你在其它端' + (obj.isAdd ? '加入' : '移除') + '黑名单');
        if (obj.isAdd) {
            addToBlacklist(obj);
        } else {
            removeFromBlacklist(obj);
        }
    }
    function addToBlacklist(obj) {
        data.blacklist = nim.mergeRelations(data.blacklist, obj.record);
        refreshBlacklistUI();
    }
    function removeFromBlacklist(obj) {
        data.blacklist = nim.cutRelations(data.blacklist, obj.record);
        refreshBlacklistUI();
    }
    function refreshBlacklistUI() {
        // 刷新界面
    }
    function onMutelist(mutelist) {
        console.log('收到静音列表', mutelist);
        data.mutelist = nim.mergeRelations(data.mutelist, mutelist);
        data.mutelist = nim.cutRelations(data.mutelist, mutelist.invalid);
        refreshMutelistUI();
    }
    function onMarkInMutelist(obj) {
        console.log(obj);
        console.log(obj.account + '被你' + (obj.isAdd ? '加入' : '移除') + '静音列表');
        if (obj.isAdd) {
            addToMutelist(obj);
        } else {
            removeFromMutelist(obj);
        }
    }
    function addToMutelist(obj) {
        data.mutelist = nim.mergeRelations(data.mutelist, obj.record);
        refreshMutelistUI();
    }
    function removeFromMutelist(obj) {
        data.mutelist = nim.cutRelations(data.mutelist, obj.record);
        refreshMutelistUI();
    }
    function refreshMutelistUI() {
        // 刷新界面
    }

    function onFriends(friends) {
        console.log('收到好友列表', friends);
        data.friends = nim.mergeFriends(data.friends, friends);
        data.friends = nim.cutFriends(data.friends, friends.invalid);
        refreshFriendsUI();
    }
    function onSyncFriendAction(obj) {
        console.log(obj);
        switch (obj.type) {
        case 'addFriend':
            console.log('你在其它端直接加了一个好友' + obj.account + ', 附言' + obj.ps);
            onAddFriend(obj.friend);
            break;
        case 'applyFriend':
            console.log('你在其它端申请加了一个好友' + obj.account + ', 附言' + obj.ps);
            break;
        case 'passFriendApply':
            console.log('你在其它端通过了一个好友申请' + obj.account + ', 附言' + obj.ps);
            onAddFriend(obj.friend);
            break;
        case 'rejectFriendApply':
            console.log('你在其它端拒绝了一个好友申请' + obj.account + ', 附言' + obj.ps);
            break;
        case 'deleteFriend':
            console.log('你在其它端删了一个好友' + obj.account);
            onDeleteFriend(obj.account);
            break;
        case 'updateFriend':
            console.log('你在其它端更新了一个好友', obj.friend);
            onUpdateFriend(obj.friend);
            break;
        }
    }
    function onAddFriend(friend) {
        data.friends = nim.mergeFriends(data.friends, friend);
        refreshFriendsUI();
    }
    function onDeleteFriend(account) {
        data.friends = nim.cutFriendsByAccounts(data.friends, account);
        refreshFriendsUI();
    }
    function onUpdateFriend(friend) {
        data.friends = nim.mergeFriends(data.friends, friend);
        refreshFriendsUI();
    }
    function refreshFriendsUI() {
        // 刷新界面
    }

    function onMyInfo(user) {
        console.log('收到我的名片', user);
        data.myInfo = user;
        updateMyInfoUI();
    }
    function onUpdateMyInfo(user) {
        console.log('我的名片更新了', user);
        data.myInfo = NIM.util.merge(data.myInfo, user);
        updateMyInfoUI();
    }
    function updateMyInfoUI() {
        // 刷新界面
    }
    function onUsers(users) {
        console.log('收到用户名片列表', users);
        data.users = nim.mergeUsers(data.users, users);
    }
    function onUpdateUser(user) {
        console.log('用户名片更新了', user);
        data.users = nim.mergeUsers(data.users, user);
    }
    function onTeams(teams) {
        console.log('群列表', teams);
        data.teams = nim.mergeTeams(data.teams, teams);
        onInvalidTeams(teams.invalid);
    }
    function onInvalidTeams(teams) {
        data.teams = nim.cutTeams(data.teams, teams);
        data.invalidTeams = nim.mergeTeams(data.invalidTeams, teams);
        refreshTeamsUI();
    }
    function onCreateTeam(team) {
        console.log('你创建了一个群', team);
        data.teams = nim.mergeTeams(data.teams, team);
        refreshTeamsUI();
    }
    function refreshTeamsUI() {
        // 刷新界面
    }
    // function onSyncTeamMembersDone() {
    //     console.log('同步群列表完成');
    // }
    function onUpdateTeam (team) {
        console.log('群状态更新', team)
    }
    function onUpdateTeamMember(teamMember) {
        console.log('群成员信息更新了', teamMember);
    }
    function refreshTeamMembersUI() {
        // 刷新界面
    }
    function onTeamMsgReceipt (teamMsgReceipts) {
        console.log('群消息已读通知', teamMsgReceipts)
    }

    function onSessions(sessions) {
        console.log('收到会话列表', sessions);
        data.sessions = nim.mergeSessions(data.sessions, sessions);
        updateSessionsUI();
    }
    function onUpdateSession(session) {
        console.log('会话更新了', session);
        data.sessions = nim.mergeSessions(data.sessions, session);
        updateSessionsUI();
    }
    function updateSessionsUI() {
        // 刷新界面
    }

    function onRoamingMsgs(obj) {
        console.log('漫游消息', obj);
        pushMsg(obj.msgs);
    }
    function onOfflineMsgs(obj) {
        console.log('离线消息', obj);
        pushMsg(obj.msgs);
    }
    function onMsg(msg) {
        console.log('收到消息', msg.scene, msg.type, msg);
        pushMsg(msg);
    }
    function onBroadcastMsg(msg) {
        console.log('收到广播消息', msg);
    }
    function onBroadcastMsgs(msgs) {
        console.log('收到广播消息列表', msgs);
    }
    function pushMsg(msgs) {
        if (!Array.isArray(msgs)) { msgs = [msgs]; }
        var sessionId = msgs[0].sessionId;
        data.msgs = data.msgs || {};
        data.msgs[sessionId] = nim.mergeMsgs(data.msgs[sessionId], msgs);
    }

    function onOfflineSysMsgs(sysMsgs) {
        console.log('收到离线系统通知', sysMsgs);
        pushSysMsgs(sysMsgs);
    }
    function onSysMsg(sysMsg) {
        console.log('收到系统通知', sysMsg)
        pushSysMsgs(sysMsg);
    }
    function onUpdateSysMsg(sysMsg) {
        pushSysMsgs(sysMsg);
    }
    function pushSysMsgs(sysMsgs) {
        data.sysMsgs = nim.mergeSysMsgs(data.sysMsgs, sysMsgs);
        refreshSysMsgsUI();
    }
    function onSysMsgUnread(obj) {
        console.log('收到系统通知未读数', obj);
        data.sysMsgUnread = obj;
        refreshSysMsgsUI();
    }
    function onUpdateSysMsgUnread(obj) {
        console.log('系统通知未读数更新了', obj);
        data.sysMsgUnread = obj;
        refreshSysMsgsUI();
    }
    function refreshSysMsgsUI() {
        // 刷新界面
    }
    function onOfflineCustomSysMsgs(sysMsgs) {
        console.log('收到离线自定义系统通知', sysMsgs);
    }
    function onCustomSysMsg(sysMsg) {
        console.log('收到自定义系统通知', sysMsg);
    }

    function onSyncDone() {
        console.log('同步完成');
    }
```
</details>

### <span id="更新初始化配置">更新 IM 初始化配置</span>


可调用[`setOptions`](https://doc.yunxin.163.com/docs/interface/messaging/web/typedoc/Latest/zh/NIM/classes/nim.NIM.html#setOptions)方法更新原 SDK 实例的初始化配置，可配置的参数与`NIM.getInstance`方法可配置的参数相同，具体见下文的[初始化参数](#初始化参数)。


以更新静态 token 为例：

```javascript
// 断开 IM
nim.disconnect();
// 更新 token
nim.setOptions({
    token: 'newToken'
});
// 重新连接
nim.connect();
```




### 出海配置




配置项 | 说明
---- | --------------
海外数据中心  | 如果你的应用主要服务于海外用户，且数据需要写入海外数据中心，请先在云信控制台[选择服务区域](https://doc.yunxin.163.com/messaging/guide/TMyMjUxOTI?platform=web#创建应用并选择服务区域)为海外，并在调用[`NIM.getInstance`](https://doc.yunxin.163.com/docs/interface/messaging/web/typedoc/Latest/zh/NIM/classes/nim.NIM.html#getInstance)方法进行首次初始化时，配置私有化服务器地址中的 LBS 和 link 域名相关信息。配置详情请参见[配置 LBS 和 Link 域名](https://doc.yunxin.163.com/messaging/guide/TMyMjUxOTI?platform=web#web-端)
融合存储  |  NIM SDK 默认使用 NOS 做文件存储。若开发者服务的对象是在海外，那么可以通过 SDK 来选择 S3 做融合存储。使用融合存储需要依赖 s3 的 SDK 文件，为了减小 NIM SDK 体积所以需要用户在自己的项目中引入 S3 SDK 并在初始化 IM 时注入，否则无法开启融合存储功能。具体如何开启融合存储，请参考[融合存储方案](https://doc.yunxin.163.com/messaging/guide/TgzMjg3Mzg?platform=web)



  

### 多端登录与互踢


当前 NIM SDK 支持配置四种不同的 IM 多端登录与互踢策略，具体参见[多端登录与互踢](https://doc.yunxin.163.com/messaging/guide/jIxMjczMzk?platform=web)





### 初始化参数



<details><summary><b>点击查看初始化配置说明</b></summary></summary>
<br>
初始化配置在 NIMGetInstanceOptions 中定义， 初始化配置可分为如下几类：
<ul>
<li><a href="#登录初始化参数">登录初始化参数</a></li><li><a href="#系统通知初始化参数">系统通知初始化参数</a></li><li><a href="#数据同步配置">数据同步配置</a></li><li><a href="#数据库配置">数据库配置</a></li>
<li><a href="#日志配置">日志配置</a></li><li><a href="#消息初始化参数">消息初始化参数</a></li><li><a href="#消息扩展配置">消息扩展配置</a></li>
<li><a href="#会话初始化参数">会话初始化参数</a></li>
<li><a href="#NOS云存储参数">NOS云存储参数</a></li>
<li><a href="#群组初始化参数">群组初始化参数</a></li>
<li><a href="#超大群初始化参数">超大群初始化参数</a></li>
<li><a href="#用户资料初始化参数">用户资料初始化参数</a></li>
<li><a href="#用户关系初始化参数">用户关系初始化参数</a></li>
</ul>

<span id="登录初始化参数"><b>登录初始化参数</b></span>

<div style="width:160px">参数</div> | <div style="width:90px">类型</div> | 是否必传 |说明
---- | -------------- | ---------
`account` | string | 是 | IM 账号（即`accid`）
`appKey` | string |  是  | 应用的 App Key，在云信控制台创建应用后获取
`authType`| number | 否  | IM 登录的鉴权方式，默认为 0 <ul><li>0：通过静态`token`鉴权，token 恒定不变，除非主动[调用服务端 API 刷新](https://doc.yunxin.163.com/messaging/guide/DUxNDQ3NjA?platform=server)</li><li>1：通过动态`token`鉴权，动态`token`[基于 App Secret 生成](https://doc.yunxin.163.com/messaging/guide/zE2NzA3Mjc?platform=server#动态token鉴权)，可在生成时指定动态`token`的过期时间</li><li>2：通过[第三方回调](https://doc.yunxin.163.com/messaging/guide/jI3ODc2ODE?platform=server)，由开发者指定的第三方服务器进行 IM 登录的鉴权，云信服务端仅负责在收到 IM 登录请求后将登录信息转发至开发者服务器，并返回第三方服务器的鉴权结果</li></ul>
`token`  | string  | 否 |验证用户身份的令牌，只会在建立连接时校验一次
`loginExt` | string | 否  | 登录自定义扩展字段，可转发给指定的第三方服务器，不会同步至其他端。长度上限为 1k 字符。<b>`authType`为 2，即通过第三方回调进行 IM 登录鉴权时，必须传入</b>，用于第三方服务器鉴权。
`customClientType` | string | 否 | 自定义客户端类型，请设置大于 0 的整数<note type=note>默认端类型只有 Web，PC，android，iOS，如果开发者需要加以更细致的类型区分，如微信小程序等环境，可用这个字段自行做映射。</note>
`needReconnect` | boolean | 否 |是否开启自动重连，默认 true，即如果长连接因为网络问题、心跳超时等原因断开，NIM SDK 默认自动尝试重连  <note type=note>重连的时间间隔从 1.6～8s 之间累加，每次重连将触发`onwillreconnect`事件</note>
`quickReconnect`| boolean  | 否 | 是否开启快速自动重连，默认 false。若设置为 true，NIM SDK 会监听浏览器的 offline 和 online 事件来嗅探网络断开和恢复，将会做相应的断开和重连策略<note type=notice>只有当 `needReconnect`为 true 时该配置才有效。</note>
`reconnectionAttempts` |number | 否 |NIM SDK 尝试重连的最大次数。达到最大重连次数后将不再重连，并触发`ondisconnect`回调，表示连接彻底断开
`customTag` | string | 否 | 客户端自定义 tag。最大 32 个字符
`defaultLink` | string  | 否  | 默认的备用长连接地址。当 LBS 请求出错时，NIM SDK 会尝试该长连接地址，若不传此参数，默认使用云信的公网的备用地址。</note>
`lbsUrl`| string | 否  | 默认的 LBS 地址。NIM SDK 需要先请求 LBS 地址能得到长连接地址，再建立长连接。若不传此参数，默认将使用云信提供的公网地址。</note>
`lbsBackup`   | boolean |  否  |是否开启备用 LBS 地址，默认为 true，即 NIM SDK 会将上一次连接成功过的 LBS 地址存储到浏览器本地缓存作为备用，当主 LBS 不可用时，会尝试请求备用 LBS 地址连接
`lbsBackupUrlsCustomer` | string[] | 否  | 自定义的备用 LBS 地址数组，用于自定义接口去代理 LBS 返回，防止运营商劫持。当主 LBS 不可用且浏览器本地缓存的备用 LBS 地址均不可用时，NIM SDK 会尝试请求自定义的备用 LBS 。示例：`['https://address1', 'https://address2']`
`onconnect`| function | - |NIM SDK 与云信服务端建立长连接后的回调函数，原型:`onconnect(data: NIMOnConnectResult): void`
`ondisconnect` | function | - | NIM SDK 与云信服务端的长连接断开后的回调函数，原型：`ondisconnect(data: NIMOnDisconnectResult): void`
`onwillreconnect` | function | - | 即将重连时触发的回调函数。如果触发，说明 NIM SDK 已与云信服务端断开连接，建议在界面上提示用户：连接已断开，正在重新建立连接
`onerror` | function | - | 出现错误的回调，这里的“错误”通常为数据库错误，也可能是连接错误
`onpushevents` | function  | - |用户在线或初始化同步时，用于接收下推的事件服务的回调函数。原型：`onpushevents(result: { msgEvents: NIMPushEventInfo[] }): void`
`onsyncdone` | function  | - | 初始化同步完成的回调函数。**推荐**在初始化同步完成后再调用 SDK 实例的接口
`onloginportschange`| function  | - | 多端登录状态变化的回调函数，用户可通过该回调函数获取登录端列表。原型：`onloginportschange(datas: NIMOnLoginPortsChangeResult[]): void`。以下情况会触发该回调函数：<ul><li>登录时已有其它设备端在线</li><li>登录后其他设备端上线或下线</li></ul>

<span id="系统通知初始化参数"><b>系统通知初始化参数</b></span>


<div style="width:160px">参数</div> | <div style="width:90px">类型</div> | 是否必传 |说明
---- | -------------- | ---------
`onsysmsg`| function  |- | 用于在线时接收系统通知的回调函数。原型：`onsysmsg(data: NIMSystemMessage): void`
`onupdatesysmsg` | function | - |用于在线时接收系统通知更新的回调函数。触发的条件包括通过或拒绝好友申请、接收或拒绝入群申请，以及通过或者拒绝入群邀请。原型：`onupdatesysmsg(data: NIMSystemMessage): void`
`oncustomsysmsg`| function | -| 用户在线时，用于接收自定义系统通知的回调函数。原型：`oncustomsysmsg(data: NIMSystemMessage): void`<note type=notice>自定义系统消息不存本地数据库，NIM SDK 直接将自定义系统通知回调透传给上层应用。</note>
`onofflinecustomsysmsgs`| function | - | 初始化同步时，用于接收离线的自定义系统通知的回调函数。原型：`onofflinecustomsysmsgs(datas: NIMSystemMessage[]): void`<note type=notice>自定义系统消息不存本地数据库，NIM SDK 直接将自定义系统通知回调透传给上层应用。</note>
`onofflinesysmsgs` | function| - | 初始化同步时，用于接收离线的系统通知的回调函数。原型：`onofflinesysmsgs(datas: NIMSystemMessage[]): void`
`onroamingsysmsgs` | function | - | 初始化同步时，用于接收漫游系统通知的回调函数。原型：`onroamingsysmsgs(datas: NIMSystemMessage[]): void`
`onsysmsgunread` | function | - | 用于在初始化同步时接收系统通知未读数的回调函数。原型：`onsysmsgunread(data: NIMSystemMessageUnreadInfo): void`<note type=notice>该函数获取的是设备端本地维护的未读数，只统计本次登录期间内接收到的未读数。</note>
`onupdatesysmsgunread` | function | - | 用于在线时接收系统通知未读数变更。原型：`onupdatesysmsgunread(data: NIMSystemMessageUnreadInfo): void` <note type=notice>该函数获取的是设备端本地维护的未读数，只统计本次登录期间内接收到的未读数。</note>

<span id="数据同步配置"><b>数据同步配置</b></span>

<div style="width:160px">参数</div> | <div style="width:90px">类型</div> | 是否必传 |说明
---- | -------------- | ---------
`syncBroadcastMsgs`| boolean | 否 |是否同步离线广播，默认 false。若同步，初始化同步结束后收到 `onbroadcastmsgs` 回调
`syncExtraTeamInfo`|  boolean  | 否 |  是否同步额外的群信息, 默认 true。若同步，则初始化同步接收群列表的额外信息，结束后收到 onteams 回调<note type=note>这里的“额外信息”举个例子，当前登录用户开启某个群的消息提醒 (SDK 只是存储了此信息, 具体用此信息来做什么事情完全由开发者控制)，开发者调用接口 updateInfoInTeam 来设置。</note>
`syncFriendUsers`| boolean  | 否  |  是否同步好友对应的用户名片列表, 默认 true。若同步，则初始化同步接收好友所对应的用户信息，结束后收到 onusers 回调
`syncFriends`| boolean  |   否  |  是否同步好友列表, 默认 true。若同步，则初始化同步接收好友信息，结束后收到 onfriends 回调
`syncMsgReceipts` |   boolean  | 否  |  是否同步已读回执时间戳, 默认 true
`syncRelations` | boolean  | 否   |  是否同步黑名单和静音列表, 默认true。若同步，则初始化同步接收黑名单和静音列表，结束后收到 onblacklist 回调和 onmutelist 回调
`syncRoamingMsgs`| boolean | 否  |是否同步漫游消息, 默认 true。若同步，则初始化同步结束后收到 onroamingmsgs 回调
`syncSessionUnread`|  boolean | 否  |  是否同步会话的未读数, 默认 false。未读数即会话（`session`）的 `unread` 属性
`syncStickTopSessions`| boolean  | 否   |  是否同步云端置顶会话信息，默认 false。初始化同步云端置顶会话信息可以通过 onStickTopSessions 回调获取，且附带在 session 定义的 isTop 属性中
`syncSuperTeamRoamingMsgs` | boolean | 否 |  是否额外同步超大群的漫游消息, 默认 true。若同步，则初始化同步结束后收到 onroamingmsgs 回调
`syncSuperTeams` | boolean | 否 | 是否同步超大群列表, 默认true。若同步，则初始化同步接收超级群列表，结束后收到 onSuperTeams 回调
`syncTeams` | boolean  | 否 | 是否同步群列表, 默认 true。若同步，则初始化同步接收群列表，结束后收到 onteams 回调








<span id="数据库配置"><b>数据库配置</b></span>


<div style="width:160px">参数</div> | <div style="width:90px">类型</div> | 是否必传 |说明
---- | -------------- | ---------
`db` | boolean | 否  | 是否使用 IM 业务数据库（采用 indexedDb），默认 true。在移动端的 safari 浏览器中，使用 SDK 操作数据库时存在一些异常问题，因此 SDK 在移动端 safari 上禁用了数据库。<strong>建议移动端浏览器使用 Web SDK 时默认不开启数据库，在初始化时将`db`设置为 false</strong><note type=note>在支持数据库的浏览器上，SDK 会将消息、会话、群组等数据缓存到 indexedDB 数据库中, 后续同步都是增量更新, 加快初始化同步速度。</note>
`dbLog` | boolean | 否 | 是否将日志存储到本地数据库，默认 true，即默认将日志存储到本地数据库。后续如需拉取本地数据库中的日志，请联系云信技术支持 <note type=note>日志数据库与 IM 业务数据库为两个数据库，互不影响</note>

<span id="日志配置"><b>日志配置</b></span>
<div style="width:160px">参数</div> | <div style="width:90px">类型</div> | 是否必传 |说明
---- | -------------- | ---------
`logLevel`| `"debug" | "log" | "info" | "warn" | "error" | "off"` | 否 | 日志级别，<b>默认 off，即不输出任何日志</b>。设置对应的日志等级后，仅输出高于或等于对应等级的日志
`expire` | number  | 否 | 本地数据库中的日志的有效期，单位：小时，默认 72 小时，<b>仅在`dbLog`为 true 时生效</b>
`logFunc` | function  | - | 是否对日志做额外的处理，诸如日志存储、日志上报等等，该函数会截获`console`日志的参数。原型：`logFunc(...args: (string | NIMStrAnyObj)[]): void`





<span id="消息初始化参数"><b>消息初始化参数</b></span>




<div style="width:160px">参数</div> | <div style="width:90px">类型</div> | 是否必传 |说明
---- | -------------- | ---------
`onmsg` | function  |- | 用户在线或多端同步时，用于接收消息的回调函数。原型：`onmsg(data: NIMMessage): void`
`onofflinemsgs`| function | - | 初始化同步时，用于接收离线消息的回调函数。原型：`onofflinemsgs(datas: NIMMessage[]): void`
`onDeleteMsgSelf`|   function  | - |  多端同步时消息单向删除的回调函数，原型：`onDeleteMsgSelf(data: NIMOnDeleteMsgSelfResult): void
`onbroadcastmsg` | function |- |用户在线时，用于接收广播消息的回调函数。原型：`onbroadcastmsg(data: NIMBroadcastMessage): void`
`onbroadcastmsgs`  |function |  -| 初始化同步时，用于接收广播消息的回调函数。原型：`onbroadcastmsgs(datas: NIMBroadcastMessage[]): void`
`onroamingmsgs` | function | - | 初始化同步时，用于接收漫游消息的回调函数。原型：`onroamingmsgs(datas: NIMMessage[]): void`<note type=notice>初始化同步会触发多次这个事件，每一个会话触发一次。</note>
`onMsgReceipts`|function|-|在线时，P2P消息标记已读回执的回调函数。




<span id="消息扩展配置"><b>消息扩展配置</b></span>


<div style="width:160px">参数</div> | <div style="width:90px">类型</div> | 是否必传 |说明
---- | -------------- | ---------
`onQuickComment`| function  | -| 在线或多端同步时，添加快捷评论的回调函数，原型：`onQuickComment(data: Pick<NIMMessage, "scene" | "from" | "time" | "idServer" | "idClient">, comment: NIMQuickComment): void`
`onDeleteQuickComment`|  function | - | 在线或多端同步时，删除快捷评论的回调函数，原型：`onDeleteQuickComment(data: Pick<NIMMessage, "scene" | "from" | "time" | "idServer" | "idClient">, comment: NIMQuickComment): void`
`onPinMsgChange`|   function  |- |  在线或多端同步时，更新 PIN 消息的回调函数，原型：`onPinMsgChange(data: NIMOnPinMsgChangeResult, action: "add" | "update" | "delete"): void`


<span id="会话初始化参数"><b>会话初始化参数</b></span>

<div style="width:160px">参数</div> | <div style="width:90px">类型</div> | 是否必传 |说明
---- | -------------- | ---------
`autoMarkRead` | boolean | 否 | 是否自动标记消息为已收到，默认为 true
`resetUnreadMode` |boolean| 否|  重置会话未读数时，若同步至服务器失败，是否仅重置本地会话未读数，默认 true，即本地未读数会被重置，服务端和其他端的未读数不会重置；若为 false，则本地、服务器和其他端都不会被重置（重置失败），各端未读数会保持一致 
`rollbackClearMsgsUnread`| boolean | 否 | 清除会话的消息时是否同时更新会话的未读数与最近一条消息，默认 true
`rollbackDelMsgUnread`| boolean|  否  |  撤回消息后是否更新该消息所属会话的未读数，默认 false。例子：假设某会话有两条消息未读，其中一条消息被撤回了，此时如果该参数为 true，则会话未读数变为 1，否则未读数仍是 2
`shouldCountNotifyUnread` | function | 否 | 钩子函数，用于判定通知消息是否计入会话未读数。默认都返回 false。接收一条通知消息，如果该函数结果返回 true，则该通知消息计入未读数，否则不计入未读数。原型：`shouldCountNotifyUnread(notification: NIMMessage): void`
`shouldIgnoreNotification` | function | 否 | 钩子函数，用于判定接收到通知消息时是否不更新会话。默认都返回 false。如过返回 true，则将该通知消息计入未读数，否则不计入。原型：`shouldIgnoreNotification(notification: NIMMessage): void`
`onsessions` | function  | - | 初始化同步时，用于获取会话列表的回调函数。原型：`onsessions(datas: NIMSession[]): void`
`onClearServerHistoryMsgs` | function | -|多端同步或初始化同步时监听会话历史消息的清除事件，需传入被删除的会话的 ID（`sessionId`以及删除时间），原型：`onClearServerHistoryMsgs(data: { sessionId: string; time: number }): void`
`onSessionsWithMoreRoaming`| function | -| 初始化同步时，如果会话仍有更多的漫游消息，将触发该回调函数，原型：`onSessionsWithMoreRoaming(datas: NIMSession[]): void`<note type=notice>其中的 `session.time` 之前的时间里，仍有超过漫游数量限制而为未漫游下来的消息。可在进入会话时，通过获取历史消息接口再拉取消息</font>
`onStickTopSessions` | function | -| 初始化同步或在线时，远端会话置顶的回调函数，原型：`onStickTopSessions(datas: NIMSession[]): void`
`onSyncUpdateServerSession`| function | -| 多端同步时，服务端会话更新的回调函数，原型：`onSyncUpdateServerSession(data: NIMCloudSession): void`
`onupdatesessions` | function | - | 批量更新会话的回调函数。触发条件包括收发消息、清理会话未读数、撤回消息等。原型：`onupdatesessions(datas: NIMSession[]): void`<note type=note>v8.2.0 版本开始支持该回调函数</note>


<span id="NOS云存储参数"><b>NOS云存储参数</b></span>

<div style="width:160px">参数</div> | <div style="width:90px">类型</div> | 是否必传 |说明
---- | -------------- | ---------
`nosScenes` |string  |否 | 上传文件存储全局配置-存储场景<note type=note>相当于使用的网易云存储的桶名，默认 “im”。</note>
`nosSurvivalTime`| number| 否   |上传文件存储全局配置-存储有效时间<note type=note>默认 Infinity，设置的时间不得小于一天，单位：秒。</note>





<span id="群组初始化参数"><b>群组初始化参数</b></span>

<div style="width:160px">参数</div> | <div style="width:90px">类型</div> | 是否必传 |说明
---- | -------------- | ---------
`onteams` | function | - | 用于在初始化同步时获取群列表的回调函数。原型：`onteams(datas: NIMTeam[]): void`
`onCreateTeam`| function | -| 在线或多端同步时，创建群组的回调函数，通过该回调函数监听“创建群的通知”，原型：`onCreateTeam(data: NIMTeam): void`
`onDismissTeam`| funciton  |- |  在线或多端同步时，解散群组的回调函数，通过该回调函数监听“解散群的通知”，原型：`onDismissTeam(data: { teamId: string }): void`
`onupdateteammember` | function | - | 用于在线或多端同步时接收群成员信息变更的回调函数。 原型：`onupdateteammember(data: Pick<NIMTeamMember, "custom" | "teamId" | "updateTime" | "account" | "id" | "muteNotiType" | "muteTeam" | "nickInTeam">): void`
`onRemoveTeamMembers`| function |-| 在线或多端同步时，删除群成员的回调函数，通过该回调函数接收删除群成员的通知，原型：`onRemoveTeamMembers(data: NIMOnRemoveTeamMembersResult): void`  <note type="notice">您需要判定`data`里 `account` 是否包含当前 IM 账号, 来处理本账号被踢出群的情况。</note>
`onTeamMsgReceipt` | function | -| 在线时，群消息标记已读回执的回调函数，原型：`onTeamMsgReceipt(data: NIMOnTeamMsgReceiptResult): void`
`onTransferTeam` | function | -|转让群的回调函数，用于在用户在线或多端同步时，接收转让群的通知。原型： `onTransferTeam(data: NIMOnTransferTeamResult): void`
`onUpdateTeam` | function | - | 更新群的回调函数，用户在在线或多端同步时，通过该回调函数接收更新群的通知。原型：`onUpdateTeam(data: Pick<NIMTeam, "custom" | "announcement" | "avatar" | "intro" | "name" | "teamId" | "updateTime">): void`
`onUpdateTeamManagers` | function | - | 更新群管理员的回调函数，用户在线或多端同步时，通过该回调函数接收更新群管理员的通知。原型：`onUpdateTeamManagers(data: NIMOnUpdateTeamManagersResult): void
`onUpdateTeamMembersMute` | function | - | 群成员被禁言的回调函数，用户在线或多端同步时，通过该回调函数接收群成员被禁言的通知。原型：`onUpdateTeamMembersMute(data: NIMOnUpdateTeamMembersMuteResult): void`
`onsynccreateteam`| function | - |用于在多端同步时接收创建群的通知的回调函数。原型：`onsynccreateteam(data: NIMTeam): void`。该回调函数触发后，将触发`onCreateTeam`
`onMyTeamMembers`|function|-|获取自己在所有高级群中的用户信息的回调函数。

<span id="超大群初始化参数"><b>超大群初始化参数</b></span>

<div style="width:160px">参数</div> | <div style="width:90px">类型</div> | 是否必传 |说明
---- | -------------- | ---------
`onSuperTeams?:function` | function | -| 初始化同步时，获取超大群列表的回调函数，原型：`onSuperTeams(datas: NIMSuperTeam[]): void`
`onSyncCreateSuperTeam`| function  | -  | 多端同步时，获取创建超大群的通知的回调函数，原型：`onSyncCreateSuperTeam(datas: NIMSuperTeam[]): void`
`onAddSuperTeamMembers`| function |- |在线或多端同步时监听“添加超大群成员的通知”，原型：`onAddSuperTeamMembers(data: NIMOnAddSuperTeamMembersResult): void`
`onDismissSuperTeam` | function | - | 在线或多端同步时，超大群解散的回调函数，通过该回调函数监听“超大群解散的通知”，原型：`onDismissSuperTeam(data: { teamId: string }): void`
`onRemoveSuperTeamMembers`| function | -| 在线或多端同步时，删除超大群成员的回调函数，通过该回调函数接收删除超大群成员的通知，原型：`onRemoveSuperTeamMembers(data: NIMOnRemoveSuperTeamMembersResult): void`<note type=notice>您需要判定`data`里 `account` 是否包含当前的 IM 账号, 来处理当前 IM 账号被踢出群的情况</note>
`onTransferSuperTeam`  | function | - | 在线或多端同步时，转让超大群的回调函数，通过该回调函数获取超大群转让的通知，原型：`onTransferSuperTeam(data: NIMOnTransferSuperTeamResult): void`
`onUpdateSuperTeam` | function  | - | 更新超大群的回调函数，用于在用户在线或多端同步时接收更新超大群信息的通知。原型：`onUpdateSuperTeam(data: Pick<NIMSuperTeam, "custom" | "announcement" | "avatar" | "intro" | "name" | "teamId" | "updateTime">): void`
`onUpdateSuperTeamManagers`| function  | -| 更新超大群管理员的回调函数，用于在用户在线或多端同步时接收更新超大群管理员的通知。原型：`onUpdateSuperTeamManagers(data: NIMOnUpdateSuperTeamManagersResult): void`
`onUpdateSuperTeamMembersMute`  | function  | - | 超大群成员被禁言的回调函数，用户可在在线或多端同步时接收超大群成员被禁言的通知。原型：`onUpdateSuperTeamMembersMute(data: NIMOnUpdateSuperTeamMembersMuteResult): void`
`onMySuperTeamMembers`|function|-|获取自己在所有超大群中的用户信息的回调函数。

<span id="用户资料初始化参数"><b>用户资料初始化参数</b></span>



<div style="width:160px">参数</div> | <div style="width:90px">类型</div> | 是否必传 |说明
---- | -------------- | ---------
`onusers` | function | - | 回调函数，用于初始化同步时获取好友的用户名片。原型：`onusers(datas: NIMUserNameCard[]): void`
`onblacklist`| function | -|初始化同步时，用于获取黑名单列表的回调函数。原型：`onblacklist(datas: NIMMarkedUserInfo[]): void`
`onmyinfo`|function | - | 初始化同步时，用于用户获得自己的用户名称。原型：`onmyinfo(data: NIMUserNameCard): void`
`onupdatemyinfo` | function |- | 用于在多端同步时获取当前用户自己的用户名片更新的回调函数。原型：`onupdatemyinfo(data: NIMUserNameCard): void`
`onupdateuser`| function | - | 用于在线接收消息后，获取聊天对象的用户名片信息更新的回调函数。原型：`onupdateuser(data: NIMUserNameCard): void`

<span id="用户关系初始化参数"><b>用户关系初始化参数</b></span>

<div style="width:160px">参数</div> | <div style="width:90px">类型</div> | 是否必传 |说明
---- | -------------- | ---------
`onfriends` | function | - | 同步好友列表的回调, 会传入好友列表。原型：`onfriends(datas: NIMFriendProfile[]): void`
`onmutelist`| function| - | 用于在初始化同步时接收静音用户列表的回调函数。原型：`onmutelist(datas: NIMMarkedUserInfo[]): void`
`onsyncfriendaction` | function | - | 用于在多端同步时获取好友动作（如添加好友、好友申请、拒绝好友申请等）的回调函数。原型：`onsyncfriendaction(data: NIMOnSyncFriendActionResult): void`
`onsyncmarkinblacklist`|function |  - | 用于在多端同步时接收拉黑/移出黑名单事件的回调函数。原型：`onsyncmarkinblacklist(data: NIMMarkedUserResult): void`
`onsyncmarkinmutelist`| function | - | 用于在多端同步时接收“静音某个用户”事件的回调函数。原型：`onsyncmarkinmutelist(data: NIMMarkedUserResult): void`



</details>

















<!--
### <span id="私有化部署">私有化部署</span>

若用户选用云信私有化部署方案，则需额外考虑以下配置：
- `privateConf` 使用新配置，即引入改配置项即可
- 使用旧私有化配置，需要额外配置以下参数：
  - `secure` 链接安全配置，默认为`true`，即对应的lbs为`https://`，websocket为`wss://`，若将此配置为`false`，则对应的lbs为`http://`，对应的websocket为`ws://`
  - `lbsUrl` 云信SDK首先会从lbsUrl中获取对应可用的socket通道地址，若客户采用私有化方案，需要配置该属性
  - `uploadUrl` 私有化部署方案中需要上传的url地址
  - `downloadUrl` 私有化部署方案通配符的下载url地址，若拿到一个`bucket`:"nim",`object`:"pic" ，那么上传得到的地址是 http(s)://nos.netease.com/nim/pic，那么无论是本地还是传给对面，都是这个域名。

配置示例：
``` javascript
// 新配置
var nim = NIM.getInstance({
    privateConf: { // 该配置可从管理后台生成并下载得到
        lbs_web: 'http://*.*.*.*:*/lbs/webconf.jsp',
        link_ssl_web: false, // 是否使用wss
        nos_uploader_web: '', // nos上传地址
        https_enabled: false,
        nos_downloader: '*.*.*.*:*/{bucket}/{object}',
        nos_accelerate: '', // nos加速地址
        nos_accelerate_host: '',
        nt_server: '' // 日志上报接口
    }
});
// 旧配置
var nim = NIM.getInstance({
    secure: false,
    lbsUrl: 'http://xxx.xxx.xxx',
    uploadUrl: 'http://xxx.yyy.xxx',
    downloadUrl: 'http://xxx.zzz.xxx/{bucket}/{object}'
});
```
**注意，downloadUrl中的{bucket}与{object}为固定通配符，请照抄**
在私有化环境中，对应的下载链接及图片链接地址，均需要通过工具方法`viewImageSync`转换，详见[预览图片通用方法](https://doc.yunxin.163.com/messaging/guide/TU1OTM4NzE?platform=web#预览图片通用方法)

-->








