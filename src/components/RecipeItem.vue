<template>
  <li>
    <h2>{{recipe.name}}</h2>
    <button @click="showCalories1(recipe)" v-if="recipe.show"> Hide Calories</button>
    <button @click="showCalories1(recipe)" v-else> Show Calories</button>
    <p v-show="recipe.show"> {{recipe.calories | addCals}}</p>
  </li>
</template>

<script>
export default {
  name: 'recipe-item',
  props: {
    recipe: {
      type: Object,
      required: true,
    },
    showCalories: {
      type: Function,
      required: true,
    }
  },
  filters: {
    addCals: function(calories) {
      return calories + ' calories';
    },
  },
  methods: {
    showCalories1: function(recipe) {
        this.$emit('show-calorie', recipe);
    },
  },
};
</script>
