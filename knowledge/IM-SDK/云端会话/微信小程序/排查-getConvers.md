---
track_type: 排查类
sub_type: 客户环境问题
product: IM-SDK
feature: 云端会话
platform: 微信小程序
title: getConversationList未拉取到新群聊
root_cause: 需要进一步排查，可能是云端会话同步延迟或其他配置问题。
solution: V10需要在网易云信控制台为应用开通云端会话开关，如已开启仍有问题，需提供完整日志和群ID进一步排查。
customers: ["千寻代售APP沟通群"]
source: chat_history
tags: ["V10", "小程序", "getConversationList", "云端会话", "群聊"]
created: 2025-02-13
updated: 2026-03-20
---

## 问题：微信小程序 getConversationList未拉取到新群聊

## 问题详情

**现象**：
客户使用小程序getConversationList API没有拉取到新创建的群聊。

## 排查过程

1. 客户反馈getConversationList未拉取到新群聊
2. 询问SDK版本，确认是V10
3. 检查云端会话开关是否开启
4. 客户确认已开启
5. 要求提供完整日志和群ID

## 问题原因

需要进一步排查，可能是云端会话同步延迟或其他配置问题。

## 解决方案

V10需要在网易云信控制台为应用开通云端会话开关，如已开启仍有问题，需提供完整日志和群ID进一步排查。

## 其他触发场景
- [微信小程序] getConversationList未拉取到新群聊，来源：['千寻代售APP沟通群']，2026-03-20
- [微信小程序] getConversationList未拉取到新群聊，来源：['千寻代售APP沟通群']，2026-03-20

