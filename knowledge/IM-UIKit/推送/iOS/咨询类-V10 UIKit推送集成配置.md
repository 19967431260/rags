---
track_type: 咨询类
sub_type: 配置开通咨询
product: IM-UIKit
feature: 推送
platform: iOS
title: V10 UIKit推送集成配置
root_cause: 
solution: UIKit已包含推送SDK，只需在控制台配置证书名称，在AppDelegate中上报deviceToken即可。参考文档：https://doc.yunxin.163.com/messaging2/guide/TUzNDAwNDY?platform=client
customers: ['太旗富鑫']
source: chat_history
tags: ['UIKit', 'V10', '推送', 'iOS', 'deviceToken', '证书配置']
created: 2025-01-20
updated: 2026-03-23
---

## 问题：V10 UIKit推送集成配置

## 问题详情

**现象**：
客户咨询V10 UIKit是否需要单独集成推送SDK，以及推送配置方式。

## 排查过程

1. 客户咨询推送是否需要单独集成SDK
2. 告知UIKit已引入SDK，配置证书名称即可
3. 客户询问是否需要单独引入NIMSDK
4. 确认UIKit已包含，无需单独引入
5. 告知只需在AppDelegate中上报token即可

## 问题原因



## 解决方案

UIKit已包含推送SDK，只需在控制台配置证书名称，在AppDelegate中上报deviceToken即可。参考文档：https://doc.yunxin.163.com/messaging2/guide/TUzNDAwNDY?platform=client

## 其他触发场景

（合并时在此处追加）
