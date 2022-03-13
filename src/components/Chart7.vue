<template>
  <Echart :option="option" title="承运商罚款情况" root="echartG"/>
</template>

<script lang="ts" setup>
import Echart from "./Echart.vue";
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
        color:"#fd7b7d"
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
          value: 1.5
        }
      ]
    },

  ]
}
</script>

<style lang="scss" scoped>

</style>