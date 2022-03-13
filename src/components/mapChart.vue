<template>
    <div class="wrap">
      <div class="title">
        <svg class="icon" >
          <use xlink:href="#icon-tip"></use>
        </svg>
        <span>各省订单量概览</span>
      </div>
      <div class="echart">
        <div :id="root" class="echartMain"></div>
      </div>
      <span>注:此图仅显示中国部分地区</span>
    </div>
</template>

<script lang="ts" setup>
import * as echarts from 'echarts/core';
import {
  BarChart,PieChart,LineChart, MapChart, LinesChart} from 'echarts/charts';
import {
  TitleComponent,
  TooltipComponent,
  GridComponent,
  DatasetComponent,
  TransformComponent,
  VisualMapComponent
} from 'echarts/components';
import { LabelLayout, UniversalTransition } from 'echarts/features';
import { CanvasRenderer } from 'echarts/renderers';
import {onMounted, ref, toRefs} from "vue";

echarts.use([
  TitleComponent,
  TooltipComponent,
  VisualMapComponent,
  GridComponent,
  DatasetComponent,
  TransformComponent,
  BarChart,
  PieChart,
  LinesChart,
  LineChart,
  MapChart,
  LabelLayout,
  UniversalTransition,
  CanvasRenderer
]);
const props=defineProps({
  option:Object,
  title:String,
  root:String
})

// 绘制图表
const {option,title,root}=toRefs(props)

const dom=ref<HTMLElement|null>()
onMounted(()=>{
  dom.value=document.getElementById(root!.value!)
  const myChart = echarts.init(dom.value!);
  option!.value&&myChart.setOption(option!.value);
})
</script>

<style lang="scss" scoped>
.echartMain{
  width: 100%;
  height: 100%;
}
@import "src/helper";
.wrap{
  display: flex;
  flex-direction: column;
  height: 100%;
  padding-left: px(20);
  position: relative;
  top: 0;
  left: 0;
  >.title{
    display: flex;
    position: absolute;
    top: px(60);
    left: px(70);
    align-items: center;
    gap: px(10);
    >.icon{
      width: 1em; height: 1em;
      vertical-align: -0.15em;
      fill: currentColor;
      overflow: hidden;
    }
    >span{
      font-size: px(16);
    }
  }
  >.echart{
    flex-grow: 10;

  }
  >span{
    font-size: px(12);
    position: absolute;
    bottom: 0;
    left: 50%;
    transform: translateX(-50%);
  }
}

</style>