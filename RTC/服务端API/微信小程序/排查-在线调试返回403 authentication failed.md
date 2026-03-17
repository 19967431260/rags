---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 服务端API
platform: 微信小程序
title: 在线调试返回403 authentication failed
root_cause: appsecret配置错误，导致checksum校验失败
solution: 确保全局变量上的appsecret和appkey与控制台一致，检查是否有刷新过
customers: ["杭州东鼎物联网有限公司"]
source: chat_history
tags: ["403", "authentication failed", "checksum", "appsecret"]
created: 2026-02-27
updated: 2026-03-17
---

## 问题：微信小程序 在线调试返回403 authentication failed

## 问题详情

**现象**：
在线调试工具返回403错误，提示authentication failed。问题出现在checksum校验失败。

## 排查过程

1. 检查全局变量中的appsecret和appkey → 发现与控制台不一致
2. 确认checksum计算参数 → checksum通过appsecret、curtime和nonce计算

**关键发现**：后台日志显示都是checksum报错，一般是appsecret没写对导致

## 问题原因

appsecret配置错误，导致checksum校验失败

## 解决方案

确保全局变量上的appsecret和appkey与控制台一致，检查是否有刷新过

## 其他触发场景
