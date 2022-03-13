<template>
  <map-chart :option="option" title="" root="echartMap"/>
</template>

<script lang="ts" setup>
import * as echarts from 'echarts/core';
import {inject} from "vue";
const screenWidth=inject("pagWidthX")
const px = (value: number) => {
  return (value / 1920 * (screenWidth as number))
}

import china from "../assets/china.json"
import MapChart from "./mapChart.vue";
//@ts-ignore
echarts.registerMap('CN', china);

const option = {
  color: "white",
  visualMap: {
    type: "piecewise",
    orient: "vertical",
    splitNumber: 5,
    show: true,
    min: 0,
    max: 10000,
    pieces: [
      {min: 9000},
      {min: 6000, max: 8999},
      {min: 3000, max: 5999},
      {min: 1, max: 2999},
      {max: 0}
    ],
    align: "left",
    left: px(60),
    bottom:px(30),
    realtime: true,
    calculable: true,
    itemWidth: px(15),
    itemHeight: px(15),
    showLabel: true,
    textStyle:{
      color:"white",
      fontSize: px(15)
    },
    itemGap:px(5),
    inRange: {
      color: ['#e0cba1','#fccf7c', '#f99b7f', '#f84c62'],
    },
  },
  tooltip: {
    trigger: 'item',
    formatter: '{b}<br/>{c} (件)'
  },
  series: [
    {
      name: '各省订单总量',
      type: 'map',
      map: 'CN',
      label: {
        show: true,
        fontSize: px(15),
        fontFamily:'-apple-system, "Noto Sans", "Helvetica Neue", Helvetica, "Nimbus Sans L", Arial, "Liberation Sans", "PingFang SC", "Hiragino Sans GB", "Noto Sans CJK SC", "Source Han Sans SC", "Source Han Sans CN", "Microsoft YaHei", "Wenquanyi Micro Hei", "WenQuanYi Zen Hei", "ST Heiti", SimHei, "WenQuanYi Zen Hei Sharp", sans-serif',
        fontWeight:"normal",
        color: "#f7f7f7"
      },
      top: px(20),
      left:px(210),
      bottom: px(20),
      data: [
        {name: '新疆', value: 1000},
        {name: '西藏', value: 600},
        {name: '内蒙古', value: 1200},
        {name: '青海', value: 2000},
        {name: '四川', value: 6000},
        {name: '黑龙江', value: 2500},
        {name: '甘肃', value: 2000},
        {name: '云南', value: 3000},
        {name: '广西', value: 4000},
        {name: '湖南', value: 6000},
        {name: '陕西', value: 5500},
        {name: '广东', value: 8000},
        {name: '吉林', value: 2800},
        {name: '河北', value: 4000},
        {name: '湖北', value: 6000},
        {name: '贵州', value: 5500},
        {name: '山东', value: 4000},
        {name: '江西', value: 5000},
        {name: '河南', value: 8000},
        {name: '辽宁', value: 6000},
        {name: '山西', value: 4000},
        {name: '安徽', value: 7000},
        {name: '福建', value: 8000},
        {name: '浙江', value: 8000},
        {name: '江苏', value: 8000},
        {name: '重庆', value: 6000},
        {name: '宁夏', value: 2500},
        {name: '海南', value: 3000},
        {name: '台湾', value: 2000},
        {name: '北京', value: 7000},
        {name: '天津', value: 5000},
        {name: '上海', value: 8000},
        {name: '香港', value: 8000},
        {name: '澳门', value: 5000}
      ],
    }
  ]
}
</script>

<style lang="scss" scoped>

</style>