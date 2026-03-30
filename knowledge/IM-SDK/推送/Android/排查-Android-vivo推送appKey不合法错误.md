---
track_type: 排查类
sub_type: 配置开通咨询
product: IM-SDK
feature: 推送
platform: Android
title: vivo推送appKey不合法错误
root_cause: vivo推送证书配置信息有误
solution: 检查vivo推送后台配置的appKey、appSecret是否正确
customers: ["上海掌鑫聚芯信息科技有限公司"]
source: chat_history
tags: ["vivo推送", "appKey", "10202", "证书配置"]
created: 2025-11-14
updated: 2026-03-20
---

## 问题：Android vivo推送appKey不合法错误

## 问题详情

**现象**：
vivo推送token生成成功，但推送时报错getAuthTokenError，result=10202，desc=appKey不合法。

**排查过程**：
1. 确认token已生成
2. 检查推送返回错误
3. 判断为证书配置问题

## 问题原因

vivo推送证书配置信息有误

## 解决方案

检查vivo推送后台配置的appKey、appSecret是否正确
