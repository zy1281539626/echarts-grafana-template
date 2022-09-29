<template>
  <div id="main6"></div>
</template>

<script>
import * as echarts from 'echarts';

import data from '../data/point-data'
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
        min: function (value) { // 自动设置最小值
          return Math.floor(value.min);
        },
        max: function (value) { // 自动设置最大值
          return Math.ceil(value.max);
        },
      },
      grid: {
        left: "20",
        top: "20",
        right: "180",
        bottom: "20",
        containLabel: true
      },
      dataset: [
        {
          source: data
        },
        {
          source: _.cloneDeep(data).map(item => { item[1] = item[1] / 2 + Math.random() * 50; return item; })
        }
      ],
      series: [
        {
          name: 'Fake Data',
          datasetIndex: 0, // 数据源 0
          type: 'line', // line 模拟散点图+面积
          symbol: 'circle',
          symbolSize: 4,
          showSymbol: true, // 显示 symbol
          sampling: 'lttb',
          itemStyle: {
            color: '#5794f2'
          },
          lineStyle: {
            color: 'transparent' // 隐藏线条
          },
          areaStyle: {
            color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [ // 渐变色
              { offset: 0, color: 'rgb(87,148,242, .4)' },
              { offset: 1, color: 'transparent' }
            ])
          }
        },
        {
          name: 'Fake Data2',
          datasetIndex: 1, // 数据源 1
          type: 'line',
          symbol: 'circle',
          symbolSize: 4,
          showSymbol: true,
          sampling: 'lttb',
          itemStyle: {
            color: '#b877d9'
          },
          lineStyle: {
            color: 'transparent'
          },
          areaStyle: {
            color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [ 
              { offset: 0, color: 'rgb(184, 119, 217, .2)' },
              { offset: 1, color: 'transparent' }
            ])
          }
        },
      ]
    };

    let myChart = echarts.init(document.getElementById('main6'), 'dark');
    myChart.setOption(option)
    
  }
}
</script>

<style>
#main6 {
  width: 100%;
  height: 300px;
}
</style>
