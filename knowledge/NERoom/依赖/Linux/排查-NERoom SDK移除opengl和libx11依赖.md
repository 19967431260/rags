---
track_type: 排查类
sub_type: 集成类
product: NERoom
feature: 依赖
platform: Linux
title: NERoom SDK移除opengl和libx11依赖
root_cause: NERoom SDK依赖libgl和libx11，但客户系统没有这些库
solution: 使用裸流传输直接外部渲染即可，不用RTC或者NERoom层的渲染就可以
customers: ["VIP_网易云信-玺文-高拍仪项目对接群"]
source: chat_history
tags: ["NERoom","裸流","opengl","libx11","依赖"]
created: 2025-08-05
updated: 2026-03-26
---

## 问题：Linux NERoom SDK移除opengl和libx11依赖

## 问题详情

**现象**：
客户板子系统很小，没有libgl和libx11的库，咨询能否去掉这些依赖

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 编译时报错需要设置path，libgl和libx11需要环境里安装 → 客户系统很小没有这些库
2. 客服反馈研发看以前版本怎么处理 → 最终方案确认

**关键发现**：NERoom SDK依赖libgl和libx11，但客户系统没有这些库

## 问题原因

NERoom SDK依赖libgl和libx11，但客户系统没有这些库

## 解决方案

使用裸流传输直接外部渲染即可，不用RTC或者NERoom层的渲染就可以

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
