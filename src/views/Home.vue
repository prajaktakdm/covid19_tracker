<template>
  <div>
    <main v-if="!loading">
     

     <div class="country d-flex justify-content-center mb-2">
       <CountrySelect @get-country="getCountryData" :countries="countries"/>

      <button @click="clearCountryData"
          :disabled="!stats.Country"
          class="button p-3 mt-10 ml-2 ">
          Clear Country
      </button>
     </div>

      <DataTitle :text="title" :dataDate="dataDate"/>

      <DataBoxes :stats="stats"/>

    </main>
    <main class="flex flex-col align-center justify-center text-center" v-else>
      <div class="text-center mt-10 mb-6">
        Fetching Data
      </div>
      <i class="fas fa-spinner fa-spin w-24 m-auto"></i>
    </main>
  </div>
 
</template>

<script>
import CountrySelect from "@/components/CountrySelect"
import DataTitle from "@/components/DataTitle"
import DataBoxes from "@/components/DataBoxes"


export default {
  name: "Home",
  components: {
    DataTitle, 
    DataBoxes,
    CountrySelect,
  },
  data(){
    return{
      loading:true,
      title: 'Global',
      dataDate:'',
      status:{},
      countries:[],

    }
  },
  methods:{
    async fetchCovidData(){
      const res = await fetch('https://api.covid19api.com/summary')
      const data = await res.json()
      return data
      
    },
      getCountryData(country){
      this.stats = country
      this.title = country.Country
    },

    async clearCountryData(){
      this.loading = true
      const data = await this.fetchCovidData()
      this.title = 'Global'
      this.stats = data.Global
      this.loading = false
    }
  },

  

  async created(){
    const data = await this.fetchCovidData()
    
    this.dataDate = data.Date
    this.stats = data.Global
    this.countries = data.Countries
    this.loading = false
  },
};
</script>

<style scoped>
.button{
  background-color: #1710f1;
  color: white;
  border: none;
}
.button:disabled{
  background-color: #9c9bb8;
}

</style>
