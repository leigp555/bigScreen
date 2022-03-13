<template>
  <Echart :option="option" title="运单到达情况" root="echartF"/>
</template>

<script lang="ts" setup>
import Echart from "./Echart.vue";
import * as echarts from 'echarts/core';
import {ECOption} from "@/type.d.ts/type";
const px=(value:number)=>{
  return (value/1920*(window.pagWidth))
}

const option:ECOption = {
  series: [
    {
      type: 'gauge',
      center: ['48%', '45%'],
      radius : '65%',
      startAngle: 90,
      endAngle: -270,
      min: 0,
      max: 100,
      splitNumber: 20,
      itemStyle: {
        color: new echarts.graphic.LinearGradient(1, 0, 0, 0, [{
          offset: 0,
          color: "#1daeff"
        }, {
          offset: 1,
          color: "#395ef5"
        },], false),
      },
      progress: {
        show: true,
        width: px(10)
      },
      pointer: {
        show: false
      },
      axisLine: {
        lineStyle: {
          width: px(10),
          color: '#f5ce85',
        }
      },
      axisTick: {
        show:false,
      },
      splitLine: {
        show:false,
      },
      axisLabel: {
        show:false,
      },
      anchor: {
        show: false
      },
      title: {
        show: false
      },
      detail: {
        valueAnimation: false,
        width: '40%',
        lineHeight: px(40),
        borderRadius: 8,
        offsetCenter: [0, '0%'],
        fontSize: px(32),
        fontWeight: 'bolder',
        formatter: '{value}%',
        color: 'white'
      },
      data: [
        {
          value: 98.5
        }
      ]
    },
  ]
}
</script>

<style lang="scss" scoped>

</style>