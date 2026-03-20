---
track_type: 排查类
sub_type: 测试问题
product: NERoom
feature: 屏幕共享
platform: Android
title: Android屏幕共享接收端闪退AbstractMethodError
root_cause: 1. 1.31.0版本的NERoom内部onUserVideoStart方法没有实现
2. 客户额外依赖nertc_core与组件底层版本冲突
solution: 1. 降级到netease_roomkit: 1.30.14（IM V9对应的最新组件版本）
2. 移除额外对nertc_core的依赖
3. pubspec.yaml修改版本: netease_roomkit: 1.30.14
4. 清除缓存后重新编译
customers: ["海南探寻未来科技有限责任公司"]
source: chat_history
tags: ["AbstractMethodError", "屏幕共享", "闪退", "1.31.0", "1.30.14", "版本冲突"]
created: 2025-11-10
updated: 2026-03-20
---

## 问题：Android Android屏幕共享接收端闪退AbstractMethodError

## 问题详情

**现象**：
客户在使用NERoom Android 1.31.0版本进行屏幕共享时，接收端出现闪退。错误信息：java.lang.AbstractMethodError: abstract method void com.netease.lava.nertc.sdk.AbsNERtcCallbackEx.onUserVideoStart。开启屏幕共享后，接收端崩溃。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 确认崩溃现象 → 接收端闪退，开启端正常
2. 检查回调实现 → 客户未实现onMemberScreenShareStateChanged回调
3. 建议实现回调 → 客户实现后仍然闪退
4. 分析日志错误 → 发现onUserVideoStart抽象方法未实现错误
5. 检查依赖版本 → 发现客户同时依赖了nertc_core，与组件底层版本冲突
**关键发现**：1.31.0版本存在内部onUserVideoStart方法未实现的问题，且与额外引入的nertc_core版本冲突

**关键发现**：

## 问题原因

1. 1.31.0版本的NERoom内部onUserVideoStart方法没有实现
2. 客户额外依赖nertc_core与组件底层版本冲突

## 解决方案

1. 降级到netease_roomkit: 1.30.14（IM V9对应的最新组件版本）
2. 移除额外对nertc_core的依赖
3. pubspec.yaml修改版本: netease_roomkit: 1.30.14
4. 清除缓存后重新编译

## 其他触发场景

