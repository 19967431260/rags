AI 助聊（前端 UI 中展示为 **回复灵感**）是一项基于场景智能推荐的聊天辅助功能，为用户提供多种风格的对话建议，助力活跃社交氛围，有效提升用户的社交体验和聊天效率。本文介绍 AI 助聊的接入方式及实现细节。

## 适用场景

当前 AI 助聊功能主要针对娱乐社交场景优化，底层模型设定为陌生人社交环境下的对话推荐。如需其他业务场景（如办公提效、客服应答等），可 [提交工单](https://app.yunxin.163.com/global/service/ticket/create) 联系网易云信技术支持工程师额外调整实现。

<style>
table th:first-of-type {width: 25%;}
table th:nth-of-type(2) {width: 25%;}
table th:nth-of-type(3) {width: 50%;}
</style>

## 效果展示

AI 助聊提供多种风格的聊天建议，您可根据场景配置不同风格的回复内容。

<div style="display: flex; justify-content: space-between; width: 100%;">
    <div style="width: 50%;text-align: center; caption-side: top;""><b>风格展示一</b><br>
        <img alt="界面展示一.png" src="https://yx-web-nosdn.netease.im/common/fd095e0579b9820d9cf842ec43b7b8d7/image.png" style="width:45%;border: 1px solid #BFBFBF;border-radius:5px;">
    </div>
    <div style="width: 50%;text-align: center; caption-side: top;""><b>风格展示二</b><br>
        <img alt="界面展示二.png" src="https://yx-web-nosdn.netease.im/common/bf0433e1aa8fadfc94fc96183df668d7/image.png" style="width:45%;border: 1px solid #BFBFBF;border-radius:5px;">
    </div>
</div>

## 准备工作

在开始接入 AI 助聊功能前，请确保您已完成以下准备工作：

1. 在 [网易云信控制台](https://app.yunxin.163.com/global/home) 创建应用，开通即时通讯 IM 服务，获取 App Key，用于服务端身份验证。
2. 获取 IM 账号体系相关信息。通过 [注册 IM 账号](https://doc.yunxin.163.com/messaging2/quick-start/jU0Mzg0MTU?platform=client#第二步注册-im-账号)，获取账号 ID (`account_id`) 和用户身份验证令牌 (`accessToken`)。
3. 完成 [导入 IM UIKit 组件](https://doc.yunxin.163.com/messaging-uikit/guide/TA5MzA4ODU?platform=iOS)。

## 接入流程

AI 助聊功能需要客户端和服务端配合实现：

1. **服务端**：负责生成和返回内容，提供 AI 助聊 API 接口。
2. **客户端**：负责发起 HTTPS 请求并展示 AI 生成的聊天建议。

## 第一步：服务端配置

您可以选择使用网易云信提供的 AI 助聊服务，或自行实现服务端逻辑。若使用网易云信服务，请参考 [网易云信 AI 助聊 API](https://doc.yunxin.163.com/messaging2/server-apis/jk4Mzg4OTA?platform=server)。网易云信 AI 助聊服务端接口返回数据格式如下。

```JSON
{
    "code": 200,
    "msg": "success",
    "data": {
        "items": [
            {
                "style": "hot",
                "style_name": "升温热聊",
                "answer": "哇哦，必须漂亮啊，穿啥都好看！"
            },
            {
                "style": "warm",
                "style_name": "贴心暖男",
                "answer": "哇，超级漂亮，很适合你！"
            }
        ]
    }
}
```

具体实现代码，请参考 IM UIKit 开源项目中的 [AIChatDataLoader.swift](https://github.com/netease-kit/nim-uikit-ios/blob/master/app/Custom/AIChatDataLoader.swift) 文件。

:::note note
IM UIKit 默认实现通过 HTTPS 地址请求服务端去获取 AI 助聊的生成内容，如果接入网易云信服务端，需要您重新配置 HTTP 请求的 URL 信息。
:::

## 第二步：配置客户端请求

1. 在请求接口文件 [AIChatDataLoader.swift](https://github.com/netease-kit/nim-uikit-ios/blob/master/app/Custom/AIChatDataLoader.swift) 中更改请求地址：

    ```Swift
    @objcMembers
    open class AIChatDataLoader: NSObject {
        ...

        // 修改 AI 助聊接口路径
        public static func getSquareData(_ messages: [V2NIMMessage]?,
                                    _ lastMessage: V2NIMMessage?,
                                    _ completion: @escaping (Error?, NECommonResult?) -> Void) {
        // 修改 AI 助聊接口路径
        let uri = "im/ai/chat_assistant/v1/chat_assist"
        ...
        }

        ...

        // 修改 AI 助聊服务地址
        private static func getHost() -> String {
            "https://***.****.im/"
        }
    }
    ```

    字段 | 说明 | 示例值 |
    :---- | :---- | :---- |
    getHost | AI 助聊服务端地址 | `https://***.****.im/` |
    uri | 接口路径 | `im/ai/chat_assistant/v1/chat_assist` |

2. 初始化 URLRequest 并配置请求。需初始化的配置包括账号信息、网易云信 AppKey 以及权限校验。具体代码示例请参考类 [AIChatDataLoader.swift](https://github.com/netease-kit/nim-uikit-ios/blob/master/app/Custom/AIChatDataLoader.swift)。

    ```Swift
    private static func getRequest(_ uri: String,
                                 _ messages: [V2NIMMessage]?,
                                 _ lastMessage: V2NIMMessage?) -> URLRequest? {
        let requestUrl = getHost() + uri
        guard let url = URL(string: requestUrl) else {
        return nil
        }
        var request = URLRequest(url: url)
        request.httpMethod = "POST"
        request.setValue(appKey, forHTTPHeaderField: "appkey")
        request.setValue("application/json;charset=utf-8", forHTTPHeaderField: "Content-Type")
        request.setValue(accountId, forHTTPHeaderField: "accountId")
        request.setValue(accessToken, forHTTPHeaderField: "accessToken")

        var bodyDic: [String: Any] = [
        "style_list": ["warm", "hot", "smart"],
        "sender_id": accountId,
        "receiver_id": sessionId,
        ]

        if let lastText = lastMessage?.text {
        bodyDic["receiver_last_message"] = lastText
        }

        var history = [[String: Any]]()
        for message in messages ?? [] {
        if let senderId = message.senderId,
            let text = message.text {
            history.append([
            "sender_id": senderId,
            "text": text,
            ])
        }
        }

        bodyDic["history"] = history

        request.httpBody = try? JSONSerialization.data(withJSONObject: bodyDic)

        return request
    }
    ```

## 第三步：客户端接入

客户端实现 AI 助聊功能需要设置 AI 助聊的内容加载回调：

通过服务端接口加载数据，具体代码示例请参考类 [AIChatDataLoader.swift](https://github.com/netease-kit/nim-uikit-ios/blob/master/app/Custom/AIChatDataLoader.swift)。

```Swift
  public static func loadData(_ messages: [V2NIMMessage]?,
                              _ completion: @escaping ([AIChatCellModel]?, Error?) -> Void) {
    if messages != nil {
      self.messages = messages
    }

    self.lastMessage = AIChatDataLoader.getLastTextMessage(messages)

    // 根据当前上下文信息获取 AI 助聊需要展示的内容
    getSquareData(messages, lastMessage) { error, result in
      var models = [AIChatCellModel]()
      if let data = result?.originData?["data"] as? [String: Any],
         let items = data["items"] as? [[String: Any]] {
        // 将内容转换为[AIChatCellModel]格式
        for (index, item) in items.enumerated() {
          if index % 3 == 0 {
            models.append(AIChatCellModel(tagTitle: item["style_name"] as? String,
                                          tagTitleColor: UIColor(hexString: "#F159A2"),
                                          tagTitleBackgroundColor: UIColor(hexString: "#FFE8F3"),
                                          contentTitle: item["answer"] as? String))
          }

          if index % 3 == 1 {
            models.append(AIChatCellModel(tagTitle: item["style_name"] as? String,
                                          tagTitleColor: UIColor(hexString: "#E75257"),
                                          tagTitleBackgroundColor: UIColor(hexString: "#FFE8E8"),
                                          contentTitle: item["answer"] as? String))
          }

          if index % 3 == 2 {
            models.append(AIChatCellModel(tagTitle: item["style_name"] as? String,
                                          tagTitleColor: UIColor(hexString: "#598CF1"),
                                          tagTitleBackgroundColor: UIColor(hexString: "#E8F4FF"),
                                          contentTitle: item["answer"] as? String))
          }
        }
      }
      completion(models, error)
    }
  }
```

`AIChatCellModel` 参数说明

| 参数 | 类型 | 说明 |
| :---- | :---- | :---- |
| tagTitle | String | 助聊标签文案 |
| tagTitleColor | UIColor | 助聊标签颜色，例如 `UIColor(hexString: "#598CF1")` |
| tagTitleBackgroundColor | UIColor | 助聊标签背景色，例如 `UIColor(hexString: "#E8F4FF")` |
| contentTitle | String | 助聊内容 |

设置 AI 助聊的内容加载回调，具体代码示例请参考类 [CustomConfig.swift](https://github.com/netease-kit/nim-uikit-ios/blob/master/app/Custom/CustomConfig.swift)。

```Swift
/// 设置 AI 助聊的数据加载器
/// messages: 上下文消息
/// lastMessage: 最后一条对方发送的文本消息
/// completion：回调，回调参数为数据列表([AIChatCellModel]?)和错误信息(Error?)
ChatUIConfig.shared.aiChatDataLoader = { messages, lastMessage, completion in
    AIChatDataLoader.loadData(messages, lastMessage, completion)
}

/// AI 助聊入口按钮点击事件
ChatUIConfig.shared.aiChatDidClick = { aiChatViewController, messages in
    // 最后一条消息未发生变更则不重新加载
    if messages?.last?.messageClientId == aiChatViewController.lastMessages?.last?.messageClientId {
    return
    }

    // 展示加载中动画
    aiChatViewController.showLoadingView()
    // 加载数据，调用 ChatUIConfig.shared.aiChatDataLoader
    aiChatViewController.loadMoreData(messages)
}

/// AI 助聊重新加载按钮点击事件
ChatUIConfig.shared.aiChatReloadClick = { aiChatViewController, messages in
    // 展示加载中动画
    aiChatViewController.showLoadingView()
    // 重新加载数据，调用 ChatUIConfig.shared.aiChatDataLoader
    aiChatViewController.loadMoreData(messages)
}
```