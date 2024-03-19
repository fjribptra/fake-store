<script>
export default {
  props: {
    cart: {
      type: Array,
      deafult: [],
    },
  },
  methods: {
    addToCart(item) {
      this.$emit("add-to-cart", item);
    },
    removeToCart(item) {
      this.$emit("remove-to-cart", item);
    },
  },
  computed: {
    priceCount() {
      let total = 0;
      this.cart.forEach((item) => {
        total += item.price * item.qty;
      });
      return parseFloat(total).toFixed(3);
    },
  },
};
</script>

<template>
  <div>
    <h1>Our Chekouts</h1>
    <table border="1" width="100%" cellpadding="10">
      <thead>
        <tr>
          <th>Actions</th>
          <th>Product</th>
          <th>qty</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item in cart">
          <td>
            <button @click="addToCart(item)">+</button>
            <button @click="removeToCart(item)">-</button>
          </td>
          <td>{{ item.title }}</td>
          <td>{{ item.qty }}</td>
        </tr>
      </tbody>
    </table>

    <h2>{{ priceCount }}</h2>
  </div>
</template>
