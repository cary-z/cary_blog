---
title: 二次封装EChart
catalog: true
comments: true
date: 2021-8-13 15:06:46
header-img: snail-bg.jpg
tags:
  - vue
categories:
  - encapsulate
---

## EChart目录

```
├── EChart
	├── chart-bar
		├──ChartBar.vue
		├──index.vue
	├── chart-line
		├──ChartLine.vue
		├──index.vue
	├── chart-pie
		├──ChartPie.vue
		├──index.vue
```

## ChartBar.vue源码

```vue
<template>
  <div id="chart"
       :style="{ width: '100%',height: height + 'px' }"></div>
</template>

<script>
import * as echarts from 'echarts'
export default {
  props: {
    seriesData: {
      // type: Array,
      required: true,
      default: () => []
    },
    height: {
      type: Number,
      default: 350
    }
    // extraOption: {
    //   type: Object,
    //   default: () => ({}),
    // },
  },
  data () {
    return {
      chart: null
    }
  },
  watch: {
    seriesData: {
      deep: true,
      handler () {
        this.updateChartView()
      }
    }
  },
  mounted () {
    this.chart = echarts.init(this.$el)
    this.updateChartView()
    window.addEventListener('resize', this.handleWindowResize)
  },
  beforeDestroy () {
    window.removeEventListener('resize', this.handleWindowResize)
  },
  methods: {
    // 更新echart视图
    updateChartView () {
      if (!this.chart) return
      const fullOption = this.assembleDataToOption()
      this.chart.setOption(fullOption, true)
    },
    // 将业务数据加入到基础样式配置中
    assembleDataToOption () {
      const name = this.seriesData.map(item => item.name)
      const value = this.seriesData.map(item => item.value)
      return {
        xAxis: {
          type: 'category',
          data: name,
          //轴线标签
          axisLabel: {
            interval: 0,
            fontSize: 15,
            rotate: name.length <= 6 ? 0 : 45
          },
        },
        yAxis: {
          type: 'value',
          //轴线标签
          axisLabel: {
            fontSize: 15
          }
        },
        series: [
          {
            data: value,
            type: 'bar',
            barWidth: '30%',
            barMaxWidth: '40px'
          }
        ],
        grid: {
          top: 25,
          left: 35,
          right: 10,
          bottom: 35
        },
        //鼠标悬浮显示
        tooltip: {
          trigger: 'axis',
          axisPointer: {
            type: 'shadow',
            label: false
          }
        }
      }
    },

    //当窗口缩放时，echart动态调整自身大小
    handleWindowResize () {
      if (!this.chart) return
      this.chart.resize()
    }
  }
}
</script>
```

## index.vue源码

```vue
<template>
  <div>
    <div class="text-center"
         v-if="isEmpty">
      <span>暂无数据</span>
    </div>
    <chart-bar v-else
               v-bind="this.$props" />
  </div>
</template>

<script>
import ChartBar from './ChartBar'

export default {
  name: 'Chart-Bar',
  components: { ChartBar },
  props: ChartBar.props,
  computed: {
    isEmpty () {
      return !this.seriesData || this.seriesData.length === 0
    }
  }
}
</script>
```

该方法仅为思路，具体封装按照需求处理

