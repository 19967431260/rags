---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 会话管理
platform: Android
title: queryRecentContacts返回contactId乱码
root_cause: 本地数据库存储异常，导致contactId字段读取时出现乱码。可能是会话对方的accid包含特殊字符，或本地数据库文件损坏。
solution: 1. 如果会话对方accid包含特殊字符，需要规范accid生成规则；2. 如果是本地数据库损坏，建议用户卸载重装应用恢复；3. 这种情况比较罕见，通常重装可以解决。
customers:
- YOOY语音
source: chat_history
tags:
- queryRecentContacts
- contactId乱码
- 本地数据库
- 特殊字符
created: '2026-01-04'
updated: '2026-03-15'
---

## 问题：Android queryRecentContacts返回contactId乱码

## 问题详情

**现象**：
调用queryRecentContacts接口查询最近会话列表，返回的contactId字段出现乱码内容。问题仅在个别用户出现，其他用户和测试环境无法复现。

## 排查过程

1. 检查接口调用 → 确认使用queryRecentContacts正常调用
2. 尝试其他设备复现 → 无法复现
3. 检查accid生成逻辑 → accid由系统生成，用户无法控制
**关键发现**：问题仅在特定用户特定设备出现，怀疑本地数据库损坏。

## 问题原因

本地数据库存储异常，导致contactId字段读取时出现乱码。可能是会话对方的accid包含特殊字符，或本地数据库文件损坏。

## 解决方案

1. 如果会话对方accid包含特殊字符，需要规范accid生成规则；2. 如果是本地数据库损坏，建议用户卸载重装应用恢复；3. 这种情况比较罕见，通常重装可以解决。
