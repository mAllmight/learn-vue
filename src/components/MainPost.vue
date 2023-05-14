<script>
import { defineComponent } from 'vue'

export default defineComponent({
  components: {},

  props: {
    postData: {
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
  <div class="main-post">
    <p>{{ postData.id }}</p>
    <p>{{ postData.body }}</p>
    <p>{{ postData.title }}</p>
  </div>
</template>

<style scoped lang="scss">
.main-post {
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
