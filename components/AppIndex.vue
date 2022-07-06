<template>
  <div class="container">
    <div class="wrapper">
      <div class="circle"></div>
      <div class="header-title">{{ recipeList[selectedRecipeIndex] }}</div>
      <div class="circle"></div>
    </div>
    <div class="row recipe-ingredients-wrapper">
      <div class="col-4 creambg recipe-wrapper">
        <input
          type="button"
          class="btn btn-primary mt-5"
          value="Add New"
          data-bs-toggle="modal"
          data-bs-target="#add-new-recipe"
        />
        <div class="row">
          <div class="col-12 sub-title">Recipes</div>
        </div>
        <ul id="recipe-list" v-for="(recipe, index) in recipeList" :key="index">
          <li @click="getIndex(index)">{{ recipe }}</li>
        </ul>
      </div>
      <div class="col-1"></div>
      <div class="col-7 creambg ingredients-wrapper">
        <input
          type="button"
          class="btn btn-danger mt-5"
          value="Delete"
          @click="deleteRecipe(selectedRecipeIndex)"
        />
        <div class="row">
          <div class="col-12 sub-title">Ingredients</div>
        </div>
        <ol id="ingredients-list">
          <li
            v-for="ingredient in ingredientsList[selectedRecipeIndex]"
            :key="ingredient + '1'"
          >
            {{ ingredient }}
          </li>
        </ol>
        <coba></coba>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      selectedRecipeIndex: 0,
      recipeList: ["Sandwich Egg", "Boiled Water", "Powerpuff Girls"],
      ingredientsList: [
        ["Egg", "Bread", "Mayonaise"],
        ["Water", "Firebender"],
        ["Sugar", "Spice", "Everything Nice", "Chemical X"],
      ],
    };
  },
  name: "IndexPage",
};
</script>

<style scoped>
.header-title {
  background-color: inherit;
  color: white;
  font-size: xx-large;
}

.circle {
  height: 35px;
  width: 35px;
  border-radius: 50%;
  background-color: rgb(214, 186, 72);
}

.wrapper {
  margin-top: 20px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: #3d3d3d;
  padding: 10px;
  border-radius: 16px;
}

.title {
  border-radius: 16px;
}

.creambg {
  background-color: rgb(227, 227, 193);
  overflow: scroll;
  height: 400px;
  box-shadow: 6px 6px 8px 0px rgba(0, 0, 0, 0.75);
}

.sub-title {
  text-align: center;
  font-size: x-large;
  color: rgb(96, 96, 96);
}

.recipe-ingredients-wrapper {
  position: relative;
}

.recipe-wrapper {
  position: absolute;
  left: 40px;
}

.ingredients-wrapper {
  position: absolute;
  right: 30px;
}

li {
  color: rgb(96, 96, 96);
  font-size: larger;
  cursor: pointer;
}

ul li {
  text-decoration: underline rgb(128, 128, 128);
}

[v-cloak] {
  display: none;
}
</style>
