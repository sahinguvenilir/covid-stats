<template>
  <div class="p-3 text-center"> 
    <h3>Demo</h3>
    <search v-on:SearchRequested="handleSearch"></search>
    <display :countryData=countryData :dataCount=dataCount></display>

  </div>
</template>

<script>
import display from "./components/display";
import Search from "./components/search"
import axios from 'axios';
import Vue from 'vue';
import VueFilterDateFormat from 'vue-filter-date-format';

Vue.use(VueFilterDateFormat);

export default {
  name: "app",
  components: {
    display, Search
  },
  data() {
    
    
    return {
      isLoading: true,
      countryData: [],
      dataCount: false
    }
  },
  methods: {

    
    handleSearch (query) {
      
      axios.get(`https://covid-19-data.p.rapidapi.com/country`,

    {
headers: {
      "x-rapidapi-host":"covid-19-data.p.rapidapi.com",
    "x-rapidapi-key":"0002deebc5mshcc0aabe2fd665b9p188943jsnab519b09a82b",
    "useQueryString":true
    },"params":{
    "format":"json",
    "date-format":"YYYY-MM-DD",
    "name":`${query}`

}
    })
    

      .then((response)=>{
      this.countryData = response.data;
      this.dataCount = this.countryData && this.countryData.length

    })
    .catch((error)=>{
      console.log(error)
    })
        
    }
    
  
    
    },
 
}
</script>
