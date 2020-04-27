<template>
  <div class="ebook">
    <!--<div v-show="isShowTitleAndMenu" class="title-wrapper">
      <div class="left">
        <span class="icon-back icon"></span>
      </div>
      <div class="right">
        <div class="icon-wrapper">
          <span class="icon-cart icon"></span>
        </div>
        <div class="icon-wrapper">
          <span class="icon-person icon"></span>
        </div>
        <div class="icon-wrapper">
          <span class="icon-more icon"></span>
        </div>
      </div>
    </div>-->
    <title-bar :isShowTitleAndMenu="isShowTitleAndMenu"></title-bar>
    <div class="read-wrapper">
      <div id="read"></div>
      <div class="mask">
        <div class="left" @click="prevPage"></div>
        <div class="center" @click="toggleTitleAndMenu"></div>
        <div class="right" @click="nextPage"></div>
      </div>
    </div>
    <!--<div v-show="isShowTitleAndMenu" class="menu-wrapper">
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
    </div>-->
    <menu-bar :isShowTitleAndMenu="isShowTitleAndMenu"></menu-bar>
  </div>
</template>

<script>
import Epub from 'epubjs'
import TitleBar from './components/ebook/TitleBar'
import MenuBar from './components/ebook/MenuBar'

const URL = '/(2020) Postgraduate English Reading Comprehension Intensive Reading 100 (Basic Edition).epub'
global.ePub = Epub
export default {
  data () {
    return {
      isShowTitleAndMenu: false
    }
  },
  methods: {
    // 上一页
    prevPage () {
      if (this.rendition) {
        this.rendition.prev()
      }
    },
    // 下一页
    nextPage () {
      if (this.rendition) {
        this.rendition.next()
      }
    },
    showEpub () {
      this.book = new Epub(URL)
      this.rendition = this.book.renderTo('read', {
        width: window.innerWidth,
        height: window.innerHeight
      })
      this.rendition.display()
    },
    toggleTitleAndMenu () {
      this.isShowTitleAndMenu = !this.isShowTitleAndMenu
    }
  },
  mounted () {
    this.showEpub()
  },
  components: {
    MenuBar,
    TitleBar
  }
}
</script>

<style lang="scss" scoped>
  @import "assets/styles/global";

  .ebook {
    position: relative;

    .read-wrapper {
      .mask {
        display: flex;
        position: absolute;
        z-index: 100;
        left: 0;
        top: 0;
        width: 100%;
        height: 100%;

        .left {
          flex: 0 0 px2rem(100);
        }

        .center {
          flex: 1;
        }

        .right {
          flex: 0 0 px2rem(100);
        }
      }
    }
  }
</style>
