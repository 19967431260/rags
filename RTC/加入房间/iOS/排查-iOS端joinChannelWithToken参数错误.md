---
track_type: 排查类
sub_type: 集成类
product: RTC
feature: 加入房间
platform: iOS
title: iOS端joinChannelWithToken参数错误
root_cause: token参数传了null，而token生成时传入的uid和channelName需与joinChannelWithToken传入的一致
solution: 检查token生成逻辑，确保生成token时传入的uid和channelName与joinChannelWithToken调用时传入的完全一致。
customers: ["南京锦辰文化传播有限公司"]
source: chat_history
tags: ["iOS", "joinChannelWithToken", "token", "参数错误", "RTC"]
created: 2025-08-30
updated: 2026-03-26
---

## 问题：iOS iOS端joinChannelWithToken参数错误

## 问题详情

**现象**：
客户调用joinChannelWithToken时报参数错误，channelName传roomId，channelOptions传nil。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：iOS
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 检查channelName参数 → 确认传的是roomId
2. 检查token → 发现token为null
3. 确认：token和joinChannelWithToken传入的uid、channelName需一致 → 定位参数不一致问题

**关键发现**：token参数传了null，而token生成时传入的uid和channelName需与joinChannelWithToken传入的一致

## 问题原因

token参数传了null，而token生成时传入的uid和channelName需与joinChannelWithToken传入的一致

## 解决方案

检查token生成逻辑，确保生成token时传入的uid和channelName与joinChannelWithToken调用时传入的完全一致。

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
