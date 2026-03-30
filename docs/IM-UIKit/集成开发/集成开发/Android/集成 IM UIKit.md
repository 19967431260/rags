<!--keywords: 快速开始,快速集成 IM UIkit,UIKit,demo,IM UIKit,IMUIKit,Kit -->

网易云信 IM UIKit 是基于 [网易云信 IM SDK（简称 NIM SDK）](https://doc.yunxin.163.com/messaging2/concept?platform=client) 开发的一款 [即时通讯 UI 组件库](https://doc.yunxin.163.com/messaging-uikit/concept/TI3NTgyNDA?platform=android)，功能涵盖了聊天、会话、群管理。本文介绍安卓项目如何按照以下流程集成 10.x.x 版本的 IM UIKit。

```mermaid
graph LR
classDef default fill:#337EFF,stroke:#337EFF,stroke-width:0px,color:#FFFFFF;
按需导入组件 --> 添加权限 --> 防止代码混淆 --> 初始化 --> 登录 --> 选择界面风格
```

## 准备工作

在开始集成 IM UIKit 前，请确保您已完成以下操作：

1. 在 [网易云信控制台](https://app.yunxin.163.com/global/home) 上，[创建应用](https://doc.yunxin.163.com/console/concept/TIzMDE4NTA?platform=console)，开通即时通讯 IM 服务，获取 App Key。
2. [注册 IM 账号](https://doc.yunxin.163.com/messaging2/quick-start/jU0Mzg0MTU?platform=client#第二步注册-im-账号)，获取账号 ID（`account_id`）和凭证（`token`）。
3. 如需发送地理位置消息，提前获取高德地图 API Key 和 Web 服务 API。具体获取方式，参考《高德开放平台》[获取 Key](https://lbs.amap.com/api/android-location-sdk/guide/create-project/get-key) 和 [静态地图](https://lbs.amap.com/api/webservice/guide/api/staticmaps)。
4. 准备如下开发环境：
   - Android Studio Bumblebee 或更高版本
   - Java 11 或更高版本
   - Gradle 7.4 或兼容版本
   - Android Gradle Plugin 7.3.1 或兼容版本
5. 了解两种会话模式的区别：

    特性 | 本地会话（默认） | 云端会话（高级版 IM 套餐及以上支持） |
    --- | --- | --- |
    数据存储 | 消息记录存储在本地设备 | 消息记录存储在云端服务器 |
    多端同步 | 不支持多端同步 | 支持消息、会话的多端同步 |
    历史记录 | 换设备后无法查看历史记录 | 换设备后仍可查看历史记录 |
    适用场景 | 简单场景，对多端同步无要求 | 多端使用场景，需要消息同步 |

    ::: note notice
    本文默认使用本地会话模式。如需使用云端会话，请在组件导入和初始化配置中做相应调整。
    :::

## 注意事项

由于 IM UIKit 的初始化与登录是通过底层调用 NIM SDK 接口实现的，因此重复调用 IM UIKit 和 NIM SDK 的初始化与登录接口会相互覆盖传入的信息（包括 **推送配置信息**）。

所以，若您同时集成 IM UIKit 和 NIM SDK，只需要调用一次 [初始化](#init) 与 [登录](#loginIM) 接口即可。

## 第一步：按需导入组件

您可以根据业务需要，选择所需的 IM UIKit 组件。各组件相互独立，添加或删除均不影响项目编译。

### 如何选择组件

| 功能需求 | 需要导入的组件 |
| ---- | ---- |
| 仅聊天功能 | `teamkit-ui`、`chatkit-ui`、`conversationkit-ui` |
| 需要通讯录 | 增加 `contactkit-ui` |
| 需要位置消息 | 增加 `locationkit` |
| 需要音视频通话 | 增加 `call-ui` 和 `avsignalling` |

### 选择导入方式

- **方式一**：添加远程依赖（推荐）。在您的项目的 `build.gradle` 中，添加相应组件和第三方库（Glide、Retrofit 和 OkHttp）。示例中的 `{LATEST_VERSION}`，建议使用 10.x.x 系列的最新版本，版本号请参考 [更新日志](https://doc.yunxin.163.com/messaging-uikit/concept/zMzNDI4MDI)。

    :::::: div linked-codes
    ::: code 本地会话模式（默认）
    ```Groovy
    dependencies {
        // 通讯录功能
        implementation("com.netease.yunxin.kit.contact:contactkit-ui:${LATEST_VERSION}")
        // 本地会话列表组件
        implementation("com.netease.yunxin.kit.localconversation:localconversationkit-ui:${LATEST_VERSION}")
        // 群组功能组件
        implementation("com.netease.yunxin.kit.team:teamkit-ui:${LATEST_VERSION}")
        // 聊天功能组件
        implementation("com.netease.yunxin.kit.chat:chatkit-ui:${LATEST_VERSION}")
        // 位置消息功能组件
        implementation("com.netease.yunxin.kit.locationkit:locationkit:${LATEST_VERSION}")
        // 呼叫组件依赖
        implementation("com.netease.yunxin.kit.call:call-ui:3.0.0")
        implementation("com.netease.nimlib:avsignalling:${LATEST_VERSION}") //信令组件

        // 第三方依赖库
        implementation("com.github.bumptech.glide:glide:4.13.1")
        implementation("com.squareup.retrofit2:retrofit:2.9.0")
        implementation("com.squareup.retrofit2:converter-gson:2.9.0")
        implementation("com.squareup.retrofit2:converter-scalars:2.9.0")
        implementation("com.squareup.okhttp3:okhttp:4.12.0")
    }
    ```
    :::
    ::: code 云端会话模式
    ```Groovy
    dependencies {
        // 通讯录功能
        implementation("com.netease.yunxin.kit.contact:contactkit-ui:${LATEST_VERSION}")
        // 云端会话列表组件
        implementation("com.netease.yunxin.kit.conversation:conversationkit-ui:${LATEST_VERSION}")
        // 群组功能组件
        implementation("com.netease.yunxin.kit.team:teamkit-ui:${LATEST_VERSION}")
        // 聊天功能组件
        implementation("com.netease.yunxin.kit.chat:chatkit-ui:${LATEST_VERSION}")
        // 位置消息功能组件
        implementation("com.netease.yunxin.kit.locationkit:locationkit:${LATEST_VERSION}")
        // 呼叫组件依赖
        implementation("com.netease.yunxin.kit.call:call-ui:3.0.0")
        implementation("com.netease.nimlib:avsignalling:${LATEST_VERSION}") //信令组件

        // 第三方依赖库
        implementation("com.github.bumptech.glide:glide:4.13.1")
        implementation("com.squareup.retrofit2:retrofit:2.9.0")
        implementation("com.squareup.retrofit2:converter-gson:2.9.0")
        implementation("com.squareup.retrofit2:converter-scalars:2.9.0")
        implementation("com.squareup.okhttp3:okhttp:4.12.0")
    }
    ```
    :::
    ::::::

- **方式二**：如需添加本地依赖，请在获取对应分支的 [nim-uikit-flutter.git 源码](https://github.com/netease-kit/nim-uikit-android) 后，通过指定路径的形式实现。详情请参考 [导入组件](https://doc.yunxin.163.com/messaging-uikit/guide/DAwNDEwNzY?platform=android#%E6%96%B9%E5%BC%8F-2%E6%B7%BB%E5%8A%A0%E6%9C%AC%E5%9C%B0%E4%BB%A3%E7%A0%81%E4%BE%9D%E8%B5%96)。

## 第二步：添加权限

根据实际应用需求，在 `AndroidManifest.xml` 文件中设置所需的权限。

<details><summary>单击展开添加所需权限的 XML 文件配置。</summary>

```XML
<!-- 声明云信后台服务 -->
<service
    android:name="com.netease.nimlib.service.NimService"
    android:process=":core"
    tools:remove="true"/>

<service
    android:name="com.netease.nimlib.push.net.HeartbeatService"
    android:process=":core"
    tools:remove="true"/>

<!-- 声明云信后台辅助服务 -->
<service
    android:name="com.netease.nimlib.job.NIMJobService"
    android:exported="false"
    android:permission="android.permission.BIND_JOB_SERVICE"
    android:process=":core"
    tools:remove="true"/>

<!-- 云信SDK的监视系统启动和网络变化的广播接收器，用户开机自启动以及网络变化时候重新登录 -->
<receiver
    android:name="com.netease.nimlib.service.NimReceiver"
    android:exported="false"
    android:process=":core"
    tools:remove="true">
    <intent-filter>
        <action android:name="android.net.conn.CONNECTIVITY_CHANGE" />
    </intent-filter>
</receiver>

<!-- 云信进程间通信receiver -->
<receiver android:name="com.netease.nimlib.service.ResponseReceiver"
    tools:remove="true"/>

<!-- 云信进程间通信service -->
<service android:name="com.netease.nimlib.service.ResponseService"
    tools:remove="true"/>

<!-- 云信内部使用的进程间通信provider -->
<provider
    android:name="com.netease.nimlib.ipc.cp.provider.PreferenceContentProvider"
    android:authorities="${applicationId}.ipc.provider.preference"
    android:exported="false"
    tools:remove="true"/>
<provider
    android:name="com.netease.nimlib.ipc.NIMContentProvider"
    android:authorities="${applicationId}.ipc.provider"
    android:exported="false"
    android:process=":core"
    tools:remove="true"/>

<!-- 声明云信后台服务 -->
<service android:name="com.netease.nimlib.service.NimServiceV2" />

<provider
    android:name="com.netease.nimlib.ipc.NIMContentProviderV2"
    android:authorities="${applicationId}.ipc.provider.v2"
    android:exported="false" />
```
</details>

::: note notice
从 Android 6.0 (API 23) 开始，敏感权限需要在运行时动态申请。IM UIKit 使用的敏感权限包括：
- 相机权限 (`CAMERA`)
- 麦克风权限 (`RECORD_AUDIO`)
- 存储权限 (`READ_EXTERNAL_STORAGE`, `WRITE_EXTERNAL_STORAGE`)
- 对于 Android 13+，文件访问需要使用专门的权限 (`READ_MEDIA_IMAGES`, `READ_MEDIA_VIDEO`, `READ_MEDIA_AUDIO`)

您需要在应用中实现这些权限的运行时请求逻辑。
:::

## 第三步：防止代码混淆

代码混淆是指使用简短无意义的名称重命名已存在的类、方法、属性等，增加逆向工程的难度，保障 Android 程序源码的安全性。

为了避免因混淆导致 IM UIKit 功能异常，请在 `proguard-rules.pro` 文件中加入以下配置，将 NIM SDK 和 IM UIKit 的相关类加入不混淆名单。

<details><summary>单击展开防混淆的 proguard-rules.pro 配置。</summary>

```ProGuard
## NIM SDK 防混淆
-dontwarn com.netease.nim.**
-keep class com.netease.nim.** {*;}

-dontwarn com.netease.nimlib.**
-keep class com.netease.nimlib.** {*;}

-dontwarn com.netease.share.**
-keep class com.netease.share.** {*;}

-dontwarn com.netease.mobsec.**
-keep class com.netease.mobsec.** {*;}

## IM UIKit 防混淆
-dontwarn com.netease.yunxin.kit.**
-keep class com.netease.yunxin.kit.** {*;}
-keep public class * extends com.netease.yunxin.kit.corekit.XKitInitOptions
-keep class * implements com.netease.yunxin.kit.corekit.XKitService {*;}

## 呼叫组件防混淆
-keep class com.netease.lava.** {*;}
-keep class com.netease.yunxin.** {*;}

## 高德地图相关
-keep class com.amap.api.maps.**{*;}
-keep class com.autonavi.**{*;}
-keep class com.amap.api.trace.**{*;}
-keep class com.amap.api.location.**{*;}
-keep class com.amap.api.fence.**{*;}
-keep class com.loc.**{*;}
-keep class com.autonavi.aps.amapapi.model.**{*;}

## Glide 4
-keep public class * implements com.bumptech.glide.module.GlideModule
-keep public class * extends com.bumptech.glide.module.AppGlideModule
-keep public enum com.bumptech.glide.load.resource.bitmap.ImageHeaderParser$** {
**[] $VALUES;
    public *;
}

## OkHttp
-dontwarn okhttp3.**
-keep class okhttp3.**{*;}

## 如使用全文检索插件则需添加以下代码
-dontwarn org.apache.lucene.**
-keep class org.apache.lucene.** {*;}

## 如开启数据库功能则需添加以下代码
-keep class net.sqlcipher.** {*;}
```
</details>

<a id="init"></a>

## 第四步：初始化

1. 在 `AndroidManefest.xml` 中配置 App Key。

    如果需要使用 **发送地理位置消息** 的功能，还需在 `AndroidManefest.xml` 中配置高德地图 API Key 和定位服务（APSService）。

    示例代码如下：

    ```XML
    <application ...>
        <!-- 网易云信 App Key -->
        <meta-data
            android:name="com.netease.nim.appKey"
            android:value="YOUR_NETEASE_APP_KEY" />

        <!-- 高德地图客户端 Key -->
        <meta-data
            android:name="com.amap.api.v2.apikey"
            android:value="YOUR_AMAP_CLIENT_KEY" />

        <!-- 高德地图 Web 服务 Key (用于静态地图图片) -->
        <meta-data
            android:name="com.amap.api.v2.web.apikey"
            android:value="YOUR_AMAP_WEB_KEY" />

        <!-- 高德地图定位服务 -->
        <service android:name="com.amap.api.location.APSService" />
    </application>
    ```

2. 在 IM UIKit 项目的 `IMApplication` 的 `onCreate` 中添加如下代码。

    ::: note notice
    SDK 默认使用本地会话，若需要使用云端会话功能，除了在组件导入时，引入云端会话外，还需要在初始化时，将 `SDKOptions.enableV2CloudConversation` 设置为 true。只有设置为 true 后，才能正常使用云端会话服务。
    :::

    ```Java
    public class IMApplication extends MultiDexApplication {
        @Override
        public void onCreate() {
            super.onCreate();

            // 1. 创建 SDK 配置
            SDKOptions options = new SDKOptions();
            // 设置 App Key
            options.appKey = "YOUR_NETEASE_APP_KEY";

            // 2. 如需使用云端会话，取消下面注释
            // options.enableV2CloudConversation = true;

            // 3. 设置语言（可选）
            // "zh"=中文，"en"=英文
            String localeStr = AppLanguageConfig.getInstance().getAppLanguage(this);

            // 4. 初始化 IM UIKit
            // Local 参数为空则跟随系统语言
            IMKitClient.init(this, options, new Locale(localeStr));

            // 5. 初始化地图组件（如需位置消息功能）
            LocationConfig locationConfig = new LocationConfig();
            locationConfig.aMapWebServerKey = "YOUR_AMAP_WEB_KEY";
            LocationKitClient.init(this, locationConfig);
        }
    }
    ```

    ::: note note
    - 如果确定只使用中文或英文，可直接传入对应语言代码。
    - 更多初始化说明，请参考 [初始化](https://doc.yunxin.163.com/messaging-uikit/guide/zkzMTgyNzg?platform=android)。
    :::

<a id="loginIM"></a>

## 第五步：登录

**登录时机**

您可以根据应用流程选择合适的登录时机：

- 在启动页或登录页完成身份验证后登录。
- 如已保存用户凭证，可在应用启动时自动登录。

**登录方法**

```Java
/**
 * 登录网易云信服务
 * @param account_id 用户账号 ID
 * @param token 用户 Token
 */
public void loginIM(String account_id, String token) {
    // 1. 创建登录选项
    V2NIMLoginOption option = new V2NIMLoginOption();

    // 2. 调用登录方法
    IMKitClient.login(
        account_id,
        token,
        option,
        new FetchCallback<Void>() {
            @Override
            public void onError(int errorCode, @NonNull String errorMsg) {
                // 登录失败处理
                Log.e("IMLogin", "登录失败: " + errorCode + ", " + errorMsg);
                // TODO: 显示错误信息给用户
            }

            @Override
            public void onSuccess(@Nullable Void data) {
                // 登录成功处理
                Log.i("IMLogin", "登录成功");
                // TODO: 跳转到应用主界面
            }
        });
}
```

::: note notice
- `account_id` 和 `token` 应从您的业务服务器获取，或通过网易云信服务端接口生成。
- 在生产环境中不要使用测试账号和固定 Token，这会带来安全风险。
- 如果在 `Application` 初始化时已设置 [`LoginInfo`](https://doc.yunxin.163.com/messaging2/references/android/doxygen/Latest/zh/classcom_1_1netease_1_1nimlib_1_1sdk_1_1auth_1_1_login_info.html)，则无需再次调用此登录方法
:::

## 第六步：选择界面风格

网易云信 IM UIKit 提供两套界面风格的 [UI 组件库](https://doc.yunxin.163.com/messaging-uikit/concept/TI3NTgyNDA?platform=android)，您可任意选择一种使用。以搭建本地会话列表界面为例，基本流程如下（更多详情参考下文的 [下一步](#下一步)）：

::: note notice
- 如果需要云端会话，则将 `FunLocalConversationFragment` 对象换成 `FunConversationFragment` 即可。
- 示例代码中的 `getSupportFragmentManager` 方法属于 Android Activity 的默认方法。
    - 如果您使用 Android X 中的 `AddCompatActivity`，则可以直接调用 `getSupportFragmentManager` 方法。
    - 如果您使用的是 `android.app.acitivity`，则需要调用 `getFragmentManager` 方法。
:::

:::::: div linked-codes
::: code 基础版 UI 界面
```Java
public class ConversationActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_conversation);

        // 1. 创建会话列表 Fragment
        LocalConversationFragment conversationFragment = new LocalConversationFragment();

        // 2. 添加到 Activity
        FragmentManager fragmentManager = getSupportFragmentManager();
        fragmentManager
            .beginTransaction()
            .add(R.id.container_conversation, conversationFragment)
            .commit();

        // 3. 可选：设置会话列表单击监听器
        conversationFragment.setOnItemClickListener((view, position, data) -> {
            // 跳转到聊天界面
            if (data.getSessionType() == SessionTypeEnum.P2P) {
                // 打开单聊页面
                ChatP2PActivity.start(this, data.getContactId());
            } else if (data.getSessionType() == SessionTypeEnum.Team) {
                // 打开群聊页面
                ChatTeamActivity.start(this, data.getContactId());
            }
        });
    }
}
```

最终集成效果参考下图：

<img style="width:80%;border: 1px solid #BFBFBF;" src="https://yx-web-nosdn.netease.im/common/11707474727796454a82bfdf823f5534/960主要模块.png" />

:::
::: code 通用版 UI 界面

```Java
public class ConversationActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_conversation);

        // 1. 创建会话列表 Fragment
        FunLocalConversationFragment conversationFragment = new FunLocalConversationFragment();

        // 2. 添加到 Activity
        FragmentManager fragmentManager = getSupportFragmentManager();
        fragmentManager
            .beginTransaction()
            .add(R.id.container_conversation, conversationFragment)
            .commit();

        // 3. 可选：设置会话列表单击监听器
        conversationFragment.setOnItemClickListener((view, position, data) -> {
            // 跳转到聊天界面
            if (data.getSessionType() == SessionTypeEnum.P2P) {
                // 打开单聊页面
                FunChatP2PActivity.start(this, data.getContactId());
            } else if (data.getSessionType() == SessionTypeEnum.Team) {
                // 打开群聊页面
                FunChatTeamActivity.start(this, data.getContactId());
            }
        });
    }
}
```
最终集成效果参考下图：

<img style="width:80%;border: 1px solid #BFBFBF;" src="https://yx-web-nosdn.netease.im/common/1d225879d3f6eda6e3a8027462f3dc60/960主要模块绿.png" />

:::
::::::

### 可用界面组件参考

IM UIKit 中提供的常用业务场景界面，创建或者跳转到界面需要传入具体参数，详情请参考 [界面跳转](https://doc.yunxin.163.com/messaging-uikit/guide/TYyOTg0MjA?platform=android)，相关详细集成说明如下：

:::::: div linked-codes
::: code 基础版 UI 界面

界面类 | 所属组件 | 界面介绍 | 参考文档
---- | ---- | ---- | ----
`ConversationFragment` | `conversationkit-ui` | 云端会话列表 | [集成会话列表界面](https://doc.yunxin.163.com/messaging-uikit/guide/Dg2NzE2NTE?platform=android)
`LocalConversationFragment` | `localconversationkit-ui` | 本地会话列表 | [集成会话列表界面](https://doc.yunxin.163.com/messaging-uikit/guide/Dg2NzE2NTE?platform=android)
`ContactFragment` | `contactkit-ui` | 通讯录界面 | [集成通讯录界面](https://doc.yunxin.163.com/messaging-uikit/guide/TMxMDU0MzQ?platform=android)
`ChatP2PFragment`/`ChatP2PActivity` | `chatkit-ui` | 单聊会话 | [集成会话消息界面](https://doc.yunxin.163.com/messaging-uikit/guide/jA3MzY2OTA?platform=android)
`ChatTeamFragment`/`ChatTeamActivity` | `chatkit-ui` | 群聊会话 | [集成会话消息界面](https://doc.yunxin.163.com/messaging-uikit/guide/jA3MzY2OTA?platform=android)

:::
::: code 通用版 UI 界面

界面类 | 所属组件 | 界面介绍 | 参考文档
---- | ---- | ---- | ----
`FunConversationFragment` | `conversationkit-ui` | 云端会话列表 | [集成会话列表界面](https://doc.yunxin.163.com/messaging-uikit/guide/Dg2NzE2NTE?platform=android)
`FunLocalConversationFragment` | `localconversationkit-ui` | 本地会话列表 | [集成会话列表界面](https://doc.yunxin.163.com/messaging-uikit/guide/Dg2NzE2NTE?platform=android)
`FunContactFragment` | `contactkit-ui` | 通讯录界面 | [集成通讯录界面](https://doc.yunxin.163.com/messaging-uikit/guide/TMxMDU0MzQ?platform=android)
`FunChatP2PFragment`/`FunChatP2PActivity` | `chatkit-ui` | 单聊会话 | [集成会话消息界面](https://doc.yunxin.163.com/messaging-uikit/guide/jA3MzY2OTA?platform=android)
`FunChatTeamFragment`/`FunChatTeamActivity` | `chatkit-ui` | 群聊会话 | [集成会话消息界面](https://doc.yunxin.163.com/messaging-uikit/guide/jA3MzY2OTA?platform=android)
:::
::::::

## （可选）第七步：接入图片选择

具体请参考 [图片选择器](https://doc.yunxin.163.com/messaging-uikit/guide/jY2MjIwNDM?platform=android)。

## 常见问题

### 如何实现音视频通话功能

集成会话界面后，如果需要在会话界面实现音视频通话功能，参考 IMUIKit Demo 中实现代码 [`MainActivity.java`](https://github.com/netease-kit/nim-uikit-android/blob/master/app/src/main/java/com/netease/yunxin/app/im/main/MainActivity.java#L443) 中 `configCallkit()` 方法。具体示例请参考 [实现音视频通话](https://doc.yunxin.163.com/messaging-uikit/guide/jgxOTUyMjQ?platform=android)。

### 开发环境与生产环境账号切换

为保障通信安全，请在不同环境中使用相应账号：

- **开发测试环境**：可使用控制台生成的测试账号和 Token。
- **正式生产环境**：必须通过 [IM 服务端 API](https://doc.yunxin.163.com/messaging2/server-apis/TQyNjgyMzc?platform=server) 生成正式 IM 账号（`account_id`）和 `token`。

### 运行时权限处理

Android 6.0 及以上版本需要动态申请相关权限，以下示例展示如何申请相机和麦克风权限：

```Java
private static final int REQUEST_PERMISSION_CODE = 100;

private void requestPermissions() {
    // Android 6.0+ 动态权限申请
    if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.M) {
        List<String> permissionsToRequest = new ArrayList<>();

        // 检查相机权限
        if (ContextCompat.checkSelfPermission(this, Manifest.permission.CAMERA)
                != PackageManager.PERMISSION_GRANTED) {
            permissionsToRequest.add(Manifest.permission.CAMERA);
        }

        // 检查录音权限
        if (ContextCompat.checkSelfPermission(this, Manifest.permission.RECORD_AUDIO)
                != PackageManager.PERMISSION_GRANTED) {
            permissionsToRequest.add(Manifest.permission.RECORD_AUDIO);
        }

        // 检查存储权限
        if (Build.VERSION.SDK_INT <= Build.VERSION_CODES.S_V2) {
            // Android 12 (API 32) 及以下版本使用传统存储权限
            if (ContextCompat.checkSelfPermission(this, Manifest.permission.READ_EXTERNAL_STORAGE)
                    != PackageManager.PERMISSION_GRANTED) {
                permissionsToRequest.add(Manifest.permission.READ_EXTERNAL_STORAGE);
            }
            if (ContextCompat.checkSelfPermission(this, Manifest.permission.WRITE_EXTERNAL_STORAGE)
                    != PackageManager.PERMISSION_GRANTED) {
                permissionsToRequest.add(Manifest.permission.WRITE_EXTERNAL_STORAGE);
            }
        } else {
            // Android 13 (API 33) 及以上版本使用媒体权限
            if (ContextCompat.checkSelfPermission(this, Manifest.permission.READ_MEDIA_IMAGES)
                    != PackageManager.PERMISSION_GRANTED) {
                permissionsToRequest.add(Manifest.permission.READ_MEDIA_IMAGES);
            }
            if (ContextCompat.checkSelfPermission(this, Manifest.permission.READ_MEDIA_VIDEO)
                    != PackageManager.PERMISSION_GRANTED) {
                permissionsToRequest.add(Manifest.permission.READ_MEDIA_VIDEO);
            }
        }

        // 申请所需权限
        if (!permissionsToRequest.isEmpty()) {
            ActivityCompat.requestPermissions(this,
                permissionsToRequest.toArray(new String[0]), REQUEST_PERMISSION_CODE);
        }
    }
}

@Override
public void onRequestPermissionsResult(int requestCode, @NonNull String[] permissions,
                                      @NonNull int[] grantResults) {
    super.onRequestPermissionsResult(requestCode, permissions, grantResults);

    if (requestCode == REQUEST_PERMISSION_CODE) {
        // 处理权限申请结果
        boolean allGranted = true;
        for (int result : grantResults) {
            if (result != PackageManager.PERMISSION_GRANTED) {
                allGranted = false;
                break;
            }
        }

        if (!allGranted) {
            // 提示用户权限被拒绝的影响
            Toast.makeText(this, "部分功能可能无法正常使用，请在设置中开启相关权限", Toast.LENGTH_LONG).show();
        }
    }
}
```

<!--

### 使用原生 SDK 中方法

如果您需要在 IM UIKit 中自行实现目前 UIKit 还未实现，但原生 IM Android SDK 已提供的能力。您可以通过调用原生 IM Android SDK 中提供的接口来实现。例如，您想对 IM UIKit 的消息历史进行全文检索，可以调用原生 IM Android SDK 中的 方法，示例代码如下：

```
```

原生 IM Android SDK 中的接口请参考对应的 [API 文档](https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/annotated.html)。
-->

### Android 13（33）系统权限适配

如果项目中的 SdkVersion 采用 Android 13（33），那么需要修改其中的权限申请，这样才能正常使用图片和文件发送功能。具体请参考 [Android 13 文件权限适配](https://doc.yunxin.163.com/messaging-uikit/guide/DkyNTcyMjI?platform=android)。

### 常见问题排查

集成过程中的常见问题的排查说明，请参考 [排查常见问题](https://doc.yunxin.163.com/messaging-uikit/guide/DE2MDc3NTM?platform=android)。