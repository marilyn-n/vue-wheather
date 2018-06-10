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
  <div class="col-md-6">
    <div class="panel panel-default">
      <div class="panel-body" v-for='d in data'>
        <p>
          {{data | json}}
        </p>
      </div>
    </div>
  </div>
</div>
</template>

<script>
import axios from 'axios';

export default {
  name: "HelloWorld",
  data () { 
    return { 
      city: '',
      base_URL: 'http://api.openweathermap.org/data/2.5/',
      api: 'cf703cde5684f6fd594aaece7c6cc8de',
      data: [],
      }
    },
    methods: {

      getData() {
      axios.get(`${this.base_URL}weather?q=${this.city}&appid=${this.api}`)
      .then(response => {
        console.log(response);
        console.log(response.data); 
      });
    },
  }
};
</script>

<style scoped>

</style>
