<template>
  <div class="card">
    <div class="card-title">
      {{ product.name }}
    </div>
    <div class="card-body">
      <i :class="getIcon()"></i>
      <form>
        <div class="row">
          <div class="cell">
            <label>Type:</label>
          </div>
          <div class="cell">
            <em>{{ product.type }}</em>
          </div>
        </div>
        <div class="row">
          <div class="cell">
            <label>Price:</label>
          </div>
          <div class="cell">
            ${{ product.price.USD.toFixed(2) }}
          </div>
        </div>
        <div class="row">
          <div class="cell">
            <label>Quantity:</label>
          </div>
          <div class="cell">
            <input type="number" min="0" v-model="quantity"/>
          </div>
        </div>
      </form>
    </div>
    <div class="card-footer">
      <button @click="addToCart(product)" class="btn btn-light">
        Add to cart
      </button>
    </div>
  </div>
</template>

<script>
  export default {
    name: "ProductCard",
    props: ['product', 'modelValue', 'addToCart'],
    data() {
      return {
      }
    },
    computed: {
      quantity: {
        get() {
          return this.modelValue === undefined ? 0 : this.modelValue;
        },
        set(value) {
          this.$emit('update:modelValue', value);
        }
      }
    },
    methods: {
      getIcon() {
        return 'icofont-10x icofont-' + this.product.icon;
      }
    }
  }
</script>