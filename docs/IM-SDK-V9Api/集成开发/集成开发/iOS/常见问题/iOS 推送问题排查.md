
云信IM即时通讯支持iOS推送平台。本节主要描述iOS苹果推送流程以及推送失败后的排查方法。


## <span id="概念">概念</span>

| **名词**    | **解释**                             |
| :-------- | :--------------------------------------- | 
| APNS      | 苹果推送通知服务。该技术由苹果公司提供。                            |
| 证书   | 苹果推送证书，一般以 .p12 或者 .p8 结尾，大小一般是 3kb 左右。P12 证书有有效期限，P8 证书一直有效。                        | 
|  正式环境</br>测试环境   | - iOS 证书在生成的时候分正式测试两用证书和测试证书，分别对应相应的环境。|\
|     | - iOS app 打包的时候分 release 和 debug ，分别对应正式环境和测试环境。|\
|     | - 云信管理后台上传证书时配置证书的环境，对应请求正式或者测试的 APNS 环境。|
| SandBox       |  测试环境（沙盒环境）。       |
| DeviceToken     | DeviceToken 是 iOS 设备上特定 app 的推送唯一 ID，APNS 服务器依次推送至相应的 iOS 设备，并展示设备上相应应用的通知栏。   | 
| Pusher、</br>SmartPush、</br>Knuff    | 第三方推送测试工具，用于模拟 APNS 服务器请求到 iOS 设备，与云信逻辑无关。可以检查 Devicetoken、推送证书、推送环境是否匹配。               | 

## <span id="推送流程">推送流程</span>

