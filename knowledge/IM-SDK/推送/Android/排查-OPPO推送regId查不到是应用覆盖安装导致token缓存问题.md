---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 推送
platform: Android
title: OPPO推送regId查不到是应用覆盖安装导致token缓存问题
root_cause: 应用覆盖安装时可能缓存了旧的token信息，导致regId查询不到；删除重装后正常
solution: OPPO推送regId缓存问题处理：删除应用重新安装；检查代码中是否有多处初始化oppo push导致token被覆盖；确保在Application中正确调用一次registerPush
customers: ["深圳市掌娱炫动"]
source: chat_history
tags: ["OPPO","regId","token缓存","推送集成"]
created: 2025-08-27
updated: 2026-03-26
---

## 问题：Android OPPO推送regId查不到是应用覆盖安装导致token缓存问题

## 问题详情

**现象**：
客户使用OPPO官方push demo后regId可以查到，但关掉后本应用又查不到regId。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：Android
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客户提供日志显示regId查到后又消失 → 发现regId获取不稳定
2. 客服分析是本地缓存覆盖问题 → 定位到token缓存问题
3. 删掉应用重新安装后regId正常 → 确认问题原因

**关键发现**：应用覆盖安装时可能缓存了旧的token信息，导致regId查询不到；删除重装后正常

## 问题原因

应用覆盖安装时可能缓存了旧的token信息，导致regId查询不到；删除重装后正常

## 解决方案

OPPO推送regId缓存问题处理：
1. 删除应用重新安装
2. 检查代码中是否有多处初始化oppo push导致token被覆盖
3. 确保在Application中正确调用一次registerPush

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
