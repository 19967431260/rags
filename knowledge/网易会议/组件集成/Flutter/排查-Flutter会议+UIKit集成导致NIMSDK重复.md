---
track_type: 排查类
sub_type: 集成类
product: 网易会议
feature: 组件集成
platform: Flutter
title: Flutter会议+UIKit集成导致NIMSDK重复
root_cause: Flutter会议组件和UIKit分别引入了不同版本的NIMSDK，导致冲突。
solution: 使用fcs_special版本的neroomkit，指定neroomkit版本为1.31.0+1。呼叫组件和会议都要集成fcs的库（NERtcCallKit/FCS_Special、NERtcCallUIKit/FCS_Special）。
customers: ['海南温蒂']
source: chat_history
tags: ['NIMSDK重复', 'Flutter', 'UIKit', 'fcs_special', '组件集成']
created: 2025-01-21
updated: 2026-03-23
---

## 问题：Flutter Flutter会议+UIKit集成导致NIMSDK重复

## 问题详情

**现象**：
客户集成Flutter版本的网易会议和IM UIKit时，Xcode打包报错Multiple commands produce NIMSDK.framework，发现有两个NIMSDK。

## 排查过程

1. 确认客户同时集成了UIKit和flutter版本的nim_core → 2. 发现nim_core集成的是fcs的NIMSDK → 3. 提供专用demo和版本修改方案

## 问题原因

Flutter会议组件和UIKit分别引入了不同版本的NIMSDK，导致冲突。

## 解决方案

使用fcs_special版本的neroomkit，指定neroomkit版本为1.31.0+1。呼叫组件和会议都要集成fcs的库（NERtcCallKit/FCS_Special、NERtcCallUIKit/FCS_Special）。

## 其他触发场景

（合并时在此处追加）
