<template>
  <div class="icons">
    <swiper :options="swiperOption">
      <swiper-slide v-for="(p,index) of pages" :key="index">
        <div class="icon" v-for="item of p" :key="item.id">
          <div class="icon-img">
            <img class="icon-con" :src="item.imgUrl">
          </div>
          <p class="icon-desc">{{item.desc}}</p>
        </div>
      </swiper-slide>
      <div class="swiper-pagination"  slot="pagination"></div>
    </swiper>
  </div>
</template>

<script>
export default {
  props:{
    iconList:Array
  },
  data () {
    return {
      // iconList:[{
      //   id:'01',
      //   imgUrl:'http://img1.qunarzz.com/piao/fusion/1803/95/f3dd6c383aeb3b02.png',
      //   desc:'景点门票'
      //   },{
      //   id:'02',
      //   imgUrl:'http://img1.qunarzz.com/piao/fusion/1804/ff/fdf170ee89594b02.png',
      //   desc:'必游榜单'
      //   },{
      //   id:'03',
      //   imgUrl:'http://img1.qunarzz.com/piao/fusion/1803/95/8246f27355943202.png',
      //   desc:'游乐场'
      //   },{
      //   id:'04',
      //   imgUrl:'http://img1.qunarzz.com/piao/fusion/1803/bd/9f7b9b2b60c1502.png',
      //   desc:'踏青赏花'
      //   },{
      //   id:'05',
      //   imgUrl:'http://img1.qunarzz.com/piao/fusion/1803/76/eb88861d78fb9902.png',
      //   desc:'动植物园'
      //   },{
      //   id:'06',
      //   imgUrl:'http://img1.qunarzz.com/piao/fusion/1804/5a/13ceb38dcf262f02.png',
      //   desc:'一日游'
      //   },{
      //   id:'07',
      //   imgUrl:'http://img1.qunarzz.com/piao/fusion/1803/dd/cce1231836f10a02.png',
      //   desc:'周边游'
      //   },{
      //   id:'08',
      //   imgUrl:'http://img1.qunarzz.com/piao/fusion/1803/96/c70f1e85ae4a4f02.png',
      //   desc:'自然风光'
      //   },{
      //   id:'09',
      //   imgUrl:'http://img1.qunarzz.com/piao/fusion/1803/e3/67df61427c8e1302.png',
      //   desc:'演出'
      //   },{
      //   id:'10',
      //   imgUrl:'http://img1.qunarzz.com/piao/fusion/1803/80/416c6ab3368d1f02.png',
      //   desc:'全部玩乐'
      // }],
      swiperOption: {
        autoplay:false,
        pagination:'.swiper-pagination',
      },
    }
  },
  computed:{
    pages(){
      const pages=[]
      this.iconList.forEach((item,index) => {
        const page = Math.floor(index/8)
        if(!pages[page]){
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
  @import '~styles/varibles.styl'
  @import '~styles/mixins.styl'
  .swiper-container-horizontal > .swiper-pagination-bullets
    bottom:0
  .icons >>> .swiper-container
    height: 0
    padding-bottom: 50%
  .icons
    margin-top:.1rem
    .icon
      position:relative
      overflow:hidden
      float:left
      width:25%
      height:0
      padding-bottom:25%
      .icon-img
        position:absolute
        top:0
        left:0
        right:0
        bottom:.44rem
        box-sizing:border-box
        padding:.1rem
        .icon-con
          display:block
          margin:0 auto
          height:100%
      .icon-desc
        position:absolute
        left: 0
        right:0
        bottom:.3rem
        height:.44rem
        line-height:.44rem
        text-align:center
        color:$darkTextColor
        ellipsis()
</style>
