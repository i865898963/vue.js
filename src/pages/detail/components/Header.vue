<template>
  <div>
    <router-link tag="div" to="/" class="header-abs" v-show="!opacity">
       <div class="iconfont header-abs-back">&#xe60f;</div>
    </router-link>
    <div class="header-fixed" v-show="opacity" :style="{opacity}">
      <router-link to="/">
        <div class="iconfont header-fixed-back">&#xe60f;</div>
      </router-link>
        景点详情
    </div>
  </div>
</template>

<script>
export default {
  name: 'DetailHeader',
  data () {
    return {
      opacity: 0
    }
  },
  methods: {
    handleWScroll () {
      const scrollTop = document.documentElement.scrollTop
      if (scrollTop > 60) {
        let opacity = scrollTop / 140
        this.opacity = opacity > 1 ? 1 : opacity
        this.headerShow = false
      } else {
        let opacity = scrollTop / 140
        this.opacity = opacity > 1 ? 1 : opacity
      }
    }
  },
  activated () {
    window.addEventListener('scroll', this.handleWScroll)
  },
  deactivated () {
    window.removeEventListener('scroll', this.handleWScroll)
  }
}
</script>

<style lang="stylus" scoped>
@import '~styles/varibles.styl'
  .header-abs
    position: absolute
    left: 10px
    top: 10px
    width: 40px
    height: 40px
    line-height: 40px
    border-radius: 20px
    text-align: center
    background: rgba(0, 0, 0,.8)
    .header-abs-back
      color: #fff
      font-size: 20px
  .header-fixed
    position: fixed
    top: 0
    left: 0
    right: 0
    overflow : hidden
    height: 40px
    line-height : 40px
    text-align: center
    color : #ffffff
    background: $bgColor
    z-index: 1
    .header-fixed-back
      position : absolute
      top: 0
      left : 0
      font-size: 20px
      width :40px
      text-align : center
      color: #ffffff
</style>
