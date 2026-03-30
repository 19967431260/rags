IM UIKit 通讯录模块（`contactkit-ui`）提供通讯录界面的 UI 自定义配置项目，助您快速实现该界面的 UI 个性化定制。您也可以直接修改该界面的布局文件自定义 UI 风格。

::: note notice
请确保在加载通讯录界面之前完成该界面的 UI 自定义，加载的对象包括 `ContactFragment` 的 `Activity` 和您的 `Application`。
:::

<div id="main-content">

## 自定义功能概述

### UI 元素自定义

<div id="examples">

通讯录界面可自定义的 UI 元素包括但不限于下图中的标注项。

<img style="width:80%;border: 1px solid #BFBFBF;" src="https://yx-web-nosdn.netease.im/common/76493061b5ae7c9188f5966127b0bc6f/通讯录界面.PNG" />

</div>

您可通过 `ContactKit-ui` 的 `ContactUIConfig` 属性所提供的个性化配置项修改该界面 UI 元素的样式，具体如下：

<div style="width:150px">属性</div> | 类型 | 说明
---- | ---- | ----
`showTitleBar` | boolean | 是否展示标题栏，具体自定义示例请参考下文的 [隐藏界面标题栏](#隐藏界面标题栏)
`showTitleBarRightIcon` | boolean | 是否展示标题栏的最右侧图标
`showTitleBarRight2Icon` | boolean | 是否展示标题栏的次最右侧图标，具体自定义示例请参考下文的 [修改界面标题栏字体颜色和图标](#修改界面标题栏字体颜色和图标)
`titleBarRightRes` | int | 标题栏的最右侧图标的 ID
`titleBarRight2Res` | int | 标题栏的次最右侧图标的 ID
`title` | String | 标题栏文案
`titleColor` | int | 标题栏字体颜色，具体自定义示例请参考下文的 [修改界面标题栏字体颜色和图标](#修改界面标题栏字体颜色和图标)
`showHeader` | int | 是否在通讯录界面显示头部模块，具体自定义示例请参考下文的 [隐藏头部模块](#隐藏头部模块)
`headerData` | List`<ContactEntranceBean>` | 头部模块的数据，如果不为空，则覆盖已有数据
`contactAttrs` | `ContactListViewAttrs` | 通讯录好友列表中 UI 属性设置，包括好友昵称的字体、好友头像、索引字体、颜色等，具体自定义示例请参考下文的 [修改通讯录列表字体颜色](#修改通讯录列表字体颜色)
`itemClickListeners` | `SparseArray<IContactClickListener>` | 好友列表的单击事件，由于列表中包含多种类型数据，所以采用 SparseArray，KEY 值即为类型，当前通讯录中包含的类型为 `IViewTypeConstant.CONTACT_ACTION_ENTER`(值为 `1`) 和 `IViewTypeConstant.CONTACT_FRIEND`(值为 `1`)类型，具体配置示例请参考下文的 [修改头部模块](#修改头部模块)
`viewHolderFactory` | `IContactFactory` | 通讯录好友列表 `ViewHolder` 构造器，用于列表中 `ViewHolder` 的创建和绑定，可参考默认实现的 `ContactDefaultFactory`
`customLayout` | `IContactViewLayout` | 通讯录好友列表界面个性化配置，在该接口中会返回

### 界面布局自定义

<div id="examples">

除了界面的 UI 元素，您也可对界面的布局进行自定义，通讯录界面的默认布局如下图所示。

<img style="width:80%;border: 1px solid #BFBFBF;" src="https://yx-web-nosdn.netease.im/common/ead6078851f333d30f56d4131044bae5/通讯录界面布局.png" />

</div>

该界面各视图的说明如下：

<div style="width:140px">属性</div> | 类型 | 说明
---- | ---- | ----
`TitleBar` | BackTitleBar | 通讯录列表界面标题视图，可通过 `ContactLayout` 的 `getTitleBar()` 来获取视图进行样式修改
`BodyTopLayout` | FrameLayout | 好友列表上方的小块视图，可通过 `ContactLayout` 的 `getBodyTopLayout()` 来获取视图进行样式修改。该视图用于在通讯录列表和顶部界面标题中间增加新的 UI 元素。具体自定义示例请参考下文的 [在头部模块增加提示消息](#在头部模块增加提示消息)
`BodyLayout` | FrameLayout | 通讯录界面的主题视图，可通过 `ContactLayout` 的 `getBodyLayout()` 来获取视图进行样式修改。该视图布局中包含 `ContactListView` 通讯录好友列表视图
`BottomLayout` | FrameLayout | 通讯录好友列表下方的小块视图，可通过 `ContactLayout` 的 `getBottomLayout()` 来获取视图进行样式修改。该视图用于在通讯录列表底部增加新的 UI 元素
`ContactListView` | ContactListView | 通讯录好友列表视图，可通过 `ContactLayout` 的 `getContactListView()` 来获取视图进行样式修改

::: note note
在会话界面（即聊天界面），上述界面元素都可以通过 `ContactLayout` 提供的相应接口获取。`ContactLayout` 的获取可参考上述的 `ContactUIConfig:customLayout` 来获取整个界面视图。示例代码可参考 [在头部模块增加提示消息](#在头部模块增加提示消息)。
:::

## 自定义示例

### 隐藏界面标题栏

- 示例代码如下：

    ```Java
    //1、创建个性化定制对象
    ContactUIConfig contactUIConfig = new ContactUIConfig();
    //2、设置 TitleBar 不可见
    contactUIConfig.showTitleBar = false;
    //3、将自定义事件设置到 ContactKitClient 即可
    ContactKitClient.setContactUIConfig(contactUIConfig);
    ```
    ::: note note
    除此之外，还可以隐藏标题栏中的最右侧图标题和次最右侧按钮。请参考上文的个性化配置项列表。
    :::

<div id="examples">

- 效果对比

    默认 | 自定义后
    ---- | ----
    <img style="width:80%;border: 1px solid #BFBFBF;" src="https://yx-web-nosdn.netease.im/common/c6e107553a2b6bafb5421af1f6aab405/contact_01.png" /> | <img style="width:80%;border: 1px solid #BFBFBF;" src="https://yx-web-nosdn.netease.im/common/008c37206e007202ce2e40dba140f49c/contact_02.png" />

</div>

### 修改界面标题栏字体颜色和图标

- 示例代码

    ```Java
    //1、创建个性化定制对象
    ContactUIConfig contactUIConfig = new ContactUIConfig();
    //2、设置 TitleBar 标题字体颜色和右侧按钮图标
    contactUIConfig.titleColor = Color.parseColor("#337EFF");
    contactUIConfig.titleBarRight2Res = R.drawable.ic_about;
    //3、设置右侧第二个按钮单击事件
    contactUIConfig.titleBarRight2Click = new View.OnClickListener() {
        @Override
        public void onClick(View v) {

        }
    };
    //4、将自定义事件设置到 ContactKitClient 即可
    ContactKitClient.setContactUIConfig(contactUIConfig);
    ```

    ::: note note
    除此之外，还可以设置标题栏的右侧第一个按钮图标和单击事件。请参考上文的个性化配置项列表。
    :::

<div id="examples">

- 效果对比

    默认 | 自定义后
    ---- | ----
    <img style="width:80%;border: 1px solid #BFBFBF;" src="https://yx-web-nosdn.netease.im/common/c6e107553a2b6bafb5421af1f6aab405/contact_01.png"/> | <img style="width:80%;border: 1px solid #BFBFBF;" src="https://yx-web-nosdn.netease.im/common/e34e6cda6b3a68a70bc7d9879b880c74/contact_03.png" />

</div>

### 隐藏头部模块

- 示例代码

    ```Java
    //1、创建个性化定制对象
    ContactUIConfig contactUIConfig = new ContactUIConfig();
    //2、设置列表头部不可见
    contactUIConfig.showHeader = false;
    //3、将自定义事件设置到 ContactKitClient 即可
    ContactKitClient.setContactUIConfig(contactUIConfig);
    ```

<div id="examples">

- 效果对比

    默认 | 自定义后
    ---- | ----
   <img style="width:80%;border: 1px solid #BFBFBF;" src="https://yx-web-nosdn.netease.im/common/c6e107553a2b6bafb5421af1f6aab405/contact_01.png" /> | <img style="width:80%;border: 1px solid #BFBFBF;" src="https://yx-web-nosdn.netease.im/common/6bdb87125b2be9f0825e096b441b1c42/contact_04.png" />

</div>

### 修改头部模块

在好友列表头部模块添加您自定义的入口和单击事件，即可自定义其展示内容。

- 示例代码

    ```Java
    //1、创建个性化定制对象
    ContactUIConfig contactUIConfig = new ContactUIConfig();
    //2、设置列表头部数据和单击事件
    List<ContactEntranceBean> header = new ArrayList<>();
    ContactEntranceBean firstHeader = new ContactEntranceBean(R.drawable.ic_about, **第一个头部站位** );
    header.add(firstHeader);
    contactUIConfig.headerData = header;
    contactUIConfig.itemClickListeners.append(IViewTypeConstant.CONTACT_ACTION_ENTER, new IContactClickListener() {
          @Override
          public void onClick(int position, BaseContactBean data) {
              Toast.makeText(context,"第一个头部站位单击",Toast.LENGTH_LONG).show();
          }
    });
    //3、将自定义事件设置到 ContactKitClient 即可
    ContactKitClient.setContactUIConfig(contactUIConfig);
    ```

<div id="examples">

- 效果对比

    默认 | 自定义后
    ---- | ----
    <img style="width:80%;border: 1px solid #BFBFBF;" src="https://yx-web-nosdn.netease.im/common/c6e107553a2b6bafb5421af1f6aab405/contact_01.png" /> | <img style="width:80%;border: 1px solid #BFBFBF;" src="https://yx-web-nosdn.netease.im/common/60fad2f3ca6b1d546f58e09709ec78a6/contact_05.png" />

</div>

### **修改通讯录列表字体颜色**

- 示例代码

    ```Java
    //1、创建个性化定制对象
    ContactUIConfig contactUIConfig = new ContactUIConfig();
    //2、设置列表中字体颜色
    contactUIConfig.contactAttrs = new ContactListViewAttrs();
    contactUIConfig.contactAttrs.setNameTextColor( Color.parseColor("#337EFF"));
    //3、将自定义事件设置到 ContactKitClient 即可
    ContactKitClient.setContactUIConfig(contactUIConfig);
    ```

    ::: note note
    除此之外，还可以修改字体大小，索引的字体颜色和字体大小，头像圆角大小，分割小颜色，是否展示索引等，请参考上文的个性化配置项列表。
    :::

<div id="examples">

- 效果对比

    默认 | 自定义后
    ---- | ----
    <img style="width:80%;border: 1px solid #BFBFBF;" src="https://yx-web-nosdn.netease.im/common/c6e107553a2b6bafb5421af1f6aab405/contact_01.png" /> | <img style="width:80%;border: 1px solid #BFBFBF;" src="https://yx-web-nosdn.netease.im/common/52ceb9553baab7f2d0387ba39fac28df/contact_08.png" />

</div>

### 在头部模块增加提示消息

- 示例代码

    ```Java
    //1、创建个性化定制对象
    ContactUIConfig contactUIConfig = new ContactUIConfig();
    //2、在列表界面头部增加自己的 View
    contactUIConfig.customLayout =
    new IContactViewLayout() {
        @Override
        public void customizeContactLayout(ContactLayout layout) {
            FrameLayout topLayout = layout.getBodyTopLayout();
            TextView contentTv = new TextView(topLayout.getContext());
            contentTv.setText("【温馨提示】欢迎使用运行 IM，在使用过程中如果遇到什么问题，请及时与我们联系。");
            contentTv.setTextColor(Color.parseColor("#333333"));
            contentTv.setBackgroundColor(Color.parseColor("#FFF8DC"));
            contentTv.setPadding(8,8,8,8);
            FrameLayout.LayoutParams layoutParams = new FrameLayout.LayoutParams(ViewGroup.LayoutParams.MATCH_PARENT,150);
            layoutParams.setMargins(16,12,16,12);
            topLayout.addView(contentTv,layoutParams);
          }
        };
    //3、将自定义事件设置到 ContactKitClient 即可
    ContactKitClient.setContactUIConfig(contactUIConfig);
    ```

<div id="examples">

- 效果对比

    默认 | 自定义后
    ---- | ----
    <img style="width:80%;border: 1px solid #BFBFBF;" src="https://yx-web-nosdn.netease.im/common/c6e107553a2b6bafb5421af1f6aab405/contact_01.png" /> | <img style="width:80%;border: 1px solid #BFBFBF;" src="https://yx-web-nosdn.netease.im/common/4a613b522ea76f4da23ab0a8f0ea0116/contact_06.png" />

</div>

## 源码导读

### 界面布局

在 `Contact-ui` 模块中，整个会话列表的布局配置在 `contact_fragment.xml` 中，可修改该文件源码实现界面元素调整和界面背景修改等自定义配置。

该文件中的源码概略如下：

```XML
<?xml version="1.0" encoding="utf-8"?>

<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    xmlns:app="http://schemas.android.com/apk/res-auto">

    //头部区块，当前包括 Titlebar 和分割线
    <LinearLayout android:id="@+id/contact_header_layout"
        android:layout_width="match_parent"
        android:layout_height="@dimen/dimen_55_dp"
        android:orientation="vertical"
        app:layout_constraintTop_toTopOf="parent"
        tools:ignore="MissingConstraints">

        <com.netease.yunxin.kit.common.ui.widgets.TitleBarView
            android:id="@+id/contact_title_layout"
            android:layout_width="match_parent"
            android:layout_height="@dimen/dimen_52_dp"
            app:head_title="@string/contact_title"
            app:head_title_color="@color/title_color"/>

        <View
            android:layout_width="match_parent"
            android:layout_height="@dimen/dimen_1_dp"
            android:background="@color/color_e9eff5"
            android:alpha="0.6"
            tools:ignore="MissingConstraints" />

    </LinearLayout>

    //内容区块，列表的形式，ContactListView 对 RecycleView 进行封装，提供多中数据操作接口
    <FrameLayout android:id="@+id/contact_body_layout"
        android:layout_width="match_parent"
        android:layout_height="0dp"
        app:layout_constraintVertical_weight="1"
        app:layout_constraintTop_toBottomOf="@+id/contact_header_layout"
        app:layout_constraintBottom_toTopOf="@+id/contact_bottom_layout">
        <com.netease.yunxin.kit.contactkit.ui.view.ContactListView
            android:id="@+id/contact_listview"
            android:layout_width="match_parent"
            android:layout_height="match_parent"
            app:head_img_visible="gone"
            app:head_title="@string/contact_title"
            app:head_title_color="@color/title_color"/>

    </FrameLayout>

    //底部区块，暂时没有使用
    <LinearLayout android:id="@+id/contact_bottom_layout"
        android:layout_width="match_parent"
        android:layout_height="48dp"
        android:orientation="horizontal"
        tools:ignore="MissingConstraints"
        android:visibility="gone"
        app:layout_constraintBottom_toBottomOf="parent">

    </LinearLayout>

</androidx.constraintlayout.widget.ConstraintLayout>
```

### 通讯录列表

`ContactListView` 为通讯录列表的实现类，`ContactListView` 是对 `RecyclerView` 和 `ContactAdapter` 的封装，同时提供数据更新接口，具体如下:
方法 | 入参类型 | 说明
---- | ---- | ----
`setViewHolderFactory` | `IContactFactory` | 设置 `RecyclerView` 的 `ViewHolder` 构造器
`setViewConfig` | `ContactListViewAttrs` | 设置列表的 UI 个性化配置
`showIndexBar` | boolean | 设置列表是否展示右侧字母索引
`addFriendData` | List`<ContactFriendBean>` | 添加好友数据，添加到已有数据之后，以 account 为唯一值
`removeFriendData` | List`<ContactFriendBean>` | 移除好友数据，以 account 为唯一值
`updateFriendData` | List`<ContactFriendBean>` | 更新好友数据，以 account 为唯一值

### 通讯录界面 UI

- 在通讯录列表中存在两种类型的 `ViewHolder`，即 `ContactViewHolder` 和 `EntranceViewHolder`。
    - `ContactViewHolder` 代表好友，其布局文件为 `friend_contact_view_holder.xml`，可以在该文件中调整其布局结构。
    - `EntranceViewHolder` 代表通讯录头部模块，其布局文件为 `friend_contact_view_holder.xml`，可以在该文件中调整其布局结构。
- 调用 `ViewHolder` 中的 `initViewBinding` 方法和 `onBind` 方法可分别实现布局的初始化和数据绑定。

</div>