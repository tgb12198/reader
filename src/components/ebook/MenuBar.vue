<template>
  <div class="menu-bar">
    <transition name="slide-up">
      <div v-show="isShowTitleAndMenu" class="menu-wrapper"
           :class="{'hide-box-shadow':ifSettingShow||!isShowTitleAndMenu}">
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
          <span class="icon-A icon" @click="showSetting"></span>
        </div>
      </div>
    </transition>
    <transition name="slide-up">
      <div class="setting-wrapper" v-show="ifSettingShow">
        <div class="setting-font-size"></div>
      </div>
    </transition>
  </div>
</template>

<script>
export default {
  props: {
    isShowTitleAndMenu: {
      type: Boolean,
      default: false
    }
  },
  data () {
    return {
      ifSettingShow: false
    }
  },
  methods: {
    showSetting () {
      this.ifSettingShow = !this.ifSettingShow
    },
    hideSetting () {
      this.ifSettingShow = false
    }
  }
}
</script>

<style lang="scss" scope>
  @import "../../assets/styles/global";

  .menu-bar {
    .menu-wrapper {
      position: absolute;
      display: flex;
      bottom: 0;
      left: 0;
      width: 100%;
      height: px2rem(48);
      z-index: 101;
      box-shadow: 0 px2rem(-8) px2rem(8) rgba(0, 0, 0, 0.15);

      &.hide-box-shadow {
        box-shadow: none;
      }

      .icon-wrapper {
        flex: 1;
        @include center;
      }
    }

    .setting-wrapper {
      position: absolute;
      left: 0;
      bottom: px2rem(48);
      width: 100%;
      height: px2rem(60);
      background: white;
      box-shadow: 0 px2rem(-8) px2rem(8) rgba(0, 0, 0, 0.15);

      .setting-font-size {

      }
    }
  }
</style>
