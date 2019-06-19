<template>
  <div id="app">
    <SvgPlayer name="test"/>
    <SvgPlayer name="test2"/>
  </div>
</template>

<script>
import SvgPlayer from './components/SvgPlayer.vue'

export default {
  name: 'app',
  components: {
    SvgPlayer
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
