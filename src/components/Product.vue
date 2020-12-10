<template>
  <div class="product">
    <h3 class="cool">{{ productProp.name }}</h3>
    <p>{{ productProp.price }}</p>
  </div>
</template>

<script>
export default {
  name: 'Product',
  props: ['productProp']
}
</script>

<style>
.product {
  display: flex;
  justify-content: space-around;
}
</style>