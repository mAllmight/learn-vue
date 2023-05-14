<script>
import { defineComponent } from 'vue'
import axios from 'axios'

export default defineComponent({
  emits: ['closeModal'],
  components: {},

  data() {
    return {
      bodyInput: '',
      titleInput: ''
    }
  },
  computed: {
    isButtonDisabled() {
      return this.bodyInput.trim() === '' || this.titleInput.trim() === ''
    }
  },
  methods: {
    closeModal() {
      this.$emit('closeModal')
    },
    createPost() {
      axios
        .post('https://jsonplaceholder.typicode.com/posts', {
          title: this.titleInput,
          body: this.bodyInput
        })
        .then(() => {
          this.bodyInput = ''
          this.titleInput = ''
          this.closeModal()
        })
    }
  }
})
</script>

<template>
  <div class="modal-form">
    <div class="modal-form__container">
      <button @click="closeModal" class="modal-form__close">X</button>

      <form @submit.prevent="createPost" class="modal-form__form form">
        <input type="text" v-model="titleInput" placeholder="введите TITLE" class="form__input" />
        <input type="text" v-model="bodyInput" placeholder="введите BODY" class="form__input" />
        <button type="submit" class="form__submit" :disabled="isButtonDisabled">Сохранить</button>
      </form>
    </div>
  </div>
</template>

<style scoped lang="scss">
.modal-form {
  position: fixed;
  z-index: 1;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  background: rgba(128, 128, 128, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
  &__close {
    background: red;
    width: 20px;
    height: 20px;
    border-radius: 50%;
    color: black;
    display: flex;
    justify-content: center;
    align-items: center;
    position: absolute;
    top: 20px;
    right: 20px;
  }

  &__container {
    width: 700px;
    background: white;
    min-height: 500px;
    padding: 50px 20px 20px 20px;
    position: relative;
  }
  .form {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    &__input {
      width: 100%;
      height: 50px;
      padding: 8px;
      border: 1px solid black;
      margin-bottom: 12px;
    }
    &__submit {
      width: 200px;
      height: 50px;
      border-radius: 10px;
      background: green;
      color: black;
      &:hover {
        background: gold;
      }
      &:active {
        background: blue;
      }
      &:disabled {
        background: gray;
        cursor: not-allowed;
      }
    }
  }
}
</style>
