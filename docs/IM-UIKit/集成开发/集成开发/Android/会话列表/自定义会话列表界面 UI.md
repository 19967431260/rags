<!--keywords: 自定义 UI,会话列表, UIKit,demo,IM UIKit,IMUIKit,Kit -->

网易云信 IM UIKit 支持本地会话组件（`localconvesationkit-ui`）和云端会话组件（`convesationkit-ui`），提供会话列表界面 UI 的自定义配置项，助您快速实现该界面的 UI 个性化定制。您也可在布局文件（`conversation_fragment.xml` 和 `local_conversation_fragment.xml`）中直接修改源码实现您所需的 UI 风格。

::: note notice
请确保您在加载会话列表界面之前完成该界面的 UI 自定义，加载的对象包括 `ConversationFragment` 和 `LocalConversationFragment` 的 Activity 和您的 Application。
:::

<div id="main-content">

## 自定义功能概述

### UI 元素自定义

<div id="examples">

会话列表界面可自定义的 UI 元素包括但不限于下图中的标注项。

<img src="https://yx-web-nosdn.netease.im/common/c521029ed687c6b63874ee599336716b/会话列表.png" style="width:80%;border: 1px solid #BFBFBF;">

</div> 

您可通过 `ConversationUIConfig` 和 `LocalConversationUIConfig` 类中的个性化配置项修改会话列表中界面 UI 元素的样式。

