---
track_type: 排查类
sub_type: 使用问题
product: IM-UIKit
feature: 消息列表
platform: Android
title: 消息列表滑动报NullPointerException
root_cause: 消息列表数据获取失败时返回null，addAll方法未做空值判断
solution: 在ChatMessageAdapter.appendMessages方法中对addAll参数增加null判断，避免空指针异常。修改代码：if (messageList != null && messages != null) { messageList.addAll(messages); }
customers: ['深圳市希楠电子科技有限公司']
source: chat_history
tags: ['IM-UIKit', 'Android', 'NullPointerException', 'addAll', '消息列表']
created: 2025-01-23
updated: 2026-03-23
---

## 问题：消息列表滑动报NullPointerException

## 问题详情

**现象**：
客户在使用IM V9 Android UIKit时，发送图片后界面不显示，滑动消息列表时报空指针异常导致闪退。

## 排查过程

1. 客户反馈发送图片后界面不显示
2. 滑动消息列表时报错：Attempt to invoke interface method on a null object reference
3. 查看堆栈发现是addAll方法传入null参数
4. 检查代码发现onListFetchFailed中messageFetchResult.setData(null)
5. 建议对addAll增加null判断

## 问题原因

消息列表数据获取失败时返回null，addAll方法未做空值判断

## 解决方案

在ChatMessageAdapter.appendMessages方法中对addAll参数增加null判断，避免空指针异常。修改代码：if (messageList != null && messages != null) { messageList.addAll(messages); }

## 其他触发场景

（合并时在此处追加）
