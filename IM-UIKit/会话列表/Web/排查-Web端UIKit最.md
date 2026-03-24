---
track_type: 排查类
sub_type: 使用问题
product: IM-UIKit
feature: 会话列表
platform: Web
title: Web端UIKit最近会话列表不渲染数据问题排查
root_cause: 待进一步排查，初步怀疑UIKit组件渲染问题
solution: 建议下载官方demo代码，更换appkey、accid和token后在测试环境验证是否能复现问题，以确定是组件问题还是集成环境问题。
customers: ["贵州预泊网络科技服务有限公司"]
source: chat_history
tags: ["UIKit", "会话列表", "Web", "im-kit-ui", "渲染问题"]
created: 2025-02-22
updated: 2026-03-20
---

## 问题：Web Web端UIKit最近会话列表不渲染数据问题排查

## 问题详情

**现象**：
客户使用xkit-yx/im-kit-ui的会话组件，NIM连接正常且sessions有数据，但最近会话列表未渲染显示。浏览器控制台无报错，代码回退到稳定版本问题依旧。

## 排查过程

1. 确认问题现象 → 之前会话正常显示，突然不显示；发送新消息后仍不生成会话
2. 检查消息漫游策略 → 会话通过消息生成，漫游消息只保留7天
3. 核实消息发送状态 → 日志显示发送正常，UI更新session也有打印
4. 检查UIKit版本 → 客户使用9.8.6版本
5. 建议对比测试 → 建议用官方demo在相同版本测试复现问题

## 问题原因

待进一步排查，初步怀疑UIKit组件渲染问题

## 解决方案

建议下载官方demo代码，更换appkey、accid和token后在测试环境验证是否能复现问题，以确定是组件问题还是集成环境问题。

## 其他触发场景
- [Web] Web端UIKit最近会话列表不渲染数据问题排查，来源：['贵州预泊网络科技服务有限公司']，2026-03-20
- [Web] Web端UIKit最近会话列表不渲染数据问题排查，来源：['贵州预泊网络科技服务有限公司']，2026-03-20

