---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 登录鉴权
platform: 通用
title: https://ysf.nosdn.127.net
root_cause: 会话中表现为配置或接口使用不一致导致。
solution: 这个就是之前说的，没登录的情况下调用SDK接口返回的，有完整的用户日志吗
customers: ["VIP云信-贵州指趣"]
source: chat_history
tags: ["登录", "回调", "云信", "技术支持", "历史会话"]
created: 2025-01-02
updated: 2026-03-20
---

## 问题：通用 https://ysf.nosdn.127.net

## 问题详情

https://ysf.nosdn.127.net/ce2cb65dd408467ba55b767fd0018da0.jpg?download=ce2cb65dd408467ba55b767fd0018da0.jpg；@潘广强 这个能看出来是什么问题么？；这个就是之前说的，没登录的情况下调用SDK接口返回的，有完整的用户日志吗；或者这个用户的accid提供一下，我们尝试拉取日志看看；tsy_11133371

## 排查过程

1. 根据会话记录核对配置与日志；2. 对关键接口与参数进行逐项验证。

## 问题原因

会话中表现为配置或接口使用不一致导致。

## 解决方案

这个就是之前说的，没登录的情况下调用SDK接口返回的，有完整的用户日志吗

## 其他触发场景
