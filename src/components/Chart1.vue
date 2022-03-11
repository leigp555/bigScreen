<template>
 <Border>
   <div class="wrap">
     <div class="title">
       <svg class="icon" >
         <use xlink:href="#icon-tip"></use>
       </svg>
       <span>本月货主下单情况</span>
     </div>
     <div class="echart">
       <Echart :option="option"/>
     </div>
   </div>
 </Border>
</template>

<script lang="ts" setup>
import Border from './Border.vue'
import Echart from "./Echart.vue";
import * as echarts from 'echarts/core';
import {ECOption} from "../type.d.ts/type";
const px=(value:number)=>{
  return (value/1920*(window.pagWidth))
}
const option:ECOption={
  grid:{
    x:px(60),
    y:px(50),
    x2:px(50),
    y2:px(50)
  },
  xAxis: {
    data: ['第一周', '第二周', '第三周', '第四周'],
    axisLabel:{
      show: true,
      fontSize:px(15)
    },
    axisTick: {
      alignWithLabel: false,
      show: false
    },
    name:"(周)",
    nameTextStyle: {
      fontSize: 12
    },
    nameGap: px(10),
  },

  yAxis: {
    name:"(笔)",
    nameGap: px(10),
    nameLocation:"end",
    nameTextStyle: {
      fontSize: 12
    },
    splitLine: {
      show: false
    },
    axisLine: {
      show: true
    },
    axisLabel:{
      fontSize:px(12)
    }
  },
  series: [
    {
      name: '笔',
      type: 'bar',
      barWidth: px(20),
      itemStyle: {
          color: new echarts.graphic.LinearGradient(0, 1, 0, 0, [{
            offset: 0,
            color: "#1268f3"
          }, {
            offset: 0.6,
            color: "#08a4fa"
          }, {
            offset: 1,
            color: "#01ccfe"
          }], false),
        barBorderRadius:[px(20), px(20), 0, 0]
      },
      data: [11036, 16521, 14780, 23467],
      label: {
        show: true,
        fontSize:px(12),
        color: "white",
        verticalAlign: "top",
        position:"top",
        distance:px(15)
      }
    },
  ]
}
</script>

<style lang="scss" scoped>
@import "src/helper";
.wrap{
  display: flex;
  flex-direction: column;
  height: 100%;
  padding-left: px(20);
 >.title{
   display: flex;
   align-items: center;
   >.icon{
     width: 1em; height: 1em;
     vertical-align: -0.15em;
     fill: currentColor;
     overflow: hidden;
   }
 }
  >.echart{
    flex-grow: 10;

  }
}

</style>