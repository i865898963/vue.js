<template>
  <div class="icons">
    <swiper :options="swiperOption">
      <swiper-slide v-for="(page, index) of pages" :key="index">
        <div class="icon" v-for="item of page" :key="item.id">
          <div class="icon-img">
            <img class="icon-imgContent" :src='item.imgUrl' alt="">
          </div>
          <p class="icon-desc">{{item.desc}}</p>
        </div>
      </swiper-slide>
      <!--<swiper-slide>-->
        <!--<div class="icon">-->
          <!--<div class="icon-img">-->
            <!--<img class="icon-imgContent" src="http://img1.qunarzz.com/piao/fusion/1803/95/f3dd6c383aeb3b02.png" alt="">-->
          <!--</div>-->
          <!--<p class="icon-desc">热门景点</p>-->
        <!--</div>-->
      <!--</swiper-slide>-->
    </swiper>
  </div>
</template>

<script>
export default {
  name: 'HomeIcons',
  props: {
    iconList: Array
  },
  data () {
    return {
      swiperOption: {
        autoplay: false
      }
    }
  },
  computed: {
    pages () {
      const pages = []
      this.iconList.forEach((item, index) => {
        const page = Math.floor(index / 8)
        if (!pages[page]) {
          pages[page] = []
        }
        pages[page].push(item)
      })
      return pages
    }
  }
}
</script>

<style lang="stylus" scoped>
  @import "~styles/varibles.styl"
  @import "~styles/mixins.styl"
  .icons >>> .swiper-container
    height :0
    padding-bottom :50%
  .icon
    position: relative
    float: left
    margin:0
    height: 0
    width: 25%
    padding-bottom: 25%
    .icon-img
      position: absolute
      top: 0
      left: 0
      right: 0
      bottom: 22px
      box-sizing: border-box
      padding: 5px
      .icon-imgContent
          display: block
          margin: 0 auto
          height: 100%
    .icon-desc
        position:absolute
        left: 0
        right: 0
        bottom: 0
        height: 22px
        line-height: 22px
        text-align : center
        color: $textColor
        ellipsis()
</style>
