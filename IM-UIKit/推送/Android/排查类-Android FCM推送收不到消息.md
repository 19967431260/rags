---
track_type: 排查类
sub_type: 集成类
product: IM-UIKit
feature: 推送
platform: Android
title: Android FCM推送收不到消息
root_cause: 推送依赖版本需要与UIKit底层SDK版本匹配
solution: 使用与UIKit底层SDK版本匹配的push依赖：implementation "com.netease.nimlib:push:9.14.2"
customers: ['四川乘洲科技有限公司']
source: chat_history
tags: ['FCM', '推送', 'Android', 'UIKit', '海外', '依赖版本']
created: 2025-01-10
updated: 2026-03-23
---

## 问题：Android FCM推送收不到消息

## 问题详情

**现象**：
海外社交App使用UIKit继承FCM推送后，收不到推送消息。客户使用VPN测试，网络环境正常。

## 排查过程

1. 客户反馈继承FCM后收不到推送
2. 查看日志发现谷歌回执成功(name=projects/testprojectcz/messages/...)
3. 确认客户已开启VPN
4. 建议调整消息优先级
5. 确认push依赖版本与UIKit底层SDK版本一致
6. 客户UIKit版本9.7.0对应IM SDK V9.14.2

## 问题原因

推送依赖版本需要与UIKit底层SDK版本匹配

## 解决方案

使用与UIKit底层SDK版本匹配的push依赖：implementation "com.netease.nimlib:push:9.14.2"

## 其他触发场景

（合并时在此处追加）
