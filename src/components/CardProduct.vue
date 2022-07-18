<template>
  <div class="card shadow card-product mt-3 mb-3" style="width: 18rem">
    <img :src=" 'assets/images/' + product.gambar" class="card-img-top" alt="..." />
    <div class="card-body">
      <h2>{{ product.nama }}</h2>
      <p class="card-text">
        Harga : {{ product.harga }}
      </p>
      <router-link :to="'/foods/'+ product.id" class="btn btn-info"><b-icon icon="cart" ></b-icon>&nbsp; Pesan</router-link>
    </div>
  </div>
</template>
<script>
export default {
  name: "CardProduct",
  props: ["product"],
};
</script>

<style></style>
