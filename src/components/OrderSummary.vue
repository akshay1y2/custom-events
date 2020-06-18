<template>
  <div class="order-summary">
    <Product
      v-for="product in products"
      :key="product.name"
      :name="product.name"
      :price="product.price"
      :storage="product.storage"
      :image="product.image"
    />
  </div>
</template>

<script>
import Product from "./Product";

export default {
  name: 'OrderSummary',
  props: ["products"],
  components: {
    Product
  }
};
</script>

<style scoped>
</style>
