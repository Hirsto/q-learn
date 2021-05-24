<template>
  <q-page class="flex flex-center justify-evenly">
    <div class="justify-center">
        <h3>Login to Q-Learn</h3>
    </div>
    
    <div class="column justify-evenly" style="height: 150px">
        <q-btn :ripple="{ center: true }" color="secondary" label="I'm a student" />
        <q-btn :ripple="{ center: true }" color="secondary" label="I'm a teacher" />
    </div>
  </q-page>
</template>

<script>
export default {
  name: 'Login'
}
</script>
