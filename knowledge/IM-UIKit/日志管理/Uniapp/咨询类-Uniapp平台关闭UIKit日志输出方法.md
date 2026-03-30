---
track_type: 咨询类
sub_type: 接口用法咨询
product: IM-UIKit
feature: 日志管理
platform: Uniapp
title: Uniapp平台关闭UIKit日志输出方法
root_cause: 
solution: 在初始化getInstance时设置debugLevel为off来关闭日志输出。建议在准备上线时关闭日志，测试环境下保持开启以便问题排查。
customers: ['陕西启星汇申网络科技有限公司']
source: chat_history
tags: ['日志', 'debugLevel', 'Uniapp', 'UIKit', 'V9']
created: 2025-01-15
updated: 2026-03-23
---

## 问题：Uniapp平台关闭UIKit日志输出方法

## 问题详情

**现象**：
客户在Uniapp平台集成IM V9 UIKit时，想要关闭NEChatUIKit和NEContactUIKit两个包的日志输出，设置debugLevel为off后仍有日志输出。

## 排查过程



## 问题原因



## 解决方案

在初始化getInstance时设置debugLevel为off来关闭日志输出。建议在准备上线时关闭日志，测试环境下保持开启以便问题排查。

## 其他触发场景

（合并时在此处追加）
