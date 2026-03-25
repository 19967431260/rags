---
track_type: 排查类
sub_type: 集成类
product: IM-UIKit
feature: UI组件
platform: Web
title: Web UIKit会话列表组件不显示
root_cause: SDK版本与UIKit版本不兼容导致会话列表组件无法正常渲染
solution: 升级SDK到10.8.10，UIKit升级到10.7.1版本解决兼容性问题
customers: ["河南潮生网络科技有限公司"]
source: chat_history
tags: ["UIKit", "会话列表", "版本兼容", "Web", "V10"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：Web UIKit会话列表组件不显示

## 问题详情

**现象**：
客户使用Web UIKit demo，初始化成功后日志显示能收到会话数据，但界面不显示会话列表。使用SDK版本10.8.0，UIKit版本10.6.0。

**环境信息**：
- 平台：Web

## 排查过程

1. 检查SDK和UIKit版本 → SDK 10.8.0，UIKit 10.6.0
2. 检查初始化配置 → 确认appkey、accid、token正确
3. 检查网络请求 → 服务器日志显示请求成功
4. 检查组件引入 → 确认已引入会话列表组件
5. 升级版本 → 升级SDK到10.8.10，UIKit到10.7.1后解决

## 问题原因

SDK版本与UIKit版本不兼容导致会话列表组件无法正常渲染

## 解决方案

升级SDK到10.8.10，UIKit升级到10.7.1版本解决兼容性问题

## 其他触发场景

（无）
