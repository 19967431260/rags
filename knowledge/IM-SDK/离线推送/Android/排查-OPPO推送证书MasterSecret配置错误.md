---
track_type: "排查类"
sub_type: "使用问题"
product: "IM-SDK"
feature: "离线推送"
platform: "Android"
title: "OPPO推送证书MasterSecret配置错误"
root_cause: "云信控制台上OPPO推送证书的MasterSecret配置不正确，使用了错误的值。"
solution: "1. 到OPPO推送控制台的应用配置里面获取正确的MasterSecret
2. 不要用其他地方的MasterSecret
3. 配置正确的MasterSecret到云信控制台"
customers: ["FVIP云信-深圳富旅奇缘"]
source: "chat_history"
tags: ["OPPO", "离线推送", "MasterSecret", "证书配置"]
created: "2025-09-10"
updated: "2026-03-20"
---

## 问题：Android OPPO推送证书MasterSecret配置错误

## 问题详情

**现象**：
OPPO手机收不到离线推送，小米的可以。

## 排查过程

1. 检查云信控制台配置
2. 发现OPPO推送证书的MasterSecret配置不正确
3. 客户更换MasterSecret后仍有问题
4. 最终排查发现需要在OPPO推送控制台的应用配置里面找正确的MasterSecret

## 问题原因

云信控制台上OPPO推送证书的MasterSecret配置不正确，使用了错误的值。

## 解决方案

1. 到OPPO推送控制台的应用配置里面获取正确的MasterSecret
2. 不要用其他地方的MasterSecret
3. 配置正确的MasterSecret到云信控制台

## 其他触发场景
