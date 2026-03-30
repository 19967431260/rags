

iOS 的离线推送需要通过 APNs 服务器来进行发送，因此在使用云信 NIM SDK 提供的离线推送功能之前，首先需要在您的项目中集成 APNs 离线推送服务，并实现与云信服务端的通信。

本文主要介绍如何集成 APNs 离线推送服务。

##  APNs 通信方式

云信服务端与 APNs 通信的方式分为以下两种：

- **使用 TLS 证书与 APNs 通信（文件扩展名为 .p12 的证书文件）**
    
    - 云信服务端通过 TLS 证书对 APNs 进行身份验证后，发送离线推送。该证书可以同时支持生产环境和开发环境。
    - TLS 证书的有效期为一年。超出有效期后，必须创建新的证书，重新提供给云信。
- **使用验证令牌与 APNs 通信（文件扩展名为 .p8 的密钥文件）**
    
    - 云信服务端通过令牌对 APNs 进行身份验证后，发送离线推送。该证书可以同时支持生产环境和开发环境。
    - 一个 APNs 签名密钥验证多个 App 的令牌，即多个应用程序可以使用同一个签名密钥。
    - 签名密钥不会过期，因此只需提供一次，后续无需更新。


更多详细信息请参考[使用验证令牌与 APNs 通信](https://developer.apple.com/cn/help/account/configure-app-capabilities/communicate-with-apns-using-authentication-tokens)和[使用 TLS 证书与 APNs 通信](https://developer.apple.com/cn/help/account/configure-app-capabilities/communicate-with-apns-using-a-tls-certificate)。

本文主要介绍使用 TLS 证书与 APNs 通信的形式（即通过 p12 推送证书）实现离线推送功能。

## 实现流程

### 步骤 1：创建 App ID 并开启推送功能

使用 APNs 推送服务前，您需要先拥有一个 App ID。若已拥有 App ID，则跳过此章节，只需在您原有的 App ID 上增加 `Push Notification` 的 `Service`。如需要了解更详细的说明，请参考 [注册 App ID](https://developer.apple.com/cn/help/account/manage-identifiers/register-an-app-id) 。

1. 登录[Apple 开发者网站](https://developer.apple.com/)，选择导航栏的**Account**。

    <img src="https://yx-web-nosdn.netease.im/common/77691a3e4a8aa14069f3598411d813c1/创建AppID.png"  width="300"/>

2. 进入 **Certificates, IDs & Profiles**（证书、标识符和描述文件），单击 **Identifiers**（标识符）。

    <img src="https://yx-web-nosdn.netease.im/common/54e4578c38ed523349b1c58d5311a7ec/Certificates.png"  width="300"/>


3. 单击 **Identifiers** 右侧的“+”按钮。

    <img src="https://yx-web-nosdn.netease.im/common/11c3bb4fa761bf3fc23e9aafeec776e2/ID.png"  width="300"/>

4. 从选择项中选择 **App IDs**，单击 **Continue**。然后确认已自动选择的 **App ID** 类型，再单击 **Continue**。

    <img src="https://yx-web-nosdn.netease.im/common/838bc09c2f5a1f0ab4432ac88a1d04af/Continue.png"  width="300"/>

5. 填写 App ID 账号信息。
    - 在 **Description** 中输入 App ID 的名称或描述。
    - 选择 **Explicit App ID**，并在 **Bundle ID** 中输入 App 的 `Bundle ID`。
    :::note notice
    - `Bundle ID`不能使用通配符 *，否则将无法使用远程推送服务。
    - 此处填写的 `Bundle ID` 应与 Xcode 中目标的 Summary 面板中输入的 `Bundle ID` 一致。
    :::

    <img src="https://yx-web-nosdn.netease.im/common/4dc0358b14a237cb4a809aa1004dde40/描述.png"  width="300"/>

6. **Capabilities** 中会显示 App 类型以及可使用的功能。勾选 **Push Notifications** 启用推送通知功能。 
    您还可以根据实际需求勾选其他对应的功能。

    <img src="https://yx-web-nosdn.netease.im/common/c78bb3a6d48e85c456487f3d180a7228/推送.png"  width="300"/>

7. 单击 **Continue**，再次确认注册信息后，单击 **Register**。


### 步骤 2：创建推送证书

您可以根据 APNs 通信方式，选择创建文件扩展名为 .p12 的证书或者文件扩展名为 .p8 的密钥。

- [创建 .p12 推送证书](https://doc.yunxin.163.com/messaging/guide/DkwNjM3OTg?platform=iOS)
- [创建 .p8 密钥文件](https://doc.yunxin.163.com/messaging/guide/TUwMDE2NDc?platform=iOS)


### 步骤 3：上传推送证书至云信

1. 登录云信控制台，在控制台首页**应用管理**中选择应用进入**应用配置**页面。

2. 顶部选择**证书管理**页签，进入推送证书配置页。
    
    ![证书管理.png](https://yx-web-nosdn.netease.im/common/203c3e78eaa5ae0eb9500d2a8aa33e29/证书管理.png)

3. 在对应的 iOS 证书配置项中，单击**添加证书**。

    - iOS APNs p12 推送证书
        
        ![P12证书.png](https://yx-web-nosdn.netease.im/common/db8e923bdd087860c7c707d16684801a/P12证书.png)


    - iOS APNs P8 推送证书

        ![P8证书.png](https://yx-web-nosdn.netease.im/common/61781a165e12f54d915c5582a889dbc4/P8证书.png)



3. 填写证书信息并上传证书文件后，单击**确定**。
    - 证书名称与 p12/p8 证书一一对应，服务器将根据证书名称来自动选择 p12/p8 文件。
    - ⽣产环境或开发环境，请选择与该证书⽣成时相同的环境类型。


### 步骤 4：创建并安装配置文件

您需要创建一个 Provisioning Profile（配置文件），才能在设备上运行您的应用程序，使用推送通知功能。

1. 在 [Apple 开发者网站](https://developer.apple.com/)的 **Certificates, IDs & Profiles**（证书、标识符和描述文件）中，单击 **Profiles**（描述文件）。然后单击右侧的“+”按钮。
    <img src="https://yx-web-nosdn.netease.im/common/ea5242d03aaf2381c20c396b1fe3d0c6/Profiles.png"  width="300"/>

2. 选择 **Provisioning Profile**的环境，单击 **Continue**。

3. 选择对应的 App ID，单击 **Continue**。

    ![对应appid.png](https://yx-web-nosdn.netease.im/common/a97d15b0372764a07a2cdce727c140dd/对应appid.png)


4. 选择所属的开发者证书，若创建了多个，选择 **Select All**，单击 **Continue**。

    ![selectall.png](https://yx-web-nosdn.netease.im/common/683996003f8fa9574b08b1bb634522e4/selectall.png)


5. 选择需要安装的设备（一般选择 **Select All**），单击 **Continue**。

6. 填写 **Profile Name**，单击 **generate**，完成创建。

    ![profilename.png](https://yx-web-nosdn.netease.im/common/0d2bc76cf71aa90e81b8cdea143fd6d8/profilename.png)


7. 单击 **Download**下载到本地，然后双击下载的 Provisioning Profile 文件，将其添加到 Xcode。


### 步骤 5： 获取当前设备的 deviceToken

在您 App 的 application 中添加如下代码，向 APNs 服务端请求推送权限，获取 deviceToken。

:::note note
考虑到合规，建议您在同意隐私协议之后再向 APNs 服务端请求 deviceToken。
:::

示例代码如下：

```
- (void)application:(UIApplication *)app didRegisterForRemoteNotificationsWithDeviceToken:(NSData *)deviceToken
{
    NSString * key = @"customAPNsType";
    [[NIMSDK sharedSDK] updateApnsToken:deviceToken
                       customContentKey:key];
    DDLogInfo(@"didRegisterForRemoteNotificationsWithDeviceToken:  %@", deviceToken);
}
```


