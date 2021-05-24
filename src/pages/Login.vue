<template>
  <q-page class="flex flex-center justify-evenly">
    <div class="justify-center">
        <h3>Login to Q-Learn</h3>
    </div>
    
    <div class="column justify-evenly" style="height: 150px">
        <q-btn :ripple="{ center: true }" color="secondary" label="I'm a student" 
        @click="changeLogin('s')"/>
        <q-btn :ripple="{ center: true }" color="secondary" label="I'm a teacher"
        @click="changeLogin('t')"/>
    </div>
  </q-page>
</template>

<script>
export default {
  name: 'Login',
  data () {
    return {
    }
  },
  
  methods: {
      changeLogin: function (status) {
          this.$emit('change-Login', status)
      }
  }
}
</script>
