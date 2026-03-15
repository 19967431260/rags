---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 通知栏推送
platform: iOS
title: iOS自定义通知推送收不到
root_cause: SDK初始化时传入的pushName与控制台配置的推送证书名称不一致
solution: 确保SDK初始化时apnsCername参数与控制台配置的证书名称一致,参考文档：https://doc.yunxin.163.com/messaging2/guide/TUzNDAwNDY?platform=client
customers:
- 南京企之诚国际贸易有限公司
source: chat_history
tags:
- sendCustomNotification
- iOS推送
- 证书配置
- pushName
- 自定义通知
created: '2026-02-11'
updated: '2026-03-16'
---

## 问题：iOS iOS自定义通知推送收不到

## 问题详情

**现象**：
客户端调用sendCustomNotification发送自定义通知,消息发送成功,但iOS端收不到推送。苹果后台推APP正常,但通过IM推送的自定义通知无法收到。

## 排查过程

1. 检查推送日志 → 发现代码中pushName为"xiaodao",但控制台配置的证书名不一致
2. 对比SDK初始化配置和控制台证书名称 → 确认证书名不匹配

**关键发现**：SDK初始化时传入的pushName必须与控制台配置的证书名称完全一致

## 问题原因

SDK初始化时传入的pushName与控制台配置的推送证书名称不一致

## 解决方案

确保SDK初始化时apnsCername参数与控制台配置的证书名称一致,参考文档：https://doc.yunxin.163.com/messaging2/guide/TUzNDAwNDY?platform=client
