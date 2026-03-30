---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 第三方推送
platform: iOS
title: Flutter iOS端APNS推送debug和release证书配置
root_cause: iOS的APNS分为开发环境(sandbox)和生产环境(production)，控制台也需要对应配置。代码中设置的apnsCername必须与当前构建环境匹配：debug build对应开发证书，release build对应生产证书。
solution: 1. debug环境：在代码中设置option.apnsCername为开发证书名称（如wepush_dev）；2. release环境：设置option.apnsCername为生产证书名称（如wepush_prod）；3. 控制台同时创建两个证书，分别对应开发和生产环境；4. 如果release包用生产证书仍报BadDeviceToken，用三方工具直接推送验证token是否有效。
customers: ["voiceverse.org"]
source: chat_history
tags: ["APNS", "push", "apnsCername", "iOS", "Flutter", "debug", "release"]
created: 2025-08-14
updated: 2025-08-14
---

## 问题：iOS Flutter iOS端APNS推送debug和release证书配置

## 问题详情

**现象**：
iOS端Flutter集成云信SDK，接入APNS离线推送。debug模式测试正常，但release模式无法收到推送。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：iOS（Flutter）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客户反馈release包收不到推送，debug包正常 → 确认环境差异
2. 客服检查发现release包上报的是wepush_dev（开发环境）证书 → 发现配置问题
3. 根因：release包代码中配置的apnsCername是开发环境证书名 → 定位根因

**关键发现**：iOS的APNS有开发环境和生产环境区分，debug和release必须对应不同的证书配置

## 问题原因

iOS的APNS分为开发环境(sandbox)和生产环境(production)，控制台也需要对应配置。代码中设置的apnsCername必须与当前构建环境匹配：debug build对应开发证书，release build对应生产证书。

## 解决方案

1. debug环境：在代码中设置option.apnsCername为开发证书名称（如wepush_dev）
2. release环境：设置option.apnsCername为生产证书名称（如wepush_prod）
3. 控制台同时创建两个证书，分别对应开发和生产环境
4. 如果release包用生产证书仍报BadDeviceToken，用三方工具直接推送验证token是否有效

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
