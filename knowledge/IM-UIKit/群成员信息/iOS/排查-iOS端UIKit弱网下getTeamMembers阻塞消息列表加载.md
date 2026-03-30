---
track_type: 排查类
sub_type: 使用问题
product: IM-UIKit
feature: 群成员信息
platform: iOS
title: iOS端UIKit弱网下getTeamMembers阻塞消息列表加载
root_cause: getTeamMembers方法在弱网环境下等待网络请求返回，阻塞了消息列表渲染
solution: 1. 业务层检测弱网情况，弱网时跳过该请求\n2. 添加全局参数控制是否请求群成员信息\n3. 等网络恢复后再加载群成员信息展示用户名\n4. 或牺牲群成员数据信息先不展示，仅展示accid
customers: ['湖南登时互动网络科技有限公司']
source: chat_history
tags: ['getTeamMembers', '弱网', '消息列表', '群聊', 'iOS', '阻塞']
created: 2025-01-02
updated: 2026-03-23
---

## 问题：iOS iOS端UIKit弱网下getTeamMembers阻塞消息列表加载

## 问题详情

**现象**：
iOS端在弱网环境下，进入群聊时消息列表加载很慢。经排查是getTeamMembers方法会等待网络请求返回，阻塞了UI渲染。该方法用于预加载群成员信息以展示系统通知中的用户名。

## 排查过程

1. 客户反馈弱网环境下消息列表很难加载\n2. 提供视频演示问题\n3. 确认使用demo测试也有同样问题\n4. 建议升级NIMSDK_LITE到10.7.0\n5. 升级后私聊改善但群聊仍卡在getTeamMembers\n6. 分析该方法用于解析通知消息时获取被操作群成员信息

## 问题原因

getTeamMembers方法在弱网环境下等待网络请求返回，阻塞了消息列表渲染

## 解决方案

1. 业务层检测弱网情况，弱网时跳过该请求\n2. 添加全局参数控制是否请求群成员信息\n3. 等网络恢复后再加载群成员信息展示用户名\n4. 或牺牲群成员数据信息先不展示，仅展示accid

## 其他触发场景

（合并时在此处追加）
