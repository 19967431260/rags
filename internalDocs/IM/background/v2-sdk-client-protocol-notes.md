# V2 SDK Client Protocol Notes

Use this file when a case explicitly mentions **V2 / V10 client protocol numbers** such as `27-1`, `30-6`, `31-23`, `34-1`, `36-2`.

This is a distilled local note based on the user-provided `v2-sdk协议` document plus the existing troubleshooting references. It is not a full replacement for the original source, but it covers the protocol families that repeatedly appear in Yunxin troubleshooting.

## Version normalization
- **IM V1 = client V9**
- **IM V2 = client V10**
- Read raw `27-* / 30-* / 31-* / 34-* / 36-*` as **V10 / V2 client protocol numbers**, not as v1-style numbers.

## Family mapping cheat sheet
- `5-* -> 27-*`：登录后同步 / 游标上传 / sync request
- `7-* -> 30-*`：单聊发送、单聊历史、已读、撤回、会话类操作
- `8-* -> 31-*`：群消息、群历史、群属性、群已读
- `3-* -> 34-*`：用户态 / push token / 前后台 / 免打扰等
- `13-* -> 36-*`：聊天室进入、发言、队列、标签相关

## High-value protocols

### 27-* — Sync / login-time cursor upload
These are the V2/V10 equivalents of the classic `5-*` sync family.

- `27-1 / 27-2 / 27-3 / 27-10` correspond to `5-1 / 5-2 / 5-3 / 24-19`
- In troubleshooting, `27-1` is the most important anchor for:
  - first login after reinstall / local reset
  - whether roaming/sync timetags are zero
  - whether the client is asking the server to rehydrate history from scratch
- Useful semantics:
  - if roaming / sync-related timetags are `0`, this strongly suggests reinstall, local DB reset, or equivalent clean-state sync
  - `414` usually means parameter issue
  - `399` often means wrong unit / need fresh LBS link
  - `398` often appears during unit migration and can be retried
  - `463` is callback deny

### 30-* — P2P domain
These are the V2/V10 equivalents of classic `7-*`.

#### 30-1 — send p2p message
Equivalent of `7-1`.
High-value cases from the v2-sdk note:
- `414` parameter error
- `102421` sender muted
- `107410` app muted
- `102404` peer accid not found
- `104404` peer is not friend
- `102426` sender blacklisted by peer
- anti-spam may still return transport `200`; check `TalkMsgTag` extra fields and anti-spam tags
- callback deny may appear as `463`; `200 + deny` may require looking at extra tag `54`

#### 30-6 — get p2p history
Equivalent of `7-6`.
Use this when the case is explicitly about **single-chat history query**.
High-value cases from the v2-sdk note:
- `414` parameter error

Important guardrail:
- Do not confuse `30-6` (single-chat history) with `31-23` (group history).

#### 30-11 — p2p read receipt
Equivalent of `7-11`.
- `414` parameter error
- `102404` peer accid not found
- some environments may also show “feature not enabled” behavior

#### 30-13 — recall message
Equivalent of `7-13`.
High-value cases:
- `414` parameter error
- `107314` recall timeout
- `102404` peer accid not found
- `107429` cannot recall a message sent to self
- `107404` message not found
- `107315` not sender / not group admin
- `463` callback deny

### 31-* — Team / group domain
These are the V2/V10 equivalents of classic `8-*`.

#### 31-2 — send team message
Equivalent of `8-2`.
High-value cases from the v2-sdk note:
- `414` parameter error
- `102421` sender muted
- `107410` app muted
- `109404` not a team member
- `108404` team not found
- `108423` team-wide mute
- `108306` all normal members muted
- anti-spam may still surface as transport `200` with extra `TalkMsgTag` fields
- callback deny may require checking extra tags rather than only transport code

#### 31-19 — team member self-property / notification-related config
Equivalent of `8-19`.
Useful when the symptom is about **group notification behavior**, especially “only admin messages remind”, “group has red dot but no reminder”, or bits/custom notification properties.
High-value cases from the v2-sdk note:
- `108404` team not found
- `108302` non-normal/fixed-group constraint
- `109404` not a team member
- `109451` anti-spam hit

#### 31-23 — get team history
Equivalent of `8-23`.
This is the core protocol for **V10 group history query**.
High-value cases from the v2-sdk note:
- `414` parameter error
- `109404` not a team member

Practical troubleshooting meaning:
- If the case is “群历史不全 / 卸载重装后群记录缺失 / 高级群历史查询参数是否异常”, `31-23` is one of the first protocols to inspect.
- Combine it with `27-1`:
  - `27-1` tells you whether the client is in a clean-state sync / reinstall state
  - `31-23` tells you whether the client actually queried the target time window and with what parameters
- When `31-23` repeatedly uses `fromTime=0`, `excludeMsgId=0`, small `limit`, and jumping `toTime`, suspect repeated first-page queries rather than stable pagination.

### 34-* — User / push / state domain
These are the V2/V10 equivalents of classic `3-*`.

#### 34-1 — update push token
Equivalent of `3-1`.
High-value cases from the v2-sdk note:
- `414` parameter error
- `500` push token update / Redis-online-state update failure

#### 34-2 — set app foreground/background state
Equivalent of `3-2`.
High-value cases from the v2-sdk note:
- `500` server internal error
- `403` unsupported platform invocation (non-iOS / non-Android case mentioned in source)

Use `34-1 / 34-2` together when the user says “有未读红点但没推送” or “离线推送异常”.

### 36-* — Chatroom domain
These are the V2/V10 equivalents of classic `13-*`.

#### 36-2 — enter chatroom
Equivalent of `13-2`.
High-value cases from the v2-sdk note:
- `414` parameter error
- `101302` wrong cluster / app forbidden on this cluster
- `101303` appkey not found
- `113410` chatroom feature not enabled
- `102302` token validation failed
- `113404` chatroom not found
- `113406` chatroom closed
- `399` wrong unit, refresh LBS link
- `398` unit migration temporary block, retry
- `102404` account not found
- `102422` account banned
- `113305` IM connection abnormal
- `114426` blacklisted from chatroom
- `113451` anti-spam
- `463` callback auth deny

#### 36-20 — chatroom queue offer/add element
Equivalent of `13-20`.
Useful when the symptom is “上麦 / 麦位 / 队列元素异常 / 元素自动消失 / 自动下麦”.
High-value cases from the v2-sdk note:
- `114303` anonymous user not allowed
- `414` parameter error
- `102404` account not found
- `102422` account banned
- `114404` account or element owner offline
- `114449` distributed lock, retry needed
- `114432` ordinary member cannot assign / modify others' queue elements
- `117437` queue full

## How to use this file
1. Normalize whether the case is **V1/V9** or **V2/V10**.
2. If the user gives raw V2 protocol numbers, read this note first.
3. Then jump to the relevant routing / playbook document:
   - sync / roaming / reinstall → `sid-routing-ledger.md` + IM roaming playbooks
   - p2p history → single-chat / roaming playbooks
   - group history → group message / roaming playbooks
   - push → push playbooks
   - chatroom → chatroom queue / room-entry playbooks
4. If live evidence is needed, invoke `qs-techsupport`.

## Relationship to `qs-techsupport`
- This file helps answer **what the protocol means and what to inspect next**.
- `qs-techsupport` helps answer **where to pull the live evidence from QS and how to query it**.
- In practice: decide here, execute there.

## Scope note
This note is intentionally distilled. Keep using the original source doc and live logs when exact field semantics or long-tail errors matter.
