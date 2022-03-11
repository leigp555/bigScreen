<template>
 <div id="echartMain"></div>
</template>

<script lang="ts" setup>
import * as echarts from 'echarts/core';
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
import {computed, onMounted, ref} from "vue";
import {ECOption} from "../type.d.ts/type";
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
  option:Object
})

// 绘制图表
const option=computed(()=>{
  return props.option
})
const dom=ref<HTMLElement|null>()
onMounted(()=>{
  dom.value=document.getElementById('echartMain')
  const myChart = echarts.init(dom.value!);
  myChart.setOption(option.value);
})
</script>

<style lang="scss" scoped>
#echartMain{
  width: 100%;
  height: 100%;
}
</style>