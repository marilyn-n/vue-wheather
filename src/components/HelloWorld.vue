<template>
<div id="page"> 
  <div class="main">
  <div class="container"> 
    <div class="row">
    <div class="col"> 
      <div class="input-group mb-3">
      <input type="text" class="form-control" v-model="city"  placeholder="Insert Country" aria-label="Recipient's username" aria-describedby="basic-addon2">
        <div class="input-group-append">
          <button class="btn btn-outline-secondary" type="submit" v-on:click="getData">Go</button>
          {{city}}
        </div>
      </div>
     </div>
    </div>
  </div>
  <div class="card mt-3">
    <h1>Forecast</h1>
       <b-list-group v-if='myData' class="list-group">
        <b-list-group-item>
          <h4>Weather and forecasts in {{myData.name}}</h4>
          <img src="http://openweathermap.org/img/w/03n.png" alt="">
          <b>Description: </b>
        </b-list-group-item>
        <b-list-group-item> <b>Wind:</b>{{myData.wind}}</b-list-group-item>
        <b-list-group-item> <b>Cloudiness:</b>{{myData.clouds}}</b-list-group-item>
        <b-list-group-item> <b>Humidity:</b></b-list-group-item>
        <b-list-group-item> <b>Sunrise:</b></b-list-group-item>
        <b-list-group-item> <b>Sunset:</b></b-list-group-item>
        <b-list-group-item> <b>Geo coords:</b></b-list-group-item>

        <!-- <b-list-group-item> <b>Location:</b>{{myData.sys}} </b-list-group-item> -->
        <!-- <b-list-group-item> <b>Temperature Min:</b>{{myData.main.temp_min}}</b-list-group-item>
        <b-list-group-item> <b>Temperature Max:</b>{{myData.main.temp_max}}</b-list-group-item>
        <b-list-group-item> <b>Temperature:</b>{{myData.main.humidity}}</b-list-group-item> -->
        <!-- <b-list-group-item> <b>Weather:</b>{{myData.weather}}</b-list-group-item> -->
        <!-- <b-list-group-item> <b>Rain:</b>{{myData.rain}}</b-list-group-item> -->
        <!-- <b-list-group-item> {{myData.weather[0].description}}</b-list-group-item> -->
        <!-- <b-list-group-item>{{myData.sys.country}}</b-list-group-item>  -->
       </b-list-group>

    </div>
  </div>
  </div>
</template>

<script>
import axios from "axios";


export default {
  components: {
  },
  name: "HelloWorld",
  data() {
    return {
      city: "",
      base_URL: "http://api.openweathermap.org/data/2.5/",
      api: "cf703cde5684f6fd594aaece7c6cc8de",
      myData: [],
    };
  },
  methods: {
    getData() {
      axios.get(`${this.base_URL}weather?q=${this.city}&appid=${this.api}`)
        .then(response => {
          this.myData = response.data;
          console.log(response.data);
        });
    }
  }
};
</script>

<style scoped>
.list-group{
  list-style: none;
  text-align: justify;
}

.card{
  width: 900px;
  margin-left: 150px;
  margin-bottom: 150px;
  padding: 50px;

}
</style>
