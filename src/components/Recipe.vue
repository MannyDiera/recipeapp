<template>
        <div class="list-wrapper">
                <h1>{{ message }} </h1>
                <br/>
                
                <h2>Enter max calorie amount to see results.</h2>
                <input type="number" v-model.number="maxCal" placeholder="Enter as 603, 700, etc ">
                
                <ul class="list" v-if="maxCal >= 1">
                  <RecipeItem
                    v-for="(recipe, index) in recipes"
                    v-if="recipe.calories < maxCal"
                    :recipe="recipe"
                    :show-calories="showCalories"
                    @show-calorie="showCalories"
                />
                </ul>
                
        </div> 
</template>

<script>
import RecipeItem from './RecipeItem.vue'

export default {
    name: 'recipe',
    components: {
        RecipeItem,
    },
    data: function (){
        return {
        message: 'Recipes ',
        maxCal: null,
        showCals: false,
        recipes: [
          {name:'lasagna', calories: 500, show: false},
          {name:'ceviche', calories: 602, show: false},
          {name:'pasta', calories: 698, show: false},
          {name:'pizza', calories: 807, show: false}
        ]
      }
    },
    methods: {
        showCalories (recipe) {
            // recipe.show = !recipe.show
          }
      },

      
      computed: {

    },
    mounted: () => {

    },
    created: () => {

    }


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