<div style="width:151px">属性</div> | 类型 | 说明
---- | ---- | ----
`showTitleBar` | boolean | 是否展示界面顶部的标题栏，具体自定义示例见下文的 [隐藏标题栏](#隐藏标题栏)
`showTitleBarLeftIcon` | boolean | 是否展示标题栏左侧图标，具体自定义示例见下文的 [修改标题栏图标](#修改标题栏图标)
`showTitleBarRightIcon` | boolean | 是否展示标题栏最右侧图标，具体自定义示例见下文的 [修改标题栏图标](#修改标题栏图标)
`showTitleBarRight2Icon` | boolean | 是否展示标题栏次最右侧图标，具体自定义示例见下文的 [修改标题栏图标](#修改标题栏图标)
`showConversationTopAIList` | boolean | 是否标题和会话列之间的置顶会话列表(当前只适用于 AI 数字人会话)，具体自定义示例见下文的 [隐藏置顶会话列表](#隐藏置顶会话列表)
`titleBarLeftRes` | int | 标题栏左侧图标 ID
`titleBarRightRes` | int | 标题栏最右侧图标 ID
`titleBarRight2Res` | int | 标题栏次最右侧图标 ID
`titleBarTitle` | String | 标题栏的文案
`titleBarTitleColor` | int | 标题栏的颜色值
`itemTitleColor` | int | 会话标题的字体颜色，具体示例见下文的 [修改会话字体颜色和大小](#修改会话字体颜色和大小)
`itemTitleSize` | int | 会话标题的字体大小
`itemBackground` | Drawable | 未被置顶的会话项的背景色，具体自定义示例见下文的 [修改会话项的背景色](#修改会话项的背景色)
`itemStickTopBackground` | Drawable | 置顶的会话项的背景色，具体自定义示例见下文的 [修改会话项的背景色](#修改会话项的背景色)
`itemContentColor` | int | 会话消息缩略内容的字体颜色
`itemContentSize` | int | 会话消息缩略内容的字体大小，具体示例见下文的 [修改会话字体颜色和大小](#修改会话字体颜色和大小)
`itemDateColor` | int | 会话时间的字体颜色，具体示例见下文的 [修改会话字体颜色和大小](#修改会话字体颜色和大小)
`itemDateSize` | int | 会话时间的字体大小
`avatarCornerRadius` | float | 会话列表中会话头像的圆角，0 代表方形，30dp 代表圆形。这里您需要自行将 dp（density-independent pixels）单位转换为像素（px）单位。
`titleBarRightClick` | View.OnClickListener | 标题栏最右侧按钮单击事件
`titleBarRight2Click` | View.OnClickListener | 标题栏次最右侧按钮单击事件
`titleBarLeftClick` | View.OnClickListener | 标题栏左侧按钮单击事件
`itemClickListener` | ItemClickListener | 会话列表单击事件，包括单击和长按事件
`conversationFactory` | IConversationFactory | 会话列表 `ViewHolder` 构造器，用于完成会话列表中 `ViewHolder` 的创建和绑定，可参考默认实现 `DefaultViewHolderFactory`
`itemStickTopBackground` | Drawable | 置顶会话背景
`itemBackground` | Drawable | 非置顶会话背景
`customLayout` | IConversationViewLayout | 自定义界面 UI 接口，回调中会传入会话列表界面的 UI 布局，您可以进行 UI 元素调整。

### 界面布局自定义

除了界面的 UI 元素，您也可对界面的布局进行自定义，具体示例请参考下文的 [在会话列表顶部增加提示条](#在会话列表顶部增加提示条)。

<div id="examples">

会话列表界面的默认视图布局如下图所示。

<img alt="会话列表布局.png" src="https://yx-web-nosdn.netease.im/common/2bc085d71f97ed21e57d3447db6e5406/会话列表布局.png" style="width:80%;border: 1px solid #BFBFBF;">

</div> 

界面上各视图的说明如下：

<div style="width:141px">属性</div> | 类型 | 说明
---- | ---- | ----
`TitleBar` | BackTitleBar | 会话列表界面标题视图，可通过 `ConversationLayout` 的 `getTitleBar()` 来获取视图进行样式修改
`BodyTopLayout` | FrameLayout | 会话列表上方的小块视图，可通过 `ConversationLayout` 的 `getBodyTopLayout()` 来获取视图进行样式修改。可用于在会话列表和顶部的界面标题中间增加新的 UI 元素
`BodyLayout` | LinearLayout | 会话列表界面的列表视图，可通过 `ConversationLayout` 的 `getBodyLayout()` 来获取视图进行样式修改。布局中包含 `ConversationView` 会话列表和通知文本。通知文本的视图的 ID 为 `conversationNetworkErrorTv`，可用于断网提示
`BottomLayout` | FrameLayout | 会话列表底部的小块视图，可通过 `ConversationLayout` 的 `getBottomLayout()` 来获取视图进行样式修改。用于在会话列表底部增加新的 UI 元素
`ConversationView` | ConversationView | 会话列表界面的列表视图，可通过 `ConversationLayout` 的 `getConversationView()` 来获取视图进行样式修改
`ErrorTextView` | TextView | 会话列表界面错误提示视图，可通过 `ConversationLayout` 的 `getErrorTextView()` 来获取视图进行样式修改

::: note note
在会话界面（即聊天界面），上述界面元素都可以通过 `ConversationLayout` 提供的相应接口获取。`ConversationLayout` 的获取可参考上述的 `ConversationUIConfig:customLayout` 来获取整个界面视图。示例代码可参考下文的 [在会话列表顶部增加提示条](#在会话列表顶部增加提示条)。
:::

## 自定义示例

<a id="隐藏标题栏"></a>

### 隐藏标题栏

- 示例代码

    :::::: div linked-codes
    ::: code 本地会话

    ```Java
    //1、实现单击事件
    LocalConversationUIConfig conversationUIConfig = new LocalConversationUIConfig();
    //2、设置 TitleBar 不可见
    conversationUIConfig.showTitleBar = false;
    //3、将自定义事件设置到 ConversationKitClient 即可
    LocalConversationKitClient.setConversationUIConfig(config);
    ```

    :::
    ::: code 云端会话
    ```Java
    //1、实现单击事件
    ConversationUIConfig conversationUIConfig = new ConversationUIConfig();
    //2、设置 TitleBar 不可见
    conversationUIConfig.showTitleBar = false;
    //3、将自定义事件设置到 ConversationKitClient 即可
    ConversationKitClient.setConversationUIConfig(config);
    ```
    :::
    ::::::
    ::: note note
    除此之外，还可以隐藏标题栏中的标题图标和右侧按钮。请参考上文的个性化配置项列表。
    :::

<div id="examples">

- 效果对比

    默认 | 自定义后
    ---- | ----
    <img alt="conversation_01_resized.png" src="https://yx-web-nosdn.netease.im/common/ef504adde369017107ee8126faba9748/conversation_01_resized.png" style="width:80%;border: 1px solid #BFBFBF;"> | <img alt="conversation_01_resized.png" src="https://yx-web-nosdn.netease.im/common/a4a21c444d2f14c9595609089aec778a/conversation_02_resized.png" style="width:80%;border: 1px solid #BFBFBF;">

</div> 

<a id="隐藏置顶会话列表"></a>

### 隐藏置顶会话列表

- 示例代码
    :::::: div linked-codes
    ::: code 本地会话
    ```Java
    //1、实现单击事件
    LocalConversationUIConfig conversationUIConfig = new LocalConversationUIConfig();
    //2、设置 TitleBar 不可见
    conversationUIConfig.showConversationTopAIList = false;
    //3、将自定义事件设置到 ConversationKitClient 即可
    LocalConversationKitClient.setConversationUIConfig(config);
    ```
    :::
    ::: code 云端会话
    ```Java
    //1、实现单击事件
    ConversationUIConfig conversationUIConfig = new ConversationUIConfig();
    //2、设置 TitleBar 不可见
    conversationUIConfig.showConversationTopAIList = false;
    //3、将自定义事件设置到 ConversationKitClient 即可
    ConversationKitClient.setConversationUIConfig(config);
    ```
    :::
    ::::::
    ::: note note
    除此之外，还可以隐藏标题栏中的标题图标和右侧按钮。请参考上文的个性化配置项列表。
    :::

<div id="examples">

- 效果对比

    默认 | 自定义后
    ---- | ----
    <img alt="数字人.png" src="https://yx-web-nosdn.netease.im/common/8539cd0e3d7e96a190d47ab7d787b303/数字人.png" style="width:80%;border: 0px solid #BFBFBF;"> | <img alt="数字人.png" src="https://yx-web-nosdn.netease.im/common/df8accf5eea932c5a491b2b64b33f7d4/隐藏数字人置顶.png" style="width:80%;border: 0px solid #BFBFBF;">

</div> 

<a id="修改标题栏图标"></a>

### 修改标题栏图标

- 示例代码

    :::::: div linked-codes
    ::: code 本地会话
    ```Java
    //1、实现单击事件
    LocalConversationUIConfig conversationUIConfig = new LocalConversationUIConfig();
    //2、设置 TitleBar 右侧图标和标题内容
    conversationUIConfig.titleBarRight2Res = R.drawable.ic_about;
    conversationUIConfig.titleBarRightRes = R.drawable.ic_collect;
    conversationUIConfig.titleBarTitle = "您好 IM";
    //3、将自定义事件设置到 ConversationKitClient 即可
    LocalConversationKitClient.setConversationUIConfig(config);
    ```
    :::
    ::: code 云端会话
    ```Java
    //1、实现单击事件
    ConversationUIConfig conversationUIConfig = new ConversationUIConfig();
    //2、设置 TitleBar 右侧图标和标题内容
    conversationUIConfig.titleBarRight2Res = R.drawable.ic_about;
    conversationUIConfig.titleBarRightRes = R.drawable.ic_collect;
    conversationUIConfig.titleBarTitle = "您好 IM";
    //3、将自定义事件设置到 ConversationKitClient 即可
    ConversationKitClient.setConversationUIConfig(config);
    ```

    :::
    ::::::
    ::: note note
    除此之外，还可以修改标题栏的字体颜色、字体大小和左侧图标等，请参考上文的个性化配置项列表。
    :::

<div id="examples">

- 效果对比

    默认 | 自定义后
    ---- | ----
    <img alt="conversation_01_resized.png" src="https://yx-web-nosdn.netease.im/common/ef504adde369017107ee8126faba9748/conversation_01_resized.png" style="width:80%;border: 1px solid #BFBFBF;"> | <img alt="conversation_01_resized.png" src="https://yx-web-nosdn.netease.im/common/f17d4531a2564972bcf525bc817c8920/conversation_03_resized.png" style="width:80%;border: 1px solid #BFBFBF;">

</div> 

<a id="修改会话字体颜色和大小"></a>

### 修改会话字体颜色和大小

- 示例代码

    :::::: div linked-codes
    ::: code 本地会话
    ```Java
    //1、实现单击事件
    LocalConversationUIConfig conversationUIConfig = new LocalConversationUIConfig();
    //2、Item 中标题字体颜色、内容字体大小和右侧时间字体颜色
    conversationUIConfig.itemTitleColor = context.getResources().getColor(R.color.color_blue_3a9efb);
    conversationUIConfig.itemContentSize = 23;
    conversationUIConfig.itemDateColor = context.getResources().getColor(R.color.color_blue);
    //3、将自定义事件设置到 ConversationKitClient 即可
    LocalConversationKitClient.setConversationUIConfig(config);
    ```
    :::
    ::: code 云端会话
    ```Java
    //1、实现单击事件
    ConversationUIConfig conversationUIConfig = new ConversationUIConfig();
    //2、Item 中标题字体颜色、内容字体大小和右侧时间字体颜色
    conversationUIConfig.itemTitleColor = context.getResources().getColor(R.color.color_blue_3a9efb);
    conversationUIConfig.itemContentSize = 23;
    conversationUIConfig.itemDateColor = context.getResources().getColor(R.color.color_blue);
    //3、将自定义事件设置到 ConversationKitClient 即可
    ConversationKitClient.setConversationUIConfig(config);
    ```
    :::
    ::::::
    ::: note note
    除此之外，还可以修改会话中的标题、内容和时间的字体颜色、字体大小，请参考上文的个性化配置项列表。
    ::::

<div id="examples">

- 效果对比

    默认 | 自定义后
    ---- | ----
    <img alt="conversation_01_resized.png" src="https://yx-web-nosdn.netease.im/common/ef504adde369017107ee8126faba9748/conversation_01_resized.png" style="width:80%;border: 1px solid #BFBFBF;"> | <img alt="conversation_01_resized.png" src="https://yx-web-nosdn.netease.im/common/0ef508e66a1da562e984dbb8737de6b7/conversation_04_resized.png" style="width:80%;border: 1px solid #BFBFBF;">

</div> 

### 修改会话项的背景色

在会话列表中，单个会话项的背景色有两种，按该会话项是否被置顶进行区分。未被置顶会话项的背景色和置顶会话项的背景色均支持自定义。

- 示例代码

    :::::: div linked-codes
    ::: code 本地会话
    ```Java
    //1、实现单击事件
    LocalConversationUIConfig conversationUIConfig = new LocalConversationUIConfig();
    //2、会话项的背景色修改
    conversationUIConfig.itemBackground = new ColorDrawable(context.getResources().getColor(R.color.color_be65d9));
    conversationUIConfig.itemStickTopBackground = new ColorDrawable(context.getResources().getColor(R.color.color_blue_3a9efb));
    //3、将自定义事件设置到 ConversationKitClient 即可
    LocalConversationKitClient.setConversationUIConfig(config);
    ```

    :::
    ::: code 云端会话
    ```Java
    //1、实现单击事件
    ConversationUIConfig conversationUIConfig = new ConversationUIConfig();
    //2、会话项的背景色修改
    conversationUIConfig.itemBackground = new ColorDrawable(context.getResources().getColor(R.color.color_be65d9));
    conversationUIConfig.itemStickTopBackground = new ColorDrawable(context.getResources().getColor(R.color.color_blue_3a9efb));
    //3、将自定义事件设置到 ConversationKitClient 即可
    ConversationKitClient.setConversationUIConfig(config);
    ```

    :::
    ::::::

<div id="examples">

- 效果对比

    默认 | 自定义后
    ---- | ----
    <img alt="conversation_01_resized.png" src="https://yx-web-nosdn.netease.im/common/ef504adde369017107ee8126faba9748/conversation_01_resized.png" style="width:80%;border: 1px solid #BFBFBF;"> | <img alt="conversation_01_resized.png" src="https://yx-web-nosdn.netease.im/common/449a8383b5852d1fee83c392caaa4b61/conversation_05_resized.png" style="width:80%;border: 1px solid #BFBFBF;">

</div> 

### 在会话列表顶部增加提示条

- 示例代码（基础版）

    :::::: div linked-codes
    ::: code 本地会话
    ```Java
    //1、实现单击事件
    LocalConversationUIConfig conversationUIConfig = new LocalConversationUIConfig();
    //2、对会话列表界面布局进行修改
    conversationUIConfig.customLayout =
    new IConversationViewLayout() {
        @Override
         public void customizeConversationLayout(LocalConversationBaseFragment fragment) {

                 // 基础版皮肤
                  if (fragment instanceof ConversationFragment){
                      LocalConversationFragment conversationFragment = (LocalConversationFragment) fragment;
                      TextView contentTv = new TextView(conversationFragment.getContext());
                      contentTv.setText("【温馨提示】欢迎使用运行 IM，在使用过程中如果遇到什么问题，请及时与我们联系。");
                      contentTv.setTextColor(Color.parseColor("#333333"));
                      contentTv.setBackgroundColor(Color.parseColor("#FFF8DC"));
                      contentTv.setPadding(8,8,8,8);
                      FrameLayout.LayoutParams layoutParams = new FrameLayout.LayoutParams(ViewGroup.LayoutParams.MATCH_PARENT,150);
                      layoutParams.setMargins(16,12,16,12);
                      conversationFragment.getBodyTopLayout().addView(contentTv,layoutParams);
                  }
              }
        };
    //3、将自定义事件设置到 LocalConversationKitClient 即可
    LocalConversationKitClient.setConversationUIConfig(config);
    ```
    :::
    ::: code 云端会话
    ```Java
    //1、实现单击事件
    ConversationUIConfig conversationUIConfig = new ConversationUIConfig();
    //2、对会话列表界面布局进行修改
    conversationUIConfig.customLayout =
    new IConversationViewLayout() {
        @Override
         public void customizeConversationLayout(ConversationBaseFragment fragment) {

                 // 基础版皮肤
                  if (fragment instanceof ConversationFragment){
                      ConversationFragment conversationFragment = (ConversationFragment) fragment;
                      TextView contentTv = new TextView(conversationFragment.getContext());
                      contentTv.setText("【温馨提示】欢迎使用运行 IM，在使用过程中如果遇到什么问题，请及时与我们联系。");
                      contentTv.setTextColor(Color.parseColor("#333333"));
                      contentTv.setBackgroundColor(Color.parseColor("#FFF8DC"));
                      contentTv.setPadding(8,8,8,8);
                      FrameLayout.LayoutParams layoutParams = new FrameLayout.LayoutParams(ViewGroup.LayoutParams.MATCH_PARENT,150);
                      layoutParams.setMargins(16,12,16,12);
                      conversationFragment.getBodyTopLayout().addView(contentTv,layoutParams);
                  }
              }
        };
    //3、将自定义事件设置到 ConversationKitClient 即可
    ConversationKitClient.setConversationUIConfig(config);
    ```
    :::
    ::::::

- 示例代码（通用版）

    :::::: div linked-codes
    ::: code 本地会话
    ```Java
    //1、实现单击事件
    LocalConversationUIConfig conversationUIConfig = new LocalConversationUIConfig();
    //2、对会话列表界面布局进行修改
    conversationUIConfig.customLayout =
    new IConversationViewLayout() {
        @Override
         public void customizeConversationLayout(LocalConversationBaseFragment fragment) {

                  // 通用版皮肤
                   if (fragment instanceof FunConversationFragment){
                      FunLocalConversationFragment conversationFragment = (FunLocalConversationFragment)fragment;
                      TextView contentTv = new TextView(conversationFragment.getContext());
                      contentTv.setText("【温馨提示】欢迎使用运行 IM，在使用过程中如果遇到什么问题，请及时与我们联系。");
                      contentTv.setTextColor(Color.parseColor("#333333"));
                      contentTv.setBackgroundColor(Color.parseColor("#FFF8DC"));
                      contentTv.setPadding(8,8,8,8);
                      FrameLayout.LayoutParams layoutParams = new FrameLayout.LayoutParams(ViewGroup.LayoutParams.MATCH_PARENT,150);
                      layoutParams.setMargins(16,12,16,12);
                      conversationFragment.getBodyTopLayout().addView(contentTv,layoutParams);
                  }

              }
        };
    //3、将自定义事件设置到 ConversationKitClient 即可
    LocalConversationKitClient.setConversationUIConfig(config);
    ```
    :::
    ::: code 云端会话
    ```Java
    //1、实现单击事件
    ConversationUIConfig conversationUIConfig = new ConversationUIConfig();
    //2、对会话列表界面布局进行修改
    conversationUIConfig.customLayout =
    new IConversationViewLayout() {
        @Override
         public void customizeConversationLayout(ConversationBaseFragment fragment) {

                  // 通用版皮肤
                   if (fragment instanceof FunConversationFragment){
                      FunConversationFragment conversationFragment = (FunConversationFragment)fragment;
                      TextView contentTv = new TextView(conversationFragment.getContext());
                      contentTv.setText("【温馨提示】欢迎使用运行 IM，在使用过程中如果遇到什么问题，请及时与我们联系。");
                      contentTv.setTextColor(Color.parseColor("#333333"));
                      contentTv.setBackgroundColor(Color.parseColor("#FFF8DC"));
                      contentTv.setPadding(8,8,8,8);
                      FrameLayout.LayoutParams layoutParams = new FrameLayout.LayoutParams(ViewGroup.LayoutParams.MATCH_PARENT,150);
                      layoutParams.setMargins(16,12,16,12);
                      conversationFragment.getBodyTopLayout().addView(contentTv,layoutParams);
                  }

              }
        };
    //3、将自定义事件设置到 ConversationKitClient 即可
    ConversationKitClient.setConversationUIConfig(config);
    ```
    :::
    ::::::

<div id="examples">

- 效果对比

    默认 | 自定义后
    ---- | ----
    <img alt="conversation_01_resized2.png" src="https://yx-web-nosdn.netease.im/common/6dbafbc42e3360c14e4ef8f60521d0a4/conversation_01_resized2.png" style="width:80%;border: 1px solid #BFBFBF;"> | <img alt="conversation_01_resized2.png" src="https://yx-web-nosdn.netease.im/common/d8eab13556e25be96792a7ea62305620/conversation_06_resized.png" style="width:80%;border: 1px solid #BFBFBF;">

</div> 

## 源码导读

### 界面布局（基础版）

:::::: div linked-codes
::: code 本地会话
`LocalConversation-ui` 模块中的布局文件 `local_conversation_fragment.xml` 支持对界面布局进行调整，包括界面元素调整和界面背景修改等。布局中的内容具体如下：

```XML
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    xmlns:app="http://schemas.android.com/apk/res-auto">

    // Title Bar
    <com.netease.yunxin.kit.common.ui.widgets.TitleBarView .../>

    // Title Bar 与会话列表的分割线
    <View android:id="@+id/conversation_line" ... />

    // 会话列表内容
    <LinearLayout ...>

      // 断网提示 Tips
      <TextView android:id="@+id/conversation_network_error_tv" ... />

      // 会话列表 View，里面封装了 RecyclerView
      <com.netease.yunxin.kit.conversationkit.local.ui.view.ConversationView
          android:id="@+id/conversation_view" .../>
    </LinearLayout>
</androidx.constraintlayout.widget.ConstraintLayout>
```
:::
::: code 云端会话
`Conversation-ui` 模块中的布局文件 `conversation_fragment.xml` 支持对界面布局进行调整，包括界面元素调整和界面背景修改等。布局中的内容具体如下：

```XML
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    xmlns:app="http://schemas.android.com/apk/res-auto">

    // Title Bar
    <com.netease.yunxin.kit.common.ui.widgets.TitleBarView .../>

    // Title Bar 与会话列表的分割线
    <View android:id="@+id/conversation_line" ... />

    // 会话列表内容
    <LinearLayout ...>

      // 断网提示 Tips
      <TextView android:id="@+id/conversation_network_error_tv" ... />

      // 会话列表 View，里面封装了 RecyclerView
      <com.netease.yunxin.kit.conversationkit.ui.view.ConversationView
          android:id="@+id/conversation_view" .../>
    </LinearLayout>
</androidx.constraintlayout.widget.ConstraintLayout>
```
:::
::::::

### 界面布局（通用版）

:::::: div linked-codes
::: code 本地会话
`LocalConversation-ui` 模块中的布局文件 `fun_local_conversation_fragment.xml` 支持对界面布局进行调整，包括界面元素调整和界面背景修改等。布局中的内容具体如下：

```XML
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    xmlns:app="http://schemas.android.com/apk/res-auto">

    // Title Bar
    <com.netease.yunxin.kit.common.ui.widgets.TitleBarView .../>

    // Title Bar 与会话列表的分割线
    <View android:id="@+id/conversation_line" ... />

    // 会话列表内容
    <LinearLayout ...>

      // 断网提示 Tips
      <TextView android:id="@+id/conversation_network_error_tv" ... />

      // 会话列表 View，里面封装了 RecyclerView
      <com.netease.yunxin.kit.conversationkit.local.ui.view.ConversationView
          android:id="@+id/conversation_view" .../>
    </LinearLayout>
</androidx.constraintlayout.widget.ConstraintLayout>
```
:::
::: code 云端会话
`Conversation-ui` 模块中的布局文件 `fun_conversation_fragment.xml` 支持对界面布局进行调整，包括界面元素调整和界面背景修改等。布局中的内容具体如下：

```XML
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    xmlns:app="http://schemas.android.com/apk/res-auto">

    // Title Bar
    <com.netease.yunxin.kit.common.ui.widgets.TitleBarView .../>

    // Title Bar 与会话列表的分割线
    <View android:id="@+id/conversation_line" ... />

    // 会话列表内容
    <LinearLayout ...>

      // 断网提示 Tips
      <TextView android:id="@+id/conversation_network_error_tv" ... />

      // 会话列表 View，里面封装了 RecyclerView
      <com.netease.yunxin.kit.conversationkit.ui.view.ConversationView
          android:id="@+id/conversation_view" .../>
    </LinearLayout>
</androidx.constraintlayout.widget.ConstraintLayout>
```
:::
::::::

### 会话列表

`ConversationView` 为会话列表的实现类，是对 `RecyclerView` 和 `ConversationAdapter` 的封装，同时提供用于数据更新的方法，具体如下:

<div style="width:151px">方法</div> | 入参类型 | 说明
---- | ---- | ----
`setLoadMoreListener` | `ILoadListener` | 加载更多监听，当界面滑动到底部会触发，如果 `ILoadListener` 中 `hasMore` 返回 `false` 则不再触发
`setItemClickListener` | `ViewHolderClickListener` | 设置会话列表单击事件，分为单击和长按
`setViewHolderFactory` | `IConversationFactory` | 列表 `Adapter` 的 `ViewHolder` 构造器
`setData` | List<ConversationBean> | 设置会话列表数据，会对已有数据进行清理
`addData` | List<ConversationBean> | 添加会话列表数据，添加到已有数据之后
`update` | List<ConversationBean> | 更新会话列表数据，根据会话 ID 进行更新
`updateUserInfo` | List<UserInfo> | 更新会话用户数据，根据会话 ID 进行更新，一般用于更新用户头像、名称等的修改
`updateFriendInfo` | List<FriendInfo> | 更新会话用户数据，根据会话 ID 进行更新，一般用于更新好友昵称
`updateTeamInfo` | List<Team> | 更新会话用户数据，根据会话 ID 进行更新，一般用于更新群或者讨论组信息，群名称、群头像等
`updateMuteInfo` | `MuteListChangedNotify` | 更新消息提醒设置

### 会话列表 UI

:::::: div linked-codes
::: code 基础版
会话列表中存在两种类型的 `ViewHolder`，即 `ConversationP2PViewHolder` 和 `ConversationTeamViewHolder`。

- `ConversationP2PViewHolder` 代表单聊会话，其布局文件为 `conversation_view_holder.xml`，可以在该文件中调整其布局结构。
- `ConversationTeamViewHolder` 代表群聊会话，其布局文件为 `conversation_view_holder.xml`，可以在该文件中调整其布局结构。
:::
::: code 通用版
会话列表中存在两种类型的 `ViewHolder`，即 `FunConversationP2PViewHolder` 和 `FunConversationTeamViewHolder`。

- `P2PViewHolder` 代表单聊会话，其布局文件为 `fun_conversation_view_holder.xml`，可以在该文件中调整其布局结构。
- `TeamViewHolder` 代表群聊会话，其布局文件为 `fun_Conversation_view_holder.xml`，可以在该文件中调整其布局结构。
:::
::::::

### 其他

:::::: div linked-codes
::: code 本地会话
<div style="width:151px">自定义配置</div> | 说明
---- | ----
修改会话列表中单击和长按事件 | 通过 `LocalConversationBaseFragment` 中 `getViewHolderClickListener` 方法中进行修改
修改 Title Bar 最右侧按钮单击事件 | <ul><li>基础版：通过 `LocalConversationFragment` 中 `initView` 方法中的 `viewBinding.conversationView.viewBinding.conversationTitleBar.setRightImageClick()` 进行修改。</li><li>通用版：通过 `FunLocalConversationFragment` 中 `initView` 方法中的 `viewBinding.conversationView.viewBinding.conversationTitleBar.setRightImageClick()` 进行修改。</li></ul>
构造最右侧按钮弹窗中的选项内容 | <ul><li>基础版：通过 `PopItemFactory` 类构造，当前默认设置为添加好友、创建讨论组和创建高级群。</li><li>通用版：通过 `FunPopItemFactory` 类构造，当前默认设置为添加好友、创建讨论组和创建高级群。</li></ul>
实现长按置顶会话和删除会话弹窗 | 请参考 `LocalConversationBaseFragment` 中 `showStickDialog` 方法
:::
::: code 云端会话
<div style="width:151px">自定义配置</div> | 说明
---- | ----
修改会话列表中单击和长按事件 | 通过 `ConversationBaseFragment` 中 `getViewHolderClickListener` 方法中进行修改
修改 Title Bar 最右侧按钮单击事件 | <ul><li>基础版：通过 `ConversationFragment` 中 `initView` 方法中的 `viewBinding.conversationView.viewBinding.conversationTitleBar.setRightImageClick()` 进行修改。</li><li>通用版：通过 `FunConversationFragment` 中 `initView` 方法中的 `viewBinding.conversationView.viewBinding.conversationTitleBar.setRightImageClick()` 进行修改。</li><ul>
构造最右侧按钮弹窗中的选项内容 | <ul><li>基础版：通过 `PopItemFactory` 类构造，当前默认设置为添加好友、创建讨论组和创建高级群。</li><li>通用版：通过 `FunPopItemFactory` 类构造，当前默认设置为添加好友、创建讨论组和创建高级群。</li></ul>
实现长按置顶会话和删除会话弹窗 | 请参考 `ConversationBaseFragment` 中 `showStickDialog` 方法
:::
::::::

</div> 