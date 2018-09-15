<template>
  <div class="list" ref="wrapper">
    <div>
      <div class="area">
          <div class="title border-top-bottom">当前城市</div>
          <div class="button-list">
            <div class="button-wrapper">
                <div class="button">
                 {{this.currentCity}}
                </div>
            </div>
          </div>
      </div>
    <div class="area">
      <div class="title border-top-bottom">热门城市</div>
      <div class="button-list">
        <div class="button-wrapper" v-for="item of hot" :key="item.id" @click="handleCityClick(item.name)">
          <div class="button">
            {{item.name}}
          </div>
        </div>
      </div>
    </div>
    <div class="area" v-for="(item , key) of cities" :key="key" :ref="key" >
      <div class="title border-top-bottom">{{key}}</div>
      <div class="item-list" v-for="innerItem of item" :key="innerItem.id" @click="handleCityClick(innerItem.name)">
          <div class="item">{{innerItem.name}}</div>
      </div>
    </div>
    </div>
  </div>
</template>

<script>
import Bscroll from 'better-scroll'
import { mapState, mapMutations } from 'vuex'
export default {
  name: 'List',
  props: {
    hot: Array,
    cities: Object,
    letter: String
  },
  computed: {
    ...mapState({
      'currentCity': 'city'
    })
  },
  mounted () {
    this.scroll = new Bscroll(this.$refs.wrapper)
  },
  methods: {
    ...mapMutations(['changeCity']),
    handleCityClick (city) {
      // this.$store.state.city = city
      // this.$store.dispatch('changeCity', city)
      // this.$store.commit('changeCity', city)
      this.changeCity(city)
      this.$router.push('/')
    }
  },
  watch: {
    letter () {
      if (this.letter) {
        const element = this.$refs[this.letter][0]
        this.scroll.scrollToElement(element)
      }
    }
  }
}
</script>

<style lang="stylus" scoped>
  .border-top-bottom
    &:before
      border-color: #cccccc
    &:after
      border-color : #cccccc
  .list
    overflow: hidden;
    position :absolute
    top:75px
    left:0
    right:0
    bottom 0
    .title
      line-height : 22px
      background : #eee
      padding-left : 10px
      color: #666
      font-size: 14px
    .button-list
      overflow : hidden
      padding: 5px 30px 5px 5px
      .button-wrapper
        width : 33.33%
        float: left
        .button
          text-align :center
          margin : 5px
          padding 5px
          border : 1px solid #ccc
          border-radius : 5px
    .item-list
      .item
        line-height:30px
        border-bottom :1px solid #cccccc
        padding-left : 10px
</style>
