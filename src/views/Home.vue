<template>
  <main v-if="!loading">
    <DataTitle :text="Tilte" :dataDate="dataDate" />
    <DataBoxes  :stats = "stats"  />
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

export default {
  name: 'Home',
  components: {
         DataTitle,
         DataBoxes
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
  },
       async created () {
       const data = await this.fatchCovidData();

       console.log(data.Countries);
        this.dataDate=data.Date
        this.stats=data.Global
        this.countries=data.Countries
        this.loading=false
       },
  
}
</script>
