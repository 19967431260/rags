音视频呼叫（呼叫组件）提供一套包含 UI 的接入方式。本文概要性介绍业务数据能力层的接口。

## API 概览

方法/属性 | 描述
--- | ---
[`initConfig`](#initConfig) | 初始化接口。需要在功能使用之前，进行初始化。
[`login`](#login) | 登录接口。如果在初始化接口中传入账号信息，则不需要再进行单独登录。
[`logout`](#logout) | 登出接口。
[`toCallPage`](#toCallPage) | 拨打通话。
[`addEventListener`](#addEventListener) | 注册监听。监听通话的状态，例如：异常、通话开始、结束等事件。

<style>
table th:first-of-type {width: 20%;}
table th:nth-of-type(2) {width: 20%;}
table th:nth-of-type(3) {width: 20%;}
table th:nth-of-type(4) {width: 40%;}
</style>

### initConfig

**接口描述**

初始化音视频通话（呼叫组件）。

**参数说明**

```JavaScript
initConfig({params}, callback(ret))
```

参数名称 | 类型 | 是否必填 | 说明
--- | --- | --- | ---
`params` | Object | 是 | 初始化配置参数。 |
 `appKey` | String | 是 | 网易云信 IM 应用的 AppKey，获取方式请参考 [创建应用并获取 AppKey](https://doc.yunxin.163.com/console/concept/TIzMDE4NTA?platform=console)。
 `account` | String | 是 | 账号 ID，获取方法请参考 [注册 IM 账号](https://doc.yunxin.163.com/messaging2/guide/jU0Mzg0MTU?platform=client#第二步注册-im-账号)。
 `token` | String | 是 | 账号 Token，获取方法请参考 [注册 IM 账号](https://doc.yunxin.163.com/messaging2/guide/jU0Mzg0MTU?platform=client#第二步注册-im-账号)。
 `rtcUid` | Number | 否 | 网易云信 RTC Uid。
 `apnsCername` | String | 否 | 网易云信 Apns 推送证书名称。
 `pkCername` | String | 否 | 网易云信 PushKit 推送证书名称。
 `language` | String | 否 | 语言，zh 为中文，en 为英文，不填默认跟随系统。
 `enableFloatingWindow` | Bool | 否 | 是否开启悬浮窗，true 开启，false 不开启。
 `enableAutoFloatingWindowWhenHome` | Bool | 否 | 是否开启回到桌面自动开启悬浮窗，true 开启，false 不开启。
 `enableForegroundService` | Bool | 否 | 是否开启前台服务，true 开启，false 不开启。
 `enableAudio2Video` | Bool | 否 | 是否显示语音转视频的按钮，true 开启，false 不开启，默认显示。
 `enableVideo2Audio` | Bool | 否 | 是否显示视频转语音的按钮，true 开启，false 不开启，默认显示。
 `audio2VideoConfirm` | Bool | 否 | 是否开启语音转视频的时候需要同意，true 开启，false 不开启，默认不开启。
 `video2AudioConfirm` | Bool | 否 | 是否开启视频转语音的时候需要同意，true 开启，false 不开启，默认不开启。
`callback` | Object | 是 | 回调函数。
 `ret` | Object | 是 | 回调信息。
  `code` | Number | 是 | 状态码。
  `message` | String | 是 | 错误信息。

**示例代码**

```JavaScript
demo.initConfig({
    appKey: "appkey123456789",
    account: "123456789",
    token: "123456789",
    apnsCername: "",
    pkCername: "",
    language: "",
    enableFloatingWindow: true,
    enableAutoFloatingWindowWhenHome: true,
    enableForegroundService: true,
}, (ret) => {
    if (ret.code != 200) {
        var msg = 'init 失败\n错误码：' + ret.code + '\n错误信息：' + ret.message;
        uni.showToast({
            title: msg,
            icon: "none"
        })
    } else {
        uni.showToast({
            title: 'init 成功 ' + ret.code,
            icon: "none"
        })
    }
})
```

### login

**接口描述**

账号登录。

**参数说明**

```JavaScript
login({params}, callback(ret))
```

参数名称 | 类型 | 是否必填 | 说明
--- | --- | --- | ---
`params` | Object | 是 | 登录参数。 |
 `appKey` | String | 是 | 网易云信 IM 应用的 AppKey，获取方式请参考 [创建应用并获取 AppKey](https://doc.yunxin.163.com/console/concept/TIzMDE4NTA?platform=console)。
 `account` | String | 是 | 账号 ID，获取方法请参考 [注册 IM 账号](https://doc.yunxin.163.com/messaging2/guide/jU0Mzg0MTU?platform=client#第二步注册-im-账号)。
 `token` | String | 是 | 账号 Token，获取方法请参考 [注册 IM 账号](https://doc.yunxin.163.com/messaging2/guide/jU0Mzg0MTU?platform=client#第二步注册-im-账号)。
`callback` | Object | 是 | 回调函数。
 `ret` | Object | 是 | 回调信息。
  `code` | Number | 是 | 状态码。
  `message` | String | 是 | 错误信息。
  `loginInfo` | Object | 是 | 登录账号信息。
   `account` | String | 是 | 登录账号的 ID。
   `token` | String | 是 | 登录账号的 Token。

**示例代码**

```JavaScript
demo.login({
    account: '123465',
    token: '456789'
}, function(ret) {
    if (ret.code != 200) {
        var msg = '登录失败\n错误码：' + ret.code + '\n错误信息：' + ret.message;
        uni.showToast({
          title: msg,
          icon: 'none',
        })
    } else {
        uni.showToast({
          title: '登录成功',
          icon: 'none',
        })
    }
})
```

### logout

账号登出。

**参数说明**

```JavaScript
logout(callback(ret))
```

参数名称 | 类型 | 是否必填 | 说明
--- | --- | --- | ---
`callback` | Object | 是 | 回调函数。
 `ret` | Object | 是 | 回调信息。
  `code` | Number | 是 | 状态码。
  `message` | String | 是 | 错误信息。

**示例代码**

```JavaScript
demo.logout({}, (ret) => {
    if (ret.code != 200) {
        uni.showToast({
          title: '登出失败 ' + ret.code,
          icon: 'none',
        })
    } else {
        uni.showToast({
          title: '登出成功 ',
          icon: 'none',
        })
    }
})
```

### toCallPage

**接口描述**

呼叫。

**参数说明**

```JavaScript
toCallPage({params}, callback(ret))
```

参数名称 | 类型 | 是否必填 | 说明
--- | --- | --- | ---
`params` | Object | 是 | 登录参数。 |
 `calledAccount` | String | 是 | 被呼叫的账号 ID。
 `type` | Number | 是 | 呼叫类型。<br>1：音频呼叫<br>2：视频呼叫
 `rtcChannelName` | String | 是 | 网易云信 RTC 频道名称。
`callback` | Object | 是 | 回调函数。
 `ret` | Object | 是 | 回调信息。
  `code` | Number | 是 | 状态码。
  `message` | String | 是 | 错误信息。

**示例代码**

```JavaScript
demo.toCallPage({
    calledAccount:'123456',
    type:2
}, function(ret) {
    if (ret.code != 200) {
        var msg = '呼叫失败\n错误码：' + ret.code + '\n错误信息：' + ret.message;
        uni.showToast({
          title: msg,
          icon: 'none',
        })
    } else {
        uni.showToast({
          title: '呼叫成功',
          icon: 'none',
        })
    }
})
```

### addEventListener

```JavaScript
callKitEvent.addEventListener('onReceiveInvited', function(e) {
      console.log('onReceiveInvited' + JSON.stringify(e));
});
callKitEvent.addEventListener('onCallConnected', function(e) {
  console.log('onCallConnected' + JSON.stringify(e));
});
callKitEvent.addEventListener('onCallTypeChange', function(e) {
  console.log('onCallTypeChange' + JSON.stringify(e));
});
callKitEvent.addEventListener('onCallEnd', function(e) {
  console.log('onCallEnd' + JSON.stringify(e));
});
callKitEvent.addEventListener('onVideoMuted', function(e) {
  console.log('onVideoMuted' + JSON.stringify(e));
});
callKitEvent.addEventListener('onAudioMuted', function(e) {
  console.log('onAudioMuted' + JSON.stringify(e));
});
```

## 回调事件

### onReceiveInvited

接收到呼叫邀请。

参数名称 | 类型 | 说明
--- | --- | ---
`callType` | Number | 呼叫类型。<br>1：音频呼叫<br>2：视频呼叫
`callerAccount` | String | 呼叫账号 ID。

### onCallConnected

建立通话。

参数名称 | 类型 | 说明
--- | --- | ---
`callType` | Number | 呼叫类型。<br>1：音频呼叫<br>2：视频呼叫
`callId` | Number | 通话 ID。
`calledAccount` | String | 被呼叫账号 ID。
`currentAccount` | String | 呼叫（当前）账号 ID。

### onCallTypeChange

通话类型变更。

参数名称 | 类型 | 说明
--- | --- | ---
`callType` | Number | 呼叫类型。<br>1：音频呼叫<br>2：视频呼叫

### onCallEnd

通话结束。

参数名称 | 类型 | 说明
--- | --- | ---
`code` | Number | 错误码<br>2：超时取消<br>12：手动取消<br>14：对方拒接通话<br>15：接听并自己结束通话<br>16：接听并对方结束通话
`message` | String | 错误信息。

### onVideoMuted

远端用户的视频流采集是否静音。

参数名称 | 类型 | 说明
--- | --- | ---
`account` | String | 远端账号 ID。
`mute` | bool | 是否静音。

### onAudioMuted

远端用户的音频流采集是否静音。

参数名称 | 类型 | 说明
--- | --- | ---
`account` | String | 远端账号 ID。
`mute` | bool | 是否静音。