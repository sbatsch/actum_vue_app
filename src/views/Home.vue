<template>
  <div class="home">
    <h1>{{ questions[1] }}</h1>
  </div>
</template>

<style>
</style>

<script>
var axios = require("axios");

export default {
  data: function() {
    return {
      message: "Welcome to Vue.js!",
      questions: []
    };
  },
  created: function() {
    axios
        .get('/api/questions')
        .then(response =>{
          this.questions = response.data
        });
  },
  methods: {}
};
</script>