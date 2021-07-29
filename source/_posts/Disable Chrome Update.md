---
title: mac禁用chrome更新
catalog: true
comments: true
header-img: snail-bg.jpg
tags:
- bash
---
## 禁止更新
在终端输入:
`cd ~/Library/Google`
`sudo chown root:wheel GoogleSoftwareUpdate`
## 恢复更新
在终端输入:
`cd ~/Library/Googlesudo chown root:staff GoogleSoftwareUpdate`