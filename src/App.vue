<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <Final />
  </div>
</template>

<script>
import Final from './components/Final.vue'

export default {
  name: 'App',
  components: {
    Final
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
