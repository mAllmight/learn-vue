<script>
import { defineComponent } from 'vue'
import axios from 'axios'
import MainPost from '@/components/MainPost.vue'
import MainUsers from '@/components/MainUsers.vue'

export default defineComponent({
  components: { MainUsers },

  data() {
    return {
      users: []
    }
  },

  methods: {
    getUsers() {
      axios.get('https://jsonplaceholder.typicode.com/users').then((response) => {
        this.users = response.data
      })
    }
  }
})
</script>

<template>
  <div class="about-page">
    <button @click="getUsers" class="about-page__btn">Информация о пользователях</button>
    <div v-for="user in users" :key="user.id">
      <MainUsers v-bind:userData="user" />
    </div>
  </div>
</template>

<style></style>
