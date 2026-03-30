---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: SDK集成
platform: 小程序
title: 小程序引入IM库编译慢问题
root_cause: IM库体积较大导致编译慢
solution: 可以使用ESM方式裁剪库,只保留使用到的模块。文档:https://doc.yunxin.163.com/messaging2/guide/DcyMjA1Njk?platform=client
customers: ["广州有爱中医门诊部有限公司"]
source: chat_history
tags: ["小程序", "IM", "编译慢", "ESM", "模块裁剪"]
created: 2026-02-09
updated: 2026-03-17
---

## 问题：小程序 小程序引入IM库编译慢问题

## 问题详情

**现象**：
客户在微信小程序中引入IM库后编译速度很慢,询问解决办法。

## 排查过程

1. 检查IM库体积 → 发现库体积较大

**关键发现**：IM库体积较大导致编译慢

## 问题原因

IM库体积较大导致编译慢

## 解决方案

可以使用ESM方式裁剪库,只保留使用到的模块。文档:https://doc.yunxin.163.com/messaging2/guide/DcyMjA1Njk?platform=client

## 其他触发场景
