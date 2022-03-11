<template>
 <Border>
    <Echart :option="option"/>
 </Border>
</template>

<script lang="ts" setup>
import Border from './Border.vue'
import Echart from "./Echart.vue";
const option={
  tooltip: {},
  xAxis: {
    data: ['衬衫', '羊毛衫', '雪纺衫', '裤子', '高跟鞋', '袜子']
  },
  yAxis: {
    splitLine: {
      show: false
    }
  },
  series: [
    {
      name: '销量',
      type: 'bar',
      data: [5, 20, 36, 10, 10, 20]
    }
  ]
}
</script>

<style lang="scss" scoped>

</style>