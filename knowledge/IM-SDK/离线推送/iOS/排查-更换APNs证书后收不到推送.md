---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 离线推送
platform: iOS
title: 更换APNs证书后收不到推送
root_cause: 更换证书后，客户端初始化代码中的apnsCername仍使用旧证书名，导致token绑定到错误的证书，无法推送。
solution: 1. 确保客户端和后台的证书名称完全一致；2. 更换证书后，需要在初始化时传入新证书名称；3. 如果运行中更换，需调用updateApnsToken接口更新token绑定；4. p12换p8同样需要保证证书名一致，无需额外配置。
customers: ["广州爱拍网络科技有限公司"]
source: chat_history
tags: ["APNs", "证书更换", "updateApnsToken", "证书名不匹配"]
created: 2026-01-23
updated: 2026-03-15
---

## 问题：iOS 更换APNs证书后收不到推送

## 问题详情

**现象**：
iOS推送证书过期后更换新的p12证书，上传到云信管理平台后应用收不到离线推送。同时咨询p12换成p8是否需要额外配置。





## 排查过程

1. 检查证书配置 → 证书已正确上传
2. 检查证书名称 → 发现客户端配置的证书名与后台不一致
3. 查询token上报 → 未找到新证书名对应的token上报记录
**关键发现**：客户端初始化时仍使用旧证书名，未调用updateApnsToken更新。



## 问题原因

更换证书后，客户端初始化代码中的apnsCername仍使用旧证书名，导致token绑定到错误的证书，无法推送。

## 解决方案

1. 确保客户端和后台的证书名称完全一致；2. 更换证书后，需要在初始化时传入新证书名称；3. 如果运行中更换，需调用updateApnsToken接口更新token绑定；4. p12换p8同样需要保证证书名一致，无需额外配置。

## 其他触发场景

（合并时在此处追加）
