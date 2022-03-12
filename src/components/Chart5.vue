<template>
  <Echart :option="option" title="上周车辆使用情况" root="echartE"/>
</template>

<script lang="ts" setup>
import Echart from "./Echart.vue";
import * as echarts from 'echarts/core';
import {ECOption} from "../type.d.ts/type";

const px = (value: number) => {
  return (value / 1920 * (window.pagWidth))
}


const option: ECOption = {
  grid: {
    x: px(80),
    y: px(50),
    x2: px(80),
    y2: px(50)
  },
  xAxis: {
    data: ['周一', '周二', '周三', '周四', '周五', '周六', '周日'],
    type: 'category',
    axisLabel: {
      show: true,
      fontSize: px(15),
      color: "#a19fc4"
    },
    axisLine: {
      show: true,
      lineStyle: {
        color: '#272258'
      }
    },
    axisTick: {
      alignWithLabel: false,
      show: false
    }
    },
    yAxis: [
      {
        type: 'value',
        name: '(%)',
        splitLine: {
          show: false
        },
        nameGap: px(10),
        nameLocation:"end",
        nameTextStyle: {
          fontSize: px(15),
          color:"#a19fc4"
        },
        position: 'right',
        alignTicks: true,
        axisLine: {
          show: true,
          lineStyle: {
            color: '#272258'
          }
        },
        axisLabel: {
          fontSize: px(15),
          color:"#a19fc4"
        }
      },
      {
        type: 'value',
        name: '',
        splitLine: {
          show: false
        },
        position: 'right',
        alignTicks: true,
        offset: 80,
        axisLine: {
          show: true,
          lineStyle: {
            color: '#272258'
          }
        },
        axisLabel: {
          fontSize: px(15),
          color:"#a19fc4"
        }
      },
      {
        type: 'value',
        name: '(辆)',
        nameGap: px(10),
        nameLocation:"end",
        nameTextStyle: {
          fontSize: px(15),
          color:"#a19fc4"
        },
        splitLine: {
          show: false
        },
        position: 'left',
        alignTicks: true,
        axisLine: {
          show: true,
          lineStyle: {
            color: '#272258'
          }
        },
        axisLabel: {
          fontSize: px(15),
          color:"#a19fc4"
        }
      }
    ],
    series: [
      {
        name: '车辆总数',
        type: 'bar',
        barWidth: px(10),
        data: [
          7000, 7900, 7950, 8100,8200, 8150, 8125
        ]
      },
      {
        name: '运输中车辆',
        type: 'bar',
        yAxisIndex: 1,
        barWidth: px(10),
        data: [
          7900, 8600, 7950, 8100,8200, 8150, 8125
        ]
      },
      {
        name: '使用率',
        type: 'line',
        yAxisIndex: 2,
        data: [ 7900, 8100, 7950, 8100,8200, 8150, 8125],
      }
    ],
  }
</script>

<style lang="scss" scoped>

</style>