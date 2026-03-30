---
track_type: 排查类
sub_type: 客户环境问题
product: IM-SDK
feature: 网络连接
platform: Web
title: weblink域名IP变更导致连接问题
root_cause: 服务器迁移导致IP变更，客户host绑定固定IP导致连接失败
solution: 不建议绑定云信服务的IP，因为IP可能会变更。应使用域名访问，或及时更新绑定的IP地址。云信weblink相关域名包括：weblink.netease.im、weblink05.netease.im、weblink07.netease.im、weblink01.yunxinfw.com、weblink02.yunxinfw.com等。
customers: ['招商证券']
source: chat_history
tags: ['weblink', 'IP变更', 'host绑定', '网络连接', 'Web']
created: 2025-01-14
updated: 2026-03-23
---

## 问题：Web weblink域名IP变更导致连接问题

## 问题详情

**现象**：
客户在host中绑定了weblink.netease.im域名的IP，服务器迁移后IP变更导致连接问题。

## 排查过程

1. 客户反馈weblink.netease.im域名IP从59.111.211.160变为111.124.204.209
2. 客户配置了host绑定
3. 新IP/socket/io访问不了
4. 确认服务器从杭州迁移到贵州导致IP变更
5. 建议去掉host绑定

## 问题原因

服务器迁移导致IP变更，客户host绑定固定IP导致连接失败

## 解决方案

不建议绑定云信服务的IP，因为IP可能会变更。应使用域名访问，或及时更新绑定的IP地址。云信weblink相关域名包括：weblink.netease.im、weblink05.netease.im、weblink07.netease.im、weblink01.yunxinfw.com、weblink02.yunxinfw.com等。

## 其他触发场景

（合并时在此处追加）
