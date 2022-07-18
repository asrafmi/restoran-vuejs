<template>
  <div class="hero">
    <!-- desktop -->
    <div class="d-none d-md-block">
      <div class="row mt-3">
        <div class="col md-6">
          <div class="d-flex h-100">
            <div class="justify-content-center align-self-center">
              <h2>
                <strong>Makanan Uenak Buanget</strong> <br />
                ada disini!
              </h2>
              <p>Ayo buruan pilih makanan favorit Anda!</p>
              <router-link class="btn btn-lg btn-info" to="/foods">
                <b-icon icon="arrow-right" animation="cylon"></b-icon> &nbsp;
                Pesan
              </router-link>
              <router-link class="btn btn-lg btn-success">Pesan</router-link>
            </div>
          </div>
        </div>
        <div class="col">
          <img id="hero-img" src="../assets/images/hero.svg" width="100%" />
        </div>
      </div>
    </div>

    <!-- Mobile -->
    <div class="d-sm-block d-md-none">
      <div class="row mt-3">
        <div class="col md-6">
          <img id="hero-img" src="../assets/images/hero.svg" width="100%" />
          <div class="d-flex h-100">
            <div class="justify-content-center align-self-center">
              <h2>
                <strong>Makanan Uenak Buanget</strong> <br />
                ada disini!
              </h2>
              <p>Ayo buruan pilih makanan favorit Anda!</p>
              <button class="btn btn-lg btn-info">
                <b-icon icon="arrow-right" animation="cylon"></b-icon> &nbsp;
                Pesan
              </button>
              <router-link class="btn btn-lg btn-success">Pesan</router-link>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "HeroPart",
};
</script>

<style>
</style>