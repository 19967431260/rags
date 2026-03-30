---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 服务端SDK
platform: Server
title: Java服务端SDK Maven依赖下载失败
root_cause: 客户网络环境限制，无法从Maven官方仓库下载插件，可能只能使用阿里云等镜像仓库
solution: 1. 使用正式版1.1.2
2. 检查网络限制，确保能访问Maven Central
3. 或配置Maven使用国内镜像仓库
customers: ["VIP云信-银川鲸麦互联网医院有限公司"]
source: chat_history
tags: ["服务端SDK", "Maven", "依赖下载", "网络限制"]
created: 2025-11-24
updated: 2026-03-20
---

## 问题：Server Java服务端SDK Maven依赖下载失败

## 问题详情

**现象**：
导入yunxin-server-sdk-java时，Maven无法下载依赖，提示找不到org.apache.maven.plugins:maven-source-plugin:3.1.0。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 尝试使用1.2.0-SNAPSHOT版本 → 失败
2. 检查Maven仓库 → 库已发布到Maven Central
3. 检查网络连接 → 能连接标准Maven域名
4. 分析错误 → maven-source-plugin下载失败
**关键发现**：客户网络环境可能有限制，无法下载Maven官方插件

**关键发现**：

## 问题原因

客户网络环境限制，无法从Maven官方仓库下载插件，可能只能使用阿里云等镜像仓库

## 解决方案

1. 使用正式版1.1.2
2. 检查网络限制，确保能访问Maven Central
3. 或配置Maven使用国内镜像仓库

## 其他触发场景

