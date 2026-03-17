---
track_type: 排查类
sub_type: 使用问题
product: IM-UIKit
feature: 消息
platform: Uniapp
title: addMsg无法插入自定义消息对象
root_cause: message对象不是SDK接口生成的对象，自己生成的数据无法随意插入本地。
solution: addMsg接口只能插入SDK生成的消息对象。如果要使用抄送数据，需要自行根据抄送数据展示，不能直接插入本地。
tags: ["addMsg", "消息抄送", "本地消息", "UIKit"]
customers: ["厦门亿佳链鑫科技有限公司"]
source: chat_history
created: 2026-02-06
updated: 2026-03-17
---

## 问题：Uniapp addMsg无法插入自定义消息对象

## 问题详情

**现象**：
使用addMsg接口添加消息抄送记录的历史消息，调用后没有添加进去也没有报错。

**环境信息**：
- 平台：Uniapp
- UIKit版本：V9

## 排查过程

**关键发现**：message对象不是SDK接口生成的对象

## 问题原因

message对象不是SDK接口生成的对象，自己生成的数据无法随意插入本地。

## 解决方案

addMsg接口只能插入SDK生成的消息对象。如果要使用抄送数据，需要自行根据抄送数据展示，不能直接插入本地。

## 其他触发场景

