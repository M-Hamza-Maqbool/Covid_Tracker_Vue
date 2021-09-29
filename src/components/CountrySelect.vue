<template>
  <div>
      <select  @change="onChange()"   v-model="selected"  class="form-select mt-1 block p-5 w-screen border p-3 rounded">

          <option value="0">Select Country</option>
          <option  v-for="countr in countries" :value="countr.ID"> {{countr.Country}} </option>

      </select>
      
  </div>
</template>
<script>
// console.log(this.countries)
export default {
    name : "CountrySelect",
    props: ['countries'],
    data () {
        return {
            selected:0,
        }
    },

    methods:{

       onChange(){
                 const data1=this.countries.find((items)   =>   items.ID === this.selected.value )
                 console.log(data1)
       }


    },
    

}
</script>