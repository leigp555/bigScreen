<template>
  <Echart :option="option" title="本月货主下单情况" root="echartD"/>
</template>

<script lang="ts" setup>
import Echart from "./Echart.vue";
import {inject} from "vue";
const screenWidth=inject("pagWidthX")
const px = (value: number) => {
  return (value / 1920 * (screenWidth as number))
}
const option = {
    grid:{
    x:px(40),
    y:px(40),
    x2:px(50),
    y2:px(40)
  },
  xAxis: {
    type: 'category',
    boundaryGap: false,
    data: ['第一周', '第二周', '第三周', '第四周',''],
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
      data: [ 2.0, 3.5, 5.0, 3.7,4],
      type: 'line',
      areaStyle: {
        color:"#331c52"
      },
      lineStyle: {
        color: "#fe9a80"
      },
      itemStyle: {
        color: "#ffffff"
      },
      label: {
        show: true,
        fontSize:px(12),
        color: "white",
        verticalAlign: "top",
        position:"top",
        distance:px(15)
      }
    }
  ]
};






</script>

<style lang="scss" scoped>

</style>