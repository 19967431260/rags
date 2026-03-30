---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 消息搜索
platform: iOS
title: V10消息全文检索报错-team receipt disabled
root_cause: 未开启群消息已读功能，需要在NIMSDKConfig中设置teamReceiptEnabled = YES。
solution: 在SDK初始化时设置：[NIMSDKConfig sharedConfig].teamReceiptEnabled = YES。参考文档：https://doc.yunxin.163.com/messaging2/references/iOS/doxygen/Latest/zh/d6/d13/interface_n_i_m_s_d_k_config.html
customers: ["杭州跨客技术服务有限公司"]
source: chat_history
tags: ["全文检索", "team receipt", "V10", "iOS", "初始化配置"]
created: 2025-05-19
updated: 2025-03-20
---

## 问题：iOS V10消息全文检索报错-team receipt disabled

## 问题详情

**现象**：
使用V10 SDK进行消息全文检索时报错，提示team receipt disabled。SDK版本10.8.21。

**环境信息**：
- SDK 版本：
- 系统版本 / 设备：
- 平台：iOS

## 排查过程

1. 客户反馈检索消息报错 → 技术支持要求提供SDK日志
2. 分析日志发现team receipt disabled错误 → 需要在初始化时设置teamReceiptEnabled
3. 提供初始化配置方法

## 问题原因

未开启群消息已读功能，需要在NIMSDKConfig中设置teamReceiptEnabled = YES。

## 解决方案

在SDK初始化时设置：[NIMSDKConfig sharedConfig].teamReceiptEnabled = YES。参考文档：https://doc.yunxin.163.com/messaging2/references/iOS/doxygen/Latest/zh/d6/d13/interface_n_i_m_s_d_k_config.html

## 其他触发场景

