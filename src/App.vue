<template>
  <div id="app">
    <h1>Megadraft Test</h1>
    <p>
      Test rendering a react library inside a Vue.js component.
    </p>
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
