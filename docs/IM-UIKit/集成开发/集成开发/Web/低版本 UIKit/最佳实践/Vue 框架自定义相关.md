
若您使用 Vue 框架引入 UIKit 组件，在自定义 UI 时需要注意一些写法问题。

本文主要介绍使用 Vue 框架自定义 UI 的相关问题。


## Vue 框架自定义渲染

### 自定义 DOM 如何进行事件绑定

例如，若需要在自定义渲染会话 header 时，给自定义会话 header 绑定事件，可以在 `methods` 中进行定义事件函数，通过 compile 的第二个参数传入（第二个参数要求是一个对象，key 和 value 自行定义），然后通过 `context.xxxx` 访问。

:::note notice
注意 click 需要写成 onClick 、输入框事件需要写成 onChange 等。
:::

<br/>

```
<template>
     <div ref="chat" />
</template>

<script>
     ...
      methods: {
        onClickHeader() {
          console.log('==========sendMsg===========');
        }
      },
      mounted() {
          this.$uikit.render(
          ChatContainer,
          {
            renderHeader :(options) => {
               //...
              return compile(
              `<div onClick={context.onClickHeader} style={{display: 'flex', alignItems: 'center'}}>
                // ...
              </div>`, { onClickHeader: this.onClickHeader })
            }
           },
          this.$refs.chat
        );
      }
</script>
```

