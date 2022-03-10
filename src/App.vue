<template>
 <div id="demo" :style=demoStyle>
   <div class="x"></div>
 </div>
</template>


<script setup lang="ts">
import {computed} from "vue";
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
#demo{
  margin-right: auto;
  margin-left: auto;
  background-color: green;
  .x{
    width: px(468);
    height: px(342);
    background-color: yellow;
  }
}

</style>
