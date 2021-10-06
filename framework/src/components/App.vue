<template>
  <div id="app">
    <giphy></giphy>
  </div>
</template>

<script>
import Giphy from './Giphy.vue'

export default {
  name: 'app',
  data () {
    return {
      msg: ''
    }
  },
  components: {
    Giphy,
  },
}
</script>

<style>
</style>
