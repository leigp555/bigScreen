<template>
  <Echart :option="option" title="承运商罚款情况" root="echartJ"/>
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
    x:px(0),
    y:px(0),
    x2:px(0),
    y2:px(0)
  },
  series: [
    {
      name: '车辆适配情况',
      type: 'pie',
      radius : '100%',//设置饼图大小
      center: ['45%', '40%'],
      radius: ['60%', '70%'],
      avoidLabelOverlap: false,
      labelLine: {
        show: false
      },
      data: [{ value: 98 }, { value: 2 },],

    }
  ]
};
</script>

<style lang="scss" scoped>

</style>