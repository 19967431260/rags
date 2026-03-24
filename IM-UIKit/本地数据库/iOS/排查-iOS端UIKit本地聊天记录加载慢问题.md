---
track_type: 排查类
sub_type: 使用问题
product: IM-UIKit
feature: 本地数据库
platform: iOS
title: iOS端UIKit本地聊天记录加载慢问题
root_cause: SDK版本过低导致本地数据库读取性能问题
solution: 1. 升级NIMSDK_LITE到10.7.0版本\n2. 将所有Kit依赖改为NOS_Special版本，如：pod 'NEChatKit/NOS_Special', '10.3.0'\n3. 删除pod lock文件，重新pod install\n4. 源码库的podspec文件中用到Kit相关库也要改成NOS_Special版本
customers: ['湖南登时互动网络科技有限公司']
source: chat_history
tags: ['iOS', 'UIKit', '本地数据库', '加载慢', 'NIMSDK_LITE', '10.7.0']
created: 2024-12-31
updated: 2026-03-23
---

## 问题：iOS iOS端UIKit本地聊天记录加载慢问题

## 问题详情

**现象**：
iOS端使用IM V10 UIKit时，聊天记录加载很卡，每次进入都要重新拉取。经排查需要升级NIMSDK_LITE到10.7.0版本解决性能问题。

## 排查过程

1. 客户反馈本地聊天记录不能保存，每次都要单独拉取\n2. 确认使用iOS原生开发，UIKit默认从本地数据库取数据\n3. 客户反馈拉取很卡\n4. 建议升级NIMSDK_LITE到10.7.0\n5. 升级后需要将所有Kit依赖改为NOS_Special版本

## 问题原因

SDK版本过低导致本地数据库读取性能问题

## 解决方案

1. 升级NIMSDK_LITE到10.7.0版本\n2. 将所有Kit依赖改为NOS_Special版本，如：pod 'NEChatKit/NOS_Special', '10.3.0'\n3. 删除pod lock文件，重新pod install\n4. 源码库的podspec文件中用到Kit相关库也要改成NOS_Special版本

## 其他触发场景

（合并时在此处追加）
