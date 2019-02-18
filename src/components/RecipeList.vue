<template>
  <div class="list-wrapper">
    <h1>{{ message }} </h1>
    <br/>

    <input type="number" v-model.number="maxCal" placeholder="Filter by Calories">

    <input type="text" v-model.trim="searchTerm" placeholder="Search term">
    <button :disabled="!searchTerm.length"
      @click="search">search</button>

    <ul class="list" v-if="filteredRecipes.length">
      <RecipeItem
        v-for="recipe in filteredRecipes"
        :key="recipe.name"
        :recipe="recipe"
        @show-details="showDetails"
      />
    </ul>
    <SimpleModal v-if="displaySelected" @close-modal="closeModal">
      <SelectedRecipe :recipe="selectedRecipe" />
    </SimpleModal>
  </div>
</template>

<script>
import RecipeItem from './RecipeItem.vue';
import SelectedRecipe from './SelectedRecipe.vue';
import SimpleModal from './SimpleModal.vue';
import edamamClient from '../edamamClient';

export default {
  name: 'recipe-list',
  components: {
    RecipeItem,
    SelectedRecipe,
    SimpleModal,
  },
  data() {
    return {
      loading: false,
      message: 'Recipes ',
      maxCal: null,
      displaySelected: false,
      selectedRecipe: {},
      searchTerm: '',
      searchResults: [],
      savedRecipes: [],
    };
  },
  methods: {
    closeModal() {
      Object.assign(this, {
        selectedRecipe: {},
        displaySelected: false,
      });
    },
    showDetails(recipe) {
      Object.assign(this, {
        selectedRecipe: recipe,
        displaySelected: true,
      })
    },
    search() {
      this.loading = true;
      edamamClient.search(this.searchTerm)
        .then(data => {
          this.searchResults = data.hits.map(x => x.recipe);
          this.loading = false;
        });
    },
  },
  computed: {
    displayedRecipes() {
      return this.searchResults.length ? this.searchResults : this.savedRecipes;
    },
    filteredRecipes() {
      if (this.maxCal <= 0)
        return this.displayedRecipes;
      return this.displayedRecipes.filter(r => r.calories <= this.maxCal);
    },
  },
}
</script>

<style scoped>
  #app{
    background-color: #ffffff;
    height: 800px;
    padding: 20px;
  }
  .list-wrapper h1{
    height: 50px;
    background: #009688;
    padding-top: 10px;
    padding-left: 11px;
    color: #ffffff;
    box-shadow: 0 4px 7px #b6b6b6;
  }
  h2 {
    color: #00422e;
    margin-left:20px;
  }
  input{
    text-align: center;
    padding: 4px;
    margin-left: 20px;
  }
  /* Card */
  .list > li {
    border:solid 1px gray;
    height: 200px;
    width: 44%;
    margin: 1%;
    float: left;
    padding: 10px;
    box-shadow: 3px 3px 8px gray;
    list-style-type: none;
    color: #00422e;
    text-transform: capitalize;

  }
  .list > li > button{
    color: white;
    background: #009688;
    padding: 4px;
    border-radius: 8px;
    border: none;
    box-shadow: 1px 1px 3px #0b5e56;
    outline: none;
  }
</style>
