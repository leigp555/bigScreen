<template>
  <Echart :option="option" title="注册用户活跃度情况" root="echartI"/>
</template>

<script lang="ts" setup>
import Echart from "./Echart.vue";
import * as echarts from 'echarts/core';
import {ECOption} from "../type.d.ts/type";

const px = (value: number) => {
  return (value / 1920 * (window.pagWidth))
}

const option: ECOption = {
  // tooltip: {
  //   trigger: 'axis',
  //   axisPointer: {
  //     type: 'shadow'
  //   }
  // },
  grid: {
    x: px(80),
    y: px(20),
    x2: px(50),
    y2: px(30)
  },
  xAxis: {
    type: 'value',
    boundaryGap: [0, 0.01],
    axisLabel: {
      show: false,
    },
    splitLine: {
      show: false
    },
  },
  yAxis: {
    type: 'category',
    splitLine: {
      show: false
    },
    axisTick: {
      alignWithLabel: false,
      show: false
    },
    axisLine: {
      show: false
    },
    axisLabel: {
      fontSize: px(12),
      color:"#a19fc4"
    },
    data: ['17.5m', '9.6m', '4.2m', '17.5(150)m', '9.6(75)m', '14.5m',
      '6.8m', '7.6m', '13.5m', '17.5(180)m']
  },
  series: [
    {
      name: '车型',
      type: 'bar',
      barGap:px(30),
      barCateGoryGap:px(30),
      barWidth: px(10),
      itemStyle: {
        color: new echarts.graphic.LinearGradient(0, 0, 1, 0, [{
          offset: 0,
          color: "#fccf7c"
        }, {
          offset: 0.6,
          color: "#f99b7f"
        }, {
          offset: 1,
          color: "#fd6e80"
        }], false),
        barBorderRadius: [0, px(20), px(20), 0],
      },
      data: [11036, 16521, 14780, 23467],
      label: {
        show: true,
        fontSize: px(12),
        color: "white",
        verticalAlign: "center",
        position: "right",
        distance: px(15)
      },
      data: [2680, 2382, 1301,942, 624, 407,312,201,137,108].reverse()
    },
  ]
};


</script>

<style lang="scss" scoped>

</style>