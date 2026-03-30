<!--keywords: 隐私合规,最佳实践-->

数据隐私保护已成为一个重要的社会议题，国家也出台了很多相关政策来保护个人隐私。因此，在应用上架到应用商店前，需确保应用采集用户隐私数据的合规性，从而保证应用能正常上线。

## 背景信息

根据《个人信息安全规范》的相关要求，在应用需要收集个人信息时，必须向个人信息主体明示个人信息处理目的、方式、范围等，并且形成单独成文的《隐私政策》。

您需确保《隐私政策》的独立性与易读性，并确保用户进入应用的主要功能界面后，能够通过 **四** 次以内的单击或滑动操作查看《隐私政策》。您还需确保应用只能用户同意《隐私政策》后收集用户的隐私信息。相关详情请参考 [《信息安全技术-个人信息安全规范》](http://openstd.samr.gov.cn/bzgk/gb/newGbInfo?hcno=4568F276E0F8346EB0FBA097AA0CE05E)。

## 第一步：完善隐私政策文件

:::note notice
建议在应用首次启动时，通过弹窗向客户展示隐私政策概要，并添加《隐私政策》的跳转链接。在用户选择 **同意** 后，应用才能进行获取用户个人信息的行为。
:::

1. 确保您的应用已出具《隐私政策》，并在《隐私政策》中添加如下声明。

    ```
    网易云信的产品或服务可能包括第三方的产品或服务，后者也可能收集并使用您的个人信息。例如，网易云信为实现即时通讯服务，集成了网易云信 SDK。网易云信将作为数据处理者，按照本公司的指示以及《网易云信隐私政策》（https://netease.im/clauses?serviceType=3）收集、使用并保护您的个人信息。
    ```

3. 如果您的应用有单独的《第三方共享清单》，建议把以下信息添加到该文档中。

    ```
    网易云信 IM 即时通讯
    第三方公司名称：杭州网易质云科技有限公司
    共享类型：内嵌 SDK
    共享信息：唯一设备识别码（APNS Token、设备序列号、AndroidID、OAID、GAID、IDFV、CID、MAC 地址）。设备运行状态（SIM 卡状态、USB 状态、充电状态、电池容量及电量、锁屏时间、启动时间）。设备信息（设备类型、设备品牌及型号、设备名称、设备厂商、设备所运行系统（版本信息、内核信息、CPU 型号、设备内存及存储大小）、屏幕亮度及分辨率、设备输入装置、设备架构、基带信息、字体 HASH、HOSTNAME、辅助功能列表、系统进程列表）。日志信息（设备运行状态（CPU、内存运行状态）、浏览器类型及版本信息（Web H5）、网络连接类型及状态、WIFISSID、WIFIBSSID、IP 地址、运营商信息、网络代理、网易云信通信服务运行日志信息）。
    使用目的：提供消息投递、多端消息同步、消息漫游功能，同时为了预防安全风险，准确识别违反法律法规的情况
    使用场景：提供即时通讯服务
    共享方式：（外部）接口共享
    第三方隐私链接：https://netease.im/clauses?serviceType=3
    ```

## 第二步：分步初始化

由于 NIM SDK 初始化时，部分 API 需在用户同意后才被允许调用，所以在用户首次启动应用时，应确保用户阅读您的《隐私政策》并取得用户授权之后，再调用 IM 的初始化函数。

为此网易云信特意提供了分步初始化的方案，Java 示例如下：

1. 每次启动应用时，在 Application 的 `onCreate` 方法中获取客户是否同意《隐私声明》的信息。

    - 如同意，则可直接调用 [`initV2`](https://doc.yunxin.163.com/messaging2/references/android/doxygen/Latest/zh/classcom_1_1netease_1_1nimlib_1_1sdk_1_1_n_i_m_client.html#aa8e0e524f223d29e8f2499557a2ae2e5) 方法进行初始化。
    - 如不同意，则调用 [`config`](https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/classcom_1_1netease_1_1nimlib_1_1sdk_1_1_n_i_m_client.html#a734a21a3519b5d930d873e731078c967) 方法进行 SDK 相关配置，不会涉及隐私相关 API 的调用。

    ::: note notice
    初始化完成后，网易云信会启动一个后台服务进程，该进程启动会触发 Applicaiton 的 `onCreate` 方法的调用，并且需要通过 `onCreate` 方法把 [`SDKOptions`](https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/classcom_1_1netease_1_1nimlib_1_1sdk_1_1_s_d_k_options.html) 设置给该进程。因此，初始化 IM SDK 时，**需确保**：

    - 在 `onCreate` 方法中调用 `NIMClient.config` 或者 `NIMClient.init`。
    - 在 `onCreate` 方法中 **不要** 进行其他第三方库的初始化，避免内存浪费或者其他意外的发生。
    :::

    初始化示例代码如下：

    ```Java
    /**
    * 如果用户同意后，可以直接对 SDK 进行初始化操作 {@link NIMClient#init(Context, LoginInfo, SDKOptions)}
    * 包含分步初始化的 config 方法和 initSDK 方法。
    * 如果用户未同意，需要先在 Applicaiton.onCreate 方法中调用 {@link NIMClient#config(Context, LoginInfo, SDKOptions)}
    * 在用户同意之后，再调用正真的初始化方法 {@link NIMClient#initSDK()}
    */
    private void initIMSdk(){
        if (hasAgree){
            //如果用户同意后，直接对 SDK 初始化
            NIMClient.init(this, getLoginInfo(), getSDKOptions());
        }else {
            //如果用户未同意，先调用 config
            NIMClient.config(this, getLoginInfo(), getSDKOptions());
        }
    }
    ```

2. 在应用的启动界面检查用户是否同意《隐私声明》，如未同意则弹出选择框，在用户单击 **同意** 后调用 [`NIMClient#initV2`](https://doc.yunxin.163.com/messaging2/references/android/doxygen/Latest/zh/classcom_1_1netease_1_1nimlib_1_1sdk_1_1_n_i_m_client.html#aa8e0e524f223d29e8f2499557a2ae2e5) 对 IM SDK 进行真正的初始化操作。

    ```Java
    //注意这里需要调用无参的分步初始化的方法，必须要在主进程中调用。
    NIMClient.initSDK();
    ```

    ::: note important
    - `NIMClient#initV2` 方法必须在主进程中调用。
    - 在调用 `NIMClient#initV2` 方法进行初始化之前，请勿调用 [`NIMClient#getService`](https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/classcom_1_1netease_1_1nimlib_1_1sdk_1_1_n_i_m_client.html#af2e4356fb14fd8077caabcb3d9570b4b) 方法，否则会出现异常 `SDK not initialized or invoked in wrong process`，导致程序崩溃。
    :::

## 第三步：去除自启动

随着市场监管越来越严格，部分市场会对频繁自启动和开机自启动的行为进行检测，并通知上架方进行整改。您可以根据检测结果，自主选择关闭频繁自启动或者开机自启动。

- 关闭频繁自启动：在初始化的时候通过将 `SDKOptions.disableAwake` 参数设置为 `true` 关闭应用内自启动行为。
- 关闭开机自启动：共有两种方式来处理，在主工程的 `AndroidManifest.xml` 文件中，通过 `tools:node="remove` 标签去掉 `NimReceiver`，可以根据具体要求自行选择。

```XML
<receiver
    android:name="com.netease.nimlib.service.NimReceiver"
    android:exported="false"
    tools:node="remove"
    android:process=":core">
</receiver>
```