## 问题描述

通过 SDK 上传本地的 x-m4a 文件，该文件的 NOS 链接无法在 safari 浏览器上播放。

## 问题原因

未声明文件类型导致无法播放。

## 解决方案

在生成的链接后拼接 `&contentType=audio/x-m4a`。

