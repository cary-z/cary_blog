---
title: 封装占比组件
catalog: true
comments: true
date: 2021-11-19 15:01:55
header-img: snail-bg.jpg
tags:
  - vue
categories:
  - encapsulate
---

## 封装占比的组件

```vue
<template>
  <div>
    <div v-if="isError">
      <span>数据异常</span>
    </div>
    <div v-else
         class="ProportionChart">
      <template v-for="(item,index) in proportion">
        <div :key="'proportion_'+index"
             :style="item"></div>
      </template>
    </div>
  </div>
</template>

<script>
export default {
  name: 'proportion-chart',
  props: {
    seriesData: {
      type: Object,
      required: true,
      deep: true
    }
  },
  data () {
    return {
      proportion: [],
    }
  },
  watch: {
    seriesData: {
      handler () {
        if (this.proportion.length === 0) {
          const color = ['#1D9BF6', '#FF001E', '#00BB28']
          for (let i = 0; i < this.seriesData.proportion.value.length; i++) {
            this.proportion.push({
              backgroundColor: color[this.seriesData.proportion.value.length - 1 - i],
              height: '35px',
              width: '100%',
              flexShrink: 0,
              transition: 'all 1s',
              transform: `translateX(${-(i + 1) * 100}%)`
            })
          }
        }
        this.$nextTick(() => {
          let num = 0
          for (let i = this.seriesData.proportion.value.length - 1; i >= 0; i--) {
            const offset = this.seriesData.proportion.value[i] / this.seriesData.total.value * 100
            this.proportion[i].transform = `translateX(${-(i + 1) * 100 + num + offset}%)`
            num += offset
          }
        })
      },
      immediate: true,
      deep: true
    }
  },
  computed: {
    isError () {
      const total = this.seriesData.total.value
      if (!total) { return true }
      return total < this.seriesData.proportion.value.reduce((pre, cur) => pre + cur, 0)
    },
  },
}
</script>
<style lang="scss" scoped>
::v-deep .ProportionChart {
  display: flex;
  width: 100%;
  height: 35px;
  background-color: gray;
  border-radius: 5px;
  overflow: hidden;
}
</style>
```

## 示例图片

![示例图](示例图.png)

## 传入数据结构

用了transform来提高性能，外部传入的数据为以下结构

```js
{
  total:{
    key:'score',// 总数描述
    value: 100// 总数值
  },
  proportion:{
    key:['Math','English','Chinese'],// 其他占比描述
    value:[99,55,77]// 其他占比的值
  }
}
```

