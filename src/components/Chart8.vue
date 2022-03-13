<template>
  <Echart :option="option" title="取件情况" root="echartH"/>
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
      radius : '70%',
      startAngle: 90,
      endAngle: -270,
      min: 0,
      max: 100,
      splitNumber: 20,
      itemStyle: {
        color:"#334084"
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
          color: '#334084',
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
        show:false,
        valueAnimation: false,
        width: '15%',
        lineHeight: px(15),
        borderRadius: 8,
        offsetCenter: [0, '0%'],
        fontSize: px(15),
        fontWeight: 'bolder',
        formatter: '{value}%',
        color: 'white'
      },
      data: [
        {
          value: 99.9
        }
      ]
    },
    {
      type: 'gauge',
      center: ['48%', '45%'],
      radius : '70%',
      startAngle: 90,
      endAngle: -270,
      min: 0,
      max: 100,
      splitNumber: 20,
      itemStyle: {
        color: new echarts.graphic.LinearGradient(1, 0, 0, 0, [{
          offset: 0,
          color: "#f7ce7e"
        }, {
          offset: 1,
          color: "#ed737e"
        }], false),
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
        width: '15%',
        lineHeight: px(15),
        borderRadius: 8,
        offsetCenter: [0, '0%'],
        fontSize: px(15),
        fontWeight: 'bolder',
        formatter: '{value}%',
        color: 'white'
      },
      data: [
        {
          value: 98
        }
      ]
    },

  ]
}
</script>

<style lang="scss" scoped>

</style>