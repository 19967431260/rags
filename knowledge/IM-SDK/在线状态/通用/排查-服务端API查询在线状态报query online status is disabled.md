---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 在线状态
platform: 通用
title: 服务端API查询在线状态报query online status is disabled
root_cause: 服务端API查询在线状态功能需要IM旗舰版以上资质，客户使用的海外高级版不具备此权限。
solution: 方案一：升级到IM旗舰版；方案二：前端SDK使用在线状态订阅方案实现（https://doc.yunxin.163.com/messaging2/guide/DA0MjM3NTk?platform=client#用户状态类型）
customers: ["WORKTOGETHER PTE LTD"]
source: chat_history
tags: ["在线状态","query online status is disabled","服务端API"]
created: 2025-08-30
updated: 2026-03-26
---

## 问题：通用 服务端API查询在线状态报query online status is disabled

## 问题详情

**现象**：
客户端使用服务端API查询用户在线状态时报错"query online status is disabled"，控制台开启对应开关后仍然报错。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 排查控制台开关是否已开启 → 确认已开启但仍报错
2. 确认客户使用的版本 → 海外高级版
3. 确认服务端API要求 → 需要IM旗舰版以上才可调用

**关键发现**：服务端API查询在线状态功能需要IM旗舰版以上资质，客户使用的海外高级版不具备此权限。

## 问题原因

服务端API查询在线状态功能需要IM旗舰版以上资质，客户使用的海外高级版不具备此权限。

## 解决方案

方案一：升级到IM旗舰版；方案二：前端SDK使用在线状态订阅方案实现（https://doc.yunxin.163.com/messaging2/guide/DA0MjM3NTk?platform=client#用户状态类型）

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
