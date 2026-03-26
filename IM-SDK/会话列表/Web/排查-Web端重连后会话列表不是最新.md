---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 会话列表
platform: Web
updated: 2025-07-31
---

<!-- entry: platform=Web, created=2025-07-31, customers=["北京师范大学"], source=chat_history, frequency=1, tags=["会话列表", "重连", "onSyncFinished", "onConversationChanged"], troubleshooting="1. 排查基于onSyncFinished回调获取会话列表\n2. 测试发现延迟200ms可以获取到最新", root_cause="onSyncFinished只是同步完成标志，最终会话变更要看onConversationChanged回调" -->
## Q: Web端重连后会话列表不是最新

**问题描述**：走云信登录流程，请求的会话列表会是最新的，但从重连的过程，同步完，立刻调会话列表并不会得到最新

**排查过程**：
1. 排查基于onSyncFinished回调获取会话列表
2. 测试发现延迟200ms可以获取到最新

**根因**：onSyncFinished只是同步完成标志，最终会话变更要看onConversationChanged回调

**解决方案**：使用onConversationChanged回调来更新会话列表，它和onSyncFinished是互补的