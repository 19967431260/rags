---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 好友管理
platform: HarmonyOS
title: 鸿蒙端getAddApplicationList查询不到历史好友申请
root_cause: 好友申请通知属于系统通知，只存储在本地，不存漫游。如果卸载重装、切换设备或删除过，本地历史数据就会丢失。
solution: getAddApplicationList查询的是本地保存的好友申请通知，不支持漫游。如卸载、切换设备或删除过，历史数据将无法恢复。接口支持分页查询。
customers: ['联通在线信息科技有限公司']
source: chat_history
tags: ['HarmonyOS', '好友申请', 'getAddApplicationList', '系统通知', '本地存储']
created: 2025-01-09
updated: 2026-03-23
---

## 问题：HarmonyOS 鸿蒙端getAddApplicationList查询不到历史好友申请

## 问题详情

**现象**：
HarmonyOS调用getAddApplicationList接口查询好友申请列表没有返回信息，只能查到当天数据。

## 排查过程

1. 确认是否使用apidemo测试 → demo正常但客户项目不行
2. 检查是否删除过好友申请通知 → 客户确认未调用clearAllAddApplication/deleteAddApplication
3. 确认是否卸载重装或切换设备 → 系统通知只存本地，卸载/切换设备后历史数据丢失

## 问题原因

好友申请通知属于系统通知，只存储在本地，不存漫游。如果卸载重装、切换设备或删除过，本地历史数据就会丢失。

## 解决方案

getAddApplicationList查询的是本地保存的好友申请通知，不支持漫游。如卸载、切换设备或删除过，历史数据将无法恢复。接口支持分页查询。

## 其他触发场景

（合并时在此处追加）
