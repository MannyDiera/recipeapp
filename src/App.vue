<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <Recipe></Recipe>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import Recipe from '@/components/Recipe.vue'

export default {
  name: 'app',
  components: {
    HelloWorld, Recipe
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
