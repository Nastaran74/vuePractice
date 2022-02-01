<template>
  <div>
    <b-jumbotron>
      <hr />
      <template>
        <h3>Question:</h3>
        <p>{{ cQuestion.question }}</p>
      </template>
      <hr class="my-4" />
      <h4>answer:</h4>
      <b-list-group>
        <b-list-group-item v-for="(answer, i) in answers" :key="i"
        @click="ChangeIndex(i)">
        {{answer}}
        </b-list-group-item>
      </b-list-group>

      <p>{{ questionlist }}</p>
      <b-button variant="primary" href="#">Submit</b-button>
      <b-button variant="success" href="#" @click="next">Next</b-button>
    </b-jumbotron>
  </div>
</template>

<script>
export default {
  props: {
    cQuestion: Object,
    next: Function,
  },
  data() {
      return {
          cindex: null
      }
  },
  methods: {
      changeIndex(i){
          this.cindex=i;
      }
  },
  computed: {
    answers() {
      let answers = [...this.cQuestion.incorrect_answers];
      answers.push(this.cQuestion.correct_answer);
      return answers;
    },
  },
};
</script>

<style scoped>
.list-group-item:hover {
  cursor: pointer;
  background-color: aquamarine;
}
.btn {
  margin: 10px 5px;
}
</style>