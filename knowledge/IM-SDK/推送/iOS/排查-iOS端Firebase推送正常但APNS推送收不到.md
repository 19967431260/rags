---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 第三方推送
platform: iOS
title: iOS端Firebase推送正常但APNS推送收不到
root_cause: APNS token未上传到云信服务器。客户虽然接了Firebase推送，但APNS token需要通过updateApnsToken方法单独上传。
solution: 1. 在iOS端登录IM后调用NIMIOSSDK的updateApnsToken:方法上报APNS token；2. debug环境需在代码中设置option.apnsCername为开发环境证书名，release环境设置为生产环境证书名（如wepush_prod）；3. 确认控制台对应环境已正确配置对应类型的APNS证书。
customers: ["OCEAN BLUE"]
source: chat_history
tags: ["APNS", "push", "updateApnsToken", "Firebase", "iOS", "证书环境"]
created: 2025-08-05
updated: 2025-08-05
---

## 问题：iOS iOS端Firebase推送正常但APNS推送收不到

## 问题详情

**现象**：
iOS端集成Flutter，Firebase推送正常，但APNS推送收不到。控制台配置了p8证书和Key ID，appkey也配置了。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：iOS（Flutter）
- 其他：Firebase推送正常

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 检查发现用的是Firebase的token而非APNS token → 发现token类型混淆
2. 客服确认需要调用updateApnsToken上传APNS token → 确认上报方式
3. 日志显示用户实际上没有登录IM账号 → 发现前置条件未满足
4. APNS token必须先上传到云信才能下发推送 → 确认根本原因
5. 证书环境与代码配置不匹配 → 发现配置问题

**关键发现**：需登录IM账号才能触发APNS token上报，且debug/release需配置不同的apnsCername

## 问题原因

APNS token未上传到云信服务器。客户虽然接了Firebase推送，但APNS token需要通过updateApnsToken方法单独上传。

## 解决方案

1. 在iOS端登录IM后调用NIMIOSSDK的updateApnsToken:方法上报APNS token
2. debug环境需在代码中设置option.apnsCername为开发环境证书名，release环境设置为生产环境证书名（如wepush_prod）
3. 确认控制台对应环境已正确配置对应类型的APNS证书

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
