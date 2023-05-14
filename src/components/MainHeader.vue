<script>
import { defineComponent } from 'vue'

export default defineComponent({
  data() {
    return {}
  },

  methods: {}
})
</script>

<template>
  <nav class="main-header">
    <ul class="main-header__list list">
      <li class="list__item">
        <a href="/" class="list__link">Home</a>
      </li>
      <li class="list__item">
        <a href="/about" class="list__link">About</a>
      </li>
    </ul>
  </nav>
</template>

<style scoped lang="scss">
.main-header {
  width: 100%;
  height: 80px;
  padding: 0 30px;
  background: aquamarine;

  .list {
    display: flex;
    justify-content: flex-start;
    align-items: center;
    height: 100%;

    &__item {
      margin-right: 10px;
      font-size: 16px;
    }

    &__link {
      color: black;

      &:hover {
        color: red;
        text-decoration: underline;
      }
    }
  }
}
</style>
