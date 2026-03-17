---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 私有化部署
platform: Linux
title: Linux SDK私有化环境进房报错30103
root_cause: 纯私有化环境错误配置了cloud_proxy_server和web_socket_proxy_server参数，且后台服务器调度存在问题。
solution: 纯私有化环境不需要配置web_socket_proxy_server、cloud_proxy_server等代理参数，这些参数必须为空。配置正确后如仍有问题，需检查后台部署和服务器调度。
customers: ["飞虎互动"]
source: chat_history
tags: ["30103","Linux SDK","私有化","web_socket_proxy_server","cloud_proxy_server","进房失败"]
created: 2026-02-05
updated: 2026-03-17
---

## 问题：Linux Linux SDK私有化环境进房报错30103

## 问题详情

**现象**：
Linux SDK在纯私有化环境下加入房间失败，返回错误码30103。配置了cloud_proxy_server和web_socket_proxy_server参数。Web端可以正常进房，但Linux SDK和其他端都无法进房。

## 排查过程

1. 检查配置参数 → 发现配置了web_socket_proxy_server
2. 移除web_socket_proxy_server配置 → 仍报30103错误
3. 检查日志 → 发现后台返回code=500006
4. 确认是否纯私有化环境 → 确认为纯私有化
5. 移除cloud_proxy_server和web_socket_proxy_server配置 → 仍报30103
6. 分析后台日志 → 初步判断是后台部署问题
7. 重新发起请求 → 调度到正确服务器后成功进房

**关键发现**：纯私有化环境不需要配置云代理和信令代理参数，且问题最终由后台服务器调度解决。

## 问题原因

纯私有化环境错误配置了cloud_proxy_server和web_socket_proxy_server参数，且后台服务器调度存在问题。

## 解决方案

纯私有化环境不需要配置web_socket_proxy_server、cloud_proxy_server等代理参数，这些参数必须为空。配置正确后如仍有问题，需检查后台部署和服务器调度。

## 其他触发场景

