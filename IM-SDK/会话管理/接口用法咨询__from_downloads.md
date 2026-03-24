---

  "track_type": "咨询类",
  "sub_type": "接口用法咨询",
  "product": "IM-SDK",
  "feature": "会话管理",
  "updated": "2026-03-20"

---

<!-- entry: platform=通用, created=2025-02-08, customers=["初晴/核芯"], source=chat_history, frequency=1, tags=["会话删除", "批量删除", "API咨询"] -->
## Q: 批量删除多个会话消息API咨询

**问题描述**：客户咨询是否有批量删除多个会话消息的API方法，文档中只看到删除单个最近会话的接口。

**答案**：SDK未提供批量删除接口，需要多次调用单条删除接口实现。

---
<!-- entry: platform=Flutter, created=2025-02-24, customers=["南宁小清柠"], source=chat_history, frequency=1, tags=["未读数量", "querySession", "Flutter", "会话", "iOS对比"] -->
## Q: Flutter获取指定会话未读数量

**问题描述**：咨询Flutter SDK中是否有类似iOS的allUnreadMessagesInSession API，已知会话id获取该会话的所有未读数量。

**答案**：Flutter SDK没有allUnreadMessagesInSession API，可以使用querySession方法获取指定会话信息，其中包含未读数

---
<!-- entry: platform=安卓, created=2025-02-19, customers=["杭州跨客技术服务有限公司"], source=chat_history, frequency=1, tags=["IM-SDK", "会话列表", "安卓"] -->
## Q: IM获取所有最近会话列表方法

**问题描述**：用户询问是否有方法可以一次获取所有会话。

**答案**：使用获取所有最近会话列表的方法，参考文档：https://doc.yunxin.163.com/messaging/guide/TgyOTE3MDI?platform=android

---
<!-- entry: platform=iOS, created=2025-02-21, customers=["杭州跨客技术服务有限公司"], source=chat_history, frequency=1, tags=["IM-SDK", "fetchServerSessions", "分页查询", "iOS"] -->
## Q: iOS fetchServerSessions分页查询参数设置

**问题描述**：用户询问fetchServerSessions方法第一次调用时minTimestamp和maxTimestamp如何设置，以及分页查询逻辑。

**答案**：第一次minTimestamp=0，maxTimestamp不传或当前时间戳-1；第二次minTimestamp=0，maxTimestamp=上次结果中最早一条会话的updateTime值；limit最小用2，避免出现相同时间戳会话时无限循环

---
<!-- entry: platform=Web, created=2025-02-20, customers=["湖南登时互动网络科技有限公司"], source=chat_history, frequency=1, tags=["会话ID", "V10", "会话类型", "Web"] -->
## Q: V10根据ID区分会话类型

**问题描述**：客户咨询V10是否有根据ID区分会话类型的API，之前V9能直接从点击回调拿类型。

**答案**：V9也是返回一个ID，都需要自行解析ID结构。V10的会话ID结构参考文档，需要自行解析判断会话类型

---
