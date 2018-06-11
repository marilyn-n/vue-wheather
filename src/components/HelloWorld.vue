<template>
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
     <ul v-if='myData' class="wheather-list">
       <h4>{{myData.name}}</h4>
       <b>{{myData.sys}}</b>
       <h4>Main</h4>
       <li>{{myData.main}}</li>
       <h4>Weather</h4>
       <li>{{myData.weather}}</li>
        <li>{{myData.wind}}</li>
        <li>{{myData.rain}}</li>
        <li>{{myData.clouds}}</li>
        <li><img v-bind:src="`${this.imgURL}{{myData.weather[0].icon}}.png`"></li>

<!-- <img v-bind:src="`${imgPreUrl()}img/logo.png`"> -->

     </ul>
  </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "HelloWorld",
  data() {
    return {
      city: "",
      base_URL: "http://api.openweathermap.org/data/2.5/",
      api: "cf703cde5684f6fd594aaece7c6cc8de",
      myData: [],
      imgURL: 'http://openweathermap.org/img/w/'
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
.wheather-list{
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
