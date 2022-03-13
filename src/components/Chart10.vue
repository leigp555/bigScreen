<template>
  <Echart :option="option" title="注册用户人数占比情况" root="echartJ"/>
</template>

<script lang="ts" setup>
import Echart from "./Echart.vue";
const px = (value: number) => {
  return (value / 1920 * (window.pagWidth))
}

const option = {
  legend: {
    show: true,
    top: '30%',
    right: "20%",
    itemGap:px(15),
    itemWidth: px(10),
    itemHeight: px(10),
    orient: "vertical",
    textStyle: {
      fontSize: px(12),
      color:"white",
    },
    itemStyle: {
      borderWidth: 0,
      borderRadius: "50%"
    }
  },
  series: [
    {
      type: 'pie',
      radius: ["40%","60%"],
      top: "0%",
      left: 'left',
      width: px(300),
      color:["#10e8eb","#f9997d","#18a9fc"],
      itemStyle: {

      },
      labelLine: {
        length: px(15),
        length2: 0,
        textStyle: {
          fontSize:px(15),
        },
        maxSurfaceAngle: px(80)
      },
      label: {
        fontSize: px(12),
        fontWeight: "normal",
        color:"white",
        padding: [px(6), px(6), px(6), px(6)],
        formatter: '{b}'.replace(/[0-9]+/,""),
        edgeDistance: px(12),
        rich: {
          fontSize:px(12)
        }
      },
        data: [
          { value: 1625, name: '货主 1625' },
          { value: 326, name: '承运商 326'  },
          { value: 8039, name: '司机 8039' },
        ]
    }
  ]
};







</script>

<style lang="scss" scoped>

</style>