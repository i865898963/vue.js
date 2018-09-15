<template>
  <div>
     <div class="recommend-title">热门推荐</div>
    <ul>
      <router-link tag="li" class="item" v-for="item of recommendList" :key="item.id" :to="'/detail/' + item.id">
          <img class="item-img" :src='item.imgUrl' alt="">
          <div class="item-info">
              <p class="item-title">{{item.title}}</p>
              <p class="item-desc">{{item.desc}}</p>
              <button class="item-button">查看详情</button>
          </div>
      </router-link>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'Recommend',
  props: {
    recommendList: Array
  }
}
</script>

<style lang="stylus" scoped>
  @import "~styles/varibles.styl"
  @import "~styles/mixins.styl"
  .recommend-title
    line-height: 35px
    margin-top: 15px
    background : #eee
    text-indent : 2rem
  .item
    overflow : hidden
    display : flex
    height: 110px
    border-bottom : 1px solid #eeeeee
    margin-top:5px
  .item-img
    padding: 10px
    width : 102px
    height : 102px
  .item-info
    flex: 1
    padding :5px
    min-width 0
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
    .item-button
      margin-top:10px
      font-size:12px
      line-height :20px
      background : #ff9300
      padding: 0 5px
      border-radius: 8px
      color: #ffffff
</style>
