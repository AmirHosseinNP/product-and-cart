<template>
  <aside class="cart-container">
    <div class="cart">
      <h1 class="cart-title spread">
            <span>
              Cart
              <i class="icofont-cart-alt icofont-1x"></i>
            </span>
        <button class="cart-close" style="cursor: pointer;" @click="toggle">&times;</button>
      </h1>

      <div class="cart-body">
        <table class="cart-table">
          <thead>
          <tr>
            <th><span class="sr-only">Product Image</span></th>
            <th>Product</th>
            <th>Price</th>
            <th>Qty</th>
            <th>Total</th>
            <th><span class="sr-only">Actions</span></th>
          </tr>
          </thead>
          <tbody>
          <tr v-for="item in cart" :key="item.id" style="text-align: center;">
            <td><i :class="getIcon(item)"></i></td>
            <td>{{ item.name }}</td>
            <td>${{ item.price.USD.toFixed(2) }}</td>
            <td class="center">{{ item.quantity }}</td>
            <td>${{ itemTotalCost(item).toFixed(2) }}</td>
            <td class="center">
              <button style="cursor: pointer" @click="remove_from_cart(item)" class="btn btn-light cart-remove">
                &times;
              </button>
            </td>
          </tr>
          </tbody>
        </table>

        <p style="margin-top: 30px;" v-if="!cart.length" class="center"><em>No items in cart</em></p>
        <div class="spread" style="margin-top: 20px;">
          <span><strong>Total:</strong> ${{ cartTotalCost.toFixed(2) }}</span>
          <button class="btn btn-light">Checkout</button>
        </div>
      </div>
    </div>
  </aside>
</template>

<script>
export default {
  name: "Sidebar",
  props: ["cart", "toggle", "remove_from_cart"],
  methods: {
    getIcon(item) {
      return "icofont-3x icofont-" + item.icon;
    },
    itemTotalCost(item) {
      return (item.quantity * item.price.USD);
    }
  },
  computed: {
    cartTotalCost() {
      return this.cart.reduce((total, item) => {
        return total + this.itemTotalCost(item);
      }, 0);
    }
  }
};
</script>