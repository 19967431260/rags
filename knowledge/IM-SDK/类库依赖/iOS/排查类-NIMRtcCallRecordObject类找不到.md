---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 类库依赖
platform: iOS
title: NIMRtcCallRecordObject类找不到
root_cause: Podfile中单独指定了NIM SDK版本，导致类库不完整
solution: 注释掉单独依赖的NIM SDK版本，清理缓存后重新pod install
customers: ['广州群市网络科技有限公司']
source: chat_history
tags: ['IM V9', 'iOS', 'NIMRtcCallRecordObject', 'pod', '类库依赖']
created: 2025-01-06
updated: 2026-03-23
---

## 问题：NIMRtcCallRecordObject类找不到

## 问题详情

**现象**：
客户iOS开发中需要导入NIMRtcCallRecordObject类，但找不到对应的库。

## 排查过程

1. 客户反馈找不到NIMRtcCallRecordObject类
2. 检查发现客户单独依赖了特定版本的NIM SDK
3. 建议注释掉单独依赖，清理缓存重新pod install

## 问题原因

Podfile中单独指定了NIM SDK版本，导致类库不完整

## 解决方案

注释掉单独依赖的NIM SDK版本，清理缓存后重新pod install

## 其他触发场景

（合并时在此处追加）
