<template>
  <div class="products">
    <main class="wrapper">
      <h1>Products</h1>

      <div class="card-container">
        <ProductCard
          v-for="product in inventory"
          :key="product.id"
          v-model="product.quantity"
          :addToCart="add_to_cart"
          :product="product"
        />
      </div>
    </main>
  </div>
</template>

<script>
import ProductCard from "../components/ProductCard";

export default {
  name: "Products",
  components: { ProductCard },
  props: ["inventory", "add_to_cart"]
};
</script>