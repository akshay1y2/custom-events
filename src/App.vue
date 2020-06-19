<template>
  <div id="app">
    <div id="productsContainer">
      <Products :products="products" @addProduct="addToProductsInCart" />
    </div>
    <div id="cartContainer">
      <Cart
        :products="productsInCart"
        :totalPrice="totalPrice"
        @checkout="checkoutOrder"
        @removeProduct="removeProductFromCart"
      />
    </div>
    <div class="orderSummaryContainer">
      <OrderSummary :products="productsInOrderSummary" :totalPrice="orderPrice" />
    </div>
  </div>
</template>

<script>
import Products from "./components/Products";
import Cart from "./components/Cart";
import OrderSummary from "./components/OrderSummary";
import _ from "lodash";

export default {
  name: "App",
  data() {
    return {
      productsInCart: [],
      productsInOrderSummary: {},
      orderPrice: null,
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
    removeProductFromCart: function(product) {
      this.productsInCart = [
        ..._.filter(this.productsInCart, function(p) {
          return p !== product;
        })
      ];
    },
    checkoutOrder: function() {
      this.productsInOrderSummary = _.cloneDeep(this.productsInCart);
      this.orderPrice = this.totalPrice;
      this.productsInCart = [];
    }
  },
  computed: {
    totalPrice: function() {
      return _.sumBy(this.productsInCart, p => Number.parseInt(p.price));
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
}
#productsContainer {
  float: left;
  width: 65%;
}
#productsContainer .product {
  float: left;
  width: 50%;
}
.products img {
  max-width: 100px;
}
.cart img {
  max-width: 50px;
}
.orderSummaryContainer img {
  max-width: 50px;
}
#cartContainer {
  float: left;
  width: 35%;
}
li {
  list-style-type: none;
}
h2 {
  color: brown;
}
</style>
