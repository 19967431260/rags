在 iOS 8 苹果新引入了名为 PushKit 的框架和一种新的 push 通知类型，被称作 VoIP Push。该 Push 方式旨在提供区别于普通 APNs Push 的能力，通过这种 Push 方式可以使 App 执行自定义的代码（在弹出通知给用户之前）。而该通知的默认行为和 APNs 通知有所区别，它的默认行为里面是不会弹出通知的。

PushKit 框架用于直接发送特定种类的通知到开发者自己的应用，例如 VoIP (Voice over IP), watchOS 各类部件更新等等。其中 VoIP 类型推送可以帮助提 VoIP 类应用的体验。本文主要介绍 VoIP Push 的相关配置。

## 第一步：创建 VoIP 证书

为了能够接收到消息推送，首先需要创建一个 Identifier。

<img alt="image-netease" src="https://yx-web-nosdn.netease.im/webdoc/pushkit/CB245AD4C88A08BCC72C6CECA6209578.jpg" style="width:80%;border: 1px solid #BFBFBF;">

指定一个 bundle id 给应用程序。本示例中使用 **com.emily.voiptest** 示例。先不用担心 App Service 部分选项，可以在后面进行补充。

<img alt="image-netease" src="https://yx-web-nosdn.netease.im/webdoc/pushkit/F9B3970E7829D295D69C41B9F95EE059.jpg" style="width:50%;border: 1px solid #BFBFBF;">

目前已经设置好 Identifier 部分已经设置好，接下来需要配置消息推送需要的证书。

<img alt="image-netease" src="https://yx-web-nosdn.netease.im/webdoc/pushkit/E836AA4D57E4A3D762731F9E623EE215.jpg" style="width:80%;border: 1px solid #BFBFBF;">

<img alt="image-netease" src="https://yx-web-nosdn.netease.im/webdoc/pushkit/8B2FB917749DE31A7AF8F18B59B95161.jpg" style="width:60%;border: 1px solid #BFBFBF;">

接下来要求选择一个 App ID，这里选择刚刚创建的 ID。下面介绍通过钥匙串创建 CSR 证书：

<img alt="image-netease" src="https://yx-web-nosdn.netease.im/webdoc/pushkit/251B57D9E5342E550CCF5EE78235CB8D.jpg" style="width:50%;border: 1px solid #BFBFBF;">

<img alt="image-netease" src="https://yx-web-nosdn.netease.im/webdoc/pushkit/544F468876752419326888359D4606CE.jpg" style="width:80%;border: 1px solid #BFBFBF;">

<img alt="image-netease" src="https://yx-web-nosdn.netease.im/webdoc/pushkit/BB3C1CF282E49D97D4258E332198708E.jpg" style="width:60%;border: 1px solid #BFBFBF;">

之后下载证书，并单击，就能自动导入钥匙串。找到您的 certificate 并单击证书旁边的小箭头，同时得到 certificate 和对应的 key。

<img alt="image-netease" src="https://yx-web-nosdn.netease.im/webdoc/pushkit/7835C078D07CC4F836B9A7D9058F2C52.jpg" style="width:80%;border: 1px solid #BFBFBF;">

选择 p12 格式并命名。注意文件格式如下图所示：

<img alt="image-netease" src="https://yx-web-nosdn.netease.im/webdoc/pushkit/5C9B26BD3AA734B89A1E7A08A797378C.jpg" style="width:60%;border: 1px solid #BFBFBF;">

## 第二步：上传网易云信服务器

1. 进入 [网易云信控制台](https://app.yunxin.163.com/global/home)，选择对应的应用。

    <img alt="image-netease" src="https://yx-web-nosdn.netease.im/common/bbe75ce0b126946ec79da5c24b22e833/image.png" style="width:80%;border: 1px solid #BFBFBF;">
2. 上传刚刚导出的 p12 文件，以上传时填写的证书名做区分。

    <img alt="image-netease" src="https://yx-web-nosdn.netease.im/webdoc/pushkit/E837CAA005D26B9A15645367132B7797.jpg" style="width:30%;border: 1px solid #BFBFBF;">
3. 开发环境或生产环境，请选择与该证书生成时相同的环境类型。


    <img alt="image-netease" src="https://yx-web-nosdn.netease.im/webdoc/pushkit/D5E005C51322656728DE2E15C9F76024.jpg" style="width:50%;border: 1px solid #BFBFBF;">

## 第三步：实现离线推送

- 注意保证创建工程的 bundle identifier 必须和证书使用的相同，这样才可以发送推送。
- 在 Target 的 capabilities-\>background Modes 下打开 Voice over IP
- 引入 PushKit 服务

## PushKit 推送的问题排查

- 首先确认证书的配置，具体配置操作见上文第一第二条
- 若证书配置无误，则下载本地 [pusher 工具](https://github.com/noodlewerk/NWPusher) 检测是否能收到消息，这个工具的 README 文档中包含了安装方式

    <img alt="image-netease" src="https://yx-web-nosdn.netease.im/webdoc/pushkit/194A5D37E0FB62485393B84CF9425551.jpg" style="width:80%;border: 1px solid #BFBFBF;">

    界面如上图所示。

通过 AppDelegate 文件这个函数日志获取 PushKit token

<img alt="image-netease" src="https://yx-web-nosdn.netease.im/webdoc/pushkit/15A7EF080963696B68312AC0D1EA5B74.jpg" style="width:80%;border: 1px solid #BFBFBF;">

<img alt="image-netease" src="https://yx-web-nosdn.netease.im/webdoc/pushkit/E5662EB9A37D2594B443336B7BDB15A6.jpg" style="width:80%;border: 1px solid #BFBFBF;">

配置后进行推送，若推送成功会出现在左下角 <img alt="image-netease" src="https://yx-web-nosdn.netease.im/webdoc/pushkit/4B814CA04E7109778FBE456773AB90E2.jpg" style="width:8%;border: 1px solid #BFBFBF;"> 并且手机该 app icon 上出现推送红色角标 **555**。

若不成功，则进行接下来几步检查：

1. 检查后台是否正确配置推送证书
2. 检查初始化时填写的 cername 是否和管理后台配置的一致
3. 检查打包证书中是否有私钥
4. 检查 provisioning profile 里是否包含新增加的推送证书
5. 检查 SDK 的日志中的 cername 是否和第三步中的 cername 一致
6. 代码调试是否可以获取 deviceToken

:::note note
如果以上步骤均尝试，仍有疑问，请 [提交工单](https://app.yunxin.163.com/global/service/ticket/create) 联系网易云信技术支持工程师，以提供解决方案。
:::