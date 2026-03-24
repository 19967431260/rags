---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 数据库加密
platform: Android
title: 升级SDK后发送消息报错数据库未打开
root_cause: sqlcipher-android依赖版本不兼容
solution: 将sqlcipher-android依赖更换为implementation("net.zetetic:sqlcipher-android:4.6.1")
customers: ["深圳市镜玩-觅伊"]
source: chat_history
tags: ["数据库加密","sqlcipher","SDK升级","MsgDatabase"]
created: 2025-02-17
updated: 2025-03-20
---

## 问题：Android 升级SDK后发送消息报错数据库未打开

## 问题详情

**现象**：
升级SDK后发送消息报错java.lang.IllegalStateException: MsgDatabase is not opened. Please login first! 已确认登录成功。

**复现步骤**：
1. 升级SDK
2. 登录成功
3. 发送消息报错

## 排查过程

1. 确认开启数据库加密 → 确认功能开启
2. 检查sqlcipher-android依赖版本 → 发现版本不兼容

**关键发现**：sqlcipher-android依赖版本不兼容导致数据库无法打开

## 问题原因

sqlcipher-android依赖版本不兼容。

## 解决方案

将sqlcipher-android依赖更换为：
```gradle
implementation("net.zetetic:sqlcipher-android:4.6.1")
```

## 其他触发场景

