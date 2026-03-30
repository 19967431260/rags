如果默认通讯录界面（`contact-kit`）无法满足您的业务需求，您可通过本节介绍的参数进行界面自定义。

## 自定义参数

`contact-kit` 模块提供了自定义参数，您可以通过设置参数实现自定义界面效果。

### 关系导航组件

<div style="width:180px">参数</div> | 类型 | 说明 |
:---- | :---- | :--- |
`renderCustomContact` | `((contactType: ContactType) => Element)` | 自定义渲染通讯录内容，具体示例参考下文的 [自定义渲染通讯录内容](#自定义通讯录内容) | 
`prefix` | string | 样式前缀，默认值为"contact" |
`onItemClick` | `((contactType: ContactType) => void)` | 通讯录导航单击事件 |

### 关系详情组件

<div style="width:180px">参数</div> | 类型 | 说明 |
:---- | :---- | :--- |
`renderFriendListEmpty` | `(() => Element)` | 自定义渲染好友列表为空时的内容 |
`renderFriendListHeader` | `(() => Element)` | 自定义渲染好友列表头部内容，具体示例参考下文的 [自定义好友列表头部内容](#自定义好友列表头部内容) |
`renderBlackListEmpty` | `(() => Element)` | 自定义渲染 [黑名单列表为空时的内容](#黑名单列表为空时的内容) |
`renderBlackListHeader` | `(() => Element)` | 自定义渲染 [黑名单列表头部内容](#黑名单列表头部内容) |
`renderGroupListEmpty` | `(() => Element)` | 自定义渲染 [群组列表为空时的内容](#群组列表为空时的内容) |
`renderGroupListHeader` | `(() => Element)` | 自定义渲染 [群组列表头部内容](#群组列表头部内容) |
`renderMsgListEmpty` | `(() => Element)` | 自定义渲染 [消息中心为空时的内容](#消息中心为空时的内容) |
`renderMsgListHeader` | `(() => Element)` | 自定义渲染 [消息中心头部内容](#消息中心头部内容) |
`renderEmpty` | `(() => Element)` | 自定义渲染 [通讯录为空时的内容](#通讯录为空时的内容) |
`afterSendMsgClick` | `(() => void)` | 单击发送消息后的事件，例如在同意好友申请后，可自定义渲染 [打招呼消息](#自定义打招呼消息) |
`onFriendItemClick` | `((account: string) => void)` | 单击好友的事件 |
`onGroupItemClick` | `((team: Team) => void)` | 群组单击事件 |
`onBlackItemClick` | `((account: string) => void)` | 黑名单单击事件 |
`prefix` | string | 样式前缀，默认值："contact" |
`commonPrefix` | string | 公共样式前缀，默认值："common" |

## 自定义通讯录内容

- [查看在线示例](https://codesandbox.io/p/sandbox/zi-ding-yi-tong-xun-lu-nei-rong-2gdj8j)

  在 `IMAppProps` 传入正确的 `appkey`、`account` 和 `token` 即可在线预览效果。

- 示例代码

  :::::: div linked-codes
  ::: code React
  ```JSX/TSX
  const handleItemClick = (contactType) => {
    store.uiStore.selectContactType(contactType)
    if (contactType === 'msgList') {
      store.sysMsgStore.resetSystemMsgUnread()
    }
  }

  const renderCustomContact = (contactType) => {
    return contactType == 'msgList' ? (
      <div className='msg-list-wrapper' onClick={() => handleItemClick(contactType)}>
        <img className='msg-list' src="https://yx-web-nosdn.netease.im/common/67be494eeca64db51d2013cc682b0f93/75573bd7b485f23.jpeg" alt="" />
        <div className='msg-list-text'>消息中心</div>
      </div>
    ) : null
  }

  <ContactListContainer renderCustomContact={renderCustomContact}/>
  ```
  :::
  ::: code Vue2/Vue3
  ```TypeScript
  <template>
      <div ref="contactList" />
  </template>

  <script>
      ...
        mounted() {
            this.$uikit.render(
            ContactListContainer,
            {
            renderCustomContact:(contactType) => {
                  console.log('==========renderCustomContact===========', contactType);
                  const handleItemClick = (contactType) => {
                    const { store, nim } = window.__xkit_store__
                    store.uiStore.selectContactType(contactType)
                    if (contactType === 'msgList') {
                      store.sysMsgStore.resetSystemMsgUnread()
                    }
                  }
                  if(contactType === 'msgList'){
                    return compile(`<div className='msg-list-wrapper' onClick={() => context.handleItemClick(context.contactType)}>
                      <div className='msg-list-text'>消息中心</div>
                    </div>`, { handleItemClick, contactType })
                  }else{
                    return null
                  }
                }
            },
            this.$refs.contactList
          );
        }
  </script>
  ```
  :::
  ::::::

- 示例代码解读

  上述示例中的 `contactType` 可获取到四种类型，分别为 'blackList'（黑名单） | 'groupList'（我的群组） | 'friendList'（我的好友） | 'msgList'（消息中心），可根据不同 `contactType` 自定义渲染逻辑，若 `renderCustomContact` 返回为 null，则使用组件默认渲染逻辑。

- 效果比对

    <div style="width:50%">默认</div> | <div style="width:50%">自定义后</div>
    :---- | :----
    <img alt="通讯录内容.png" src="https://yx-web-nosdn.netease.im/common/744d22423aafce8c0086e19494bf6e89/通讯录内容.png" style="width:80%;border: 1px solid #BFBFBF;"> | <img alt="通讯录内容自定义 1.png" src="https://yx-web-nosdn.netease.im/common/accc7a581f79ec7e18ed23c11b68bdb6/通讯录内容自定义1.png" style="width:80%;border: 1px solid #BFBFBF;">

在集成通讯录组件时，如果不需要展示群组，您可在 `contactType` 为 'groupList' 时，return 一个空 div 即可，其余 `contactType` return null，使用默认渲染逻辑。

:::::: div linked-codes
::: code React
```JSX/TSX
<ContactListContainer
      renderCustomContact={(contactType) => {
        console.log(
          "==========renderCustomContact===========",
          contactType
        );
        if (contactType === "groupList") {
          return <div></div>;
        } else {
          return null;
        }
      }}
  />
```
:::
::: code Vue2/Vue3
```TypeScript
<template>
     <div ref="contactList" />
</template>

<script>
     ...
      mounted() {
          this.$uikit.render(
          ContactListContainer,
          {
            renderCustomContact: (contactType) => {
                console.log('==========renderCustomContact===========', contactType);
                if(contactType === 'groupList'){
                  return compile(`<div></div>`)
                }else{
                  return null
                }
              }
          },
          this.$refs.contactList
        );
      }
</script>
```
:::
::::::

## 自定义好友列表头部内容

- [查看在线示例](https://codesandbox.io/p/sandbox/zi-ding-yi-hao-you-lie-biao-tou-bu-nei-rong-ztttj7)

  在 `IMAppProps` 传入正确的 `appkey`、`account` 和 `token` 即可在线预览效果。

- 示例代码

  :::::: div linked-codes
  ::: code React
  ```JSX/TSX
  const renderFriendListHeader = () => {
    return (
      <div className='friend-header'>
        <img className='friend' src="https://yx-web-nosdn.netease.im/common/71a3ab830b7c8171580dad6ac2885fd6/邀请好友.png" alt="" />
        <div className='friend-text'>我的好友</div>
      </div>
    )
  }

  <ContactInfoContainer
      renderFriendListHeader={renderFriendListHeader}
    />
  ```
  :::
  ::: code Vue2/Vue3
  ```TypeScript
  <template>
      <div ref="contactInfo" />
  </template>

  <script>
      ...
        mounted() {
            this.$uikit.render(
            ContactInfoContainer,
            {
              renderFriendListHeader: () => {
                return compile(
                  `<div style={{ display: 'flex' }}>
                    <img src="https://yx-web-nosdn.netease.im/common/71a3ab830b7c8171580dad6ac2885fd6/邀请好友.png" alt="" />
                    <div>我的好友</div>
                  </div>`
                )
              }
            },
            this.$refs.contactInfo
          );
        }
  </script>
  ```
  :::
  ::::::

  :::note note
  `renderBlackListHeader`、`renderGroupListHeader`、`renderMsgListHeader` 同理。
  :::

- 效果比对

    <div style="width:50%">默认</div> | <div style="width:50%">自定义后</div>
    :---- | :----
    <img alt="好友列表头部.png" src="https://yx-web-nosdn.netease.im/common/bf7f0d6108b8b8d2b6836eb290fc6c1b/好友列表头部.png" style="width:80%;border: 1px solid #BFBFBF;"> | <img alt="好友列表头部内容自定义后 1.png" src="https://yx-web-nosdn.netease.im/common/41c1d58088c52319411059b6ae39bd96/好友列表头部内容自定义后1.png" style="width:80%;border: 1px solid #BFBFBF;">

## 自定义打招呼消息

- [查看在线示例](https://codesandbox.io/p/sandbox/zi-ding-yi-da-zhao-hu-xiao-xi-zs9mxy)

  在 `IMAppProps` 传入正确的 `appkey`、`account` 和 `token` 即可在线预览效果。

- 示例代码

  :::::: div linked-codes
  ::: code React
  ```JSX/TSX
  <ContactInfoContainer
        //...
        afterAcceptApplyFriend={(account) => {
          store.msgStore
            .sendTextMsgActive({
              scene: 'p2p',
              to: account,
              body: t('passFriendAskText'),
            })
            .then(() => {
              setModel('chat')
            })
        }}
      />
  ```
  :::
  ::: code Vue2/Vue3
  ```TypeScript
  <template>
      <div ref="contactInfo" />
  </template>

  <script>
      ...
        mounted() {
            this.$uikit.render(
            ContactInfoContainer,
            {
              afterAcceptApplyFriend: (account) => {
                const { store, nim } = window.__xkit_store__
                store.msgStore
                  .sendTextMsgActive({
                    scene: 'p2p',
                    to: account,
                    body: '我已经同意了好友申请，现在开始聊天吧~',
                  })
                  .then(() => {
                    this.model = "chat";
              })
            },
            this.$refs.contactInfo
          );
        }
  </script>
  ```
  :::
  ::::::

- 效果比对

    <div style="width:50%">默认</div> | <div style="width:50%">自定义后</div>
    :---- | :----
    <img alt="web 无打招呼.png" src="https://yx-web-nosdn.netease.im/common/f7295257c2f867af17b8a8ef20dd7b73/web无打招呼.png" style="width:80%;border: 1px solid #BFBFBF;"> | <img alt="web 打招呼.png" src="https://yx-web-nosdn.netease.im/common/738f13c59d8aed409a9f8550d899ea4a/web打招呼.png" style="width:80%;border: 1px solid #BFBFBF;">

## 相关图例

本节介绍通讯录界面的部分默认展示内容。

<a id="好友列表为空时的内容"></a>

**好友列表为空时的内容**

<img style="width:60%" src="https://yx-web-nosdn.netease.im/common/ec2a08183d020aa47ef43ef95943a913/好友列表为空时的内容.png" />

<a id="黑名单列表为空时的内容"></a>

**黑名单列表为空时的内容**

<img style="width:60%" src="https://yx-web-nosdn.netease.im/common/73af4dcaf5c071e6b3495ed247ca2a75/黑名单列表为空时的内容.png" />

<a id="黑名单列表头部内容"></a>

**黑名单列表头部内容**

<img style="width:60%" src="https://yx-web-nosdn.netease.im/common/d7ad0ca8bb388abecbab71dc65bec8ee/黑名单头部.png" />

<a id="群组列表为空时的内容"></a>

**群组列表为空时的内容**

<img style="width:60%" src="https://yx-web-nosdn.netease.im/common/e215db32e6c681019ec61fe5e9916dc2/群组列表为空时的内容.png" />

<a id="群组列表头部内容"></a>

**群组列表头部内容**

<img style="width:60%" src="https://yx-web-nosdn.netease.im/common/50b68aa04ea98cf34fb2f491e03673bd/群组列表头部内容.png" />

<a id="消息中心为空时的内容"></a>

**消息中心为空时的内容**

<img style="width:60%" src="https://yx-web-nosdn.netease.im/common/ad3a70b34a52b18c2283d5820e1e219e/消息中心为空时的内容.png" />

<a id="消息中心头部内容"></a>

**消息中心头部内容**

<img style="width:60%" src="https://yx-web-nosdn.netease.im/common/5cd6d25c211f5ec9ca298c9a4025577a/消息中心头部.png" />

<a id="通讯录为空时的内容"></a>

**通讯录为空时的内容**

<img style="width:60%" src="https://yx-web-nosdn.netease.im/common/2e60820dcf04554dc71d9b18fb7ab62b/通讯录为空时的内容.png" />