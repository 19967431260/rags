## 问题描述

VUE.js 框架引入 V10.3.0 IM UIKit 后，没有输入框，Demo 同样有这个问题，怎么解决？

## 解决方法

您可以在 `App.vue` 中，在 `localOptions` 中自定义设置一个界面输入框，并自定义可选项。例如，在引入 AI 数字人后，您可以在 AI 翻译场景中，自定义语言输入框，示例如下：

```JavaScript
aiUserAgentProvider: {
getAITranslateLangs: (users: V2NIMAIUser[]): string[] => {
return ['英语', '日语', '韩语', '俄语', '法语', '德语']
},
},
```

更多详情，请参考 [`localOptions`](https://doc.yunxin.163.com/messaging-uikit/guide/Tg0NjMzMzg?platform=web#%E5%88%9D%E5%A7%8B%E5%8C%96%E5%8F%82%E6%95%B0) 和 [通过 AI 数字人在聊天时实现多国语言翻译](https://doc.yunxin.163.com/aiagents/guide/TIxODQyNzE?platform=client)。