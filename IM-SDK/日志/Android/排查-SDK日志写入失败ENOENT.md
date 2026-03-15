---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 日志
platform: Android
title: Android SDK日志写入失败ENOENT
root_cause: SDK尝试在默认路径写入日志时没有权限，导致文件创建失败
solution: 在初始化SDK时通过sdkStorageRootPath参数指定一个私有缓存目录作为日志存储路径。参考文档：https://doc.yunxin.163.com/messaging/guide/TI5ODE2MTM?platform=android
customers: ["时间在线-gj"]
source: chat_history
tags: ["日志", "ENOENT", "FileNotFoundException", "sdkStorageRootPath", "权限"]
created: 2026-01-04
updated: 2026-03-15
---

## 问题：Android Android SDK日志写入失败ENOENT

## 问题详情

**现象**：
Android端SDK报错：java.io.FileNotFoundException: /data/user/0/hoklo.android/cache/nim/log/nim_sdk.log: open failed: ENOENT (No such file or directory)，日志无法写入。

**相关日志**：
```
java.io.FileNotFoundException: /data/user/0/hoklo.android/cache/nim/log/nim_sdk.log: open failed: ENOENT (No such file or directory)
```

## 排查过程

1. 检查报错路径 → /data/user/0/包名/cache/nim/log/
2. 确认是否为私有目录 → 不是，私有目录应为/sdcard/Android/data/包名或/data/data/包名
3. 检查是否设置sdkStorageRootPath → 未设置
4. 分析原因 → 默认路径没有权限导致创建文件失败

**关键发现**：SDK默认日志路径可能没有写入权限

## 问题原因

SDK尝试在默认路径写入日志时没有权限，导致文件创建失败

## 解决方案

在初始化SDK时通过sdkStorageRootPath参数指定一个私有缓存目录作为日志存储路径。参考文档：https://doc.yunxin.163.com/messaging/guide/TI5ODE2MTM?platform=android

## 其他触发场景

