<template>
  <div id="main8"></div>
</template>

<script>
import * as echarts from 'echarts';

import data from '../data/bars-data'
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
          source: _.cloneDeep(data).map(item => { item[1] = item[1] + Math.random(); return item; }),
        },
        {
          source: _.cloneDeep(data).map(item => { item[1] = item[1] + Math.random(); return item; }),
        },
        {
          source: _.cloneDeep(data).map(item => { item[1] = item[1] + Math.random(); return item; }),
        },
        {
          source: _.cloneDeep(data).map(item => { item[1] = item[1] + Math.random(); return item; }),
        }
      ],
      series: [
        {
          datasetIndex: 0, // 数据源 0
          name: 'Fake Data',
          type: 'bar',
          stack: 'stackA', // 堆叠(名称任意)
          symbol: 'circle',
          symbolSize: 8,
          showSymbol: false,
          sampling: 'lttb',
          itemStyle: {
            color: '#ba43a9'
          },
          barWidth: 40  // bar宽
        },
        {
          datasetIndex: 1, // 数据源 1
          name: 'Fake Data2',
          type: 'bar',
          stack: 'stackA', // 堆叠
          symbol: 'circle',
          symbolSize: 8,
          showSymbol: false,
          sampling: 'lttb',
          itemStyle: {
            color: '#7eb26d'
          }
        },
        {
          datasetIndex: 2, // 数据源 2
          name: 'Fake Data2',
          type: 'bar',
          stack: 'stackA', // 堆叠
          symbol: 'circle',
          symbolSize: 8,
          showSymbol: false,
          sampling: 'lttb',
          itemStyle: {
            color: '#eab839'
          }
        },
        {
          datasetIndex: 3, // 数据源 3
          name: 'Fake Data2',
          type: 'bar',
          stack: 'stackA', // 堆叠
          symbol: 'circle',
          symbolSize: 8,
          showSymbol: false,
          sampling: 'lttb',
          itemStyle: {
            color: '#ff780a'
          }
        },
        {
          datasetIndex: 4, // 数据源 4
          name: 'Fake Data2',
          type: 'bar',
          stack: 'stackA', // 堆叠
          symbol: 'circle',
          symbolSize: 8,
          showSymbol: false,
          sampling: 'lttb',
          itemStyle: {
            color: '#f2495c'
          }
        }
      ]
    };

    let myChart = echarts.init(document.getElementById('main8'), 'dark');
    myChart.setOption(option)
    
  }
}
</script>

<style>
#main8 {
  width: 100%;
  height: 300px;
}
</style>
