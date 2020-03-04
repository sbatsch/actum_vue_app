<template>
  <div class="recipes-index">
    <h1 class="text-center mb-5">ACTUM</h1>

    <div class="row">
      <div class="col-sm-4 mb-2" v-for="question in questions">
        <router-link v-bind:to="'/questions/' + question.id">
          <div class="card">
            <h1 class="card-img-top">{{question.description}}"</h1>
            <div class="card-body text-info">
              <h5 class="card-title">{{ question.category }}</h5>
              <p class="card-text">Difficulty Level: {{ question.difficulty_level }}</p>
            </div>
          </div>
        </router-link>
      </div>

    </div>
  </div>
</template>

<style>
</style>

<script>
var axios = require("axios");

export default {
  data: function() {
    return {
      questions: []
    };
  },
  created: function() {
    axios
      .get("/api/questions") 
      .then(response => {
        this.questions = response.data;
      });
  },
  methods: {}
};
</script>