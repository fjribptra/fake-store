<script>
export default {
  props: {
    cart: {
      type: Array,
      deafult: [],
    },
  },
};
</script>

<template>
  <div>
    <h1>{{ cart.length }}</h1>
  </div>
</template>
