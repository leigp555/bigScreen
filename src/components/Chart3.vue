<template>
  <Echart :option="option" title="承运商车辆适配情况" root="echartC" :intro="intro"/>
</template>

<script lang="ts" setup>
import Echart from "./Echart.vue";
import * as echarts from 'echarts/core';
import {inject} from "vue";
const screenWidth=inject("pagWidthX")
const px = (value: number) => {
  return (value / 1920 * (screenWidth as number))
}
const option = {
  series: [
    {
      type: 'gauge',
      center: ['48%', '35%'],
      radius : '55%',
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
        width: px(5)
      },
      pointer: {
        show: false
      },
      axisLine: {
        lineStyle: {
          width: px(5),
          color: '#f5ce85',
        }
      },
      axisTick: {
        distance: px(-30),
        splitNumber: 2,
        lineStyle: {
          width: px(2),
          length:px(14),
          color: '#03e4e6'
        }
      },
      splitLine: {
        show:false,
        distance: px(-50),
        length: px(30),
        lineStyle: {
          width:px(3),
          color: '#999'
        }
      },
      axisLabel: {
        show:false,
        distance: px(-60),
        color: '#999',
        fontSize: px(15)
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
          value: 98
        }
      ]
    },
  ]
};
const intro={"派车数":"483,080","适配数":"483,218"}
</script>

<style lang="scss" scoped>

</style>