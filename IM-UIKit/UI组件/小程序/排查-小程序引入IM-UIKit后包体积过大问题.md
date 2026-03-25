---
track_type: 排查类
sub_type: 集成问题
product: IM-UIKit
feature: 小程序集成
platform: 小程序
title: 小程序引入IM UIKit后包体积过大问题
root_cause: npm安装的依赖包体积过大
solution: 解决方案有两种：方案1（推荐）：使用ESM SDK文件引入方式，下载ESM格式的SDK文件，删除npm依赖；方案2：分包加载，将IM相关页面和依赖放入分包。注意事项：上报事件的代码可以删除或固定版本号写死为10.8.25。
customers: ["江苏博融信息技术有限公司"]
source: chat_history
tags: ["小程序", "包体积", "npm", "ESM", "分包", "UIKit", "im-store-v2"]
created: 2025-05-12
updated: 2025-03-23
---

## 问题：小程序 小程序引入IM UIKit后包体积过大问题

## 问题详情

**现象**：
在小程序中通过npm安装@xkit-yx/im-store-v2和@xkit-yx/utils依赖后，打包后的vendor.js体积过大，导致小程序包体积超出限制。

**环境信息**：
- 平台：小程序

## 排查过程

**关键发现**：npm安装的依赖包体积过大

## 问题原因

npm安装的依赖包体积过大

## 解决方案

解决方案有两种：

方案1（推荐）：使用ESM SDK文件引入方式
- 下载ESM格式的SDK文件（如esmNim.js）
- 将import { V2NIMConst, NIM } from './esmNim.js'中的V2NIMConst改为NIM
- 删除npm依赖（nim-web-sdk-ng可以去掉）
- 修改代码中的import路径

方案2：分包加载
- 将IM相关页面和依赖放入分包
- 整个UIKit空项目依赖最终约1.3MB
- 更彻底的优化是将依赖的esm文件都放到分包内，不通过npm依赖，需要修改代码中的import

注意事项：上报事件的代码可以删除或固定版本号写死为10.8.25。
