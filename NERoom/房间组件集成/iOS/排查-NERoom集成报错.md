---
track_type: 排查类
sub_type: 集成类
product: NERoom
feature: 房间组件集成
platform: iOS
title: NERoom集成报错Symbol not found NIMQChatGetServersByPageParam
root_cause: 集成NERoom时缺少NIMSDK/QChat模块依赖
solution: 在Podfile中添加pod 'NIMSDK/QChat' 10.6.0依赖
customers: ["VIP云信-广州圣女果"]
source: chat_history
tags: ["NERoom", "QChat", "Symbol not found", "dyld", "iOS"]
created: 2025-02-08
updated: 2026-03-20
---

## 问题：iOS NERoom集成报错Symbol not found NIMQChatGetServersByPageParam

## 问题详情

**现象**：
iOS端集成NERoom SDK时出现dyld报错，提示找不到NIMQChatGetServersByPageParam符号，客户同时集成了QChat功能。

## 排查过程

1. 检查Podfile.lock中的依赖项
2. 发现同时集成NIMSDK和QChat相关功能
3. 缺少QChat模块依赖

## 问题原因

集成NERoom时缺少NIMSDK/QChat模块依赖

## 解决方案

在Podfile中添加pod 'NIMSDK/QChat' 10.6.0依赖

## 其他触发场景
- [iOS] NERoom集成报错Symbol not found NIMQChatGetServersByPageParam，来源：['VIP云信-广州圣女果']，2026-03-20
- [iOS] NERoom集成报错Symbol not found NIMQChatGetServersByPageParam，来源：['VIP云信-广州圣女果']，2026-03-20

