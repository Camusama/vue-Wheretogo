<template>
  <div >
    <city-header></city-header>
    <search :cities = "cities"></search>
    <list :cities="cities" :hot ="hotCities" :letter="letter"></list>
    <alpha-list :cities="cities" @change="handleLetterChange"></alpha-list>
  </div>
</template>

<script>
import axios from 'axios'
import CityHeader from './components/Header'
import Search from './components/Search'
import List from './components/List'
import AlphaList from './components/Alphabet'

export default {
  components:{
    CityHeader,
    Search,
    List,
    AlphaList
  },
  data () {
    return {
      cities:{},
      hotCities:[],
      letter:''
    }
  },
  //数据结构为res.data.data:{ret,data:{索引[]，hotcity[]},...}
  methods:{
    getCityInfo (){
      axios.get('/api/city.json')
        .then(this.handleGetCityInfoSucc)
    },
    handleGetCityInfoSucc (res) {
      res = res.data
      if(res.ret && res.data) {
        const data =res.data
        this.cities = data.cities
        this. hotCities = data.hotCities
      }
    },
    handleLetterChange(letter){
      this.letter=letter
    }
  },
  mounted(){
    this.getCityInfo()
  }
}
</script>


<style>

</style>
