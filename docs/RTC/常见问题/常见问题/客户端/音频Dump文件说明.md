音频 Dump 文件主要用于定位音频相关问题，分析音频的输入输出情况一般也需要依赖音频 Dump 文件。

各端可参考集成文档获取音频 Dump 文件。

- [Android](https://doc.yunxin.163.com/nertc/guide/TA0NjAwMDY?platform=android)
- [iOS](https://doc.yunxin.163.com/nertc/guide/Tk3OTM1OTA?platform=iOS)
- [Windows](https://doc.yunxin.163.com/nertc/guide/DkxOTY1MDc?platform=windows)

各端的开始记录音频 Dump 信息接口（`startAudioDumpWithType`）的逻辑不同，具体如下：

- Android：每次调用该方法生成的 dump 文件都会覆盖之前的 dunmp 文件。
- iOS：SDK 的实例销毁（destroy）后，重新进行初始化，那么新生成的 dump 文件会覆盖之前的 dump 文件。如果只是退出音视频房间，再重新进入，那么 dump 文件会续写累加。
- Windows：每次调用该方法生成的 dump 文件都会覆盖之前的 dunmp 文件。