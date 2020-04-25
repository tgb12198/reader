<template>
  <div class="ebook-reader">
    <div class="ebook-reader-mask"
         @touchmove="move"
         @touchend="moveEnd"
         @mousedown.left="onMouseEnter"
         @mousemove.left="onMouseMove"
         @mouseup.left="onMouseEnd" @click="onMaskClick"></div>
    <div class="read-wrapper">
      <div id="read"></div>
    </div>
  </div>
</template>

<script>
export default {}
</script>

<style lang="stylus" rel="stylesheet/stylus">

</style>
