---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 群组管理
platform: 服务端
title: 取消管理员接口返回accid not members
root_cause: 取消管理员接口传入的members参数值与实际accid不一致，群详情返回的是m81105，但接口传入的是81105。
solution: 确保取消管理员接口传入的members参数与实际accid完全匹配，注意大小写和前后缀。
customers: ["北京新守心城"]
source: chat_history
tags: ["取消管理员", "accid", "群管理", "414错误"]
created: 2025-02-24
updated: 2026-03-20
---

## 问题：服务端 取消管理员接口返回accid not members

## 问题详情

**现象**：
客户调用取消管理员接口时报错提示不是管理员，但查群详情显示是管理员。

## 排查过程

1. 检查群详情返回的管理员列表 → 显示m81105是管理员\n2. 检查取消接口参数 → 传入的是81105（不带M前缀）\n3. 对比发现参数accid与实际accid不一致

## 问题原因

取消管理员接口传入的members参数值与实际accid不一致，群详情返回的是m81105，但接口传入的是81105。

## 解决方案

确保取消管理员接口传入的members参数与实际accid完全匹配，注意大小写和前后缀。

## 其他触发场景
- [服务端] 取消管理员接口返回accid not members，来源：['北京新守心城']，2026-03-20
- [服务端] 取消管理员接口返回accid not members，来源：['北京新守心城']，2026-03-20

