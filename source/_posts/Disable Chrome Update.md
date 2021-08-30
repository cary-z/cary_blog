---
title: mac禁用chrome更新
catalog: true
comments: true
date: 2021-07-28 17:22:59
header-img: snail-bg.jpg
tags:
  - bash
categories:
  - Google
---

## 禁止更新

在终端输入:
`cd ~/Library/Google`
`sudo chown root:wheel GoogleSoftwareUpdate`

## 恢复更新

在终端输入:
`cd ~/Library/Googlesudo chown root:staff GoogleSoftwareUpdate`
