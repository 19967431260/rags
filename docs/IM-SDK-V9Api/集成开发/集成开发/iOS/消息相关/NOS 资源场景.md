SDK 支持通过 NOS 资源场景设置图片、语音、视频与文件等资源在网易对象存储（Netease Object Storage, NOS）服务的存活时间。

## NOS 资源场景

可通过<a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/de/de3/interface_n_i_m_s_d_k.html#ab3a7228bc75f8faf1671356a4e815e35" target="_blank">`sceneDict`</a> 预设图片、语音、视频与文件等资源在 NOS 的存活时间。

- API 原型
    ```objc
    @interface NIMSDK : NSObject

    /**
    *  资源场景配置
    *  @discussion nos 预设场景和自定义场景规则
    *  可以覆盖设置，如果预设场景不设置，为系统默认设置
    *  sceneDict key-value，系统默认预设场景为3种，自定义场景不超过10种
    *  key 是场景，nsstring类型；value 是资源存活时间，nsnumber类型，精确到天，0为永久存活
    */
    @property (nonatomic,strong)         NSMutableDictionary *sceneDict;
    @end
    ```

- NOS 资源场景例子

    如果`sceneDict`设置为`@{@"nim_icon":@0,@"nim_msg":@0,@"nim_system":@0}`，则代表：

    - 头像等用户资料（nim_icon）的 NOS 资源存活时间为“永久”。

    - 图片、音频、视频等各类消息附件（nim_msg）的 NOS 资源存活时间为“永久”。

    nim_system为SDK内部使用。

    sceneDict-key | NIMNOSSceneType枚举值
    :-:|:-:
    nim_icon | NIMNOSSceneTypeAvatar
    nim_msg | NIMNOSSceneTypeMessage



## 预设 NOS 资源场景

NOS 资源场景在多媒体消息附件的初始化方法中定义。例如，图片附件的 NOS 资源场景，可在<a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/de/d55/interface_n_i_m_image_object.html#a57199f8b569cfd55868fadb5014b9423" target="_blank">`initWithImage:scene:`</a>方法中定义。

示例代码如下：

```objc
NIMSession *session = [NIMSession session:@"user" type:NIMSessionTypeP2P];
// 获得图片附件对象,并设置对应的scene为nim_msg
NIMImageObject *imageObject = [[NIMImageObject alloc] initWithImage:image scene:NIMNOSSceneTypeMessage];
// 构造出具体消息并注入附件
NIMMessage *message = [[NIMMessage alloc] init];
message.messageObject = imageObject;
...
[[NIMSDK sharedSDK].chatManager sendMessage:message toSession:session error:&error];
```



## API参考

更多可设置多媒体消息附件的 NOS 资源场景的方法，请参见以下类中中带`scene`关键字的方法。
- <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/de/d55/interface_n_i_m_image_object.html" target="_blank">`NIMImageObject`</a>
- <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d0/d2d/interface_n_i_m_audio_object.html" target="_blank">`NIMAudioObject`</a>
- <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d4/dc3/interface_n_i_m_video_object.html" target="_blank">`NIMVideoObject`</a>
- <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d0/de8/interface_n_i_m_file_object.html" target="_blank">`NIMFileObject`</a> 
