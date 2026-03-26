---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 推送配置
platform: Android
title: Android端OPPO新消息分类推送配置
root_cause: 使用OPPO新消息分类时，发送方未正确传递category和channel_id参数
solution: OPPO新消息分类推送配置：发送方需同时传递category字段和channel_id（默认通道）；参考文档：https://doc.yunxin.163.com/messaging/server-apis/DQyNjc5NjE?platform=server
customers: ["广州纪元互动"]
source: chat_history
tags: ["OPPO推送","新消息分类","category","channel_id"]
created: 2025-08-22
updated: 2025-08-22
---

## 问题：Android Android端OPPO新消息分类推送配置

## 问题详情

**现象**：
客户有两个APP，一个使用OPPO旧版自建通道，一个使用新消息分类（OPPO New Type）。使用新消息分类的APP收不到离线推送。

**复现步骤**：
（无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客户查阅OPPO官方文档
2. 客服确认：新消息分类只需要正常传category字段，channel_id也需要带，发送方要带category

**关键发现**：使用OPPO新消息分类时，发送方未正确传递category和channel_id参数。

## 问题原因

使用OPPO新消息分类时，发送方未正确传递category和channel_id参数。

## 解决方案

OPPO新消息分类推送配置：发送方需同时传递category字段和channel_id（默认通道）；参考文档：https://doc.yunxin.163.com/messaging/server-apis/DQyNjc5NjE?platform=server

## 其他触发场景

（合并时在此处追加）
