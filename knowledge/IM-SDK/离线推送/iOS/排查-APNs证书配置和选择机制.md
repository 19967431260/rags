---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 离线推送
platform: iOS
title: APNs证书配置和选择机制
root_cause: 客户端registerWithOption时配置的apnsCername与后台上传的证书名不匹配，导致token绑定失败，无法正确推送。
solution: 1. 客户端必须在registerWithOption时指定正确的证书名(option.apnsCername)；2. 证书替换时(p12换p8)，需要用相同的证书名上传新证书，先删除旧证书再上传新证书；3. 没有兜底逻辑，必须证书名匹配才能推送。
customers: ["上海袋虎-壹点灵"]
source: chat_history
tags: ["APNs", "p8证书", "p12证书", "apnsCername", "推送异常"]
created: 2026-01-04
updated: 2026-03-15
---

## 问题：iOS APNs证书配置和选择机制

## 问题详情

**现象**：
客户后台配置了同一BundleID的p12和p8两种证书，不清楚云信会选用哪个证书推送。客户端代码中配置的证书名(ydl_user_dev)在后台找不到对应配置，导致推送异常。需要了解证书选择规则和替换流程。





## 排查过程

1. 检查后台证书配置 → 发现同一BundleID有两个证书
2. 检查客户端代码 → apnsCername配置为ydl_user_dev
3. 查询服务端日志 → 发现该证书名不存在，推送全部异常
**关键发现**：客户端上报的证书名必须与后台配置的证书名完全一致。



## 问题原因

客户端registerWithOption时配置的apnsCername与后台上传的证书名不匹配，导致token绑定失败，无法正确推送。

## 解决方案

1. 客户端必须在registerWithOption时指定正确的证书名(option.apnsCername)；2. 证书替换时(p12换p8)，需要用相同的证书名上传新证书，先删除旧证书再上传新证书；3. 没有兜底逻辑，必须证书名匹配才能推送。

## 其他触发场景

（合并时在此处追加）
