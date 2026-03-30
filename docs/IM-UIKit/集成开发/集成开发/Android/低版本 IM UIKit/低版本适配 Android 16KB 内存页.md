云信 IM Android UIKit v9.7.7 版本适配了 16KB 内存页大小（Page Size），确保可以在使用 4 KB 和 16 KB 内存页大小的设备上无缝运行，提升兼容性并避免崩溃。

若您的应用需要支持 16 KB 内存页，需要按照本文介绍的步骤引入相关依赖库。

## 引入依赖

1. 升级 UIKit 底层库 chatkit 至 v9.7.7 版本。

    ```java
    implementation("com.netease.yunxin.kit.chat:chatkit:9.7.7")
    ```

2. 如果您的应用使用了呼叫组件，请同步升级至 v2.7.1 版本。

    ```java
    implementation("com.netease.yunxin.kit.call:call-ui:2.7.1")
    ```

## 故障排查

如果在 16KB 内存页设备上运行时出现崩溃，且错误日志中包含 `libyx_alog.so` 或 `com.netease.yunxin.kit.alog.ALog` 相关信息，那么请确认是否已添加 `alog:1.1.1` 依赖。若未添加，请手动添加以下依赖：

```java
implementation("com.netease.yunxin.kit:alog:1.1.1")
```