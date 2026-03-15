---
track_type: 排查类
sub_type: 客户环境问题
product: IM-SDK
feature: 日志管理
platform: Android
title: SDK日志写入失败ENOENT错误
root_cause: SDK默认日志路径没有写入权限，且客户未配置sdkStorageRootPath指定有效的存储路径
solution: 在SDK初始化时通过sdkStorageRootPath参数指定一个有权限的私有缓存目录。Android私有目录路径：/sdcard/Android/data/包名 或 /data/data/包名。参考文档：https://doc.yunxin.163.com/messaging/guide/TI5ODE2MTM?platform=android
customers: ["时间在线"]
source: chat_history
tags: ["Android", "日志", "ENOENT", "FileNotFoundException", "sdkStorageRootPath", "权限"]
created: 2026-01-04
updated: 2026-03-15
---

## 问题：Android SDK日志写入失败ENOENT错误

## 问题详情

**现象**：
SDK初始化后日志无法写入，报错：java.io.FileNotFoundException: /data/user/0/hoklo.android/cache/nim/log/nim_sdk.log: open failed: ENOENT (No such file or directory)。客户认为/data/user/0/包名/cache是私有目录应该有默认权限。

## 排查过程

1. 检查报错路径 → /data/user/0/hoklo.android/cache/nim/log/
2. 确认目录权限 → 该路径不是私有目录
3. 检查sdkStorageRootPath配置 → 客户未设置
**关键发现**：客户误认为该路径是私有目录，实际上Android私有目录是/sdcard/Android/data/包名或/data/data/包名

## 问题原因

SDK默认日志路径没有写入权限，且客户未配置sdkStorageRootPath指定有效的存储路径

## 解决方案

在SDK初始化时通过sdkStorageRootPath参数指定一个有权限的私有缓存目录。Android私有目录路径：/sdcard/Android/data/包名 或 /data/data/包名。参考文档：https://doc.yunxin.163.com/messaging/guide/TI5ODE2MTM?platform=android

## 其他触发场景

（合并时在此处追加）
- [Android] SDK日志写入失败ENOENT错误，来源：['时间在线']，2026-03-15
