<template >
  <div>
    <ul v-for="(recipe, index) in recipeList" id="recipe-list" :key="index">
      <li @click="getIndex(index)">{{ recipe }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  props: ["recipeList", "recipe", "index"],
  methods: {
    getIndex(index) {
      this.$emit("changeIndex", index);
    },
  },
};
</script>

<style scoped>
li {
  color: rgb(96, 96, 96);
  font-size: larger;
  cursor: pointer;
}
ul li {
  text-decoration: underline rgb(128, 128, 128);
}
</style>