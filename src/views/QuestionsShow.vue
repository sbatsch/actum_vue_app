<template>
  <div class="recipes-show">
    <div class="row">
      <div class="col-md-6">
        <h2 class="text-center">{{ question.category }}</h2>
        <h4 class="text-center"> {{ question.difficulty_level }}</h4>

        <div class="card text-left mb-4">
          <div class="card-header my-header">
            <ul class="nav nav-tabs card-header-tabs">
              <li class="nav-item">
                <span class="nav-link active">Current Question: </span>
              </li>
            </ul>
          </div>

        </div>

        <div class="card text-left mb-4">
          <div class="card-header my-header">
            <ul class="nav nav-tabs card-header-tabs">
              <li class="nav-item">
                <span class="nav-link active"></span>
              </li>
            </ul>
          </div>
          <div class="card-body">
            <p class="card-text">
              <ol>
                <li v-for="direction in question.description">{{ description }}</li>
              </ol>
            </p>
          </div>
        </div>

        <div class="card-body">
          <p class="card-text">
            <ul>
              <li class="btn btn-info m-2" v-bind:to="[NEED ANSWERS URL]">{{ answer_a }}</li>
              <li class="btn btn-info m-2" v-bind:to="[NEED ANSWERS URL]">{{ answer_b }}</li>
              <li class="btn btn-info m-2" v-bind:to="[NEED ANSWERS URL]">{{ answer_c }}</li>
              <li class="btn btn-info m-2" v-bind:to="[NEED ANSWERS URL]">{{ answer_d }}</li>
            </ul>
          </p>
        </div>

        <div>
          <router-link class="btn btn-info m-2" v-bind:to="'/questions/' + question.id + '/edit'">Edit</router-link>
        </div>
      </div>
      <div class="col-md-6">
        <img class="img-fluid w-100 mt-5" v-bind:src="question.image_url" v-bind:alt="question.id">
      </div>
    </div>
    
  <div>
    <h1>{{question.description}}</h1>
  </div>
</template>

<style>
</style>


<script>
var axios = require('axios');

export default {
  data: function() {
    return {
      question: {
        id: "",
        description: "",
        category: "",
        difficulty_level: "",
        answer_key: "",
        answer_a: "",
        answer_b: "",
        answer_c: "",
        answer_d: "",
        true_false: ""
        }
    };
  },
  created: function() {
    axios
      .get("/api/questions/" + this.$route.params.id)
      .then(response => {
        this.question = response.data;
      });
  },
  methods: {
    destroyQuestion: function() {
      axios
        .delete("/api/questions/" + this.$route.params.id)
        .then(response => {
          this.$router.push("/");
        });
    }
  }
};
</script>








