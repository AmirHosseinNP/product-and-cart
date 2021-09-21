<template>
  <Navbar
    :cart="cart"
    :toggle="toggleSidebar"
  />
  <router-view
    :add_to_cart="addToCart"
    :inventory="inventory"
  />
  <Sidebar
    v-if="showSidebar"
    :cart="cart"
    :toggle="toggleSidebar"
    :remove_from_cart="removeFromCart"
  />
</template>

<script>
import Navbar from "./components/Navbar";
import Sidebar from "./components/Sidebar";
import food from "@/assets/food.json";

export default {
  data() {
    return {
      showSidebar: false,
      inventory: food,
      cart: []
    };
  },
  methods: {
    toggleSidebar() {
      this.showSidebar = !this.showSidebar;
    },
    addToCart(product) {
      const p = JSON.parse(JSON.stringify(product));
      const productExistsInCart = this.cart.findIndex((item) => {
        return item.id === p.id;
      });
      if (productExistsInCart > -1) {
        this.cart[productExistsInCart].quantity += p.quantity;
      } else {
        this.cart.push(p);
      }
      product.quantity = 0;
    },
    removeFromCart(product) {
      const index = this.cart.findIndex((item) => {
        return item.id === product.id;
      });
      this.cart.splice(index, 1);
    }
  },
  components: { Sidebar, Navbar }
};

</script>