<template>
  <b-container class="bv-example-row wrapper mt-3">
    <b-row>
      <b-col>
        <b-row class="mt-3 mb-1 ml-1">
          <h5>{{ item.recipeName }}</h5>
        </b-row>
        <b-row class="image-wrapper mb-3">
          <img :src="item.menuList[selectedSize].image" alt="" />
        </b-row>
      </b-col>

      <b-col class="mt-5">{{ item.recipeDescription }} </b-col>
      <div class="mt-5 ml-3 mr-2">
        <b-col class="border-right">
          <b-row>
            <b-form-group>
              <b-form-radio-group
                id="btn-radios-2"
                v-model="selectedSize"
                @click="changeSelected(selectedSize)"
                :options="options"
                button-variant="outline-primary"
                size="sm"
                name="radio-btn-outline"
                buttons
              ></b-form-radio-group>
            </b-form-group>
            <h5 class="ml-4 mr-3">
              Rp. {{ item.menuList[selectedSize].price }}
            </h5>
          </b-row>
          <b-row class="mt-5 mr-2 mb-4">
            <nuxt-link
              :to="{ name: 'form', params: { foodID: item.recipeID } }"
              class="btn-block"
              ><b-button variant="outline-info">Edit</b-button></nuxt-link
            >
          </b-row>
        </b-col>
      </div>

      <b-col class="mt-5">
        <h5>Ingredients</h5>
        <ul
          class="ingredients-list"
          v-for="ingredients in item.recipeIngredients"
          :key="ingredients"
        >
          <li>{{ ingredients }}</li>
        </ul></b-col
      >
    </b-row>
  </b-container>
</template>

<script>
export default {
  props: ["options", "item", "selectedSize", "name"],
  methods: {
    changeSelected(size) {
      this.item.prices = this.item.prices[size];
    },
  },
};
</script>

<style scoped>
.ingredients-list {
  list-style: none;
  margin: 0;
  padding: 0;
}

.wrapper {
  border-radius: 16px;
  box-shadow: rgba(99, 99, 99, 0.2) 0px 2px 8px 0px;
  cursor: pointer;
  transition: 0.5s ease-in-out;
}
.wrapper:hover {
  box-shadow: -2px 0px 78px -35px rgba(0, 0, 0, 0.75);
  transition: 0.3s ease-in-out;
  padding: 1rem;
}
</style>