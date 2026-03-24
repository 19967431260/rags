---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 登录
platform: Android
title: 海外用户IM登录失败-SDKCache.getAccount为空
root_cause: 1. 中东地区运营商域名解析失败
2. SDK版本过低(9.3.0)，缺少海外登录优化
3. 登录接口调用方式不当，频繁调用AuthService/login
4. 传入的登录信息无效，账号或token未传入
solution: 1. 申请IP直连方式解决域名解析问题
2. 升级到9.19.4版本，该版本针对海外场景做了登录成功率优化
3. 使用自动登录方式，参考文档：https://doc.yunxin.163.com/messaging/guide/DE1NjMxNjU?platform=android
4. 检查登录代码，确保账号和token正确传入
customers: ['逗趣互动']
source: chat_history
tags: ['SDKCache.getAccount', '登录失败', '海外用户', '中东', '域名解析', 'IP直连']
created: 2025-01-02
updated: 2026-03-23
---

## 问题：海外用户IM登录失败-SDKCache.getAccount为空

## 问题详情

**现象**：
安卓版本经常出现登录失败，报错SDKCache.getAccount为空。用户主要集中在中东地区。

## 排查过程

1. 检查日志发现大量域名解析失败导致的IM登录问题
2. 发现客户端使用SDK 9.3.0版本较老
3. 发现登录接口调用频繁调用AuthService/login
4. 发现登录传参问题，传入的登录信息无效

## 问题原因

1. 中东地区运营商域名解析失败
2. SDK版本过低(9.3.0)，缺少海外登录优化
3. 登录接口调用方式不当，频繁调用AuthService/login
4. 传入的登录信息无效，账号或token未传入

## 解决方案

1. 申请IP直连方式解决域名解析问题
2. 升级到9.19.4版本，该版本针对海外场景做了登录成功率优化
3. 使用自动登录方式，参考文档：https://doc.yunxin.163.com/messaging/guide/DE1NjMxNjU?platform=android
4. 检查登录代码，确保账号和token正确传入

## 其他触发场景

（合并时在此处追加）
