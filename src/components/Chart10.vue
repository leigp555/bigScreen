<template>
  <Echart :option="option" title="注册用户人数占比情况" root="echartJ"/>
</template>

<script lang="ts" setup>
import Echart from "./Echart.vue";
import * as echarts from 'echarts/core';
import {ECOption} from "../type.d.ts/type";

const px = (value: number) => {
  return (value / 1920 * (window.pagWidth))
}

const option = {
  tooltip: {
    trigger: 'item'
  },
  legend: {
    show: true,
    top: '5%',
    left: "50%",
    textStyle: {
      fontSize: px(12),
      color:"white"
    }
  },
  series: [
    {
      name: 'Access From',
      type: 'pie',
      radius: ['40%', '70%'],
      avoidLabelOverlap: false,
      itemStyle: {
        borderRadius: 10,
        borderColor: '#fff',
        borderWidth: 2
      },
      label: {
        show: false,
        position: 'center'
      },
      emphasis: {
        label: {
          show: true,
          fontSize: '40',
          fontWeight: 'bold'
        }
      },
      labelLine: {
        show: false
      },
      data: [
        { value: 1048, name: 'Search Engine' },
        { value: 735, name: 'Direct' },
        { value: 580, name: 'Email' },
        { value: 484, name: 'Union Ads' },
        { value: 300, name: 'Video Ads' }
      ]
    }
  ]
};
</script>

<style lang="scss" scoped>

</style>