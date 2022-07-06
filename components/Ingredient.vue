<template>
  <div>
    <li
      v-for="ingredient in ingredientsList[selectedRecipeIndex]"
      :key="ingredient + '1'"
    >
      {{ ingredient }}
    </li>
  </div>
</template>

<script>
export default {
  props: ["ingredientsList", "selectedRecipeIndex"],
};
</script>

<style scoped>
li {
  color: rgb(96, 96, 96);
  font-size: larger;
  cursor: pointer;
}
</style>