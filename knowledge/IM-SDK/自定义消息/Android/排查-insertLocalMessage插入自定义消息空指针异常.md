---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 自定义消息
platform: Android
title: insertLocalMessage插入自定义消息空指针异常
root_cause: 自定义消息的MsgAttachment实现类中包含不可序列化数据类型（JSONObject）的属性，本地插入时copy过程需要对象可序列化
solution: MsgAttachment的实现类不能有不可序列化数据类型的属性，确保所有属性都可序列化
customers: ['新视展']
source: chat_history
tags: ['insertLocalMessage', '空指针', '自定义消息', '序列化', 'MsgAttachment']
created: 2025-01-03
updated: 2026-03-23
---

## 问题：Android insertLocalMessage插入自定义消息空指针异常

## 问题详情

**现象**：
调用MsgService#insertLocalMessage方法插入本地自定义消息时回调报空指针异常，错误为Attempt to invoke interface method 'void com.netease.nimlib.sdk.msg.model.IMMessage.setFromAccount' on a null object reference。

## 排查过程

1. 客户反馈插入本地自定义消息必现空指针
2. 技术支持查看堆栈信息
3. 客户打开云信日志发现序列化失败
4. 确认自定义消息的attachment中有不可序列化的对象（JSONObject）

## 问题原因

自定义消息的MsgAttachment实现类中包含不可序列化数据类型（JSONObject）的属性，本地插入时copy过程需要对象可序列化

## 解决方案

MsgAttachment的实现类不能有不可序列化数据类型的属性，确保所有属性都可序列化

## 其他触发场景

（合并时在此处追加）
