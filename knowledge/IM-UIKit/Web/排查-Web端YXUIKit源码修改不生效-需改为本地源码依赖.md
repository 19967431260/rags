---
track_type: 排查类
sub_type: 使用问题
product: IM-UIKit
feature: Web
platform: Web
title: Web端YXUIKit源码修改不生效：需将远端依赖改为本地源码依赖
root_cause: Web端UIKit默认是远端依赖(node_modules)，修改源码文件不生效；需要把远端依赖改为本地源码依赖
solution: 把所有@xkit-yx/im-kit-ui的引入路径改为本地源码路径（../../yxUIKit/im-kit-ui/src/...）；React项目支持此方式；Vue项目需要React重新打包产物给Vue依赖
customers: ["深圳市直角力矩科技"]
source: chat_history
tags: ["Web端", "YXUIKit", "源码修改", "远端依赖", "本地依赖"]
created: 2025-07-02
updated: 2026-03-25
---

## 问题：Web端YXUIKit源码修改不生效：需将远端依赖改为本地源码依赖

## 问题原因

Web端UIKit默认是远端依赖(node_modules)，修改源码文件不生效；需要把远端依赖改为本地源码依赖

## 解决方案

把所有@xkit-yx/im-kit-ui的引入路径改为本地源码路径（../../yxUIKit/im-kit-ui/src/...）；React项目支持此方式；Vue项目需要React重新打包产物给Vue依赖
