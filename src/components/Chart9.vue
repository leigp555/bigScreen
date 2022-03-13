<template>
  <Echart :option="option" title="注册用户活跃度情况" root="echartI"/>
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
    data: ["货主","承运商","司机"]
  },
  series: [
    {
      name: '车型',
      type: 'bar',
      showBackground: true,
      barGap:px(30),
      barCateGoryGap:px(30),
      barWidth: px(10),
      itemStyle: {
        color: new echarts.graphic.LinearGradient(0, 0, 1, 0, [{
          offset: 0,
          color: "#3f5dfb"
        }, {
          offset: 0.6,
          color: "#2e82fe"
        },{
          offset: 0.90,
          color: "#65d0fa"
        },{
          offset: 0.97,
          color: "#ffffff"
        }, {
          offset: 1,
          color: "#ffffff"
        }], false),
        barBorderRadius: [0, px(20), px(20), 0],
      },
      label: {
        show: true,
        formatter: '{@score}%',
        fontSize: px(12),
        color: "white",
        verticalAlign: "center",
        position: "outside",
        distance: px(10)
      },
      data: [78.0,81.5,88.0].reverse()
    },
  ]
};


</script>

<style lang="scss" scoped>

</style>