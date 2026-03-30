---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 群组管理
platform: Server
title: V10更新群组消息报internal server error
root_cause: 传入的configuration参数为null导致空指针错误。
solution: 为null的参数都不传，只传有值的前三个参数即可，传空会报空指针错误。
customers: ['海南无限链科技有限公司']
source: chat_history
tags: ['V10', '更新群组', 'internal server error', '空指针', 'configuration']
created: 2025-01-02
updated: 2026-03-23
---

## 问题：V10更新群组消息报internal server error

## 问题详情

**现象**：
调用V10更新群组消息接口返回internal server error(500)，之前可以正常调用成功。

## 排查过程

1. 确认是本地报错未到达服务端；2. 客户提供完整传参截图；3. 发现configuration参数为null。

## 问题原因

传入的configuration参数为null导致空指针错误。

## 解决方案

为null的参数都不传，只传有值的前三个参数即可，传空会报空指针错误。

## 其他触发场景

（合并时在此处追加）
