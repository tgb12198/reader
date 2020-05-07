<template>
  <div class="ebook">
    <title-bar :isShowTitleAndMenu="isShowTitleAndMenu"></title-bar>
    <div class="read-wrapper">
      <div id="read"></div>
      <div class="mask">
        <div class="left" @click="prevPage"></div>
        <div class="center" @click="toggleTitleAndMenu"></div>
        <div class="right" @click="nextPage"></div>
      </div>
    </div>
    <menu-bar :isShowTitleAndMenu="isShowTitleAndMenu" :fontSizeList="fontSizeList" ref="menuBar"></menu-bar>
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
      isShowTitleAndMenu: false,
      fontSizeList: [{ fontSize: 12 }, { fontSize: 14 }, { fontSize: 16 }, { fontSize: 18 }, { fontSize: 20 }, { fontSize: 22 }, { fontSize: 24 }]
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
      if (!this.isShowTitleAndMenu) {
        this.$refs.menuBar.hideSetting()
      }
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
          @include center
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
