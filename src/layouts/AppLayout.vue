<template>
  
  <div v-if="loggedin">
    <student-layout v-bind:topics="topics" v-bind:questions="questions" v-if="student"/>
    <teacher-layout v-bind:topics="topics" v-bind:questions="questions" v-if="teacher"/>
  </div>
</template>

<script>
import StudentLayout from './StudentLayout.vue'
import TeacherLayout from './TeacherLayout.vue'

export default {
  name: 'AppLayout',
  components: {  StudentLayout, TeacherLayout },
  data () {
    return {
      loggedin: true,
      teacher: false,
      student: true,
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
