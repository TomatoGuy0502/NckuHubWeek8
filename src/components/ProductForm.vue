<template>
  <form @submit.prevent="handleSubmit">
    <h3 class="cool">新增商品表單</h3>
    <label>name</label>
    <input type="text" required v-model="name">
    <br>
    <label>price</label>
    <input type="number" required v-model="price">
    <br>
    <button type="submit">新增商品</button>
  </form>
</template>

<script>
export default {
  name: 'ProductForm',
  data() {
    return {
      name: '',
      price: null
    }
  },
  methods: {
    handleSubmit() {
      this.$emit('addProductEvent', {
        name: this.name,
        price: this.price
      })
      this.name = ''
      this.price = null
    }
  }
}
</script>

<style scoped lang="scss">
form {
  input {
    border: none;
  }
}
.cool {
  font-size: 24px;
}
</style>