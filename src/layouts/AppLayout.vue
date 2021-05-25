<template>
  <div>
    <q-layout v-if="loggedin == 'n'">
      <q-page-container>
        <Login @change-Login="changeLogin"/>
      </q-page-container>
    </q-layout>
    
    <div v-if="loggedin != 'n'">
      <student-layout v-bind:topics="topics" v-if="loggedin == 's'"
      @change-Login="changeLogin"/>
      <teacher-layout v-bind:topics="topics" v-if="loggedin == 't'"
      @change-Login="changeLogin"/>
    </div>
  </div>
</template>

<script>
import Login from 'src/pages/Login.vue'
import StudentLayout from './StudentLayout.vue'
import TeacherLayout from './TeacherLayout.vue'

export default {
  name: 'AppLayout',
  components: {  StudentLayout, TeacherLayout, Login },
  methods: {
        changeLogin: function (status){
          this.loggedin = status
          console.log("status")
        }
      },
  data () {
    return {
      loggedin: "n",
      topics: [{
        ID: 0,
        name: 'Math',
        progress: 0,
        questions: [{
          ID: 0,
          qName: 'Addition',
          qParagraphs: 'What is 374 + 474?',
          qCorrect: 1,
          qOptions: [{
            ID: 0,
            label: '825',
            value: '0',
            correct: false
          },
          {
            ID: 1,
            label: '848',
            value: '1',
            correct: true
          },
          {
            ID: 2,
            label: '846',
            value: '2',
            correct: false
          }]
        }]
      }]
    }
  }
}
</script>
