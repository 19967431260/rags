---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息撤回
platform: iOS
title: 撤回失败消息报错NIMLocalErrorCodeInvalidParam
root_cause: 点击撤回时本地消息未删除，重复点击撤回导致参数错误。SDK有时会同步删除本地消息，有时不会。
solution: 撤回时增加本地消息删除处理，避免对已删除消息重复调用撤回接口。
customers: ["娱想网络"]
source: chat_history
tags: ["消息撤回","NIMLocalErrorCodeInvalidParam","参数错误"]
created: 2026-02-07
updated: 2026-03-17
---

## 问题：iOS 撤回失败消息报错NIMLocalErrorCodeInvalidParam

## 问题详情

**现象**：
调用消息撤回接口时报错：Error Domain=NIMLocalErrorDomain Code=1 "错误的参数" UserInfo={NSLocalizedDescription=错误的参数, enum=NIMLocalErrorCodeInvalidParam}。

## 问题原因

点击撤回时本地消息未删除，重复点击撤回导致参数错误。SDK有时会同步删除本地消息，有时不会。

## 解决方案

撤回时增加本地消息删除处理，避免对已删除消息重复调用撤回接口。

## 其他触发场景

