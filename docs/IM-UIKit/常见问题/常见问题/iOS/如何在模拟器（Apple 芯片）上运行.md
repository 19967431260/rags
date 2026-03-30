IM iOS（Flutter-iOS） UIKit 在 Intel 芯片中可直接运行。因此这里主要介绍如何在 Apple 芯片机器上使用模拟器运行云信 IM demo。

::: note note
由于部分三方库未适配 arm64 架构，因此模拟器运行时需移除 arm64 架构。
:::

1. 在 Podfile 文件末尾添加以下代码，然后重新执行 `pod install`。

```Swift
# Apple 芯片 系列模拟器运行打开以下代码
post_install do |installer|
installer.pods_project.targets.each do |target|
    target.build_configurations.each do |config|
    config.build_settings["EXCLUDED_ARCHS[sdk=iphonesimulator*]"] = "arm64"
    end
end
end
```

2. 在工程配置中 **移除 arm64 架构** 或者 **使用 Rosetta 模拟器**。

:::::: div linked-codes
::: code 移除 arm64 架构
![iOS模拟器运行1.png](https://yx-web-nosdn.netease.im/common/1efba7b6f90d66cabc98bbb26d260540/iOS模拟器运行1.png)

配置完成后模拟器只剩下 x86_64 架构。

![iOS模拟器运行2.png](https://yx-web-nosdn.netease.im/common/4e133fbf74f6b57d1a12cc3a9cdbc1ed/iOS模拟器运行2.png)

如果模拟器还存在 arm64 架构，说明未能正确配置移除模拟器 arm64，如下图所示。

![iOS模拟器运行3.png](https://yx-web-nosdn.netease.im/common/93c416c26faf7b198882ea96648d1935/iOS模拟器运行3.png)

此时可以重复步骤 2，直至完全移除模拟器 arm64。

:::
::: code 使用 Rosetta 模拟器
指定 Rosetta 模拟器运行云信 IM Demo。

![iOS模拟器运行4.png](https://yx-web-nosdn.netease.im/common/aafd6e2d1198854fc21f7e8c210560c9/iOS模拟器运行4.png)
:::
::::::