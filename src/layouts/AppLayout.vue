<template>
  <div>
    <q-layout v-if="!loggedin">
      <q-page-container>
        <Login/>
      </q-page-container>
    </q-layout>
    
    <div v-if="loggedin">
      <student-layout v-bind:topics="topics" v-bind:questions="questions" v-if="student"/>
      <teacher-layout v-bind:topics="topics" v-bind:questions="questions" v-if="teacher"/>
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
  data () {
    return {
      loggedin: false,
      teacher: false,
      student: false,
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
