<script>
import Card from "../Utilites/Card.vue";

export default {
  data() {
    return {
      products: [],
      maximum: 999999999,
    };
  },
  components: {
    Card,
  },
  mounted() {
    fetch("https://fakestoreapi.com/products")
      .then((res) => res.json())
      .then((data) => {
        this.products = data;
        console.log(this.products);
      });
  },
};
</script>

<template>
  <main>
    <h1>Our Produtcs</h1>
    <div class="filter-price-wrapper">
      <label>Filter by price:</label>
      <input type="number" v-model="maximum" />
    </div>
    <div class="card-container">
      <Card :products="products" :maximum="maximum" />
    </div>
  </main>
</template>

<style scoped>
main {
  width: 100%;
  padding: 20px;
  background-color: #ddd;
}

h1 {
  font-weight: bold;
}

.filter-price-wrapper {
  display: flex;
  gap: 10px;
}

.card-container {
  width: 100%;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
  margin-top: 20px;
}
</style>
