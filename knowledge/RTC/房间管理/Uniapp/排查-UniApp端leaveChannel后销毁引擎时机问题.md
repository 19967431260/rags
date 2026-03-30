---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 房间管理
platform: Uniapp
title: UniApp端leaveChannel后销毁引擎时机问题
root_cause: leave接口调用后引擎立即被销毁，但SDK内部还在打印日志，导致空指针报错，且后续代码未执行
solution: leave接口调用后会触发onLeaveChannel回调，需在该回调里再执行destroyEngine销毁引擎，而不是在leave调用后立即销毁。
customers: ["云南深度科技有限公司"]
source: chat_history
tags: ["UniApp", "RTC", "leaveChannel", "destroyEngine", "报错"]
created: 2025-08-15
updated: 2026-03-26
---

## 问题：Uniapp UniApp端leaveChannel后销毁引擎时机问题

## 问题详情

**现象**：
客户从房间返回后不退出房间，通过浮窗可再次进入。点击关闭按钮时调用leaveChannel和destroyEngine，报错NERtcMoudle.nertcPrint，且未走进后续代码。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：UniApp
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
NERtcMoudle.nertcPrint空指针报错

## 排查过程

1. 确认问题：leave后立即销毁引擎导致SDK内部日志打印报错 → 定位时机问题
2. 确认解决方案：在leave的onLeaveChannel回调里再调用destroyEngine → 确认正确时机

**关键发现**：leave接口调用后引擎立即被销毁，但SDK内部还在打印日志，导致空指针报错

## 问题原因

leave接口调用后引擎立即被销毁，但SDK内部还在打印日志，导致空指针报错，且后续代码未执行

## 解决方案

leave接口调用后会触发onLeaveChannel回调，需在该回调里再执行destroyEngine销毁引擎，而不是在leave调用后立即销毁。

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
