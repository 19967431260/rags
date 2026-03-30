---
track_type: 排查类
sub_type: 集成类
product: 呼叫组件
feature: 组件集成
platform: iOS
title: 呼叫组件NOS_Special与FCS_Special版本选择
root_cause: nim_core集成的是fcs的NIMSDK，而呼叫组件集成的是NOS_Special版本，导致引入两个NIMSDK。
solution: 将pod依赖从NERtcCallKit/NOS_Special改为NERtcCallKit/FCS_Special，NERtcCallUIKit/NOS_Special改为NERtcCallUIKit/FCS_Special。
customers: ['海南温蒂']
source: chat_history
tags: ['NOS_Special', 'FCS_Special', '呼叫组件', 'NIMSDK冲突', 'pod']
created: 2025-01-22
updated: 2026-03-23
---

## 问题：iOS 呼叫组件NOS_Special与FCS_Special版本选择

## 问题详情

**现象**：
客户集成NERtcCallKit/NOS_Special和NERtcCallUIKit/NOS_Special时，与flutter nim_core冲突。

## 排查过程

1. 确认nim_core集成的是fcs的NIMSDK → 2. 建议呼叫组件和会议都要集成fcs的库 → 3. 修改pod依赖后解决

## 问题原因

nim_core集成的是fcs的NIMSDK，而呼叫组件集成的是NOS_Special版本，导致引入两个NIMSDK。

## 解决方案

将pod依赖从NERtcCallKit/NOS_Special改为NERtcCallKit/FCS_Special，NERtcCallUIKit/NOS_Special改为NERtcCallUIKit/FCS_Special。

## 其他触发场景

（合并时在此处追加）
