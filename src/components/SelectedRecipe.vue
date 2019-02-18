<template>
  <div>
    <h1><a :href="recipe.url" target="recipe-source">{{recipe.label}}</a></h1>
    <img :src="recipe.image" />
    <ul>
      <li v-for="(ing, i) in recipe.ingredientLines" :key="i">{{ing}}</li>
    </ul>
    <p>Calories: {{recipe.calories.toFixed(0)}}</p>
    <p>Yield: {{recipe.yield}}</p>
    <!-- <p>Yield: {{recipe.healthLabels}}</p> -->
    <!-- <p>{{Object.keys(recipe)}}</p> -->
  </div>
</template>

<script>
export default {
  props: {
    recipe: {
      type: Object,
      required: true,
    },
  },
}
</script>

<style>

h1 a {
  color: #009688;
  text-decoration: none;
}

li {
  text-align: left;
}

</style>
