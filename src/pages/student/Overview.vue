<template>
  <q-page class="flex flex-center column">
    <Questions @improve-results="improveResults"
    @out-of-questions="activateQuestions" v-if="qActive" v-bind:topic="this.topic"/>
    <div v-else >
      <h1>{{this.topic.name}}</h1>
      <h4>Number of questions in this topic: {{this.topic.questions.length}}</h4>
      <h4>Number of questions you've gotten correct: {{this.topic.progress}}</h4>
      <q-btn :ripple="{ center: true }" color="secondary" label="Attempt Questions"
        @click="activateQuestions()"/>
      <p v-if="!questionsAvaliable">There are no avaliable questions in this topic</p>
    </div>
  </q-page>
</template>

<script>
import Questions from './Questions.vue'
export default {
  components: { Questions },
  name: 'Overview',
  props: {
    topic: Object
  },
  methods: {
    activateQuestions () {
      if (this.topic.questions.length >0){
      this.qActive = !this.qActive;
      } else {
        this.questionsAvaliable = false;
      }
    }, 
      improveResults () {
          this.$emit('improve-results')
      }
  },
  
  data () {
    return {
      qActive: false,
      qNumber: this.topic.questions.length,
      questionsAvaliable: true
    }
  }
}
</script>