---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: Demo问题
platform: Windows
title: PC Demo编译运行报错
root_cause: Demo代码中特定配置导致编译或运行失败。
solution: 1. 不要勾选私有化环境配置
2. 按文档替换自己的appkey
3. 检查token是否有md5加密处理，如有则注释掉
4. 确保移动端和PC端使用相同的accid和token登录。
customers: ['云信-广州群市网络科技有限公司']
source: chat_history
tags: ['Demo', 'Windows', '编译报错', 'config_helper', 'PC']
created: 2025-02-20
updated: 2026-03-23
---

## 问题：Windows PC Demo编译运行报错

## 问题详情

**现象**：
Windows PC Demo编译过程中报错，config_helper.cpp文件108行出错。

**环境信息**：
- 平台：Windows
- 产品：IM-SDK

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 检查Demo版本和配置
2. 确认私有化环境配置未勾选
3. 检查appkey配置和替换
4. 远程排查发现代码问题

## 问题原因

Demo代码中特定配置导致编译或运行失败。

## 解决方案

1. 不要勾选私有化环境配置
2. 按文档替换自己的appkey
3. 检查token是否有md5加密处理，如有则注释掉
4. 确保移动端和PC端使用相同的accid和token登录。

## 其他触发场景

（合并时在此处追加：`- [Windows] PC Demo编译运行报错，来源：['云信-广州群市网络科技有限公司']，2026-03-23`）
