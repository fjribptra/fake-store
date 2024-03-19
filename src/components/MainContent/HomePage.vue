<script>
import Card from "../Utilites/Card.vue";

export default {
  components: {
    Card,
  },
};
</script>

<template>
  <main>
    <h1>Our Produtcs</h1>
    <div class="card-container">
      <Card />
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

.card-container {
  width: 100%;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
  margin-top: 20px;
}
</style>
