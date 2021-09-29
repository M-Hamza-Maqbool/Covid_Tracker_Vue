<template>
<div class="w-screen text-center ">
<div class="flex flex-row  w-screen ">
  <div class="flex-2 w-1/5">
      <div class="p-10 ">  
    <div class="max-w-lg text-center rounded overflow-hidden bg-red-500 shadow-lg">
       <div class="px-4 py-4 text-center">
        <div class="font-bold text-xl text-white   mb-2">NewConfirmed</div>
         <h1 class="text-gray-700  text-2xl text-base">      {{numberWithCommas(stats.NewConfirmed)}}<br>
         </h1>
       </div>   
    </div>
  </div>

  </div>
  <div class="flex-2 w-1/5">
  <div class="p-10 ">  
   <div class="max-w-lg text-center rounded overflow-hidden bg-gray-500 shadow-lg">
       <div class="px-4 py-4 text-center">
        <div class="font-bold text-xl text-white  mb-2">TotalConfirmed</div>
         <h1 class="text-gray-700  text-2xl text-base">      {{numberWithCommas(stats.TotalConfirmed)}}<br>
         </h1>
       </div>   
    </div>
  </div>
  </div>

  <div class=" flex-2 w-1/5">
  <div class="p-10 ">  
   <div class="max-w-lg text-center rounded overflow-hidden bg-yellow-500 shadow-lg">
       <div class="px-4 py-4 text-center">
        <div class="font-bold text-xl text-white  mb-2">NewRecovered</div>
         <h1 class="text-gray-700  text-2xl text-base">      {{numberWithCommas(stats.NewRecovered)}}<br>
         </h1>
       </div>   
    </div>
  </div>
  </div>



    <div class="flex-2  w-1/5 ">
  <div class="p-10">  
   <div class="max-w-lg text-center rounded overflow-hidden bg-blue-500 shadow-lg">
       <div class="px-4 py-4 text-center">
        <div class="font-bold text-xl text-white  mb-2">TotalRecovered</div>
         <h1 class="text-gray-700  text-2xl text-base">      {{numberWithCommas(stats.TotalRecovered)}}<br>
         </h1>
       </div>   
    </div>
  </div>
  </div>


  <div class="flex-2 w-1/5 ">
    <div class="p-10 ">  
    <div class="max-w-lg text-center rounded overflow-hidden bg-black shadow-lg">
        <div class="px-4 py-4 text-center">
        <div class="font-bold text-xl text-white  mb-2">NewDeaths</div>
         <h1 class="text-gray-700  text-2xl text-base">      {{numberWithCommas(stats.NewDeaths) }}<br>
         </h1>
       </div>   
    </div>
  </div> 
   </div>
</div>

</div>
  
</template>
<script>
export default {
    name: 'DataBoxes',
    props: ['stats'],
    methods: {
    numberWithCommas (x) {
           return x.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ',');
      }
    }
}
</script>