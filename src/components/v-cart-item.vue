<template>
  <div class="v-cart-item">
    <img class="v-cart-item_image" :src="require('../assets/images/' + cart_item_data.image)" alt="picture" />
    <div>
      <p class="v-cart-item_name">{{ cart_item_data.name }}</p>
      <p class="v-cart-item_price">{{ cart_item_data.price }}</p>
      <p class="v-cart-item_article">{{ cart_item_data.article }}</p>
      <p class="v-cart-item_about">{{ cart_item_data.about }}</p>
    </div>
    <button class="btn" @click="deleteFromCart">Удалить товар из корзины</button>
  </div>
</template>

<script>
export default {
  name: 'v-cart-item',
  props: {
    cart_item_data: {
      type: Object,
      default () {
        return {}
      }
    }
  },
  methods: {
    deleteFromCart () {
      this.$emit('deleteFromCart')
    }
  },
  mounted () {
    console.log('hello Im here!')
  }
}
</script>

<style>
.v-cart-item {
    display: flex;
    justify-content: space-between;
    flex-wrap: wrap;
    align-items: center;
    flex-basis: 25%;
    box-shadow: 0 0 8px 0 gray;
    padding: 20px;
    margin: 20px;
}
</style>
