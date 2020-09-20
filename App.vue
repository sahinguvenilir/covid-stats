<template>
  <div class="p-3 text-center">
    <h3>Demo</h3>
    <search v-on:SearchRequested="handleSearch"></search>
    <display :countryData=countryData></display>

  </div>
</template>

<script>
import display from "./components/display";
import Search from "./components/search"
import axios from 'axios';
import Vue from 'vue';
import VueFilterDateFormat from 'vue-filter-date-format';

Vue.use(VueFilterDateFormat);

require('dotenv').config();

export default {
  name: "app",
  components: {
    display, Search
  },
  data() {
    
    
    return {
      isLoading: true,
      countryData: [],

    }
  },
  methods: {

    
    handleSearch (query) {
      
      axios.get(`https://covid-19-data.p.rapidapi.com/country`,

    {
headers: {
      "x-rapidapi-host":"covid-19-data.p.rapidapi.com",
    "x-rapidapi-key":"YOUR API-KEY",
    "useQueryString":true
    },"params":{
    "format":"json",
    "date-format":"YYYY-MM-DD",
    "name":`${query}`

}
    })
    
      .then(response => this.countryData = response.data)

    }
    
  
    
    },
 
}
</script>
