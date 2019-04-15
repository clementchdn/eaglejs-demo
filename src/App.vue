<template lang='pug'>
#app
  router-view
</template>

<script>
import Vue from 'vue'
import ToggleButton from 'vue-js-toggle-button'
Vue.use(ToggleButton)
export default {
  name: 'app'
}
</script>

<style lang="scss">
body {
  width: 100%;
  margin: 0 0;
}
html {
  height: 0;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  width: 100%;
  height: 90vh;
}
</style>
