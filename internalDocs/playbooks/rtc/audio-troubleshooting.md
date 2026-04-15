# Playbook: RTC 音频问题排查

- source file: `/Users/yxgc/.openclaw/workspace/tmp/popo-doc-export/docs/0e75a2c03c22477fa80bed693a6fc837__音频问题排查手册.md`
- scope: RTC 实时音频
- intent: 把“无声/声音小/回声/噪声/卡顿/延迟/路由异常/音质异常”快速切到正确链路阶段

## 适用场景

适用于用户反馈：
- A 听不到 B / 声音很小 / 偶现无声
- 声音忽大忽小
- 回声、噪声、啸叫、电流声
- 声音卡顿、机械音、断续
- 声音延迟明显
- 蓝牙/听筒/扬声器路由异常
- 某些机型或系统版本稳定复现音频异常

不适用于：
- 纯入房失败（先转“加入音视频房间失败”或“基于服务器数据排查是否加入房间”）
- 纯服务端接口报错（转服务端接口 playbook）

## 最小输入

至少要有：
- appkey / room id(cname/cid) / uid（至少异常侧和对端各 1 个）
- 问题时间点
- 谁听不到谁、谁听到回声/噪声
- 平台、系统版本、SDK 版本

最好补齐：
- QS 指标截图或可查询时间窗
- 是否可稳定复现 / 是否持续发生
- 是否使用蓝牙、耳机、外置声卡、虚拟声卡、AirPlay、投屏
- 是否切后台、来电、CallKit、微信语音、Siri、录音/屏幕共享/伴音/前处理
- 日志；回声/噪声/采集播放异常时优先补 audio dump

## 首先判断

1. **问题是持续还是偶现？**
   - 持续：优先按链路逐段排。
   - 偶现：更依赖精确时间点、事件上报、系统打断、后台切换、设备争用。

2. **问题属于哪一类现象？**
   - 无声/声音小
   - 回声/噪声
   - 卡顿/延迟
   - 路由/设备选择异常
   - 音质/特定设备适配

3. **先确认房间和状态是否成立。**
   - 是否实际在房间内
   - 是否掉线
   - mute / subscribeRemoteAudio 状态是否错误

## 分支排查路径

### A. 无声 / 声音小

按链路顺序切分：

#### A1. 先看播放侧（用户主诉“听不到”时）
- 看接收侧是否有接收码率：`Audio Recv Bitrate`
- 看播放音量：`Farin`
- 看播放连续性：`Audio Playback Frequency`
- 看输出路由：`Audio Output Route`、`audioDeviceEvent -> OutputDeviceChange`

结论方向：
- **有接收码率，但 Farin 很低/固定、播放频率异常**：优先怀疑接收端播放/设备/路由/系统打断。
- **有接收码率、Farin 也正常，但用户仍称听不到**：优先查输出设备选错、系统/应用静音、蓝牙模式错配、画面外放/听筒切换。
- **无接收码率**：继续往下看下行网络或发送端。

#### A2. 看下行传输 + 解码
- `Audio Recv RTT`
- `Audio Recv Lossrate`
- `Audio Recv Render Freeze Time`
- `Audio Decode Time`
- `RTX/FEC repaired ratio`

结论方向：
- RTT > 500ms、丢包 > 30%：先按弱网处理。
- 解码时间停滞、接收码率异常：查下行链路或解码异常。

#### A3. 看发送端上行
- `Audio Send Total Bitrate`
- `Audio Encode Bitrate`
- `Audio Send RTT`
- `Audio Send Lossrate`
- `Audio Send Allocated Bitrate`
- `SDK Mute Status`

结论方向：
- muteLocalAudio / subscribeRemoteAudio 配错是高频误判点。
- 分配带宽明显不足、NACK/FEC 异常高：优先弱网。
- 仍无发送：继续看采集。

#### A4. 看采集 + 处理
- `Nearin` / `Nearout`
- `Audio Record Frequency`
- `Audio ADM Type`
- `Audio Engine Error Code`
- `audioDeviceEvent`
- `CPU/Mem`

结论方向：
- `Nearin` 长期低于 -40dB 或固定不动：优先怀疑采集设备/权限/硬件 AGC/系统音频会话异常。
- `Audio Record Frequency` 大幅波动或异常：优先怀疑设备/系统音频模块异常或性能问题。
- iOS 出现 `CategoryChange` 非 `PlayAndRecord`、`setActive:0`、打断事件：优先怀疑业务侧 AudioSession 干预。

