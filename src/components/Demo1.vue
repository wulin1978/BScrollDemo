<template>
  <div class='wrap'>
    <slot></slot>
  </div>
</template>
<script>
import BScroll from 'better-scroll'
export default {
  created () {
    this.$nextTick(() => {
      this.scroll = new BScroll('.wrap')
    })
  }
}
</script>
<style lang='scss' scoped>
</style>
