<template>
  <div id="app">
    <div id="productsContainer">
      <Products :products="products" @addProduct="addToProductsInCart" />
    </div>
    <div class="cartContainer">
      <Cart :products="productsInCart" @checkout="checkoutOrder" />
    </div>
    <div class="orderSummaryContainer">
      <OrderSummary :products ="productsInOrderSummary" />
    </div>
  </div>
</template>

<script>
import Products from "./components/Products";
import Cart from "./components/Cart";
import OrderSummary from "./components/OrderSummary";

export default {
  name: "App",
  data() {
    return {
      productsInCart: [],
      productsInOrderSummary: [],
      products: [
        {
          name: "Iphone 11 Pro (Silver)",
          price: "999",
          storage: "64gb",
          image: "silver.png"
        },
        {
          name: "Iphone 11 Pro (Grey)",
          price: "1199",
          storage: "128gb",
          image: "grey.png"
        },
        {
          name: "Iphone 11 Pro (Gold)",
          price: "1399",
          storage: "256gb",
          image: "gold.png"
        },
        {
          name: "Iphone 11 Pro (Midnight Green)",
          price: "1599",
          storage: "512gb",
          image: "green.png"
        }
      ]
    };
  },
  components: {
    Products,
    Cart,
    OrderSummary
  },
  methods: {
    addToProductsInCart: function(product) {
      this.productsInCart.push(product);
    },
    checkoutOrder: function() {
      this.productsInOrderSummary = Array.from(this.productsInCart);
      this.productsInCart = [];
    }
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
#productsContainer {
  width: 60%;
}
.products img {
  max-width: 100px;
}
.cart img {
  max-width: 20px;
}
#cartContainer {
  width: 30%;
}
#orderSummaryContainer {
  margin: 5px;
}
</style>
