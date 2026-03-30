本文介绍如何在集成含 UI 呼叫组件后，定制界面界面风格，包括界面布局、界面样式等。

::: note note
本文适用于呼叫组件 V2.1.0 及之后版本，如果您集成的是呼叫组件 V1 版本，请参考 [自定义 UI（V1）](https://doc.yunxin.163.com/nertccallkit/docs/jE1NDM1ODI?platform=android)。
:::

## 步骤说明

1. 呼叫组件包含六种类型的 Fragment，分别针对不同的呼叫状态（呼叫、被叫、通话中）和呼叫类型（音频、视频），具体类型如下表所示。

   **P2PCallFragmentType** 类型枚举：

   | 代码 | 具体值 | 对应 Fragment 页面 | 说明 |
   | ---- | ---- | ---- | ---- |
   | `VIDEO_CALLER`|1|`VideoCallerFragment` | 视频呼叫页面 |
   | `VIDEO_CALLEE`|2|`VideoCalleeFragment` | 视频被叫页面 |
   | `VIDEO_ON_THE_CALL` | 3 | `VideoOnTheCallFragment` | 视频通话页面 |
   | `AUDIO_CALLER` | 4 | `AudioCallerFragment` | 音频呼叫页面 |
   | `AUDIO_CALLEE` | 5 | `AudioCalleeFragment` | 音频被叫页面 |
   | `AUDIO_ON_THE_CALL` | 6 | `AudioOnTheCallFragment` | 音频通话页面 |

2. 您如果需要修改相关 UI，请按照如下步骤实现：

    1. 创建 Fragment。

        例如，创建一个名为 `TestAudioCallerFragment` 的 Fragment，用于修改音频呼叫页面的样式。该 Fragment 继承目标 Fragment `AudioCallerFragment`，也可以直接继承 `BaseP2pCallFragment`，但这种情况下需要自己完全负责 UI。示例代码如下：

        ```Java
        public class TestAudioCallerFragment extends AudioCallerFragment {
        }
        ```

   2. 创建页面 Activity。

        创建一个名为 `TestActivity` 的页面，该页面应继承自 `P2PCallFragmentActivity` 类。在 `TestActivity` 中重写 `provideUIConfig` 方法，并注册修改后的页面。示例代码如下：

        ```Java
        public class TestActivity extends P2PCallFragmentActivity {
            @NonNull
            @Override
            protected P2PUIConfig provideUIConfig(CallParam param) {
            return new P2PUIConfig.Builder()
                // 此处通过 P2PCallFragmentType 类型以及具体的 Fragment 完成页面注册
                .customCallFragmentByKey(P2PCallFragmentType.AUDIO_CALLER, new TestAudioCallerFragment())
                .build();
            }
        }
        ```

    3. 在初始化呼叫组件时，将刚刚创建的 Activity 在组件中注册，示例代码如下：

        ```Java
        CallKitUIOptions options = new CallKitUIOptions.Builder()
            ......
            // 设置自定义的音频通话界面
            .p2pAudioActivity(TestActivity.class)
            .build();
        // 组件初始化
        CallKitUI.init(this, options);
        ```

3. 以上步骤已完成组件 UI 的自定义，如需进行具体的 UI 修改，请参考下文。

## 自定义 UI 示例（基于 Fragment）

修改 UI 可以分为两种情况：
- 对界面进行简单的修改，例如更换图标、隐藏控制按钮等。这些修改可以通过代码实现，而无需重新编写布局。
- 对界面进行较大的修改，需要进行大量的 UI 修改。对于这种情况，可以考虑通过自定义 XML 文件来实现。

本文以自定义语音呼叫界面为例，展示如何修改背景图片、增加或去除图标、增加标题和副标题、将默认的对方头像样式从方形改为圆形。

**效果对比**

<div style="display: flex; justify-content: space-between; width: 100%;">
    <div style="width: 50%;text-align: center; caption-side: top;"">
        <figure>
      <figcaption style="width: 100%; text-align: center; caption-side: top;"><b>默认样式</b></figcaption>
        <img alt="" src="https://yx-web-nosdn.netease.im/common/19a7eb28d782350925cd10718a1ca305/自定义UI原图.png" style="width:60%;border: 1px solid #BFBFBF;"></figure>
    </div>
    <div style="width: 50%;text-align: center; caption-side: top;"">
            <figure>
      <figcaption style="width: 100%; text-align: center; caption-side: top;"><b>自定义样式</b></figcaption>
      <img alt="" src="https://yx-web-nosdn.netease.im/common/164c2258355e640c8adb5353fe7fc358/自定义UI修改后.png" style="width:60%;border: 1px solid #BFBFBF;"></figure>
    </div>
</div>

### 方式 1：通过 layout.xml 修改 UI

示例代码如下：

```XML
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/clRoot"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="@color/black"
    tools:ignore="ContentDescription,SpUsage">

    <ImageView
        android:id="@+id/ivBg"
        android:layout_width="match_parent"
        android:layout_height="match_parent" />

    <ImageView
        android:id="@+id/ivUserInnerAvatar"
        android:layout_width="90dp"
        android:layout_height="90dp"
        android:layout_marginTop="160dp"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"/>

    <TextView
        android:id="@+id/tvOtherCallTip"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="8dp"
        android:text="自定义提示信息内容"
        android:textColor="@color/colorWhite"
        android:textSize="14dp"
        app:layout_constraintStart_toStartOf="@id/ivUserInnerAvatar"
        app:layout_constraintTop_toBottomOf="@id/ivUserInnerAvatar"
        app:layout_constraintEnd_toEndOf="@id/ivUserInnerAvatar" />

    <ImageView
        android:id="@+id/ivCancel"
        android:layout_width="75dp"
        android:layout_height="75dp"
        android:layout_marginBottom="75dp"
        android:src="@drawable/call_reject"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent" />
</androidx.constraintlayout.widget.ConstraintLayout>
```

`TestAudioCallerFragment` 代码如下：

```Java
public class TestAudioCallerFragment extends AudioCallerFragment {
  @Nullable
  @Override
  protected View toCreateRootView(@NonNull LayoutInflater inflater, @Nullable ViewGroup container, @Nullable Bundle savedInstanceState) {
    // 创建根布局
    return inflater.inflate(R.layout.fragment_test_audio_caller, container, false);
  }

  @Override
  protected void toBindView() {
    View rootView = getRootView();
    if (rootView == null) {
      return;
    }
    // 绑定取消按钮
    bindView(getViewKeyImageCancel(), rootView.findViewById(R.id.ivCancel));
  }

  @Override
  protected void toRenderView(@NonNull CallParam callParam, @Nullable P2PUIConfig uiConfig) {
    // 需要保留，否则上面绑定的默认单击事件无效
    super.toRenderView(callParam, uiConfig);
    View rootView = getRootView();
    if (rootView == null) {
      return;
    }
    // 渲染对方昵称
    TextView nameView = rootView.findViewById(R.id.tvUserName);
    nameView.setText("18012345678");

    // 渲染对方头像
    ImageView avatarView = rootView.findViewById(R.id.ivUserAvatar);
    String avatarUrl = "https://yx-web-nosdn.netease.im/quickhtml/assets/yunxin/default/g2-demo-avatar-imgs/86117845552861184.jpg";
    Glide.with(requireContext()).load(avatarUrl)
      .circleCrop()
      .into(avatarView);
  }
}
```

### 方式 2：通过代码修改 UI

示例代码如下：

```Java
public class TestAudioCallerFragment extends VideoCallerFragment {
  @Override
  protected void toRenderView(@NonNull CallParam callParam, @Nullable P2PUIConfig uiConfig) {
    // 获取到背景大图
    ImageView backgroundView = getView(getViewKeyImageBigBackground());
    // 避免被组件内部异步加载图片
    removeView(getViewKeyImageBigBackground());
    // 获取到用户头像
    ImageView avatarView = getView(getViewKeyImageUserInnerAvatar());
    removeView(getViewKeyImageUserInnerAvatar());
    // 父类渲染
    super.toRenderView(callParam, uiConfig);
    // 修改背景大图
    if (backgroundView != null) {
      backgroundView.setScaleType(ImageView.ScaleType.CENTER_CROP);
      backgroundView.setImageResource(R.drawable.bg_custom_for_audio);
    }
    // 修改用户头像为圆形
    String avatarUrl = "https://yx-web-nosdn.netease.im/quickhtml/assets/yunxin/default/g2-demo-avatar-imgs/86117845552861184.jpg";
    if (avatarView != null) {
      Glide.with(requireContext()).load(avatarUrl)
        .circleCrop()
        .into(avatarView);
    }
    // 添加自定义 View
    View rootView = getRootView();
    if (rootView instanceof ConstraintLayout) {
      ViewGroup viewGroup = (ViewGroup) rootView;
      TextView newAddedView = new TextView(getContext());
      newAddedView.setText("每个人都会遇到那个 TA");
      ConstraintLayout.LayoutParams params = new ConstraintLayout.LayoutParams(ViewGroup.LayoutParams.WRAP_CONTENT, ViewGroup.LayoutParams.WRAP_CONTENT);
      params.endToEnd = ConstraintLayout.LayoutParams.PARENT_ID;
      params.startToStart = ConstraintLayout.LayoutParams.PARENT_ID;

      View tipView = getView(getViewKeyTextOtherCallTip());
      if (tipView != null) {
        params.topToBottom = tipView.getId();
      }
      newAddedView.setLayoutParams(params);
      viewGroup.addView(newAddedView);
    }
    // 隐藏麦克风图片按钮
    View muteAudioImage = getView(getViewKeyMuteImageAudio());
    if (muteAudioImage != null) {
      muteAudioImage.setVisibility(View.GONE);
    }
    // 隐藏麦克风文本说明
    View muteAudioText = getView(getViewKeyTextMuteAudioDesc());
    if (muteAudioText != null) {
      muteAudioText.setVisibility(View.GONE);
    }
    // 隐藏扬声器图片按钮
    View speakerImage = getView(getViewKeyImageSpeaker());
    if (speakerImage != null) {
      speakerImage.setVisibility(View.GONE);
    }
    // 隐藏扬声器文本说明
    View speakerText = getView(getViewKeyTextSpeakerDesc());
    if (speakerText != null) {
      speakerText.setVisibility(View.GONE);
    }
  }
}

```

`BaseP2pCallFragment` 提供的主要方法如下表所示。

| <div style="width: 150px">方法</div> | 参数 | <div style="width: 50px">返回</div> | 说明 |
| ---- | ---- | ---- | ---- |
| toUpdateUIState | `Integer` | - | 页面状态更新，执行时机在 `onCreateAction` 方法执行后，用户可根据更新类型执行不同的行为，目前支持 `P2PUIUpdateType.INIT` 和 `P2PUIUpdateType.CHANGE_CALL_TYPE`，页面创建完成后都会触发此方法的 `INIT` 类型调用。 |
| toCreateRootView | `LayoutInflater,ViewGroup,Bundle ` | `View` | 创建 Fragment 的 View，等同于 `onCreateView` 方法，<note type="notice">若重写此方法后需要同时重写 `toBindView` 否则会出现崩溃。</note> |
| toBindView | - | - | 用户可重写此方法，在此方法内调用 `bindView` 来进行 View 的绑定 |
| toRenderView | - | - | 此方法在 `toBindView` 执行后被调用，通过调用 `getView` 方法获取组件依赖的控件进行单击时间以及图标等设置，用户可重写此方法实现覆盖父类设置 |
| onCreateAction | - | - | 页面创建动作，对应 `onCreateView` 方法，在 `toRenderView` 方法后执行 |
| onDestroyAction | - | - | 页面销毁动作，对应 `onDestroyView` 方法 |
| bindView | `String,View` | - | 将 key 和对应的 View 绑定，绑定后，组件会通过相应的 key 获取 view 并实现单击或者显/隐控制等 |
| getView | `String` | `View` | 通过 key 获取对应绑定的 View，若未绑定返回 null |
| removeView | `String` | - | 移除对应 key 绑定的 View |

现有布局控件 `key` 说明如下表所示。所有定义均在 Fragment 父类 `BaseP2pCallFragment` 中。

| key | 控件默认类型 | 说明 |
| ---- | ---- | ---- |
| `viewKeyVideoViewPreview` | `NERtcVideoView` | 视频呼叫时本地视频预览控件 |
| `viewKeyVideoViewBig` | `NERtcVideoView` | 视频通话中大视频展示控件 |
| `viewKeyVideoViewSmall` | `NERtcVideoView` | 视频通话中小视频展示控件 |
| `viewKeyImageVideoShadeBig` | `ImageView` | 视频通话关闭视频时大视频的覆盖控件 |
| `viewKeyImageVideoShadeSmall` | `ImageView` | 视频通话关闭视频时小视频的覆盖控件 |
| `viewKeyTextRemoteVideoCloseTip` | `TextView` | 视频通话中远端视频关闭时文本提示控件 |
| `viewKeyImageBigBackground` | `ImageView` | 语音通话时大的背景图控件 |
| `viewKeyTextUserInnerAvatar` | `TextView` | 对端用户没有头像时展示文本头像控件 |
| `viewKeyImageUserInnerAvatar` | `ImageView` | 对端用户头像展示控件 |
| `viewKeyFrameLayoutUserAvatar` | `FrameLayout` | 头像整体父布局控件 |
| `viewKeyTextUserName` | `TextView` | 对端用户昵称文本控件 |
| `viewKeyTextOtherCallTip` | `TextView` | 呼叫/被叫/语音通话时文本提示控件 |
| `viewKeyImageCancel` | `ImageView` | 取消呼叫图片控件 |
| `viewKeyTextCancelDesc` | `TextView` | 取消呼叫文本说明控件 |
| `viewKeyImageReject` | `ImageView` | 拒绝接听图片控件 |
| `viewKeyTextRejectDesc` | `TextView` | 拒绝接听文本说明控件 |
| `viewKeyImageAccept` | `ImageView` | 接听图片控件 |
| `viewKeyTextAcceptDesc` | `TextView` | 接听文本说明控件 |
| `viewKeyImageHangup` | `ImageView` | 通话中挂断图片控件 |
| `viewKeyImageSwitchCamera` | `ImageView` | 切换摄像头方向图片控件 |
| `viewKeyImageSwitchType` | `ImageView` | 切换通话类型图片控件 |
| `viewKeyTextSwitchTypeDesc` | `TextView` | 切换通话类型文本说明控件 |
| `viewKeyTextSwitchTip` | `TextView` | 切换通话过程中提示文本控件 |
| `viewKeyImageSwitchTipClose` | `ImageView` | 切换通话过程中提示关闭图片控件 |
| `viewKeySwitchTypeTipGroup` | `Group` | 切换通话过程中整体提示组控件，用户控制 `viewKeyTextSwitchTip]` 和 `viewKeyImageSwitchTipClose` 的展示/隐藏 |
| `viewKeyMuteImageVideo` | `ImageView` | 摄像头开关图片控件 |
| `viewKeyMuteImageAudio` | `ImageView` | 本地麦克风开关图片控件 |
| `viewKeyTextMuteAudioDesc` | `TextView` | 本地麦克风开关文本说明控件 |
| `viewKeyImageSpeaker` | `ImageView` | 扬声器开关图片控件 |
| `viewKeyTextSpeakerDesc` | `TextView` | 扬声器开关文本说明控件 |
| `viewKeyTextConnectingTip` | `TextView` | 接听成功前，单击接听后的提示文本控件 |
| `viewKeyTextTimeCountdown` | `TextView` | 通话中倒计时文本控件 |

## 完全自实现 UI（不基于 Fragment）

如果您不想使用 Fragment 来修改自定义 UI，可以直接继承 `CommonCallActivity` 类来实现呼叫通话 UI 的修改。您可以使用该类的方法来执行呼叫相关的操作，并且可以根据自己的逻辑来定义所有的 UI 和行为。

::: note notice
在初始化呼叫组件时，不要忘记注册自定义的 Activity。
:::

操作步骤如下：

1. 创建页面 Activity。

    创建 `TestActivity` 页面，并让它继承 `CommonCallActivity`。在这个页面中，实现自己的业务逻辑，并调用呼叫流程方法。

    ::: note note
    此时 `P2PUIConfig` 中关于 UI 部分参数会失效。但前台服务开/关及配置仍然有效。
    :::

    示例代码如下：

    ```Java
    public class TestActivity extends CommonCallActivity {
        @Override
        protected int provideLayoutId() {
        return 0;
        }
    }
    ```

2. 在初始化呼叫组件时，将刚刚创建的 Activity 在组件中注册，示例代码如下：

    ```Java
    CallKitUIOptions options = new CallKitUIOptions.Builder()
        ......
        // 设置自定义的视频通话界面
        .p2pVideoActivity(TestActivity.class)
        .build();
    // 组件初始化
    CallKitUI.init(this, options);
    ```

## UI 层组件方法和参数

`CommonCallActivity` 提供的方法：

| <div style="width: 150px">方法</div> | 参数 | <div style="width: 50px">返回</div> | 说明 |
| ---- | ---- | ---- | ---- |
| getCallParam | - | `CallParam` | 呼叫/被叫时的必要参数 |
| getCallEngine | - | `NECallEngine` | 呼叫组件实例 |
| getUiConfig | - | `P2PUIConfig` | 获取 `provideUIConfig` 方法返回的实例 |
| isLocalMuteAudio | - | `Boolean` | 本地音频是否关闭采集 |
| isLocalMuteVideo | - | `Boolean` | 本地视频是否关闭采集 |
| isRemoteMuteVideo | - | `Boolean` | 对端用户是否关闭视频 |
| doOnCreate | `Bundle` | - | 对应页面 `onCreate` 方法 |
| configWindow | - | - | 可重写方法配置 window 相关配置 |
| provideLayoutId | - | `Int` | 返回页面布局 ID |
| provideUIConfig | `CallParam` | `P2PUIConfig` | 根据呼叫参数返回对应的页面配置，用于配置前台服务开启/关闭、大小窗单击切换等 |
| doMuteAudio | - | - | 修改本地当前音频采集状态，若当前为开启则执行后为关闭 |
| doMuteVideo | - | - | 修改本地当前视频采集状态，若当前为开启则执行后为关闭 |
| doSwitchCamera | - | - | 切换摄像头方向，默认为正向 |
| doCall | ` NEResultObserver<CommonResult<NECallInfo>>` | - | 主叫呼叫 |
| doAccept | `NEResultObserver<CommonResult<NECallInfo>>` | - | 被叫接受 |
| doHangup | `NEResultObserver<CommonResult<Void>>`, `String`, `String` | - | 终止通话 |
| showOverlayPermissionDialog | `View.OnClickListener` | - | 展示申请浮窗权限弹窗 |
| doShowFloatingWindow | - | - | 具有浮窗权限后，展示浮窗 |
| startVideoPreview | - | - | 开启视频预览 |
| stopVideoPreview | - | - | 关闭视频预览 |

`CallParam` 参数字段：

| 字段 | 类型 | 说明 |
| ---- | ---- | ---- |
| isCalled | `Boolean` | 通话中是否为被叫 |
| callType | `Int` | 通话类型请参考 `NECallType` |
| callerAccId | `String` | 通话主叫方 accId |
| calledAccId | `String` | 通话被叫方 accId |
| callExtraInfo | `String` | 扩展信息，透传到到被叫 onReceiveInvited |
| globalExtraCopy | `String` | 自定义的呼叫全局抄送信息，用户服务端接收抄送时设置自己的业务标识 |
| rtcChannelName | `String` | 呼叫时确定的 rtc 房间名称 |
| pushConfig | `NECallPushConfig` | 呼叫的推送配置 |
| extras | `Map<String, Object>` | 呼叫的 UI 页面传递扩展信息，类似 Intent |

`P2PUIConfig` 支持的配置内容：

| 配置项 | 说明 |
| ---- | ---- |
| showAudio2VideoSwitchOnTheCall | 是否展示通话中音频转视频按钮<br />默认 true |
| showVideo2AudioSwitchOnTheCall | 是否展示通话中视频转音频按钮<br />默认 true |
| closeVideoLocalUrl | 本端用户关闭摄像头时的图片 url 链接 |
| closeVideoLocalTip | 本端用户关闭摄像头时的文本提示 |
| closeVideoRemoteUrl | 对端用户关闭摄像头时的本端的图片 url 链接 |
| closeVideoRemoteTip | 对端用户关闭摄像头时的本端文本提示 |
| closeVideoType | 关闭视频模式，默认 `CLOSE_TYPE_MUTE` 详细见下文 |
| enableCanvasSwitch | 是否支持通话中单击小视频预览进行大小画面单击切换<br />默认 true |
| enableTextDefaultAvatar | 当没有头像时是否展示文字头像（取传入昵称的最后两个字）<br />默认 true |
| enableForegroundService | 是否通话中开启前台服务，可提高应用的优先级，避免在后台时被系统回收资源<br />默认 false |
| foregroundNotificationConfig | 通话中前台服务绑定的通知配置（图标，标题，内容，以及通道 ID） |
| customCallFragmentByKey | 配置自定义通话中 fragment 页面 |
| enableFloatingWindow | 配置是否开启小窗功能，默认 false 关闭 |
| enableVideoCalleePreview | 配置是否开启被叫视频预览，默认 false 关闭，**当配置 rtc 初始化模式为 `NECallInitRtcMode.IN_NEED_DELAY_TO_ACCEPT` 时，此功能不生效** |
| enableVirtualBlur | 配置是否支持通话视频虚化，默认 false 关闭<br />虚化功能说明，若需要开启虚化，在配置此开关 true 情况下，同时需要引入，`com.netease.yunxin:nertc-nenn` 和 `com.netease.yunxin:nertc-segment` 库，具体请参考 [集成音视频 SDK](https://doc.yunxin.163.com/nertc/docs/DcyNDc0ODI?platform=android) |

您可以设置当用户在界面上单击 **关闭摄像头** 按钮时，摄像头数据采集的模式。包括 3 种模式，区别和说明如下表所示。

| 模式 | 说明 |
| ---- | ---- |
| Constants.CLOSE_TYPE_MUTE | 用户在界面上单击 **关闭摄像头** 按钮时，不发布本地摄像头数据，但仍然采集摄像头数据。该模式下，用户单击开启摄像头后，界面能快速展示摄像头采集的数据。<br>默认为该模式。 |
| Constants.CLOSE_TYPE_DISABLE | 用户在界面上单击 **关闭摄像头** 按钮时，关闭本地摄像头数据采集及发布。 |
| Constants.CLOSE_TYPE_COMPAT | 兼容此前使用 `CLOSE_TYPE_MUTE` 模式后续希望更换为 `CLOSE_TYPE_DISABLE`。 |