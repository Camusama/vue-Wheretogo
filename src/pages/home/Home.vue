<template>
  <div>
    <home-header></home-header>
    <home-swiper :swiperList="swiperList"></home-swiper>
    <home-icons :iconList="iconList"></home-icons>
    <recommend-icons :recommendList="recommendList"></recommend-icons>
    <Weekend :weekendList="weekendList"></Weekend>
  </div>
</template>

<script>
import HomeHeader from './components/Header'
import HomeSwiper from './components/swiper'
import HomeIcons from './components/icons'
import RecommendIcons from './components/Recommend'
import Weekend from './components/Weekend'
import axios from 'axios'
import { mapState } from 'vuex'
export default {
  name:'home',
  components:{
    HomeHeader,
    HomeSwiper,
    HomeIcons,
    RecommendIcons,
    Weekend
  },
  data () {
    return {
      lastcity:'',
      swiperList: [],
      iconList: [],
      recommendList: [],
      weekendList: []
    }
  },
  computed : {
    ...mapState(['city'])
  },
  methods:{
    getHomeInfo(){
      axios.get('/api/index.json?city=' + this.city).then(this.getHomeInfoSucc)
    },
    getHomeInfoSucc(res){
      res=res.data
      //数据结构为res.data.{ret,data:{city,swiperList...}}
      if(res.ret && res.data){
        const data = res.data
        this.swiperList = data.swiperList
        this.iconList = data.iconList
        this.recommendList = data.recommendList
        this.weekendList = data.weekendList
      }
      console.log(res)
    }
  },
  mounted () {
    this.lastcity = this.city
    this.getHomeInfo()
  },
  //性能优化，keep-alive里如果城市变化再发送请求
  activated () {
    if(this.lastcity !== this.city){
      this.lastcity = this.city
      this.getHomeInfo()
    }
  }
}
</script>

<style>

</style>