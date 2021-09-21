<template>
  <header class="top-bar spread">
    <nav class="top-bar-nav">
      <router-link class="top-bar-link" to="/">
        <i class="icofont-spoon-and-fork"></i>
        <span>Home</span>
      </router-link>
      <router-link class="top-bar-link" to="/products">
        <span>Products</span>
      </router-link>
      <router-link class="top-bar-link" to="/past-orders">
        <span>Past Orders</span>
      </router-link>
    </nav>
        <div style="cursor: pointer;" @click.prevent="toggle" class="top-bar-cart-link">
          <i class="icofont-cart-alt icofont-1x"></i>
          <span>Cart ({{ cart.length }})</span>
        </div>
  </header>
</template>

<script>
export default {
  name: "Navbar",
  props: ['cart', 'toggle']
}
</script>
