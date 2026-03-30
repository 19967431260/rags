---
track_type: 排查类
sub_type: 集成类
product: RTC
feature: 私有化部署
platform: 服务端
title: 私有化服务器IP冲突更换方案
root_cause: IP地址冲突导致服务异常
solution: 全量替换IP地址：grep 46 -rl /opt | while read line; do sed -i 's#46#49#g' $line; 需修改brain、roomserver、logic-call等多个配置文件
customers: ["杭州诚道道路交通研究院"]
source: chat_history
tags: ["RTC", "私有化", "IP冲突", "服务器配置"]
created: 2025-02-24
updated: 2026-03-20
---

## 问题：服务端 私有化服务器IP冲突更换方案

## 问题详情

**现象**：
私有化部署服务器出现IP冲突(20.65.1.46)，需要更换为20.65.1.49。

## 排查过程

1. 确认IP冲突情况
2. 检查arp绑定和MAC地址
3. 修改各服务配置文件中的IP地址
4. 更新brain/private/cells/small配置
5. 更新roomserver/conf配置
6. 更新logic-call配置
7. 更新事件抄送地址

## 问题原因

IP地址冲突导致服务异常

## 解决方案

全量替换IP地址：grep 46 -rl /opt | while read line; do sed -i 's#46#49#g' $line; 需修改brain、roomserver、logic-call等多个配置文件

## 其他触发场景
- [服务端] 私有化服务器IP冲突更换方案，来源：['杭州诚道道路交通研究院']，2026-03-20
- [服务端] 私有化服务器IP冲突更换方案，来源：['杭州诚道道路交通研究院']，2026-03-20

