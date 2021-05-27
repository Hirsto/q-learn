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
          Q-Learn: Teacher
        </q-toolbar-title>
      <q-btn :ripple="{ center: true }" flat dense label="Logout"  @click="changeLogin('n')"/>
      </q-toolbar>
    </q-header>
    

    <q-drawer
      v-model="leftDrawerOpen"
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
      <overview v-bind:topic="activeTopic" @add-question="addQuestion"/>
    </q-page-container>
  </q-layout>
</template>

<script>
import Overview from 'src/pages/teacher/Overview.vue'

export default {
  components: { Overview },
  name: 'MainLayout',
  //components: { EssentialLink },
  props: {
    topics: Object
  },
  methods: {
      changeLogin: function (status) {
          this.$emit('change-Login', status)
      },
      addQuestion: function (
            title,
            paragraph,
            option_1,
            option_2,
            option_3,
            option_4,
            correct){
          this.$emit('add-question',
          this.activeTopicNum,
          title,
          paragraph,
          option_1,
          option_2,
          option_3,
          option_4,
          correct)
        }
  },
  data () {
    return {
      leftDrawerOpen: false,
      activeTopicNum: 0,
      activeTopic: this.topics[0]
    }
  }
}
</script>
