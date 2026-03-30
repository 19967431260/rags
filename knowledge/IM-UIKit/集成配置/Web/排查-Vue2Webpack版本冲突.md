---
track_type: 排查类
sub_type: 集成类
product: IM-UIKit
feature: 集成配置
platform: Web
title: Vue2老项目Webpack版本冲突
root_cause: 客户项目使用Webpack4老版本，与UIKit Demo要求的less-loader 5+版本存在兼容性冲突
solution: UIKit底层支持Vue2，不要直接复制Demo全部代码。核心逻辑只需两行：生成conversationId和调用selectConversation接口，按此逻辑在老项目中实现即可，无需升级构建工具
tags: ["Webpack4", "版本冲突", "less-loader", "Vue2", "构建工具"]
customers: ["山东华御信息技术有限公司"]
source: chat_history
created: 2026-02-05
updated: 2026-03-17
---

## 问题：Web Vue2老项目Webpack版本冲突

## 问题详情

**现象**：
客户使用Webpack4的Vue2老项目，集成UIKit V10 Demo时报错，提示需要less-loader 5+版本，但项目环境只能支持Webpack4，存在版本冲突无法编译。

## 排查过程

1. 按Demo集成UIKit → 编译报错
2. 检查依赖版本 → less-loader需要5+，Webpack只能用4
**关键发现**：客户项目使用老版本Webpack4，与UIKit Demo的构建工具版本不兼容

## 问题原因

客户项目使用Webpack4老版本，与UIKit Demo要求的less-loader 5+版本存在兼容性冲突

## 解决方案

UIKit底层支持Vue2，不要直接复制Demo全部代码。核心逻辑只需两行：生成conversationId和调用selectConversation接口，按此逻辑在老项目中实现即可，无需升级构建工具

## 其他触发场景

