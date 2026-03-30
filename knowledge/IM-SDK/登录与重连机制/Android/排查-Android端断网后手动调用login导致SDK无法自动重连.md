---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 登录与重连机制
platform: Android
title: Android端断网后手动调用login导致SDK无法自动重连
root_cause: 业务层在observeOnlineStatus回调中手动调用login，干扰了SDK的自动重连机制。SDK的自动重连会在断网恢复后自动发起，但手动login会覆盖此行为。
solution: 1. 参考最佳实践文档：https://doc.yunxin.163.com/messaging/guide/DE1NjMxNjU?platform=android\n2. 如需手动登录，建议先调用logout再login\n3. 或设计重试机制：间隔1秒尝试3次，都失败再返回登录界面
customers: ['海岛游']
source: chat_history
tags: ['415', 'login', '自动重连', 'observeOnlineStatus', '断网重连']
created: 2025-01-08
updated: 2026-03-23
---

## 问题：Android Android端断网后手动调用login导致SDK无法自动重连

## 问题详情

**现象**：
用户登录云信成功后，断网恢复时SDK无法自动重连。原因是业务层在observeOnlineStatus回调中手动调用了login方法，与SDK的自动重连机制冲突。日志显示手动登录返回415错误，切回前台后SDK因已手动login过而不再自动重连。

## 排查过程

1. 查看日志确认问题时间点（01-08 11:20:04登录成功，11:25:45出现onFailed:415）\n2. 分析日志发现11:26:45 app切后台，11:26:50发起手动登录失败\n3. 检查网络状态：SDK尝试ping不同link地址均失败，说明网络受限\n4. 确认11:29:53切回前台，但因已手动login，SDK不会自动重连\n5. 最终11:41:02再次login成功

## 问题原因

业务层在observeOnlineStatus回调中手动调用login，干扰了SDK的自动重连机制。SDK的自动重连会在断网恢复后自动发起，但手动login会覆盖此行为。

## 解决方案

1. 参考最佳实践文档：https://doc.yunxin.163.com/messaging/guide/DE1NjMxNjU?platform=android\n2. 如需手动登录，建议先调用logout再login\n3. 或设计重试机制：间隔1秒尝试3次，都失败再返回登录界面

## 其他触发场景

（合并时在此处追加）
