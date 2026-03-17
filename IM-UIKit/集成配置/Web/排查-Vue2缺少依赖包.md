---
track_type: 排查类
sub_type: 集成类
product: IM-UIKit
feature: 集成配置
platform: Web
title: Vue2项目集成UIKit缺少依赖包
root_cause: 集成文档中未明确列出所有必需依赖包，客户只安装了@xkit-yx/utils，缺少@xkit-yx/im-store-v2
solution: 手动安装缺失的依赖包：npm install @xkit-yx/im-store-v2，安装后即可正常引入UIKit组件
tags: ["依赖缺失", "im-store-v2", "Vue2", "UIKit集成", "npm安装"]
customers: ["山东华御信息技术有限公司"]
source: chat_history
created: 2026-02-03
updated: 2026-03-17
---

## 问题：Web Vue2项目集成UIKit缺少依赖包

## 问题详情

**现象**：
客户在Vue2项目中集成IM UIKit时，引入@xkit-yx/im-kit-ui后报错提示找不到@xkit-yx/im-store-v2模块。客户已按文档安装@xkit-yx/utils，但缺少im-store-v2依赖包。

## 排查过程

1. 检查package.json依赖 → 发现只安装了@xkit-yx/utils
2. 查看错误提示 → Module not found: @xkit-yx/im-store-v2
**关键发现**：客户按文档只安装了utils包，遗漏了im-store-v2依赖包

## 问题原因

集成文档中未明确列出所有必需依赖包，客户只安装了@xkit-yx/utils，缺少@xkit-yx/im-store-v2

## 解决方案

手动安装缺失的依赖包：npm install @xkit-yx/im-store-v2，安装后即可正常引入UIKit组件

## 其他触发场景

