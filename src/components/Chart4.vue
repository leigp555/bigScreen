<template>
  <Echart :option="option" title="本月货主下单情况" root="echartD"/>
</template>

<script lang="ts" setup>
import Echart from "./Echart.vue";
import * as echarts from 'echarts/core';
import {ECOption} from "../type.d.ts/type";
const px=(value:number)=>{
  return (value/1920*(window.pagWidth))
}

const option:ECOption = {
    grid:{
    x:px(40),
    y:px(40),
    x2:px(50),
    y2:px(40)
  },
  xAxis: {
    type: 'category',
    boundaryGap: false,
    data: ['','第一周', '第二周', '第三周', '第四周',''],
    axisLabel: {
      show: true,
      fontSize: px(15),
      color: "#a19fc4"
    },
    axisTick: {
      alignWithLabel: false,
      show: false
    },
    name: "(周)",
    nameTextStyle: {
      fontSize: px(15)
    },
    nameGap: px(10),
  },

  yAxis: {
    name: "(%)",
    nameGap: px(10),
    nameLocation: "end",
    nameTextStyle: {
      fontSize: px(15),
      color: "#a19fc4",
    },
    splitLine: {
      show: false
    },
    axisLine: {
      show: true
    },
    axisLabel: {
      fontSize: px(12),
      color: "#a19fc4"
    }
  },
  series: [
    {
      data: [1.2, 2.0, 3.5, 5.0, 3.7,4],
      type: 'line',
      areaStyle: {}
    }
  ]
};






</script>

<style lang="scss" scoped>

</style>