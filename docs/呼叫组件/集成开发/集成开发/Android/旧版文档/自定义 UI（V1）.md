如需快速实现双人通话的呼叫功能，您可以直接基于网易云信提供的一对一视频通话示例项目进行修改与适配，也可以通过**集成呼叫组件 + 自定义 UI 界面**的方式实现。本文介绍自定义 UI 的实现方法。


::: note note
本文适用于呼叫组件 V1.8.2 及之前版本，如果您集成的是呼叫组件 V2 版本，请参见[自定义 UI（V2）](https://doc.yunxin.163.com/nertccallkit/docs/zYzNzI5NDI?platform=android)。
:::

 

### 步骤 1 创建呼叫 Activity

创建呼叫 Activity 并继承 `CommonCallActivity`。

```
public class TestActivity extends CommonCallActivity {

    @Override // 布局文件
    protected int provideLayoutId() {
        return R.layout.activity_test;
    }

    @NotNull
    @Override // rtc 相关回调设置，用户可实现自己的回调，并根据 回调处理相关 UI
    protected NERTCCallingDelegate provideRtcDelegate() {
        return new NERtcCallDelegateForP2P();
    }
}
```
### 步骤 2 实现自定义布局

实现自定义布局并调用父类方法完成呼叫与被叫页面。通过关键字 **CommonCallActivity** 过滤日志信息，示例代码中未处理接口错误情况，可根据情况自己实现。详细示例请参考[附件](https://github.com/netease-kit/documents/tree/main/%E4%B8%9A%E5%8A%A1%E7%BB%84%E4%BB%B6/%E5%91%BC%E5%8F%AB%E7%BB%84%E4%BB%B6/%E5%BC%80%E5%8F%91%E6%96%87%E6%A1%A3/%E8%BF%9B%E9%98%B6%E5%8A%9F%E8%83%BD/Android/%E9%99%84%E4%BB%B6)。

作为子类可使用如下方法以及参数完成相应实现。

CommonCallActivity：

| <div style="width: 150px">方法</div>             | 参数                            | <div style="width: 50px">返回</div>      | 说明                                                 |
| ---------------- | ------------------------------- | --------- | ---------------------------------------------------- |
| getCallParam     | -                               | CallParam | 呼叫/被叫时的必要参数                                |
| isLocalMuteAudio | -                               | Boolean   | 本地音频是否关闭采集                                 |
| isLocalMuteVideo | -                               | Boolean   | 本地视频是否关闭采集                                 |
| doMuteAudio      | -                               | -         | 修改本地当前音频采集状态，若当前为开启则执行后为关闭 |
| doMuteVideo      | -                               | -         | 修改本地当前视频采集状态，若当前为开启则执行后为关闭 |
| doSwitchCamera   | -                               | -         | 切换摄像头方向，默认为正向                           |
| doCall           | `JoinChannelCallBack`，`String` | -         | 主叫呼叫                                             |
| doCancel         | `RequestCallbackWrapper<Void>`  |           | 主叫取消                                             |
| doReject         | `RequestCallbackWrapper<Void>`  | -         | 被叫拒绝                                             |
| doAccept         | `JoinChannelCallBack`           | -         | 被叫接受                                             |
| doHangup         | `RequestCallbackWrapper<Void>`  | -         | 挂断                                                 |



| 属性      | 类型           | 说明             |
| --------- | -------------- | ---------------- |
| videocall | NERTCVideoCall | 基础呼叫组件实例 |


CallParam：

| 方法               | 类型                  | 说明                       |
| ------------------ | --------------------- | -------------------------- |
| isCalled           | `Boolean`             | <ul><li>true：被叫<br></li><li>false：主叫</li> </ul>     |
| getChannelType     | `int`                 | <ul><li>1：音频通话<br></li><li>2：视频通话</li> </ul>   |
| getCallerAccId     | `String`              | 呼叫方 IM 账号 ID           |
| getCurrentAccId    | `String`              | 当前用户 IM 账号 ID        |
| getCalledAccIdList | `List<String>`        | 被呼叫用户 IM 账号列表     |
| getGroupId         | `String`              | 群组 ID                    |
| getExtras          | `Map<String, Object>` | 自定义扩展参数             |
| getP2pCalledAccId  | `String`              | 获取 p2p 通话的被叫账号 ID |

### 步骤 3 注册呼叫页面

在初始化时注册呼叫页面。

示例代码：

```java
CallKitUIOptions options = new CallKitUIOptions.Builder()
		......
  	.p2pVideoActivity(TestActivity.class)// 注册对应视频呼叫页面
  	.....
		.build();

CallKitUI.init(getApplicationContext(), options);
```
### （可选）步骤 4 设置关闭摄像头时的数据采集模式

您可以设置当用户在界面上单击**关闭摄像头**按钮时，摄像头数据采集的模式。包括 3 种模式，区别和说明如下表所示。

模式 | 说明 
---- | --------------
Constants.CLOSE_TYPE_MUTE | 用户在界面上单击**关闭摄像头**按钮时，不发布本地摄像头数据，但仍然采集摄像头数据。该模式下，用户单击开启摄像头后，界面能快速展示摄像头采集的数据。<br>默认为该模式。
Constants.CLOSE_TYPE_DISABLE |用户在界面上单击**关闭摄像头**按钮时，关闭本地摄像头数据采集及发布。
Constants.CLOSE_TYPE_COMPAT | 兼容此前使用 `CLOSE_TYPE_MUTE` 模式后续希望更换为`CLOSE_TYPE_DISABLE`。



具体实现方法：

1. 继承 `P2PCallActivity`，并设置关闭摄像头的相关自定义配置。

    ```java
    public class TestActivity extends P2PCallActivity {
    @Override
    protected P2PUIConfig provideUIConfig(CallParam param) {
        return new P2PUIConfig.Builder()
            .closeVideoType(Constants.CLOSE_TYPE_COMPAT)// 设置关闭摄像头时的数据采集模式
            .closeVideoLocalUrl(localUrl) // 设置关闭本地摄像头展示图片，若不填则默认黑色
            .closeVideoRemoteUrl(remoteUrl) // 设置对端关闭摄像头展示图片，若不填则默认黑色
            .closeVideoLocalTip(localTipStr) // 设置关闭本地摄像头展示的文案提示，若不填，本地预览切换至大窗会展示我方关闭了摄像头
            .closeVideoRemoteTip(remoteTipStr) // 设置对端关闭摄像头展示的文案提示，若不填，对端画布在大窗会展示对方关闭了摄像头
            .build();
    }
    }
    ```

2. 注册 `TestActivity` 到组件中。

    ```java
    CallKitUIOptions options = new CallKitUIOptions.Builder()
        ......
        .p2pVideoActivity(TestActivity.class)// 注册对应视频呼叫通话页面
        .p2pAudioActivity(TestActivity.class)// 注册对应音频呼叫通话页面
        .....
        .build();
    
    CallKitUI.init(getApplicationContext(), options);
    ```
### 步骤 5 发起呼叫

完成上述步骤后请参见[快速开始](/docs/zMwMzkwNTE/DQwNDU1NjM)实现通话。


