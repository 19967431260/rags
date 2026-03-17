---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 云端会话
platform: Windows
title: C++ SDK获取云端会话实例返回null
root_cause: SDK初始化时V2NIMInitOption参数未正确配置，缺少云端会话相关配置项
solution: 在SDK初始化时正确配置V2NIMInitOption参数，需要包含云端会话相关配置。配置后可通过本地日志验证，开启与否日志打印不同
customers: ["南京信息技术研究院"]
source: chat_history
tags: ["云端会话","V2NIMInitOption","初始化配置","C++","Windows"]
created: 2026-02-02
updated: 2026-03-17
---

## 问题：Windows C++ SDK获取云端会话实例返回null

## 问题详情

**现象**：
使用C++ SDK时，获取云端会话服务实例返回null，本地会话实例无此问题。已确认控制台开启了云端会话功能。

## 排查过程

1. 检查云端会话开关 → 已开启
2. 尝试使用不带local的会话服务 → 仍返回null
3. 检查SDK日志 → 日志内容不足以定位问题
4. 建议使用UIKit demo测试 → 客户表示不适用于现有项目
5. 检查数据库表数据 → 有数据但accid未对齐
6. 检查初始化参数 → 发现V2NIMInitOption参数配置不完整

**关键发现**：SDK初始化时未配置云端会话相关参数

## 问题原因

SDK初始化时V2NIMInitOption参数未正确配置，缺少云端会话相关配置项

## 解决方案

在SDK初始化时正确配置V2NIMInitOption参数，需要包含云端会话相关配置。配置后可通过本地日志验证，开启与否日志打印不同。

## 其他触发场景

（暂无）
