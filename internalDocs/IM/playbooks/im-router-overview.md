# IM Router Overview

Use this overview when the user reports an IM problem but the symptom is still vague.

## Typical user complaints
- 消息丢了 / 没收到
- 换端后消息历史没了
- 未读数不对
- 明明发出去了却被拦截 / 安全通异常

## Stage-based routing
Do not route by wording alone. Route by the stage where the problem most likely stopped.

### A. Message delivery complaint
Use when the user says “丢消息 / 没收到消息 / 发了对方没收到”.

Questions to ask first:
- 发送方和接收方是谁？
- 是点对点还是群？
- 大概时间点？
- 是否在线？是否换端？
- 有没有 clientId / serverId / 日志？

Then read:
- `message-loss-triage.md`

### B. Unread-state complaint
Use when the user says “未读数不对 / 已读变未读 / 换设备后会话状态异常”.

Questions to ask first:
- 哪些会话异常？全部还是部分？
- 是否换设备 / 重装 / 切账号？
- 时间范围？
- 相关消息本身是否实际丢失？

Then read:
- `unread-state-troubleshooting.md`

### C. Roaming / history-sync complaint
Use when the user says “换手机后历史消息没了 / 离线消息没有补到 / 漫游异常”.

Questions to ask first:
- 是否换端或离线重登？
- 目标消息是否应该存漫游？
- 有没有明确时间点和账号？
- QS / 服务端是否可查到对应消息？

Then read:
- `roaming-troubleshooting.md`

### D. Anti-spam / Safetong complaint
Use when the user says:
- 内容没被拦截
- 被误拦截
- 安全通没生效
- 反垃圾策略异常

Questions to ask first:
- 文本/图片/语音/视频中的哪种类型？
- 是否拿到了 antiSpam / suggestion / spendMs 等字段？
- 是否涉及安全通、通用反垃圾或易盾协查？

Then read:
- `im-safetong-troubleshooting.md`
- `safetong-internal-troubleshooting.md`

## Cross-links and caveats
- Message-loss, unread-state, and roaming often overlap. Do not force a single path too early.
- Backend existence does not guarantee client visibility.
- If the case is actually special handling (e.g. callback / blacklist / unfinished edge case), reduce confidence and say what is missing.
