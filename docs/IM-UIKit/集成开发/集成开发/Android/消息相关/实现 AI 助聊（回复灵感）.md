AI 助聊（前端 UI 中展示为 **回复灵感**）是一项基于场景智能推荐的聊天辅助功能，为用户提供多种风格的对话建议，助力活跃社交氛围，有效提升用户的社交体验和聊天效率。本文介绍 AI 助聊的接入方式及实现细节。

<div id="scenarios">

## 适用场景

当前 AI 助聊功能主要针对娱乐社交场景优化，底层模型设定为陌生人社交环境下的对话推荐。如需其他业务场景（如办公提效、客服应答等），可 [提交工单](https://app.yunxin.163.com/global/service/ticket/create) 联系网易云信技术支持工程师额外调整实现。

<style>
table th:first-of-type {width: 25%;}
table th:nth-of-type(2) {width: 25%;}
table th:nth-of-type(3) {width: 50%;}
</style>

</div>

<div id="examples">

## 效果展示

AI 助聊提供多种风格的聊天建议，您可根据场景配置不同风格的回复内容。

<div style="display: flex; justify-content: space-between; width: 100%;">
    <div style="width: 50%;text-align: center; caption-side: top;""><b>风格展示一</b><br>
        <img alt="界面展示一.png" src="https://yx-web-nosdn.netease.im/common/fd095e0579b9820d9cf842ec43b7b8d7/image.png" style="width:45%;border: 1px solid #BFBFBF;;border-radius:5px;">
    </div>
    <div style="width: 50%;text-align: center; caption-side: top;""><b>风格展示二</b><br>
        <img alt="界面展示二.png" src="https://yx-web-nosdn.netease.im/common/bf0433e1aa8fadfc94fc96183df668d7/image.png" style="width:45%;border: 1px solid #BFBFBF;border-radius:5px;">
    </div>
</div>

</div>

<div id="prerequisites">

## 准备工作

在开始接入 AI 助聊功能前，请确保您已完成以下准备工作：

1. 在 [网易云信控制台](https://app.yunxin.163.com/global/home) 创建应用，开通即时通讯 IM 服务，获取 App Key，用于服务端身份验证。
2. 获取 IM 账号体系相关信息。通过 [注册 IM 账号](https://doc.yunxin.163.com/messaging2/quick-start/jU0Mzg0MTU?platform=client#第二步注册-im-账号)，获取账号 ID (`account_id`) 和用户身份验证令牌 (`accessToken`)。
3. 完成 [导入 IM UIKit 组件](https://doc.yunxin.163.com/messaging-uikit/guide/DAwNDEwNzY?platform=android)。

</div>

<div id="main-content">

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

具体实现代码，请参考 IM UIKit 开源项目中的 [MainActivity.java](https://github.com/netease-kit/nim-uikit-android/blob/master/app/src/main/java/com/netease/yunxin/app/im/main/MainActivity.java) 文件。

:::note note
IM UIKit 默认实现通过 HTTPS 地址请求服务端去获取 AI 助聊的生成内容，如果接入网易云信服务端，需要您重新配置 HTTP 请求的 URL 信息。
:::

## 第二步：配置客户端请求

1. 在您的应用配置文件 [AppConfig.java](https://github.com/netease-kit/nim-uikit-android/blob/master/app/src/main/java/com/netease/yunxin/app/im/AppConfig.java) 中配置请求地址：

    ```Java
    // 配置 AI 助聊服务地址
    AIHelperHost_ONLINE = "https://***.****.im/";
    AIHelperUrl = "/ai/chat_assistant/v1/chat_assist";
    ```

    字段 | 说明 | 示例值 |
    :---- | :---- | :---- |
    AIHelperHost_ONLINE | AI 助聊服务端地址 | `https://***.****.im/` |
    AIHelperUrl | 接口路径 | `/ai/chat_assistant/v1/chat_assist` |

2. 配置请求 Header 并初始化 OkHttp。需初始化的配置包括账号信息、网易云信 AppKey 以及权限校验。具体代码示例请参考类 [IMKitNetRequester](https://github.com/netease-kit/nim-uikit-android/blob/master/app/src/main/java/com/netease/yunxin/app/im/network/IMKitNetRequester.java)。

    ```Java
    public void setup(String url, String appKey, String accountId, String signature) {
    if (TextUtils.isEmpty(url)) {
        return;
    }
    this.appKey = appKey;
    headerMap.put("appKey", appKey);
    headerMap.put("accountId", accountId);
    headerMap.put("accessToken", signature);
    headerMap.put("Content-Type", "application/json;charset=utf-8");
    
    // 初始化 OkHttp 客户端
    OkHttpClient httpClient =
        new OkHttpClient.Builder()
            .connectTimeout(10L, TimeUnit.SECONDS)
            .readTimeout(5L, TimeUnit.SECONDS)
            .writeTimeout(5L, TimeUnit.SECONDS)
            .build();

    // 初始化 Retrofit
    retrofit =
        new Retrofit.Builder()
            .baseUrl(url)
            .client(httpClient)
            .addConverterFactory(GsonConverterFactory.create())
            .build();

    // 创建 API 接口实例
    aiChatHelperAPI = retrofit.create(AIChatHelperAPI.class);
    }
    ```

## 第三步：客户端接入

1. 参考 IM UIKit 开源工程中的 [MainActivity.java](https://github.com/netease-kit/nim-uikit-android/blob/9c776bf52b7861562219523ef34a9eadb7c0a6a9/app/src/main/java/com/netease/yunxin/app/im/main/MainActivity.java#L648C33-L648C45) 文件，通过 HTTPS 请求获取助聊信息并设置给 AI 助聊页面。

2. 配置 AI 助聊回调，`onAIHelperClick` 在 AI 助聊展示或者单击刷新的时候进行回调。

    参数 | 类型 | 说明 |
    :---- | :---- | :---- |
    context | Context | 会话页面上下文信息 |
    view | AIHelperView | AI 助聊 View，您可通过 AIHelperView 提供的对外方法进行操作 |
    action | String | 操作行为，用来区分 AIHelperView 上不同的单击事件。 |
    msgList | List | 当前聊天页面的消息列表。默认当前拉取到的 100 条消息 |

    ```Java
    ChatUIConfig uiConfig = new ChatUIConfig();
    uiConfig.chatInputMenu = new IChatInputMenu() {
    @Override
    public boolean onAIHelperClick(
        Context context, View view, String action, List<IMMessageInfo> msgList) {
        if (TextUtils.equals(action, ActionConstants.ACTION_AI_HELPER_REFRESH)
            && view instanceof AIHelperView) {
        // 刷新或重试时加载 AI 助聊内容
        // 业务逻辑处理参考下文
        loadAIHelper((AIHelperView) view, msgList);
        } else if (TextUtils.equals(action, ActionConstants.ACTION_AI_HELPER_SHOW)
            && view instanceof AIHelperView) {
        // AIHelperView 由不可见变为可见的时候触发，此时不会主动展示 loading 动画
        // 您可以根据自己的业务来判断是否要展示
        AIHelperView helperView = ((AIHelperView) view);
        helperView.showLoading();
        // 业务逻辑处理参考下文
        loadAIHelper((AIHelperView) view, msgList);
        }
        return true;
    }
    };
    ```

4. 实现 AI 助聊内容加载与设置，参数说明请参考 [AIHelperItem](https://github.com/netease-kit/nim-uikit-android/blob/master/chatkit-ui/src/main/java/com/netease/yunxin/kit/chatkit/ui/normal/view/AIHelperView.java#L242)：

    参数 | 类型 | 说明 |
    :---- | :---- | :---- |
    content | String | 每一条助聊展示的内容 |
    tag | String | 每一条助聊展示的标签 |
    tagTextColor | int | 助聊标签的文本颜色（资源 ID） |
    tagBgDrawable | int | 助聊标签的背景颜色（资源 ID） |

    ```Java
    private void loadAIHelper(AIHelperView helperView, List<IMMessageInfo> msgList) {
    if (helperView == null) {
        return;
    }
    // 根据当前聊天信息获取 AI 助聊内容
    // 将内容转换为 List<AIHelperView.AIHelperItem>格式
    List<AIHelperView.AIHelperItem> itemList = new ArrayList();
    // 这里添加获取 AI 助聊内容的逻辑

    if (itemList.isEmpty()) {
        // 内容为空时显示错误信息
        helperView.showError("");
    } else {
        // 设置 AI 助聊展示内容
        helperView.setHelperContent(itemList);
    }
    }
    ```

3. 设置配置信息到 UIKit 组件中。

    ```Java
    ChatKitClient.setChatUIConfig(uiConfig);
    ```

</div> 