<template>
  <div >
    <div class="rcmd-title">热销推荐</div>
    <ul>
      <router-link tag="li"
      class="item border-bottom"
      v-for="item in recommendList"
      :key="item.id"
      :to="'/detail/'+item.id">
        <img class="item-img" :src="item.imgUrl" />
        <div class="item-info">
          <p class="item-title">{{ item.title}}</p>
          <p class="item-desc">{{ item.desc}}</p>
          <button class="item-btn">查看详情</button>
        </div>
      </router-link>
    </ul>
  </div>
</template>

<script>
export default {
  props:{
    recommendList:Array
  },
  // data () {
  // return {
  //     recommendList:[{
  //       id:'0001',
  //       imgUrl:'http://img1.qunarzz.com/sight/p0/1504/47/4730a0c01664b63d.water.jpg_200x200_d7f52253.jpg',
  //       title:'武汉海昌极地海洋世界',
  //       desc:'浪漫的海洋主题公园'
  //     },{
  //       id:'0002',
  //       imgUrl:'http://img1.qunarzz.com/sight/p0/1412/1a/ad942d69c7fe7aa5aba971dedf28c1c5.water.jpg_200x200_4a971355.jpg',
  //       title:'武汉大学',
  //       desc:'民国四大名校之一'
  //     }]
  //   }
  // }
}
</script>


<style lang="stylus" scoped>
  @import '~styles/mixins.styl'
  .rcmd-title
    margin-top: .2rem
    line-height: .8rem
    background: #eee
    text-indent: .2rem
    font-weight:bold
  .item
    overflow: hidden
    display: flex
    height: 1.9rem
    .item-img
      width: 1.7rem
      height: 1.7rem
      padding: .1rem
    .item-info
      flex: 1
      padding: .1rem
      min-width: 0
      .item-title
        line-height: .54rem
        font-size: .32rem
        ellipsis()
      .item-desc
        line-height: .4rem
        color: #ccc
        ellipsis()
      .item-btn
        line-height: .44rem
        margin-top: .16rem
        background: #ff9300
        padding: 0 .2rem
        border-radius: .06rem
        color: #fff
</style>
