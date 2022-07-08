<template>
  <div>
    <b-container class="mt-3 text-right">
      <NuxtLink to="/form"
        ><b-button variant="success">Add New</b-button></NuxtLink
      >
    </b-container>
    <Food
      v-for="item in itemList"
      :options="item.options"
      :key="item.id"
      :selectedSize="selectedSize"
      :item="item"
      :name="item.namaMakanan"
      @changeSelected="changeSelected($event)"
    />
  </div>
</template>

<script>
export default {
  data() {
    return {
      selectedSize: "small",
      selectedId: 1,
      itemList: [
        {
          id: 1,
          namaMakanan: "Nasi Padang",
          options: [
            { text: "Small", value: "small" },
            { text: "Medium", value: "medium" },
            { text: "Large", value: "large" },
          ],
          prices: {
            small: 10,
            medium: 15,
            large: 25,
          },
          ingredientsList: ["Sapi", "Babi", "Rendang", "Santan"],
        },
        {
          id: 1,
          namaMakanan: "Nasi Padang",
          options: [
            { text: "Small", value: "small" },
            { text: "Medium", value: "medium" },
            { text: "Large", value: "large" },
          ],
          prices: {
            small: 10,
            medium: 15,
            large: 25,
          },
          ingredientsList: ["Sapi", "Babi", "Rendang", "Santan"],
        },
        {
          id: 1,
          namaMakanan: "Nasi Padang",
          options: [
            { text: "Small", value: "small" },
            { text: "Medium", value: "medium" },
            { text: "Large", value: "large" },
          ],
          prices: {
            small: 10,
            medium: 15,
            large: 25,
          },
          ingredientsList: ["Sapi", "Babi", "Rendang", "Santan"],
        },
      ],
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