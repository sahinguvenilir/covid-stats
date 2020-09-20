<template>
  <div class="card text-center m-3">
    <h5 class="card-header">Covid Stats (updated every 15 min)</h5>
    <div class="card-body" v-for="info in countryData" :key="info.key">
   
      <table>
        <tr>
          <th>Country</th>
          <th>Confirmed</th>
          <th>Recovered</th>
          <th>Critical</th>
          <th>Deaths</th>
          <th>Last Update</th>


        </tr>
        <tbody>
        <tr>
          <td>{{info.country}}</td>
          <td>{{info.confirmed}}</td>
          <td>{{info.recovered}}</td>
          <td>{{info.critical}}</td>
          <td>{{info.deaths}}</td>
          
          <td>{{new Date(info.lastUpdate) | dateFormat('DD MMMM YYYY - HH:mm A')}}</td>
          
        </tr>
        </tbody>
          
      </table>
          </div>
  </div>
</template>


<script>


export default {
  name: "display",
  props: ['countryData']
  
  };

  
  
</script>


<style>
td, th {
  border: 1px solid #dddddd;
  text-align: left;
  padding: 8px;
}
</style>
