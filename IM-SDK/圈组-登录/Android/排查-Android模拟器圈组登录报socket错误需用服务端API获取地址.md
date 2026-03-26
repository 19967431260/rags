---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 圈组-登录
platform: Android
title: Android模拟器圈组登录报socket错误需用服务端API获取地址
root_cause: Android模拟器环境使用SDK的getQChatAddress方法获取到的是socket类型地址，APP端需要websocket地址类型
solution: Uniapp Android模拟器圈组登录临时方案：调用服务端API（https://doc.yunxin.163.com/messaging/server-apis/DY3NDU0NDU?platform=server）查询地址时type参数选1获取websocket类型地址；正式方案SDK会优化待后续更新
customers: ["家有学霸"]
source: chat_history
tags: ["圈组","Android模拟器","socket连接失败","websocket","getQChatAddress"]
created: 2025-08-20
updated: 2026-03-26
---

## 问题：Android Android模拟器圈组登录报socket错误需用服务端API获取地址

## 问题详情

**现象**：
Uniapp打包Android模拟器后圈组登录报错：clientSocketV1::socket xhr or socket connect failed。

**复现步骤**：
（无明确步骤，从会话提取）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：Android模拟器
- 其他：Uniapp + 圈组

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客户提供Android模拟器登录错误日志 → 获取错误信息
2. 客服确认是SDK获取link地址方式的问题 → 根因定位
3. 临时方案：不要用uni.$NIM.plugin.getQChatAddress获取地址，改为调用服务端API查询地址 → 方案
4. 服务端API查询时type参数选1（返回websocket地址而非socket地址）→ 方案细化
5. 后续客服与研发确认有更优方案，通知客户先web端调试 → 后续

**关键发现**：Android模拟器环境使用SDK的getQChatAddress方法获取到的是socket类型地址，APP端需要websocket地址类型

## 问题原因

Android模拟器环境使用SDK的getQChatAddress方法获取到的是socket类型地址，APP端需要websocket地址类型。

## 解决方案

Uniapp Android模拟器圈组登录临时方案：调用服务端API（https://doc.yunxin.163.com/messaging/server-apis/DY3NDU0NDU?platform=server）查询地址时type参数选1获取websocket类型地址；正式方案SDK会优化待后续更新。

## 其他触发场景

（合并时在此处追加）
