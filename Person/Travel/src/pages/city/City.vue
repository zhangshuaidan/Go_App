<template>
    <div>
         <city-header></city-header>
         <ctiy-search :cities="cities"></ctiy-search>
         <ctiy-list :cities="cities" :hot="hotCities"
         
         :letter="letter"></ctiy-list>
         <ctiy-alphabet :cities="cities"
        @change="handleLetterChange"
         ></ctiy-alphabet>
    </div>
</template>

<script>
import axios from 'axios'
import CityHeader from './components/Header.vue'
import CtiySearch from './components/Search.vue'
import CtiyList from './components/List.vue'
import CtiyAlphabet from './components/Alphabet'
export default {
    name:"Ctiy",
  components: {
    CityHeader,
    CtiySearch,
    CtiyList,
    CtiyAlphabet
  },
  data(){
      return{
        cities:{},
        hotCities:[],
        letter:""
      }
    },
  methods:{
    getCityInfo(){
      axios.get('/api/city.json').then(
        this.handleGetCityInfoSucc
      )
    },

    handleGetCityInfoSucc(res) {
        // console.log(res)
        res=res.data
        if (res.ret&&res.data) {
          const data=res.data
          this.cities = data.cities
          this.hotCities =data.hotCities
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

<style lang="stylus" scoped>

</style>

