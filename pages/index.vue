<template>
  <div>
    <b-container class="mt-3 text-right">
      <NuxtLink to="/form"
        ><b-button variant="success">Add New</b-button></NuxtLink
      >
    </b-container>
    <Food
      v-for="(item, index) in itemList"
      :options="item.options"
      :key="index"
      :selectedSize="selectedSize"
      :item="item"
      :name="item.recipeName"
      @changeSelected="changeSelected($event)"
    />
  </div>
</template>

<script>
import axios from "axios";
export default {
  async fetch() {
    const fetchData = await axios.get(
      `https://6b29a167-3f3e-45e8-83d9-043a5685490f.mock.pstmn.io/getMenuAllByRecipeID`
    );
    console.log(fetchData);
    this.itemList = fetchData.data.completedRecipeList;
  },
  data() {
    return {
      selectedSize: "small",
      selectedId: 1,
      itemList: [],
    };
  },
  methods: {
    changeSelected(data) {
      console.log(data[0]);
      console.log(data[1]);
    },
  },
};
</script>

<style>
.image-wrapper {
  position: relative;
}
img {
  max-height: 200px;
  margin: auto;
  display: block;
  border-radius: 16px;
}
.card-body {
  border: none;
}
</style>