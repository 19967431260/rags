---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 会话管理
platform: Uniapp
title: Uniapp端UIKit会话列表为空
root_cause: 初始化参数中未开启云端会话（sceneType未设置），依赖漫游同步但同步失败
solution: 在初始化参数中将sceneType设置为true开启云端会话（需高级版或以上，且管理后台需打开云端会话功能）；设置为false则是本地会话
customers: ["云信-七七星球技术对接群"]
source: chat_history
tags: ["UIKit", "Uniapp", "会话列表为空", "sceneType", "云端会话"]
created: 2025-08-18
updated: 2026-03-26
---

## 问题：Uniapp Uniapp端UIKit会话列表为空

## 问题详情

**现象**：
客户使用UIKit打包成App后，PC端和手机端都显示空白，刷新也无反应。管理后台漫游开关已开启。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：PC端和手机端
- 其他：管理后台漫游开关已开启

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客服确认是否开启了会话同步 → 确认已开启
2. 客服询问UIKit版本号 → 获取版本信息
3. 客服让客户提供初始化参数配置截图 → 检查初始化参数
4. 客服确认需要开启云端会话配置 → 定位初始化参数问题

**关键发现**：初始化参数中未开启云端会话（sceneType未设置）

## 问题原因

初始化参数中未开启云端会话（sceneType未设置），依赖漫游同步但同步失败

## 解决方案

在初始化参数中将sceneType设置为true开启云端会话（需高级版或以上，且管理后台需打开云端会话功能）；设置为false则是本地会话

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
