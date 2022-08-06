<template>
  <header class="top-bar spread">
    <nav class="top-bar-nav">
      <router-link to="/" class="top-bar-link">
        <span> <svg xmlns="http://www.w3.org/2000/svg" width="30" height="30" fill="currentColor"
            class="bi bi-house-fill" viewBox="0 0 16 16" style="color: white;">
            <path fill-rule="evenodd"
              d="m8 3.293 6 6V13.5a1.5 1.5 0 0 1-1.5 1.5h-9A1.5 1.5 0 0 1 2 13.5V9.293l6-6zm5-.793V6l-2-2V2.5a.5.5 0 0 1 .5-.5h1a.5.5 0 0 1 .5.5z" />
            <path fill-rule="evenodd"
              d="M7.293 1.5a1 1 0 0 1 1.414 0l6.647 6.646a.5.5 0 0 1-.708.708L8 2.207 1.354 8.854a.5.5 0 1 1-.708-.708L7.293 1.5z" />
          </svg>
          </span>
      </router-link>
      <router-link to="/products" class="top-bar-link">
        <span>Productos</span>
      </router-link>
      <router-link to="/past-orders" class="top-bar-link">
        <span>Compras realiazadas</span>
      </router-link>
    </nav>
    <div @click="toggleSidebar" class="top-bar-cart-link">
      <i class="icofont-cart-alt icofont-1x"></i>
      <span>Cart ({{ totalQuantity }})</span>
    </div>
  </header>
  <router-view :inventory="inventory" :addToCart="addToCart" />

  <Sidebar v-if="showSidebar" :toggle="toggleSidebar" :cart="cart" :inventory="inventory" :remove="removeItem" />
</template>

<script>
import Sidebar from '@/components/Sidebar.vue'
import food from './food.json'

export default {
  components: {
    Sidebar
  },
  data() {
    return {
      showSidebar: false,
      inventory: food,
      cart: {}
    }
  },
  computed: {
    totalQuantity() {
      return Object.values(this.cart).reduce((acc, curr) => {
        return acc + curr
      }, 0)
    }
  },
  methods: {
    addToCart(name, quantity) {
      if (!this.cart[name]) this.cart[name] = 0
      this.cart[name] += quantity
    },
    toggleSidebar() {
      this.showSidebar = !this.showSidebar
    },
    removeItem(name) {
      delete this.cart[name]
    }
  }
}
</script>
