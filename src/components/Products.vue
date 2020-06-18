<template>
  <div class="products">
    <Product
      v-for="product in products"
      :key="product.name"
      :name="product.name"
      :price="product.price"
      :storage="product.storage"
      :image="product.image"
    >
      <button class="add-to-cart" @click="$emit('addProduct', product)">Add To Cart</button>
    </Product>
  </div>
</template>

<script>
import Product from "./Product";

export default {
  name: "Products",
  props: ["products"],
  components: {
    Product
  }
};
</script>

<style scoped>
</style>
