---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 登录连接
platform: 微信小程序
title: 微信小程序获取历史消息报illegal state错误
root_cause: 控制台未开启多端登录配置，同一账号在其他端登录时会将当前端踢下线（disconnect due to kicked），离线状态下调用获取历史消息接口失败。
solution: 在控制台开启多端登录配置，参考文档：https://doc.yunxin.163.com/messaging2/guide/DUyNjI2MjQ?platform=client#策略三各端均可以同时登录在线。可配置各端均可同时在线或自定义互踢策略。
customers: ["上海复醒网络科技有限公司"]
source: chat_history
tags: ["illegal state", "多端登录", "互踢", "getHistoryMsgActive", "微信小程序"]
created: 2026-02-11
updated: 2026-03-17
---

## 问题：微信小程序 微信小程序获取历史消息报illegal state错误

## 问题详情

**现象**：
微信小程序端调用getHistoryMsgActive获取历史消息时报错"V2NIMError: illegal state"，错误发生在validateConversationId环节。登录成功后在聊天页面停留一段时间后出现，刷新页面后恢复正常。

**环境信息**：
- 平台：微信小程序

## 排查过程

1. 检查登录状态 → 登录显示成功
2. 查看错误堆栈 → 错误发生在validateConversationId，提示illegal state
3. 分析日志 → 发现是被踢下线导致，原因是多端登录互踢

**关键发现**：后台未开启多端登录配置，其他同事登录同一账号导致当前端被踢下线，离线后调用接口失败。

## 问题原因

控制台未开启多端登录配置，同一账号在其他端登录时会将当前端踢下线（disconnect due to kicked），离线状态下调用获取历史消息接口失败。

## 解决方案

在控制台开启多端登录配置，参考文档：https://doc.yunxin.163.com/messaging2/guide/DUyNjI2MjQ?platform=client#策略三各端均可以同时登录在线。可配置各端均可同时在线或自定义互踢策略。

## 其他触发场景
