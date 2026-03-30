---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 登录
platform: HarmonyOS
title: 鸿蒙SDK数据同步成功后getUseInfo报错
root_cause: V2NIMUserService服务未提前注册
solution: 在SDK初始化时提前注册V2NIMUserService服务，参考文档：https://doc.yunxin.163.com/messaging2/guide/TY4MTAxNzE
customers: ["圆通"]
source: chat_history
tags: ["HarmonyOS", "鸿蒙", "getUseInfo", "服务注册"]
created: 2025-05-15
updated: 2025-03-20
---

## 问题：HarmonyOS 鸿蒙SDK数据同步成功后getUseInfo报错

## 问题详情

**现象**：
鸿蒙端在数据同步成功后调用getUseInfo提示错误，显示V2NIMUserServiceImpl服务未注册。

## 排查过程

**关键发现**：V2NIMUserService服务未提前注册

## 问题原因

V2NIMUserService服务未提前注册

## 解决方案

在SDK初始化时提前注册V2NIMUserService服务，参考文档：https://doc.yunxin.163.com/messaging2/guide/TY4MTAxNzE
