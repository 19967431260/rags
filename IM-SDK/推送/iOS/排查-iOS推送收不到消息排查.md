---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 推送
platform: iOS
title: iOS推送收不到消息排查
root_cause: vivo推送category与classification配置不匹配；华为推送style=1时缺少big_title和big_body字段
solution: 按各厂商官方文档配置正确的payload字段，vivo需确保category与classification对应，华为style=1时必须包含big_title和big_body
customers: ["万象森森(上海)科技有限公司"]
source: chat_history
tags: ["推送", "iOS", "vivo", "华为", "离线推送"]
created: 2025-06-26
updated: 2025-03-23
---

## 问题：iOS iOS推送收不到消息排查

## 问题详情

**现象**：
App通过SDK配置成功注册厂商推送服务后，退出APP或杀掉进程后无法接收推送消息。

**环境信息**：
- 涉及厂商：vivo、华为

## 排查过程

1. 检查vivo推送返回错误：category与classification不对应 → 2. 检查华为推送返回错误：style为1时需要big_title和big_body → 3. 确认payload配置符合各厂商要求

## 问题原因

vivo推送category与classification配置不匹配；华为推送style=1时缺少big_title和big_body字段

## 解决方案

按各厂商官方文档配置正确的payload字段，vivo需确保category与classification对应，华为style=1时必须包含big_title和big_body
