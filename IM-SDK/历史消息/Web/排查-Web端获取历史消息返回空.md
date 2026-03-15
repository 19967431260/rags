---
track_type: 排查类
sub_type: 客户开发能力
product: IM-SDK
feature: 历史消息
platform: Web
title: Web端获取历史消息返回空
root_cause: 获取历史消息接口参数配置错误
solution: 检查getHistoryMsgs接口参数，确保sessionId、limit等参数正确。参考文档：https://doc.yunxin.163.com/messaging2/guide/jgyMzYwMzI?platform=web
customers: ["云信-北京中科金财科技股份有限公司-dx"]
source: chat_history
tags: ['Web', '历史消息', 'getHistoryMsgs', '参数配置']
created: 2026-02-14
updated: 2026-03-15
---

## 问题：Web Web端获取历史消息返回空

## 问题详情

**现象**：
Web端调用获取历史消息接口，返回空数组，无法获取到历史消息。

## 排查过程

1. 检查接口调用 → 返回空
2. 检查参数配置 → 参数错误
**关键发现**：参数配置错误

## 问题原因

获取历史消息接口参数配置错误

## 解决方案

检查getHistoryMsgs接口参数，确保sessionId、limit等参数正确。参考文档：https://doc.yunxin.163.com/messaging2/guide/jgyMzYwMzI?platform=web
