Postman 是一款 API 开发和测试工具，提供了一个直观的可视化界面，您可以通过该工具发送 HTTP 请求（如GET、POST、PUT、DELETE 等），并查看服务器的响应。它还提供了一些高级功能，如环境变量、多语言、预定义脚本，通过该工具您能够更好地调试和管理您的 API。

本文介绍如何使用 Postman 调试 Netease IM 即时通讯 RESTful API，我们提供了 [Postman Collection](https://faq.yunxin.163.com/Postman.zip) 供您调试测试。

::: note notice
该 Postman Collection 仅供调试测试使用，并未包含所有服务端 API，且存在部分参数与 API 参考文档有偏差，**请以文档为准**。
:::
  

## 前提条件

- 已下载并安装 [Postman](https://www.postman.com/downloads/)。
- 已经下载并解压 [IM Postman Collection](https://faq.yunxin.163.com/Postman.zip)。
- 已在云信控制台[创建应用](https://doc.yunxin.163.com/console/docs/TIzMDE4NTA?platform=console)，获取 App Key。
- 已了解 [API 调用方式](https://doc.yunxin.163.com/messaging/docs/jk3MzY2MTI?platform=server)。
  

## 步骤1 导入并配置环境变量

1. 打开 Postman，单击 **Import**，导入解压后的 Postman Collection 文件夹。

2. 导入成功后，单击右上角眼睛图标，然后在 **Globals** 下单击 **Add** 添加全局变量。

    ![添加环境变量.png](https://yx-web-nosdn.netease.im/common/1028030950c1094c55ad1fbbe2503418/添加环境变量.png)

3. 添加 AppKey 和 AppSecret 两个全局变量，并在 **CURRENT VALUE** 填入在[云信控制台获取](https://doc.yunxin.163.com/console/docs/TIzMDE4NTA?platform=console)的 App Key 和 App Secret。

    ![环境变量.png](https://yx-web-nosdn.netease.im/common/3318a6ac520b450417077f8a839de8d8/环境变量.png)


    单击 **Save** 保存配置，在随后请求时，模板会根据填入的 AppKey 和 AppSecret 自动实时计算生成鉴权参数 Nonce、CurTime、CheckSum。

## 步骤2 开始调试

本节以[注册云信IM账号](https://doc.yunxin.163.com/messaging/docs/DQ3Nzk1MTY?platform=server)和[发送消息](https://doc.yunxin.163.com/messaging/docs/DQ2NTg4ODE?platform=server)接口为例介绍如何使用 Postman 调试 RESTful API。

### 注册云信IM账号

1. 在 Postman 左侧目录选择 **IM > 网易云通信ID > 创建网易云通信ID**，单击 **Send**。

2. 在下方查看响应内容，若 `code` 不是 200，请根据响应内容中的 `desc` 排查问题。

    ![注册账号.png](https://yx-web-nosdn.netease.im/common/845f13b2fd271fea5372bb493833df5c/注册账号.png)

### 发送消息

1. 在 Postman 左侧目录选择 **IM > 消息功能 > 发送普通消息**，单击 **Body**。
    
    Body 默认为 x-www-form-urlencoded 格式，根据 Key 填入对应 Value，已勾选的 Key 为必填参数。参数详细说明请参考[发送消息请求参数](https://doc.yunxin.163.com/messaging/docs/DQ2NTg4ODE?platform=server#%E8%AF%B7%E6%B1%82%E5%8F%82%E6%95%B0)。


    ![发送消息.png](https://yx-web-nosdn.netease.im/common/99bb730e187796aee44ccf79bf425c6c/发送消息.png)


2. 在下方查看响应内容，若 `code` 不是 200，请根据响应内容中的 `desc` 排查问题。


    ![发送失败.png](https://yx-web-nosdn.netease.im/common/dee3df57b24ba51a3e0c0535125e431e/发送失败.png)


### 语言选择

单击 Postman 右侧代码图标，选择您需要的代码语言，即可生成指定语言的示例代码。


![语言选择.png](https://yx-web-nosdn.netease.im/common/79eaae8cd9cd05fa1c11c900209f9a52/语言选择.png)








