网易云信即时通讯（NIM）提供的 UI 组件（UIKit）从 10.2.0 版本起支持 AI 数字人功能，支持您在即时通讯场景中组件化调用 AI 数字人的能力，并通过功能开关在应用层面实现全局一键关闭或启用 AI 数字人能力。

AI 数字人目前从实现层面而言，常见的类型有 AI 聊数字人和 AI 翻译数字人。

:::note note
- **AI 聊** 是网易云信即时通讯 IM 的创新功能，终端用户可以在 IM 单聊场景里，直接艾特（@）AI 数字人，快速参与到好友互动中，无需拉群或加好友，以第三人称提供 AI 辅助和聊天互动。
- 网易云信支持 AI 数字人 **流式输出** 能力，通过实时分片传输 AI 生成的内容，降低响应延迟、支持中断控制，显著改善用户交互体验。
:::

## 功能概览

- 在会话列表中，新增置顶 AI 数字人会话。
- 在通讯录页面，新增我的 AI 数字人。
- 在会话聊天中，支持 AI 数字人聊天功能。详情请参考 [实现与 AI 数字人聊天](https://doc.yunxin.163.com/aiagents/guide/zg2MzU5NDc?platform=client)。包括：
    - 在会话中，支持 AI 数字人聊天功能。
    - 在群聊中，支持添加 AI 数字人，并 @ AI 数字人，AI 数字人会对您的消息进行回复。
<!--未实现
- 在会话聊天中，支持 AI 划词搜索功能。详情请参考 [实现划词搜索](https://doc.yunxin.163.com/aiagents/guide/Dc5NzMwMTY?platform=client)。
-->
- 在会话聊天中，支持 AI 翻译功能。详情请参考 [实现多国语言翻译](https://doc.yunxin.163.com/aiagents/guide/TIxODQyNzE?platform=client)。
- 在与 AI 数字人对话的场景中，当 AI 数字人正在流式输出时，支持打断 AI 数字人的流式输出。详情请参考 [打断 AI 数字人流式输出](https://doc.yunxin.163.com/aiagents/guide/DgyNDI0NTk?platform=client#打断输出)。
- 在与 AI 数字人对话的场景中，当 AI 数字人流式输出完成或者已打断 AI 数字人的流式输出时，支持重新生成 AI 回复。详情请参考 [重新输出 AI 流式消息](https://doc.yunxin.163.com/aiagents/guide/DgyNDI0NTk?platform=client#重新输出)。

<!--
**大概功能实现效果如下图所示：**

<style>
.container {
  display: flex;
  justify-content: space-between;
}

.column {
  flex: 1;
  margin: 5px;
  text-align: center;
}

.column img {
  width: 100%;
  height: auto;
}
</style>

<div class="container">
  <div class="column">
    <figure>    <figcaption style="width: 100%; text-align: center; caption-side: top;"><b>AI 划词搜索</b></figcaption> <img alt="image2.png" src="https://yx-web-nosdn.netease.im/common/ab310b8a0ae08c7164338cc2765c8328/image2.png" style="width:80%;border: 1px solid #BFBFBF;"> </figure>
  </div>
  <div class="column">
    <figure>  <figcaption style="width: 100%; text-align: center; caption-side: top;"><b>AI 语言翻译</b></figcaption> <img alt="image1.png" src="https://yx-web-nosdn.netease.im/common/1e8ff28e8a56e0580f8d554578274eef/image1.png" style="width:80%;border: 1px solid #BFBFBF;"> </figure>
  </div>
</div>
-->

## AI 数字人配置

::: note notice
创建的 AI 数字人有对应的账号 ID，但是该 ID 仅用于识别，无法进行登录。 
:::

<a id="add"></a>

### 添加 AI 数字人

AI 数字人配置的第一步是在网易云信控制台上添加并配置一个 AI 数字人，步骤如下，如果您已经完成了部分步骤，则可相应跳过：

1. 在 [网易云信控制台](https://app.yunxin.163.com/global/home) 上创建了至少一个应用。详细步骤请参考 [创建应用并获取 AppKey](https://doc.yunxin.163.com/console/concept/TIzMDE4NTA?platform=console)。
2. 为应用开通了 IM 产品。详细步骤请参考 [开通或试用服务](https://doc.yunxin.163.com/console/concept/zc3NDYzNzc?platform=console)。
3. 添加了至少一个 AI 数字人，包括 AI 聊天数字人、AI 搜索数字人、AI 翻译数字人。详细步骤请参考 [开通和添加 AI 数字人](https://doc.yunxin.163.com/console/concept/TYxMDEzNDg?platform=console)。

### 配置 AI 聊数字人

在实现层面，数字人被视为一种特殊的用户，[添加了数字人](#add) 后，您需要调用服务端 [`/im/v2/users/:{account_id}`](https://doc.yunxin.163.com/messaging2/server-apis/TA0NzYzNjk?platform=server) 接口，将数字人的账号 ID（`account_id`）传入，并在 `extension` 字段中加入 AI 聊数字人的信息扩展，如下所示，即可被 IM UIKit 识别为 AI 聊数字人。

- `aichat`：1 表示该数字人功能定位为 AI 聊数字人，可以进行聊天或者置顶到会话列表。
- `welcomeText`：用户首次进入 AI 数字人聊天页面，AI 数字人发送的欢迎消息。
- `pinDefault`：表示该 AI 数字人是否置顶到会话列表中。1 表示置顶，0 表示不置顶。默认为不置顶。
- `aiStream`：表示 AI 数字人是否为流式输出方式。1 表示流式输出，0 表示非流式输出。默认为非流式输出。
- `ai_stream_status`：表示 AI 数字人输出状态。1 表示占位，2 表示停止输出，3 表示停止输出并更新 AI 消息，4 表示输出完成，5 表示服务器终止。

    ```JSON
    {
        "aiChat": 1,
        "welcomeText": "欢迎使用 AI 聊数字人",
        "pinDefault": 1,
        "ai_stream": 1, //是否为流式输出方式
        "ai_stream_status": 4 //输出状态
    }
    ```

    <!-- AI 数字人的更多扩展配置字段，请参考 [V2NIMAIModelConfigParams](https://doc.yunxin.163.com/messaging2/client-apis/DAxNjk0Mzc?platform=client#V2NIMAIModelConfigParams)。 -->

### 配置其他 AI 数字人

当您在网易云信控制台上配置 AI 数字人时，只能配置 AI 聊数字人功能相关配置。如果是其他功能类型 AI 数字人，例如 AI 多国语言翻译<!--暂未实现、AI 划词搜索-->，则需要在应用中接入 IM UIKit 进行配置。

在登录成功之后，您需要根据网易云信控制台配置的 AI 数字人进行筛选，并确定负责 AI 翻译<!--暂未实现或者 AI 划词-->的数字人。然后在接口方法中，将网易云信控制台上配置的 AI 数字人作为入参，如下所示。更多详情，请参考 IM UIKit Demo 中 `main` 中的代码。

```
// AI搜索数字人账号
  final String AI_SEARCH_USER_ACCOUNT = "search";

  // AI翻译数字人账号
  final String AI_TRANSLATION_USER_ACCOUNT = "translation";
 ///初始化AI数字人相关配置
  void _initAIUser() {
    AIUserManager.instance.init();
    AIUserManager.instance.aiSearchUserProvider = (List<NIMAIUser> users) {
      for (var user in users) {
        if (user.accountId == AI_SEARCH_USER_ACCOUNT) {
          return user;
        }
      }
      return null;
    };
    AIUserManager.instance.aiTranslateUserProvider = (List<NIMAIUser> users) {
      for (var user in users) {
        if (user.accountId == AI_TRANSLATION_USER_ACCOUNT) {
          return user;
        }
      }
      return null;
    };
    AIUserManager.instance.aiTranslateLanguagesProvider =
        (List<NIMAIUser> users) {
      return ["英语", "日语", "韩语", "俄语", "法语", "德语"];
    };
  }

```

## AI 数字人开关

IM UIKit 提供全局功能开关，用来控制是否使用 AI 数字人相关功能。一旦您将功能开关设置为 `false`，则所有跟 AI 数字人相关功能均不可用。

建议您在初始化之前配置即可：

```
IMKitClient.enableAi = false;
```