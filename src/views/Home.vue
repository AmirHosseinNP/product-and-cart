<template>
  <div class="home">
    <div class="splash-container">
      <div class="splash">
        <h1>Splendid Food</h1>
      </div>
    </div>
    <main class="wrapper">
        <h2>Recommended</h2>
        <div class="recommended">
          <ProductCard
            v-for="(product) in inventory.slice(0,3)"
            :key="product.id"
            :product="product"
            :addToCart="add_to_cart"
            v-model="product.quantity"
          />
        </div>
    </main>
  </div>
</template>

<script>
// @ is an alias to /src

import ProductCard from "../components/ProductCard";
export default {
  name: "Home",
  props: ['inventory', 'add_to_cart'],
  components: {
    ProductCard
  }
};
</script>
