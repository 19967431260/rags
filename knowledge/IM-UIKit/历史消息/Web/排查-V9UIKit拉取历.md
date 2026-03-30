---
track_type: 排查类
sub_type: 测试问题
product: IM-UIKit
feature: 历史消息
platform: Web
title: V9UIKit拉取历史消息报错
root_cause: UIKit层V9和V10互通问题，V9和V10在消息回复的实现上存在部分差异导致消息解析不了
solution: 建议各端版本保持一致，iOS端已升级到V10，Web端最好也升级到V10
customers: ["湖南登时互动网络科技有限公司"]
source: chat_history
tags: ["历史消息", "V9", "V10", "消息解析", "版本兼容"]
created: 2025-02-10
updated: 2026-03-20
---

## 问题：Web V9UIKit拉取历史消息报错

## 问题详情

**现象**：
V9版本聊天拉取历史消息报错，res是undefined，且只有这一个群聊有问题，其他群聊正常。

## 排查过程

1. 检查res返回值 → 打印res是undefined
2. 确认问题范围 → 只有这一个群聊有问题
3. 查看日志 → getHistoryMsgActive success有返回结果
4. 客户提供iOS端消息日志分析
5. 发现V9和V10消息回复实现存在差异导致消息解析不了

## 问题原因

UIKit层V9和V10互通问题，V9和V10在消息回复的实现上存在部分差异导致消息解析不了

## 解决方案

建议各端版本保持一致，iOS端已升级到V10，Web端最好也升级到V10

## 其他触发场景
- [Web] V9UIKit拉取历史消息报错，来源：['湖南登时互动网络科技有限公司']，2026-03-20
- [Web] V9UIKit拉取历史消息报错，来源：['湖南登时互动网络科技有限公司']，2026-03-20

