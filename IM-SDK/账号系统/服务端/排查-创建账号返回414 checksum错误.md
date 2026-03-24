---

  "track_type": "排查类",
  "sub_type": "集成类",
  "product": "IM-SDK",
  "feature": "账号系统",
  "platform": "服务端",
  "title": "创建账号返回414 checksum错误",
  "root_cause": "checksum计算有误",
  "solution": "检查checksum计算逻辑，参考文档：https://faq.yunxin.163.com/kb/main/#/item/KB0297",
  "customers": [
    "华信永道"
  ],
  "source": "chat_history",
  "tags": [
    "414",
    "checksum",
    "创建账号",
    "服务端API"
  ],
  "created": "2025-02-12",
  "updated": "2026-03-20"

---

## 问题：服务端 创建账号返回414 checksum错误

## 问题详情

**现象**：
调用创建应用接口/user/create.action返回账号创建失败，第三方服务返回[414,checksum]。

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程



## 问题原因

checksum计算有误

## 解决方案

检查checksum计算逻辑，参考文档：https://faq.yunxin.163.com/kb/main/#/item/KB0297

## 其他触发场景

