<template>
  <main class="wrapper">
    <h1>Productos</h1>
    <p>ENVÍO A CARGO DEL COMPRADOR</p>
    <p>ENTREGAS EN LA ESTACIÓN DE LOMAS/BANFIELD🎁</p>
    <div class="card-container">
      <ProductCard v-for="(product, index) in inventory.slice(0, 50)" :key="product.id" class="card" :index="index"
        :product="product" :addToCart="addToCart" />
    </div>
  </main>

</template>

<script>
import ProductCard from '@/components/ProductCard.vue'

export default {
  props: ['inventory', 'addToCart'],
  components: {
    ProductCard
  }
}
</script>
