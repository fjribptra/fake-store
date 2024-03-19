<script>
import Navbar from "./components/Header/Navbar.vue";
import HomePage from "./components/MainContent/HomePage.vue";

export default {
  components: {
    Navbar,
    HomePage,
  },

};
</script>

<template>
  <Navbar />
  <HomePage :produtcs="products" />
</template>

<style scoped></style>
