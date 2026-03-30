---
track_type: 排查类
sub_type: 集成类
product: IM-UIKit
feature: P2P聊天
platform: iOS
title: 登录后首次进入P2P聊天界面消息重复显示
root_cause: 登录后立即进入ChatViewController，loadData拉取历史记录与onRecvMessage回调时序冲突，导致UI刷新两次
solution: 在ChatViewController的loadData中先清空viewmodel.messages再获取数据，或在收到消息时判断消息是否已存在，避免重复添加
customers: ["VIP云信-广州市点图网络科技有限公司"]
source: chat_history
tags: ["IM-UIKit", "消息重复", "P2P聊天", "iOS", "时序问题"]
created: 2025-02-27
updated: 2026-03-20
---

## 问题：iOS 登录后首次进入P2P聊天界面消息重复显示

## 问题详情

**现象**：
iOS端使用IM UIKit，登录成功后立即push到P2P聊天界面，会出现最新消息重复显示的问题。退出界面再进入则正常。

## 排查过程

1. 复现步骤：用其他账号发消息→启动app→登录IM→block回调中直接push到聊天界面
2. 分析发现登录后直接进页面，先拉取历史记录，后触发onRecvMessage
3. 页面刷新两次导致消息重复

## 问题原因

登录后立即进入ChatViewController，loadData拉取历史记录与onRecvMessage回调时序冲突，导致UI刷新两次

## 解决方案

在ChatViewController的loadData中先清空viewmodel.messages再获取数据，或在收到消息时判断消息是否已存在，避免重复添加

## 其他触发场景
- [iOS] 登录后首次进入P2P聊天界面消息重复显示，来源：['VIP云信-广州市点图网络科技有限公司']，2026-03-20
- [iOS] 登录后首次进入P2P聊天界面消息重复显示，来源：['VIP云信-广州市点图网络科技有限公司']，2026-03-20

