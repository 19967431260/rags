---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 推送
platform: Android
title: OPPO推送private_msg_template_id报错需在OPPO后台申请消息模板
root_cause: OPPO私信通道（category:IM）从2024年起必须携带private_msg_template_id字段，需提前在OPPO开发者后台申请对应的IM类消息模板
solution: OPPO私信推送配置：在OPPO开放平台申请IM类消息模板（私信模板），在云信后台配置channel_id时关联该模板；同时确保payload中包含category:"IM"和正确的private_msg_template_id字段
customers: ["深圳市掌娱炫动"]
source: chat_history
tags: ["OPPO","推送","private_msg_template_id","code54","私信模板"]
created: 2025-08-25
updated: 2026-03-26
---

## 问题：Android OPPO推送private_msg_template_id报错需在OPPO后台申请消息模板

## 问题详情

**现象**：
OPPO推送报{"code":54,"message":"private_msg_template_id is null"}，推送送达OPPO服务器成功但用户收不到。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：Android
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
{"code":54,"message":"private_msg_template_id is null"}

## 排查过程

1. 客户提供日志显示code54错误 → 确认OPPO服务器返回模板ID缺失错误
2. 客服确认需在OPPO后台申请私信模板 → 指引到正确的配置路径
3. 在OPPO推送后台创建IM类消息模板后解决 → 问题解决

**关键发现**：OPPO私信通道从2024年起必须携带private_msg_template_id字段，需提前在OPPO开发者后台申请IM类消息模板

## 问题原因

OPPO私信通道（category:IM）从2024年起必须携带private_msg_template_id字段，需提前在OPPO开发者后台申请对应的IM类消息模板

## 解决方案

OPPO私信推送配置：
1. 在OPPO开放平台申请IM类消息模板（私信模板）
2. 在云信后台配置channel_id时关联该模板
3. 同时确保payload中包含category:"IM"和正确的private_msg_template_id字段

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
