<script>
import Card from "../Utilites/Card.vue";
import Cart from "../Utilites/Cart.vue";
import Checkout from "../Utilites/Checkout.vue";

export default {
  data() {
    return {
      products: [],
      maximum: 999999999,
      cart: [],
    };
  },
  components: {
    Card,
    Cart,
    Checkout,
  },
  mounted() {
    fetch("https://fakestoreapi.com/products")
      .then((res) => res.json())
      .then((data) => {
        this.products = data;
        console.log(this.products);
      });
  },
  methods: {
    addToCart(item) {
      let existingItem = this.cart.find((cartItem) => cartItem.title === item.title);
      if (existingItem) {
        existingItem.qty++;
        existingItem.price *= existingItem.qty;
        return;
      }
      this.cart.push({ title: item.title, price: parseFloat(item.price).toFixed(3), qty: 1 });

      console.log(this.cart);
    },

    removeToCart(item) {
      let existingItem = this.cart.find((cartItem) => cartItem.title === item.title);
      if (existingItem) {
        existingItem.qty--;
        existingItem.price *= existingItem.qty;
        if (existingItem.qty === 0) {
          this.cart = this.cart.filter((cartItem) => cartItem.title !== item.title);
        }
        return;
      }
    },
  },
};
</script>

<template>
  <main>
    <h1>Our Produtcs</h1>
    <div class="filter-price-wrapper">
      <label>Filter by price:</label>
      <input type="number" v-model="maximum" />
      <Cart :cart="cart" />
    </div>
    <Checkout :cart="cart" @add-to-cart="addToCart" @remove-to-cart="removeToCart" />
    <div class="card-container">
      <Card :products="products" :maximum="maximum" @add-to-cart="addToCart" />
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
