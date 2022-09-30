<template>
  <div id="main7"></div>
</template>

<script>
import * as echarts from 'echarts';

import { data1, data2 } from '../data/mix-data'
import _ from 'lodash'
export default {
  name: 'SimpleGraph',
  mounted () { 
    let option = {
      tooltip: {
        trigger: 'axis',
        axisPointer: {
          type: 'cross',
          label: {
            show: false
          }
        },
        backgroundColor: '#22252b',
        borderColor: 'transparent',
        textStyle: {
          color: "#fff"
        }
      },
      legend: {
        top: 20,
        right: 0,
        orient: 'vertical',
        padding: [0, 20],
        icon: 'rect',
        itemWidth: 14,
        itemHeight: 4
      },
      xAxis: {
        type: 'time',
        splitLine: {
          show: true,
          lineStyle: {
            color: 'rgba(255,255,255,.1)'
          }
        },
        axisLine: {
          show: false
        },
        axisTick: {
          lineStyle: {
            color: 'rgba(255,255,255,0.1)'
          }
        },
        axisLabel: {
          formatter: '{HH}:{mm}' // 'time' 时可用
        }
      },
      yAxis: {
        type: 'value',
        splitLine: {
          show: true,
          lineStyle: {
            color: 'rgba(255,255,255,.1)'
          }
        },
        max: function (value) { // 自动设置最大值
          return Math.ceil(value.max) + 300;
        },
      },
      grid: {
        left: "20",
        top: "20",
        right: "180",
        bottom: "20",
        containLabel: true
      },
      series: [
        {
          name: 'Fake Data',
          type: 'line',
          symbol: 'circle',
          symbolSize: 8,
          showSymbol: false,
          sampling: 'lttb',
          itemStyle: {
            color: '#b7dbab'
          },
          areaStyle: {
            color: '#b7dbab'
          },
          data: data1,
          z: 4 // 层级4
        },
        {
          name: 'Fake Data2',
          type: 'line',
          symbol: 'circle',
          symbolSize: 8,
          showSymbol: false,
          sampling: 'lttb',
          itemStyle: {
            color: '#7eb26d'
          },
          areaStyle: {
            color: '#7eb26d'
          },
          data: _.cloneDeep(data1).map(item => { item[1] = item[1] * 2; return item; }),
          z: 3 // 层级3
        },
        {
          name: 'Fake Data3',
          type: 'line',
          symbol: 'circle',
          symbolSize: 8,
          showSymbol: false,
          sampling: 'lttb',
          itemStyle: {
            color: '#508642'
          },
          areaStyle: {
            color: '#508642'
          },
          data: _.cloneDeep(data1).map(item => { item[1] = item[1] * 3; return item; }),
          z: 2 // 层级2
        },
        {
          name: 'Fake Data4',
          type: 'line',
          symbol: 'circle',
          symbolSize: 8,
          showSymbol: true, // 一直显示symbol
          sampling: 'lttb',
          itemStyle: {
            color: '#eab839'
          },
          data: _.cloneDeep(data1).map(item => { item[1] = item[1] * 3 + Math.random() * 200 + 100; return item; }),
          z: 1 // 层级1
        },
        {
          name: 'Fake Data5',
          type: 'bar', // 柱状
          symbol: 'circle',
          symbolSize: 8,
          showSymbol: false,
          sampling: 'lttb',
          itemStyle: {
            color: 'rgba(226, 77, 66, 0.7)'
          },
          barWidth: 20, // bar 宽度
          data: data2,
          z: 5 // 层级5
        },
      ]
    };

    let myChart = echarts.init(document.getElementById('main7'), 'dark');
    myChart.setOption(option)
    
  }
}
</script>

<style>
#main7 {
  width: 100%;
  height: 300px;
}
</style>
