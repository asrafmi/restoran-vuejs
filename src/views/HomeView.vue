<template>
  <div class="home">
    <NavbarSide />
    <div class="container">
      <HeroPart />

      <div class="row mt-3">
        <div class="col">
          <h2>Makanan <strong>Terlaris</strong></h2>
        </div>
        <div class="col">
          <router-link to="/foods" class="btn btn-info float-right"
            ><b-icon icon="eye" animation="throb"></b-icon>&nbsp; Lihat
            semua</router-link
          >
        </div>
      </div>

      <div class="row mb-3">
        <div class="col md-4 mt-4" id="row-best-products" v-for="product in products" :key="product.id">
          <CardProduct :product="product"/>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import NavbarSide from '@/components/Navbar.vue'
import HeroPart from '@/components/Hero.vue'
import CardProduct from '@/components/CardProduct.vue'
import axios from "axios"

export default {
  name: 'HomeView',
  components: {
    NavbarSide,
    HeroPart,
    CardProduct
  },
  data() {
    return {
      products: [],
    };
  },
  methods: {
    setProducts(data) {
      this.products = data;
    }
  },
  mounted() {
    axios
    .get('http://localhost:3000/best-products')
    .then((response) => this.setProducts(response.data))
    .catch((error) => console.log(error)
  )}
}
</script>
