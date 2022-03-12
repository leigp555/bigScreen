<template>
  <Border>
    <div class="wrap">
      <div class="title">
        <svg class="icon">
          <use xlink:href="#icon-tip"></use>
        </svg>
        <span>{{ title }}</span>
      </div>
      <div class="echart">
        <div :id="root" class="echartMain"></div>
      </div>
    </div>
    <div class="intro" v-if="intro">
      <div class="introA" v-for="(value,key,index) in intro" :key="index">
        <span>{{ key }}</span><span>{{ value }}</span>
      </div>
    </div>
  </Border>

</template>

<script lang="ts" setup>
import * as echarts from 'echarts/core';
import Border from './Border.vue'
import {
  BarChart, PieChart, LineChart, MapChart, LinesChart, GaugeChart
} from 'echarts/charts';
import {
  TitleComponent,
  TitleComponentOption,
  TooltipComponent,
  TooltipComponentOption,
  GridComponent,
  GridComponentOption,
  DatasetComponent,
  DatasetComponentOption,
  TransformComponent,
  VisualMapComponent
} from 'echarts/components';
import {LabelLayout, UniversalTransition} from 'echarts/features';
import {CanvasRenderer} from 'echarts/renderers';
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
  GaugeChart,
  MapChart,
  LabelLayout,
  UniversalTransition,
  CanvasRenderer
]);

const props = defineProps({
  option: Object,
  title: String,
  root: String,
  intro: Object
})

// 绘制图表
const {option, title, root, intro} = toRefs(props)
const dom = ref<HTMLElement | null>()
onMounted(() => {
  dom.value = document.getElementById(root.value!)
  const myChart = echarts.init(dom.value!);
  option.value && myChart.setOption(option.value);
})
</script>

<style lang="scss" scoped>
.echartMain {
  width: 100%;
  height: 100%;
}

@import "src/helper";
.wrap {
  display: flex;
  flex-direction: column;
  height: 100%;
  padding-left: px(20);

  > .title {
    display: flex;
    align-items: center;
    gap: px(10);

    > .icon {
      width: 1em;
      height: 1em;
      vertical-align: -0.15em;
      fill: currentColor;
      overflow: hidden;
    }

    > span {
      font-size: px(16);
    }
  }

  > .echart {
    flex-grow: 10;

  }
}


.intro {
  position: absolute;
  bottom: px(80);
  left: 50%;
  transform: translateX(-50%);
  font-size: px(20);

  > .introA {
    margin-bottom: px(5);

    > span:first-child {
      margin-right: px(5);
      color: #9391a7;
    }
  }
}


</style>