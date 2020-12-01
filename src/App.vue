<template>
  <div id="app">
    <musics></musics>
  </div>
</template>

<script>
import musics from './components/musics.vue'

export default {
  name: 'App',
  components: {
    musics
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
  padding:20px;
  background:url("https://images.unsplash.com/photo-1576553836648-156f0007cfd2?ixlib=rb-1.2.1&ixid=MXwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHw%3D&auto=format&fit=crop&w=334&q=80");
  overflow-x:hidden;
  background-repeat: no-repeat;
  background-size: cover;
}
</style>
