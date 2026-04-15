# Playbook: 加入音视频房间失败

- source file: `/Users/yxgc/.openclaw/workspace/tmp/popo-doc-export/docs/1333115ab34a4c22abe8741b50cfdb42__加入音视频房间失败问题排查.md`
- scope: 呼叫组件 / 信令 / token / roomserver / joinChannel 前半链路
- intent: 快速判断失败发生在“被叫没接/没申请 token/getChannelInfo 鉴权失败/请求没到音视频服务器/网络特殊环境”哪一层

## 适用场景

适用于：
- 用户已接听或已触发呼叫流程，但无法进入音视频房间
- joinChannel 报错
- token 看似正确但仍无法入房
- 日志出现 `joinChannel response: null`

不适用于：
- 已成功加入房间但媒体不可见/不可听

## 最小输入

至少要有：
- 问题时间点
- 主叫/被叫 uid
- 房间标识（若有）
- 是否使用信令或呼叫组件
- joinChannel 错误日志（若有）

最好补齐：
- token 申请记录
- roomserver 鉴权日志
- 客户端是否处于代理/防火墙/内网环境
- 设备系统时间是否明显异常

## 首先判断

1. 客户是否使用信令或组件？如果是，先从信令链路开始。
2. 被叫到底有没有接受邀请？
3. token 是否申请成功？
4. roomserver 鉴权是否通过？
5. 请求是否真正到达音视频服务器？

## 分支排查路径

### A. 信令邀请是否走通

- 查 `sid 15 cid 9`：被叫是否接受邀请。

判断：
- 没接受邀请：问题停在呼叫/信令层，不是 RTC 入房问题。
- 已接受：继续查 token。

### B. 是否成功申请 token

- 查 `sid 10003 cid 12`

判断：
- 没有 token 申请记录或申请失败：停在业务服务/鉴权前置层。
- token 申请成功：继续查 roomserver 鉴权。

### C. roomserver 鉴权是否成功

- 查 `sid -38 cid 1`
- 关键词：`cname`、`cid`、`uid`

判断：
- 没有记录：说明还没走到 roomserver，或前置参数就失败。
- 有记录但鉴权失败：优先检查 token 绑定和有效期。
- 有记录且正常：继续确认请求是否到了音视频服务器。

### D. 是否到达音视频服务器

- 如果 roomserver 有记录，继续找音视频同学确认后续请求是否到达服务器。

判断：
- roomserver 正常但后续服务器无记录：偏后端链路/网络/转发问题。

### E. 特殊场景：`response is null`

日志示例：
- `joinChannel response: null`
- `joinChannel request error response is null`

文档给出的高频原因：
- 网络异常
- 代理环境
- 防火墙 / 内网限制
- 手机系统时间与真实时间差距过大，HTTPS 校验失败

### F. token 传对了但加入仍失败

逐项检查：
1. 是否已过期
2. 是否绑定 `channelName`
3. 是否绑定错 `uid`
4. 是否是不允许多次使用的一次性 token

## 证据不足时必须补充

必须追补：
- 被叫是否真实接受邀请
- token 申请结果
- roomserver 鉴权记录
- joinChannel 原始错误日志
- 客户网络环境说明（代理/内网/防火墙）
- 系统时间是否异常

## 不要轻易下的结论

- 不要一看到 join 失败就怪 token；文档明确列出网络/代理/防火墙/系统时间等非 token 原因。
- 不要只因“申请过 token”就断言 token 一定可用；还要核查过期、channelName、uid、一次性使用限制。
- 不要在缺少 `sid 15` 证据时假设被叫已经真正接受邀请。

## 升级条件

- 已有 `sid -38 cid 1` 正常记录，但后续请求是否到达音视频服务器仍不清楚
- token、时间、网络环境都排除后仍无法入房
- 同一集成逻辑下批量用户出现 join 失败

## 产出模板

```md
### 入房失败排查结论
- 时间点：
- 主叫/被叫：
- 是否使用信令/组件：

### 链路核查
- 信令接受邀请（sid 15 cid 9）：
- token申请（sid 10003 cid 12）：
- roomserver鉴权（sid -38 cid 1）：
- 后续是否到达音视频服务器：

### 当前判断
- 失败停留阶段：信令 / token / roomserver / 后端链路 / 网络环境
- 关键依据：

### 建议动作
- 客户侧：
- 内部升级方向：IM/信令 / RTC服务端 / 网络环境排查
```
