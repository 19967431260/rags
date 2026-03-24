---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息更新
platform: Uniapp
title: Uniapp更新自定义消息attachment参数格式错误
root_cause: attachment参数需要将整个value转为JSON字符串格式，而不是直接传入JSON对象
solution: 将attachment后的所有内容整体转为JSON字符串传入，例如：attachment: JSON.stringify({type:"1005",roomNo:"95814599"...})
customers: ['海康华安']
source: chat_history
tags: ['更新消息', 'attachment', '非法参数', 'Uniapp', '自定义消息']
created: 2025-01-16
updated: 2026-03-23
---

## 问题：Uniapp Uniapp更新自定义消息attachment参数格式错误

## 问题详情

**现象**：
调用更新消息方法时传入自定义消息的attachment参数报非法参数错误。客户将attachment后的内容作为JSON对象传入，但接口要求将整个attachment后的内容转为JSON字符串。

## 排查过程

1. 客户反馈更新消息方法调用报错\n2. 检查传入参数：attachment后传入的是JSON对象\n3. 确认问题：需要将attachment后的所有内容转为JSON字符串\n4. 验证解决方案后问题解决

## 问题原因

attachment参数需要将整个value转为JSON字符串格式，而不是直接传入JSON对象

## 解决方案

将attachment后的所有内容整体转为JSON字符串传入，例如：attachment: JSON.stringify({type:"1005",roomNo:"95814599"...})

## 其他触发场景

（合并时在此处追加）
