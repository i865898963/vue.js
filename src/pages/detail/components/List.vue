<template>
  <div>
    <div class="item" v-for="(item,index) in list" :key="index">
      <div class="item-title border-bottom">
        <span class="item-title-icon"></span>
        {{item.title}}
      </div>
      <div v-if="item.children" class="item-children">
        <list :list="item.children"></list>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'List',
  props: {
    list: Array
  }
}
</script>

<style lang="stylus" scoped>
  .item-title
    line-height: 40px
    font-size: 18px
    padding: 0 10px
    border-bottom: 1px solid #ccc
    .item-title-icon
      position: relative
      left: 5px
      top: 6px
      display: inline-block;
      width: 22px;
      height: 22px;
      background: url(http://s.qunarzz.com/piao/image/touch/sight/detail.png) 0px -30px no-repeat;
      margin-right: 5px;
      background-size: 26px;
  .item-children
    padding 0 10px
</style>
