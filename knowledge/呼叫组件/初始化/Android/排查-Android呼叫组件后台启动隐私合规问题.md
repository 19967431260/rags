---
track_type: 排查类
sub_type: 集成类
product: 呼叫组件
feature: 初始化
platform: Android
title: Android呼叫组件后台启动隐私合规问题
root_cause: 呼叫组件初始化逻辑放在BaseActivity.onCreate中，当应用后台重启时会触发初始化，读取应用列表等敏感信息。
solution: 1. 延迟初始化：不需要在Application或Activity.onCreate中提前初始化呼叫组件
2. 按需初始化：在真正需要使用呼叫功能时再初始化
3. 检查版本配置：确认是否有按需初始化的配置项
4. 参考文档：https://doc.yunxin.163.com/nertccallkit/guide/DI5Nzg0OTM?platform=android
customers: ["深圳对娱信息技术有限公司"]
source: chat_history
tags: ["呼叫组件", "隐私合规", "后台启动", "初始化", "应用列表"]
created: 2025-11-24
updated: 2026-03-20
---

## 问题：Android Android呼叫组件后台启动隐私合规问题

## 问题详情

**现象**：
客户应用在上架审核时被检测存在后台读取应用列表行为，堆栈显示是呼叫组件初始化代码导致，且触发位置为BaseActivity.onCreate。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 分析审核反馈 → 后台读取应用列表
2. 检查堆栈信息 → 呼叫组件在BaseActivity.onCreate中初始化
3. 确认初始化时机 → 登录后的启动页面初始化
4. 分析触发场景 → 应用挂了重启时可能后台启动MainActivity
**关键发现**：呼叫组件在Activity.onCreate中初始化，当应用后台重启时会触发初始化，导致隐私合规问题

**关键发现**：

## 问题原因

呼叫组件初始化逻辑放在BaseActivity.onCreate中，当应用后台重启时会触发初始化，读取应用列表等敏感信息。

## 解决方案

1. 延迟初始化：不需要在Application或Activity.onCreate中提前初始化呼叫组件
2. 按需初始化：在真正需要使用呼叫功能时再初始化
3. 检查版本配置：确认是否有按需初始化的配置项
4. 参考文档：https://doc.yunxin.163.com/nertccallkit/guide/DI5Nzg0OTM?platform=android

## 其他触发场景

