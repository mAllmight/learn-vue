<script>
import { defineComponent } from 'vue'

export default defineComponent({
  components: {},

  props: {
    userData: {
      type: Object,
      required: true
    }
  },

  data() {
    return {}
  },

  methods: {}
})
</script>

<template>
  <div class="main-user">
    <p>{{ userData.id }}</p>
    <p>{{ userData.email }}</p>
    <p>{{ userData.username }}</p>
    <p>{{ userData.address.street }}</p>
  </div>
</template>

<style scoped lang="scss">
.main-user {
  width: 100%;
  border: 1px solid black;
  padding: 8px;
  background: rgba(148, 0, 211, 0);
  color: red;
  margin-bottom: 20px;
  p {
    margin-bottom: 8px;
    font-size: 14px;
  }
}
</style>
