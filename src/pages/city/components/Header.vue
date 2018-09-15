<template>
  <div class="header">
    城市选择
    <router-link to="/">
      <div class="iconfont header-back">&#xe60f;</div>
    </router-link>

  </div>
</template>

<script>
export default {
  name: 'Header'
}
</script>

<style lang="stylus" scoped>
  @import "~styles/varibles.styl"
  .header
    position: relative
    overflow : hidden
    height: 40px
    line-height : 40px
    text-align: center
    color : #ffffff
    background: $bgColor
    .header-back
      position : absolute
      top: 0
      left : 0
      font-size: 20px
      width :40px
      text-align : center
      color: #ffffff
</style>
