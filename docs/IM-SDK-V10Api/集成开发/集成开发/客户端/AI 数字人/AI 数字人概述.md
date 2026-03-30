网易云信即时通讯 IM 的 AI 数字人，既可以是虚拟的 AI 对话伙伴，又可以是高效的协同工作助手。

AI 数字人融合了第三方主流大模型 LLM（Large Language Models），也可定制贴合业务所需更高安全性的本地大模型，再结合灵活的企业私有知识库资料，确保 AI 数字人能无缝融入多样化的业务场景。凭借 AI 数字人高度拟人化、智能化的特性，您可以为 IM 应用注入活力，拓展丰富聊天体验，有效提升沟通效率与用户体验。

本文介绍了客户端接入和使用已经配置好的 AI 数字人的相关内容。

<a id="billing"></a>

:::note note
- 目前 AI 数字人处于免费试用阶段，您可以在 [网易云信控制台](https://app.yunxin.163.com/global/home) 免费开通和使用 AI 数字人功能，详细步骤参考 [开通和添加 AI 数字人](https://doc.yunxin.163.com/console/concept/TYxMDEzNDg?platform=console)。开通后，您可以免费使用三个月。后续计费方式将另行通知。
- 自 V10.8.30 版本，网易云信支持 AI 数字人 **流式输出** 能力，通过实时分片传输 AI 生成的内容，降低响应延迟、支持中断控制，显著改善用户交互体验。
:::

## 支持平台

本文内容适用的开发平台或框架如下表所示，涉及的接口请参考下文 [相关接口](#相关接口) 章节：

安卓 | iOS | macOS/Windows | Web/uni-app/小程序 | Node.js/Electron | 鸿蒙 | Flutter
:----: | :----: | :----: | :----: | :----: | :---: | :----:
✔️️️ | ✔️️️ | ✔️️️ | ✔️️ | ✔️️ | ✔️️ | ✔️️

## 功能概述

### 业务场景

您通过在 [网易云信控制台](https://app.yunxin.163.com/global/home) 上创建对应的 AI 数字人，即可实现以下四种场景：

场景类型 | 说明
--- | --- 
**AI 单聊** | 用户与 AI 数字人一对一聊天。用户可以直接与 AI 数字人发起一对一的聊天会话。无论是寻求信息查询、情感陪伴、知识分享还是娱乐互动、实现角色扮演/拟人沟通、AI 客服等场景，AI 数字人都能迅速响应，提供个性化的反馈和服务。
**AI 聊** | 双人聊中 @AI 数字人引出会话。当两个用户正在进行一对一聊天时，任意一方可以通过艾特（@）AI 数字人的方式，邀请其参与对话。AI 数字人会根据当前聊天的上下文，结合提问回答有用的信息，促进更深层次的交流。<note type="note">**AI 聊** 是网易云信即时通讯 IM 的创新功能，终端用户可以在 IM 单聊场景里，直接艾特（@）AI 数字人，快速参与到好友互动中，无需拉群或加好友，以第三人称提供 AI 辅助和聊天互动。</note>
**AI 群聊** | 群聊中 @AI 数字人。在群聊环境中，AI 数字人同样可以被召唤加入。通过艾特（@）操作，AI 数字人能够理解群聊的主题和氛围，为群组成员提供实时的智能建议、解答疑问或是活跃气氛，成为群聊中的智慧助手，提升整体的沟通效率和娱乐性。用户可以将数字人拉入群中，进行互动，当然您也可以使用 **AI 聊** 功能替代。
**AI 助聊** | 预设 AI 聊天提示词选项。通过 NIM SDK 代理接口，结合聊天对方的用户角色属性和 IM 聊天上下文，为用户推荐聊天话题和措词，为用户提供表达建议。

### AI 输出模式

AI 数字人支持两种输出模式，开发者可根据产品需求选择合适的方式：

输出模式 | 特性
--- | ---
非流式输出 | <li>响应时间通常为 3-10 秒，等待完整内容生成后再发送。<li>AI 内容生成采用流式方式，但实现需等待全部内容生成后才通过 IM 通道下发，存在一定消息延迟。<li>无法体现 AI 思考与回复的渐进过程。<li>无法打断输出过程，需要等待回复完毕才能结束聊天。
流式输出 | <li>通过实时分片传输 AI 生成的内容，降低消息延迟。<li>支持消息内容的渐进式展示，模拟人类打字输出效果，增强对话真实感。<li>支持打断 AI 输出，减少无效内容生成，节约计算资源。<li>支持 AI 消息的重新生成和输出，增强交互体验。

### 流式输出

AI 数字人流式输出功能通过实时分片传输 AI 生成的内容，显著改善用户交互体验。

流式输出模式下，支持开发者控制 AI 交互，包括打断 AI 输出以及请求重新生成 AI 回复。

- **打断输出：** 用户可随时打断正在输出的 AI 回复，支持以下三种处理方式：
    - 停止输出：以当前输出内容为最终消息。
    - 撤回：直接撤回整条消息。
    - 更新：用自定义文本替换当前消息。
- **重新生成：** 用户可请求重新生成 AI 回复，支持以下两种方式：
    - 更新原消息：新内容覆盖原消息（限 3 天内消息）。
    - 发送新消息：创建全新消息来展示重新生成的内容。

<!-- ## 应用场景

AI 数字人旨在推动工作效率与增强团队协作，其应用场景包括并不限于以下情形：

- 在跨国企业协作中，AI 数字人的多语言支持能力能跨越语言界限，成为团队间无缝沟通的桥梁。员工只需通过 IM 平台与 AI 数字人互动，无论是项目进度查询、技术问题咨询，还是跨部门协作需求，都能获得即时、精准的回应，大大降低了沟通成本与时间延误。

- 在金融行业，通过定制化 AI 数字人，银行和保险公司能够为客户提供 24/7 的个性化咨询服务。AI 数字人不仅能解答常见的金融产品疑问，还能根据客户的提问上下文，提出个性化的理财建议，增强了客户互动的同时，也提升了服务的专业性和满意度。

- 在教育行业，在线教育平台利用 AI 数字人打造智能助教，它可以依据机构积累的题库以及学生的学习进度和难点，提供定制化学习计划和即时答疑服务。这种个性化的辅导方式不仅提高了学习效率，也让教育变得更加有趣和互动。

- 在医疗健康行业，AI 数字人可以为患者提供初步问诊服务。通过分析患者的症状描述，AI 数字人给出初步的健康建议或引导至相应的医疗服务，减轻了医生的工作负担，也加快了患者获取帮助的速度。

- 在零售与电商行业，通过 AI 数字人进行客户服务和商品推荐，不仅提升了顾客购物体验，还通过分析顾客行为数据，实现了更加精准的个性化营销策略。-->

## 注意事项

- AI 数字人是一个普通成员，但是需要与普通成员有所区分。因此，普通成员使用 `User` 数据结构，而 AI 数字人使用 `AIUser` 数据结构。
- 为了保障 AI 数字人发送的消息的安全合规，AI 数字人发送消息之前，SDK 会发送第三方回调、安全通、抄送等，实现对消息的校验。

## 配置数字人

配置数字人的相关流程如下所示，如果您已经完成了第一步和第二步，则可以视情况跳过步骤：

1. 在 [网易云信控制台](https://app.yunxin.163.com/global/home) 上创建了至少一个应用。若无应用，请参考 [创建应用](https://doc.yunxin.163.com/console/concept/TIzMDE4NTA?platform=console)。
2. 为应用开通了 IM 产品。详细步骤请参考 [开通或试用服务](https://doc.yunxin.163.com/console/concept/zc3NDYzNzc?platform=console)。
3. 添加了至少一个 AI 数字人。详细步骤请参考 [开通和添加 AI 数字人](https://doc.yunxin.163.com/console/concept/TYxMDEzNDg?platform=console)。配置的相关流程如下所示：

    <img alt="流程图.png" src="https://yx-web-nosdn.netease.im/common/caf8b8e0ece86702440a9fa554355ac3/流程图.png" style="width:100%;border: 1px solid #BFBFBF;">

## 相关接口

配置了 AI 数字人后，您就可以在客户端实现以下操作：

1. 调用 `getAIUserList` 查询您在网易云信控制台上配置的 AI 数字人列表。
2. 调用 `addAIListener` 添加监听器。注册成功后，当聊天会话中添加了 AI 数字人后，SDK 会返回对应的回调。 
3. 调用 `proxyAIModelCall` 实现通过 AI 数字人发起 LLM（Large Language Models）模型请求。
4. 调用 `sendMessage` 在聊天会话中为 AI 数字人，根据 AI 数字人账号 ID（`aiUserAccountId`）实现消息发送。
5. （可选）调用 `stopAIStreamMessage` 打断 AI 数字人的流式输出。
6. （可选）调用 `regenAIMessage` 重新输出 AI 数字人流式消息。

<!--调用 `tbd` 实现-->

:::::: div custom-tabs
::: tab 安卓/iOS/macOS/Windows
API | 说明
--- | ---
[`addAIListener`](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#addAIListener) | 注册 API 数字人相关监听
[`removeAIListener`](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#removeAIListener) | 取消注册 AI 数字人相关监听
[`getAIUserList`](https://doc.yunxin.163.com/messaging2/client-apis/TA0NjQ0ODE?platform=client#getAIUserList) | 查询 AI 数字人列表
[`proxyAIModelCall`](https://doc.yunxin.163.com/messaging2/client-apis/TA0NjQ0ODE?platform=client#proxyAIModelCall) | 通过 AI 数字人发起 LLM（Large Language Models）模型请求
[`sendMessage`](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#sendMessage) | 发送消息
[`stopAIStreamMessage`](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#stopAIStreamMessage) | 停止 AI 数字人消息输出。可选择直接停止输出，也可以选择撤回/更新 AI 数字人消息
[`regenAIMessage`](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#regenAIMessage) | 重新请求输出 AI 数字人消息
[`stopAIModelStreamCall`](https://doc.yunxin.163.com/messaging2/client-apis/TA0NjQ0ODE?platform=client#stopAIModelStreamCall) | 停止 AI 流式输出请求
:::
::: tab Web/uni-app/小程序/Node.js/Electron/鸿蒙
API | 说明
--- | ---
[`on`](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#on) | 注册 API 数字人相关监听
[`off`](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#off) | 取消注册 AI 数字人相关监听
[`getAIUserList`](https://doc.yunxin.163.com/messaging2/client-apis/TA0NjQ0ODE?platform=client#getAIUserList) | 查询 AI 数字人列表
[`proxyAIModelCall`](https://doc.yunxin.163.com/messaging2/client-apis/TA0NjQ0ODE?platform=client#proxyAIModelCall) | 通过 AI 数字人发起 LLM（Large Language Models）模型请求
[`sendMessage`](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#sendMessage) | 发送消息
[`stopAIStreamMessage`](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#stopAIStreamMessage) | 停止 AI 数字人消息输出。可选择直接停止输出，也可以选择撤回/更新 AI 数字人消息
[`regenAIMessage`](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#regenAIMessage) | 重新请求输出 AI 数字人消息
[`stopAIModelStreamCall`](https://doc.yunxin.163.com/messaging2/client-apis/TA0NjQ0ODE?platform=client#stopAIModelStreamCall) | 停止 AI 流式输出请求
:::
::: tab Flutter
API | 说明
--- | ---
[`listen`](https://doc.yunxin.163.com/messaging2/client-apis/DAyMDc1MjE?platform=client#listen) | 注册 API 数字人相关监听
[`off`](https://doc.yunxin.163.com/messaging2/client-apis/DAyMDc1MjE?platform=client#off) | 取消注册 AI 数字人相关监听
[`getAIUserList`](https://doc.yunxin.163.com/messaging2/client-apis/DAyMDc1MjE?platform=client#getAIUserList) | 查询 AI 数字人列表
[`proxyAIModelCall`](https://doc.yunxin.163.com/messaging2/client-apis/DAyMDc1MjE?platform=client#proxyAIModelCall) | 通过 AI 数字人发起 LLM（Large Language Models）模型请求
[`sendMessage`](https://doc.yunxin.163.com/messaging2/client-apis/TU1MDAxMjA?platform=client#sendMessage) | 发送消息
[`stopAIStreamMessage`](https://doc.yunxin.163.com/messaging2/client-apis/TU1MDAxMjA?platform=client#stopAIStreamMessage) | 停止 AI 数字人消息输出。可选择直接停止输出，也可以选择撤回/更新 AI 数字人消息
[`regenAIMessage`](https://doc.yunxin.163.com/messaging2/client-apis/TU1MDAxMjA?platform=client#regenAIMessage) | 重新请求输出 AI 数字人消息
[`stopAIModelStreamCall`](https://doc.yunxin.163.com/messaging2/client-apis/DAyMDc1MjE?platform=client#stopAIModelStreamCall) | 停止 AI 流式输出请求
:::
::::::

## 最佳实践

- [实现与 AI 数字人聊天](https://doc.yunxin.163.com/aiagents/guide/zg2MzU5NDc?platform=client)
- [通过 AI 数字人在聊天时实现多国语言翻译](https://doc.yunxin.163.com/aiagents/guide/TIxODQyNzE?platform=client)
- [通过 AI 数字人在聊天时实现划词搜索](https://doc.yunxin.163.com/aiagents/guide/Dc5NzMwMTY?platform=client)