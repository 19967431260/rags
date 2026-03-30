---
track_type: 排查类
sub_type: 使用问题
product: IM-UIKit
feature: 用户资料
platform: Android
title: 聊天窗口显示账号ID而不是name字段
root_cause: UIKit默认使用云信用户资料，客户传入的name字段未正确更新到云信用户资料
solution: 自定义UI时显示用户昵称有两种方式：1. 通过ContactKit的getUserListFromCloud接口查询用户资料获取昵称；2. 发送消息时将头像和昵称带到消息扩展字段，UI展示时优先使用扩展字段的数据。
customers: ['深圳市希楠电子科技有限公司']
source: chat_history
tags: ['IM-UIKit', 'Android', '用户昵称', 'name', '扩展字段', 'getUserListFromCloud']
created: 2025-01-23
updated: 2026-03-23
---

## 问题：聊天窗口显示账号ID而不是name字段

## 问题详情

**现象**：
客户反馈聊天窗口中显示的是账号ID而不是传入的name字段，希望显示用户昵称。

## 排查过程

1. 客户反馈聊天窗口显示账号ID而非name
2. 技术支持确认demo默认展示name
3. 客户反馈头像和名字已传给云信但不更新
4. 建议通过ContactKit的getUserListFromCloud查询昵称
5. 或发消息时将头像带到扩展字段，UI展示时用扩展字段的头像

## 问题原因

UIKit默认使用云信用户资料，客户传入的name字段未正确更新到云信用户资料

## 解决方案

自定义UI时显示用户昵称有两种方式：1. 通过ContactKit的getUserListFromCloud接口查询用户资料获取昵称；2. 发送消息时将头像和昵称带到消息扩展字段，UI展示时优先使用扩展字段的数据。

## 其他触发场景

（合并时在此处追加）
