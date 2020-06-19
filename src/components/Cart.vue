<template>
  <div class="cart">
    <div class="cart-head">
      <h2>Cart: ${{totalPrice}}</h2>
      <button v-if="products.length" class="checkout" @click="$emit('checkout')">Checkout</button>
    </div>
    <Product
      v-for="product in products"
      :key="product.name"
      :name="product.name"
      :price="product.price"
      :storage="product.storage"
      :image="product.image"
    >
      <button class="remove-from-cart" @click="$emit('removeProduct', product)">Remove</button>
    </Product>
  </div>
</template>

<script>
import Product from "./Product";

export default {
  name: "Cart",
  props: ["products", "totalPrice"],
  components: {
    Product
  }
};
</script>

<style scoped>
.remove-from-cart {
  background-color: lightsalmon;
}
.checkout {
  margin: 1em;
  background-color: lime;
}
.cart {
  min-height: 500px;
}
.cart-head {
  display: flex;
}
</style>
