---
track_type: 咨询类
sub_type: 接口用法咨询
product: IM-SDK
feature: 消息发送
platform: iOS
title: sendMessage回调与didCompleteWithError区别
root_cause: 
solution: send方法的回调是本地回调，本地参数校验不过时返回。didCompleteWithError是服务器返回的错误（如403）。本地回调成功的基础上才会有didCompleteWithError的成功回调。
customers: ['杭州晶达网络科技有限公司']
source: chat_history
tags: ['sendMessage', 'didCompleteWithError', '回调', '消息发送']
created: 2025-01-23
updated: 2026-03-23
---

## 问题：sendMessage回调与didCompleteWithError区别

## 问题详情

**现象**：
客户咨询发送消息时send方法的回调和didCompleteWithError的区别，以及如何正确处理。

## 排查过程



## 问题原因



## 解决方案

send方法的回调是本地回调，本地参数校验不过时返回。didCompleteWithError是服务器返回的错误（如403）。本地回调成功的基础上才会有didCompleteWithError的成功回调。

## 其他触发场景

（合并时在此处追加）
