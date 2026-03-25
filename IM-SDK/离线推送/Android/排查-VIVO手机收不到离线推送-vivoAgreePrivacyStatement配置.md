---
track_type: "排查类"
sub_type: "使用问题"
product: "IM-SDK"
feature: "离线推送"
platform: "Android"
title: "VIVO手机收不到离线推送-vivoAgreePrivacyStatement配置"
root_cause: "vivo推送SDK需要隐私合规处理，vivoAgreePrivacyStatement默认为false，需要在用户同意隐私政策后设置为true，并且IM登录需要在同意隐私政策之后执行。"
solution: "1. 确保在用户同意隐私政策后将vivoAgreePrivacyStatement设置为true
2. 用户未同意隐私政策前可以先配置SDKOption，但不要执行initSdk初始化
3. 用户同意后再执行NIMClient.init()进行初始化
4. vivo推送真正初始化是在IM登录成功后触发
5. 参考vivo推送接入文档和云信隐私合规最佳实践处理"
customers: ["FVIP云信-深圳享笑"]
source: "chat_history"
tags: ["VIVO", "离线推送", "vivoAgreePrivacyStatement", "隐私合规", "104错误", "Android"]
created: "2025-09-02"
updated: "2026-03-20"
---

## 问题：Android VIVO手机收不到离线推送-vivoAgreePrivacyStatement配置

## 问题详情

**现象**：
VIVO手机突然收不到离线推送，日志显示vivo推送SDK注册报错104。

## 排查过程

1. 检查日志发现vivo推送SDK版本获取不到，注册报错104
2. 确认用户未配置vivoAgreePrivacyStatement或配置为false
3. 用户尝试设置为true后仍收不到
4. 最终排查发现需要在用户同意隐私政策后再执行IM初始化

## 问题原因

vivo推送SDK需要隐私合规处理，vivoAgreePrivacyStatement默认为false，需要在用户同意隐私政策后设置为true，并且IM登录需要在同意隐私政策之后执行。

## 解决方案

1. 确保在用户同意隐私政策后将vivoAgreePrivacyStatement设置为true
2. 用户未同意隐私政策前可以先配置SDKOption，但不要执行initSdk初始化
3. 用户同意后再执行NIMClient.init()进行初始化
4. vivo推送真正初始化是在IM登录成功后触发
5. 参考vivo推送接入文档和云信隐私合规最佳实践处理

## 其他触发场景
