<template>
  <student-layout/>
</template>

<script>
import StudentLayout from './StudentLayout.vue'

export default {
  name: 'MainLayout',
  components: {  StudentLayout },
  data () {
    return {
      loggedin: False,
      teacher: False,
      student: False
    }
  }
}
</script>
