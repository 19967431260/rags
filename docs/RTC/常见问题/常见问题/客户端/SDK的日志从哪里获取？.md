各端设置日志路径的方式如下：

- Android：
    调用 `NERtc.getInstance().init` 方法初始化 SDK 时，通过 `NERtcOption` 对象的 `LogDir` 参数指定日志路径。V5.3.0 及之后版本的默认日志路径为：`sdcard/Android/data/your_app_name/files/rtc_log`。
- iOS：
    调用 `setupEngineWithContext` 方法初始化 SDK 时，通过 `NERtcEngineContext` 类下 `NERtcLogSetting` 的 `logSetting` 参数指定日志路径。SDK 日志会保存在沙盒中，V4.X 版本的默认日志路径为 `Document/NERtcSDK`，V5.3.0 及之后版本的默认日志路径为：`~/Documents/Logs`。

- PC：
    调用 `initialize` 方法初始化 SDK 时，通过 `rtc_engine_context` 对象的 `log_dir_path` 参数指定日志路径。V5.3.0 及之后版本，Windows 端的默认日志路径为：EXE 同级目录下的 **logs** 文件夹，子目录的命名规则为`AppKey 前6位_AppKey hash值的前 9 位`。macOS 端的默认日志路径为：`~/Documents/Logs`。
- Web：
    调用 `WebRTC2.createClient` 方法创建客户端时，通过设置 `debug` 参数为 true 开启调试模式，SDK 将在浏览器控制台输出日志。