<template>
  <div id="main"></div>
</template>

<script>
import * as echarts from 'echarts';

import data from '../data/simple'
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
        // max: 80
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
            color: 'rgb(87,148,242)'
          },
          areaStyle: {
            color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [
              { offset: 0, color: 'rgb(87,148,242)' },
              { offset: 1, color: 'transparent' }
            ])
          },
          data: data
        },
        {
          name: 'Fake Data22222222',
          type: 'line',
          symbol: 'circle',
          symbolSize: 8,
          showSymbol: false,
          sampling: 'lttb',
          itemStyle: {
            color: '#73bf69'
          },
          areaStyle: {
            color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [
              { offset: 0, color: '#73bf69' },
              { offset: 1, color: 'transparent' }
            ])
          },
          data: _.cloneDeep(data).map(item => { item[1] = item[1] / 2; return item; })
        }
      ]
    };

    let myChart = echarts.init(document.getElementById('main'), 'dark');
    myChart.setOption(option)
    
  }
}
</script>

<style>
#main {
  width: 100%;
  height: 300px;
}
</style>
