<template>
  <div class="list" ref="wrapper">
    <div>
      <div class="area">
          <div class="title border-topbottom">当前城市</div>
          <div class="btn-list">
            <div class="btn-wrap">
              <div class="btn">{{ this.currentCity }}</div>
            </div>
          </div>
      </div>
      <div class="area">
          <div class="title border-topbottom">热门城市</div>
          <div class="btn-list">
            <div class="btn-wrap"
            v-for="item in hot"
            :key="item.id"
            @click="handleCityClick(item.name)">
              <div class="btn">{{ item.name }}</div>
            </div>
          </div>
      </div>
      <div class="area"
      v-for="(item,key) in cities"
      :key="key"
      :ref="key">
          <div class="title">{{ key }}</div>
          <div class="item-list">
            <div class="item border-bottom"
            v-for="innerItem in item"
            :key="innerItem.id"
            @click="handleCityClick(innerItem.name)">
              {{innerItem.name}}
            </div>
          </div>
      </div>
    </div>
  </div>
</template>

<script>
import Bscroll from 'better-scroll'
import { mapState,mapMutations } from 'vuex'
export default {
  props :{
    hot:Array,
    cities:Object,
    letter:String
  },
  mounted () {
    this.scroll = new Bscroll(this.$refs.wrapper)
  },
  computed :{
    ...mapState({
      currentCity :'city'
    })
  },
  watch:{
    letter () {
      if(this.letter){
        const element = this.$refs[this.letter][0]
        //better-scroll插件方法参数为dom元素，$refs数据结构中第一个为dom，$refs[]为所有含ref的组件，组件ref属性为键名
        this.scroll.scrollToElement(element)
      }
    }
  },
  methods:{
    handleCityClick(city){
      // this.$store.dispatch('changeCity',city)
      this.changeCity(city)
      this.$router.push('/')
    },
    ...mapMutations(['changeCity'])
  }
}
</script>


<style lang="stylus" scoped>
  @import '~styles/varibles.styl'
  .border-topbottom
    &:before
      border-color: #ccc
    &:after
      border-color: #ccc
  .border-bottom
    &:before
      border-color: #ccc
  .list
    position:absolute
    overflow:hidden
    top:1.58rem
    left:0
    right:0
    bottom:0
    .title
      line-height:.54rem
      background:#eee
      padding-left:.2rem
      color:#666
      font-size:.26rem
    .btn-list
      overflow:hidden
      padding:.1rem .6rem .1rem .1rem
      .btn-wrap
        float:left
        width:33.33%
        .btn
          margin:.1rem
          padding:.1rem 0
          text-align:center
          border-radius:.02rem solid #ccc
          border:.02rem solid #ccc
    .item-list
      .item
        line-height:.54rem
        color:#666
        padding-left:.2rem
</style>
