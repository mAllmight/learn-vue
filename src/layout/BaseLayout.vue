<script>
import { defineComponent } from 'vue'
import { RouterView } from 'vue-router'
import MainHeader from '@/components/MainHeader.vue'

export default defineComponent({
  components: {
    RouterView,
    MainHeader
  },

  data() {
    return {}
  },

  methods: {}
})
</script>

<template>
  <div>
    <MainHeader />
    <RouterView />
  </div>
</template>

<style></style>
