<template>
  <q-page class="flex flex-center column">
    <Question v-bind:question="topic.questions[current_question]"/>
    <div style="height: 50px"/>
    <q-btn label="Continue" @click="nextQuestion"/>
    <p> You have {{this.qNumber - this.current_question -1}} questions left</p>
  </q-page>
</template>

<script>
import Question from '../../components/Question.vue'
export default {
  components: { Question },
  name: 'Questions',
  props: {
    topic: Array
  },
  methods: {
      nextQuestion () {
          if (this.current_question + 1 == this.qNumber){
              console.log("out of questions");
          } else {
              this.current_question = this.current_question +1;
          }
      }
  },
  data () {
    return {
        current_question: 0,
        qNumber: this.topic.questions.length
    }
  }
}
</script>