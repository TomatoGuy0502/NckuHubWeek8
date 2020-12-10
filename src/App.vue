<template>
  <p v-if="!products.length">Loading</p>
  <div v-else class="products">
    <Product 
      v-for="product in products" 
      :key="product.name" 
      :productProp="product"/>
  </div>
  <ProductForm @addProductEvent="addProduct"/>
</template>

<script>
import Product from './components/Product.vue'
import ProductForm from './components/ProductForm.vue'

export default {
  name: 'App',
  components: {
    Product,
    ProductForm
  },
  data() {
    return {
      products: []
    }
  },
  methods: {
    addProduct(data) {
      this.products.push(data)

      fetch('http://localhost:3000/products', {
        method: 'POST',
        headers: { 'content-type': 'application/json' },
        body: JSON.stringify(data)
      })
        .then(res => console.log(res))
        .catch(err => console.log(err))
    }
  },
  created() {
    fetch('http://localhost:3000/products')
      .then(res => res.json())
      .then(data => this.products = data)
      .catch(err => console.log(err))
  }
}
</script>

<style lang="scss">
body {
  background-color: #eee;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.products {
  background-color: #fff;
  padding: 10px;
  border-radius: 10px;
}
</style>
