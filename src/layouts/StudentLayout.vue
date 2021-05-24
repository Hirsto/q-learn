<template>
  <q-layout view="hHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="leftDrawerOpen = !leftDrawerOpen"
        />

        <q-toolbar-title>
          Q-Learn: Student
        </q-toolbar-title>

      </q-toolbar>
    </q-header>
    

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      bordered
      content-class="bg-grey-1"
    >
      <div v-for="topic in topics" :key="topic.ID">
      <q-item clickable v-ripple>
        <q-item-section>{{topic.name}}</q-item-section>
          <q-knob
          show-value
          font-size="12px"
          v-model="topic.progress"
          size="50px"
          :thickness="0.22"
          color="teal"
          track-color="grey-3"
          class="q-ma-md"
          >
          {{ topic.progress }}%
          </q-knob>
      </q-item>
      
      </div>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>

export default {
  name: 'MainLayout',
  //components: { EssentialLink },
  data () {
    return {
      leftDrawerOpen: false,
      topics: [{
        ID: 0,
        name: 'Physics',
        progress: 0
      }]
    }
  }
}
</script>
