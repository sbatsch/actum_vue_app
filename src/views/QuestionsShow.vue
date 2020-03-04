<template>
  <div class="questions-show">
    <div class="row">
      <div class="col-md-6">
        <h2 class="text-center">{{ question.category }}</h2>
        <h4 class="text-center">{{ question.difficulty_level }}</h4>

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
                <li>{{ question.description }}</li>
              </ol>
            </p>
          </div>
        
</div>
        <div class="card-body">
          <p class="card-text">
            <ul>
              <p v-bind:class="{'text-success': question.answer_key === chosen_answer && question.answer_key === question.answer_a}" class="btn btn-info m-2" v-on:click="checkAnswer(question.answer_a)">{{ question.answer_a }}</p>
              <p v-bind:class="{'text-success': question.answer_key === chosen_answer && question.answer_key === question.answer_b}" class="btn btn-info m-2" v-on:click="checkAnswer(question.answer_b)">{{ question.answer_b }}</p>
              <p v-bind:class="{'text-success': question.answer_key === chosen_answer && question.answer_key === question.answer_c}" class="btn btn-info m-2" v-on:click="checkAnswer(question.answer_c)">{{ question.answer_c }}</p>
              <p v-bind:class="{'text-success': question.answer_key === chosen_answer && question.answer_key === question.answer_d}" class="btn btn-info m-2" v-on:click="checkAnswer(question.answer_d)">{{ question.answer_d }}</p>
            </ul>
          </p>
        </div>

        <div>
          <router-link class="btn btn-info m-2" v-bind:to="'/questions/' + question.id + '/edit'">Edit</router-link>
        </div>
      </div>
      <div class="col-md-6">
      </div>
    </div>
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
        true_false: "",
      },
      chosen_answer: ""
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
    },
    checkAnswer: function(answerString) {
      this.chosen_answer = answerString;
      // if(this.question.answer_key === this.question["answer_" + letter]) {
      //   document.getElementById("answer_" + letter).style.color = "green";
      // } else {
      //    document.getElementById("answer_" + letter).style.color = "red";
      // }
    }
  }
};

</script>








