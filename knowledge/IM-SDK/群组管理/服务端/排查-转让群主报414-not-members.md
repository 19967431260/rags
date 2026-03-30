---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 群组管理
platform: 服务端
title: 转让群主报414：被邀请人未完成入群同意流程
root_cause: 群设置为需要被邀请人同意才能入群，但只调用了拉人入群接口，没有调用同意入群接口，导致被邀请人还在等待同意状态不在群内
solution: 先拉人入群后还需调用同意入群接口；或将群设置为不需要被邀请人同意（msg_receipt_type=0）；注意msg_receipt_type默认是1（需要同意）。
customers: ["杭州徕檬"]
source: chat_history
tags: ["转让群主", "414", "msg_receipt_type", "入群同意"]
created: 2025-07-02
updated: 2025-07-25
---

## 问题：转让群主报414：被邀请人未完成入群同意流程

## 问题原因

群设置为需要被邀请人同意才能入群，但只调用了拉人入群接口，没有调用同意入群接口，导致被邀请人还在等待同意状态不在群内

## 解决方案

先拉人入群后还需调用同意入群接口；或将群设置为不需要被邀请人同意（msg_receipt_type=0）；注意msg_receipt_type默认是1（需要同意）。
