## <span id="10.0.1 (2025-09-09)">10.0.1 (2025-09-09)</span>

全新 QChat UIKit 组件 10.0.1 版本发布！

该版本底层适配 [NIM SDK v10.9.42 版本](https://doc.yunxin.163.com/messaging2/concept/TIxNTgxOTk?platform=client) 以及 [IM UIKit v10.8.6 版本](https://doc.yunxin.163.com/messaging-uikit/concept/jE5MTA5NjA?platform=client)。

## <span id="[9.5.6] - 2025-04-11">[9.5.6] - 2025-04-11</span>

- 修复已知问题。
- 升级兼容的 IM SDK 至 [V9.17.0](https://doc.yunxin.163.com/messaging/concept/jQ3NzQ3NDI?platform=client#9170-2024-07-04)。

## <span id="[9.5.3] - 2023-12-08">[9.5.3] - 2023-12-08</span>

圈组 UIKit 正式发布。相关文档请参阅 [圈组 UIKit 简介](https://doc.yunxin.163.com/messaging-uikit/concept/zc3MDc4Nzk?platform=iOS)。

### 新增特性

- 新增社区广场模块。
- 新增公告频道功能。
- 新增表情快捷评论。
- 扩展消息体类型。
- 增加消息体长按操作菜单以及删除撤回复复制等操作。
- UIKit 支持隐藏群组功能开关配置。

### 优化

- 优化多个场景下的权限动态变更处理逻辑。
- 双端提示语以及各种异常处理逻辑对齐。
- 所有二级页面监听用户有效性，如果用户离开被删除各种权限移除动态销毁页面。

### 变更

- repo 层提供单例 shared，不提供实例化接口。
- 移除第三方依赖 RSKPlaceholderTextView （使用 NETextView）。

### 兼容 NIM SDK 版本

V9.14.0





