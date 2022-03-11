<template>
  <div class="borderWrap">
    <slot></slot>
  </div>
</template>

<script lang="ts" setup>


</script>

<style lang="scss" scoped>
@import "src/helper";

.borderWrap {
  width: 100%;
  height: 100%;
  border: px(1) solid #016add;
  box-shadow: inset 0 0 px(20) px(20) rgba(15, 28, 124,.5);
  position:relative;
  padding-top: px(24);
  &:before{
    display: block;
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    box-shadow:
        px(32) 0 0 px(-30) #102b86,
        px(-32) 0 0 px(-30) #102b86,
        0 px(32) 0 px(-30) #102b86,
        0 px(-32) 0 px(-30) #102b86,

  }
}
</style>