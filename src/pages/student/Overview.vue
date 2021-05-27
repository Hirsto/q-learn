<template>
  <q-page class="flex flex-center column">
    <Questions @improve-results="improveResults"
    @out-of-questions="activateQuestions" v-if="qActive" v-bind:topic="this.topic"/>
    <div v-else >
      <h1>{{this.topic.name}}</h1>
      <h4>Number of questions in this topic: {{qNumber}}</h4>
      <h4>Number of questions you've gotten correct: {{this.topic.progress/qNumber}}</h4>
      <q-btn :ripple="{ center: true }" color="secondary" label="Attempt Questions"
        @click="activateQuestions()"/>
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
      this.qActive = !this.qActive;
    }, 
      improveResults () {
          this.$emit('improve-results')
      }
  },
  
  data () {
    return {
      qActive: false,
      qNumber: this.topic.questions.length
    }
  }
}
</script>