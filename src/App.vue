<template>
 <div id="demoWrap" :style=demoStyle>
   <header>
     <div class="headerWrap">
       <span>数据时段</span>
       <span>2021年5月28日 周一 18:30</span>
     </div>
     <div class="title"><span>2021圆通全国集运平台数据监控</span></div>
   </header>
   <main>
     <section class="chartA">货主订单月报 /</section>
     <section class="chartAA">
       <Chart1></Chart1>
     </section>
     <section class="chartB">承运商车辆认证 /</section>
     <section class="chartBB"></section>
     <section class="chartCC"></section>
     <section class="chartDD"></section>
     <section class="chartEE"></section>
     <section class="chartFF"></section>
     <section class="chartG">承运商派单情况 /</section>
     <section class="chartGA"></section>
     <section class="chartGB"></section>
     <section class="chartGC"></section>
     <section class="chartH">用户注册情况分析 /</section>
     <section class="chartHA"></section>
     <section class="chartHB"></section>
   </main>
 </div>
</template>


<script setup lang="ts">
import {computed} from "vue";
import Chart1 from "./components/Chart1.vue"
//通过浏览器宽高以及设计稿比例计算出页面的宽度高度
const deviceWidth=document.documentElement.clientWidth
const deviceHeight=document.documentElement.clientHeight
let pagWidth:number=deviceWidth/deviceHeight>1920/1080?deviceHeight*(1920/1080):deviceWidth
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
      >span{
        font-size: px(32);
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
