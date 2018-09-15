<template>
<div class="header">
    <div class="header-left">
      <div class="iconfont back-icon">&#xe60f;</div>
    </div>
    <div class="header-input">
    输入城市/景点/游玩主题
    </div>
  <router-link to="/city">
    <div class="header-right">
      {{this.city}}
      <span class="iconfont">&#xe65b;</span>
    </div>
  </router-link>
</div>
</template>

<script>
import {mapState} from 'vuex'
export default {
  name: 'HomeHeader',
  computed: {
    ...mapState(['city'])
  }
}
</script>
<style lang="stylus" scoped>
  @import "~styles/varibles.styl"
  .header
    display: flex
    line-height:60px
    background: $bgColor
    color: #fff
    .header-left
      width: 40px
      float: left
      .back-icon
        text-align :center
        font-size: 20px
    .header-input
      flex:1
      height :36px
      line-height: 36px
      margin-top: 12px
      padding-left :10px
      background: #ffffff
      border-radius: 5px
      color:#ccc
    .header-right
      min-width:75px
      padding: 0 10px
      float: right
      text-align: center
      color : #ffffff

</style>
