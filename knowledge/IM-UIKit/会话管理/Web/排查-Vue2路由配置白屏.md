---
track_type: 排查类
sub_type: 集成类
product: IM-UIKit
feature: 会话管理
platform: Web
title: Vue2项目中UIKit路由配置问题
root_cause: 客户未理解UIKit集成原理，业务层只需传递一个渲染容器div给UIKit，路由逻辑在UIKit内部处理
solution: 参考官方Demo代码逻辑：https://github.com/netease-kit/nim-uikit-web/tree/main/vue2-demo，业务层传入渲染div容器即可，无需手动配置router
tags: ["Vue2", "UIKit", "路由配置", "白屏", "渲染容器"]
customers: ["山东华御信息技术有限公司"]
source: chat_history
created: 2026-02-04
updated: 2026-03-17
---

## 问题：Web Vue2项目中UIKit路由配置问题

## 问题详情

**现象**：
客户在Vue2项目中按文档集成UIKit时，代码中使用了router但未找到注册位置，导致页面白屏。客户不理解UIKit的渲染容器配置方式。

## 排查过程

1. 检查文档代码 → 发现router未在项目中注册
2. 页面加载 → 白屏无内容
**关键发现**：客户直接复制文档代码，未理解UIKit需要传入渲染容器div的逻辑

## 问题原因

客户未理解UIKit集成原理，业务层只需传递一个渲染容器div给UIKit，路由逻辑在UIKit内部处理

## 解决方案

参考官方Demo代码逻辑：https://github.com/netease-kit/nim-uikit-web/tree/main/vue2-demo，业务层传入渲染div容器即可，无需手动配置router

## 其他触发场景

