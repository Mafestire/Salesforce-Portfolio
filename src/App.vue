<template>
  <!-- <NavBar /> -->
  <router-view />
  <Footer />
</template>

<script>
// import NavBar  from "./components/NavBar.vue";
import Footer  from "./components/Footer.vue";

export default {
  components: {  Footer }
}
</script>

<style >
#app{
  background-color: #0A1128;
  font-family: 'Playfair Display', serif;
}


</style>
