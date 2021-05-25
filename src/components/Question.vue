<template>
  <div>
    <h2>{{question.qName}}</h2>
    <p>{{question.qParagraphs}}</p>
    <q-option-group v-if="!answered"
      :options="question.qOptions"
      label="Answers"
      type="radio"
      v-model="group"
      @input="checkAnswer(question, group)"
      />
    <q-option-group v-else
      :options="question.qOptions"
      label="Answers"
      type="radio"
      v-model="group"
      @input="checkAnswer(question, group)"
      disable
      />
    <p v-show="answered && correct">correct!</p>
    <p v-show="answered && !correct">incorrect!</p>
  </div>
</template>
<script>
export default {
  Name: 'Question',
  props: {
    question: Object
  },
  methods: {
      checkAnswer (question, selection){
          console.log(selection)
          this.answered = true;
          if (selection == question.qCorrect){
              this.correct = true;              
          }
      }
  },
  data () {
    return {
      group: null,
      answered: false,
      correct: false
    }
  }
}
</script>
