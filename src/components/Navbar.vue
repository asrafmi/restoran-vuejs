<template>
    <nav class="navbar navbar-expand-lg">
        <div class="container">
            <div class="container-fluid">
                <a class="navbar-brand" href="#">Navbar</a>
                <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
                </button>
            <div class="collapse navbar-collapse" id="navbarSupportedContent">
                <ul class="navbar-nav me-auto mb-2 mb-lg-0">
                    <li class="nav-item">
                      <router-link class="nav-link" to="/">Home</router-link>
                    </li>
                    <li class="nav-item">
                      <router-link class="nav-link" to="/foods">Foods</router-link>
                    </li>
                </ul>
            </div>
            <div class="collapse navbar-collapse" id="navbarSupportedContent">
                <ul class="navbar-nav ml-auto mb-2 mb-lg-0">
                    <li class="nav-item">
                      <router-link class="nav-link" to="/keranjang">Keranjang
                        <b-icon icon="bag" animation="cylon-vertical"></b-icon>
                        <span class="badge badge-info ml-2" >{{ updateKeranjang ? updateKeranjang.length : jumlah_pesanan.length }}</span>
                      </router-link>   
                    </li>
                </ul>
            </div>
          </div>
      
        </div>
    </nav>
</template>

<script>
import axios from 'axios';

export default {
    name : 'NavbarSide',
    data() {
        return {
            jumlah_pesanan : [],
        };
    },
    props: ['updateKeranjang'],
    methods: {
        setJumlah(data){
            this.jumlah_pesanan = data;
        }
    },
    mounted() {
        axios
        .get('http://localhost:3000/keranjangs')
        .then((response) => this.setJumlah(response.data))
        .catch((error) => console.log(error));
    }
}
</script>

<style>

</style>