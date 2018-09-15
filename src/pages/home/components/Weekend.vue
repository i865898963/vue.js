<template>
    <div>
      <div class="recommend-title">热门推荐</div>
      <ul>
        <li class="item" v-for="item of weekendList" :key="item.id">
          <div class="item-img-wrapper">
            <img class="item-img" :src='item.imgUrl' alt="">
          </div>
          <div class="item-info">
            <p class="item-title">{{item.title}}</p>
            <p class="item-desc">{{item.desc}}</p>
          </div>
        </li>
      </ul>
    </div>
</template>

<script>
export default {
  name: 'Weekend',
  props: {
    weekendList: Array
  }
}
</script>

<style lang="stylus" scoped>
  .recommend-title
    line-height: 35px
    margin-top: 15px
    background : #eee
    text-indent : 2rem
  .item-img-wrapper
    overflow: hidden
    height 0
    padding-bottom : 33.9%
    .item-img
      width 100%
  .item-info
    padding :5px
    .item-title
      margin-top :5px
      line-height : 22px;
      height: 22px
      font-size: 18px
      ellipsis()
    .item-desc
      line-height : 22px
      height :22px
      font-size: 14px
      color: #ccc
      ellipsis()
</style>
