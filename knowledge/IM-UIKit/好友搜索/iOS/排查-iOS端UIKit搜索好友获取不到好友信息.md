---
track_type: 排查类
sub_type: 使用问题
product: IM-UIKit
feature: 好友搜索
platform: iOS
title: iOS端UIKit搜索好友获取不到好友信息
root_cause: NEFriendUserCache缓存读取时机问题，客户改造源码可能导致缓存写入顺序变化
solution: 1. 检查是否修改了渲染顺序或时机\n2. 确认NEFriendUserCache在首次获取好友列表后写入\n3. 用户信息变更、好友添加、好友变更时会更新缓存\n4. 建议对比原版源码检查改造部分
customers: ['湖南登时互动网络科技有限公司']
source: chat_history
tags: ['搜索好友', 'NEFriendUserCache', '缓存', 'iOS', 'UIKit', 'getFriendList']
created: 2025-01-22
updated: 2026-03-23
---

## 问题：iOS iOS端UIKit搜索好友获取不到好友信息

## 问题详情

**现象**：
iOS端使用UIKit时，通讯录页面有好友但搜索好友页面搜不到。经排查是NEFriendUserCache缓存问题，getFriendList和getFriendListNotInBlocklist方法在特定时机获取不到数据。

## 排查过程

1. 客户反馈搜索好友获取不到好友信息\n2. 确认登录成功且有好友\n3. 测试getContactList可以获取到\n4. 建议用10.3.0源码测试是否复现\n5. 客户测试源码可以获取到\n6. 分析是NEFriendUserCache缓存读取时机问题\n7. 研发确认好友信息首次获取后写入缓存，后续用户信息变更、好友添加、好友变更会更新缓存

## 问题原因

NEFriendUserCache缓存读取时机问题，客户改造源码可能导致缓存写入顺序变化

## 解决方案

1. 检查是否修改了渲染顺序或时机\n2. 确认NEFriendUserCache在首次获取好友列表后写入\n3. 用户信息变更、好友添加、好友变更时会更新缓存\n4. 建议对比原版源码检查改造部分

## 其他触发场景

（合并时在此处追加）
