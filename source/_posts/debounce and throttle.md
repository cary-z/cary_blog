---
title: 防抖和节流
catalog: true
comments: true
date: 2021-11-22 11:13:49
header-img: snail-bg.jpg
tags:
  - js
categories:
  - CommonMethods

---

## 防抖

只要事件发生就延迟设定时间执行传入函数

```js
function debounce(fn, delay) {
  let timer = null
  return function (...args) {
    clearTimeout(timer)
    timer = setTimeout(() => {
      fn.apply(this, args)
    }, delay)
  }
}
```

## 节流

两次事件发生时间间隔超过设定时间间隔才执行传入函数

```js
function throttle(fn, wait) {
  let previous = 0
  return function (...args) {
    const now = Date.now()
    if (now - previous > wait) {
      previous = now
      fn.apply(this, args)
    }
  }
}
```

