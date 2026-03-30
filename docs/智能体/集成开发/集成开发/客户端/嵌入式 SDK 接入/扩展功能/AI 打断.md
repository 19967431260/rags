本文介绍 AI 对话过程中的打断功能，通过合理运用打断机制，您可以构建出自然流畅、功能丰富的 AI 对话体验。打断分自动打断和手动打断两种类型。

## 前提条件

根据本文操作前，请确保您已经完成了：

- [基础实现流程](https://doc.yunxin.163.com/ai-hardware/guide/jUyMDgyNTQ?platform=client)
- [AEC 方案配置](https://doc.yunxin.163.com/messaging2/guide/TY2MjA2ODA?platform=client)

## 自动打断

自动打断依赖 [AEC 方案](https://doc.yunxin.163.com/messaging2/guide/TY2MjA2ODA?platform=client) 来区分用户语音和 AI 语音：

- **语音检测**：云端或设备本地的 VAD（Voice Activity Detection）检测到用户说话。
- **信号区分**：通过 AEC 处理，确认检测到的是用户语音而非 AI 回声。
- **自动中断**：系统自动停止当前 AI 播放，开始处理用户新的输入。

    ```mermaid
    flowchart LR
        A[AI 正在说话] --> B[检测到音频输入]
        B --> C{AEC 处理后<br/>确认为用户语音?}
        C -->|是| D[自动停止 AI 播放]
        C -->|否| E[继续 AI 播放]
        D --> F[处理用户新输入]
        E --> A
    ```

## 手动打断

所有 AI 对话都支持手动打断，通过调用 API 立即停止 AI 播放：

```cpp
// 手动打断 AI 说话
void MyAPPClass::ManualInterrupt() {
    int result = nertc_ai_manual_interrupt(engine_);
    if (result == 0) {
        RTC_LOGI(TAG, "Manual interrupt successful");
    } else {
        RTC_LOGE(TAG, "Manual interrupt failed: %d", result);
    }
}

// 在用户按键或触摸事件中调用
void MyAPPClass::OnUserInterruptTrigger() {
    // 例如：用户按下打断按钮
    ManualInterrupt();
}
```

## 监听打断状态

通过 `on_ai_data` 回调监听 AI 的说话状态变化：

```cpp
void MyAPPClass::OnAiData(const nertc_sdk_callback_context_t* ctx, 
                          nertc_sdk_ai_data_result_t* ai_data) {
    std::string type(ai_data->type, ai_data->type_len);
    std::string data(ai_data->data, ai_data->data_len);
    
    if (type == "event") {
        if (data == "audio.agent.speech_started") {
            RTC_LOGI(TAG, "AI started speaking");
            // 可以在此处更新 UI 状态
            UpdateUIState(AI_SPEAKING);
        } else if (data == "audio.agent.speech_stopped") {
            RTC_LOGI(TAG, "AI stopped speaking");
            // AI 停止说话，可能是自然结束或被打断
            UpdateUIState(AI_IDLE);
        } else if (data == "audio.agent.interrupted") {
            RTC_LOGI(TAG, "AI was interrupted");
            // AI 被打断的特殊处理
            HandleAIInterrupted();
        } else if (data == "audio.agent.interrupted") {
            RTC_LOGI(TAG, "AI was interrupted");
            // AI 被打断的特殊处理
            HandleAIInterrupted();
        }
    }
}
```