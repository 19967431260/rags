本文介绍 uni-app 端快速集成并初始化网易云信房间组件（NERoom SDK）的操作步骤，帮助您快速集成并初始化 NERoom SDK。

## 开发环境

在开始运行工程之前，请您准备以下开发环境：

- 安全环境：HTTPS 环境或者本地连接 localhost（127.0.0.1）环境。
- 浏览器：谷歌 Chrome 72 及以上版本、苹果 Safari 12 及以上版本。

## 前提条件

根据本文操作前，请确保您已经在 [网易云信控制台](https://app.yunxin.163.com/global/home) 上完成了以下设置：

- 创建至少一个应用。详细步骤请参考 [创建应用并获取 AppKey](https://doc.yunxin.163.com/console/concept/TIzMDE4NTA?platform=console)。
- 为应用开通一个房间组建模板。详细步骤请参考 [开通或试用服务](https://doc.yunxin.163.com/console/concept/zc3NDYzNzc?platform=console)。

## 集成 SDK

前往 [SDK 下载页面](https://doc.yunxin.163.com/neroom/resource?platform=uniapp)获取当前最新版本 SDK。

## 初始化 SDK

请参考以下示例代码进行初始化实例。

```JavaScript
import { RoomEngine } from '@/uni_modules/netease-roomkit'

const engine = new RoomEngine()
engine.initialize({
  appkey: 'YOUR_APP_KEY',
  result: (code, message) => {
    if (code !== 0) return console.error('初始化失败', message)
    console.log('初始化成功')
  }
})
```