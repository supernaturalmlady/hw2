<template>
  <div>
    <ProductCard
      v-for="product in products"
      :key="product.id"
      :product="product"
    />
  </div>
</template>

<script>
import axios from 'axios'
import ProductCard from './components/ProductCard.vue'

export default {
  components: {
    ProductCard,
  },

  data() {
    return {
      products: [],
    }
  },

  mounted() {
    axios.get('https://fakestoreapi.com/products').then((response) => {
      this.products = response.data
    })
  },
}
</script>

<style scoped>
div {
  width: 80vh;
  height: 600px;
  margin: 0 auto;
  margin-bottom: 30px;
}
</style>
