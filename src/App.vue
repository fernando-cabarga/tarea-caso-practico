<template>
  <div id="app">
    
    <Documento />
  </div>
</template>

<script>

import Documento from '@/components/Documento.vue'

export default {
  name: 'App',
  components: {
    Documento
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #2c3e50;
  margin-top: 60px;
}

</style>
