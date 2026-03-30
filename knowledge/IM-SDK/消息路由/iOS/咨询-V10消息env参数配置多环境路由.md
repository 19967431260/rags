---
track_type: 咨询类
sub_type: 接口用法咨询
product: IM-SDK
feature: 消息路由
platform: iOS
title: V10消息env参数配置多环境路由
root_cause: ""
solution: V10不支持在初始化时统一配置env。需要在发送消息时通过V2NIMSendMessageParams的routeConfig参数配置环境路由。如果需要统一走一个地址，可以在控制台后台配置统一的抄送和回调地址。参考文档：抄送：https://doc.yunxin.163.com/messaging2/server-apis/jY5MDk1NTQ?platform=server 回调：https://doc.yunxin.163.com/messaging2/server-apis/jI3ODc2ODE?platform=server#开通和配置第三方回调 routeConfig参数：https://doc.yunxin.163.com/messaging2/references/iOS/doxygen/Latest/zh/d5/dc2/interface_v2_n_i_m_send_message_params.html
customers: ["时间在线-gj"]
source: chat_history
tags: ["env", "routeConfig", "多环境", "消息路由", "V10"]
created: 2026-01-15
updated: 2026-03-15
---

## 问题：iOS V10消息env参数配置多环境路由

## 问题详情

**现象**：
V10 iOS SDK需要配置消息的env参数来实现测试环境和生产环境的路由分离，但routeConfig属性只读无法修改。

## 排查过程

1. 查找env配置 → 未找到统一配置入口
2. 尝试修改routeConfig → 发现是只读属性
3. 查看发送消息参数 → 找到V2NIMSendMessageParams.routeConfig

**关键发现**：V10的env需要在每次发送消息时通过routeConfig参数配置

## 解决方案

V10不支持在初始化时统一配置env。需要在发送消息时通过V2NIMSendMessageParams的routeConfig参数配置环境路由。如果需要统一走一个地址，可以在控制台后台配置统一的抄送和回调地址。参考文档：
- 抄送：https://doc.yunxin.163.com/messaging2/server-apis/jY5MDk1NTQ?platform=server
- 回调：https://doc.yunxin.163.com/messaging2/server-apis/jI3ODc2ODE?platform=server#开通和配置第三方回调
- routeConfig参数：https://doc.yunxin.163.com/messaging2/references/iOS/doxygen/Latest/zh/d5/dc2/interface_v2_n_i_m_send_message_params.html

## 其他触发场景

