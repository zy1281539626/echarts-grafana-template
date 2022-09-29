<template>
  <div id="main4"></div>
</template>

<script>
import * as echarts from 'echarts';

import { data1, data2, data3 } from '../data/multiple-data'

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
      yAxis: [ // 多y轴
        {
          type: 'value',
          position: 'left', // 左侧
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
        {
          type: 'value',
          position: 'right', // 右侧
          splitLine: {
            show: false,
          },
          min: 40,
          max: 100
        },
        {
          type: 'value',
          position: 'right', // 右侧
          offset: 40, // 距离左边20px, 不然y轴会重合
          splitLine: {
            show: false // 刻度相差较大时隐藏掉网格线，只保留一个网格线（范围相似的可以共存）
          },
          min: 0,
          max: 1
        }
      ],
      grid: {
        left: "20",
        top: "20",
        right: "180",
        bottom: "20",
        containLabel: true
      },
      dataset: [ // 多数据源
        {
          dimensions: ['time', 'Requests/s'],
          source: data2
        },
        {
          dimensions: ['time', 'value'],
          source: data1
        },
        {
          dimensions: ['time', 'value'],
          source: data3
        }
      ],
      series: [
        {
          datasetIndex: 0, // 数据源 0
          yAxisIndex: 0, // y轴 0
          name: 'Fake Data',
          type: 'line',
          symbol: 'circle',
          symbolSize: 8,
          showSymbol: false,
          sampling: 'lttb',
          itemStyle: {
            color: '#f2cc0c'
          }
        },
        {
          datasetIndex: 1, // 数据源 1
          yAxisIndex: 1, // y轴 1
          name: 'Fake Data2',
          type: 'line',
          symbol: 'circle',
          symbolSize: 8,
          showSymbol: false,
          sampling: 'lttb',
          itemStyle: {
            color: 'rgb(87,148,242)'
          }
        },
        {
          datasetIndex: 2, // 数据源 2
          yAxisIndex: 2, // y轴 2
          name: 'Fake Data3',
          type: 'line',
          symbol: 'circle',
          symbolSize: 8,
          showSymbol: false,
          sampling: 'lttb',
          itemStyle: {
            color: '#73bf69'
          }
        }
      ]
    };

    let myChart = echarts.init(document.getElementById('main4'), 'dark');
    myChart.setOption(option)
    
  }
}
</script>

<style>
#main4 {
  width: 100%;
  height: 300px;
}
</style>
