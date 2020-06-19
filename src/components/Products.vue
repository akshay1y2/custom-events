<template>
  <div class="products">
    <h2>Products</h2>
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
.add-to-cart {
  margin-top: 1em;
  background-color: lightgreen;
}
</style>
