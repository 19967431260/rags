---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 云端录制回调
platform: 服务端
title: 录制完成回调失败SSL证书验证错误
root_cause: 回调地址使用IP(121.41.59.121)但SSL证书绑定的是域名(video.firetv4k.online)，导致证书验证失败
solution: 修改回调地址使用域名而非IP，或更新证书配置。修改后不会重新回调，需要重新执行录制
customers: ["杭州帆特科技有限公司"]
source: chat_history
tags: ["回调失败", "SSL证书", "域名验证", "云端录制"]
created: 2026-02-26
updated: 2026-03-17
---

## 问题：服务端 录制完成回调失败SSL证书验证错误

## 问题详情

**现象**：
云端录制完成后未收到回调通知，手动查询有录制文件。回调地址为https://121.41.59.121/api/yunxin/callback/receive。

## 排查过程

1. 检查回调日志 → 发现SSL证书验证失败
2. 查看错误详情 → javax.net.ssl.SSLPeerUnverifiedException: Hostname 121.41.59.121 not verified，证书DN为video.firetv4k.online

**关键发现**：回调地址使用IP但证书绑定的是域名，导致证书验证失败

## 问题原因

回调地址使用IP(121.41.59.121)但SSL证书绑定的是域名(video.firetv4k.online)，导致证书验证失败

## 解决方案

修改回调地址使用域名而非IP，或更新证书配置。修改后不会重新回调，需要重新执行录制

## 其他触发场景
