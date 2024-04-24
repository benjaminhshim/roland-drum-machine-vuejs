<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
    <HelloWorld msg="Welcome to Your Vue.js App" 
      @startPlayback="startPlayback" 
      @stopPlayback="stopPlayback"/>
  </div>
</template>

<script>
import HelloWorld from './components/JS-808.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  },
  methods: {
    startPlayback() {
      console.log('startPlayback');
    },
    stopPlayback() {
      console.log('stopPlayback');
    }
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
