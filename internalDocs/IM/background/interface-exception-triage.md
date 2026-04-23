# Evidence Card: 接口调用异常先分哪一类

- source file: `/Users/yxgc/.openclaw/workspace/tmp/popo-doc-export/docs/2181d94bd287461692580fc033f6d6bf__音视频2-0技术支持接口调用异常类型问题排查路径解析.md`
- why this is an evidence card instead of a playbook:
  - 原文核心价值是“分型原则”，不是可直接执行的细步骤。
  - 它告诉 agent 先判断错误发生在 SDK 本地校验、SDK 调服务端、还是纯服务端接口，不适合强行改成逐步操作 SOP。

## 这张卡回答什么问题

当客户说“接口调用异常/返回错误码/调用失败”时，先判断应该查哪一段链路，而不是立刻钻进某个系统。

## 三种异常类型

### 1) SDK 本地校验失败
特征：
- 调用 SDK 接口后，尚未真正进入服务端链路
- 常见于参数类型错误、参数不合法

应取证：
- 客户提供的接口名、错误码
- 对应端 SDK 错误码文档
- 若无日志：尽量补 SDK 日志或 QS 事件上报

常见结论：
- 接口参数错误
- 集成姿势错误
- 错误码需结合端侧文档解释

### 2) SDK 调服务端后，被服务端校验失败
特征：
- 客户从 SDK 侧看到了错误码，但根因在服务器校验或后续链路
- 常见于权限错误、join 链路中间节点失败

文中给出的典型链路：
- 客户端 JoinRoom：`getChannelInfo -> 创建房间 -> 加入房间 -> 调度 -> wss/quic -> udpconnect`
- 互动直播推流任务：`roomserver -> dispatcher -> rtmp -> cdn`

应取证：
- 错误码
- kibana 中 getChannelInfo 记录
- grafana 调度情况
- 客户端日志中的 wss / udpconnect 建连信息

### 3) 纯服务端接口校验失败
特征：
- 客户调用服务端 REST API，本身被服务端拒绝
- 常见于鉴权失败

应取证：
- requestId / appkey / url / 请求头 / 请求体
- 服务端接口日志

## Agent 分诊规则

收到“接口异常”类请求时，先按以下顺序问：
1. 出错的是 SDK 接口还是服务端接口？
2. 有没有明确错误码？
3. 是否有 room/cid/uid/时间点？
4. 有没有 SDK 日志或 QS 事件？
5. 如果是 join 或推流，当前停在链路哪一段？

## 不足与风险

原文自己也指出：
- 错误码文档分散
- 部分释义不清
- 各节点排查手段还没完全串起来

因此这张卡的用途是：
- **做分诊，不做最终定责**
- **帮 agent 决定下一步该查 SDK、服务端日志还是 join/推流链路**

## 推荐联动文档

- 入房失败：`playbooks/join-room-failure.md`
- 服务端接口：`playbooks/server-api-diagnostics.md`
- 无 SDK 日志判断是否入房：`playbooks/server-data-join-room-check.md`
- 媒体质量问题：音频/视频 playbook
