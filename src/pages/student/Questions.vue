<template>
  <q-page class="flex flex-center">
    <Question v-bind:question="questions[0]"/>
  </q-page>
</template>

<script>
import Question from '../../components/Question.vue'
export default {
  components: { Question },
  name: 'Questions',
  data () {
    return {
      questions: [{
        ID: 0,
        qName: 'test',
        qParagraphs: 'This is a test paragraph',
        qOptions: [{
          ID: 0,
          label: 'This is the correct option',
          value: 'corr'
        },
        {
          ID: 1,
          label: 'This is the incorrect option',
          value: 'incorr'
        }]
      }]
    }
  }
}
</script>