AI 数字人接口类。

## `AIRepo` 类

`AIRepo` 类提供 AI 数字人获取和变更监听方法等。

## 方法列表

| 接口 | 接口原型 |接口描述|
|---|---|---|
| `addAIListener` | `addAIListener(listener: V2NIMAIListener)` | 添加 AI 监听。 |
| `getAIUserList`| `getAIUserList(callback: FetchCallback<List<V2NIMAIUser>>)` | 获取 AI 用户列表。 |
| `proxyAIModelCall` | `proxyAIModelCall(params: V2NIMProxyAIModelCallParams, callback: FetchCallback<Void>)` | AI 数字人请求代理接口。 |
| `removeAIListener` |  `removeAIListener(listener: V2NIMAIListener)` | 移除 AI 监听。 |