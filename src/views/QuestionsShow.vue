<template>
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
    destroyRecipe: function() {
      axios
        .delete("/api/questions/" + this.$route.params.id)
        .then(response => {
          this.$router.push("/");
        });
    }
  }
};
</script>








