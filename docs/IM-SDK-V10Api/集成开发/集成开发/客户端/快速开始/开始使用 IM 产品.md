本文介绍了接入网易云信即时通讯（Instant Messages，简称 IM）产品国内单元的流程。如果您暂未明确具体的需求细节，请联系您的网易云信商务经理，沟通您的业务背景。

<!--
若用户有明确的出海业务场景，需要先接入海外单元，再进行对应的开发集成。具体的海外接入流程，请参考 [海外数据中心](https://doc.yunxin.163.com/messaging2/concept/Dk0Nzk3MDE?platform=client)。
-->

## <span id="创建账号">准备工作</span>

根据本文操作前，请确保您已经完成了以下设置：

1. [注册](https://app.netease.im/regist) 网易云信开发者账号，并能 [登录](https://app.netease.im/login) 网易云信控制台。
2. 创建应用，并获取到了应用密钥（App Key）。详细步骤，请参考 [创建应用](https://doc.yunxin.163.com/console/guide/TIzMDE4NTA?platform=console)。

## <span id="开通 IM 套餐包">第一步：开通产品</span>

网易云信 IM 产品分为免费版和套餐包版。

- 套餐包支持安卓、iOS、Web、电脑桌面等主流平台，提供单聊、群聊、文字、图片、语音、视频、地理位置等消息类型，同时支持自定义消息，满足常见的个性化需求。
- 免费版能注册的 IM 账号数上限为 100 个，套餐包没有限制。

使用网易云信 IM 套餐包功能前，您需要在网易云信控制台开通 IM 套餐包服务。开通步骤如下：

1. 在 [网易云信控制台](https://app.yunxin.163.com/global/home) 首页 **应用管理** 列表下，选择并单击一款应用。

    <img alt="image.png" src="https://yx-web-nosdn.netease.im/common/1a2418461ab8435724f793b957cf7930/image.png" style="width:80%;border: 1px solid #BFBFBF;">

2. 在 **应用配置** 页面，找到并单击 **IM 即时通讯** 下的 **免费试用** 或 **正式开通**。

    <img alt="image.png" src="https://yx-web-nosdn.netease.im/common/7b1689604e5ee7af4015587aa624bdcb/image.png" style="width:80%;border: 1px solid #BFBFBF;">

    :::note note
    因产品服务升级，仅部分存量客户能开通 IM 旧版套餐包（即专业版和极速版）。如果您有相关需求，请联系您的网易云信商务经理。
    :::

### 方式一：免费试用

如需免费试用 IM，则在 **免费试用** 界面指定 IM 节点的服务区域为 **国内** 或 **海外**（海外节点适用有出海及国际化业务场景的客户），然后单击 **立即试用**。

<img alt="免费试用 IM 7 天.png" src="https://yx-web-nosdn.netease.im/common/b13afd036444fca5bc4d7cf184e55c5f/image.png" style="width:50%;border: 1px solid #BFBFBF;">

::: note notice
- 免费试用期限为 7 个自然日，试用结束后默认当前应用为 **IM 即时通讯 免费版**，您将无法使用 IM 套餐包支持的功能。
- 试用结束后，您可以单击 **套餐升级** 将免费版升级为套餐包，具体开通步骤请参考下文正式开通。
:::

### 方式二：正式开通

1. 单击 **IM 即时通讯** 下的 **正式开通**。

2. 在 **套餐对比** 界面指定 IM 节点的服务区域为 **国内**。

2. 仔细查看套餐详情，并单击您适用的产品套餐。

    <img alt="image.png" src="https://yx-web-nosdn.netease.im/common/81adc7a673eddab753f85e6c9ff4515b/image.png" style="width:100%">

2. 鼠标继续下滑，按应用的实际需求配置服务。

3. 按照控制台会生成的预估费用，设置不少于预估费用的 **充值金额**。

    关于具体的计费策略，请参考 [计费方式](https://doc.yunxin.163.com/messaging2/concept/DczNjI1ODM?platform=client) 或咨询您的网易云信商务经理。

3. 勾选协议条款，并单击 **提交订单**。

6. 单击 **立即支付** 完成订单支付。

    :::note note
    请确保账号余额中有足够的金额开通服务。
    :::

7. 开通完成后基本信息页面 IM 即时通讯套餐包状态为 **已开通**，您可以单击 **功能配置** 继续开通和配置具体功能。

    <img alt="image.png" src="https://yx-web-nosdn.netease.im/common/b4c08cb9c2fa97f2bcc99523ffae697a/image.png" style="width:35%;border: 1px solid #BFBFBF;">

## <span id="创建 IM 账号">第二步：注册 IM 账号</span>

网易云信 IM 账号是网易云信 IM 系统中用户的唯一身份标识。通过 IM 账号，用户可以在应用中使用各种 IM 服务。您在将自身应用与网易云信 IM 对接时，需要注册 IM 账号与自身应用中的账号相对应。您可以根据业务需要，注册多个网易云信 IM 账号来构成应用的账号体系。

为了保护用户账号的隐私和安全，建议您区分 IM 测试账号和 IM 业务账号。

### 类型一：业务账号

如果您有具体的业务需求，那么可以通过服务端 API 注册 IM 业务账号。详情请参考 [注册 IM 账号](https://doc.yunxin.163.com/messaging2/server-apis/TQyNjgyMzc?platform=server)。

::: note notice
- 通过服务端 API 注册的账号不会出现在 [网易云信控制台](https://app.yunxin.163.com/global/home) 的账号列表中。
- 通过服务端 API 注册账号成功后，网易云信将返回 `account_id` 与 `token`，请在应用服务器上维护 `account_id` 与 `token` 信息列表。
:::

### 类型二：测试账号

如果您只需要体验产品或者快速测试功能，那么您可以在 [网易云信控制台](https://app.yunxin.163.com/global/home) 创建 IM 测试账号。

1. 在 [网易云信控制台](https://app.yunxin.163.com/global/home) 首页 **应用管理** 列表下，选择一款应用，进入 **应用配置** 页面。
2. 单击 **IM 即时通讯 套餐包** 下的 **功能配置** 按钮，进入 IM 即时通讯配置页。

    <img alt="image.png" src="https://yx-web-nosdn.netease.im/common/847eb7f407623f92aa7012c0577c2979/image.png" style="width:35%;border: 1px solid #BFBFBF;">

2. 在顶部选择 **基础功能** 页签，单击 **测试账号管理** 下的 **子功能配置**。

    <img alt="image.png" src="https://yx-web-nosdn.netease.im/common/0a0c60a15ca9e297c4b4ce4090d8bd34/image.png" style="width:35%;border: 1px solid #BFBFBF;">

3. 单击 **新建账号**，在弹窗填写 **账号**、**昵称**、**密码** 后，单击 **确定**。

    在 [网易云信控制台](https://app.yunxin.163.com/global/home) 创建的 IM 账号信息，与服务端 OpenAPI 账号信息字段的映射关系如下：

    - **账号**：`account_id`
    - **密码**：`token`
    - **昵称**：`name`

4. （可选）对于创建好的测试账号，您可以在 [网易云信控制台](https://app.yunxin.163.com/global/home) 修改昵称，重置密码，以及禁用操作。

    <img alt="image.png" src="https://yx-web-nosdn.netease.im/common/79c4d3b0e38af6e29b42680417b089e3/image.png" style="width:100%">

## 第三步：配置功能

1. 在 [网易云信控制台](https://app.yunxin.163.com/global/home) 首页 **应用管理** 列表下，选择一款应用，进入 **应用配置** 页面。
2. 单击 **IM 即时通讯 套餐包** 下的 **功能配置** 按钮进入 IM 即时通讯配置页。

    <img alt="image.png" src="https://yx-web-nosdn.netease.im/common/0ca1a84112a7edeb6341cccf96de1ac6/image.png" style="width:35%">

2. 在顶部选择 **基础功能**、**全局功能** 或其他页签，开启或配置所需功能。

    <img alt="image.png" src="https://yx-web-nosdn.netease.im/common/9cb4fd32ae9f510eee7ab4d397f4f65a/image.png" style="width:50%">

    请参考下文了解 IM 基础功能和全局功能的功能说明情况。

### 基础功能

您需要单独开通和配置的基础功能说明，请参考如下列表：

- ✔️：表示默认开启、默认支持、有默认设置
- 🔒：表示默认不开启、默认不支持、无默认设置

| 基础功能 | 功能介绍 | 默认设置 |
| ---- | ---- | ---- |
| **IM 服务区域** | <ul><li>服务区域决定了该应用下产品（此处仅对 IM 产品生效）的数据处理和存储，将在哪个区域的单元节点完成。</li><li>服务区域在正式开通 IM 套餐包时指定。</li></ul> | 🔒 |
| **信令** | 开启信令服务 | 🔒 |
| **API 调试** | API 调试测验 | ✔️️ |
| **测试账号管理** | 通过网易云信控制台创建的账号管理。单击 **子功能配置** 创建和管理 IM 账号。 | ✔️️ |
| **登录策略** | 设置用户登录应用服务器或网易云信服务器的方式。单击 **编辑** 设置 [登录鉴权方式](https://doc.yunxin.163.com/messaging2/server-apis/jA1MTQ4MDU?platform=server)。 | ✔️️ 静态 Token |
| **多端登录模式** | 设置用户在不同端的登录模式。单击 **编辑** 设置 [多端登录与互踢](https://doc.yunxin.163.com/messaging2/guide/DUyNjI2MjQ?platform=client)。默认为：<ul><li>桌面 PC 与 Web 端互踢</li><li> 移动安卓与 iOS 端互踢</li><li> 桌面与移动端同时登录</li></ul> | ✔️️ |
| **第三方回调** | 单击 **编辑** 设置第三方回调的默认服务器地址。 | 无 |
| **iOS 应用角标未读数上限** | 针对 iOS 应用角标的未读消息数上限配置，最大配置为 99。 | 0 |
| **应用服务器 IP 白名单** | 仅支持设置的 IP 地址访问，多用于安全防护功能。 | 🔒 |
| **第三方厂商消息分类** | 开启后会将所有通过网易云信的消息默认配置为配置字段用以各平台的消息分类（单独设置的以设置的为准）。单击 **子功能配置** 设置各推送厂商的消息分类。 | 无 |
| **推送通知 TTL（Time to Live）** | 设置推送离线消息的存活时间，填写推送通知服务必须向终端节点发送消息的秒数（60 秒 ~ 604800 秒/7 天）。 | 默认不填写 |
| **自定义推送** | 配置自定义推送文案（通知栏现实的文案），最多可配 100 种自定义文案，每种自定义文案用一个自定义类型来标识。 | 🔒 |
| **添加好友逻辑配置** | 开启后，用户直接调用同意协议或 API 添加好友时，系统将进行判断对方是否有发起好友申请。 | 🔒 |
| **单聊消息配置** | 设置非好友关系是否允许发送单聊消息。 | ✔️️ |
| **消息扩展字段上限调整** | 单条消息可扩展字段的长度上限。 | 长度限制与各套餐的配置有关，具体请参考 [字段限制说明](https://doc.yunxin.163.com/messaging2/faq/zc1MzA1MDY?platform=client)。 |
| **消息 attach 字段大小上限** | 修改发送图片/语音/视频/文件消息的 `attach` 字段上限。 | 长度限制与各套餐的配置有关，具体请参考 [字段限制说明](https://doc.yunxin.163.com/messaging2/faq/zc1MzA1MDY?platform=client)。 |
| **消息漫游** | 设置用户是否可拉取云端漫游消息。 | 🔒 |
| **消息撤回时长** | 设置用户发送消息后可在多长时间内操作撤回。 | 120 秒 |
| **撤回消息覆盖策略** | 设置用户撤回消息时，是否需要覆盖原始消息的推送。 | 默认不覆盖 |
| **PC 端在线，强推消息策略配置** | 设置当 PC 端在线时阻止强推消息推到手机端。 | 🔒 |
| **被拉黑时被拉黑者无法唤起呼叫** | 开启后被拉黑者无法呼叫对方。 | 🔒 |
| **IM 离线原因抄送配置** | 开通后抄送内 IM 的 `logoutReason` 字段可区分是被踢还是主动登出还是掉线。 | 🔒 |
| **聊天室离线原因抄送配置** | 开通后抄送内聊天室的 `logoutReason` 字段可区分是被踢还是主动登出还是掉线。 | 🔒 |
| **拉黑场景可以正常下发消息已读回执通知** | 开启后若已拉黑对方，则对方的已读回执仍可以发送。 | 🔒 |

### 全局功能

您需要单独开通和配置的全局功能说明，请参考如下列表：

- ✔️：表示默认开启、默认支持、有默认设置
- 🔒：表示默认不开启、默认不支持、无默认设置

| 基础功能 | 功能介绍 | 默认值 |
| ---- | ---- | ---- |
| **好友数** | 单击 **编辑** 设置单用户可添加好友数上限。 | 3000 人 |
| **在线状态订阅** | 可获取用户的当前在线状态（一般用于用户列表、会话界面显示用户在线或离线）。 | 🔒 |
| **单向消息删除** | 单向删除指一方删除不影响其他方的消息存储。 | 🔒 |
| **会话置顶** | [会话置顶](https://doc.yunxin.163.com/messaging2/guide/zExMDk4ODU?platform=client#会话置顶)指服务端维护需要个性化配置的会话。 | 🔒 |
| **全员广播** | 即 [广播通知](https://doc.yunxin.163.com/messaging2/guide/zMyMjcyOTA?platform=client)，单条消息可发送给所有用户。 | 🔒 |
| **历史消息** | 单击 **编辑** 设置用户可查询的历史消息范围。 | ✔️️默认 1 年 |
| **高保障消息抄送** | 当客户服务器遇到阻塞或故障不能接受消息时，网易云信会缓存需要抄送的消息，待客户自有服务器恢复正常后重新抄送，保障抄送消息完整到达。该功能为增值服务。 | 🔒 |
| **客户端反垃圾** | 客户端反垃圾用于配置聊天时希望被过滤的敏感词、违禁词，开通后可在子功能配置进行应用级别的客户端词条配置。该功能为增值服务。 | 🔒 |
| **登录登出事件记录查询** | 可随时查询用户的登录登出事件。该功能为增值服务。 | 🔒 |
| **会话消息标记** | 需要实现 [PIN 消息](https://doc.yunxin.163.com/messaging2/guide/jQ2MTkzODg?platform=client) 功能时，需开通此功能。类似 Slack 应用里 pin（标记）的能力，可针对某条消息做单独标记，并在标记列表单独展示。该功能为增值服务。 | 🔒 |
| **会话消息回复** | 需要实现 [Thread 消息](https://doc.yunxin.163.com/messaging2/guide/jQ2MTkzODg?platform=client#实现消息回复)功能时，需开通此功能。可根据某条消息单独进入一个独立会话序。该功能为增值服务。 | 🔒 |
| **消息快捷评论** | 开启后，可针对某条消息直接进行点表情操作（每条消息最多点亮 100 个表情）。该功能为增值服务。 | 🔒 |
| **全文云端消息检索** | 开启后，针对关键词搜索，可提供应用级别的 [全文检索消息](https://doc.yunxin.163.com/messaging2/guide/jA4MDk5MzA?platform=client#全文搜索历史消息)。该功能为增值服务。 | 🔒 |
| **IM 存储清理任务管理** | IM 存储提交系统任务自动清理。单击 **子功能配置** [新建和管理清理任务](https://doc.yunxin.163.com/messaging2/guide/zgwNTU3Njc?platform=client)。 | ✔️️ |