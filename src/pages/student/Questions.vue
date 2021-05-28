<template>
  <q-page class="flex flex-center column">
    <Question @improve-results="improveResults" 
    v-bind:question="topic.questions[current_question]"/>
    <div style="height: 50px"/>
    <q-btn label="Continue" @click="nextQuestion"/>
    <p> You have {{this.topic.questions.length - this.current_question -1}} questions left</p>
  </q-page>
</template>

<script>
import Question from '../../components/Question.vue'
export default {
  components: { Question },
  name: 'Questions',
  props: {
    topic: Object
  },
  methods: {
      nextQuestion () {
          if (this.current_question + 1 == this.topic.questions.length){
              this.$emit('out-of-questions')
          } else {
              this.current_question = this.current_question +1;
          }
      }, 
      improveResults () {
          this.$emit('improve-results')
      }
  },
  data () {
    return {
        current_question: 0
    }
  }
}
</script>