<!--keywords: 推送,离线推送,推送服务,第三方推送,推送消息,限制,限制说明,payload,小米,OPPO,vivo,华为,荣耀,魅族,谷歌,FCM,APNs -->

云信 IM 服务端支持自定义消息的推送配置。

用户在发送消息或者自定义系统通知时，可以通过入参 `payload` 来自定义推送配置，包括推送标题，消息类型，点击跳转形式等。为了集成多家厂商的推送服务，云信限定了 `payload` 的格式（JSON），当用户按照格式正确填写对应的推送参数后，云信将自动解析，并透传给对应的厂商。

:::note notice
若 `payload` 格式填写不正确，可能会导致推送不成功。
:::

本文主要介绍云信 payload 字段的使用说明并提供各厂商对应的示例代码。

## 云信 payload 格式

云信的 payload 参数格式如下：

<table>
    <thead>
        <tr> <th style="width:180px">参数</th><th style="width:100px">类型</th><th>说明</th></tr></thead>
            <tr> <td> pushTitle </td><td>String</td><td>公用参数，指定推送消息的标题</td></tr>
            <tr> <td> apsField </td><td>JSON</td><td>APNs 推送消息中的 aps 参数，可参考 <a href="#apns推送消息">APNs 推送消息示例</a></td></tr>
            <tr> <td> pushkitFirst </td><td>boolean</td><td>是否优先使用 PushKit 推送（如果没有 PushKit 相关信息，则采用 APNs 推送）。<br>true：优先使用 PushKit 推送；false：优先使用 APNs 推送。</td></tr>
            <tr> <td> notifyId </td><td>int</td><td>推送通知的消息 ID（标识符），需要为 32 位整数。若 ID 相同，后一条会覆盖前一条通知。</td></tr>
            <tr> <td> hwPassThroughField </td><td>JSON</td><td>华为透传消息中的 Message 参数，可参考 <a href="#华为透传消息">华为透传消息示例</a></td></tr>
            <tr> <td> hwField </td><td>JSON</td><td>华为通知栏消息中的 android.notification 参数，可参考 <a href="#华为通知栏消息">华为通知栏消息示例</a></td></tr>
            <tr> <td> honorPassThroughField </td><td>JSON</td><td>荣耀透传消息中的 Message 参数，可参考 <a href="#荣耀透传消息">荣耀透传消息示例</a></td></tr>
            <tr> <td> honorField </td><td>JSON</td><td>荣耀通知栏消息中的 Message.android 参数，可参考 <a href="#荣耀通知栏消息">荣耀通知栏消息示例</a></td></tr>
            <tr> <td> vivoField </td><td>JSON</td><td>vivo 推送消息的请求体参数，可参考 <a href="#vivo推送消息"> vivo 推送消息示例</a></td></tr>
            <tr> <td> oppoField </td><td>JSON</td><td>OPPO 推送消息中的 Message 参数，可参考 <a href="#oppo推送消息"> OPPO 推送消息示例</a></td></tr>
            <tr> <td> fcmField </td><td>JSON</td><td>旧版谷歌 FCM 推送消息中的 notification 参数，可参考 <a href="#谷歌fcm推送消息">谷歌 FCM 推送消息示例</a></td></tr>
            <tr> <td> fcmFieldV1 </td><td>JSON</td><td>新版谷歌 FCM 推送消息中的 notification 参数，可参考 <a href="#谷歌fcm推送消息">谷歌 FCM 推送消息示例</a></td></tr>    
            <tr><td> harmonyField </td><td>JSON</td><td>鸿蒙推送消息中的 Message 参数，可参考 <a href="#鸿蒙推送消息">鸿蒙推送消息示例</a></td></tr>                
<table>

