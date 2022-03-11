<template>
  <Border>
    <div class="wrap">
      <div class="title">
        <svg class="icon" >
          <use xlink:href="#icon-tip"></use>
        </svg>
        <span>{{title}}</span>
      </div>
      <div class="echart">
        <div :id="root" class="echartMain"></div>
      </div>
    </div>
  </Border>

</template>

<script lang="ts" setup>
import * as echarts from 'echarts/core';
import Border from './Border.vue'
import {
  BarChart,
  // 系列类型的定义后缀都为 SeriesOption
  BarSeriesOption,
  LineChart,
  LineSeriesOption
} from 'echarts/charts';
import {
  TitleComponent,
  // 组件类型的定义后缀都为 ComponentOption
  TitleComponentOption,
  TooltipComponent,
  TooltipComponentOption,
  GridComponent,
  GridComponentOption,
  // 数据集组件
  DatasetComponent,
  DatasetComponentOption,
  // 内置数据转换器组件 (filter, sort)
  TransformComponent
} from 'echarts/components';
import { LabelLayout, UniversalTransition } from 'echarts/features';
import { CanvasRenderer } from 'echarts/renderers';
import {onMounted, ref, toRefs} from "vue";

echarts.use([
  TitleComponent,
  TooltipComponent,
  GridComponent,
  DatasetComponent,
  TransformComponent,
  BarChart,
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
  dom.value=document.getElementById(root.value!)
  const myChart = echarts.init(dom.value!);
  myChart.setOption(option.value);
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
  >.title{
    display: flex;
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
}

</style>