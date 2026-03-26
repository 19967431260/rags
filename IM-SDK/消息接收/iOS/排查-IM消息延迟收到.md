---
track_type: 排查类
sub_type: 客户环境问题
product: IM-SDK
feature: 消息接收
platform: iOS
updated: 2025-08-14
---

<!-- entry: platform=iOS, created=2025-08-14, customers=["深圳市镜玩/觅伊"], source=chat_history, frequency=1, tags=["消息延迟", "断网", "后台进程"], troubleshooting="1. 排查发送方日志\n2. 发现发送时SDK是断网状态\n3. 协议请求没发出去\n4. 进程被阻塞到凌晨2点才重连成功", root_cause="发送时SDK是断网状态，协议请求没发出去。后来可能杀进程或者app在后台进程被限制，直到2点08分才重新OnConnect回来" -->
## Q: IM消息延迟收到

**问题描述**：用户反馈晚上8点40左右发送的消息，其他用户凌晨2点才收到

**排查过程**：
1. 排查发送方日志
2. 发现发送时SDK是断网状态
3. 协议请求没发出去
4. 进程被阻塞到凌晨2点才重连成功

**根因**：发送时SDK是断网状态，协议请求没发出去。后来可能杀进程或者app在后台进程被限制，直到2点08分才重新OnConnect回来

**解决方案**：这是设备网络或后台进程被系统限制导致的，建议检查用户网络环境和应用后台运行状态