<template>
  <div class="cart">
    <Product
      v-for="product in products"
      :key="product.name"
      :name="product.name"
      :price="product.price"
      :storage="product.storage"
      :image="product.image"
    >
      <button class="remove-from-cart" @click="removeProduct(product.name)">Remove</button>
    </Product>
    <button v-if="products.length" class="checkout" @click="$emit('checkout')">Checkout</button>
  </div>
</template>

<script>
import Product from "./Product";

export default {
  name: "Cart",
  props: ["products"],
  components: {
    Product
  },
  methods: {
    removeProduct: function(name) {
      this.products = this.products.filter(product => product.name !== name);
    }
  }
};
</script>

<style scoped>
</style>
