---
track_type: 排查类
sub_type: 集成类
product: IM-UIKit
feature: UI组件
platform: Flutter
title: netease_roomkit_interface版本冲突
root_cause: Flutter默认拉取netease_roomkit_interface高版本，与netease_roomkit版本不兼容
solution: 在pubspec.yaml中显式指定netease_roomkit_interface版本号与netease_roomkit保持一致
customers: ["海南温蒂科技有限公司"]
source: chat_history
tags: ["Flutter", "版本冲突", "netease_roomkit", "UIKit"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：netease_roomkit_interface版本冲突

## 问题详情

**现象**：
客户集成Flutter UIKit时遇到版本冲突，netease_roomkit和netease_roomkit_interface版本不匹配。

**环境信息**：
- 平台：Flutter

## 排查过程

1. 检查依赖版本 → netease_roomkit 1.28.1，netease_roomkit_interface被默认拉到高版本
2. 指定版本号 → 在pubspec.yaml中指定netease_roomkit_interface: 1.28.0
3. 重新clean和运行 → 问题解决

## 问题原因

Flutter默认拉取netease_roomkit_interface高版本，与netease_roomkit版本不兼容

## 解决方案

在pubspec.yaml中显式指定netease_roomkit_interface版本号与netease_roomkit保持一致

## 其他触发场景

（无）
