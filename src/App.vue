<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Welcome to Your Vue.js App"/>
  <HourCalculator />
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import HourCalculator from './components/HourCalculator.vue';

export default {
  name: 'App',
  components: {
    HelloWorld, HourCalculator
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
