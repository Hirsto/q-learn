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
      <q-item clickable v-ripple @click="setActive(topic.ID)">
        <q-item-section>{{topic.name}}</q-item-section>
          <q-knob
          readonly
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
      <h5>Add a new topic</h5>
      <q-form
      @submit="onSubmit"
      @reset="onReset"
      class="q-gutter-md"
      >
      <q-input
        filled
        v-model="name"
        label="Topic Name"
        :rules="[ val => val && val.length > 0 || 'Please type something']"
      />



      <div>
        <q-btn label="Submit" type="submit" color="primary"/>
        <q-btn label="Reset" type="reset" color="primary" flat class="q-ml-sm" />
      </div>
    </q-form>
      
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
    topics: Array
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
        },
      addTopic: function (name){
        this.$emit('add-topic', name)
      },
      onSubmit () {
      
        this.$q.notify({
          color: 'green-4',
          textColor: 'white',
          icon: 'cloud_done',
          message: 'Submitted'
        })
        this.$emit('add-topic', this.name)
      
    },

    onReset () {
      this.name = null
    },
    setActive(ID){
      this.activeTopicNum = ID,
      this.activeTopic = this.topics[ID]
    }

  },
  data () {
    return {
      name: null,
      leftDrawerOpen: false,
      activeTopicNum: 0,
      activeTopic: this.topics[0]
    }
  }
}
</script>
