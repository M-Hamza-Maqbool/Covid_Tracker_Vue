<template>
  <main v-if="!loading">
    <DataTitle :text="Tilte" :dataDate="dataDate" />
    <DataBoxes  :stats = "stats"  />
    <CountrySelect  @get-country="getContryData" :countries= "countries" />
  </main>
  <main class="flex flex-col align-center justigy-center text-center" v-else>
          <div class="text-gray-500 text-3xl mt-10 mb-6" >
             Fatching Data
          </div>
         <img :src="loadingimage" class="w-24 m-auto" alt="">
            </main>
</template>

<script>
// @ is an alias to /src
import DataTitle from '@/components/DataTitle'
import DataBoxes from '@/components/DataBoxes'
import CountrySelect from '@/components/CountrySelect'

export default {
  name: 'Home',
  components: {
         DataTitle,
         DataBoxes,
         CountrySelect
  },
  data  () {
    return{
     loading:true,
     Tilte:'Global',
     dataDate:'',
     stats:{},
     countries:[],
     loadingimage : require('../assets/img/loading.gif'),

    }
  },

  methods : {
      async fatchCovidData(){
          const res= await fetch('https://api.covid19api.com/summary')
          const data=await  res.json()
          return data
      },
      getContryData(Country){
        this.stats=Country
        this.Tilte=Country.Country
      }
  },
       async created () {
       const data = await this.fatchCovidData();

        this.dataDate=data.Date
        this.stats=data.Global
        this.countries=data.Countries
        this.loading=false
       },
  
}
</script>
