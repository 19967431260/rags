---
track_type: 排查类
sub_type: 使用问题
product: IM-UIKit
feature: 聊天记录
platform: iOS
title: iOS清空本地聊天记录后页面未刷新
root_cause: 清空操作后页面缓存未刷新，需要手动清理viewmodel.messages并reload tableview。
solution: 两种处理方式：1) 清空后返回上上个页面，不要返回到会话详情页；2) 返回后手动清空viewmodel.messages，然后调用reload刷新tableview。
customers: ['VIP云信-沈阳捷影']
source: chat_history
tags: ['清空聊天记录', '页面刷新', 'UIKit', 'iOS', 'V10']
created: 2025-02-20
updated: 2026-03-23
---

## 问题：iOS iOS清空本地聊天记录后页面未刷新

## 问题详情

**现象**：
iOS V10 UIKit在群聊管理中清空本地聊天记录后，返回聊天页面数据仍然存在，需要退出到会话列表再进入才清空。

**环境信息**：
- 平台：iOS
- 产品：IM-UIKit

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

（从会话提取排查过程）

## 问题原因

清空操作后页面缓存未刷新，需要手动清理viewmodel.messages并reload tableview。

## 解决方案

两种处理方式：1) 清空后返回上上个页面，不要返回到会话详情页；2) 返回后手动清空viewmodel.messages，然后调用reload刷新tableview。

## 其他触发场景

（合并时在此处追加：`- [iOS] iOS清空本地聊天记录后页面未刷新，来源：['VIP云信-沈阳捷影']，2026-03-23`）
