网易云信即时通讯 SDK（NetEase IM SDK，以下简称 NIM SDK）提供 AI 数字人。数字人既可以是虚拟的 AI 对话伙伴、高效的协同工作助手、也可定制贴合业务所需更高安全性的本地大模型。

本文介绍 AI 数字人相关的 API。更多详情，请参考《集成开发》[AI 数字人](https://doc.yunxin.163.com/messaging2/guide/zQ1MDEwNzA?platform=client)。

## 支持平台

本文内容适用的开发平台或框架如下表所示：

Android | iOS | macOS/Windows | Web/uni-app/小程序 | Node.js/Electron | HarmonyOS |
:----: | :----: | :----: | :----: | :----: | :----: | 
✔️️ | ✔️️ | ✔️️ | ✔️️ | ✔️️ | ✔️️ |

## API 概览

### AI 数字人监听

:::::: div linked-codes
::: code Android/iOS/macOS/Windows
API | 说明 | 起始版本
---- | ---- | ----
[addAIListener](#addAIListener) | 注册 AI 数字人相关监听器 | v10.3.0 |
[removeAIListener](#removeAIListener) | 移除 AI 数字人相关监听器 | v10.3.0 |
:::
::: code Web/uni-app/小程序/Node.js/Electron/HarmonyOS
API | 说明 | 起始版本
---- | ---- | ----
[on("EventName")](#on) | 注册 AI 数字人相关监听 | v10.3.0（对应 HarmonyOS v10.6.0）
[off("EventName")](#off) | 取消注册 AI 数字人相关监听 | v10.3.0（对应 HarmonyOS v10.6.0）
:::
::::::

### AI 数字人操作

API | 说明 | 起始版本
---- | ---- | ----
[`getAIUserList`](#getAIUserList) | 根据用户账号 ID 列表获取 AI 数字人 | v10.3.0（对应 HarmonyOS v10.6.0）
[`proxyAIModelCall`](#proxyAIModelCall) | AI 数字人向 LLM 发起查询请求 | v10.3.0（对应 HarmonyOS v10.6.0）
[`sendMessage`](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#sendMessage) | AI 数字人发送消息 | v10.2.0（对应 HarmonyOS v10.6.0）
[`stopAIModelStreamCall`](#stopAIModelStreamCall) | 停止 AI 流式输出请求 | v10.8.30

## 接口类

`V2NIMAIService` 类提供 AI 数字人相关接口，包括查询数字人、LLM 模型请求、添加 AI 数字人监听、移除 AI 数字人监听。

## <span id="addAIListener">addAIListener</span>

**接口描述**

注册添加 AI 数字人的监听器。注册成功后，当聊天会话中添加了 AI 数字人后，SDK 会返回对应的回调。

::: note note
- 建议在初始化后调用该接口。

- 全局只需注册一次。
:::

**参数说明**

:::::: div linked-codes
::: code Android
```Java
/**
 * 添加 AI 监听
 * @param listener
 */
void addAIListener(V2NIMAIListener listener);
```
:::
::: code iOS
```Objective-C
//AI 消息的响应的回调
- (void)onProxyAIModelCall:(V2NIMAIModelCallResult *)data;
//AI 透传接口的流式响应的回调
- (void)onProxyAIModelStreamCall:(V2NIMAIModelStreamCallResult *)data;
/**
 * 添加数字人监听器
 *
 * @param listener 消息监听回调
 */
- (void)addAIListener:(id<V2NIMAIListener>)listener;
```
:::
::: code macOS/Windows
```C++
// AI 回调
struct V2NIMAIListener {
    nstd::function<void(const V2NIMAIModelCallResult& response)> onProxyAIModelCall;
    nstd::function<void(const V2NIMAIModelStreamCallResult& response)> onProxyAIModelStreamCall;
};
// 添加数字人监听器
virtual void addAIListener(V2NIMAIListener listener) = 0;
```
:::
::::::

| 参数名称 | 类型 | 是否必填 | 说明 |
| ---- | ---- | ---- | ---- |
| `listener` | [`V2NIMAIListener`](https://doc.yunxin.163.com/messaging2/client-apis/DAxNjk0Mzc?platform=client#V2NIMAIListener) | 是 | AI 数字人相关监听器。 |

**示例代码**

:::::: div linked-codes
::: code Android
```Java
V2NIMAIListener listener = new V2NIMAIListener() {
    /**
     * AI 消息的响应的回调
     *
     * @param result 本次响应的结构体
     */
    @Override
    public void onProxyAIModelCall(V2NIMAIModelCallResult result) {
        // do something
    }
    /**
     * AI 透传接口的流式响应的回调
     *
     * @param result 本次响应的结构体
     */
    @Override
    public void onProxyAIModelStreamCall(V2NIMAIModelStreamCallResult result) {
        // do something
    }
};

NIMClient.getService(V2NIMAIService.class).addAIListener(listener);
```
:::
::: code iOS
```Objective-C
[NIMSDK.sharedSDK.v2AIService addAIListener:self];
```
:::
::: code macOS/Windows
```C++
auto& aiService = v2::V2NIMClient::get().getAIService();
aiService.addAIListener(aiListener);
```
:::
::::::

**返回参数**

无。

## <span id="removeAIListener">removeAIListener</span>

**接口描述**

移除 AI 数字人监听器。

**参数说明**

:::::: div linked-codes
::: code Android
```Java
/**
 * 移除 AI 监听
 * @param listener
 */
void removeAIListener(V2NIMAIListener listener);
```
:::
::: code iOS
```Objective-C
/**
 * 删除数字人监听器
 *
 * @param listener 消息监听回调
 */
- (void)removeAIListener:(id<V2NIMAIListener>)listener;
```
:::
::: code macOS/Windows
```C++
virtual void removeAIListener(V2NIMAIListener listener) = 0;
```
:::
::::::

| 参数名称 | 类型 | 是否必填 | 说明 |
| ---- | ---- | ---- | ---- |
| `listener` | [`V2NIMAIListener`](https://doc.yunxin.163.com/messaging2/client-apis/DAxNjk0Mzc?platform=client#V2NIMAIListener) | 是 | AI 数字人相关监听器。 |

**示例代码**

:::::: div linked-codes
::: code Android
```Java
NIMClient.getService(V2NIMAIService.class).removeAIListener(listener);
```
:::
::: code iOS
```Objective-C
[NIMSDK.sharedSDK.v2AIService removeAIListener:self];
```
:::
::: code macOS/Windows
```C++
auto& aiService = v2::V2NIMClient::get().getAIService();
aiService.removeAIListener(aiListener);
```
:::
::::::

**返回参数**

无。

## <span id="on">on("EventName")</span>

**接口描述**

注册添加 AI 数字人的监听器。注册成功后，当聊天会话中添加了 AI 数字人后，SDK 会返回对应的回调。

::: note note
- 建议在初始化后调用该接口。

- 全局只需注册一次。

- 该方法为同步。
:::

**参数说明**

:::::: div linked-codes
::: code Web/uni-app/小程序
```TypeScript
/**
 * 继承自 eventEmitter3 的监听事件方法
 */
interface V2NIMAIService extends EventEmitter3<V2NIMAIListener>
```
| 参数名称 | 类型 | 是否必填 | 说明 |
| ---- | ---- | ---- | ---- |
| `eventName` | [`V2NIMAIListener`](https://doc.yunxin.163.com/messaging2/client-apis/DAxNjk0Mzc?platform=client#V2NIMAIListener)  | 是 | 回调事件 <li>`onProxyAIModelCall`：AI 透传接口的响应的回调。<li>`onProxyAIModelStreamCall`：AI 透传接口的流式响应的回调。 | 
:::
::: code Node.js/Electron
```TypeScript
```TypeScript
/**
 * 继承自 eventEmitter3 的监听事件方法
 */
interface V2NIMAIService extends EventEmitter3<V2NIMAIListener>
```
| 参数名称 | 类型 | 是否必填 | 说明 |
| ---- | ---- | ---- | ---- |
| `eventName` | [`V2NIMAIListener`](https://doc.yunxin.163.com/messaging2/client-apis/DAxNjk0Mzc?platform=client#V2NIMAIListener)  | 是 | 回调事件 <li>`proxyAIModelCall`：AI 透传接口的响应的回调。<li>`proxyAIModelStreamCall`：AI 透传接口的流式响应的回调。 | 
:::
::: code HarmonyOS
```TypeScript
/**
 * 继承自 eventEmitter3 的监听事件方法
 */
interface V2NIMAIService extends EventEmitter3<V2NIMAIListener>
```
| 参数名称 | 类型 | 是否必填 | 说明 |
| ---- | ---- | ---- | ---- |
| `eventName` | [`V2NIMAIListener`](https://doc.yunxin.163.com/messaging2/client-apis/DAxNjk0Mzc?platform=client#V2NIMAIListener)  | 是 | 回调事件 <li>`onProxyAIModelCall`：AI 透传接口的响应的回调。<li>`onProxyAIModelStreamCall`：AI 透传接口的流式响应的回调。 | 
:::
::::::

**示例代码**

:::::: div linked-codes
::: code Web/uni-app/小程序
```TypeScript
nim.V2NIMAIService.on('onProxyAIModelCall', function() {
    // ... do something
})
nim.V2NIMAIService.on('onProxyAIModelStreamCall', function() {
    // ... do something
})
```
:::
::: code Node.js/Electron
```TypeScript
v2.aIListener.on("proxyAIModelCall", function (userStatusList: Array<V2NIMUserStatus>) {})
v2.aIListener.on("proxyAIModelStreamCall", function (aiStreamStatus: Array<V2NIMAIModelStreamCallStatus>) {})
```
:::
::: code HarmonyOS
```TypeScript
nim.aiService.on('onProxyAIModelCall', function() {
    // ... do something
})
nim.aiService.on('onProxyAIModelStreamCall', function() {
    // ... do something
})
```
:::
::::::

**返回参数**

无。

## <span id="off">off("EventName")</span>

**接口描述**

移除 AI 数字人监听器。

**参数说明**

:::::: div linked-codes
::: code Web/uni-app/小程序
```TypeScript
/**
 * 继承自 eventEmitter3 的监听事件方法
 */
interface V2NIMAIService extends EventEmitter3<V2NIMAIListener>
```
| 参数名称 | 类型 | 是否必填 | 说明 |
| ---- | ---- | ---- | ---- |
| `eventName` | [`V2NIMAIListener`](https://doc.yunxin.163.com/messaging2/client-apis/DAxNjk0Mzc?platform=client#V2NIMAIListener)  | 是 | 回调事件 <li>`onProxyAIModelCall`：AI 透传接口的响应的回调。<li>`onProxyAIModelStreamCall`：AI 透传接口的流式响应的回调。 | 
:::
::: code Node.js/Electron
```TypeScript
/**
 * 继承自 eventEmitter3 的监听事件方法
 */
interface V2NIMAIService extends EventEmitter3<V2NIMAIListener>
```
| 参数名称 | 类型 | 是否必填 | 说明 |
| ---- | ---- | ---- | ---- |
| `eventName` | [`V2NIMAIListener`](https://doc.yunxin.163.com/messaging2/client-apis/DAxNjk0Mzc?platform=client#V2NIMAIListener)  | 是 | 回调事件 <li>`proxyAIModelCall`：AI 透传接口的响应的回调。<li>`proxyAIModelStreamCall`：AI 透传接口的流式响应的回调。 | 
:::
::: code HarmonyOS
```TypeScript
/**
 * 继承自 eventEmitter3 的监听事件方法
 */
interface V2NIMAIService extends EventEmitter3<V2NIMAIListener>
```
| 参数名称 | 类型 | 是否必填 | 说明 |
| ---- | ---- | ---- | ---- |
| `eventName` | [`V2NIMAIListener`](https://doc.yunxin.163.com/messaging2/client-apis/DAxNjk0Mzc?platform=client#V2NIMAIListener)  | 是 | 回调事件 <li>`onProxyAIModelCall`：AI 透传接口的响应的回调。<li>`onProxyAIModelStreamCall`：AI 透传接口的流式响应的回调。 | 
:::
::::::

**示例代码**

:::::: div linked-codes
::: code Web/uni-app/小程序
```TypeScript
nim.V2NIMAIService.off('onProxyAIModelCall', function() {
    // ... do something
})
nim.V2NIMAIService.off('onProxyAIModelStreamCall', function() {
    // ... do something
})
```
:::
::: code Node.js/Electron
```TypeScript
v2.aIListener.off("proxyAIModelCall", function () {
    // ... do something
})
v2.aIListener.off("proxyAIModelStreamCall", function () {
    // ... do something
})
```
:::
::: code HarmonyOS
```TypeScript
nim.aiService.off('onProxyAIModelCall')
nim.aiService.off('onProxyAIModelStreamCall')
```
:::
::::::

**返回参数**

无。

## <span id="getAIUserList">getAIUserList</span>

**接口描述**

批量查询 AI 数字人列表。返回全量的开发者账号下的相关的数字人用户。

<!-- 该接口根据用户账号 ID 先从客户端本地获取 AI 数字人数据，若本地数据缺失或不足，再查询服务端中的 AI 数字人数据。-->

<!-- ::: note note
- 单次最多查询 150 个 AI 数字人。
- 若传入的账号 ID 都不存在，则调用接口失败。若部分账号 ID 存在，则调用接口成功。调用结果只返回账号 ID 存在的 AI 数字人，错误的账号 ID 不返回。
::: -->

**参数说明**

:::::: div linked-codes
::: code Android
```Java
/**
 * 数字人拉取接口
 * @param success 成功回调
 * @param failure 失败回调
 */
void getAIUserList(V2NIMSuccessCallback<List<V2NIMAIUser>> success, V2NIMFailureCallback failure);
```
:::
::: code iOS
```Objective-C
/**
 * 数字人拉取接口
 * 返回全量的本 Appkey 相关的数字人用户
 *
 * @param success 请求成功回调
 * @param failure 请求失败回调
 */
- (void)getAIUserList:(nullable V2NIMGetAlUserListSuccess)success
              failure:(nullable V2NIMFailureCallback)failure;
```
:::
::: code macOS/Windows
```C++
    /// @brief 获取 AI 数字人列表
    /// @param success 成功回调
    /// @param failure 失败回调
    /// @return void
    /// @par 示例代码
    /// @code
    /// aiService.getAIUserList(
    ///     [](nstd::vector<nstd::shared_ptr<V2NIMAIUser>> result) {
    ///         // get AI users success
    ///     },
    ///     [](V2NIMError error) {
    ///         // get AI users failed, handle error
    ///     });
    /// @endcode
    virtual void getAIUserList(V2NIMSuccessCallback<nstd::vector<nstd::shared_ptr<V2NIMAIUser>>> success, V2NIMFailureCallback failure) = 0;
```
:::
::: code Web/uni-app/小程序
```TypeScript
/**
 * ESM 模式时，需要动态引入 V2NIMAIService 后使用:
 * NIM.registerService(V2NIMAIService, 'V2NIMAIService')
 *
 * 数字人拉取接口
 *
 * 注: 返回全量的本 Appkey 相关的数字人用户
 *
 * @returns 数字人用户列表
 */
getAIUserList(): Promise<V2NIMAIUser[]>
```
:::
::: code Node.js/Electron
```TypeScript
/**
 * ESM 模式时，需要动态引入 V2NIMAIService 后使用:
 * NIM.registerService(V2NIMAIService, 'V2NIMAIService')
 *
 * 数字人拉取接口
 *
 * 注: 返回全量的本 Appkey 相关的数字人用户
 *
 * @returns 数字人用户列表
 */
getAIUserList(): Promise<V2NIMAIUser[]>
```
:::
::: code HarmonyOS
```TypeScript
  /**
 * 数字人拉取接口
 *
 * 注: 返回全量的本 Appkey 相关的数字人用户
 *
 * @returns 数字人用户列表
 */
getAIUserList(): Promise<V2NIMAIUser[]>
```
:::
::::::

| 参数名称 | 类型 | 是否必填 | 说明 |
| ---- | ---- | ---- | ---- |
| `success` | [`V2NIMSuccessCallback`](https://doc.yunxin.163.com/messaging2/client-apis/DAxNjk0Mzc?platform=client#V2NIMSuccessCallback) | 是 | 获取 AI 数字人成功回调，返回 [`V2NIMAIUser`](https://doc.yunxin.163.com/messaging2/client-apis/DAxNjk0Mzc?platform=client#V2NIMAIUser) AI 数字人列表。 |
| `failure` | [`V2NIMFailureCallback`](https://doc.yunxin.163.com/messaging2/client-apis/DAxNjk0Mzc?platform=client#V2NIMFailureCallback) | 是 | 获取 AI 数字人失败回调，返回 [错误码](https://doc.yunxin.163.com/messaging2/client-apis/DUxNjU3MzU?platform=client#AI)。 |

**示例代码**

:::::: div linked-codes
::: code Android
```Java
NIMClient.getService(V2NIMAIService.class).getAIUserList(new V2NIMSuccessCallback<List<V2NIMAIUser>>() {
    @Override
    public void onSuccess(List<V2NIMAIUser> users) {
        // success
    }
}, new V2NIMFailureCallback() {
    @Override
    public void onFailure(V2NIMError error) {
        // failure
    }
});
```
:::
::: code iOS
```Objective-C
[NIMSDK.sharedSDK.v2AIService getAIUserList:^(NSArray<V2NIMAIUser *> * _Nullable result) {
           // 成功回调
        } failure:^(V2NIMError * _Nonnull error) {
            // 失败回调
        }];
```
:::
::: code macOS/Windows
```C++
auto& AIService = v2::V2NIMClient::get().getAIService();
AIService.getAIUserList(
    [=](nstd::vector<nstd::shared_ptr<V2NIMAIUser>> result) {
        // 成功回调                                      auto detailString = xpack::json::encode(result);
    },
    [=](v2::V2NIMError error) {
        // 失败回调
    });
```
:::
::: code Web/uni-app/小程序
```TypeScript
const aiUsers = await nim.V2NIMAIService.getAIUserList()
```
:::
::: code Node.js/Electron
```TypeScript
const aiUsers = await v2.aIService.getAIUserList()
```
:::
::: code HarmonyOS
```TypeScript
const aiUsers = await nim.aiService.getAIUserList()
```
:::
::::::

**返回参数**

:::::: div linked-codes
::: code Android/iOS/macOS/Windows
无返回值。
:::
::: code Web/uni-app/小程序/Node.js/Electron/HarmonyOS
Promise\<[`V2NIMAIUser`](https://doc.yunxin.163.com/messaging2/client-apis/DAxNjk0Mzc?platform=client#V2NIMAIUser)[]>：查询到的 AI 数字人列表。
:::
::::::

**相关回调**

:::::: div linked-codes
::: code Android/iOS/macOS/Windows
- 请求成功，返回 `V2NIMSuccessCallback` 回调，包含 [`V2NIMAIUser`](https://doc.yunxin.163.com/messaging2/client-apis/DAxNjk0Mzc?platform=client#V2NIMAIUser) AI 数字人列表。
- 请求失败，返回 `V2NIMFailureCallback` 回调，包含 AI 数字人相关错误码。
:::
::: code Web/uni-app/小程序/Node.js/Electron/HarmonyOS
无。
:::
::::::

## <span id="proxyAIModelCall">proxyAIModelCall</span>

**接口描述**

向 LLM（Large Language Models）发起模型调用请求。数字人发送消息调用 [`sendMessage`](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#sendMessage)。

```JSON
{ "msg": "xxxx", "type": 0 }
```

::: note note
- 发送前请确保 AI 数字人已被添加。详情请参考 [开通和添加 AI 数字人](https://doc.yunxin.163.com/console/concept/TYxMDEzNDg?platform=console)。
- 本接口为异步接口。
:::

**参数说明**

:::::: div linked-codes
::: code Android
```Java
/**
 * AI 数字人请求代理接口
 * @param params 请求参数
 * @param success 成功回调
 * @param failure 失败回调
 */
void proxyAIModelCall(V2NIMProxyAIModelCallParams params, V2NIMSuccessCallback<Void> success, V2NIMFailureCallback failure);
```
:::
::: code iOS
```Objective-C
/**
 * AI 数字人请求代理接口
 *
 * @param params   接口入参
 * @param success 请求成功回调
 * @param failure 请求失败回调
 */

- (void)proxyAIModelCall:(V2NIMProxyAIModelCallParams *)params
                 success:(nullable V2NIMSuccessCallback)success
                 failure:(nullable V2NIMFailureCallback)failure;
```
:::
::: code macOS/Windows
```C++
    /// @brief AI 数字人请求代理接口
    /// @param params 接口入参
    /// @param success 成功回调
    /// @param failure 失败回调
    /// @return void
    /// @par 示例代码
    /// @code
    /// V2NIMProxyAIModelCallParams params;
    /// aiService.proxyAIModelCall(
    ///     params,
    ///     []() {
    ///         // update success
    ///     },
    ///     [](V2NIMError error) {
    ///         // update failed, handle error
    ///     });
    /// @endcode
    virtual void proxyAIModelCall(V2NIMProxyAIModelCallParams params, V2NIMSuccessCallback<void> success, V2NIMFailureCallback failure) = 0;
```
:::
::: code Web/uni-app/小程序
```TypeScript
/**
 * ESM 模式时，需要动态引入 V2NIMAIService 后使用:
 * NIM.registerService(V2NIMAIService, 'V2NIMAIService')
 *
 * AI 数字人请求代理接口
 *
 * @param params 接口入参
 */
proxyAIModelCall(params: V2NIMProxyAIModelCallParams): Promise<void>
```
:::
::: code Node.js/Electron
```TypeScript
/**
 * ESM 模式时，需要动态引入 V2NIMAIService 后使用:
 * NIM.registerService(V2NIMAIService, 'V2NIMAIService')
 *
 * AI 数字人请求代理接口
 *
 * @param params 接口入参
 */
proxyAIModelCall(params): Promise<void>
```
:::
::: code HarmonyOS
```TypeScript
proxyAIModelCall(params: V2NIMProxyAIModelCallParams): Promise<void>
```
:::
::::::

| 参数名称 | 类型 | 是否必填 | 说明 |
| ---- | ---- | ---- | ---- |
| `params` | [`V2NIMProxyAIModelCallParams`](https://doc.yunxin.163.com/messaging2/client-apis/DAxNjk0Mzc?platform=client#V2NIMProxyAIModelCallParams) | 是 | AI 数字人更新参数，包括输出方式、用户昵称、头像、签名、邮箱、性别、生日、手机号以及扩展信息。 |
| `success` | [`V2NIMSuccessCallback`](https://doc.yunxin.163.com/messaging2/client-apis/DAxNjk0Mzc?platform=client#V2NIMSuccessCallback) | 是 | 更新 AI 数字人成功回调。 |
| `failure` | [`V2NIMFailureCallback`](https://doc.yunxin.163.com/messaging2/client-apis/DAxNjk0Mzc?platform=client#V2NIMFailureCallback) | 是 | 更新 AI 数字人失败回调，返回 [错误码](https://doc.yunxin.163.com/messaging2/client-apis/DUxNjU3MzU?platform=client#AI)。 |

**示例代码**

:::::: div linked-codes
::: code Android
```Java
V2NIMProxyAIModelCallParams params = new V2NIMProxyAIModelCallParams.Builder()
    .accountId("accountId")
    .requestId("requestId")
    .content(new V2NIMAIModelCallContent("msg",0))
    .build();
NIMClient.getService(V2NIMAIService.class).proxyAIModelCall(params, new V2NIMSuccessCallback<Void>() {
    @Override
    public void onSuccess(Void unused) {
        // success
    }
}, new V2NIMFailureCallback() {
    @Override
    public void onFailure(V2NIMError error) {
        // failure
    }
});
```
:::
::: code iOS
```Objective-C
V2NIMProxyAIModelCallParams *params = [[V2NIMProxyAIModelCallParams alloc] init];
    params.accountId = @"accid";
    params.requestId = @"requestId"
    //...
    [NIMSDK.sharedSDK.v2AIService proxyAIModelCall:params success:^{
        // 成功回调
    } failure:^(V2NIMError * _Nonnull error) {
        // 失败回调
    }];
```
:::
::: code macOS/Windows
```C++
auto& aiService = v2::V2NIMClient::get().getAIService();
V2NIMProxyAIModelCallParams proxyAIModelCallParams;
aiService.proxyAIModelCall(
    proxyAIModelCallParams,
    [=]() {
        // 成功回调
    },
    [=](v2::V2NIMError error) {
        // 失败回调
    });
```
:::
::: code Web/uni-app/小程序
```TypeScript
await nim.V2NIMAIService.proxyAIModelCall({
  "accountId": "YOUR_AI_ACCOUNT_ID",
  "requestId": "YOUR_REQUEST_ID",
  "content": {
    "msg": "YOUR_CONTENT_MSG",
    "type": 0
  }
})
```
:::
::: code Node.js/Electron
```TypeScript
await v2.aIService.proxyAIModelCall({
  "accountId": "YOUR_AI_ACCOUNT_ID",
  "requestId": "YOUR_REQUEST_ID",
  "content": {
    "msg": "YOUR_CONTENT_MSG",
    "type": 0
  }
})
```
:::
::: code HarmonyOS
```TypeScript
await nim.aiService.proxyAIModelCall({
  "accountId": "YOUR_AI_ACCOUNT_ID",
  "requestId": "YOUR_REQUEST_ID",
  "content": {
    "msg": "YOUR_CONTENT_MSG",
    "type": 0
  }
})
```
:::
::::::

**返回参数**

:::::: div linked-codes
::: code Android/iOS/macOS/Windows
无返回值。
:::
::: code Web/uni-app/小程序/Node.js/Electron/HarmonyOS
Promise\<void>
:::
::::::

**相关回调**

:::::: div linked-codes
::: code Android/iOS/macOS/Windows
- 请求成功，返回 `V2NIMSuccessCallback` 回调，包含 [`V2NIMAIListener`](https://doc.yunxin.163.com/messaging2/client-apis/DAxNjk0Mzc?platform=client#V2NIMAIListener) AI 数字人列表。
- 请求失败，返回 `V2NIMFailureCallback` 回调，包含 AI 数字人相关错误码。
:::
::: code Web/uni-app/小程序/HarmonyOS
调用成功，返回 [`onProxyAIModelCall`](https://doc.yunxin.163.com/messaging2/client-apis/DAxNjk0Mzc?platform=client#V2NIMAIListener) 回调或 [`onProxyAIModelStreamCall`](https://doc.yunxin.163.com/messaging2/client-apis/DAxNjk0Mzc?platform=client#V2NIMAIListener) 回调。
:::
::: code Node.js/Electron
调用成功，返回 [`proxyAIModelCall`](https://doc.yunxin.163.com/messaging2/client-apis/DAxNjk0Mzc?platform=client#V2NIMAIListener) 回调或 [`proxyAIModelStreamCall`](https://doc.yunxin.163.com/messaging2/client-apis/DAxNjk0Mzc?platform=client#V2NIMAIListener) 回调。
::::::

## <span id="stopAIModelStreamCall">stopAIModelStreamCall</span>

**接口描述**

停止 AI 流式输出请求。

::: note note
本接口为异步接口。
:::

**参数说明**

:::::: div linked-codes
::: code Android
```Java
/**
* 停止流式输出接口
* @param params 请求参数
* @param success 成功回调
* @param failure 失败回调
*/
void stopAIModelStreamCall(V2NIMAIModelStreamCallStopParams params, V2NIMSuccessCallback<Void> success, V2NIMFailureCallback failure);
:::
::: code iOS
```Objective-C
/**
 * 停止流式输出
 *
 *  @param params   接口入参
 *  @param completion  完成后的回调
 */
- (void)stopAIModelStreamCall:(V2NIMAIModelStreamCallStopParams *)params
                            success:(nullable V2NIMSuccessCallback)success
                            failure:(nullable V2NIMFailureCallback)failure;
```
:::
::: code macOS/Windows
```C++
virtual void stopAIModelStreamCall(const V2NIMAIModelStreamCallStopParams& params,
    V2NIMSuccessCallback<void> success,
    V2NIMFailureCallback failure) = 0;
```
:::
::: code Web/uni-app/小程序
```TypeScript
stopAIModelStreamCall(params: V2NIMAIModelStreamCallStopParams): Promise<void>
```
:::
::: code Node.js/Electron
```TypeScript
stopAIModelStreamCall(params): Promise<void>
```
:::
::: code HarmonyOS
```TypeScript
stopAIModelStreamCall(params): Promise<void>
```
:::
::::::

| 参数名称 | 类型 | 是否必填 | 说明 |
| ---- | ---- | ---- | ---- |
| `params` | [`V2NIMAIModelStreamCallStopParams`](https://doc.yunxin.163.com/messaging2/client-apis/DAxNjk0Mzc?platform=client#V2NIMAIModelStreamCallStopParams) | 是 | 停止流式输出配置参数，包括停止输出的 AI 数字人账号 ID。 |
| `success` | [`V2NIMSuccessCallback`](https://doc.yunxin.163.com/messaging2/client-apis/DAxNjk0Mzc?platform=client#V2NIMSuccessCallback) | 是 | 停止流式输出成功回调。 |
| `failure` | [`V2NIMFailureCallback`](https://doc.yunxin.163.com/messaging2/client-apis/DAxNjk0Mzc?platform=client#V2NIMFailureCallback) | 是 | 停止流式输出失败回调，返回 [错误码](https://doc.yunxin.163.com/messaging2/client-apis/DUxNjU3MzU?platform=client#AI)。 |

**示例代码**

:::::: div linked-codes
::: code Android
```Java
V2NIMAIModelStreamCallStopParams params = new V2NIMAIModelStreamCallStopParams();
// AI 账号 ID
params.setAccountId(aiAccountId);
// 请求ID，和 proxyAIModelCall 中一致
params.setRequestId(requestId);

NIMSDK.sharedSDK().getV2AIService().stopAIModelStreamCall(params,
    new RequestCallback<Void>() {
        @Override
        public void onSuccess(Void result) {
            // Stop AI success
        }
        
        @Override
        public void onFailed(int code) {
            // Stop AI failed
        }
        
        @Override
        public void onException(Throwable exception) {
            // Exception occurred
        }
    });
```
:::
::: code iOS
```Objective-C
V2NIMAIModelStreamCallStopParams *params = [[V2NIMAIModelStreamCallStopParams alloc] init];
// AI 账号
params.accountId = aiAccountId;
// 请求 ID，和 proxyAIModelCall:completion:中一致
params.requestId = requestId;
[[NIMSDK sharedSDK].v2AIService stopAIModelStreamCall:params
                                            success:^{
   // Stop AI success
} failure:^(V2NIMError * _Nonnull error) {
   // Stop AI failed
}];
```
:::
::: code macOS/Windows
```C++
V2NIMAIModelStreamCallStopParams params;
params.accountId = "account_id";
params.requestId = "request_id";
aiService.stopAIModelStreamCall(
    params,
    []() {
        // stop AI model stream call success
    },
    [](V2NIMError error) {
        // stop AI model stream call failed, handle error
    });
```
:::
::: code Web/uni-app/小程序
```TypeScript
await nim.V2NIMAIService.stopAIModelStreamCall({
  accountId: 'AI user account ID',
  requestId: 'Request ID'
})
```
:::
::: code Node.js/Electron
```TypeScript
const message = v2.aiService.stopAIModelStreamCall({
   accountId: 'AI user account ID',
   requestId: 'Request ID'
})
```
:::
::: code HarmonyOS
```TypeScript
const params: V2NIMAIModelStreamCallStopParams = {
  accountId: this.stopAccountId,
  requestId: this.stopRequestId
}
const aiService = nim.aiService! // Demo启用 ai 模块，aiService不为空
const res = await aiService.stopAIModelStreamCall(params)
```
:::
::::::

**返回参数**

:::::: div linked-codes
::: code Android/iOS/macOS/Windows
无返回值。
:::
::: code Web/uni-app/小程序/Node.js/Electron/HarmonyOS
Promise\<void>
:::
::::::

**相关回调**

:::::: div linked-codes
::: code Android/iOS/macOS/Windows
- 请求成功，返回 `V2NIMSuccessCallback` 回调。
- 请求失败，返回 `V2NIMFailureCallback` 回调，包含 AI 数字人相关错误码。
:::
::: code Web/uni-app/小程序/Node.js/Electron/HarmonyOS
无。
:::
::::::