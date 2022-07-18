<template>
  <div>
    <NavbarSide />
    <div class="container">
      <div class="row mt-4">
        <div class="col">
          <h2>Daftar Makanan</h2>
        </div>
      </div>
      <div class="row">
        <div class="col">
          <div class="input-group mb-3">
            
            <input
              v-model="search"
              type="text"
              class="form-control"
              placeholder="Cari makanan favoritmu!"
              aria-label="Cari makanan favoritmu!"
              aria-describedby="basic-addon1"
              @keyup="searchFood"
            />
          <span class="input-group-text" id="basic-addon1"><b-icon icon="search" ></b-icon></span>
          </div>
        </div>
      </div>
      <div class="row mb-4">
        <div class="col md-4" v-for="product in products" :key="product.id">
          <CardProduct :product="product" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import NavbarSide from "@/components/Navbar.vue";
import CardProduct from "@/components/CardProduct.vue";
import axios from "axios";

export default {
  name: "FoodView",
  components: {
    NavbarSide,
    CardProduct,
  },
  data() {
    return {
      products: [],
      search:''
    };
  },
  methods: {
    setProducts(data) {
      this.products = data;
    },
    searchFood(){
        axios
      .get("http://localhost:3000/products?q="+this.search)
      .then((response) => this.setProducts(response.data))
      .catch((error) => console.log(error));
    }
  },
  mounted() {
    axios
      .get("http://localhost:3000/products")
      .then((response) => this.setProducts(response.data))
      .catch((error) => console.log(error));
  },
};
</script>

<style>
</style>