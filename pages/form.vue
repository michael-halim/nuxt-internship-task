<template>
  <b-container class="wrapper mt-5">
    <div class="m-4">
      <b-form @submit="onSubmit" @reset="onReset" v-if="show" class="mt-2">
        <!-- Label dan Input Makanan -->
        <b-form-group
          id="input-group-2"
          label="Nama Makanan"
          label-for="namaMakanan"
          class="pt-3"
        >
          <b-form-input
            id="namaMakanan"
            v-model="form.namaMakanan"
            placeholder="Masukkan Nama Makanan"
            required
          ></b-form-input>
        </b-form-group>

        <!-- Label dan Input Foto Makanan -->
        <b-form-group
          id="input-group-2"
          label="Foto Makanan"
          label-for="fotoMakanan"
          ><b-form-file
            id="fotoMakanan"
            v-model="form.foto"
            :state="Boolean(form.foto)"
            placeholder="Pilih Foto Makanan"
            drop-placeholder="Drop file here..."
          ></b-form-file>
        </b-form-group>

        <b-form-group label="Deskripsi Makanan" label-for="deskripsi">
          <b-form-textarea
            id="deskripsi"
            v-model="form.deskripsi"
            size="sm"
            placeholder="Makanan ini adalah makanan khas dari solo. Karakteristik makanan ini...."
          ></b-form-textarea>
        </b-form-group>

        <!-- Size dan Harga  1 -->
        <b-form inline class="mt-4">
          <b-form-group
            label="Size Makanan 1"
            label-for="sizeMakanan1"
            class="mr-5"
          >
            <b-form-input
              id="sizeMakanan1"
              v-model="form.sizeMakanan1"
              placeholder="Small"
              class="ml-3"
              required
            ></b-form-input>
          </b-form-group>

          <b-form-group
            label="Harga Makanan ($)"
            label-for="hargaMakanan1"
            class=""
          >
            <b-form-input
              id="hargaMakanan1"
              v-model="form.hargaMakanan1"
              placeholder="10"
              class="ml-3"
              required
            ></b-form-input>
          </b-form-group>
        </b-form>

        <!-- Size dan Harga  2 -->
        <b-form inline class="mt-3">
          <b-form-group
            label="Size Makanan 2"
            label-for="sizeMakanan2"
            class="mr-5"
          >
            <b-form-input
              id="sizeMakanan2"
              v-model="form.sizeMakanan2"
              placeholder="Medium"
              class="ml-3"
              required
            ></b-form-input>
          </b-form-group>

          <b-form-group
            label="Harga Makanan ($)"
            label-for="hargaMakanan2"
            class=""
          >
            <b-form-input
              id="hargaMakanan2"
              v-model="form.hargaMakanan2"
              placeholder="15"
              class="ml-3"
              required
            ></b-form-input>
          </b-form-group>
        </b-form>

        <!-- Size dan Harga 3 -->
        <b-form inline class="mt-3">
          <b-form-group
            label="Size Makanan 3"
            label-for="sizeMakanan3"
            class="mr-5"
          >
            <b-form-input
              id="sizeMakanan3"
              v-model="form.sizeMakanan3"
              placeholder="Large"
              class="ml-3"
              required
            ></b-form-input>
          </b-form-group>

          <b-form-group
            label="Harga Makanan ($)"
            label-for="hargaMakanan3"
            class=""
          >
            <b-form-input
              id="hargaMakanan3"
              v-model="form.hargaMakanan3"
              placeholder="25"
              class="ml-3"
              required
            ></b-form-input>
          </b-form-group>
        </b-form>

        <!-- Ingredients Makanan -->
        <b-form-group
          label="Ingredients Makanan"
          label-for="ingredientsMakanan"
          class="mt-5"
        >
          <b-form-input
            id="ingredientsMakanan"
            v-model="form.ingredientsList"
            placeholder="Masukkan Ingredients Makanan Dipisahkan Koma"
            required
          ></b-form-input>
        </b-form-group>

        <b-button type="submit" variant="primary">Submit</b-button>
        <b-button type="reset" variant="danger">Reset</b-button>
      </b-form>
      <b-card class="mt-3" header="Form Data Result">
        <pre class="m-0">{{ form }}</pre>
      </b-card>
    </div>
  </b-container>
</template>

<script>
export default {
  data() {
    return {
      form: {
        namaMakanan: "",
        deskripsi: "",
        foto: null,
        ingredientsList: "",
        sizeMakanan1: "",
        hargaMakanan1: "",
        sizeMakanan2: "",
        hargaMakanan2: "",
        sizeMakanan3: "",
        hargaMakanan3: "",
      },
      foods: [
        { text: "Select One", value: null },
        "Carrots",
        "Beans",
        "Tomatoes",
        "Corn",
      ],
      show: true,
    };
  },
  methods: {
    onSubmit(event) {
      const ingredientsList = this.form.ingredientsList.split(",");
      let data = {
        id: Math.floor((1 + Math.random()) * 0x10000).toString(16),
        namaMakanan: this.form.namaMakanan,
        options: [
          { text: this.form.sizeMakanan1, value: this.form.sizeMakanan1 },
          { text: this.form.sizeMakanan2, value: this.form.sizeMakanan2 },
          { text: this.form.sizeMakanan3, value: this.form.sizeMakanan3 },
        ],
        prices: {
          [this.form.sizeMakanan1]: this.form.hargaMakanan1,
          [this.form.sizeMakanan2]: this.form.hargaMakanan2,
          [this.form.sizeMakanan3]: this.form.hargaMakanan3,
        },
        ingredientsList: ingredientsList,
      };

      event.preventDefault();
      alert(JSON.stringify(data));
    },
    onReset(event) {
      event.preventDefault();
      // Reset our form values
      this.form.namaMakanan = "";
      this.form.deskripsi = "";
      this.form.ingredientsList = "";
      this.form.sizeMakanan1 = "";
      this.form.hargaMakanan1 = "";
      this.form.sizeMakanan2 = "";
      this.form.hargaMakanan2 = "";
      this.form.sizeMakanan3 = "";
      this.form.hargaMakanan3 = "";

      // Trick to reset/clear native browser form validation state
      this.show = false;
      this.$nextTick(() => {
        this.show = true;
      });
    },
  },
};
</script>
<style scoped>
.wrapper {
  border-radius: 16px;
  box-shadow: rgba(0, 0, 0, 0.24) 0px 3px 8px;
}
</style>