<template>
  <div id="main5"></div>
</template>

<script>
import * as echarts from 'echarts';

import data from '../data/bar-data'

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
      dataset: {
        source: data  // 默认 第一列是x 轴
      },
      series: [
        {
          name: 'Fake Data',
          type: 'bar', // 柱状图
          symbol: 'circle',
          symbolSize: 8,
          showSymbol: false,
          sampling: 'lttb',
          itemStyle: {
            color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [ // 渐变色柱图
              { offset: 0, color: '#4f86d9' },
              { offset: 1, color: 'transparent' }
            ]),
            borderColor: '#5794f2', // 描边
            borderWidth: 1 // 边宽
          }
        }
      ]
    };

    let myChart = echarts.init(document.getElementById('main5'), 'dark');
    myChart.setOption(option)
    
  }
}
</script>

<style>
#main5 {
  width: 100%;
  height: 300px;
}
</style>
