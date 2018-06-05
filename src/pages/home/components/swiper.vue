<template>
  <div class="wrap">
    <swiper :options="swiperOption" v-if="swiperList.length">
      <swiper-slide v-for="item of swiperList" :key="item.id">
        <img :src="item.imgUrl" class="sw-img">
      </swiper-slide>
      <div class="swiper-pagination"  slot="pagination"></div>
    </swiper>
  </div>

</template>

<script>
export default {
  name: 'carrousel',
  props:{
    swiperList:{}
  },
  data() {
    return {
      swiperOption: {
        pagination:'.swiper-pagination',
        loop:true
      },
      // swiperList: [{
      //   id:'0001',
      //   imgUrl:'http://img1.qunarzz.com/piao/fusion/1804/b5/8bd6da9d794e1902.jpg_750x200_b1a28179.jpg'
      // },{
      //   id:'0002',
      //   imgUrl:'http://img1.qunarzz.com/piao/fusion/1805/99/74349dce41d79002.jpg_750x200_e619a2d8.jpg'
      // }]
    }
  }

}
</script>

<!-- 宽高比31.25 -->
<style lang="stylus" scoped>
  .wrap>>> .swiper-pagination-bullet-active
    background: #fff
  .wrap
    overflow:hidden
    width:100%
    height:0
    padding-bottom:31.25%
    .sw-img
      width:100%
      height:100%
</style>
