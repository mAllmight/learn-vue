<script>
import { defineComponent } from 'vue'
import axios from 'axios'
import MainPost from '@/components/MainPost.vue'
import ModalForm from '@/components/ModalForm.vue'

export default defineComponent({
  components: {
    ModalForm,
    MainPost
  },

  data() {
    return {
      posts: [],
      isShowModal: false
    }
  },

  methods: {
    getPosts() {
      axios
        .get('https://jsonplaceholder.typicode.com/posts')
        .then((response) => {
          this.posts = response.data.filter((post) => {
            return post.id % 2 !== 0
          })
        })
        .catch((err) => {
          console.log(err)
        })
    },

    createPost() {
      this.isShowModal = true
    },
    closeModalHandler() {
      this.isShowModal = false
    }
  }
})
</script>

<template>
  <div class="home-page">
    <button @click="getPosts" class="home-page__btn">Получить данные</button>
    <button @click="createPost" class="home-page__btn">Создать пост</button>
    <div v-for="post in posts" :key="post.id">
      <MainPost :postData="post" />
    </div>
    <ModalForm v-if="isShowModal" @closeModal="closeModalHandler" />
  </div>
</template>

<style scoped lang="scss">
.home-page {
  &__btn {
    width: 200px;
    height: 50px;
    border-radius: 8px;
    background: aqua;
    color: black;
    &:hover {
      background: darkviolet;
    }
    &:active {
      background: green;
    }
  }
}
</style>
