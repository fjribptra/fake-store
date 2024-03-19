<script>
export default {
  data() {
    return {
      products: [],
    };
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
  <div class="card-wrapper" v-for="item in products" :key="item.id">
    <div>
      <img :src="item.image" alt="..." />
      <h2>{{ item.title }}</h2>
      <p>{{ item.description }}</p>
    </div>
    <div class="button-wrapper">
      <button>Add to cart</button>
      <strong>Rp {{ parseFloat(item.price).toFixed(3) }}</strong>
    </div>
  </div>
</template>

<style scoped>
.card-wrapper {
  background-color: white;
  padding: 20px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  gap: 10px;
  border-radius: 20px;
}

img {
  width: 100%;
  height: 300px;
}

.button-wrapper {
  display: flex;
  align-items: center;
  gap: 20px;
}

button {
  padding: 10px;
  border: none;
  background-color: blue;
  color: white;
  cursor: pointer;
  border-radius: 5px;
  transition: 0.3s all;
}

button:hover {
  background-color: black;
}

strong {
  font-weight: bold;
  font-size: 1.5rem;
}
</style>
