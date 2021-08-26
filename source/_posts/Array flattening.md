---
title: 数组扁平化处理
catalog: true
comments: true
header-img: snail-bg.jpg
tags:
  - js
categories:
  - algorithm

---

提供一个测试数组以及记录时间代码

```js
// 测试数组
const arr = [[[[1,2],[3,4]],[5,6]],[[7,8,9],[10,11,12,13]],14,[[[15,16],17],18,[[19,20],21,22]],[23,24],25,[[[26,[27,28,[29,30]]],31,32],33,34,35],36,[37,38,39,40]]
// 记录运行时间
console.time('数组扁平化')
const lastArr = flatten(arr)
console.timeEnd('数组扁平化')
console.log(lastArr)
```

## 用数组的reduce方法递归

```js
function flatten(arr) {
  return arr.reduce((accumulator, currentValue) => {
    return accumulator.concat(Array.isArray(currentValue) ? flatten(currentValue) : currentValue)
  }, [])
}
```

## for循环判断数组递归

```js
function flatten(arr) {
  let result = []
  for (let i = 0; i < arr.length; i++) {
    if (Array.isArray(arr[i])) result.push(...flatten(arr[i]))
    else result.push(arr[i])
  }
  return result
}
```

## while循环加数组的some方法

```js
function flatten(arr) {
  while (arr.some(item => Array.isArray(item))) { 
    arr = [].concat(...arr)
  }
  return arr
}
```

## 数组的flat方法

```js
function flatten(arr) {
  return arr.flat(Infinity)
}
```

## 总结

个人测试flat方法性能最好，其余性能接近（个人看法）