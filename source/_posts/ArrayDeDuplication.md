---
title: 数组去重处理
catalog: true
comments: true
header-img: snail-bg.jpg
tags:
  - js
categories:
  - algorithm
---

```js
const arr = [123,'webank',[1,2,3],'123',[{a:1,b:2}],[{b:2,a:1}],{c:3,b:2,a:1,d:null},'tencent',123,[1,2,3],{a:1,b:2,c:3,d:null},null,null,NaN,NaN]
function ArrayDeDuplication (arr) {
  function checkRepeat(obj1,obj2) {
    if (obj1 === null) return obj1 === obj2
    if (Object.getOwnPropertyNames(obj1).length !== Object.getOwnPropertyNames(obj2).length) return false
    for (const key in obj1) {
      const [item1,item2] = [obj1[key],obj2[key]]
      if (obj2.hasOwnProperty(key)) {
        if (typeof item1 === typeof item2 && typeof item1 === 'object') {
          return checkRepeat(item1,item2)
        } else if(Number.isNaN(item1) && Number.isNaN(item2)) return true
        else return item1 === item2
      } else return false
    }
  }
  // 双重循环
  const newArr = []
  for (const item of arr) {
    if (typeof item === 'object') {
      const flag = newArr.every(newItem => {
        if (typeof newItem !== 'object') return true
        else return !checkRepeat(item,newItem)
      })
      flag && newArr.push(item)
    } else {
      newArr.includes(item) || newArr.push(item)
    }
  }
  return newArr

  // reduce方法
  // return arr.reduce((acc,cur) => {
  //   if (typeof cur === 'object') {
  //     const flag = acc.every(newItem => {
  //       if (typeof newItem !== 'object') return true
  //       else if (Array.isArray(newItem) || newItem == null ||  item == null) return JSON.stringify(item) !== JSON.stringify(newItem)
  //       else return !checkRepeat(item,newItem)
  //     })
  //     flag && acc.push(cur)
  //   } else {
  //     acc.includes(cur) || acc.push(cur)
  //   }
  //   return acc
  // },[])
}
console.log(ArrayDeDuplication(arr))
```