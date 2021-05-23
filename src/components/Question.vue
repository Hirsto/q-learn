<template>
  <div>
    <h2>{{question.qName}}</h2>
    <p>{{question.qParagraphs}}</p>
    <q-option-group
      :options="question.qOptions"
      label="Answers"
      type="radio"
      v-model="group"
      />
  </div>
</template>
<script>
export default {
  Name: 'Question',
  props: {
    question: Object
  },
  data () {
    return {
      group: null
    }
  }
}
</script>