![推送流程图.png](https://yx-web-nosdn.netease.im/common/06487e0a08e4167483dc3fb4958ac883/推送流程图.png)


## <span id="问题排查">问题排查</span>

::: note notice
在排查问题前，请检查是否按照开发文档集成推送功能。
:::


对应推送流程图，问题排查的步骤如下：

**步骤1：检查 DeviceToken 是否生成**

检查项目中`didRegisterForRemoteNotificationsWithDeviceToken`回调是否正常回调了`DeviceToken`。

如果没有，需要检查 iOS 推送的配置。具体请参见：[https://doc.yunxin.163.com/messaging/guide/DMxMjU0MDY?platform=iOS#%E5%BC%80%E5%90%AF%E6%8E%A8%E9%80%81%E5%8A%9F%E8%83%BD](https://doc.yunxin.163.com/messaging/guide/DMxMjU0MDY?platform=iOS#%E5%BC%80%E5%90%AF%E6%8E%A8%E9%80%81%E5%8A%9F%E8%83%BD)

**步骤2：检查 Token 是否上报云信**

1. 获取 sdk 日志。如何获取，请参见：[https://faq.yunxin.163.com/#KB0179/2](https://faq.yunxin.163.com/#KB0179/2)
2. 查看日志中 token 关键字。如果有如下的日志打印，说明 token 已经被 sdk 获取并上报，日志中后续打印的即为服务器收到的`devicetoken`：
![日志token词.png](https://yx-web-nosdn.netease.im/common/47ef37d6de1add8d66b22270213ebe26/日志token词.png)

**步骤3：检查是否满足推送条件**  

具体触发消息推送的条件，请参见：[https://faq.yunxin.163.com/#KB0065/1-1](https://faq.yunxin.163.com/#KB0065/1-1)

**步骤4：检查管理后台证书配置**

![管理后台证书配置.png](https://yx-web-nosdn.netease.im/common/1ac18bf31a8f57833c7fe44e1f76f594/管理后台证书配置.png)

**步骤5：利用工具测试 token 和证书的有效性**
::: note notice
Pusher 目前无法使用，可以用 SmartPush 、 Knuff 或者其他工具替换。
:::
这里以 Knuff 为例，请[下载](https://github.com/KnuffApp/Knuff/releases)安装 Knuff。

![下载knuff.png](https://yx-web-nosdn.netease.im/common/30c777447db9c1706bb91c7bac87c209/下载knuff.png)

- Knuff 测试的是证书和 devicetoken 的有效性，用开发者自行申请到的 p12 证书，iOS 系统生成的 DeviceToken 直接请求到 APNS 服务器，所以本质上和云信没有关系。

- 如果 Knuff 无法推送成功，请查看相应的错误提示，例如证书环境错误、token 错误等。一般都是因为证书异常，或者 token 和所选的环境不匹配导致的。

- 如果 Knuff 推送成功，但是使用网易云信SDK推送失败，那么请确认以下信息：
  - 保证步骤 2 中的 token 和提供给 Knuff 的一致。
  - 保证步骤 4 中上传的证书环境，和 Knuff 选择的推送环境一致。

**步骤6：服务器推送记录排查**

若上述步骤均未发现问题，则需要提交工单交由技术支持排查后端的请求情况。

需要提供以下信息：

- 步骤 2 的 sdk 日志以及 devicetoken 文本
- 步骤 4 的推送后台证书上传详情截图
- 步骤 5 的 Knuff 推送成功记录完整截图
- 测试的时间点和消息 msgid

工单提交：[https://app.yunxin.163.com/index#/issue/submit](https://app.yunxin.163.com/index#/issue/submit)

## <span id="关于点击通知栏回调">关于点击通知栏回调</span>

发消息时可以通过消息的`payload`字段，配置`sessionid`和`sessionType`。

通过 iOS 系统相应的回调，获取到 payload 信息进行跳转。具体请参见：[https://doc.yunxin.163.com/messaging/guide/DMxMjU0MDY?platform=iOS#%E7%82%B9%E5%87%BB%E9%80%9A%E7%9F%A5%E6%A0%8F%E8%B7%B3%E8%BD%AC](https://doc.yunxin.163.com/messaging/guide/DMxMjU0MDY?platform=iOS#%E7%82%B9%E5%87%BB%E9%80%9A%E7%9F%A5%E6%A0%8F%E8%B7%B3%E8%BD%AC)

客户端点击通知栏通知，会打开 app 触发`didReceiveRemoteNotification`回调方法，回调方法返回`userInfo`，`userInfo`的数据格式如下：

![回调userInfo的数据.png](https://yx-web-nosdn.netease.im/common/fb57891fe5e339643157afe9e984a38d/回调userInfo的数据.png)
```
{
    aps =     {
        alert =         {
            body = Oppp;
            title = ooiipp;
        };
        badge = 4;
        ext = "ext test";
        sound = default;
    };
    nim = 1;
    pushTitle = ooiipp;
}
```
对应发送的消息的apnsPayload
```
message.apnsPayload = @{
        @"pushTitle" : @"ooiipp",
        @"apsField" : @{
            @"ext" : @"ext test",
            @"alert": @{
                        @"title" : @"ooiipp",
                        @"body" : @"Oppp"
                    }
        }
    };
```

## <span id="推送Service Extension">推送Service Extension</span>

自 iOS10 开始支持 Service Extension，主要用途是苹果服务器发推送消息到手机后，手机上通知栏通知展示推送消息之前，允许开发者对推送消息做一些处理。常见用途是在 Extension 中获取到推送的扩展参数，根据参数给推送通知加上图片。详细用法和用途，请参见：[https://developer.apple.com/documentation/usernotifications/unnotificationserviceextension/](https://developer.apple.com/documentation/usernotifications/unnotificationserviceextension/)

对于云信来说，只会在发消息的时候进行处理，如在apnsPayload里面加上自定义参数，其余的需要客户端处理，在 Extension 中的`didReceiveNotificationRequest`方法里面，获取到推送数据`userInfo` ，即下图的 dict，云信的任务就完成了。

![获取数据dict.png](https://yx-web-nosdn.netease.im/common/0f64847d373ad580027563136f4cc2ce/获取数据dict.png)
