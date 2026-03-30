---
track_type: 排查类
sub_type: 配置类
product: IM-SDK
feature: 离线推送
platform: iOS
title: iOS端Uniapp集成推送token上报失败
root_cause: 客户生成的p12证书是iOS开发证书（Apple Development），不是推送专用证书（Apple Push Notification service SSL (Sandbox & Production)）。开发证书无法用于生产环境推送。
solution: 1. 登录Apple Developer后台，创建专门的推送证书（选择Apple Push Notification service SSL类型）2. 导出.p12文件时在钥匙串中确保选择正确的证书类型 3. 将证书配置到云信控制台，确保证书状态为'已验证' 4. 设置证书信任：右键证书 > 显示简介 > 信任 > 使用此证书时设为'始终信任'
customers: ["四川巨蟹科技有限公司"]
source: chat_history
tags: ["iOS","推送","p12证书","Uniapp","token上报","MissingProviderToken"]
created: 2025-08-08
updated: 2026-03-26
---

## 问题：iOS iOS端Uniapp集成推送token上报失败

## 问题详情

**现象**：
iOS端Uniapp集成IM SDK，真机调试可以收到推送消息，但系统通知栏没有推送通知。检查发现推送token没有上报到云信服务器。

**复现步骤**：
（无明确步骤，从会话提取）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：Uniapp编译到iOS

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 确认推送token未注册成功（服务端日志显示MissingProviderToken）→ 确认问题
2. 排查发现iOS p12证书是开发证书（非推送证书），在钥匙串中显示为'此证书根证书无效，不受信任' → 根因定位
3. 客户从钥匙串导出证书时导成了开发证书而非推送专用证书 → 根因确认

**关键发现**：客户生成的p12证书是iOS开发证书（Apple Development），不是推送专用证书（Apple Push Notification service SSL (Sandbox & Production)）。开发证书无法用于生产环境推送。

## 问题原因

客户生成的p12证书是iOS开发证书（Apple Development），不是推送专用证书（Apple Push Notification service SSL (Sandbox & Production)）。开发证书无法用于生产环境推送。

## 解决方案

1. 登录Apple Developer后台，创建专门的推送证书（选择Apple Push Notification service SSL类型）
2. 导出.p12文件时在钥匙串中确保选择正确的证书类型
3. 将证书配置到云信控制台，确保证书状态为'已验证'
4. 设置证书信任：右键证书 > 显示简介 > 信任 > 使用此证书时设为'始终信任'

## 其他触发场景

（合并时在此处追加）
