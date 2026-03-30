---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 收藏
platform: Flutter
title: Flutter端收藏列表查询返回191004错误
root_cause: 1. NIMCollectionOption的limit参数需要大于0；2. NIMCollection的collectionType（收藏类型）必须大于0，默认为0是无效值。Flutter UIKit组件封装问题导致传了0。
solution: 1. 直接使用SDK接口时：NIMCollectionOption的limit参数设置为大于0的值（如100）\n2. NIMCollection的collectionType字段必须设置大于0的值（自定义收藏类型），默认0表示无效\n3. 如果没有多种收藏类型需求，无脑设置为1即可，查询时也用1作为type条件
customers: ["东莞市仁众丽科技有限公司"]
source: chat_history
tags: ["191004","getCollectionListByOption","collectionType","Flutter"]
created: 2025-08-15
updated: 2026-03-26
---

## 问题：Flutter Flutter端收藏列表查询返回191004错误

## 问题详情

**现象**：
Flutter端调用getCollectionListByOption接口返回191004错误（参数错误）。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 拉取日志分析 → 参数错误
2. 确认错误原因 → NIMCollectionOption的limit参数为0
3. 确认SDK要求 → limit必须大于0
4. 进一步确认 → NIMCollection的collectionType也必须大于0
5. 确认为组件封装问题：Flutter UIKit组件在创建收藏时collectionType传了默认值0

**关键发现**：NIMCollectionOption的limit参数需要大于0；NIMCollection的collectionType（收藏类型）必须大于0，默认为0是无效值。Flutter UIKit组件封装问题导致传了0。

## 问题原因

NIMCollectionOption的limit参数需要大于0；NIMCollection的collectionType（收藏类型）必须大于0，默认为0是无效值。Flutter UIKit组件封装问题导致传了0。

## 解决方案

1. 直接使用SDK接口时：NIMCollectionOption的limit参数设置为大于0的值（如100）
2. NIMCollection的collectionType字段必须设置大于0的值（自定义收藏类型），默认0表示无效
3. 如果没有多种收藏类型需求，无脑设置为1即可，查询时也用1作为type条件

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
