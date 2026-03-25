---
track_type: 排查类
sub_type: 版本兼容
product: IM-UIKit
feature: UIKit集成
platform: Web
title: Vue2项目集成UIKit V10版本问题
root_cause: 最新版UIKit(10.x)只支持Vue3，Vue2项目需要使用V9版本
solution: 最新版UIKit(10.x)只支持Vue3。Vue2项目需要使用V9版本(9.x)。建议升级到Vue3以使用最新功能，或临时使用V9版本。参考文档：https://doc.yunxin.163.com/messaging-uikit/guide/TM0ODQxMTM?platform=web
customers: ["郑州开缘商贸有限公司"]
source: chat_history
tags: ["Vue2", "Vue3", "UIKit", "版本兼容", "组件库"]
created: 2025-05-14
updated: 2025-03-23
---

## 问题：Web Vue2项目集成UIKit V10版本问题

## 问题详情

**现象**：
Vue2项目引入@xkit-yx/im-kit-ui组件库时报错，需要确认版本兼容性。

**环境信息**：
- 平台：Web

## 排查过程

**关键发现**：UIKit V10只支持Vue3

## 问题原因

最新版UIKit(10.x)只支持Vue3，Vue2项目需要使用V9版本

## 解决方案

最新版UIKit(10.x)只支持Vue3。Vue2项目需要使用V9版本(9.x)。建议升级到Vue3以使用最新功能，或临时使用V9版本。参考文档：https://doc.yunxin.163.com/messaging-uikit/guide/TM0ODQxMTM?platform=web
