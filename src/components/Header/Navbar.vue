<script>
import Cart from "../Utilites/Cart.vue";
export default {
  components: {
    Cart,
  },
};
</script>
<template>
  <header>
    <div class="logo">
      <img src="https://vuejs.org/images/logo.png" alt="navbar-logo" />
      <h1>Fake Store</h1>
    </div>
    <Cart />
  </header>
</template>

<style scoped>
header {
  display: flex;
  justify-content: space-between;
  background-color: rgba(0, 150, 50, 0.9);
  padding: 20px;
  color: white;
  position: sticky;
  top: 0;
}

.logo {
  display: flex;
  align-items: center;
  gap: 10px;
}

.logo img {
  width: 50px;
}
</style>
