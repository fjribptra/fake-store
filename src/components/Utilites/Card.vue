<script>
export default {
  props: {
    products: {
      type: Array,
      deafult: [],
    },
    maximum: {
      type: Number,
      default: 0,
    },
  },
  computed: {
    showItems() {
      let max = this.maximum;
      return this.products.filter((product) => product.price <= max);
    },
  },
};
</script>

<template>
  <div class="card-wrapper" v-for="item in showItems" :key="item.id">
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
