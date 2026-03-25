---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息同步
platform: iOS
title: iOS首次登录消息同步卡顿导致APP无响应
root_cause: 同步阶段进行数据库查询操作导致死锁，用户数据量大时同步时间较长，期间的数据库查询会阻塞同步流程
solution: 避免在消息同步阶段调用数据库操作接口（loadStickTopSessionInfos、addStickTopSession、stickTopInfoForSession、getMessagesDynamically），建议等待同步完成（login step=8）后再进行相关操作
customers: ["初晴/核芯"]
source: chat_history
tags: ["iOS", "消息同步", "死锁", "卡顿", "stickTopInfoForSession", "首次登录"]
created: 2025-05-28
updated: 2025-03-20
---

## 问题：iOS iOS首次登录消息同步卡顿导致APP无响应

## 问题详情

**现象**：
iOS端账号294652首次登录后消息一直加载不出来，导致整个APP特别卡顿。现象：登录后消息同步阶段APP卡死，持续约6分钟才同步完成。环境：IM SDK V10版本，iOS平台。

## 排查过程

**关键发现**：同步阶段进行数据库查询操作导致死锁，用户数据量大时同步时间较长，期间的数据库查询会阻塞同步流程

## 问题原因

同步阶段进行数据库查询操作导致死锁，用户数据量大时同步时间较长，期间的数据库查询会阻塞同步流程

## 解决方案

避免在消息同步阶段调用数据库操作接口（loadStickTopSessionInfos、addStickTopSession、stickTopInfoForSession、getMessagesDynamically），建议等待同步完成（login step=8）后再进行相关操作