::: note note 
- 小米推送的 extra 参数直接以以下方式传递，可参考[小米推送消息示例](#小米推送消息)。`extra` 开头的字段说明详见[小米官方文档](https://dev.mi.com/distribute/doc/details?pId=1559)。
    ```
    "channel_id": "channel"  // 小米  extra.channel_id
    "channel_name": "channel_name"  // 小米 extra.channel_name
    ```
- 魅族推送暂只提供 clickTypeInfo.parameters 的自定义配置，可直接通过 `key`-`value` 形式填写对应参数，可参考[魅族推送消息示例](#魅族推送消息)。
:::




**云信 payload 示例：**

```
{
    "pushTitle":"",  // 公用参数，指定推送消息的标题
    "apsField":{},  // 等同于APNS推送中的aps参数 
    "fcmField": {}, // 等同于FCM推送中的notification参数 
    "honorPassThroughField": {},  // 荣耀透传消息等同于荣耀推送的Message参数
    "honorField": {},  // 等同于荣耀推送的Message.android参数
    "hwPassThroughField": {}, // 华为Message参数
    "hwField": {
          // android.notification参数直接在此处添加
          "click_action": {}, // 等同于android.notification.click_action参数
          "androidConfig": {
              "category":"",// 等同于AndroidConfig.category
          }
    }
    "oppoField": {}  //等同于Oppo推送的message参数
    "vivoField": {}  // 等同于vivo推送的请求体参数
    
    // 小米推送的extra参数直接以以下方式传递：
    "ticker":"value",
    "notify_foreground":"value"
    
    // 魅族推送暂只提供clickTypeInfo.parameters的自定义配置， 直接在此处填写对应参数
    "key":"value" 
}
```


## 第三方推送厂商对应的 payload 示例

### APNs推送消息

```
{
   "pushTitle":"",  // 指定推送消息的标题
   "apsField": {
      "alert" : {
         "title" : "Game Request",
         "subtitle" : "Five Card Draw",
         "body" : "Bob wants to play poker"
      },
      "category" : "GAME_INVITATION"
   },
}
```

`apsField` 中的字段说明，详见[ APNs 官网文档](https://developer.apple.com/library/archive/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/PayloadKeyReference.html#//apple_ref/doc/uid/TP40008194-CH17-SW1)。



### 小米推送消息

```
{
    "pushTitle":"",// 推送消息标题
    // 小米推送的 extra 参数直接以以下方式传递：
    "channel_id":""//通知类别（Channel）的ID
    "sound":"",//自定义通知栏消息铃声 URI，铃声文件放在 Android app 的 raw 目录下
    "ticker":"",//开启通知消息在状态栏滚动显示
    "notify_foreground":"1",//开启或关闭 app 在前台时的通知弹出，1：弹出，2：不弹出，默认为1
    "notify_effect":"1",//预定义通知栏消息的点击行为。1：通知栏点击后打开app的Launcher Activity，2：通知栏点击后打开app的任一Activity（开发者还需要传入intent_uri），3：通知栏点击后打开网页（开发者还需要传入web_uri）
    "intent_uri":"",
    "web_uri":"",
    "jobkey":"",
    "app_version":"",//可以接收消息的 app 版本号，用逗号分割
    "app_version_not_in":"",//无法接收消息的app版本号，用逗号分割
    "connpt":"",//指定在特定的网络环境下才能接收到消息。目前仅支持指定 wifi
    "only_send_once":"1"//设置为1，表示该仅设备在线时发送一次，不缓存离线消息进行多次下发
}
```



::: note note
- `extra` 开头的字段说明详见[小米官方文档](https://dev.mi.com/distribute/doc/details?pId=1559)。
- 由于网易云信默认需占用 2 个 extra 字段用于内部逻辑，因此您最多可再添加 8 个字段（总数上限为 10 个）。
:::


### 华为推送消息


华为推送消息分类通知栏消息和透传消息，两种类型分别传入 `hwPassThroughField` 和 `hwField` JSON 字符串来自定配置。

:::note notice
- 如果一条消息的 payload 中同时包含 hwPassThroughField 和 hwField，则该推送会作为透传消息。即 hwPassThroughField 生效，hwField 的字段无效。
- 其他字段说明详见[华为官方文档](https://developer.huawei.com/consumer/cn/doc/development/HMSCore-References/https-send-api-0000001050986197#ZH-CN_TOPIC_0000001134031085__p431142991615)。
:::


#### 华为通知栏消息

```
{
    "pushTitle":"",//消息标题
    "hwField": {
        "click_action": { "type": 1},//消息点击行为。type为1：打开应用自定义页面，type为2：点击后打开特定URL，type为3：点击后打开应用
        "badge": {},//Android通知消息角标控制
        "style":0,//通知栏样式
        "androidConfig": {
            "collapse_key":-1,//用户设备离线时，Push 服务器对离线消息缓存机制，默认为-1，详见官方文档 AndroidConfig.collapse_key
            "urgency":"NORMAL",//透传消息投递优先级，详见官方文档AndroidConfig.urgency
            "category":"IM",//标识消息类型，用于标识高优先级透传场景，详见官方文档 AndroidConfig.category
            "data":""//自定义消息负载，详见官方文档AndroidConfig.data
        }
    }
}
```

#### 华为透传消息

```
{
    "pushTitle":"",//消息标题
    "hwPassThroughField": {
        "data":"{\"1111\":\"22222\"}",//自定义消息负载,只支持字符串或json格式字符串
        "android": {
            "collapse_key":-1,//用户设备离线时，Push服务器对离线消息缓存机制,默认为-1，详见官方文档AndroidConfig.collapse_key
            "urgency":"NORMAL",//透传消息投递优先级,详见官方文档AndroidConfig.urgency
            "category":"IM",//标识消息类型,用于标识高优先级透传场景,，详见官方文档AndroidConfig.category
        }
    }
}
```


### 荣耀推送消息

荣耀推送消息分类通知栏消息和透传消息，两种类型分别传入 `honorPassThroughField` 和 `honorField` JSON 字符串来自定配置。

:::note notice
- 如果一条消息的 payload 中同时包含 honorPassThroughField 和 honorField，则该推送会作为透传消息。即 honorPassThroughField 生效，honorField 的字段无效。
- 其他字段说明详见[荣耀官方文档](https://developer.hihonor.com/cn/kitdoc?category=%E5%9F%BA%E7%A1%80%E6%9C%8D%E5%8A%A1&kitId=11002&navigation=ref&docId=downlink-message.md)。
:::

#### 荣耀通知栏消息

```
{
    "pushTitle":"",  // 消息标题
    "honorField":{  
        "biTag": "biTag001",  // AndroidConfig.biTag
        "data": "",  // AndroidConfig.data
        "notification": {  // AndroidNotification
            "bigBody": "the big body",
            "bigTitle": "the big title",
            "body": " the big body",
            "title": " the big title",
            "buttons": [{
                    "actionType": 0,
                    "data": "",
                    "intent": "",
                    "intentType": 0,
                    "name": "test"
            }],
            "clickAction": {//	消息点击行为
                "action": "",
                "intent": "intent://com.hihonor.codelabpush",
                "type": 1,//1为打开应用自定义页面，2为点击后打开特定URL，3为点击后打开应用
                "url": "https://www.vmall.com"
            },
            "image": "https://res.vmallres.com/SXppnESYv4K11DBxDFc2.png",
            "importance": "NORMAL",
            "style": 0,
            "when": "2014-10-02T15:01:23.045123456Z"
        }
    }
}
```

#### 荣耀透传消息

```
{
    "pushTitle":"",  //消息标题
    "honorPassThroughField": {
        "data":"{\"1111\":\"22222\"}",  // message.data
        "android": {
            "biTag":"",  // AndroidCofig.biTag
        }
    }
}
```



### vivo推送消息

```
{
    "pushTitle":"",//消息标题
    "vivoField": {
        "skipType":"1",//点击跳转类型 1：打开APP首页 2：打开链接 3：自定义 4:打开app内指定页面，默认为1
        "skipContent":"",//跳转内容,与skipType对应
        "classification":"0",//消息类型 0：运营类消息，1：系统类消息。默认为0
        "networkType":"-1",//网络方式 -1：不限，1：wifi下发送，不填默认为-1
        "pushMode":"0",//推送模式 0：正式推送；1：测试推送，不填默认为0
        "category":"IM" // 二级分类
    }
}
```

`vivoField` 中的字段说明，详见[ vivo 官方文档](https://dev.vivo.com.cn/documentCenter/doc/362)。


### OPPO推送消息

```
{
    "pushTitle":"",//消息标题
    "oppoField": {
            "channel_id": "", //指定下发的通道ID
            “category”:"IM", //通道类别名
            "notify_level": 2, //通知栏消息提醒等级，1-通知栏；2-通知栏+锁屏；16-通知栏+锁屏+横幅+震动+铃声
            "click_action_type": "", //点击通知栏后触发的动作类型。0（默认0.启动应用；1.跳转指定应用内页（action标签名）；2.跳转网页；4.跳转指定应用内页（全路径类名）；5.跳转Intent scheme URL: "",
            "click_action_activity": "",
            "click_action_url": "",
            "action_parameters": "",
            "style": 1, //通知栏样式
            "action_parameters": 
            "sub_title": "", // 子标题
            "network_type": 0, //推送的网络环境类型
    }
}
```

`oppoField` 中的字段说明，详见[ OPPO 官方文档](https://open.oppomobile.com/new/developmentDoc/info?id=11235)。

### 魅族推送消息

```
{
    "pushTitle":"",//消息标题
    // 魅族推送暂只提供 clickTypeInfo.parameters 的自定义配置， 直接在此处填写对应参数
    "key":"value",  // clickTypeInfo.parameters中的自定义字段
    "key":"value"  // clickTypeInfo.parameters中的自定义字段
}
```

`clickTypeInfo.parameters` 的自定义配置说明，详见[魅族官方文档](https://open-res.flyme.cn/fileserver/upload/file/201803/be1f71eac562497f92b42c750196a062.pdf)。

### 谷歌FCM推送消息

<!--

```
{
    "pushTitle":"",//消息标题
    "fcmField": {
        "android_channel_id":"string",
        "click_action":"string"
    }
}
```


::: note notice
目前云信的 fcmField 只支持设置 [Firebase 官网文档-Notification payload support](https://firebase.google.com/docs/cloud-messaging/http-server-ref#notification-payload-support)中的字段。

<img style="width:50%" src="https://yx-web-nosdn.netease.im/common/93efc8bdf56cc4a6dde72c766e10361b/FirebaseNotificationPayloadSupport.png" />
:::

-->

**旧版**

```
{
    "fcmField": {
        "analytics_label":"统计字段，对应官方文档中fcm_options字段中的analytics_label",
        "icon":"string",
        "color":"string",
        "sound":"string",
        "tag":"string",
        "click_action":"string",
        "body_loc_key":"string",
        "body_loc_args": [
            "string"
        ],
        "title_loc_key":"string",
        "title_loc_args": [
        ],
        "channel_id":"string",
        "ticker":"string",
        "sticky":"boolean",
        "event_time":"string",
        "local_only":"boolean",
        "notification_priority":"",
        "default_sound":"boolean",
        "default_vibrate_timings":"boolean",
        "default_light_settings":"boolean",
        "vibrate_timings": [
            "string"
        ],
        "visibility":"",
        "notification_count":"integer",
        "light_settings": {

        },
        "image":"string"
    },
    "key":"value",
}
```

更多字段信息请参考[官方文档](https://firebase.google.com/docs/cloud-messaging/http-server-ref)。

**新版**（FCM HTTP V1 推送）

使用 FCM HTTP V1 协议推送需要申请 HTTP V1 鉴权证书。当使用该版本证书进行推送时，payload 中应使用 "fcmFieldV1" 字段配置自定义推送参数。使用旧版本证书推送时，应使用"fcmField"字段配置自定义推送参数。新版本证书和旧版本证书可以同时使用，服务器会根据用户SDK中配置的证书版本选取推送通道。

FCM HTTP V1 推送的更多信息请参考[官方文档](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages/send)。

```
{
    "fcmFieldV1":{
        "validate_only": true,
        "message": {
          "needNotification": false, // 是否需要自动填充notification字段，默认true，当需要使用数据消息时，此字段需要设置为false
          "notification": {
            "image": "string"
          },
          "data": {
            "name": "wrench",
            "mass": "1.3kg",
            "count": "3" 
          },
          "android": {
            "restricted_package_name": "string",
            "data": {
              "string": "string",
            },
            "notification": {
              "channel_id": "string",
              "color": "string",
            },
            "fcm_options": {
              "analytics_label": "string"
            },
            "direct_boot_ok": true
          }
        }
    }    
}
```




<!--

## 推送相关参数说明


|参数|类型|说明|
|:-----|:-----|:-----|
|option|JSON|特殊指定的行为选项，其中涉及消息的推送属性包括是否需要推送（`push`）、推送文案是否需要带上昵称（`needPushNick:`）<br/>可参考以下示例：<br>{"push":false,"roam":true,"history":false,"sendersync":true,<br/>"route":false,"badge":false,"needPushNick":true}
|pushcontent|String|推送内容，最大长度 500 字节<font color=red>（单位是什么，字节还是字符）</font>，如果不填，则使用默认文案。推送文案的显示规则如下：<ul><li>pushcontent不为空且needPushNick=true，最终推送文案为：推送者昵称+pushcontent</li><li>pushcontent不为空且needPushNick=false，最终推送文案为：pushcontent</li><li>pushcontent为且needPushNick=true ，最终推送文案为：推送者昵称+默认文案</li><li>pushcontent为且needPushNick=false，最终推送文案为：默认文案</li></ul>其中，根据消息类型，默认文案分为以下几种：<ul><li>文本消息默认文案：发来了一条消息</li><li>地理位置默认文案：发来了一个地理位置</li><li>语音消息默认文案：发来了一段语音</li><li>视频消息默认文案：发来了一段视频</li><li>文件消息默认文案：发来了一个文件</li><li>图片消息默认文案：发来了一张图片</li><li>语音聊天消息默认文案：发来了语音聊天邀请</li><li>视频聊天邀请消息默认文案：发来了视频聊天邀请</li></ul>|
|payload|JSON|第三方推送对应的 payload，最大长度 2048 字节。<br>各第三方推送服务对应的 payload 示例如下：<ul><li><a href="" target="_blank">小米</a></li><li><a href="" target="_blank">华为</a></li><li><a href="" target="_blank">荣耀</a></li><li><a href="" target="_blank">vivo</a></li><li><a href="" target="_blank">OPPO</a></li><li><a href="" target="_blank">魅族</a></li><li><a href="" target="_blank">谷歌 FCM</a></li></ul>


-->

### 鸿蒙推送消息

```json
{
    "harmonyField": {
        "payload": {
            "notification": {
                "category": "MARKETING",
                "title": "普通通知标题",
                "body": "普通通知内容",
                "clickAction": {
                    "actionType": 0
                },
                "badge": {
                    "addNum": 1
                },
                "notifyId": 12345
            }
        },
        "pushOptions": {
            "testMessage": true,
            "ttl": 1223
        }
    }
}
```

`harmonyField` 中的字段说明，详见 [鸿蒙推送官网文档](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides-V13/push-send-alert-V13)。


## 相关参考文档

更多推送参数说明请参考第三方推送厂商的官方文档：

- [小米](https://dev.mi.com/distribute/doc/details?pId=1559)
- [华为](https://developer.huawei.com/consumer/cn/doc/development/HMSCore-References/https-send-api-0000001050986197)
- [荣耀](https://developer.hihonor.com/cn/kitdoc?category=%E5%9F%BA%E7%A1%80%E6%9C%8D%E5%8A%A1&kitId=11002&navigation=ref&docId=downlink-message.md)
- [OPPO](https://open.oppomobile.com/new/developmentDoc/info?id=11235)
- [vivo](https://dev.vivo.com.cn/documentCenter/doc/362)
- [魅族](https://open.flyme.cn/docs?id=129)
- [谷歌 FCM（旧）](https://firebase.google.com/docs/cloud-messaging/http-server-ref#notification-payload-support)
- [谷歌 FCM（新）](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages/send)
- [APNs](https://developer.apple.com/library/archive/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/PayloadKeyReference.html#//apple_ref/doc/uid/TP40008194-CH17-SW1)
- [鸿蒙](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides-V13/push-send-alert-V13)