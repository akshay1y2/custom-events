<template>
  <div class="order-summary" v-if="products.length">
    <h2>Congratulations! Your order is successfully placed</h2>
    <Product
      v-for="product in products"
      :key="product.name"
      :name="product.name"
      :price="product.price"
      :storage="product.storage"
      :image="product.image"
    />
    <hr />
    <h2>Items Ordered: {{products.length}}</h2>
    <h2>Total Price: {{totalPrice}}</h2>
  </div>
</template>

<script>
import Product from "./Product";

export default {
  name: "OrderSummary",
  props: ["products", "totalPrice"],
  components: {
    Product
  }
};
</script>

<style scoped>
.order-summary {
  max-width: 50%;
}
</style>
