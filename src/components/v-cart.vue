<template>
  <div class="v-cart">
    <h2 class="v-cart_title">Корзина</h2>
    <router-link :to="{ name: 'catalog' }">
      <div class="v-catalog__link_to_cart">
        <i class="medium material-icons">shopping_basket</i>
        {{ CART.length }}
      </div>
      <button class="v-catalog__link_to_cart_btn btn">Перейти в каталог</button>
    </router-link>
    <p class="v-cart_text" v-if="!CART.length">В корзине пока нет товаров...</p>
    <vCartItem v-for="(item, index) in CART" :key="item.article" :cart_item_data="item"
      @deleteFromCart="deleteFromCart(index)" />
  </div>
</template>

<script>
import vCartItem from './v-cart-item.vue'
import { mapActions, mapGetters } from 'vuex'

export default {
  name: 'v-cart',
  components: {
    vCartItem
  },
  props: {
    cart_data: {
      type: Array,
      default () {
        return []
      }
    }
  },
  computed: {
    ...mapGetters(['CART'])
  },
  methods: {
    ...mapActions(['DELETE_FROM_CART']),
    deleteFromCart (index) {
      this.DELETE_FROM_CART(index)
    }
  }
}
</script>

<style scoped>
.v-cart {
  display: flex;
  flex-direction: column;
  flex-wrap: wrap;
  color: #4e4b4b;
  font-size: 15px;
  margin-bottom: 100px;
}

.v-cart_title,
.v-cart_text {
  text-align: center;
}
</style>
