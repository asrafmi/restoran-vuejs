<template>
  <div class="food-detail">
    <NavbarSide />
    <div class="container">
        <!-- breadcrumb -->
      <div class="row mt-5">
        <div class="col">
          <nav aria-label="breadcrumb">
            <ol class="breadcrumb">
              <li class="breadcrumb-item"><router-link class="text-dark" to="/">Home</router-link></li>
              <li class="breadcrumb-item"><router-link to="/foods" class="text-dark">Foods</router-link></li>
              <li class="breadcrumb-item active" aria-current="page">Food Order</li>
            </ol>
          </nav>
        </div>
      </div>
      <!-- Details -->
      <div class="row">
        <div class="col md-6">
            <img :src="'../assets/images/' +product.gambar " class="img-fluid shadow">
        </div>
        <div class="col md-6">
            <h2>
                <strong>{{product.nama}}</strong>
            </h2>
            <hr>
            <h4>
                Harga : <strong>Rp {{ product.harga }} </strong>
            </h4>
            <form class="">
                <div class="form-group" v-on:submit.prevent>
                    <label for="jumlah_pesanan">Jumlah Pesan</label>
                    <input type="number" class="form-control" v-model="pesan.jumlah_pesanan">
                </div>
                    <div class="form-group">
                    <label for="keterangan">Keterangan</label>
                    <textarea class="form-control" v-model="pesan.keterangan" placeholder="Keterangan seperti : Nggak pedes, nasi setengah, etc" id="" cols="30" rows="2"></textarea>
                </div>
                <button type="submit" class="btn btn-info" @click="pemesanan">
                    <b-icon-cart></b-icon-cart> Pesan
                </button>
            </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import NavbarSide from "@/components/Navbar.vue";
import axios from 'axios'


export default {
  name: "FoodDetail",
  components: {
    NavbarSide,
  },
  data() {
    return{
        product:{},
        pesan:{}
    }
  },
  methods: {
    setProduct(data) {
      this.product = data;
    },
    pemesanan() {
        if (this.pesan.jumlah_pesanan) {
            this.pesan.products = this.product;
            axios
            .post("http://localhost:3000/keranjangs", this.pesan)
            .then(() => {
                this.$router.push({ path: "/keranjang"})
                this.$toast.success('Sukses masuk keranjang!', {
                    position:'bottom-right',
                    duration: 5000,
                    dismissible: true
                })
            })
            .catch((error) => console.log(error));            
        } else {
            this.$toast.error('Silahkan isi jumlah Pesanannn!!', {
                    position:'bottom-right',
                    duration: 5000,
                    dismissible: true
            })
        }

    }
  },
  mounted() {
    axios
      .get("http://localhost:3000/products/" + this.$route.params.id)
      .then((response) => this.setProduct(response.data))
      .catch((error) => console.log(error));
  },
};
</script>

<style>
</style>