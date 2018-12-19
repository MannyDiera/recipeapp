<template>
  <h1>{{recipe.name}}</h1>
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

</style>
