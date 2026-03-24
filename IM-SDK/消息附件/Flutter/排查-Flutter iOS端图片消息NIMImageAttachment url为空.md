---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息附件
platform: Flutter
title: Flutter iOS端图片消息NIMImageAttachment url为空
root_cause: 低版本nim_core在iOS端存在附件url获取问题，1.7.8及以上版本已修复
solution: 升级nim_core到1.7.8或更高版本；若遇到依赖冲突使用dependency_overrides解决；Android端需要JDK 17
customers: ['医惠科技有限公司']
source: chat_history
tags: ['Flutter', 'iOS', '图片消息', 'NIMImageAttachment', 'url为空', 'nim_core']
created: 2025-01-07
updated: 2026-03-23
---

## 问题：Flutter Flutter iOS端图片消息NIMImageAttachment url为空

## 问题详情

**现象**：
Flutter端使用nim_core发送图片消息后，点击查看大图时NIMImageAttachment的url字段为空，退出聊天页面重新进入后才能获取到值。安卓端正常，iOS端只有thumbPath，其他字段为空。

## 排查过程

1. 客户反馈iOS端图片消息url为空，安卓正常
2. 建议监听observeMsgStatus，成功时刷新内存消息
3. 客户反馈Flutter使用NimCore.instance.messageService.onMessageStatus.listen监听到成功，但返回的NIMMessage中NIMImageAttachment的url仍为空
4. 确认客户使用nim_core: ^1.1.0版本
5. 建议升级到1.8.2版本，优化过附件问题
6. 客户询问1.7.2是否有解决，回复1.7.2没有，建议1.7.8
7. 客户升级后遇到yunxin_alog库版本冲突
8. 建议在pubspec.yaml使用dependency_overrides指定yunxin_alog到最高版本，同时建议nertc_core升级到5.5.101
8. 客户升级1.8.2后Android编译报错，建议升级到1.8.3
9. 客户反馈1.8.3仍报错，建议清理缓存、重新gradle
10. 客户询问JDK版本，回复需要JDK 17
11. 客户降级回1.1.0后报错，建议flutter clean
12. 最终客户使用1.7.8版本，iOS图片问题已解决，Android可正常编译

## 问题原因

低版本nim_core在iOS端存在附件url获取问题，1.7.8及以上版本已修复

## 解决方案

升级nim_core到1.7.8或更高版本；若遇到依赖冲突使用dependency_overrides解决；Android端需要JDK 17

## 其他触发场景

（合并时在此处追加）
