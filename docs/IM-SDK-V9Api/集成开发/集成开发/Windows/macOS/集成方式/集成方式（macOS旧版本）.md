
 
macOS NIM SDK 和 iOS NIM SDK 基于同一份代码开发，拥有和 iOS NIM SDK 几乎完全一致的功能，兼容 macOS 10.10，但仅支持 x86_64 架构，不支持 i386。

## <span id="开发准备">开发准备</span>

macOS NIMSDK 目前仅提供手动集成方式

* 根据工程需要，下载对应版本的 macOS NIM SDK，得到 NIMSDK.framework 并导入工程
* 导入 Libs 中的依赖库
* 添加其他 macOS NIM SDK 依赖库
	* CoreServices.framework
	* AVFoundation.framework
	* libc++.tbd
	* libsqlite3.0.tbd
	* libz.tbd

* 在 `Build Settings` -> `Other Linker Flags` 里，添加选项 `-ObjC`。
* 在需要使用 macOS NIM SDK 的地方 `import <NIMSDK/NIMSDK.h>` 

## <span id="SDK 使用">SDK 使用</span>

如上文所言，macOS NIM SDK 拥有 iOS NIM SDK 几乎完全一致的功能。对应功能集成和 API 使用可以参考 iOS 对应文档。

当然 macOS NIM SDK 和 iOS NIM SDK 仍有少量差异，主要体现在推送和部分类名上。

### 推送

对于 iOS NIM SDK 而言，推送是非常重要的部分。但对于 macOS NIM SDK 而言推送的地位则较为尴尬：macOS NIM SDK 已经提供完备的长连接实现，可以使用它作为任何通知的推送通道。所以在 macOS 平台上我们并不提供推送服务，相关的界面表现可以由上层自行处理。

### 类名

macOS NIM SDK 和 iOS NIM SDK 采取的是一份代码两个平台共用的策略，这意味着绝大部分代码都是跨平台的。然而仍有小部分实现必须针对具体平台提供对应的实现。为了处理这种情况同时保证 iOS NIM SDK 兼容性，我们使用 `@compatibility_alias` 对两个平台不同的类名做了处理，详情可以参考 `NIMPlatform.h` 这个头文件。