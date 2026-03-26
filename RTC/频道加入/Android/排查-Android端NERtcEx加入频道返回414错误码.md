---
track_type: 排查类
sub_type: 集成类
product: RTC
feature: 频道加入
platform: Android
title: Android端NERtcEx加入频道返回414错误码
root_cause: 客户端同时集成了呼叫组件(CallKitUI)和NERtcEx，NERtcEx被重复初始化导致appkey未被正确赋值。
solution: 去掉CallKitUI初始化（不需要呼叫组件时无需引入call-ui），让NERtcEx自己完成init和appkey配置。
customers: ["OCEAN BLUE"]
source: chat_history
tags: ["414", "joinChannel", "appkey", "NERtcEx", "Android"]
created: 2025-08-02
updated: 2025-08-02
---

## 问题：Android Android端NERtcEx加入频道返回414错误码

## 问题详情

**现象**：
Android端调用NERtcEx.getInstance().joinChannel时报414错误，错误信息显示appkey is empty，但客户确认已在init时设置了appkey。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：Android
- 其他：同时使用了CallKitUI和NERtcEx

**相关日志**：
result.code:414 result.err_msg:appkey is empty

## 排查过程

1. 客服拉取RTC日志分析发现错误码414且错误信息为appkey is empty → 确认错误信息
2. 检查客户端初始化代码发现客户同时使用了CallKitUI和NERtcEx → 发现集成方式异常
3. 根因：NERtcEx被重复初始化，CallKitUI.init覆盖了appkey设置 → 定位根因

**关键发现**：日志中显示result.code:414 result.err_msg:appkey is empty

## 问题原因

客户端同时集成了呼叫组件(CallKitUI)和NERtcEx，NERtcEx被重复初始化导致appkey未被正确赋值。

## 解决方案

去掉CallKitUI初始化（不需要呼叫组件时无需引入call-ui），让NERtcEx自己完成init和appkey配置。

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
