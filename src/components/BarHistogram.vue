<template>
  <div id="main9"></div>
</template>

<script>
import * as echarts from 'echarts';

import data from '../data/bar2-data'

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
        source: data
      },
      series: [
        {
          name: 'Fake Data',
          type: 'bar',
          symbol: 'circle',
          symbolSize: 8,
          showSymbol: false,
          sampling: 'lttb',
          itemStyle: {
            color: 'rgba(115, 191, 105, .8)'
          },
          barCategoryGap: 0 // 无间隙 同一系列的柱间距离 设置0
        }
      ]
    };

    let myChart = echarts.init(document.getElementById('main9'), 'dark');
    myChart.setOption(option)
    
  }
}
</script>

<style>
#main9 {
  width: 100%;
  height: 300px;
}
</style>
