<template>
  <div id="app">
    <router-view/>
    <FooterPart/>
  </div>
</template>
<script>
import FooterPart from "@/components/FooterPart.vue"

export default {
  components: {
    FooterPart
  }
}
</script>
