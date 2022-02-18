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
function _new (constructor,...arg) {
    let obj = Object.create(constructor.prototype)
    const result = constructor.apply(obj,arg)
  	if (result && typeof (result === 'function' || typeof result === 'object')) {
        return result
    }
    return obj
}
```

## 手写call(简陋版)

```js
function _call () {
    const [_thisArg,...arg] = [...arguments]
    const thisArg = Object(_thisArg) || window
    const temFn = Symbol()
    thisArg[temFn] = this
    thisArg[temFn](...arg)
    delete thisArg[temFn]
}
```

## 手写instanceof(简陋版)

```js
function _instanceof (object,constructor) {
  	if (typeof object !== 'object' || object === null) return false
    while (object) {
        if (object.__proto__ === constructor.prototype) return true
        object = object.__proto__
    }
    return false
}
```

