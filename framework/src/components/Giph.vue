<template>
  <div>          
  <iframe :src="url" width="500" frameBorder="0" class="giphy-embed" allowFullScreen></iframe>
  </div>
</template>

<script>

    export default {
      name: 'giph',
      props: {
          url: String
      },
      data () {
          return {
          }
      },
      methods: {},
    }

    
</script>

<style>
</style>
