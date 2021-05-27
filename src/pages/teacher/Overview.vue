<template>
  <q-page class="flex flex-center justify evenly">
    <div>
      <h1>{{topic.name}}</h1>
    </div>
    <div class="column">
      <div v-for="question in topic.questions" :key="question.ID">{{question.qParagraphs}}</div>
    </div>

    <div>
      <h4>Add a new question</h4>
        <div class="q-pa-md" style="max-width: 400px">

    <q-form
      @submit="onSubmit"
      @reset="onReset"
      class="q-gutter-md"
    >
      <q-input
        filled
        v-model="title"
        label="Question Title"
        hint="The title of the question"
        lazy-rules
        :rules="[ val => val && val.length > 0 || 'Please type something']"
      />
      <q-input
        filled
        v-model="paragraph"
        label="Question paragraph"
        hint="What you want your students to answer"
        lazy-rules
        :rules="[ val => val && val.length > 0 || 'Please type something']"
      />

      <q-input
        filled
        v-model="option_1"
        label="The first option"
        lazy-rules
        :rules="[ val => val && val.length > 0 || 'Please type something']"
      />
      <q-input
        filled
        v-model="option_2"
        label="The second option"
        lazy-rules
        :rules="[ val => val && val.length > 0 || 'Please type something']"
      />
      <q-input
        filled
        v-model="option_3"
        label="The third option"
        lazy-rules
        :rules="[ val => val && val.length > 0 || 'Please type something']"
      />
      <q-input
        filled
        v-model="option_4"
        label="The fourth option"
        lazy-rules
        :rules="[ val => val && val.length > 0 || 'Please type something']"
      />
      
      <div>
        <q-btn label="Submit" type="submit" color="primary"/>
        <q-btn label="Reset" type="reset" color="primary" flat class="q-ml-sm" />
      </div>
    </q-form>

  </div>
    </div>
  </q-page>
</template>

<script>
export default {
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
      },
      
    onSubmit () {
      if (this.accept !== true) {
        this.$q.notify({
          color: 'red-5',
          textColor: 'white',
          icon: 'warning',
          message: 'Please complete the above'
        })
      }
      else {
        this.$q.notify({
          color: 'green-4',
          textColor: 'white',
          icon: 'cloud_done',
          message: 'Submitted',
        })
        this.$emit('add-question',
        this.title,
        this.paragraph,
        this.option_1,
        this.option_2,
        this.option_3,
        this.option_4)
        
      }
    },

    onReset () {
      this.title = null
      this.paragraph = null
      this.option_1 = null
      this.option_2 = null
      this.option_3 = null
      this.option_4 = null
      this.accept = false
    }
  },
  
  data () {
    return {
      qActive: false,
      qNumber: this.topic.questions.length,
      title: null,
      paragraph: null,
      option_1: null,
      option_2: null,
      option_3: null,
      option_4: null,

      accept: true
    }
  }
}
</script>