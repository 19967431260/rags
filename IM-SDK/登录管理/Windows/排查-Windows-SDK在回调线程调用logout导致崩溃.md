---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 登录管理
platform: Windows
title: Windows SDK在回调线程调用logout导致崩溃
root_cause: 在SDK回调线程中直接调用SDK其他接口（如logout）会导致线程死锁或崩溃。
solution: 1. 不要在SDK回调线程中直接调用SDK其他接口
2. 收到SDK回调后，发送信号到UI线程，从UI线程槽函数去调用其他SDK接口
3. 业务上判定连接超时后，发送信号到UI线程，从UI线程调用logout接口
4. 参考文档：https://doc.yunxin.163.com/rtc1/guide/TUxOTU2Mjc?platform=windows
customers: ["深圳千舸智联"]
source: chat_history
tags: ["崩溃", "logout", "回调线程", "Windows", "死锁"]
created: 2025-11-11
updated: 2026-03-20
---

## 问题：Windows Windows SDK在回调线程调用logout导致崩溃

## 问题详情

**现象**：
客户在使用Windows IM SDK时，在网络不好时登录状态不返回，业务判定连接超时后直接调用logout导致崩溃。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 分析崩溃堆栈 → 发现崩溃发生在login回调线程
2. 确认调用时序 → 客户在登录回调中直接调用logout
3. 分析线程问题 → SDK回调线程调用其他SDK接口导致死锁/崩溃
4. 提供修复包 → 技术提供修复版本
**关键发现**：在SDK回调线程直接调用SDK其他接口会导致线程死锁或崩溃

**关键发现**：

## 问题原因

在SDK回调线程中直接调用SDK其他接口（如logout）会导致线程死锁或崩溃。

## 解决方案

1. 不要在SDK回调线程中直接调用SDK其他接口
2. 收到SDK回调后，发送信号到UI线程，从UI线程槽函数去调用其他SDK接口
3. 业务上判定连接超时后，发送信号到UI线程，从UI线程调用logout接口
4. 参考文档：https://doc.yunxin.163.com/rtc1/guide/TUxOTU2Mjc?platform=windows

## 其他触发场景

