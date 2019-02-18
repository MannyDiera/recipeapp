<template>
  <li class="summary-card">
    <div class="tn">
      <img :src="recipe.image" />
    </div>
    <div class="recipe-meta">
      <h2>{{recipe.label}}</h2>
      <p>{{recipe.calories | addCals}}</p>
      <button @click="showDetails">Show Details</button>
    </div>
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
button {
  cursor: pointer;
}

.summary-card {
  display: flex;
}

.tn {
  display: inline-flex;
  vertical-align: middle;
}

.tn img {
  max-height: 200px;
  margin: auto;
}

.recipe-meta {
  flex-grow: 1;
  padding-left: 20px;
  text-align: right;
}

.recipe-meta h2 {
  text-align: left;
  color: #009688;
  font-weight: bold;
}
</style>
