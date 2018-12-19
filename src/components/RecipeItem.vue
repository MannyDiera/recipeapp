<template>
  <li>
    <h2>{{recipe.name}}</h2>
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
      return calories + ' calories';
    },
  },
  methods: {
    showDetails() {
      this.$emit('show-details', this.recipe)
    },
  },
};
</script>
