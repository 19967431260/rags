---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 聊天室消息
platform: Unity
title: 聊天室消息自定义字段headicon获取为空
root_cause: headicon是业务自定义字段，不能直接赋值给消息对象的属性，需要放到Extension（第三方扩展字段）中，长度限制4096，必须为可解析为Json的非格式化字符串。
solution: 聊天室消息的业务自定义字段（如headicon）应放到Extension字段中存储。Extension是string类型，长度限制4096，必须为可以解析为Json的非格式化的字符串。获取消息时从Extension中解析该字段。
customers: ['上海风林火山网络科技有限公司']
source: chat_history
tags: ['聊天室', 'Unity', 'Extension', '自定义字段', 'headicon']
created: 2025-01-15
updated: 2026-03-23
---

## 问题：聊天室消息自定义字段headicon获取为空

## 问题详情

**现象**：
客户使用Unity SDK，在发送聊天室消息时给headicon字段赋值，但通过QueryMessageHistoryOnline获取消息时headicon为空。

## 排查过程

1. 客户反馈获取消息时headicon为空 → 客服询问字段定义方式
2. 客户展示代码显示直接给headicon属性赋值
3. 客服指出业务参数应放到Extension扩展字段中
**关键发现**：headicon作为业务自定义字段，应使用Extension字段存储

## 问题原因

headicon是业务自定义字段，不能直接赋值给消息对象的属性，需要放到Extension（第三方扩展字段）中，长度限制4096，必须为可解析为Json的非格式化字符串。

## 解决方案

聊天室消息的业务自定义字段（如headicon）应放到Extension字段中存储。Extension是string类型，长度限制4096，必须为可以解析为Json的非格式化的字符串。获取消息时从Extension中解析该字段。

## 其他触发场景

（合并时在此处追加）
