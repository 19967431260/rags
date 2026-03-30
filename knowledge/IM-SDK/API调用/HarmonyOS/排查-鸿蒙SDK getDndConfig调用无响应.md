---
track_type: 排查类
sub_type: 测试问题
product: IM-SDK
feature: API调用
platform: HarmonyOS
title: 鸿蒙SDK getDndConfig调用无响应
root_cause: SDK bug：accid包含@、.、-等特殊字符时，getDndConfig接口参数校验失败
solution: SDK bug，计划在10.8.0版本修复；临时方案避免accid包含特殊字符
customers: ['台州浩瀚网络']
source: chat_history
tags: ['HarmonyOS', 'getDndConfig', 'storeId', '参数错误', 'SDK bug']
created: 2025-01-10
updated: 2026-03-23
---

## 问题：HarmonyOS 鸿蒙SDK getDndConfig调用无响应

## 问题详情

**现象**：
客户调用getDndConfig方法时没有任何响应，不打印日志也不进入回调，直接跳出方法。

## 排查过程

1. 客户反馈getDndConfig调用无响应，不打印日志
2. 建议客户使用异步调用方式
3. 客户提供代码示例，确认写法正确
4. 建议客户打印error查看
5. 客户打印error为空对象
6. 建议客户使用官方demo测试
7. 客户测试后捕获到错误：Parameter error:storeId must be string
8. 研发确认是SDK问题：accid包含@、.、-字符时会出现此问题
9. 计划在10.8.0版本修复

## 问题原因

SDK bug：accid包含@、.、-等特殊字符时，getDndConfig接口参数校验失败

## 解决方案

SDK bug，计划在10.8.0版本修复；临时方案避免accid包含特殊字符

## 其他触发场景

（合并时在此处追加）
