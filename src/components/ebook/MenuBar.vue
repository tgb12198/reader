<template>
  <div v-show="isShowTitleAndMenu" class="menu-wrapper">
    <div class="icon-wrapper">
      <span class="icon-menu icon"></span>
    </div>
    <div class="icon-wrapper">
      <span class="icon-progress icon"></span>
    </div>
    <div class="icon-wrapper">
      <span class="icon-bright icon"></span>
    </div>
    <div class="icon-wrapper">
      <span class="icon-A icon"></span>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    isShowTitleAndMenu: {
      type: Boolean,
      default: false
    }
  }
}
</script>

<style lang="scss" scope>
  @import "../../assets/styles/global";

  .menu-wrapper {
    position: absolute;
    bottom: 0;
    left: 0;
    width: 100%;
    height: px2rem(48);
    z-index: 101;
    box-shadow: 0 px2rem(-8) px2rem(8) rgba(0, 0, 0, 0.15);
    display: flex;

    .icon-wrapper {
      flex: 1;
      @include center;
    }
  }
</style>
