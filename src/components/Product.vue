<template>
  <div class="product">
    <div class="product-image">
      <img :src="require(`../assets/${image}`)" :alt="image" />
    </div>
    <ul class="product-text">
      <li><strong>{{name}}</strong></li>
      <li><strong>${{price}}({{storage}})</strong></li>
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
.product {
  display: flex;
}
</style>
