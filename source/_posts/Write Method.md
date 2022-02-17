---
title: 手写各种方法
catalog: true
comments: true
date: 2022-2-16 17:37:57
header-img: snail-bg.jpg
tags:
  - js
categories:
  - CommonMethods

---

## 手写new(简陋版)

```js
function _new (fn,...arg) {
    let obj = Object.create(fn.prototype)
    fn.apply(obj,arg)
    return obj
}
```

## 手写call(简陋版)

```js
function _call (obj,...arg) {
    const temFn = Symbol('temFn')
    obj[temFn] = this
    obj[temFn](...arg)
    delete obj[temFn]
}
```

## 手写instanceof(简陋版)

```js
function _instanceof (children,father) {
    while (children) {
        if (children.__proto__ === father.prototype) return true
        children = children.__proto__
    }
    return false
}
```

