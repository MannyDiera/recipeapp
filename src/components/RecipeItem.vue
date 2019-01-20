<template>
  <li>
    <h2>{{recipe.label}}</h2>
    <span>{{recipe.calories | addCals}}</span>
    <img :src="recipe.image" class="tn" />
    <button @click="showDetails">Show Details</button>
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
  },
  filters: {
    addCals: function(calories) {
      return calories.toFixed(0) + ' calories';
    },
  },
  methods: {
    showDetails() {
      this.$emit('show-details', this.recipe)
    },
  },
};
</script>

<style>
  .tn {
    width: 100px;
  }
</style>
