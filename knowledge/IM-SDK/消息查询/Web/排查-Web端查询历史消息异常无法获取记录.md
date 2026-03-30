---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息查询
platform: Web
title: Web端查询历史消息异常无法获取记录
root_cause: 安卓端发送消息时MemberPushOption的ForcePushList字段传值不规范，导致消息包含异常字符#%@all@%#，Web SDK无法解析
solution: 使用修复版JS文件替换原有SDK；检查安卓端代码，确保MemberPushOption参数按规范传递，艾特所有人时传null
customers: ["广西源龙网络科技有限公司"]
source: chat_history
tags: ["Web", "历史消息", "查询失败", "MemberPushOption", "ForcePushList"]
created: 2025-05-13
updated: 2025-03-20
---

## 问题：Web Web端查询历史消息异常无法获取记录

## 问题详情

**现象**：
客户反馈Web端查询历史消息出错，无法获取聊天记录。经排查发现是由于消息中包含异常字段内容导致SDK无法解析。

**环境信息**：
- SDK 版本：
- 系统版本 / 设备：
- 平台：Web

## 排查过程

1. 客户提供日志分析
2. 发现消息中包含#%@all@%#字符
3. 确认是安卓端发送消息时MemberPushOption的ForcePushList字段不规范导致
4. 建议检查NIMMessagePushConfig中forcePush设置
5. 提供修复版JS文件https://yx-web-nosdn.netease.im/package/1747194828266/index.umd_10_4_0.js

## 问题原因

安卓端发送消息时MemberPushOption的ForcePushList字段传值不规范，导致消息包含异常字符#%@all@%#，Web SDK无法解析

## 解决方案

使用修复版JS文件替换原有SDK；检查安卓端代码，确保MemberPushOption参数按规范传递，艾特所有人时传null

## 其他触发场景

