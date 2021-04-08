<template>
  <div class="home">
    <div class="container-fluid">
      <h1>{{ message }}</h1>
      <div class="row">
        <div class="col-sm-4" v-for="product in products" :key="product.id">
          <div class="card">
            <div class="card-body">
              <h5 class="card-title">{{ product.name }}</h5>
              <p class="card-text">{{ product.description }}</p>
              <p class="card-text">{{ product.price }}</p>
              <a href="#" class="btn btn-primary">Click here for more info!</a>
            </div>
          </div>
          <br />
        </div>
      </div>
    </div>
  </div>
</template>

<style></style>
<script>
import axios from "axios";
export default {
  data: function () {
    return {
      message: "All Products",
      products: [],
    };
  },
  created: function () {
    this.productsIndex();
  },
  methods: {
    productsIndex: function () {
      console.log("getting index");
      axios.get("/api/products").then((response) => {
        console.log(response.data);
        this.products = response.data;
      });
    },
  },
};
</script>
