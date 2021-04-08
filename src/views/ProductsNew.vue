<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <form>
      <div class="form-group">
        <label for="newProductName">Name</label>
        <input type="text" class="form-control" id="newProductName" placeholder="enter product name" />
        <label for="newProductDescription">Description</label>
        <input type="text" class="form-control" id="newProductDescription" placeholder="enter product description" />
        <label for="newProductPrice">Price</label>
        <input type="text" class="form-control" id="newProductPrice" placeholder="enter product price" />
        <label for="newProductUrl">Image Url</label>
        <input type="text" class="form-control" id="newProductImageUrl" placeholder="enter product image url" />
        <button v-on:click="createProduct()">Create Product</button>
      </div>
    </form>
  </div>
</template>

<style></style>

<script>
import axios from "axios";
export default {
  data: function () {
    return {
      message: "Add a new product!",
      newProductName: "",
      newProductDescription: "",
      newProductPrice: "",
      newProductImageUrl: "",
    };
  },
  created: function () {},
  methods: {
    createProduct: function () {
      var params = {
        name: this.newProductName,
        description: this.newProductDescription,
        price: this.newProductPrice,
        image_url: this.newProductImageUrl,
      };
      axios.post("/api/products", params).then((response) => {
        console.log("making new product", response);
        this.$router.push("/products");
      });
    },
  },
};
</script>
