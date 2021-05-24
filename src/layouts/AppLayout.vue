<template>
  <div>
    <q-layout v-if="loggedin == 'n'">
      <q-page-container>
        <Login @change-Login="changeLogin"/>
      </q-page-container>
    </q-layout>
    
    <div v-if="loggedin != 'n'">
      <student-layout v-bind:topics="topics" v-bind:questions="questions" v-if="loggedin == 's'"/>
      <teacher-layout v-bind:topics="topics" v-bind:questions="questions" v-if="loggedin == 't'"/>
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
        progress: 0
      }],
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
