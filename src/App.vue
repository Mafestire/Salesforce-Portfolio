<template>
  <SpaceBackground />
  <router-view />
  <Footer />
</template>

<script>
import SpaceBackground from "@/components/SpaceBackground.vue";
import Footer from "./components/Footer.vue";

export default {
  components: { SpaceBackground, Footer },
};
</script>

<style>
#app {
  background-color: transparent;   /* 👈 was #0A1128 */
  font-family: 'Playfair Display', serif;
  position: relative;
  z-index: 1;
}

html, body {
  /*background: #050B14;*/
  margin: 0;
  padding: 0;
}
</style>
