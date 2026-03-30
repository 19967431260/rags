---
track_type: 排查类
sub_type: 使用问题
product: IM-UIKit
feature: 会话列表
platform: iOS
title: iOS自定义ConversationListCell头像加载失败
root_cause: VC里的UI设置有问题
solution: 检查自定义cell中的头像设置逻辑，确保与父类ConversationListCell一致
customers: ['北京兔玩在线']
source: chat_history
tags: ['自定义cell', '头像加载', 'ConversationListCell', 'iOS', 'UIKit']
created: 2025-09-23
updated: 2026-03-25
---

## 问题：iOS iOS自定义ConversationListCell头像加载失败

## 问题详情

**现象**：
客户继承ConversationListCell自定义cell后，头像加载出现问题，仅部分头像能加载成功。

## 解决方案

检查自定义cell中的头像设置逻辑，确保与父类ConversationListCell一致
