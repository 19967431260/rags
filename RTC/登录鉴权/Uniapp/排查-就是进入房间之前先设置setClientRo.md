---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 登录鉴权
platform: Uniapp
title: 就是进入房间之前先设置setClientRo
root_cause: ""
solution: "是的，观众是不会触发用户加入房间的回调的，您目前是什么业务场景，要统计观众的人数"
customers: ["VIP云信-雨后生活服务（杭州）"]
source: chat_history
tags: ["回调", "云信", "SDK", "技术支持"]
created: 2025-01-19
updated: 2026-03-20
---

## 问题：Uniapp 就是进入房间之前先设置setClientRo

## 问题详情

**现象**：
就是进入房间之前先设置 setClientRole 为 1的身份， 在进入房间 就不会触发 onUserJoined，远端就无法统计到观众进入， 进行一个数量的展示

## 排查过程

1. 根据会话信息确认问题触发路径并复核关键配置。

## 问题原因

会话中未提供更细根因。

## 解决方案

是的，观众是不会触发用户加入房间的回调的，您目前是什么业务场景，要统计观众的人数
