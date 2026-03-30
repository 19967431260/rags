## 问题描述

调试或者使用 NERTC SDK Web 版本时，监听到 `videoTrackEnded` 或者 `audioTrackEnded`。

## 原因分析

该回调表明视频、音频的采集都被异常中断了。

## 解决方法

建议监听这两个回调 `videoTrackEnded`、`audioTrackEnded`。在每个监听里，去执行 `close` 关闭对应的 `video` 或者 `audio` 设备。然后重新 `open` 恢复正常的采集。

示例代码：

```TypeScript
rtc.client.on("videoTrackEnded",async function(evt){

console.log("videoTrackEnded"+evt);

await rtc.localStream.close({type:"video"});

await rtc.localStream.open({type:"video",deviceId:"对应的摄像头id"});

})

rtc.client.on("audioTrackEnded",async function(evt){

console.log("audioTrackEnded"+evt);

await rtc.localStream.close({type:"audio"});

await rtc.localStream.open({type:"audio",deviceId:"对应的麦克风id"});

})
```