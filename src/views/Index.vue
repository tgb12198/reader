<template>
  <div class="ebook">
    <div class="title-wrapper">
      <div class="left">
        <span class="icon-back"></span>
      </div>
      <div class="right">
        <div class="icon-wrapper">
          <span class="icon-cart"></span>
        </div>
        <div class="icon-wrapper">
          <span class="icon-person"></span>
        </div>
        <div class="icon-wrapper">
          <span class="icon-more"></span>
        </div>
      </div>
    </div>
    <div class="read-wrapper">
      <div id="read"></div>
      <div class="mask">
        <div class="left" @click="prevPage"></div>
        <div class="center"></div>
        <div class="right" @click="nextPage"></div>
      </div>
    </div>
    <div class="menu-wrapper"></div>
  </div>
</template>

<script>
import Epub from 'epubjs'

const URL = '/(2020) Postgraduate English Reading Comprehension Intensive Reading 100 (Basic Edition).epub'
global.ePub = Epub
export default {
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
    }
  },
  mounted () {
    this.showEpub()
  }
}
</script>

<style lang="scss" scoped>
  @import "../assets/styles/global";

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
