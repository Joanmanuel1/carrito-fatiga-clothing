<template>
  <div class="card">

    <div class="card-body">
      <img :src="require(`../assets/img/${product.icon}`)" alt="Top News" style="width: 100%; height:200px; border-radius: 25%;" />

      <form>
        <div class="row">
          <div class="cell">
            <label>Tipo:</label>
          </div>
          <div class="cell">
            <em>{{ product.type }}</em>
          </div>
        </div>
        <div class="row">
          <div class="cell">
            <label>Precio:</label>
          </div>
          <div class="cell">
            ${{ product.price.USD }}
          </div>
        </div>
        <div class="row">
          <div class="cell">
            <label>Marca:</label>
          </div>
          <div class="cell">
            {{ product.marca }}
          </div>
        </div>
        <div class="row">
          <div class="cell">
            <label>Color:</label>
          </div>
          <div class="cell">
            {{ product.name }}
          </div>
        </div>
        <div class="row">
          <div class="cell">
            <label>Cantidad:</label>
          </div>
          <div class="cell">
            <input type="number" v-model.number="quantity">
          </div>
        </div>
      </form>
    </div>
    <div class="card-footer">
      <button @click="addToCart(product.name, quantity)" class="btn btn-light">
        Add to cart
      </button>
    </div>
  </div>
</template>

<script>
export default {
  props: ['product', 'index', 'addToCart'],
  data() {
    return {
      quantity: 0
    }
  }
}
</script>