#### A5. 设备与权限补刀
- 让用户用系统录音机 / 播放音乐做设备自检。
- Win 端同时检查系统扬声器静音和音量合成器 App 静音。
- 蓝牙设备注意 `A2DP`（音乐）与 `SCO`（通话）模式不可混搭。

### B. 回声 / 噪声

先区分：
- **回声**：谁听到了自己的声音？通常问题更可能出在“对方设备采集了自己播放出来的声音”。
- **噪声**：是所有人都听到，还是单个接收端听到？

重点判断：
- 是否近场多机同时开麦（同会议室/距离很近）
- 是否外放过大、未戴耳机
- 是否开启耳返/监听麦克风
- 是否环境噪声大、风扇、摩擦、电流声
- 是否 CPU 过高、设备异常

必须知道：
- **仅凭 QS 往往不能直接定责回声/噪声。** 文档明确建议收集 `audio dump + 日志`。

优先动作：
- 让怀疑的回声源用户降播放音量或戴耳机复测
- 让远端静音/轮流静音，定位噪声源
- 若算法/机型适配嫌疑大，收 dump 交研发

### C. 声音卡顿

按以下顺序：
1. 明确卡顿表现：偶发断续 / 机械音 / 周期性断续 / 丢字
2. 看 `CPU`、`上/下行 RTT`、`丢包`
3. 看采集和播放连续性：`Audio Record Frequency`、`Audio Playback Frequency`
4. 若业务开启 `onRecordFrame` 等原始数据回调，确认处理是否阻塞线程

结论方向：
- 高 RTT / 高丢包：弱网优先
- CPU > 90%：设备性能优先
- 频率异常：音频线程/系统音频模块优先

### D. 声音延迟

优先看：
- `Audio Send RTT`
- `Audio Recv RTT`
- 丢包、抖动、JitterBuffer 迹象
- 是否启用硬件 AEC、特定 Android 音频模式

结论方向：
- 网络 RTT 和抖动高：网络主因
- 硬件 AEC / 音频模式差异：设备/平台策略主因

### E. 设备路由 / 蓝牙 / 听筒扬声器异常

优先看：
- `Audio Output Route`
- `audioDeviceEvent` 的输入输出设备名
- iOS `CategoryOptionChange`

高频判断：
- 蓝牙模式切换造成音质/音量变化
- 业务侧修改 AudioSession 导致强制外放或停止活跃
- 虚拟声卡 / 显示器音频 / 外接设备被系统选为默认设备

## 证据不足时必须补充

以下情况必须追补证据，不能只凭猜测：
- 回声/噪声：补 `audio dump + 日志`
- 设备抢占/权限/系统打断：补 `audioDeviceEvent` 或客户端日志
- 路由异常：补设备名、连接方式、系统声音面板截图
- 偶现问题：补精确时间点、问题持续时长、是否能二次复现
- 疑似版本 case：补 SDK 版本、平台、机型

## 不要轻易下的结论

- 不要仅因“有接收码率”就断言播放一定正常。
- 不要仅因“有发送码率”就断言采集一定正常；muteLocalAudio 可能仍发静音包。
- 不要把回声/噪声直接归因于网络；文档明确说这类问题常需 dump 才能定责。
- 不要把所有无声都归因于 SDK；系统权限、AudioSession、设备 boost/AGC、蓝牙模式、后台限制都很常见。
- 不要把单一 case 版本结论直接泛化到所有版本。

## 升级条件

满足任一项可升级给研发/专项同学：
- 已补齐 dump + 日志，仍无法区分算法、设备、系统或 SDK 问题
- 指标显示链路正常，但主观异常稳定复现
- 特定机型/系统版本稳定复现，怀疑适配
- iOS AudioSession / Android 后台限制 / 蓝牙模式行为与 SDK 预期不一致
- 怀疑既有已知版本 bug，需确认是否命中历史 case

## 产出模板

```md
### 音频问题排查结论
- 现象：
- 时间点：
- 影响对象：谁听不到谁 / 谁听到回声或噪声
- 环境：平台 / 系统 / SDK版本 / 设备 / 音频外设

### 已核查链路
- 房间状态 / mute / subscribe：
- 采集侧（Nearin/Nearout/RecordFreq/audioDeviceEvent）：
- 上行侧（Send Bitrate/RTT/Loss）：
- 下行侧（Recv Bitrate/RTT/Loss/Decode）：
- 播放侧（Farin/PlaybackFreq/OutputRoute）：

### 当前判断
- 最可疑阶段：
- 判断依据：
- 是否需要补 dump / 日志 / 设备信息：

### 建议动作
- 客户侧建议：
- 内部升级方向：客户端 / 音频算法 / 网络 / 服务器 / 业务集成
```
