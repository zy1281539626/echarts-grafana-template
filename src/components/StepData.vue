<template>
  <div id="main3"></div>
</template>

<script>
import * as echarts from 'echarts';

import data from '../data/step-data'

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
        dimensions: ['time', 'Requests/s'],
        source: data
      },
      series: [
        {
          name: 'Fake Data',
          type: 'line',
          step: 'start', // 阶梯 start middle end
          symbol: 'circle',
          symbolSize: 8,
          showSymbol: true, // 显示 symbol
          sampling: 'lttb',
          itemStyle: {
            color: 'rgb(87,148,242)'
          },
          areaStyle: {
            color: 'rgba(87,148,242, 0.2)'
          }
        }
      ]
    };

    let myChart = echarts.init(document.getElementById('main3'), 'dark');
    myChart.setOption(option)
    
  }
}
</script>

<style>
#main3 {
  width: 100%;
  height: 300px;
}
</style>
