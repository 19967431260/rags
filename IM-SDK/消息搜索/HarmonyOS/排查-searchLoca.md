---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 消息搜索
platform: HarmonyOS
title: searchLocalMessages报191001错误
root_cause: 模拟器兼容性问题导致搜索服务初始化失败
solution: 使用真机运行，模拟器存在兼容性问题；需先注册搜索服务并导入search.har包
customers: ["VIP云信-上海素翼科技有限公司"]
source: chat_history
tags: ["searchLocalMessages", "191001", "搜索", "HarmonyOS", "模拟器"]
created: 2025-02-11
updated: 2026-03-20
---

## 问题：HarmonyOS searchLocalMessages报191001错误

## 问题详情

**现象**：
调用searchLocalMessages进行本地消息搜索时返回191001错误

## 排查过程

1. 确认是否注册搜索服务 → 需要registerCustomServices注册
2. 确认search.har包是否导入 → 已导入
3. 验证运行环境 → 模拟器报错，真机正常

## 问题原因

模拟器兼容性问题导致搜索服务初始化失败

## 解决方案

使用真机运行，模拟器存在兼容性问题；需先注册搜索服务并导入search.har包

## 其他触发场景

