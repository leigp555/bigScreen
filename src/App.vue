<template>
 <div id="demoWrap" :style=demoStyle>
   <header>
     <div class="headerWrap">
       <span>数据时段</span>
       <span>2021年5月28日 周一 18:30</span>
     </div>
     <div class="title"><h2>2021圆通全国集运平台数据监控</h2></div>
   </header>
   <main>
     <h2 class="chartA">货主订单月报 /</h2>
     <section class="chartAA">
       <Chart1></Chart1>
     </section>
     <h2 class="chartB">承运商车辆认证 /</h2>
     <section class="chartBB">
       <Chart2></Chart2>
     </section>
     <section class="chartCC">
       <ChartMap/>
     </section>
     <section class="chartDD">
       <Chart3></Chart3>
     </section>
     <section class="chartEE">
       <Chart4></Chart4>
     </section>
     <section class="chartFF">
       <Chart5></Chart5>
     </section>
     <h2 class="chartG">承运商派单情况 /</h2>
     <section class="chartGA">
       <Chart6></Chart6>
     </section>
     <section class="chartGB">
       <Chart7></Chart7>
     </section>
     <section class="chartGC">
       <Chart8></Chart8>
     </section>
     <h2 class="chartH">用户注册情况分析 /</h2>
     <section class="chartHA">
       <Chart9></Chart9>
     </section>
     <section class="chartHB">
       <Chart10></Chart10>
     </section>
   </main>
 </div>
</template>


<script setup lang="ts">
import {computed} from "vue";
import Chart1 from "./components/Chart1.vue"
import Chart2 from "./components/Chart2.vue";
import Chart3 from "./components/Chart3.vue";
import Chart4 from "./components/Chart4.vue";
import Chart5 from "./components/Chart5.vue";
import Chart6 from "./components/Chart6.vue";
import Chart7 from "./components/Chart7.vue";
import Chart8 from "./components/Chart8.vue";
import Chart9 from "./components/Chart9.vue";
import Chart10 from "./components/Chart10.vue";
import ChartMap from "./components/ChartMap.vue";
//通过浏览器宽高以及设计稿比例计算出页面的宽度高度
const deviceWidth=document.documentElement.clientWidth
const deviceHeight=document.documentElement.clientHeight
window.pagWidth=deviceWidth/deviceHeight>1920/1080?deviceHeight*(1920/1080):deviceWidth
const pagHeight=pagWidth/(1920/1080)
const style=document.createElement("style")
const string=`html{
  font-size:${pagWidth/100}px
}`
style.innerHTML=string
document.head.appendChild(style)
//上下左右居中对其
const marginTop=(deviceHeight-pagHeight)/2
const demoStyle=computed(()=>{
  return {"width":pagWidth+'px',"height":pagHeight+'px',"marginTop":marginTop+'px'}
})




</script>


<style lang="scss" scoped>
@import "helper";
#demoWrap{
  margin-right: auto;
  margin-left: auto;
  background: linear-gradient(180deg, rgba(8,12,99,1) 0%, rgba(1,4,37,1) 100%);
  color: white;
  display: flex;
  flex-direction: column;
  >header{
    position: relative;
    top: 0;
    left: 0;
    >.headerWrap{
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: px(15) px(30);
      border: 1px solid #4e6dc0;
      font-size: px(14);
      background-color: #0c2e99;
    }
    >.title{
      height: px(75);
      width: px(1080);
      background-color:  #0c2e99;
      position: absolute;
      top: 0;
      left: 50%;
      z-index: 1;
      transform: translateX(-50%);
      display: flex;
      justify-content: center;
      align-items: center;
      border-bottom:1px solid #4e6dc0;
      border-bottom-right-radius: px(80);
      border-bottom-left-radius: px(80);
      >h2{
        font-size: px(32);
        text-align: center;
        vertical-align: center;
        letter-spacing: px(5);
      }
    }
  }
  >main{
    flex-grow: 1;
    margin-top: px(10);
    padding: px(30);
    >section {

    }
    display: grid;
    grid-gap: px(20);
    grid-template-columns: px(486) px(308) px(504) auto px(220);
    grid-template-rows: 1fr px(170) px(170) 1fr px(242) px(242);
    grid-template-areas:
    "a c c g g"
    "aa c  c ga gb"
    "aa c  c ga gc"
    "b c c h h"
    "ba d e ha ha"
    "ba d f hb hb"
  ;
    >h2{
      font-size: px(20);
    }
    >.chartA{
      grid-area: a;
      margin-bottom: px(-5);
      background-color: inherit;
    }
    >.chartAA{
      grid-area: aa;
    }
    >.chartB{
      grid-area: b;
      margin-bottom: px(-5);
      background-color: inherit;
    }
    >.chartBB{
      grid-area: ba;
    }
    >.chartCC{
      grid-area: c;
      background-color: inherit;
    }
    >.chartDD{
      grid-area: d;
    }
    >.chartEE{
      grid-area: e;
    }
    >.chartFF{
      grid-area: f;
    }
    >.chartG{
      grid-area: g;
      margin-bottom: px(-5);
      background-color: inherit;
    }
    >.chartGA{
      grid-area: ga;
    }
    >.chartGB{
      grid-area:gb;
    }
    >.chartGC{
      grid-area: gc;
    }
    >.chartH{
      grid-area: h;
      margin-bottom: px(-5);
      background-color: inherit;
    }
    >.chartHA{
      grid-area: ha;
    }
    >.chartHB{
      grid-area: hb;
    }
  }
}

</style>
