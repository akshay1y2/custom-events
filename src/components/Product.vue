<template>
  <div class="product">
    <div class="product-image">
      <img :src="require(`../assets/${image}`)" :alt="image" />
    </div>
    <ul class="product-text">
      <li>{{name}}</li>
      <li>${{price}}</li>
      <li>{{storage}}</li>
      <li>
        <slot></slot>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "Product",
  props: {
    name: String,
    price: String,
    storage: String,
    image: String
  }
};
</script>

<style scoped>
.product-image {
  width: 30%;
}
.product-text {
  width: 60%;
}
</style>
