---
track_type: "咨询类"
sub_type: "接口用法咨询"
product: "RTC"
feature: "云端录制"
updated: "2026-03-20"
---
<!-- entry: platform=iOS, created=2025-09-04, customers=["ISV云信-恒生芸泰-互联网医院-dx"], source=chat_history, frequency=1, tags=["云端录制", "iOS", "setParameters", "kNERtcKeyRecordAudioEnabled", "kNERtcKeyRecordVideoEnabled"] -->
## Q: iOS端音视频录制参数设置方法

**问题描述**：客户咨询：1349305433575350这个音视频通话没有收到录制的音视频抄送，询问如何设置录制参数。

**答案**：iOS端通过setParameters设置录制参数：kNERtcKeyRecordAudioEnabled开启云端音频录制（默认NO），kNERtcKeyRecordVideoEnabled开启云端视频录制（默认NO）。录制类型通过kNERtcKeyRecordType设置：0-单人和混录都要，1-只录混路，2-只录制单人。

---

