<template>
  <div >
    <div class="rcmd-title">周末去哪儿</div>
    <ul>
      <li class="item border-bottom" v-for="item in weekendList" :key="item.id">
        <div class="item-img-wrap">
          <img class="item-img" :src="item.imgUrl" />
        </div>
        <div class="item-info">
          <p class="item-title">{{ item.title}}</p>
          <p class="item-desc">{{ item.desc}}</p>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props:{
    weekendList:Array
  }
  // data () {
  //   return {
  //     weekendList:[{
  //         id:'0001',
  //         imgUrl:'http://img1.qunarzz.com/sight/source/1505/d5/abe8a48a6ef8bf.jpg_r_640x214_7c41cc81.jpg',
  //         title:'武汉必游TOP10',
  //         desc:'到武汉感受神奇的热干面之旅'
  //     },
  //     {
  //         id:'0002',
  //         imgUrl:'http://img1.qunarzz.com/sight/source/1505/3a/f96e254541abb.jpg_r_640x214_6b1fc9f0.jpg',
  //         title:'鄂西旅游圈',
  //         desc:'感受鄂西旖旎风光，土苗民族风情'
  //     }]
  //   }
  // }
}
</script>


<style lang="stylus" scoped>
  @import '~styles/mixins.styl'
  .rcmd-title
    line-height: .8rem
    background: #eee
    text-indent: .2rem
    font-weight:bold
  .item-img-wrap
    height:0
    overflow:hidden
    padding-bottom:37.09%
    .item-img
      width:100%
  .item-info
    padding: .1rem
    .item-title
      line-height: .54rem
      font-size: .32rem
      font-weight:bold
      ellipsis()
    .item-desc
      line-height: .4rem
      color: #ccc
      ellipsis()
</style>
