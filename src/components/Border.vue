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
  border: 2px solid #016add;

  position:relative;
  &:before{
    display: block;
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    box-shadow: 12px 0 0 -10px #102b86,-12px 0 0 -10px #102b86,0 11px 0 -10px #102b86,0 -12px 0 -10px #102b86;

  }
}
</style>