网易云信在 Github 上提供开源的 IM Demo 源码。您可参考 Demo 源码，在您的本地项目中快速构建即时通讯应用。本文介绍如何快速跑通 IM Demo 源码。

## 主要模块

<style>
table th:first-of-type {width: 35%;}
</style>

网易云信 IM UIKit 提供两套界面风格的 [UI 组件库](https://doc.yunxin.163.com/messaging-uikit/concept/TI3NTgyNDA?platform=android)，您可任意选择一种使用。

<div style="display: flex; justify-content: space-between; width: 100%;">
    <div style="width: 50%;text-align: center; caption-side: top;""><b>基础版单聊</b><br>
        <img alt="im-android-flutter.png" src="https://yx-web-nosdn.netease.im/common/32c07cc1de486b16df79a48127f7f0ff/image.png" style="width:60%;border: 1px solid #BFBFBF;">
    </div>
    <div style="width: 50%;text-align: center; caption-side: top;""><b>基础版群聊</b><br>
        <img alt="party-android.png" src="https://yx-web-nosdn.netease.im/common/d35be1ce1d50cdf9c312495b022eae52/%E7%BE%A4%E8%81%8A%E6%B6%88%E6%81%AF%E8%93%9D.png" style="width:60%;border: 0px solid #BFBFBF;">
    </div>
    <div style="width: 50%;text-align: center; caption-side: top;""><b>通用版单聊</b><br>
        <img alt="im-android-flutter.png" src="https://yx-web-nosdn.netease.im/common/d7c6668de7a42f59621c39c2d17d7cf8/%E5%8D%95%E8%81%8A%E6%B6%88%E6%81%AF.png" style="width:60%;border: 0px solid #BFBFBF;">
    </div>
    <div style="width: 50%;text-align: center; caption-side: top;""><b>通用版群聊</b><br>
        <img alt="party-android.png" src="https://yx-web-nosdn.netease.im/common/15773b00cfd3c6a91b547c3e3820cbe2/%E7%BE%A4%E8%81%8A%E6%B6%88%E6%81%AF.png" style="width:60%;border: 0px solid #BFBFBF;">
    </div>
</div>

## 前提条件

在开始运行示例项目之前，请确保您已：

- 在 [网易云信控制台](https://app.yunxin.163.com/global/home) 上，[创建应用](https://doc.yunxin.163.com/console/guide/TIzMDE4NTA?platform=console)，获取应用密钥（App Key）。
- 已 [注册 IM 账号](https://doc.yunxin.163.com/messaging2/guide/jU0Mzg0MTU?platform=client#第二步注册-im-账号)，获取账号 ID（`account_id`）和凭证（Token）。
- 已在 [网易云信控制台](https://app.yunxin.163.com/global/home) 为应用开通 **云端会话** 开关。开启步骤请参考《控制台文档》[配置应用](https://doc.yunxin.163.com/console/concept/TQ2NzE5MzQ?platform=console)。

    <img alt="开通云端会话.png" src="https://yx-web-nosdn.netease.im/common/d80e78c7f8d0a5b7f0452e7f5d9c6b47/开通云端会话.png" style="width:40%;border: 1px solid #BFBFBF;">

- 准备如下开发环境:

    环境要求 | 说明 |
    ---- | ---- |
    JDK 版本 | 1.8.0 及以上版本 |
    Android API 版本 | API 21、Android 5.0 及以上版本 |
    CPU 架构 | ARM 64、ARM V7 |
    IDE | Android Studio 4.0 及以上 |
    其他 | 依赖 Androidx，不支持 support 库。请使用 Android 系统 5.0 或以上版本的移动设备。 |

## 跑通流程

1. 前往 GitHub <a href="https://github.com/netease-kit/nim-uikit-android" target="_blank">下载 Demo 源码</a>。

    示例项目结构如下：
     目录 | 说明
     ---- | ----
     app | 应用主入口，包含外部界面框架
     chatkit-ui | 聊天功能界面相关代码
     contactkit-ui | 通讯录功能界面相关代码
     conversationkit-ui | 云端会话功能界面相关代码
     localconversationkit-ui | 本地会话功能界面相关代码
     aisearchkit-ui | AI 数字人划词搜索功能界面相关代码
     teamkit-ui | 群组功能界面相关代码

2. 将示例项目导入 Android Studio。

3. 在 Android Studio 里找到工程目录 `app/src/main/AndroidManifest.xml` 文件，将文件里如下代码中的 `your app key` 替换成您在 [网易云信控制台](https://app.yunxin.163.com/global/home) 获取的 [App Key](https://doc.yunxin.163.com/console/guide/TIzMDE4NTA?platform=console)。

    ```XML
    <meta-data
        android:name="com.netease.nim.appKey"
        android:value="your app key" />

    ```

4. 在 Android Studio 里找到工程目录 `app/src/main/java/com.netease.yunxin.app.im.AppConfig.java` 文件，并填入您的 [网易云信 IM 账号（accid）和 Token](https://doc.yunxin.163.com/messaging-uikit/guide/Dc0NjI1MTA?platform=android#4-注册-im-账号)。

    ```Java
    public class AppConfig {

        // IM 登录

        // IM UIKit 和 IM SDK 登录账号 ID
        public static final String account = "";
        // IM UIKit 和 IM SDK 登录 Token
        public static final String token = "";

            .....
    }
    ```

5. 将源码运行在您的 Android 设备上，即可进入如下界面，开始体验 IM Demo。

    可以在 **我的->设置->外观** 中切换 UI 风格。

    <div style="display: flex; justify-content: space-between; width: 100%;">
        <div style="width: 50%;text-align: center; caption-side: top;""><b>Demo 界面</b><br>
            <img alt="Demo.png" src="https://yx-web-nosdn.netease.im/common/6858362055e77fc8a23285b63b0965be/Demo首页不含圈组.png" style="width:45%;border: 0px solid #BFBFBF;">
        </div>
        <div style="width: 50%;text-align: center; caption-side: top;""><b>设置</b><br>
            <img alt="UI.png" src="https://yx-web-nosdn.netease.im/common/214d463a68d5aef7a320449a0936221e/image.png" style="width:45%;border: 1px solid #BFBFBF;">
        </div>
        <div style="width: 50%;text-align: center; caption-side: top;""><b>外观</b><br>
            <img alt="UI.png" src="https://yx-web-nosdn.netease.im/common/9a8557684d1b6fbbc453a9f281a91825/image.png" style="width:45%;border: 1px solid #BFBFBF;">
        </div>
    </div>