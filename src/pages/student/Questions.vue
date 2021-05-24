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
  props: {
    topics: Object,
    questions: Object
  },
  data () {
    return {
    }
  }
}
</script>