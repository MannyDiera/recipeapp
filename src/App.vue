<template>
  <div id="app">
    <RecipeList />
  </div>
</template>

<script>
import RecipeList from '@/components/RecipeList.vue'

export default {
  name: 'app',
  components: {
    RecipeList
  },
};
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
