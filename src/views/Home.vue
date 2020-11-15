<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <br>
    <h1>All Flavors of IceCream for your Enjoyment!</h1>
    <div v-for="flavor in flavors">
      <ul>
        <li>title: {{flavor.title}}</li>
        <li>{{flavor.description}}</li>
        <li>price!: {{flavor.price}}</li>
        <hr>
      </ul>
    </div>


  </div>

</template>

<style>
</style>

<script>
import axios from "axios";

export default {
  data: function() {
    return {
      message: "Welcome to Vue.js!",
      flavors: []
    };
  },
  
  created: function() {
    this.indexFlavors();
  },


  methods: {
    indexFlavors: function() {
      axios.get("/api/flavors").then(response => {
        console.log("flavors index: ", response);
        this.flavors = response.data;
      });
    },
  },
};
</script>