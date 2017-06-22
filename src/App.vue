<template>
  <div id="app">
    <mega-draft></mega-draft>
  </div>
</template>

<script>
import MegaDraft from './components/MegaDraft'

export default {
  name: 'app',
  components: {
    MegaDraft
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
