---
track_type: 咨询类
sub_type: 功能实现咨询
product: IM-SDK
feature: ESM模块引入
platform: Uniapp
title: IM SDK集成导致小程序主包过大
root_cause: 完整引入SDK导致包体积过大，需要使用ESM按需引入减小体积。
solution: 使用ESM进行模块引入，截至10.5.0版本，完整导出约550kb，只引入消息与会话功能模块约为400kb。
customers: ['云南城市心网络科技有限公司']
source: chat_history
tags: ['Uniapp', '小程序', 'ESM', '包体积', '模块引入']
created: 2025-01-02
updated: 2026-03-23
---

## 问题：IM SDK集成导致小程序主包过大

## 问题详情

**现象**：
集成NIM SDK进小程序后，主包体积过大导致无法发布。

## 排查过程

1. 客户反馈集成后主包太大发布不了 → 技术支持建议使用ESM模块引入
2. 提供ESM产物体积数据：完整导出550kb，仅消息与会话功能约400kb

## 问题原因

完整引入SDK导致包体积过大，需要使用ESM按需引入减小体积。

## 解决方案

使用ESM进行模块引入，截至10.5.0版本，完整导出约550kb，只引入消息与会话功能模块约为400kb。

## 其他触发场景

（合并时在此处追加）
