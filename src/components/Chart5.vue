<template>
  <Echart :option="option" title="上周车辆使用情况" root="echartE"/>
</template>

<script lang="ts" setup>
import Echart from "./Echart.vue";
import {ECOption} from "@/type.d.ts/type";

const px = (value: number) => {
  return (value / 1920 * (window.pagWidth))
}
const data1=[6500, 7700, 7250, 7500,8000, 7200, 6900]
const data2=[7000, 7900, 7950, 8100,8200, 8150, 8125]
const data3=[]
for (let i=0;i<data1.length;i++){
   data3.push((data1[i]/data2[i])*100)
}
const option: ECOption = {
  grid: {
    x: px(80),
    y: px(50),
    x2: px(80),
    y2: px(50)
  },
  legend: {
    show: true,
    top: 0,
    right: "20%",
    itemGap:px(15),
    itemWidth: px(10),
    itemHeight: px(10),
    orient: "horizontal",
    textStyle: {
      fontSize: px(12),
      color:"white",
    },
    itemStyle: {
      borderWidth: 0,
      borderRadius: "50%"
    }
  },
  xAxis: {
    data: ['周一', '周二', '周三', '周四', '周五', '周六', '周日'],
    type: 'category',
    axisLabel: {
      show: true,
      fontSize: px(15),
      color: "#a19fc4"
    },
    axisLine: {
      show: true,
      lineStyle: {
        color: '#272258'
      }
    },
    axisTick: {
      alignWithLabel: false,
      show: false
    }
    },
    yAxis: [
      {
        type: 'value',
        name: '(辆)',
        splitLine: {
          show: false
        },
        nameGap: px(10),
        nameLocation:"end",
        nameTextStyle: {
          fontSize: px(15),
          color:"#a19fc4"
        },
        position: 'left',
        alignTicks: true,
        axisLine: {
          show: true,
          lineStyle: {
            color: '#272258'
          }
        },
        axisLabel: {
          fontSize: px(15),
          color:"#a19fc4"
        }
      },
      {
        type: 'value',
        name: '',
        splitLine: {
          show: false
        },
        position: 'left',
        alignTicks: true,
        offset: 80,
        axisLine: {
          show: true,
          lineStyle: {
            color: '#272258'
          }
        },
        axisLabel: {
          fontSize: px(15),
          color:"#a19fc4"
        }
      },
      {
        type: 'value',
        name: '(%)',
        nameGap: px(10),
        nameLocation:"end",
        scale:true,
        nameTextStyle: {
          fontSize: px(15),
          color:"#a19fc4"
        },
        splitLine: {
          show: false
        },
        position: 'right',
        alignTicks: true,
        axisLine: {
          show: true,
          lineStyle: {
            color: '#272258'
          }
        },
        axisLabel: {
          fontSize: px(15),
          color:"#a19fc4"
        }
      }
    ],
    series: [
      {
        name: '运输中车辆',
        type: 'bar',
        yAxisIndex: 1,
        barWidth: px(10),
        data: data2
      },
      {
        name: '车辆总数',
        type: 'bar',
        barWidth: px(10),
        data: data1
      },

      {
        name: '使用率',
        type: 'line',
        yAxisIndex: 2,
        data:data3
      },

    ],
  }
</script>

<style lang="scss" scoped>

</style>